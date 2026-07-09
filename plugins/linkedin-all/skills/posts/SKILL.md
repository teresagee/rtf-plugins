---
name: posts
description: Use when the operator wants a LinkedIn post drafted — "write a LinkedIn post about X", "turn this story/win/lesson into a post", "repurpose this newsletter for LinkedIn", "draft the next post from my queue" — or when they report how a published post performed and the win should be templatized into the swipe file.
argument-hint: "[topic, story, or queue item] [optional format — text, document, image]"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebFetch
---

# Posts — draft one LinkedIn post properly

You draft one post at a time, built the way the people who actually win on LinkedIn build them: a named skeleton, a hook that does most of the work, receipts that are real, and a format chosen against what performs in 2026 — not what performed in 2023. Every expert worth studying writes inside structures and templatizes their own winners; this skill does both for the operator.

**Where things live:** each post gets a piece folder — `workspace/content/pieces/<YYYY-MM-DD>-<slug>/post.md` (create idempotently). The plugin's shared standing folder is `workspace/linkedin/` (strategy, queue, swipe file — created by `/linkedin:plan`; this skill reads them and appends to the swipe file). Nothing is ever posted — the operator publishes everything themselves.

## Step 1 — Read the context profiles

Read all four first:

- `context/user.md` — the stories, expertise, and receipts posts are made of
- `context/business.md` — what the post ultimately serves
- `context/ICP.md` — who it's written to, in whose language
- `context/tools.md` — channels and conventions

`ICP.md` and `user.md` are load-bearing: a post that isn't written to this operator's reader, out of this operator's actual experience, is the generic slop the 2026 algorithm exists to suppress. **If a profile is missing or empty:** say which one and continue — ask the operator directly for what's missing (who's this for? what's the real story here?) rather than inventing it. Never error out, never fill gaps with fabricated specifics.

## Step 2 — The voice rule

Check for a matching voice-profile skill — the operator's own voice for their content, a client's voice if this post is for a client. If one exists, invoke it before drafting. If none exists: say so, offer the two paths — build one (the Voice plugin) or proceed inferring voice from `context/user.md` — and never draft in a generic default voice. On 2026 LinkedIn this is a distribution issue, not just taste: AI-pattern writing is detected and suppressed (multiple sources report it; the mechanism is unverified, the direction is consistent), and the converging fix across every expert is the same — personal stories, specific numbers, first-person receipts.

## Step 3 — Read the standing system

- `workspace/linkedin/strategy.md` — the lane, pillars, outcome mix. If it exists, the post must sit in the lane; if it doesn't, say so, work from `business.md`, and mention `/linkedin:plan` once without nagging.
- `workspace/linkedin/swipe-file.md` — the operator's templatized winners. **A proven template beats a fresh structure** — if a swipe-file entry fits this topic, default to it and say which one you're reusing (the templatize-your-winners doctrine: analyze what worked, abstract the skeleton, run variations).
- `workspace/linkedin/queue.md` — if the ask is "the next post," pull the top unchecked idea and mark it as promoted (link the piece folder).
- The last 2–3 piece folders with `channel: linkedin` — don't repeat a hook pattern or story the operator just used.

If the operator handed source material (a newsletter, a transcript, a URL — fetch URLs with WebFetch), read it in full and mine it for ONE post-sized idea. One post carries one idea; flag the leftovers as queue candidates.

## Step 4 — Choose outcome and format

**Outcome first** (the Content Matrix discipline — every post targets exactly one): **engage** (dopamine/reach), **positioning** (thought leadership), **capture** (email subscribers), or **sale**. If `strategy.md` declares a mix, respect it — capture and sale posts are the minority that the majority earns.

**Then format, against the 2026 hierarchy** (full table and reasoning in [references/format-library.md](references/format-library.md)):

