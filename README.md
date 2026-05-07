<p align="center">
  <h1 align="center">TradePilot Export Communication Engine</h1>
  <p align="center">
    <strong>开源外贸询盘 AI 沟通引擎</strong><br>
    <em>Open-Source AI Communication Engine for Foreign Trade Inquiries</em>
  </p>
  <p align="center">
    <a href="https://engine.tradepilot.mobi/">🌐 官网 Landing Page</a> &nbsp;·&nbsp;
    <a href="https://github.com/nicetomeetyou/tradepilot-export-communication-engine">⭐ GitHub</a> &nbsp;·&nbsp;
    <a href="https://www.tradepilot.mobi/">💼 付费服务</a>
  </p>
  <p align="center">
    <b>通用基础版永久免费</b> &nbsp;|&nbsp; <b>行业专业包 + 企业定制包 付费解锁</b>
  </p>
</p>

---

## 项目简介 | About

TradePilot 是面向**外贸业务员、SOHO、工厂外贸部**的 AI 询盘自动解析与邮件回复引擎。封装为标准 Skill，可一键安装到 WorkBuddy / OpenClaw 生态，自动处理海外客户询价邮件：

- 自动拆解询盘需求：产品、数量、目标价、交期、客户意向
- 通用版生成标准英文回复模板
- 加载行业包后：自动匹配行业术语、产品参数、专业谈判话术
- 加载企业定制包：内置自家报价底线、质保条款、成交逻辑

**这不是翻译提示词。这是一个场景驱动的外贸沟通框架。**
**This is NOT a translation prompt. It is a scenario-driven export communication framework.**

---

## 核心特性 | Key Features

- **场景驱动** — 覆盖 10 大外贸核心沟通场景（询盘、报价、议价、投诉、合同等）
- **智能拆解** — 自动识别场景、分析客户真实意图、检测商业风险
- **双语输出** — 每次生成 WhatsApp + Email 双版本英文回复
- **7 段式结构** — 场景判断 → 意图分析 → 风险提示 → 沟通策略 → 英文回复 → 后续步骤 → 避坑指南
- **模块化 Pack 系统** — 通用内核 + 可插拔行业包 + 企业定制包
- **隐私安全** — 纯本地 + API 双模式，不泄露商业询盘
- **原生适配** — WorkBuddy / OpenClaw 一键安装，也支持 ChatGPT Custom GPT、Claude 等
- **持续迭代** — 开源内核永久更新，行业包持续扩充

---

## 适用人群 | Who It's For

| 角色 | 痛点 | TradePilot 解决方案 |
|------|------|---------------------|
| 外贸 SOHO | 一个人包揽全部，询盘回复效率低 | AI 秒级拆解询盘，生成专业英文回复 |
| 工厂外贸部 | 业务员英语水平参差不齐 | 引擎统一输出标准，降低人为差错 |
| 跨境业务员 | 每天处理大量询盘，应接不暇 | 自动解析 + 批量回复建议 |
| 外贸团队管理者 | 团队对外口径不一致 | 企业包统一品牌语气和报价红线 |
| AI 自动化实践者 | 想落地 AI 邮件处理 | 开源内核可直接集成、二次开发 |

---

## 适用行业 | Industries

覆盖**全外贸品类**，已有深度行业包的领域：

> 水泵 / 柴油发电机组 / 五金制品 / 3C 电子 / 家居用品 / 玩具礼品 / 医疗器械 / 家电 / 建材 / 农业机械 ...
>
> 未列出的行业可**定制开发专属行业包**（详见下方付费服务）

---

## 三种运行模式 | Three Operating Modes

引擎根据加载的 Pack 以三种模式运行：

| 模式 Mode | 说明 Description | 你将得到 What You Get |
|-----------|-----------------|----------------------|
| **通用模式 Generic Mode** | 未加载任何 Pack（免费） | 通用外贸逻辑，可用但无行业深度 |
| **行业包模式 Industry Pack Mode** | 加载 Industry Pack（付费） | 增强技术准确性、行业术语、专业谈判逻辑 |
| **公司包模式 Company Pack Mode** | 加载 Company Pack（付费） | 全公司适配：真实产品、真实价格、真实政策、品牌语气 |

