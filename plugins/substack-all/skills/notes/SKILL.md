---
name: notes
description: Use when the operator wants Substack Notes — compose one or a few notes ("write a note about...", "give me today's notes"), batch a week of notes, atomize a published post into notes ("turn my last post into notes"), log how posted notes performed ("that note got 40 likes and 3 subscribers"), or diagnose a Notes reach drop.
argument-hint: "[compose|batch|atomize] [topic, piece path, or URL]"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebFetch
---

# Notes — compose, batch, atomize

You write Substack Notes for the operator. The north star is **subscriber conversion, not virality**: the feed is a subscription-prediction engine, and a 2026 analysis of 243,000+ notes found 40% of the most-liked notes converted zero subscribers. A note that gets 30 likes and 4 subscribers beat one that got 300 likes and none. Every choice in this skill — format, hook, CTA, cadence — serves that.

**Shared home (this plugin's owned folder): `workspace/substack/`.** This skill works in `workspace/substack/notes/`:

```
workspace/substack/notes/
  bank.md                 ← idea bank, one section per format
  tracker.md              ← performance log: what each note actually converted
  YYYY-MM-DD-<slug>.md    ← composed output, one dated file per run
```

The strategy this skill runs on — algorithm realities, cadence, the reach diagnostic — lives in [references/algorithm-and-cadence.md](references/algorithm-and-cadence.md). The format taxonomy and note anatomy live in [references/note-formats.md](references/note-formats.md). Read both before producing.

## Step 1 — Read the context profiles

Read all four before writing a word:

- `context/user.md` — the operator's story, expertise, and real experiences (the only legitimate source of personal material for notes)
- `context/business.md` — what they sell, what the notes ultimately feed
- `context/ICP.md` — who the reader is; their frustrations, aspirations, and language (hooks are written in *their* words)
- `context/tools.md` — where things live

**If a profile is missing or empty:** say which one and continue. Without `ICP.md`, hooks can't be aimed — write the notes from what exists and flag which ones are guessing at the audience. Never stop, never invent facts about the operator's world.

## Step 2 — Voice

Notes are content. Check for the operator's voice-profile skill and invoke it before drafting. If no voice profile exists: say so, offer two paths — build one (the Voice plugin) or proceed by inferring voice from the context profiles — and never produce in a generic default voice. The conversational register notes demand (short lines, talk-not-lecture) is a *format* constraint; the voice inside it must still be theirs.

## Step 3 — Make sure the home exists (idempotent)

`mkdir -p workspace/substack/notes`. If `bank.md` doesn't exist, create it: one `##` section per format from `references/note-formats.md`, each section empty except a one-line description. If `tracker.md` doesn't exist, create it with this header:

```markdown
# Notes tracker — subscribers per note, not likes
| date | format | hook (first line) | likes | comments | restacks | subs gained | verdict |
|---|---|---|---|---|---|---|---|
```

Never overwrite an existing bank or tracker.

## Step 4 — Run the mode

### Compose (default) — one note, or a few, now

1. Check `tracker.md` and the most recent batch file for which formats were used last. **Rotate** — don't repeat the same format twice running unless the tracker shows it converting for this operator.
2. Pick the format (taxonomy in `references/note-formats.md`) that fits the material the operator brought. If they brought no topic, pull from `bank.md` or propose 2–3 ideas from their world (recent pieces in `workspace/content/pieces/`, profile facts, things said this session).
3. Write to the anatomy: **hook → 2–5 scannable lines of substance → a question, never a subscribe ask.** Specific beats clever; a real number in line 1 where one truthfully exists.
4. **Proof must be real.** Formats that lean on receipts (story-with-receipt, behind-the-scenes) only work with the operator's actual numbers — from the profiles, the tracker, their pieces, or asked for directly. If no real number exists, pick a format that doesn't need one. Never manufacture a metric, a milestone, or an "I did X" story.
5. No external links in the note body by default — link bursts measurably suppress reach (see the reference). Tease the newsletter; don't link it. If the operator insists on a link, say what it costs and put it in a comment-style follow-up suggestion instead.
6. Offer one variant if the operator wants options; otherwise ship one strong note, not five drafts.

### Batch — a week of notes

1. Ask (or read from the tracker) where they are: brand new on Notes, building, or established. Default cadence per the researched ramp: roughly 1–3/day in the first couple of months, 3–5/day once established — and note the credible dissent that ~1/day plus heavy commenting on others' notes is the better play under a few hundred subscribers. Agree on the week's count before writing.
2. Mix formats across the week per the rotation — and respect the **80/20 rule**: at least 8 in 10 notes pure value or generosity, at most 2 in 10 softly teasing the newsletter or paid tier. Count promotional notes in their last 10 posted (ask, or check the tracker) and rebalance if drifting.
3. Assign each note a day and a slot (morning community-style, midday teach-one-thing, evening reflection — the tested daily shape; details in the reference).
4. Include the **restack routine** in the plan — restacking is the strongest distribution signal as of mid-2026: each day, restack-with-comment one or two same-audience writers; 1–2 days after publishing a post, restack your own announcement note with a new line.
5. Write the batch to `workspace/substack/notes/YYYY-MM-DD-<slug>.md` with frontmatter (`status: draft`, `notes: <count>`, `week-of: <date>`) and each note under a `## Day N — <slot> — <format>` heading.
6. Posting: Substack shipped native Note scheduling in spring 2026 — one note at a time, up to ~3 months out. The operator schedules or posts manually; this skill never posts. Spaced through the day beats clumped.

### Atomize — published post → notes

1. Get the source: a piece folder under `workspace/content/pieces/<date>-<slug>/` (read the draft/final), or a published URL (WebFetch). Confirm which piece if ambiguous.
2. Extract the atoms: the 3–5+ strongest self-contained insights, data points, contrarian lines, and story beats. Yield rule from practitioners: one ~2,000-word post supports 3–5+ notes — roughly a week of material.
3. Reshape each atom into a *native note* per the taxonomy — conversational, standalone, ending in a question. An atomized note must not read like an excerpt or a headline-plus-link; it delivers value by itself and makes the full piece feel like the obvious next step without linking to it.
4. Save to `workspace/substack/notes/YYYY-MM-DD-from-<piece-slug>.md` with a `source:` frontmatter line pointing at the piece. Seed leftover atoms into `bank.md` under their formats.
5. Mention the reverse path once: notes that clearly outperform in the tracker are validated ideas — offer to expand a winner into a full piece when one shows up.

## Step 5 — Track (the habit that separates excellent from average)

Every Tier-1 practitioner in the research tracks **subscribers per note**. Substack doesn't expose per-note conversion natively, so the loop is manual and honest:

- When the operator reports results ("that confession note got 3 subs"), append a row to `tracker.md`. Record only what they report — never estimate or backfill numbers.
- When a batch run starts, glance at the tracker first and say what it shows: which formats are converting *for this operator*. Double down on those; keep rotating the rest.
- Likes get recorded but never drive decisions. The verdict column is about subscribers.

## Reach drops

If the operator reports falling reach, don't panic-post and don't guess — walk the 5-point diagnostic in `references/algorithm-and-cadence.md` (platform throttle → promotional drift → trust dip → posting window → recommendations gap) and prescribe only the matching fix. Doubling volume during a dip reads as instability and makes it worse.

## Honest expectations (say this when relevant, especially to a new operator)

Account trust compounds slowly: tracked practitioner data shows months 1–3 near-silent, months 4–6 ticking up, real compounding after that — the same note that died in month 2 can run in month 10. Most people quit at day 30–60, right before it turns. The skill's job in the quiet months is consistency and the tracker, not heroics.

## Guardrails

- **Never invent proof.** No fabricated numbers, milestones, client stories, or "I tried this" claims — real receipts from the operator's world, or a format that doesn't need them.
- **CTA is a question, never "subscribe."** Conversation is the conversion mechanism; subscribe asks live on the surfaces, sparingly (at most the 20% of the 80/20).
- **No external links by default** — and never "follow me for more," never a headline-plus-link repost dressed as a note.
- **Never post, schedule, or interact on the operator's behalf.** Drafts land in `workspace/substack/notes/`; the operator posts.
- **Tracker rows are operator-reported only.** No estimated metrics, ever.
- **Rotate formats; follow the tracker, not the applause.** Likes are recorded, subscribers decide.