- **Text (~700–1,000 characters)** — the default workhorse, the most stable performer.
- **Document/carousel** — the engagement leader as of 2026; choose it when the content is step-based or list-based and worth saving. Produce a slide-by-slide outline.
- **Image + text** — a real photo (ideally with the operator's face — face images outperform faceless by a wide margin in the 2025 algorithm data) where the image is part of the hook, not decoration.
- **Short vertical video** — only for cold-audience discovery, and only if the operator already produces video. Don't build LinkedIn video-first in 2026; the platform's video push has visibly cooled.
- **Poll** — flagged option, not doctrine: reputationally cringe but measurably high-reach in 2025 personal-profile data. Offer it for testing only.

## Step 5 — Build the hook, then the body

**The first line is the product.** The post lives or dies in the ~210 characters above the fold, and the first line should run about 8–10 words so it survives a phone screen. Write **three hook options** using the hook types in the reference file (curiosity gap, specific number/credential, expectation break, relatable enemy), each one a trailer for the post's payoff — never a bait-and-switch. Recommend one; let the operator pick.

**Body on a named skeleton** from [references/format-library.md](references/format-library.md) — Story→Lesson→Advice→You, PAS, enemy-opener, listicle, X-vs-Y, non-obvious solution. Craft rules that are not optional:

- Short sentences, paragraphs of 4 lines max, white space as a feature. Plain words — read-aloud simple.
- Every line should be able to stand alone — assume skimming.
- **Receipts must be real.** Specific numbers and named outcomes are the doctrine, but only from `user.md`/`business.md` or the operator's mouth this session. A post needing a number the operator doesn't have gets written around the gap or the operator gets asked. Never invent, never round up.
- **No external links in the body** (40–60% reach penalty). The link-in-first-comment workaround is also reportedly detected as of early 2026 (single source — treat as probable, not proven): for capture posts, prefer pointing at the profile's Featured section, and tell the operator the link-placement tradeoff honestly.
- 0–3 hashtags, cosmetic only. No engagement bait ("comment YES"). No one-line-per-sentence broetry padding — dwell-time ranking rewards substance density.
- End with one move the reader can make: a real question (comments are weighted roughly double likes), an invitation to save (saves are weighted heavily), or the capture/sale ask if that's this post's job.

## Step 6 — Save the piece

Write `workspace/content/pieces/<YYYY-MM-DD>-<slug>/post.md`:

```markdown
---
title: "<working title>"
status: draft
channel: linkedin
format: text | document | image | video | poll
outcome: engage | positioning | capture | sale
pillar: "<from strategy.md, if it exists>"
template: "<swipe-file template name, if one was reused>"
date: <YYYY-MM-DD>
---

# <Working title>

## Post
<the full post, exactly as it will be pasted — chosen hook included>

## Alternate hooks
1. <option>
2. <option>

## Visual
<image direction / carousel slide-by-slide outline / "none — text post">

## First comment
<only if one is planned, e.g. context or the link with the tradeoff noted>

## Posting notes
<in your own words: timing (never within 24h of the last post), the
first-hour reply plan, and the ask to report results back so winners get
templatized>
```

For carousels, add `carousel.md` in the same folder: hook slide, one idea per slide (roughly 8–12), a closing slide with the post's one move. The operator builds the PDF from it.

Show the full post in chat for review and revise on feedback — full redrafts when asked for "better," not polish passes.

## Step 7 — The winner loop (when the operator reports back)

When the operator says a post performed (or flopped):

1. **File the numbers exactly as given** — append a `## Result` line to the piece's `post.md` and flip `status:` to `published`. "Did well" stays "did well"; never harden it into invented metrics.
2. **If it's a winner, templatize it:** abstract the skeleton (hook move, structure beat by beat, the close) into `workspace/linkedin/swipe-file.md` — entry shape is in the reference file. Then offer the variations play: same skeleton, different pillar/story, spaced out over the coming weeks — added to `queue.md` as ideas, not auto-drafted.
3. **If it flopped,** note the suspect honestly (hook? topic outside the lane? format?) — a brief note in the piece file. No post-mortem theater.

## What this skill never does

- Never posts, schedules, or touches LinkedIn — drafts only, operator publishes.
- Never invents numbers, stories, clients, or results for a post — real receipts or none.
- Never drafts in a generic default voice — voice skill, or declared inference from `user.md`.
- Never ships dated mechanics — engagement bait, hashtag strategy, broetry, pod tactics, link tricks presented as safe. The blocklist in the reference file is binding.
- Never batch-produces — one post, built properly, per run. Batching is what the queue in `/linkedin:plan` is for.
