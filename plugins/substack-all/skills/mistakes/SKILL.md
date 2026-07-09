---
name: mistakes
description: Write "common mistakes" newsletters that name specific errors, explain the hidden cost of each, and show the fix. High-engagement format — readers love knowing what NOT to do.
---

# Mistakes Newsletter

You write "common mistakes" newsletters that name specific errors people make, reveal the hidden cost of each, and show how to fix them. The format is "{Number} {Topic} Mistakes That Cost You {Specific Loss}." Readers engage hard with this format because everyone wants to know what NOT to do.

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need a topic, audience, or specific mistakes that aren't clear from context or the user's request, ask — but only what's actually missing.

## What You Produce

A complete newsletter piece (800-1,500 words) with:
- Subject line
- Preview text (the snippet that appears in email clients, 40-90 characters)
- Full body with headers
- CTA at the end

## The Opening

Open with data or a sharp observation showing how many people get this wrong and what it costs them. Name the core misconception that causes these mistakes. This should be 80-150 words — enough to earn the scroll, not a wall of text.

Then a short "The Real Problem" section: explain how conventional wisdom, common advice, or default behavior creates these mistakes. This frames the entire piece — the mistakes aren't random, they stem from a shared root cause.

## The Mistakes

Each mistake gets its own H2 section. Use 3-5 mistakes — that's the sweet spot for newsletter format. Each mistake gets a category label in the header to signal what kind of error it is:

| Label | When to Use |
|-------|-------------|
| **Fundamental Error** | The root cause mistake — gets everything else wrong downstream |
| **Technical Error** | Something misunderstood at the mechanics level |
| **Strategic Error** | A higher-level misstep that undermines goals |
| **System Error** | Where spot fixes don't work — it's a systemic issue |
| **Integration Error** | Where it affects everything else connected to it |

These labels are guidelines, not requirements. Adapt them to the topic. Not every piece needs all five types.

### Mistake Section Format

```markdown
## Mistake {N}: {Descriptive title} — {Category Label}

[Describe the mistake in action — what it looks like when someone is making it. Be specific enough that the reader recognizes themselves.]

**The hidden cost:**
- [Immediate impact]
- [Long-term consequences]
- [Missed opportunities]

**How to spot it:** [How to identify if you're making this mistake right now — a specific signal, metric, or pattern to check.]

**The fix:** [Connect to what actually works instead. Concrete, actionable.]
```

## The Close

After the final mistake:

1. **The framework** — give readers a practical approach for addressing these mistakes systematically, not one at a time
2. **The one thing** — name the single most important change to make today. Not three options. One clear action.
3. **CTA** — reply with their biggest mistake, share the piece, or link to a related resource

## Writing Rules

- **Name the mistake specifically.** "Not having a strategy" is not a mistake. "Writing content without knowing which of your three audiences it's for" is a mistake.
- **Show the cost in concrete terms.** "This hurts your growth" is vague. "This means every piece of content you publish reaches 40% fewer people than it should" is specific.
- **Don't shame the reader.** The tone is "here's what I've seen go wrong" not "you're doing it wrong." Frame mistakes as common and fixable.
- **Each mistake must be distinct.** If two mistakes are really the same mistake from different angles, combine them.
- **No fabrication.** Never invent stats, examples, or case studies. If the user hasn't provided specific data, write around it — use the structure but leave placeholders clearly marked as [YOUR STAT HERE] or [YOUR EXAMPLE].

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Opening — the cost of getting this wrong]

[The Real Problem — root cause of these mistakes]

[Mistakes with category labels, hidden costs, and fixes]

[Close — framework + one thing + CTA]
```

Always include the subject line and preview text. The body uses markdown formatting (headers, bold, lists) that works in email platforms.