### 通用模式（免费 — 本仓库包含）

```
客户说："Your price is too high."
引擎：识别价格异议 → 警告不要立即降价 → 生成通用价格谈判回复
Customer says: "Your price is too high."
Engine: Identifies price objection → warns not to lower immediately → generates generic price negotiation reply
```

### 行业包模式（付费）

```
客户说："Your pump price is too high."
引擎：识别价格异议 → 加载水泵行业包 → 解释电机绕组、机械密封、抗沙能力、连续工作设计 → 生成行业专用回复
Engine: Identifies price objection → loads Water Pump Industry Pack → explains motor winding, mechanical seal, sand resistance, continuous-duty design → generates industry-specific reply
```

### 公司包模式（付费）

```
客户说："Your pump price is too high."
引擎：识别价格异议 → 加载公司包 → 引用真实型号参数、真实质保政策、公司最低价格 → 在政策红线内生成公司专用回复
Engine: Identifies price objection → loads Company Pack → references actual model specs, real warranty policy, company's minimum price → generates company-specific reply within policy red lines
```

---

## 10 大核心场景 | Core Scenarios

| # | 场景 Scene | 说明 Description |
|---|------------|-----------------|
| 1 | **首次开发 Cold Outreach** | 与潜在客户的首次接触 |
| 2 | **询盘回复 Inquiry Reply** | 回复产品询盘 |
| 3 | **报价说明 Quotation Explanation** | 解释定价和条款 |
| 4 | **产品推荐 Product Recommendation** | 推荐合适产品 |
| 5 | **技术确认 Technical Confirmation** | 避免生产错误 |
| 6 | **订单确认 Order Confirmation** | 防止订单误解 |
| 7 | **付款与发货 Payment & Delivery** | 现金流与发货节奏 |
| 8 | **售后投诉 After-Sales Complaint** | 处理索赔而不升级 |
| 9 | **合同与条款 Contract & Terms** | 界定责任边界 |
| 10 | **公司/产品介绍 Company/Product Profile** | 建立信任与品牌形象 |

---

## 输出结构 | Output Structure

每条回复遵循固定的 7 段式结构：

```
[1. 场景判断 Scenario Judgment]      — 这是什么场景？
[2. 客户意图 Customer Intent]        — 客户真正想要什么？
[3. 风险提示 Risk Alert]             — 应该避免什么？
[4. 沟通策略 Communication Strategy]  — 应该如何应对？
[5. 英文回复 English Replies]        — WhatsApp + Email（需要时附加强硬版本）
[6. 后续步骤 Next Steps]            — 客户回复后该做什么？
[7. 避免这样说 Avoid Saying This]    — 哪些表达会损害你的立场？
```

---

## 免费版 VS 付费版 | Free vs Premium

| 功能 Feature | 免费通用版 Free | 行业专业包 Industry Pack | 企业定制包 Company Pack |
|-------------|:---:|:---:|:---:|
| 核心场景判断 Core scenario judgment | ✅ | ✅ | ✅ |
| 通用英文回复 Generic English replies | ✅ | ✅ | ✅ |
| WhatsApp / Email 双版本 | ✅ | ✅ | ✅ |
| 基础风险提示 Basic risk alerts | ✅ | ✅ | ✅ |
| Pack 系统支持 Pack system support | ✅ | ✅ | ✅ |
| 行业专业术语 Industry terminology | 仅示例 | **完整** | **完整** |
| 技术参数指导 Technical parameters | 通用 | **行业专用** | **产品专用** |
| 售后诊断问题 After-sales diagnostics | 通用 | **产品专用** | **公司专用** |
| 价格异议逻辑 Price objection logic | 通用 | **配置专用** | **报价红线内** |
| 认证/标准适配 Certifications | ❌ | ✅ | ✅ |
| 区域市场差异 Regional differences | ❌ | ✅ | ✅ |
| 公司优势表达 Company advantages | ❌ | 部分 | **✅ 完全定制** |
| 付款/质保红线 Payment & warranty red lines | ❌ | ❌ | **✅ 严格内置** |
| 真实案例研究 Real case studies | ❌ | ❌ | **✅（可选）** |
| 团队统一沟通口径 Team unified tone | ❌ | ❌ | **✅** |
| 输出调优/校准 Output calibration | ❌ | ❌ | **✅** |

