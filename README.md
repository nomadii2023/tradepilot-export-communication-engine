# TradePilot Export Communication Engine

> **Open-source core. Premium industry packs. Custom company communication systems.**

A structured communication engine for exporters. It helps foreign trade teams generate practical, deal-closing English replies based on scenario judgment, customer intent analysis, commercial risk awareness, and communication strategy.

This is **not** a translation prompt. It is a **scenario-driven export communication framework**.

---

## What It Does

- Identify common foreign trade communication scenarios (10 core scenarios)
- Analyze customer real intent behind messages
- Detect commercial communication risks
- Generate WhatsApp and Email replies (dual versions)
- Suggest next-step follow-up actions
- Flag expressions to avoid
- Support industry-specific customization through **Industry Packs**
- Support company-specific customization through **Company Packs**

---

## How It Works

The engine operates in three modes based on loaded packs:

| Mode | Description | What You Get |
|------|-------------|-------------|
| **Generic Mode** | No pack loaded | General trade logic, usable but not industry-specific |
| **Industry Pack Mode** | Industry Pack loaded | Enhanced technical accuracy, industry terminology, specialized negotiation logic |
| **Company Pack Mode** | Company Pack loaded | Full company adaptation: real products, real prices, real policies, brand voice |

### Generic Mode (Free — included in this repo)

```
Customer says: "Your price is too high."
Engine: Identifies price objection → warns not to lower immediately → generates generic price negotiation reply
```

### Industry Pack Mode (Premium)

```
Customer says: "Your pump price is too high."
Engine: Identifies price objection → loads Water Pump Industry Pack → explains motor winding, mechanical seal, sand resistance, continuous-duty design → generates industry-specific reply
```

### Company Pack Mode (Premium)

```
Customer says: "Your pump price is too high."
Engine: Identifies price objection → loads Company Pack → references actual model specs, real warranty policy, company's minimum price → generates company-specific reply within policy red lines
```

---

## Core Scenarios

The engine covers 10 essential foreign trade communication scenarios:

1. **Cold Outreach** — First contact with potential customers
2. **Inquiry Reply** — Responding to product inquiries
3. **Quotation Explanation** — Explaining pricing and terms
4. **Product Recommendation** — Recommending the right product
5. **Technical Confirmation** — Avoiding production errors
6. **Order Confirmation** — Preventing order misunderstandings
7. **Payment & Delivery** — Cash flow and delivery rhythm
8. **After-Sales Complaint** — Handling claims without escalating
9. **Contract & Terms** — Defining liability boundaries
10. **Company/Product Profile** — Building trust and brand image

---

## Output Structure

Every reply follows a fixed 7-section structure:

```
[1. Scenario Judgment]     — What scenario is this?
[2. Customer Intent]       — What does the customer really want?
[3. Risk Alert]            — What should you avoid?
[4. Communication Strategy]— How should you approach this?
[5. English Replies]       — WhatsApp + Email (and Stronger version when needed)
[6. Next Steps]            — What to do after the customer replies
[7. Avoid Saying This]     — Expressions that hurt your position
```

---

## Repository Structure

```
tradepilot-export-communication-engine/
│
├── README.md                          ← You are here
├── LICENSE
│
├── core/                              ← Core Engine (the framework)
│   ├── core_engine_prompt.md          ← Main prompt — use this as your base
│   └── output_format.md               ← Output structure reference
│
├── schemas/                           ← Pack Templates (standards for customization)
│   ├── industry_pack_template.md      ← How to build an Industry Pack
│   ├── company_pack_template.md       ← How to build a Company Pack
│   └── case_pack_template.md          ← How to build a Case Pack
│
├── demo_packs/                        ← Demo Packs (shallow, for reference only)
│   └── general_trading_demo_pack.md   ← General trading demo (not industry-specific)
│
├── examples/                          ← Usage Examples
│   ├── price_objection_example.md     ← How the engine handles price objections
│   ├── complaint_handling_example.md  ← How the engine handles complaints
│   └── inquiry_reply_example.md       ← How the engine handles vague inquiries
│
├── premium/                           ← Premium (paid) content
│   └── README.md                      ← What's available as premium
│
└── docs/                              ← Documentation
    ├── overview.md                    ← How the system works
    ├── pack-system.md                 ← How the Pack system works
    ├── customization-guide.md         ← Step-by-step customization guide
    └── comparison.md                  ← Free vs Premium comparison
```

---

## Quick Start

### Option 1: Use as a Prompt Directly

1. Copy the content of `core/core_engine_prompt.md`
2. Paste it into your AI tool (ChatGPT, Claude, WorkBuddy, etc.) as a system prompt or custom instruction
3. Start sending customer messages — the engine will respond in Generic Mode

