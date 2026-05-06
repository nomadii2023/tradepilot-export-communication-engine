# TradePilot 外贸英文沟通引擎
# TradePilot Export Communication Engine

> **开源通用内核，付费行业包与公司定制包。**
> **Open-source core. Premium industry packs. Custom company communication systems.**

一个专为外贸从业者设计的结构化沟通引擎。基于场景判断、客户意图分析、商业风险识别和沟通策略，帮助外贸团队生成实用、能成交的英文回复。
A structured communication engine for exporters. It helps foreign trade teams generate practical, deal-closing English replies based on scenario judgment, customer intent analysis, commercial risk awareness, and communication strategy.

**这不是翻译提示词。这是一个场景驱动的外贸沟通框架。**
**This is NOT a translation prompt. It is a scenario-driven export communication framework.**

---

## 它能做什么 | What It Does

- 识别常见外贸沟通场景（10 大核心场景）| Identify common foreign trade communication scenarios (10 core scenarios)
- 分析客户消息背后的真实意图 | Analyze customer real intent behind messages
- 检测商业沟通风险 | Detect commercial communication risks
- 生成 WhatsApp 和 Email 双语回复 | Generate WhatsApp and Email replies (dual versions)
- 建议后续跟进动作 | Suggest next-step follow-up actions
- 标注应避免的表达 | Flag expressions to avoid
- 通过**行业包（Industry Pack）**支持行业定制 | Support industry-specific customization through **Industry Packs**
- 通过**公司包（Company Pack）**支持公司定制 | Support company-specific customization through **Company Packs**

---

## 工作原理 | How It Works

引擎根据加载的 Pack 以三种模式运行：
The engine operates in three modes based on loaded packs:

| 模式 Mode | 说明 Description | 你将得到 What You Get |
|-----------|-----------------|----------------------|
| **通用模式 Generic Mode** | 未加载任何 Pack | 通用外贸逻辑，可用但无行业深度 |
| **行业包模式 Industry Pack Mode** | 加载 Industry Pack | 增强技术准确性、行业术语、专业谈判逻辑 |
| **公司包模式 Company Pack Mode** | 加载 Company Pack | 全公司适配：真实产品、真实价格、真实政策、品牌语气 |

### 通用模式（免费 — 本仓库包含）| Generic Mode (Free — included in this repo)

```
客户说："Your price is too high."
引擎：识别价格异议 → 警告不要立即降价 → 生成通用价格谈判回复
Customer says: "Your price is too high."
Engine: Identifies price objection → warns not to lower immediately → generates generic price negotiation reply
```

### 行业包模式（付费）| Industry Pack Mode (Premium)

```
客户说："Your pump price is too high."
引擎：识别价格异议 → 加载水泵行业包 → 解释电机绕组、机械密封、抗沙能力、连续工作设计 → 生成行业专用回复
Engine: Identifies price objection → loads Water Pump Industry Pack → explains motor winding, mechanical seal, sand resistance, continuous-duty design → generates industry-specific reply
```

### 公司包模式（付费）| Company Pack Mode (Premium)

```
客户说："Your pump price is too high."
引擎：识别价格异议 → 加载公司包 → 引用真实型号参数、真实质保政策、公司最低价格 → 在政策红线内生成公司专用回复
Engine: Identifies price objection → loads Company Pack → references actual model specs, real warranty policy, company's minimum price → generates company-specific reply within policy red lines
```

---

## 核心场景 | Core Scenarios

引擎覆盖 10 个外贸核心沟通场景：
The engine covers 10 essential foreign trade communication scenarios:

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
Every reply follows a fixed 7-section structure:

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

## 仓库结构 | Repository Structure

```
tradepilot-export-communication-engine/
│
├── README.md                          ← 当前文件 | You are here
├── LICENSE
│
├── core/                               ← 核心引擎（框架）| Core Engine (the framework)
│   ├── core_engine_prompt.md          ← 主提示词 — 以此为基底 | Main prompt — use this as your base
│   └── output_format.md               ← 输出结构参考 | Output structure reference
│
├── schemas/                            ← Pack 模板（定制标准）| Pack Templates (standards for customization)
│   ├── industry_pack_template.md      ← 如何构建 Industry Pack
│   ├── company_pack_template.md       ← 如何构建 Company Pack
│   └── case_pack_template.md         ← 如何构建 Case Pack
│
├── demo_packs/                         ← 示例 Pack（浅层，仅作参考）| Demo Packs (shallow, for reference only)
│   └── general_trading_demo_pack.md  ← 通用贸易示例（非行业专用）
│
├── examples/                           ← 使用案例 | Usage Examples
│   ├── price_objection_example.md     ← 引擎如何处理价格异议
│   ├── complaint_handling_example.md  ← 引擎如何处理投诉
│   └── inquiry_reply_example.md      ← 引擎如何处理模糊询盘
│
├── premium/                            ← 付费内容 | Premium (paid) content
│   └── README.md                      ← 付费产品目录 | What's available as premium
│
└── docs/                               ← 文档 | Documentation
    ├── overview.md                    ← 系统工作原理 | How the system works
    ├── pack-system.md                 ← Pack 系统说明 | How the Pack system works
    ├── customization-guide.md         ← 分步定制指南 | Step-by-step customization guide
    └── comparison.md                  ← 免费 vs 付费对比 | Free vs Premium comparison
```

