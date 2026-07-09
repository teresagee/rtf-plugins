# File shapes — workspace/linkedin/

Three standing files define the system. Create them exactly in these shapes; never overwrite an existing file with a fresh template. Placeholders in `<angle brackets>` get filled; everything is derived from this operator's context profiles, not from generic strategy.

---

## 1. `workspace/linkedin/strategy.md`

Written by the plan skill's setup mode; rewritten in place on refresh (bump `updated:`). Read by `/linkedin:posts` and `/linkedin:profile` — the lane declared here is THE lane, everywhere.

```markdown
---
title: "LinkedIn Strategy"
type: linkedin-strategy
updated: <YYYY-MM-DD>
lane: "<the one topic LinkedIn should associate with this profile>"
one-action: "<where content ultimately sends people — usually the email list>"
---

# LinkedIn strategy

**The lane:** <one sentence — "When LinkedIn sees this profile, the topic it
should associate with it is ___." Everything below stays inside it.>

**The one action:** <the capture asset / destination, with its link. If none
exists yet: "[MISSING — no capture asset yet; posts run engage/positioning
only until one exists]">

## Pillars
| Pillar | What it covers | Why the ICP cares (from ICP.md) |
|---|---|---|
| <name> | <a phrase> | <their frustration/aspiration it speaks to> |

## Outcome mix
<the weighting across engage / positioning / capture / sale, and the
reasoning behind it — e.g. "value earns the asks; capture posts only after
the list asset exists">

## Cadence + format mix
- <N> posts/week (never >1 per 24h) — chosen as sustainable for 8+ weeks
- Formats: <this operator's mix — e.g. "text default · 1 carousel/week ·
  face-photo posts when there's a story" — per what they can actually produce>

## Comment list
<20–30 in-lane + ~10 adjacent. Suggestions from search stay (unverified)
until the operator confirms them.>

| Creator | Lane / adjacent | Why on the list | Status |
|---|---|---|---|
| <name> | <which> | <one phrase> | confirmed / (unverified) |

## Daily routine (~15–30 min)
<this operator's routine, built from the engagement system: daily
substantive comments on the list (the seven types — never "Great post"),
first-hour replies on posting days, thread depth over spread, and the
inbound-led-only DM stance>

## What we don't do
Pods, automation, cold DM blasts, engagement bait, hashtag schemes,
virality-chasing. All detected, penalized, or pointless as of 2026 — and the
goal is the list and the pipeline, not impressions.

## Notes
<anything decided that doesn't fit above — dated lines>
```

---

## 2. `workspace/linkedin/queue.md`

Rolling idea queue, newest week at the top. The plan skill appends a week per run; `/linkedin:posts` marks ideas as promoted when it drafts them.

```markdown
# LinkedIn queue

Rolling, newest week first. Pick an idea, say "draft it" — that's
/linkedin:posts. Stale ideas get dropped on the next planning pass, not
hoarded.

---

## Week of <YYYY-MM-DD>
- [ ] <pillar> × <style> → <outcome> — "<draft first line, 8–10 words>" —
  format: <text/document/image> <("variation of: <swipe-file template>")
  if applicable>
- [ ] <...>
```

When an idea is drafted: check the box and append `→ pieces/<YYYY-MM-DD>-<slug>/`.

---

## 3. `workspace/linkedin/swipe-file.md`

Created empty by the plan skill on first run; filled by `/linkedin:posts` when the operator reports a winner. Entry shape lives with the posts skill (its format-library reference) — this file just needs the header on creation:

```markdown
# Swipe file — templatized winners

Proven post skeletons, abstracted from this operator's own published posts
that performed. /linkedin:posts reuses these before inventing fresh
structures, and runs spaced variations of them. Results are recorded exactly
as the operator reported them — never embellished.

---
```

---

## One more file in the same folder

`workspace/linkedin/profile.md` — the live profile copy. Owned by `/linkedin:profile`; this skill only reads it (to keep the lane consistent). Never create or edit it from here.
