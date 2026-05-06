# TradePilot Customer Intelligence Layer
## 客户背景情报预处理层

> **版本：** 1.0.0 | **状态：** 付费内容 Premium Content
> **作用：** 在引擎 7 段式输出前，基于客户邮件信号挖掘客户背景，增强意图识别精度

---

## 概述 | Overview

本层是 TradePilot 引擎的**信号提取 → 背景调查 → 画像生成 → 意图增强**预处理模块。
在引擎执行 7 段式输出之前运行，将生成的客户画像简报喂入【客户意图】【风险提示】【沟通策略】三个核心环节，大幅提升回复的针对性。

**价值主张：**
- 没有本层：引擎只看文字，水平 ≈ 通用翻译器
- 加载本层：引擎知道对方是谁，水平 ≈ 资深行业业务员

---

## 1. 信号提取规则 | Signal Extraction

### 1.1 可提取的信号源

从用户输入的客户邮件 / 消息中抓取以下内容：

| 信号 | 来源 | 提取方法 |
|------|------|---------|
| 邮箱域名 | `@` 后面的部分 (user@company.com → company.com) | 正则提取 |
| 公司名称 | 邮件签名 / 正文中明确的公司名 | 语义识别 |
| 网站 URL | 邮件签名 / 正文中的链接 | URL 模式匹配 |
| 联系人姓名 | 发件人名称 / 签名行 | 语义识别 |
| 职位/头衔 | 签名行中的 title | 语义识别（如 CEO, Procurement Manager, Engineer）|
| 联系电话 | 签名行中的 phone | 号码格式匹配 |
| 地址 | 签名行 / 正文中的地址 | 地址格式匹配 |
| 客户来源国 | 邮箱域名 TLD / 地址 / 电话国家码 | 推断 |

### 1.2 信号优先级

```
高优先级 —— 对公司识别和搜索最关键：
  1. 网站 URL（最精确，直接提供官网入口）
  2. 公司名称（可组合多维度搜索）
  3. 邮箱域名（邮箱=公司域名时可用作公司标识）

中优先级 —— 用于辅助验证：
  4. 联系人姓名 + 职位（判断决策层级）
  5. 客户来源国（限定搜索范围）

低优先级 —— 补充信息：
  6. 电话 / 地址（辅助确认公司位置）
```

### 1.3 邮件解析示例

输入：客户邮件（签名含 `John Smith | Procurement Manager | ABC Pumps Ltd. | www.abc-pumps.com | john@abc-pumps.com | +234-XXX-XXXX | Lagos, Nigeria`）

提取结果：
```
email_domain: abc-pumps.com
company_name: ABC Pumps Ltd.
website: www.abc-pumps.com
contact_name: John Smith
contact_title: Procurement Manager
phone: +234-XXX-XXXX
region: Nigeria (from phone code + address)
```

---

## 2. 背景调查方法 | Background Investigation

### 2.1 搜索维度

根据提取的信号，按优先级依次执行以下搜索：

| 搜索维度 | 搜索目标 | 搜索方法 | 优先级 |
|---------|---------|---------|:------:|
| 公司官网 | 找到官网 → 了解公司规模、主营产品、市场定位 | web_fetch 官网首页 + About Us + Products | 🔴 高 |
| 公司简介 | 在行业目录 / 黄页上查公司背景 | web_search + web_fetch | 🔴 高 |
| 联系人查证 | LinkedIn 或社交平台查联系人职位 | web_search `"name" + company + LinkedIn` | 🟡 中 |
| 产品线 | 搜索公司主营产品 / 主打品类 | web_search `"company" products` | 🟡 中 |
| 贸易数据 | 搜索该公司进口/采购记录 | web_search `"company" import export buyer`（如有 ImportGenius 等更好）| 🟡 中 |
| 信誉信号 | 搜索客户评价、投诉、新闻 | web_search `"company" review complaint news` | 🟢 低 |
| 行业地位 | 搜索行业报道、合作伙伴 | web_search `"company" partner client project` | 🟢 低 |

### 2.2 多语言搜索策略

沿用 b2b-search-strategy 的思路，对同一目标使用多语言搜索以提高命中率：

```python
search_queries = [
    # English (highest priority)
    'ABC Pumps Ltd Nigeria profile',
    'ABC Pumps Ltd products supplier distributor',
    
    # Local language (if region is known)
    'ABC Pumps Ltd Nigeria yabo' if region == 'Nigeria' else '',
    'ABC Pumps Ltd empresa' if region in ['Mexico', 'Spain', 'Colombia'] else '',
    
    # Chinese (additional discovery)
    'ABC Pumps Ltd 公司 介绍 水泵' if product in ['pump', 'water pump'] else '',
    'ABC Pumps Ltd 进口商' if product in ['pump', 'generator'] else '',
    
    # Trade data exploration
    '"ABC Pumps" import export buyer',
    '"ABC Pumps Ltd" Nigeria',
]
```

### 2.3 搜索执行规则