### Option 2: Use with WorkBuddy Skill

If you use [WorkBuddy](https://www.codebuddy.cn), the core engine is available as a skill. It will automatically detect loaded packs and switch modes.

### Option 3: Build a Custom GPT

Use `core/core_engine_prompt.md` as the base instruction for a Custom GPT. Then add your Industry Pack and Company Pack content to the Knowledge section.

---

## Pack System

The core engine is generic. Its real power comes from Packs.

### What is a Pack?

A Pack is a structured knowledge file that extends the core engine with industry-specific or company-specific communication intelligence.

### Types of Packs

| Pack Type | Purpose | Who Needs It |
|-----------|---------|-------------|
| **Industry Pack** | Industry terminology, technical parameters, negotiation logic, diagnostic questions | Anyone selling in a specific industry |
| **Company Pack** | Real product specs, payment terms, warranty policy, brand voice, internal red lines | Companies wanting team-wide communication consistency |
| **Case Pack** | Real customer case studies (anonymized) for training | Sales teams wanting to learn from experience |

### How to Create a Pack

Use the templates in `schemas/`:
- `industry_pack_template.md` — Follow this to build an Industry Pack
- `company_pack_template.md` — Follow this to build a Company Pack
- `case_pack_template.md` — Follow this to build a Case Pack

### Demo Pack

A `general_trading_demo_pack.md` is included in `demo_packs/` as a reference. It shows the structure but intentionally lacks industry depth.

---

## Free vs Premium

| Feature | Free (This Repo) | Premium (Paid) |
|---------|:---:|:---:|
| Core scenario judgment | Yes | Yes |
| Generic English replies | Yes | Yes |
| WhatsApp / Email dual versions | Yes | Yes |
| Basic risk alerts | Yes | Yes |
| Pack system support | Yes | Yes |
| Industry-specific terminology | Demo only | Full |
| Technical parameter guidance | Generic | Industry-specific |
| After-sales diagnostic questions | Generic | Product-specific |
| Price objection logic | Generic | Configuration-specific |
| Company advantage expression | No | Yes |
| Payment/warranty red lines | No | Yes |
| Real case studies | No | Yes |
| Team unified communication | No | Yes |
| Output tuning / calibration | No | Yes |

> The public core engine is designed for generic foreign trade communication. **For real business use, industry-specific and company-specific packs are required.**

---

## Available Premium Packs

The following premium packs are available:

- Water Pump Industry Communication Pack
- Diesel Generator Industry Communication Pack
- Custom Industry Pack (any product category)
- Company/Product Communication Pack (customized for your business)
- Customer Case Pack (from your real customer interactions)
- Team Training Version (with calibration and support)

For premium packs and customization services, visit [TradePilot.mobi](https://tradepilot.mobi)

---

## How to Customize

See `docs/customization-guide.md` for a step-by-step guide on creating your own packs.

### Quick Path

1. Copy `schemas/industry_pack_template.md`
2. Fill in your industry's product terminology, key parameters, price objection factors
3. Combine with `core/core_engine_prompt.md`
4. Start using — the engine will automatically switch to Industry Pack Mode

### Full Path

1. Create Industry Pack (from template)
2. Create Company Pack (from template)
3. Create Case Pack from real customer interactions (from template)
4. Load all packs with the Core Engine
5. Test with your team's real customer messages
6. Iterate and improve

---

## License

- **Core Engine and Framework:** MIT License
- **Pack Templates and Demo Content:** CC BY-NC 4.0 (non-commercial)
- **Premium Packs:** Private commercial assets — not included in this repository

See [LICENSE](LICENSE) for details.

---

## Contributing

This is an open-source framework. Contributions are welcome:

- Bug fixes and improvements to the Core Engine
- New language packs (Spanish, French, Arabic, etc.)
- New example scenarios
- Documentation improvements

Please note: Industry Packs and Company Packs with real commercial value should NOT be submitted as pull requests — they are premium assets.

---

## About TradePilot

TradePilot is an AI-powered B2B customer intelligence and outreach platform for foreign trade businesses. We combine AI-driven lead discovery, communication intelligence, and sales workflow automation.

- Website: [TradePilot.mobi](https://tradepilot.mobi)
- WeChat: [外贸AI实战录](https://mp.weixin.qq.com) (Foreign Trade AI in Practice)

---

## One-Line Summary

> **TradePilot Export Communication Engine: Open-source core, premium industry packs, custom company communication systems.**
>
> **开源通用内核，付费行业包与公司定制包。**