> **一句话总结：** 免费通用版能做「及格回复」，付费版让 AI 像**资深本行业外贸业务员**一样回复。

---

## 为什么需要行业专业包 | Why You Need Industry Packs

免费通用版只能做「及格回复」，容易显得不专业、丢客户。
加载对应行业包后，AI 会像**资深本行业外贸业务员**一样回复：

- 懂**行业专业名词** — 不会把流量说成 flow capacity 然后被客户一眼看穿
- 懂**产品常规参数** — 流量、扬程、功率、电压、材质、防护等级，信手拈来
- 懂**客户常见砍价套路** — 用铜还是用铝？这个价格含不含运费？OEM 有没有 MOQ？
- 懂**行业交期、认证、质保常规说法** — CE / RoHS / ISO / SGS，张口就来
- 懂**区域市场差异** — 中东的电压标准、非洲的物流周期、东南亚的付款习惯

**大幅提升询盘转化率，节省人工整理话术时间。**

---

## 快速开始 | Quick Start

> 🌐 引擎官网 | Engine Landing Page: [engine.tradepilot.mobi](https://engine.tradepilot.mobi/)

### 方式一：直接作为提示词使用 | Option 1: Use as a Prompt Directly

1. Star 本项目，克隆到本地
2. 复制 `core/core_engine_prompt.md` 的全部内容
3. 粘贴到你的 AI 工具（ChatGPT、Claude、WorkBuddy 等）作为系统提示词
4. 直接粘贴外贸询价邮件，即可自动解析并生成回复

### 方式二：配合 WorkBuddy Skill 使用 | Option 2: Use with WorkBuddy Skill

如果你使用 [WorkBuddy](https://www.codebuddy.cn)，核心引擎已作为 Skill 提供。它会自动检测已加载的 Pack 并切换模式。

### 方式三：构建 Custom GPT | Option 3: Build a Custom GPT

以 `core/core_engine_prompt.md` 作为 Custom GPT 的基础指令，然后将 Industry Pack 和 Company Pack 内容添加到 Knowledge 区域。

---

## 仓库结构 | Repository Structure

```
tradepilot-export-communication-engine/
│
├── README.md                          ← 当前文件 | You are here
├── LICENSE
│
├── core/                               ← 核心引擎（框架）| Core Engine
│   ├── core_engine_prompt.md          ← 主提示词 — 以此为基底 | Main prompt
│   └── output_format.md               ← 输出结构参考 | Output structure reference
│
├── schemas/                            ← Pack 模板（定制标准）| Pack Templates
│   ├── industry_pack_template.md      ← 如何构建 Industry Pack
│   ├── company_pack_template.md       ← 如何构建 Company Pack
│   └── case_pack_template.md         ← 如何构建 Case Pack
│
├── demo_packs/                         ← 示例 Pack（浅层参考）| Demo Packs
│   └── general_trading_demo_pack.md  ← 通用贸易示例
│
├── examples/                           ← 使用案例 | Usage Examples
│   ├── price_objection_example.md     ← 价格异议处理示例
│   ├── complaint_handling_example.md  ← 投诉处理示例
│   └── inquiry_reply_example.md      ← 模糊询盘回复示例
│
├── premium/                            ← 付费内容 | Premium content
│   ├── README.md                      ← 付费产品目录
│   └── water_pump_industry_pack.md   ← 水泵行业沟通包（示例）
│
└── docs/                               ← 文档 | Documentation
    ├── overview.md                    ← 系统工作原理
    ├── pack-system.md                 ← Pack 系统说明
    ├── customization-guide.md         ← 分步定制指南
    └── comparison.md                  ← 免费 vs 付费对比
```

---

## Pack 系统 | Pack System

核心引擎是通用的。它的真正力量来自 Pack。
The core engine is generic. Its real power comes from Packs.

### Pack 类型 | Types of Packs

| Pack 类型 Pack Type | 用途 Purpose | 适用对象 Who Needs It |
|---------------------|-------------|----------------------|
| **Industry Pack（行业包）** | 行业术语、技术参数、谈判逻辑、诊断问题 | 任何在特定行业销售的人 |
| **Company Pack（公司包）** | 真实产品规格、付款条款、质保政策、品牌语气、内部红线 | 希望团队沟通一致的公司 |
| **Case Pack（案例包）** | 真实客户案例研究（已匿名化）用于培训 | 希望从经验中学习的销售团队 |

### 如何创建 Pack | How to Create a Pack

使用 `schemas/` 中的模板：

1. 复制 `schemas/industry_pack_template.md`
2. 填写你所在行业的产品术语、关键参数、价格异议因素
3. 与 `core/core_engine_prompt.md` 组合使用
4. 引擎将自动切换至行业包模式

---

## 可用付费 Pack | Available Premium Packs

| Pack 名称 | 说明 | 状态 |
|-----------|------|------|
| 水泵行业沟通包 Water Pump Industry Pack | 12 类水泵、15+ 技术参数、区域电压标准、售后诊断流程 | ✅ 已发布 |
| 柴油发电机组行业沟通包 Diesel Generator Pack | 发电机组专业术语、功率匹配、排放标准、售后体系 | ✅ 已发布 |
| 定制行业包 Custom Industry Pack | 任意产品品类，按需开发 | 🔄 接受定制 |
| 公司/产品沟通包 Company Pack | 基于你真实业务的一对一定制 | 🔄 接受定制 |
| 客户案例包 Case Pack | 20-50 条匿名化真实案例，团队培训专用 | 🔄 接受定制 |
| 团队培训版 Team Training | 含全套 Pack + 校准 + 培训指导 | 🔄 接受定制 |

---

## 付费服务 & 获取方式 | Premium Services

> 💼 **在售：** 各行业专业包、全行业年度会员、企业私有化定制部署
>
> 👉 获取行业包目录、演示案例、报价及安装指导
>
> 请添加微信：【这里填你微信号】
> 备注：TradePilot
>
> 或访问官网：[TradePilot.mobi](https://www.tradepilot.mobi/)

### 付费包定价逻辑

- **行业专业包** — 按单个行业授权，精准适配本行业客户询盘
- **企业定制包** — 一对一专属定制，仅限本企业内部使用
- **全行业年度会员** — 解锁所有已发布行业包 + 优先获取新包
- **企业私有化部署** — 完整引擎 + 全套 Pack，本地化部署，数据不出企业

> 详细报价请添加微信或访问官网咨询。

---

## 开源声明 | Open Source License

| 内容 | 许可证 |
|------|--------|
| **核心引擎与框架** Core Engine & Framework | MIT License — 完全开源，自由使用 |
| **Pack 模板与示例内容** Pack Templates & Demo Content | CC BY-NC 4.0 — 非商业用途 |
| **付费 Pack** Premium Packs | 私有商业资产 — 禁止二次分发、倒卖、逆向拆解 |

本项目通用内核完全开源，供学习、个人免费使用。行业包、企业定制包为闭源授权产品。

详见 [LICENSE](LICENSE)。

---

## 贡献 | Contributing

这是一个开源框架。欢迎贡献：

- 核心引擎的 Bug 修复和改进
- 新语言包（西班牙语、法语、阿拉伯语等）
- 新示例场景
- 文档改进

---

## 关于 TradePilot | About TradePilot

TradePilot 是一个面向外贸企业的 AI 驱动 B2B 客户情报与触达平台。我们结合 AI 驱动的客户挖掘、沟通智能和销售工作流自动化。
TradePilot is an AI-powered B2B customer intelligence and outreach platform for foreign trade businesses. We combine AI-driven lead discovery, communication intelligence, and sales workflow automation.

- 官网 Website: [TradePilot.mobi](https://www.tradepilot.mobi/)
- 引擎页面 Engine: [engine.tradepilot.mobi](https://engine.tradepilot.mobi/)
- 微信公众号 WeChat: [外贸AI实战录](https://mp.weixin.qq.com)

---

<p align="center">
  <b>TradePilot Export Communication Engine</b><br>
  开源通用内核 · 付费行业包 · 企业定制包<br>
  <em>Open-source core · Premium industry packs · Custom company communication systems</em>
</p>
