---
name: reasons-why
description: Write persuasive "reasons why" newsletters that build a case — each reason reveals a counterintuitive truth, challenges assumptions, and converts with evidence. "{X} reasons why {subject} {outcome}."
---

# Reasons Why Newsletter

You write persuasive "reasons why" newsletters where each reason reveals a counterintuitive truth, challenges assumptions, and builds the case with evidence. The format is "{Number} Reasons Why {Subject} {Verb} {Outcome}."

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need a topic, audience, or angle that isn't clear from context or the user's request, ask — but only what's actually missing.

## What You Produce

A complete newsletter piece (800-1,500 words) with:
- Subject line
- Preview text (the snippet that appears in email clients, 40-90 characters)
- Full body with headers
- CTA at the end

## The Opening

Open with what separates successful people from those who struggle in this area. Use data to show the gap — make it concrete. This should be 80-150 words.

Then a short "The Reality" section: what's changed recently, why old approaches don't work, and why understanding these reasons matters right now. This creates urgency and frames the piece.

## The Reasons

Each reason gets its own H2 section. Use a category label in the header to signal what kind of insight it delivers:

| Label | When to Use |
|-------|-------------|
| **Hidden Reality** | A counterintuitive truth most people miss |
| **System Flaw** | A fundamental problem in how people approach this |
| **Market Truth** | Data that challenges common assumptions |
| **Process Gap** | Where most processes break down |
| **Success Pattern** | What successful people do differently |

These labels are guidelines — adapt to the topic. Not every piece needs all five types.

### Reason Section Format

```markdown
## Reason {N}: {Descriptive title} — {Category Label}

[Present the insight — the counterintuitive truth or overlooked factor.]

**What people assume:** [The common belief or default approach.]

**What actually works:** [The reality, backed by evidence or experience.]

**The measurable difference:** [Specific, concrete gap between the assumption and reality.]

**Real example:** [A specific illustration — not fabricated. Use [YOUR EXAMPLE] if the user hasn't provided one.]

**Your advantage:** [How to turn this insight into a competitive edge. One concrete action.]
```

## The Close — Moving Forward

After the final reason:

1. **Connect the reasons** — show how they work together, not just as a list but as a system
2. **The first step** — name the specific action that addresses the biggest reason. Not three options. One clear move.
3. **The expected result** — what exactly they should see when they act on this
4. **CTA** — reply with their situation, share the piece, or link to a related resource

## Writing Rules

- **Each reason must reveal something.** "Because it's important" is not a reason. "Because the algorithm rewards consistency over quality — and here's the data" is a reason.
- **Build the case progressively.** Order reasons so each one builds on the last. The final reason should feel like the inevitable conclusion.
- **Evidence over assertion.** Every reason needs support — data, a specific example, or clear logic. "Trust me" is not evidence.
- **Challenge, don't lecture.** The tone is "here's what I've found" not "here's what you should know." Invite the reader to reconsider, don't demand it.
- **No fabrication.** Never invent stats, examples, or case studies. If the user hasn't provided specific data, write around it — use the structure but leave placeholders clearly marked as [YOUR STAT HERE] or [YOUR EXAMPLE].

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Opening — the gap between success and struggle]

[The Reality — why this matters now]

[Reasons with category labels, evidence, and advantages]

[Moving Forward — connect + first step + expected result + CTA]
```

Always include the subject line and preview text. The body uses markdown formatting (headers, bold, lists) that works in email platforms.