- 对**每个搜索维度**，至少尝试 2 种不同表述的搜索词
- 使用可用搜索工具：`web_search` + `web_fetch`
- 如果某个维度搜索无结果，**不要编造**，标记为 `unconfirmed`
- 如果信息互相矛盾（如官网说 50 人，黄页说 200 人），标记为 `conflicting`
- 对搜索结果标注来源和置信度

---

## 3. 客户画像简报格式 | Customer Profile Brief

搜索完成后，生成结构化的客户画像简报。以下是标准格式：

```json
{
  "company": {
    "name": "ABC Pumps Ltd",
    "website": "www.abc-pumps.com",
    "estimated_size": "中型（约50-100人）",
    "established": "2010年（来源：LinkedIn）",
    "main_products": "离心泵、潜水污水泵、配件",
    "target_market": "西非（尼日利亚、加纳）",
    "market_position": "西非本地分销商，代理多个品牌",
    "customer_type": "distributor",
    "source": "官网 + 黄页（高置信度）"
  },
  "contact": {
    "name": "John Smith",
    "title": "Procurement Manager",
    "seniority": "中高层（能决策型号选择和供应商筛选）",
    "language": "英语（尼日利亚英语）",
    "source": "邮件签名（直接确认）"
  },
  "purchase_signals": {
    "intent_level": "medium",
    "urgency": "medium",
    "price_sensitivity": "high",
    "quality_focus": "medium",
    "repeat_likelihood": "medium（可能是首次询此类产品）",
    "source": "根据邮件语气 + 公司规模推断（中置信度）"
  },
  "reputation": {
    "known_complaints": false,
    "positive_news": true,
    "industry_presence": "有参加本地行业展会",
    "source": "搜索未发现负面信息（低置信度，仅供参考）"
  },
  "confidence": {
    "company_info": "high",
    "contact_info": "confirmed",
    "purchase_signals": "medium",
    "reputation": "low"
  }
}
```

### 3.1 画像字段说明

| 字段 | 说明 | 必填 | 填写规则 |
|------|------|------|---------|
| company.name | 公司名称 | ✅ | 从邮件提取，不编造 |
| company.website | 官网 | ❌ | 未找到时留空，不编造 |
| company.estimated_size | 估算规模 | ❌ | 注明估算依据（如"约20-50人，来源LinkedIn"）|
| company.main_products | 主营产品 | ❌ | 从官网/社交账号获取 |
| company.target_market | 目标市场 | ❌ | 根据公司所在国/出口记录推断 |
| company.market_position | 市场地位 | ❌ | 如实描述，不夸大 |
| company.customer_type | 客户类型 | ✅ | 7 类之一：importer / wholesaler / contractor / distributor / brand / ecommerce / end-user |
| contact.name | 联系人姓名 | ✅ | 从邮件提取 |
| contact.title | 联系人职位 | ❌ | 未找到时留空 |
| contact.seniority | 决策层级判断 | ❌ | 根据职位和公司规模判断 |
| purchase_signals.* | 采购信号 | ❌ | 根据邮件 + 公司背景综合推断 |
| confidence.* | 各维度置信度 | ✅ | high / medium / low / confirmed / unconfirmed |

### 3.2 置信度标注规则

```markdown
- **confirmed** — 直接来自邮件签名/官网（100% 可靠）
- **high** — 多方来源交叉验证，无矛盾
- **medium** — 单一来源，或逻辑推断合理
- **low** — 推测，或来源不可靠
- **unconfirmed** — 未找到相关信息，标记空白
```

**重要规则：**
- 任何时候不要编造信息。如果搜索无结果，就写 `unconfirmed`
- 如果信息不确定，必须标注置信度
- 带 `low` 或 `unconfirmed` 的信源信息**不能**作为定价、交期等敏感决策的依据
- 输出格式统一为 JSON 结构，方便后续程序化处理

---

## 4. 增强意图识别规则 | Enhanced Intent Recognition

生成客户画像简报后，将其注入引擎的以下环节：

### 4.1 客户意图分析增强（原来只看文字）

```
之前："客户说价格太高 → 是价格异议"
之后："客户说价格太高 + 已知是西非分销商，年采购约50万美金，经常比价
       → 不是最终用户投诉，而是分销商在测试供应商价格体系
       → 沟通策略：解释配置差异，提供经济款对比，保持长期合作窗口"
```

增强规则：

**已知客户是 Distributor：**
- 重点看利润空间、产品线广度、市场支持
- 压价时 → 解释价格构成，而非"质量好所以贵"
- 关注 MOQ 和备货周期

**已知客户是 End User：**
- 重点看应用场景、安装条件、使用环境
- 压价时 → 解释为什么他的应用需要这个配置
- 关注安装指导和售后支持

**已知客户是 Contractor：**
- 重点看项目参数、交期、质保
- 关注技术规格的完整性
- 提醒用户提供技术方案参考

**已知客户是 Importer：**
- 重点看稳定供货、价格体系、认证、OEM 可能性
- 压价时 → 用数量谈判，而非单次降价
- 关注长期合作框架

### 4.2 风险提示增强

