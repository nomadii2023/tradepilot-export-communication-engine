# Example: Inquiry Reply (Incomplete Information)

> A practical example showing how the TradePilot Core Engine handles an inquiry with insufficient information.

---

## Scenario

**Core Scenario:** Inquiry Reply (Scenario 2)

**Context:**
- Product: Unspecified — Generic Mode
- Customer Country: Unknown
- Customer Type: Unknown
- Channel: WhatsApp

**Customer Message:**

> "Send me your price list."

---

## Engine Output (Generic Mode)

> **Current Mode:** Generic Mode
> **Note:** This reply is based on generic foreign trade logic. For more accurate, industry-specific responses, load an Industry Communication Pack or Company Communication Pack.

### 1. Scenario Judgment

This is an **inquiry reply** scenario — specifically, a "price list request" which is one of the most common but lowest-quality inquiry types. The customer gives zero context about what they want, which usually means:
- They're casting a wide net to multiple suppliers
- They may not know exactly what they need
- They may be price-shopping without real purchase intent

### 2. Customer Intent

- Testing supplier responsiveness and professionalism
- Browsing/collecting price information
- Possibly a genuine buyer who doesn't know how to specify their needs
- Low probability of immediate conversion without more information

### 3. Risk Alert

- Don't send a full price list — it gives away pricing with zero commitment
- Don't ignore the message — even low-quality inquiries can convert
- Don't ask too many questions at once — the customer will stop replying
- Don't say "we have many products, which one do you want?" — too passive

### 4. Communication Strategy

1. Respond quickly (speed matters for first-contact inquiries)
2. Ask 2-3 targeted questions to narrow down the product
3. Offer to send relevant options (not the full catalog)
4. Make it easy for the customer to reply (short questions)
5. If possible, suggest a popular product to give the conversation direction

### 5. Recommended English Replies

**A. WhatsApp / IM (Brief):**

> Thanks for reaching out! We have several product lines. Could you let me know:
> 1. What type of product are you looking for?
> 2. What's the application (where will it be used)?
> 3. Any specific requirement (size, material, quantity)?
>
> This will help me send you the right info instead of a long catalog you don't need.

**B. Email / Platform (Formal):**

> Dear [Name/Sir/Madam],
>
> Thank you for your interest in our products.
>
> We supply a range of products and would like to send you the most relevant information. Could you please share:
>
> 1. The type of product you're looking for
> 2. Your intended application or use case
> 3. Estimated quantity
> 4. Destination country (for shipping cost reference)
>
> Based on your requirements, we'll prepare a targeted quotation rather than a general price list — this way you get more useful information.
>
> If you're not sure about specifications yet, just tell us what you need the product for, and we can suggest suitable options.
>
> Looking forward to your reply.

### 6. Next Steps

- If the customer replies with details → move to quotation stage
- If the customer asks for "everything" → suggest starting with the most popular product line
- If the customer goes silent → send one follow-up in 2-3 days with a specific product suggestion
- If the customer only wants a catalog → send a condensed version (top 5 products) rather than full catalog

### 7. Avoid Saying This

| Don't Say | Why |
|-----------|-----|
| "Here is our full price list." | Sends all your pricing to someone who hasn't committed — no negotiating leverage |
| "What do you want to buy?" | Too blunt and lazy; shows no professionalism |
| "Please check our website." | Passing the work to the customer; they asked you, not your website |
| "We have too many products. Please be specific." | Condescending — it's YOUR job to help them specify |
| "Send me your company profile first." | Asking for too much before you've even shown basic helpfulness |

---

## Key Takeaway

The key to handling "price list" inquiries is to convert a low-effort request into a focused conversation. Instead of dumping data, ask targeted questions that help you understand the customer's real needs. In Generic Mode, the questions are general; with an Industry Pack, you'd ask about specific technical parameters relevant to the product category.
