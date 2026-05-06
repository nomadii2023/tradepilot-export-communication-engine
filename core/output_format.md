# Output Format Reference

> The fixed 7-section output structure of the TradePilot Export Communication Engine.

---

## Standard Output

Every engine response follows this structure:

```
[Mode Indicator]
> Current Mode: [Generic Mode / Industry Pack Mode / Company Pack Mode]
> [Additional mode information if applicable]

---

[1. Scenario Judgment]
[Analysis of which trade scenario this falls under]

[2. Customer Intent]
[Analysis of what the customer really wants]

[3. Risk Alert]
[Key risks to avoid in this response]

[4. Communication Strategy]
[Step-by-step approach: what to say, ask, hold, advance]

[5. Recommended English Replies]

  A. WhatsApp / IM (Brief Version)
  [Short, natural reply]

  B. Email / Platform (Formal Version)
  [Structured, professional reply]

  C. Safer / Stronger Version (if applicable)
  [For high-risk scenarios: price pressure, complaints, legal]

[6. Next Steps]
[What to do after customer replies, with follow-up phrases]

[7. Avoid Saying This]
[2-5 expressions NOT to use, with reasons]
```

---

## Section Details

### Mode Indicator (New in v2.0)

Always displayed at the top. Shows the current operating mode:

- **Generic Mode:** "This reply is based on generic foreign trade logic. For more accurate responses, load an Industry Pack or Company Pack."
- **Industry Pack Mode:** Shows which industry pack is loaded
- **Company Pack Mode:** Shows which company pack is loaded

### Section 1: Scenario Judgment

- Identify the scenario from the 10 core types
- Explain WHY this scenario was identified
- If information is insufficient, state what's missing

### Section 2: Customer Intent

- List possible intents ranked by likelihood
- Distinguish between stated intent and real intent
- Consider cultural and market context

### Section 3: Risk Alert

- Use warning indicators (⚠️) for high risks
- Be specific about what NOT to do
- Include both communication risks and commercial risks

### Section 4: Communication Strategy

- Sequential: First do X, then do Y
- Include: what to ask the customer
- Include: what bottom line to hold
- Include: how to advance the deal

### Section 5: English Replies

**Minimum:** WhatsApp + Email versions
**For high-risk scenarios:** Add a Safer/Stronger version

WhatsApp version rules:
- Short paragraphs (1-3 sentences each)
- Conversational but professional
- No formal salutations ("Dear Sir")
- Clear call-to-action

Email version rules:
- Proper structure (greeting, body, closing)
- Professional but not stiff
- No meaningless filler ("hope this email finds you well")
- Clear next step for the customer

### Section 6: Next Steps

- If-then logic: "If customer does X, then do Y"
- Include English follow-up phrases when helpful
- Cover both positive and negative customer responses

### Section 7: Avoid Saying This

- 2-5 expressions with explanations
- Focus on expressions that seem natural but actually hurt the position
- Keep concise — table format preferred

---

## Language Rules

- Default: Chinese analysis, English replies
- User can request: all English, less Chinese, English only
- The language of analysis sections follows the user's preference
- English replies are ALWAYS in English (never translated back to Chinese)