```
之前："不要立即降价"
之后："不要立即降价 + 该公司已知是比价型采购商，建议使用配置对比策略"
```

| 情境 | 增强风险提示 |
|------|-------------|
| 对方是大公司（500+人）| 注意他们的采购流程可能有多轮谈判和法务审核 |
| 对方是小公司（<20人）| 注意付款能力和信用风险 |
| 对方来自低外汇储备国家 | 注意付款风险，建议 TT 预付或 LC |
| 对方有投诉历史（如能查到） | 注意售后条款应更严格，保留质量争议仲裁权 |
| 联系人是 Owner / Director | 可直接做决策，沟通效率可能更高 |
| 联系人是 Purchasing Agent | 可能正在比价，注意不要过早暴露底价 |

### 4.3 沟通策略增强

根据画像定制沟通策略：

| 画像特征 | 策略调整 |
|---------|---------|
| Distributor | 强调利润空间、市场保护、产品线完整度、补货效率 |
| End User | 强调应用场景、使用案例、安装支持、质保服务 |
| Contractor | 强调参数匹配、交期可靠、项目经验、技术方案 |
| New customer | 建立信任为主，提供小样或较低 MOQ 试探 |
| Repeat/large customer | 维护关系为主，提供阶梯价格或专属支持 |

### 4.4 英文回复增强

根据联系人级别调整语气和内容：

```
联系人是 Owner/CEO：
  → 直接、简洁、决策导向
  → "可以"就是可以，不要说"we will try our best"

联系人是 Engineer/Technical：
  → 关注技术参数、标准、认证
  → 提供 Datasheet 和技术文档

联系人是 Procurement：
  → 关注价格、交期、MOQ、付款条件
  → 提供报价比较和数量折扣
```

---

## 5. 输出示例

当加载本层后，引擎的标准 7 段式输出中，第 2~4 段会被增强：

**【0. 客户画像简报】** ← 新增段落，仅在加载本层后出现
```
> 客户画像简报（由 TradePilot Customer Intelligence Layer 生成）
> 公司：ABC Pumps Ltd | 官网：www.abc-pumps.com
> 规模：中型（约50人）| 类型：西非水泵分销商
> 联系人：John Smith（采购经理 | 中高层决策者）
> 采购信号：中等意图，高价格敏感度，已知比价型采购商
> 置信度：公司信息 high | 联系人 confirmed | 采购信号 medium
```

**【1. 场景判断】** ↔ 不变

**【2. 客户意图】** ← 增强
```
之前版本：客户可能是在询问价格信息。
增强版本：作为西非水泵分销商，John Smith 很可能在测试新供应商的价格体系，
判断是否值得引入其产品线。高价格敏感度暗示已有亚洲供应商在供货。
建议策略：解释配置差异和贸易条款，提供经济款对比方案，而非直接降价。
```

**【3. 风险提示】** ← 增强
```
之前版本：不要直接降价。
增强版本：不要直接降价。采购经理级别意味着他可能同时在询价多家供应商，
过早降价会暴露价格空间。建议用配置对比策略守住底价。
```

**【4. 沟通策略】** ← 增强
```
之前版本：向客户解释质量差异。
增强版本：对分销商客户，重点解释：
1. 该配置的利润空间优势（分销商关注）
2. 供货稳定性和备件支持（西非市场关键需求）
3. 提供经济款 / 标准款的配置对比表
4. 首单可建议标准 MOQ 以降低试单门槛
```

---

## 6. 付费门控机制 | Paywall Gating

### 6.1 本地测试（免费）

在本地测试阶段，本层指令集成在引擎提示词中，AI 使用内置的 `web_search` / `web_fetch` 工具执行搜索。能力受限于 AI 自身的搜索范围，适合效果验证。

### 6.2 API 付费（生产）

> **此内容在免费/开源版本中作为软性提示存在，但搜索深度受限。**
> **付费用户通过 TradePilot API 获得完整的客户背景调查能力：**

- 专用搜索引擎调用（Firecrawl 付费版、Exa Search API 等）
- 多语言深度搜索（同时搜索英/中/本地语言）
- 结构化 JSON 画像完整返回
- 历史客户数据积累（同一客户再次查询时直接命中缓存）
- 进口数据/海关数据对接（按可用源）

付费版本的用户只需要调用：
```
POST https://api.tradepilot.mobi/v1/customer-intel
{
  "email_text": "...",
  "industry_pack": "water_pump"  // optional
}

Response:
{
  "profile_brief": { ... },  // 结构化画像
  "enhanced_reply": { ... }  // 增强后的7段式回复
}
```

API 门控逻辑：
- 无 API key → 仅通用引擎（当前免费版）
- 有 API key → 激活 CI 层 → 生成画像简报 → 增强 7 段式输出
- API 请求按次计费，或月度订阅

---

## 版本历史

| 版本 | 日期 | 变更说明 |
|------|------|---------|
| 1.0.0 | 2026-05-07 | 初版：信号提取 + 多语言搜索 + 画像简报格式 + 增强推理规则 |