---

## 快速开始 | Quick Start

### 方式一：直接作为提示词使用 | Option 1: Use as a Prompt Directly

1. 复制 `core/core_engine_prompt.md` 的全部内容 | Copy the content of `core/core_engine_prompt.md`
2. 粘贴到你的 AI 工具（ChatGPT、Claude、WorkBuddy 等）作为系统提示词或自定义指令 | Paste it into your AI tool as a system prompt or custom instruction
3. 开始发送客户消息 — 引擎将以通用模式响应 | Start sending customer messages — the engine will respond in Generic Mode

### 方式二：配合 WorkBuddy Skill 使用 | Option 2: Use with WorkBuddy Skill

如果你使用 [WorkBuddy](https://www.codebuddy.cn)，核心引擎已作为 Skill 提供。它会自动检测已加载的 Pack 并切换模式。
If you use [WorkBuddy](https://www.codebuddy.cn), the core engine is available as a skill. It will automatically detect loaded packs and switch modes.

### 方式三：构建 Custom GPT | Option 3: Build a Custom GPT

以 `core/core_engine_prompt.md` 作为 Custom GPT 的基础指令，然后将你的 Industry Pack 和 Company Pack 内容添加到 Knowledge 区域。
Use `core/core_engine_prompt.md` as the base instruction for a Custom GPT. Then add your Industry Pack and Company Pack content to the Knowledge section.

---

## Pack 系统 | Pack System

核心引擎是通用的。它的真正力量来自 Pack。
The core engine is generic. Its real power comes from Packs.

### 什么是 Pack？| What is a Pack?

Pack 是一个结构化知识文件，用行业专用或公司专用的沟通智能扩展核心引擎。
A Pack is a structured knowledge file that extends the core engine with industry-specific or company-specific communication intelligence.

### Pack 类型 | Types of Packs

| Pack 类型 Pack Type | 用途 Purpose | 适用对象 Who Needs It |
|---------------------|-------------|----------------------|
| **Industry Pack（行业包）** | 行业术语、技术参数、谈判逻辑、诊断问题 | 任何在特定行业销售的人 |
| **Company Pack（公司包）** | 真实产品规格、付款条款、质保政策、品牌语气、内部红线 | 希望团队沟通一致的公司 |
| **Case Pack（案例包）** | 真实客户案例研究（已匿名化）用于培训 | 希望从经验中学习的销售团队 |

### 如何创建 Pack | How to Create a Pack

使用 `schemas/` 中的模板：
Use the templates in `schemas/`:
- `industry_pack_template.md` — 按照此模板构建 Industry Pack
- `company_pack_template.md` — 按照此模板构建 Company Pack
- `case_pack_template.md` — 按照此模板构建 Case Pack

### 示例 Pack | Demo Pack

`demo_packs/` 中包含 `general_trading_demo_pack.md` 作为参考。它展示了结构，但有意缺乏行业深度。
A `general_trading_demo_pack.md` is included in `demo_packs/` as a reference. It shows the structure but intentionally lacks industry depth.

---

## 免费 vs 付费 | Free vs Premium

| 功能 Feature | 免费（本仓库）Free (This Repo) | 付费（需购买）Premium (Paid) |
|-------------|-------------------------------|-------------------------------|
| 核心场景判断 Core scenario judgment | ✅ | ✅ |
| 通用英文回复 Generic English replies | ✅ | ✅ |
| WhatsApp / Email 双版本 | ✅ | ✅ |
| 基础风险提示 Basic risk alerts | ✅ | ✅ |
| Pack 系统支持 Pack system support | ✅ | ✅ |
| 行业专业术语 Industry-specific terminology | 仅示例 Demo only | 完整 Full |
| 技术参数指导 Technical parameter guidance | 通用 Generic | 行业专用 Industry-specific |
| 售后诊断问题 After-sales diagnostic questions | 通用 Generic | 产品专用 Product-specific |
| 价格异议逻辑 Price objection logic | 通用 Generic | 配置专用 Configuration-specific |
| 公司优势表达 Company advantage expression | ❌ | ✅ |
| 付款/质保红线 Payment/warranty red lines | ❌ | ✅ |
| 真实案例研究 Real case studies | ❌ | ✅ |
| 团队统一沟通 Team unified communication | ❌ | ✅ |
| 输出调优/校准 Output tuning / calibration | ❌ | ✅ |

> 公开核心引擎专为通用外贸沟通设计。**实际商业使用需要行业专用和公司专用 Pack。**
> The public core engine is designed for generic foreign trade communication. **For real business use, industry-specific and company-specific packs are required.**

---

## 可用付费 Pack | Available Premium Packs

以下付费 Pack 可供选购：
The following premium packs are available:

- 水泵行业沟通包 Water Pump Industry Communication Pack
- 柴油发电机组行业沟通包 Diesel Generator Industry Communication Pack
- 定制行业包（任意产品品类）Custom Industry Pack (any product category)
- 公司/产品沟通包（为你的业务定制）Company/Product Communication Pack (customized for your business)
- 客户案例包（基于真实客户互动）Customer Case Pack (from your real customer interactions)
- 团队培训版（含校准与支持）Team Training Version (with calibration and support)

如需购买付费 Pack 和定制服务，访问 [TradePilot.mobi](https://tradepilot.mobi)
For premium packs and customization services, visit [TradePilot.mobi](https://tradepilot.mobi)

---

## 如何定制 | How to Customize

详见 `docs/customization-guide.md` 获取创建自定义 Pack 的分步指南。
See `docs/customization-guide.md` for a step-by-step guide on creating your own packs.

### 快速路径 | Quick Path

1. 复制 `schemas/industry_pack_template.md` | Copy `schemas/industry_pack_template.md`
2. 填写你所在行业的产品术语、关键参数、价格异议因素 | Fill in your industry's product terminology, key parameters, price objection factors
3. 与 `core/core_engine_prompt.md` 组合使用 | Combine with `core/core_engine_prompt.md`
4. 开始使用 — 引擎将自动切换至行业包模式 | Start using — the engine will automatically switch to Industry Pack Mode

### 完整路径 | Full Path

1. 创建 Industry Pack（根据模板）| Create Industry Pack (from template)
2. 创建 Company Pack（根据模板）| Create Company Pack (from template)
3. 根据真实客户互动创建 Case Pack（根据模板）| Create Case Pack from real customer interactions (from template)
4. 将所有 Pack 与核心引擎一起加载 | Load all packs with the Core Engine
5. 用团队真实客户消息测试 | Test with your team's real customer messages
6. 迭代改进 | Iterate and improve

---

## License | 许可证

- **核心引擎与框架 Core Engine and Framework：** MIT License
- **Pack 模板与示例内容 Pack Templates and Demo Content：** CC BY-NC 4.0（非商业用途）
- **付费 Pack Premium Packs：** 私有商业资产 — 不包含在本仓库中

详见 [LICENSE](LICENSE)。
See [LICENSE](LICENSE) for details.

---

## 贡献 | Contributing

这是一个开源框架。欢迎贡献：
This is an open-source framework. Contributions are welcome:

- 核心引擎的 Bug 修复和改进 | Bug fixes and improvements to the Core Engine
- 新语言包（西班牙语、法语、阿拉伯语等）| New language packs (Spanish, French, Arabic, etc.)
- 新示例场景 | New example scenarios
- 文档改进 | Documentation improvements

---

## 关于 TradePilot | About TradePilot

TradePilot 是一个面向外贸企业的 AI 驱动 B2B 客户情报与触达平台。我们结合 AI 驱动的客户挖掘、沟通智能和销售工作流自动化。
TradePilot is an AI-powered B2B customer intelligence and outreach platform for foreign trade businesses. We combine AI-driven lead discovery, communication intelligence, and sales workflow automation.

- 官网 Website: [TradePilot.mobi](https://tradepilot.mobi)
- 微信公众号 WeChat Official Account: [外贸AI实战录](https://mp.weixin.qq.com) (Foreign Trade AI in Practice)

---

## 一句话总结 | One-Line Summary

> **TradePilot 外贸英文沟通引擎：开源通用内核，付费行业包与公司定制包。**
> **TradePilot Export Communication Engine: Open-source core, premium industry packs, custom company communication systems.**
