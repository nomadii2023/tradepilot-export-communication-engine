# How It Works

> An overview of the TradePilot Export Communication Engine architecture and workflow.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│              TradePilot Communication Engine          │
│                                                       │
│  ┌──────────────────────────────────────────────┐    │
│  │           Core Engine (core_engine_prompt.md)  │    │
│  │                                                │    │
│  │  • 10 Core Scenarios                          │    │
│  │  • 7-Section Output Structure                  │    │
│  │  • Risk Control Rules                          │    │
│  │  • English Style Guidelines                    │    │
│  │  • Customer Type Adaptation                    │    │
│  │  • Regional Market Adaptation                  │    │
│  └────────────────────┬─────────────────────────┘    │
│                       │                              │
│          ┌────────────┼────────────┐                │
│          ▼            ▼            ▼                │
│   ┌──────────┐ ┌──────────┐ ┌──────────┐          │
│   │ Industry │ │ Company  │ │  Case    │          │
│   │   Pack   │ │   Pack   │ │  Pack    │          │
│   │          │ │          │ │          │          │
│   │ Product  │ │ Real     │ │ Real     │          │
│   │ Terms    │ │ Products │ │ Customer │          │
│   │ Params   │ │ Prices   │ │ Stories  │          │
│   │ Diag.    │ │ Policy   │ │ Lessons  │          │
│   │ Logic    │ │ Redlines │ │          │          │
│   └──────────┘ └──────────┘ └──────────┘          │
└─────────────────────────────────────────────────────┘
```

---

## Workflow

### Step 1: Customer Message Arrives

A customer sends a message via WhatsApp, Email, LinkedIn, or a B2B platform.

### Step 2: User Feeds Context to Engine

The user provides:
- Customer's original message (required)
- Product name (recommended)
- Customer country (recommended)
- Customer type (recommended)
- Current trade stage (recommended)
- User's goal (recommended)
- Output channel (recommended)

### Step 3: Engine Identifies Scenario

The engine matches the message against 10 core scenarios:
1. Cold Outreach
2. Inquiry Reply
3. Quotation Explanation
4. Product Recommendation
5. Technical Confirmation
6. Order Confirmation
7. Payment & Delivery
8. After-Sales Complaint
9. Contract & Terms
10. Company/Product Profile

### Step 4: Pack System Activates

Based on loaded packs:
- **No pack** → Generic Mode (general trade logic)
- **Industry Pack** → Industry Pack Mode (enhanced with industry knowledge)
- **Company Pack** → Company Pack Mode (full company adaptation)

### Step 5: Engine Generates Output

The engine produces a structured 7-section response:
1. Scenario Judgment
2. Customer Intent Analysis
3. Risk Alert
4. Communication Strategy
5. English Replies (WhatsApp + Email, plus stronger version if needed)
6. Next Steps
7. Avoid Saying This

### Step 6: User Reviews and Sends

The user reviews the output, adjusts if needed, and sends the reply to the customer.

---

## Mode Detection Logic

```
IF Company Pack is loaded:
    Mode = Company Pack Mode
    Use company's real products, prices, policies, brand voice
    Follow company's internal red lines

ELSE IF Industry Pack is loaded:
    Mode = Industry Pack Mode
    Use industry terminology and parameters
    Apply industry-specific price objection logic
    Use industry-specific diagnostic questions

ELSE:
    Mode = Generic Mode
    Use general trade communication logic
    Display upgrade suggestion in output
```

---

## Design Principles

### 1. Scenario-Driven, Not Translation-Driven

The engine doesn't just translate Chinese to English. It analyzes the business scenario and generates replies designed to advance the deal.

### 2. Risk-Aware

Every output includes risk alerts. The engine proactively warns about common mistakes that cost money, time, or customer relationships.

### 3. Modular by Design

The core engine is deliberately generic. All industry and company specificity comes from Packs. This means:
- The same core works for any industry
- Switching industries only requires changing the Pack
- Company-specific rules don't pollute the generic framework

### 4. Practical, Not Theoretical

All English replies are designed for real use — not textbook examples. They avoid clichés, empty claims, and over-formal language.

### 5. Structured, Not Free-Form

The fixed 7-section output ensures consistency. Every reply covers scenario, intent, risk, strategy, reply, next steps, and things to avoid.

---

## Integration Options

| Platform | How to Use |
|----------|-----------|
| **ChatGPT** | Paste core_engine_prompt.md as Custom Instructions |
| **Claude** | Use as system prompt in a Project |
| **WorkBuddy** | Install as a Skill (auto-detects packs) |
| **Custom GPT** | Set as Instructions, add Packs to Knowledge |
| **API** | Use as system message in API calls |
| **Any LLM** | Paste as system prompt — works with any model |

---

## Limitations

- The engine provides communication guidance, not legal advice
- It cannot verify real product specifications, prices, or certifications
- Company Packs should be reviewed and approved by company management
- The engine's quality depends on the quality of input context
- It is an AI tool — human judgment should always be applied to final output
