# Pack System

> How the TradePilot Pack system works — extending the Core Engine with industry and company intelligence.

---

## What is a Pack?

A Pack is a structured knowledge file (in Markdown format) that extends the TradePilot Core Engine with specific domain intelligence. Think of it as a "knowledge cartridge" that plugs into the engine.

Without Packs, the Core Engine is a solid but generic framework. With Packs, it becomes a business-ready tool tailored to your industry and company.

---

## Pack Types

### 1. Industry Communication Pack

**Purpose:** Add industry-specific product knowledge, technical parameters, and communication patterns.

**What it contains:**
- Product terminology (industry-specific English terms)
- Key technical parameters and their trade significance
- Inquiry reply rules (what to ask before quoting)
- Product recommendation logic (by application scenario)
- Price objection handling (industry-specific cost factors)
- After-sales troubleshooting (diagnostic questions)
- Regional market notes (if applicable)

**Example:** A Water Pump Industry Pack knows that when a customer inquires, you should ask about flow rate, head, power supply, well diameter, and water condition — not just "what pump do you need?"

**Who needs it:** Anyone selling products in a specific industry category.

---

### 2. Company / Product Communication Pack

**Purpose:** Encode a specific company's real business rules, product data, and brand voice.

**What it contains:**
- Real product catalog with specifications and pricing
- Actual payment terms and trade conditions
- Warranty and after-sales policy
- MOQ, lead time, and shipping rules
- Brand voice and tone guidelines
- Internal red lines (things the team must NEVER promise)
- OEM/ODM capabilities
- Standard answers to common customer questions

**Example:** A Company Pack for "ABC Pump Factory" would know that their standard payment is T/T 30/70, they never accept O/A for first orders, their warranty is 12 months, and their red line is never promising CE certification if they don't actually have it.

**Who needs it:** Companies that want consistent, policy-compliant communication across their sales team.

---

### 3. Customer Case Pack

**Purpose:** Provide real-world training material from actual customer interactions.

**What it contains:**
- Anonymized real customer messages
- What was actually replied
- What worked and what didn't
- Outcome (order placed, customer lost, complaint resolved, etc.)
- Optimized reply (lesson learned)
- Organized by scenario type

**Example:** A Case Pack might include 15 price negotiation cases from Nigeria, 10 after-sales complaint cases from Kenya, and 5 inquiry-to-order conversion cases from the UAE.

**Who needs it:** Sales teams that want to learn from real experience, not hypothetical scenarios.

---

## How Packs Interact

```
Priority (highest to lowest):

Company Pack > Industry Pack > Core Engine (Generic)

If Company Pack is loaded:
  → Company rules override everything
  → Industry knowledge is embedded within or referenced by Company Pack

If only Industry Pack is loaded:
  → Industry knowledge enhances the Core Engine
  → Generic rules still apply where industry rules don't cover

If no Pack is loaded:
  → Core Engine operates in Generic Mode
  → Outputs include upgrade suggestion
```

---

## Pack Format

All packs are plain Markdown files with YAML frontmatter:

```markdown
---
pack_name: "Water Pump Industry Communication Pack"
pack_version: "1.0.0"
industry: "Water Pump"
created_date: "2026-05-06"
compatible_core_version: "2.0+"
---

# Pack Content...
```

This format works with any AI tool that accepts system prompts or knowledge files.

---

## Creating a Pack

### Quick Creation Path

1. Copy the relevant template from `schemas/`:
   - `industry_pack_template.md`
   - `company_pack_template.md`
   - `case_pack_template.md`

2. Fill in the sections with your industry/company data

3. Save as a Markdown file

4. Load it alongside the Core Engine prompt

### What Makes a Good Pack

**Industry Pack quality criteria:**
- Specific parameters to ask (not generic "please tell me more")
- Real cost factors for price negotiation (not "our quality is better")
- Practical diagnostic questions for after-sales (not "please send details")
- Application-scenario-based recommendation logic

**Company Pack quality criteria:**
- Accurate product data (not aspirational)
- Real payment terms (not what you wish you could offer)
- Clear red lines (not vague guidelines)
- Honest brand voice (not corporate jargon)

**Case Pack quality criteria:**
- Real customer messages (not fabricated)
- Honest outcomes (include failures, not just wins)
- Clear lessons learned
- Properly anonymized

---

## Loading Packs

### With WorkBuddy

Packs are automatically detected when placed in the skill's pack directory.

### With ChatGPT / Claude

Paste the Pack content after the Core Engine prompt, or add it as a separate knowledge file in Custom GPT / Projects.

### With API

Include both the Core Engine and Pack content in the system message.

### Example System Message (with Industry Pack loaded):

```
[System Message Part 1: Core Engine]
... (paste core_engine_prompt.md)

[System Message Part 2: Industry Pack]
... (paste your industry pack content)
```

The engine will automatically detect the Industry Pack content and switch to Industry Pack Mode.

---

## Pack Versioning

Packs should include a version number and change history:

```yaml
pack_version: "1.2.0"
```

Recommended update frequency:
- Industry Packs: Quarterly (as market conditions change)
- Company Packs: Monthly or when business rules change
- Case Packs: After each significant customer interaction

---

## Premium vs Free Packs

| Pack Type | Free (This Repo) | Premium |
|-----------|:---:|:---:|
| Pack Schema Templates | Yes (full) | N/A |
| General Trading Demo Pack | Yes (shallow) | N/A |
| Industry-Specific Packs | No | Yes |
| Company-Specific Packs | No | Yes |
| Customer Case Packs | No | Yes |

The demo pack in this repository shows the format but intentionally lacks the depth needed for real business use. Premium packs provide the full industry intelligence that makes the engine truly effective.

---

*For premium packs, see `premium/README.md` or visit [TradePilot.mobi](https://tradepilot.mobi)*
