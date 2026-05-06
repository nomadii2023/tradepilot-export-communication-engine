# Customization Guide

> Step-by-step guide to customizing the TradePilot Export Communication Engine for your business.

---

## Option 1: Quick Start (5 Minutes)

### Use the Core Engine as-is

1. Copy `core/core_engine_prompt.md`
2. Paste it into your AI tool as a system prompt
3. Start sending customer messages

**Result:** Generic Mode — works for basic trade scenarios but lacks industry depth.

---

## Option 2: Add an Industry Pack (30-60 Minutes)

### Step 1: Copy the Template

```bash
cp schemas/industry_pack_template.md my_industry_pack.md
```

### Step 2: Fill in Your Industry Data

Complete each section:

#### Section 2: Product Terminology
List your main product categories and their English names. Include common variants and related terms.

#### Section 3: Inquiry Reply Rules
Define the 5 key parameters customers MUST provide before you can quote. Write the English template for asking these questions.

#### Section 4: Product Recommendation Logic
Map application scenarios to recommended product types. Write the English recommendation template.

#### Section 5: Price Objection Handling
List 3-5 cost factors that justify your price differences. Write the English negotiation template.

#### Section 6: After-Sales Troubleshooting
List the diagnostic questions your technical team needs when a customer reports an issue.

### Step 3: Load with Core Engine

Combine the Core Engine prompt and your Industry Pack into a single system prompt:

```
[PASTE core_engine_prompt.md HERE]

---

## LOADED INDUSTRY PACK

[PASTE your industry pack content HERE]
```

### Step 4: Test

Use your real customer messages to test. Check:
- Does the engine use your industry terminology?
- Does it ask the right parameters?
- Does the price objection logic match your industry?

---

## Option 3: Add a Company Pack (2-4 Hours)

### Step 1: Copy the Template

```bash
cp schemas/company_pack_template.md my_company_pack.md
```

### Step 2: Gather Information

You'll need:
- Product catalog with specifications
- Price list (FOB prices, MOQ, lead times)
- Payment terms policy
- Warranty and after-sales policy
- OEM/ODM capabilities
- Certifications (real ones only)
- Brand voice guidelines
- Internal red lines

### Step 3: Fill in Each Section

#### Most Important Sections:
- **Section 3: Pricing and Payment Rules** — This prevents the engine from promising terms you can't deliver
- **Section 5: Warranty and After-Sales Policy** — This controls how the engine handles complaints
- **Section 9: Internal Red Lines** — This is the safety net

#### Fill Honestly:
- Don't inflate your capabilities
- Don't claim certifications you don't have
- Don't set payment terms more generous than what management approves
- Don't omit red lines — they protect your business

### Step 4: Load with Core Engine

```
[PASTE core_engine_prompt.md HERE]

---

## LOADED COMPANY PACK

[PASTE your company pack content HERE]
```

### Step 5: Test with Real Scenarios

Test these critical scenarios:
1. Customer asks for O/A payment → Does the engine refuse?
2. Customer complains about quality → Does it follow your warranty process?
3. Customer demands a price below your minimum → Does it hold the line?
4. Customer asks about certifications → Does it only mention real ones?

---

## Option 4: Build a Case Pack (Ongoing)

### Step 1: Set Up a Collection Process

After every significant customer interaction:
1. Save the customer's original message (anonymized)
2. Save what you actually replied
3. Note the outcome
4. Write a brief lesson learned

### Step 2: Use the Template

```bash
cp schemas/case_pack_template.md my_case_pack.md
```

### Step 3: Structure Cases

For each case, fill in:
- Scenario type (which of the 10 core scenarios)
- Context (country, product, customer type, channel)
- Customer's original message
- What was actually replied
- What worked / what didn't
- Outcome
- Optimized reply (if different from actual)

### Step 4: Organize by Scenario

Group cases by scenario type so your team can find relevant examples quickly.

---

## Option 5: Full Customization (Team Deployment)

For companies deploying across a sales team:

### Phase 1: Foundation (Week 1)
1. Build Industry Pack
2. Build Company Pack
3. Test with 10 real customer messages
4. Calibrate output

### Phase 2: Training (Week 2-3)
1. Build initial Case Pack (10-20 cases)
2. Train team on engine usage
3. Establish feedback loop

### Phase 3: Iteration (Ongoing)
1. Collect new cases weekly
2. Update Company Pack when policies change
3. Refine Industry Pack based on new market intelligence
4. Quarterly calibration session

---

## Testing Checklist

After customization, test these scenarios:

| Scenario | What to Check |
|----------|--------------|
| Vague inquiry ("send price list") | Does it ask targeted questions? |
| Price objection | Does it use your industry/company price factors? |
| After-sales complaint | Does it follow your warranty policy? |
| Payment term request | Does it enforce your red lines? |
| Product recommendation | Does it recommend based on application? |
| Order confirmation | Does it use checklist format? |
| Delivery delay | Does it handle diplomatically? |
| Cold outreach | Is it brief and relevant? |
| Contract negotiation | Does it warn about legal advice? |
| Company profile | Does it avoid empty claims? |

---

## Common Mistakes

1. **Making the Industry Pack too generic** — If it reads like "ask the customer what they want," it's not specific enough
2. **Inflating the Company Pack** — Claiming capabilities you don't have will backfire when the engine promises them
3. **Skipping red lines** — Without clear boundaries, the engine may promise things your team can't deliver
4. **Not testing with real messages** — Theoretical testing misses real-world complexity
5. **Never updating** — Markets, products, and policies change. Packs need maintenance.

---

## Need Help?

If you'd like TradePilot to build your custom packs, see `premium/README.md` or visit [TradePilot.mobi](https://tradepilot.mobi).

We offer:
- Industry Pack building (any product category)
- Company Pack building (from your product catalog and policies)
- Case Pack structuring (from your customer interactions)
- Team training and calibration
- Ongoing pack maintenance and updates
