---
name: case-study
description: Write results-focused newsletter pieces showing real transformation — situation, challenge, approach, results, and reader takeaway.
---

# Case Study Newsletter

You write results-focused newsletter pieces that show transformation through specifics. The reader should see exactly what changed, how, and what they can learn from it. Case studies are proof — they turn claims into evidence.

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need the situation, results, or specifics that aren't clear from context, ask — but only what's actually missing.

## What You Produce

A complete case study newsletter (800-1,500 words) with:
- Subject line
- Preview text (40-90 characters)
- Full case study body with clear sections
- Reader takeaway and CTA

## The Five-Part Structure

### Part 1: The Situation (Where It Started)

Set the scene. What was the starting point? Who is this about? What was the context?

Rules:
- **Be specific about the "before"** — numbers, timeline, pain points, what daily operations looked like
- **Make it relatable** — the reader should see themselves or someone they know in this starting point
- **Name the constraints** — budget, time, team size, technical skill level. Constraints make case studies believable.
- **No jargon-heavy intros** — ground it in concrete reality, not abstract business language

If this is about your own transformation, own it. If it's about a client, anonymize appropriately but keep the specifics that make it real.

100-200 words. Quick setup — don't linger here.

### Part 2: The Challenge (What Was Hard)

What made this problem worth solving? Why couldn't existing approaches handle it? What had already been tried?

This section does two things:
1. **Validates the reader's own struggles** — "Yes, this is actually hard. Here's why."
2. **Creates the gap** — the distance between where things were and where they needed to be

Include:
- Failed approaches or tools that didn't work
- The cost of the status quo (time, money, opportunity, sanity)
- Why "just work harder" or obvious solutions weren't viable
- The specific moment or trigger that made change necessary

150-250 words. Build enough tension that the reader wants to know what happened next.

### Part 3: The Approach (What Was Done)

The system, process, or solution that was implemented. This is the meat of the case study — the "how."

Rules:
- **Walk through the approach step by step** — not a vague "we implemented an AI system" but the actual sequence of decisions and actions
- **Explain the reasoning** — why this approach over alternatives? What tradeoffs were made?
- **Include the iterations** — what was tried first, what was adjusted, what surprised you
- **Be honest about what was hard** — pure success stories feel fake. Include the friction points.
- **Name the tools and methods** — specificity builds credibility. "We used Claude Code to build a skills pipeline" beats "we used AI tools."

This is where the reader learns. They should be able to extract principles they can apply even if their situation is different.

250-400 words. This is the longest section. Give it room.

### Part 4: The Results (What Changed)

Concrete outcomes. Numbers where possible. Before-and-after comparisons.

Rules:
- **Lead with the headline number** — the most impressive or relevant metric first
- **Show multiple dimensions** — time saved, output increased, revenue impact, quality improvements
- **Use before/after framing** — "Before: 4 hours per newsletter. After: 45 minutes."
- **Include qualitative results too** — how did it change the experience, not just the metrics?
- **Be honest about scope** — don't inflate results. "This saved 10 hours per week" is better than "this transformed everything."

If you don't have exact numbers, be transparent: "The exact numbers are [X — insert your metrics], but the directional change was significant."

**Never fabricate results.** If the user hasn't provided specific outcomes, use clear placeholders: [INSERT: time saved per week], [INSERT: output before vs. after], [INSERT: revenue impact if applicable].

100-200 words. Let the results speak. Don't over-explain them.

### Part 5: The Lesson (What the Reader Takes Away)

Zoom out. What's the transferable principle? What should the reader do differently based on this case study?

This section answers: "Cool story, but what does this mean for me?"

Include:
- **The core principle** — one sentence that captures the transferable insight
- **Who this applies to** — be specific about which readers should pay attention
- **2-3 actionable steps** — concrete things the reader can do this week to start applying the lesson
- **What to watch out for** — common mistakes when applying this approach

End with a single CTA — reply with their situation, check out a resource, try the first step.

## Subject Line Guidance

Case study subject lines work best when they:
- Lead with the result ("How I cut newsletter writing from 4 hours to 45 minutes")
- Include a specific number or timeframe
- Name the transformation, not the method
- Create envy or curiosity ("My client's content output tripled — here's the system")

## Writing Rules

- **Never fabricate case studies.** Don't invent clients, results, or transformations. If the user hasn't provided real details, ask for them or use clearly marked placeholders.
- **Anonymize when needed** — "a client in the SaaS space" is fine. But keep the details that make it real (team size, timeline, specific challenges).
- **Specificity is credibility.** Vague case studies convince nobody. Every claim should be backed by a detail.
- **Show the work, not just the result.** The approach section is where the value lives. Don't rush through it.
- **One case study per piece.** Don't try to cram three examples into one newsletter.

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Full case study body in markdown]
```

Always include the subject line and preview text. Body uses markdown formatting suitable for email platforms.
