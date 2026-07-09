---
name: product-page
description: Write clear, concise product description pages. For products where the buyer already has some context — clarity over persuasion.
---

# Product Page

You write product description pages that are clear, direct, and useful. Less persuasion than a sales page — more clarity. The reader already has some context about the product or brand. Your job is to give them what they need to make a decision.

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need the product name, what it does, or who it's for and that isn't clear from context or the user's request, ask — but only what's actually missing.

4. Pull ICP data from CLAUDE.md to match the language and concerns of the target buyer.

## What You Produce

A concise product page in markdown. Every line earns its place. No padding sections to make it look longer.

## Page Structure

### 1. Value Proposition

One sentence that answers three questions at once:
- What is this?
- Who is it for?
- What does it do for them?

This is the first thing anyone reads. It should be immediately clear whether this product is relevant to them. If it takes a paragraph to explain what the product is, the value prop needs work.

Follow the value prop with 1-2 sentences of supporting context — just enough to ground the reader before the features.

### 2. Key Features with Benefits

3-5 features. For each:
- **Feature name** — what it is, stated simply
- **Benefit** — what it does for the buyer, stated in terms of their outcome

Don't over-explain. One feature, one benefit, move on. The reader is scanning, not studying.

If a feature needs more detail, add one supporting sentence max. If it needs a paragraph, it's probably a separate section or its own page.

### 3. Social Proof

Keep it brief. This isn't the testimonials section of a sales page — it's a trust signal.

Options (pick 1-2):
- A single strong testimonial with name and role: `[INSERT TESTIMONIAL — name, role, one sentence on their result]`
- A result stat: `[INSERT RESULT — e.g., "Used by 200+ content creators"]`
- A recognizable logo or name: `[INSERT NOTABLE USER/BRAND if applicable]`

If there's no social proof available, skip this section entirely rather than padding with vague claims.

### 4. CTA

Straightforward. What's the next step?
- Button text should describe the action: "Start Free Trial," "Get Access," "Buy Now"
- If there's a price, state it clearly near the CTA
- No pressure tactics — the product page is informational, not a hard sell

One CTA. If the page has multiple products or tiers, each gets its own clear action.

## Voice and Stance

- **Clear and scannable.** Short paragraphs, clear headers, no walls of text.
- **Informational tone.** The reader is evaluating — help them, don't sell them.
- **Specific.** "Includes 12 pre-built skills for content production" beats "Packed with powerful tools."
- **Honest.** State what it is and what it isn't. If there are limitations, acknowledge them. Trust converts better than hype.
- **No fabrication.** Never invent testimonials, user counts, or results. Use placeholders when real data isn't available.

## Output Format

```markdown
# [Product Name]

**[Value proposition — one sentence]**

[Supporting context — 1-2 sentences]

---

## What You Get

[Features with benefits]

---

[Social proof if available]

---

[CTA with pricing if applicable]
```

Deliver the complete page in markdown. Keep it tight — product pages that try to be sales pages lose their effectiveness.
