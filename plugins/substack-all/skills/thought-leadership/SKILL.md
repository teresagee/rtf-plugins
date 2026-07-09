---
name: thought-leadership
description: Write opinion-driven positioning pieces (800-1,500 words) that establish authority and drive engagement. Built for newsletters and Substack.
---

# Thought Leadership Newsletter

You write opinion-driven newsletter pieces that position the author as a practitioner — someone with real experience and strong takes, not a summarizer of other people's ideas.

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

## The Headline

Use the irresistible headline framework. A strong headline combines several of these elements:

- **How many** — a specific number ("7 reasons," "3 mistakes")
- **What** — the content type ("lessons," "strategies," "truths")
- **Proven approach** — credibility signal ("I learned running my business," "after 500 client calls")
- **Who** — the audience ("for solo founders," "that every content creator")
- **Outcome** — what they get ("to 10x your output," "that actually convert")
- **Twist the knife** — the pain point or contrarian hook ("...but nobody talks about," "...that feel counterintuitive")

Not every headline needs all six. But the best ones hit 3-4. The headline should make someone stop scrolling.

## The Introduction (5-Block Opener)

Every piece opens with five short blocks. Each is 1-3 sentences max:

1. **Greeting** — optional, brief. Can be skipped if the voice doesn't use greetings.
2. **Hook** — a specific observation, surprising stat, or bold claim that earns the next sentence.
3. **Promise** — what the reader walks away with if they keep reading.
4. **Solution** — the angle or framework you're about to share (not the full answer — the shape of it).
5. **Transition** — bridge into the body. Usually a single line.

This intro should be 80-150 words total. Not a wall of text. Quick, punchy, earns the scroll.

## Headers That Deliver Value Standalone

Every H2 header should teach something even if the reader never reads the section below it. Bad: "The Problem." Good: "Most newsletters fail because they teach concepts, not actions."

Headers are mini-promises. Each one should make the reader think "I need to read this section."

## What This Skill Is (and Isn't)

This skill writes **opinion pieces with a strong position**. You have a take. You argue for it. You back it with experience and evidence. The reader walks away seeing something differently.

If the piece is primarily structured as numbered items, use a more specific skill instead:
- **Numbered tips** → `tips` skill
- **Common mistakes** → `mistakes` skill
- **Reasons for/against** → `reasons-why` skill
- **Myth-busting** → `contrarian` skill
- **Sequential steps** → `how-to-guide` skill
- **Numbered resources/tools/items** → `listicle` skill

This skill is for pieces that don't fit neatly into a numbered format — essays, arguments, frameworks, analysis, and position pieces where the structure follows the argument, not a count.

## Body Structure

Organize the body around 3-5 sections that build your argument. Each section should advance the reader's understanding — not just list more points.

Common structures for opinion pieces:
- **Problem → Reframe → Solution** — show why the common framing is wrong, then offer a better one
- **Observation → Implication → Action** — notice something, explain what it means, tell them what to do
- **Thesis → Evidence → Evidence → Evidence → Conclusion** — make your claim, stack proof
- **Before/After** — show what the world looked like before an insight, and after

The key: every section earns the next one. The reader should feel pulled through the argument, not just reading a list.

## Voice and Stance

- **Strong opinions held loosely.** Take a position. Don't hedge with "it depends" unless you then explain exactly what it depends on.
- **Specific over general.** "I wrote 47 newsletters last year" beats "I write a lot of newsletters." Numbers, names, details.
- **Practitioner energy.** Write from experience, not research. The reader should feel like they're getting advice from someone who does this, not someone who studies it.
- **Tactical value.** Every section should leave the reader with something they can do, think differently about, or apply. No filler sections.
- **No fabrication.** Never invent stories, metrics, quotes, or examples. If the user hasn't provided specific data, write around it — use the structure but leave placeholders clearly marked as [YOUR STAT HERE] or [YOUR EXAMPLE].

## The Close

End with one of these patterns:
- **Direct CTA** — tell the reader exactly what to do next (reply, click, try something)
- **Reframe** — restate the core idea in a way that sticks
- **Challenge** — give them a specific action for this week
- **Callback** — circle back to the opening hook with a new layer of meaning

One CTA only. Not three. Not "also check out." One clear next step.

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Full newsletter body in markdown]
```

Always include the subject line and preview text. The body uses markdown formatting (headers, bold, lists) that works in email platforms.
