---
name: listicle
description: Write numbered-list newsletters where each item delivers standalone value — "{X} things that {outcome}" format. Not sequential steps (that's how-to-guide), not opinion (that's thought-leadership).
---

# Listicle Newsletter

You write numbered-list newsletters where every item stands on its own. The reader can jump to any section and walk away with value. Items are not sequential steps — they're independent observations, principles, or examples unified by a theme.

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need the specific topic, items, or angle that isn't clear from context, ask — but only what's actually missing.

## What You Produce

A complete listicle newsletter (650-1,200 words) with:
- Subject line
- Preview text (40-90 characters)
- Opening section
- Numbered items, each as its own H2 section
- Closing section with synthesis and action step

## Subject Line Guidance

Listicle subject lines follow one of two patterns:

- **The count + outcome:** "{Number} {Things} That {Drive Specific Outcome}" — e.g., "7 Writing Habits That Separate Professionals From Hobbyists"
- **The count + contrast:** "{Number} Ways to {Achieve Result} Without {Common Obstacle}" — e.g., "5 Ways to Scale Content Without Hiring a Team"

The number should be specific and honest. Don't inflate the count to seem more impressive.

## The Opening Section

100-150 words. Do two things:

1. **Explain why these items matter right now** — what's changed, what most people are getting wrong, or why the reader should care about this particular collection
2. **Challenge a common assumption** — set up the list by pushing back on conventional wisdom about the topic

Don't preview every item. Don't write "Here are 7 things that..." — the subject line already did that. Use the opening to earn the reader's attention with a perspective, not a table of contents.

## The Item Framework

Each item gets its own H2 header with a number and descriptive title.

### Structure Per Item

1. **Why it matters** — 1-3 sentences explaining the significance. What does this change? Why do most people overlook it?
2. **What makes it work** — Break it down with bullets:
   - Core principle or mechanism
   - Real example or evidence
   - Key difference from the obvious alternative
3. **What it looks like in practice** — A concrete illustration. A scenario, a before/after, a quick case. Make it tangible.

### Varying Presentation

Not every item should look identical. Vary the approach across sections:
- Some items use bullet breakdowns
- Some use direct comparisons (what most people do vs. what works)
- Some lead with a specific example or anecdote
- Some use a short quote or data point as the anchor

Variation keeps the reader engaged. If every section follows the exact same template, it reads like a checklist, not a newsletter.

## Item Format

```markdown
## 1. [Descriptive title]

[Why this matters. 1-3 sentences.]

[Breakdown — bullets, comparison, example, or data point]

[What it looks like in practice — concrete illustration]
```

## How Many Items

- **Sweet spot:** 5-9 items for a newsletter format
- **If it's more than 10:** Consider splitting into a series or tightening the theme
- **If it's fewer than 4:** It might be too thin — consider expanding scope or combining with another format

## The Closing Section

After the final item, wrap with a "Using These Together" section:

1. **Show the system** — 2-3 sentences connecting the items. How do they reinforce each other? What's the compound effect?
2. **First action step** — one specific thing the reader can do this week. Not three options — one clear move.
3. **CTA** — reply with their favorite item, share which one they're trying first, or link to a related resource.

## Writing Rules

- **Each item must stand alone.** The reader should be able to read item #5 without reading items #1-4. No "building on the previous point" dependencies.
- **Specificity over volume.** Seven specific items beat twelve vague ones. Cut anything that's filler.
- **No ranking unless stated.** Unless the list is explicitly ranked, don't imply items are in order of importance.
- **Show, don't just name.** "Use storytelling" is not an item. "Open with the moment everything changed — not the backstory" is an item.
- **No fabrication.** Don't invent statistics, studies, or examples. If you're unsure about a specific detail, flag it with [VERIFY: description of what to check].

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Opening section]

[Numbered items as H2 sections]

[Closing section]
```

Always include the subject line and preview text. Body uses markdown formatting suitable for email platforms.
