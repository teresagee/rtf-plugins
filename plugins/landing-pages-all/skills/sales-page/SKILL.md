---
name: sales-page
description: Write long-form sales page copy that converts. Full structure from headline through final CTA — built for products, services, and membership offers.
---

# Sales Page

You write long-form sales page copy that earns every scroll. Each section has a job. No filler paragraphs. No clever-for-the-sake-of-clever. The copy moves the reader from problem to solution to action.

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need the product, audience, pricing, or offer details that aren't clear from context or the user's request, ask — but only what's actually missing.

4. Pull ICP data from CLAUDE.md to inform pain points, objections, and language. Write to the specific person described there, not a generic audience.

## What You Produce

A complete sales page in markdown with all sections below. Each section is labeled with an H2 so the user can rearrange, edit, or hand off to a designer.

## Page Structure

### 1. Headline + Subheadline

The headline is the most important line on the page. It should:
- State the transformation or outcome clearly
- Speak directly to the reader's situation
- Be specific enough that the wrong person self-selects out

The subheadline expands on the headline — adds context, specificity, or a secondary benefit. Together they answer: "What is this, who is it for, and what will it do for me?"

No clever wordplay that sacrifices clarity. Clear beats clever every time.

### 2. Problem Agitation

Describe the pain they're living with right now. Be specific and vivid — not dramatic, but accurate. The reader should think "this person understands my situation."

Structure:
- Name the frustration in their language (not your marketing language)
- Describe what it looks like day-to-day — the symptoms, not just the label
- Show the cost of staying stuck — what they're losing by not solving this

This section earns trust. If you get their problem wrong, they leave. If you get it right, they keep reading.

### 3. Solution Introduction

Introduce what you've built and why it solves the problem. This is not a feature dump — it's the bridge from "I have this problem" to "here's what fixes it."

- Name the product/service clearly
- Explain the core mechanism — why this approach works
- Connect it directly back to the pain points from section 2

Keep it concise. The details come later. This section's job is to create the "tell me more" feeling.

### 4. Features to Benefits

Don't just list features — translate each one into an outcome the reader cares about.

For each feature:
- **Feature:** What it is (factual, brief)
- **Benefit:** What it does for them (outcome-focused)
- **Proof point:** Why they should believe this works (optional — use when you have data or examples)

3-7 features is the sweet spot. More than that and you're padding. Less and you're not giving enough to justify the price.

### 5. Social Proof

Structure the social proof section with clear placeholders. Never fabricate testimonials, results, or logos.

Use these placeholder formats:
- `[INSERT TESTIMONIAL — name, role, specific result they got]`
- `[INSERT RESULT STAT — e.g., "47 members in first 30 days"]`
- `[INSERT LOGO BAR — companies/publications if applicable]`

If the user provides real testimonials, weave them in naturally. Best placement: after a benefit claim that the testimonial directly validates.

### 6. Value Stack

If the offer includes multiple components, stack them with perceived value:

For each component:
- What it is
- What it's worth (if pricing this way)
- Why it matters

End with the total value vs. actual price. This only works if the individual values are credible — don't inflate numbers absurdly.

Skip this section entirely if the product is a single straightforward offer. Value stacks work for bundles and memberships, not simple products.

### 7. Pricing

Present the offer clearly:
- State the price confidently — no apologizing
- Anchor against the value stack total or against alternatives (cost of hiring, cost of doing nothing, cost of other solutions)
- If there are multiple tiers, keep them scannable
- If there's a guarantee, state it here

The price should feel like a logical conclusion, not a surprise. Everything above it builds the case.

### 8. Objections / FAQ

Anticipate and address the top 5-7 concerns. These should be real objections the ICP has, not softballs.

Format each as:
- **The objection** (stated in their voice — how they'd actually say it)
- **The answer** (direct, honest, specific)

Common objections to consider:
- "Is this right for my situation?"
- "What if it doesn't work for me?"
- "Why this vs. [alternative]?"
- "Is there a guarantee?"
- "How much time does this require?"

If you don't know the real objections, ask the user rather than guessing.

### 9. Final CTA

Close with clarity and confidence:
- Restate the core transformation in one line
- Clear call to action — exactly what happens when they click
- If urgency is real (limited spots, doors closing, price increase), state it factually. Never manufacture fake urgency.

One button. One action. Don't dilute with secondary CTAs.

## Voice and Stance

- **Confident, not pushy.** The copy should feel like a knowledgeable friend explaining why this is worth it — not a used car salesman cornering them.
- **Specific over vague.** "You'll build a 5-skill voice system in week one" beats "You'll get amazing tools."
- **Honest about limitations.** If it's not for everyone, say so. Exclusion builds trust.
- **No fabrication.** Never invent testimonials, results, case studies, or data. Use placeholders clearly marked when real proof isn't available.

## Output Format

```markdown
# [Headline]

## [Subheadline]

---

[Full sales page body organized by the sections above, each with H2 headers]
```

Deliver the complete page in markdown. The user can then move it into their site builder, landing page tool, or hand it to a designer.
