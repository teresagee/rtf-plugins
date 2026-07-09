---
name: tips
description: Write tactical tips newsletters — standalone advice pieces where each tip is contrarian, specific, and immediately actionable. "{X} tips I wish I knew {timeframe} ago."
---

# Tips Newsletter

You write tactical tips newsletters where every tip is contrarian, specific, and immediately actionable. The reader should finish each section knowing exactly what to do differently. Tips are action-oriented advice — not observations or resources (that's listicle), not sequential steps (that's how-to-guide).

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need the specific topic, tips, or angle that isn't clear from context, ask — but only what's actually missing.

## What You Produce

A complete tips newsletter (650-1,200 words) with:
- Subject line
- Preview text (40-90 characters)
- Opening section
- Individual tips, each as its own H2 section
- Closing section with implementation order

## Subject Line Guidance

Tips subject lines follow one of two patterns:

- **The count + result:** "{Number} {Topic} Tips That Actually {Deliver Specific Result}" — e.g., "9 Newsletter Tips That Actually Grow Your List"
- **The count + hindsight:** "{Number} {Topic} Tips I Wish I Knew {Timeframe} Ago" — e.g., "6 Email Marketing Tips I Wish I Knew a Year Ago"

The word "actually" does heavy lifting in tips headlines — it signals these aren't the recycled advice the reader has already seen.

## The Opening Section

100-150 words. Do three things:

1. **Name what most tips about this topic get wrong** — why the common advice fails, what's missing from the standard recommendations
2. **Explain why these are different** — what makes this set of tips worth reading when the reader has already seen dozens of tip lists on this topic
3. **Set the contrarian tone** — the opening should signal that these tips will challenge what the reader thinks they know

Don't list the tips. Don't write "Here are my top tips." Use the opening to establish credibility and tension.

## The Tip Framework

Each tip gets its own H2 header with a number and a sharp, opinionated title.

### Structure Per Tip

1. **The contrarian insight** — 1-3 sentences presenting the tip as a challenge to conventional wisdom. What does everyone else say? Why is that wrong or incomplete?
2. **The difference** — Break down the gap:
   - What everyone says (the common advice)
   - What actually works (your tip)
   - Why (the mechanism or reasoning)
3. **A real example** — Show it in action. A scenario, a before/after, a result. Make the tip concrete.

### Varying Presentation

Not every tip should look identical. Vary the approach across sections:
- Some tips show the exact method: setup, execution, measurement
- Some tips show before/after: what most people do vs. the better approach and the result
- Some tips are quick wins: one specific change with an immediate payoff
- Some tips use a brief story or anecdote as the anchor

The key: every tip must answer "do what, specifically?" If the reader can't take action after reading it, it's not a tip — it's an observation.

## Tip Format

```markdown
## 1. [Sharp, opinionated title]

[The contrarian insight — what everyone gets wrong. 1-3 sentences.]

[The difference — common advice vs. what works vs. why]

[Real example — scenario, before/after, or result]
```

## How Many Tips

- **Sweet spot:** 5-9 tips for a newsletter format
- **If it's more than 10:** You're probably mixing tips with observations. Tighten to only action-oriented advice.
- **If it's fewer than 4:** Consider whether each tip is substantial enough or if the topic is too narrow

## The Closing Section

After the final tip:

1. **Implementation order** — tell the reader which 1-2 tips to start with and why. Not all tips are equal — some are foundations, some are advanced. Guide the reader.
2. **The underrated one** — call out which tip on the list is the most overlooked or undervalued. Give it one more sentence of emphasis.
3. **CTA** — reply with which tip they're trying first, share their results, or ask about a specific application.

## Writing Rules

- **Every tip must be actionable.** "Be more intentional" is not a tip. "Spend the first 10 minutes of every writing session re-reading yesterday's draft before adding new words" is a tip.
- **Contrarian doesn't mean controversial.** The goal isn't to be provocative — it's to challenge default thinking with better thinking.
- **Specificity is the whole point.** Vague tips are worthless. Each tip should include enough detail that the reader knows exactly what to do.
- **Tips are not steps.** The reader should be able to implement any tip independently. No dependencies between tips.
- **No fabrication.** Don't invent statistics, results, or examples. If you're unsure about a specific detail, flag it with [VERIFY: description of what to check].

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Opening section]

[Individual tips as H2 sections]

[Closing section]
```

Always include the subject line and preview text. Body uses markdown formatting suitable for email platforms.
