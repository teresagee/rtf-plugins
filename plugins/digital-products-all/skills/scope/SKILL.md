---
name: scope
description: Use when the operator has picked a product idea and wants it made buildable — "scope the template pack", "let's do #2 from the brainstorm", "turn this idea into a real product", "what would it take to build X" — whether the idea comes from a brainstorm doc or arrives raw in conversation. Also use when an already-scoped product's plan needs revising after validation results come in.
argument-hint: "[the idea — a candidate name from the brainstorm doc, or describe it]"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebSearch, WebFetch
---

# Scope — turn one idea into a buildable product plan

You are the planning arm of the operator's product work. One run = one idea, taken from "that could work" to a written scope: format chosen with reasons, an outline tied to real assets, a price with a place in the ladder, a validation plan with thresholds that gate the build, and a phased build plan Claude executes with the operator inside this system. The standing rule, from every practitioner who has published their numbers: **money or a met waitlist threshold validates a product; enthusiasm does not.** This skill's job is to make sure nothing big gets built before something small gets proven.

This skill owns **`workspace/product/`** (shared home with the brainstorm skill). Each scoped product gets one folder: `workspace/product/<slug>/` containing `scope.md` plus `validation/`. Create folders idempotently with `mkdir -p`. Nothing is ever published, sent, or sold by this skill — the operator presses every send button.

## Step 1 — Read the context profiles

Read all four before anything else:

- `context/user.md`
- `context/business.md`
- `context/ICP.md`
- `context/tools.md`

`tools.md` decides where this product can actually be sold; `business.md` decides where it sits in the ladder; `ICP.md` supplies the buyer and the starting language; `user.md` grounds the mechanism in real expertise.

**If a profile is missing or empty:** say which, continue, and degrade honestly — e.g. with an empty `tools.md`, the format section lists the platform-dependent choices as open and asks the operator what they sell on today. Never error out, never assume a stack.

## Step 2 — Locate and sharpen the idea

- If a brainstorm doc exists in `workspace/product/ideas/`, read the most recent one and pull the chosen candidate — its spine, source assets, and open validation question carry forward.
- If the idea arrives raw in conversation, that's fine — but it must pass the same gate before scoping continues:

> **The spine: specific person × specific problem × named mechanism.** If any leg is missing, fix it now with the operator — a scope built on "content creators who want to grow" will be generic all the way down.

**Mechanism naming:** if the mechanism has no real name yet, propose 3 candidates and let the operator pick. Names are invented fresh — never a competitor's framework or product name (if `workspace/competitors/` shows the lane's naming patterns, use that only to avoid collisions, not as source material). The test of a good name: it makes the outcome feel doable and signals *how*, not just *what*.

Also check `workspace/product/<slug>/scope.md` for this idea: if it already exists, this run is a **revision** — read it, keep the decision log, and update rather than restart.

## Step 3 — Problem-evidence scan (the outward check)

Before committing a week to anything, run a short web scan — the discipline practitioners describe as validating the *problem*, not the product. Use WebSearch to find, WebFetch to confirm. Look for three things:

1. **People discussing this problem** — forums, communities, comment sections; capture the exact phrases they use (this language feeds the outline and copy later).
2. **Competing or adjacent products** — what exists, at what price, in what format. A crowded shelf is demand evidence, not a disqualifier; an empty shelf is a question, not an answer.
3. **Failed attempts** — what buyers say they tried that didn't work; this is where the mechanism earns its difference.

Rules: every claim cited; **`[NO EVIDENCE FOUND]` is an acceptable and reportable result** — never pad it; prices and counts get an as-of date; anything from a single source is marked **(single source)**. This is a timeboxed scan (think minutes, not a research session) — if it surfaces a competitor worth a real workup and the competitor-tracker plugin is installed, suggest a scout run rather than doing one here.

Write the findings to `workspace/product/<slug>/validation/evidence.md` (frontmatter and required content in [references/scope-doc-template.md](references/scope-doc-template.md)).

## Step 4 — Choose the format

Walk the taxonomy in [references/taxonomy-and-price-bands.md](references/taxonomy-and-price-bands.md) and apply its three fit filters — platform stack, audience size, capacity mode — out loud, in the doc, so the operator sees why the format won:

- Bias **implementation-first**: the deliverable should be deployable, not just watchable. For an operator whose asset is a process Claude executes, weigh the AI-hybrid shape (curriculum + the encoded process itself) — flagging honestly that this lane is emergent with few public receipts as of mid-2026.
- Name the **runner-up format and why it lost**. Format choices age; the reasoning is what lets a future revision re-decide cleanly.

## Step 5 — Price it

Use the pricing architecture in [references/validation-and-pricing.md](references/validation-and-pricing.md):

- Place the product **in the operator's existing ladder** (from `business.md`) — entry, core, or backend — and say what rung it creates or fills. A price chosen in a vacuum is the documented average-operator mistake.
- Recommend a **band, then a number inside it**, with the reasoning. Bands come from the taxonomy file; the number comes from the ladder position, the evidence scan's competitive prices (cited), and the operator's pole — cheap-volume or ascension-ladder. Don't split the poles.
- Set the **founding price** — the discounted first-cohort price that trades margin for testimonials and co-creation, per the validation plan.
- Flag what must be re-verified at build time: platform fees move; the taxonomy file's bands are observation, not law.

## Step 6 — Outline the product

Module-by-module (or section/template-by-template) structure, with two disciplines:

- **Every part traces to a source asset.** Each module lists the workspace path it's built from (the SOP, the pieces, the client method generalized). A module with no source is new work — allowed, but marked, because unsourced modules are where build timelines die.
- **Every part ends in something the buyer deploys** — a template filled, a system installed, an asset shipped. "Understand X" is not a module outcome.

Mark all module titles **provisional**: the validation survey (Step 7) exists partly to harvest the audience's exact language, and the published titles should come from that harvest, not from the operator's jargon. Say this in the doc.

If the format wants a free companion asset (the educational-email-course pattern — a short sequence delivering a real taste of the paid outcome), outline it here too: it's part of the product's surface, not marketing to bolt on later.

## Step 7 — Write the validation plan (and draft its assets)

Build the gate sequence from [references/validation-and-pricing.md](references/validation-and-pricing.md), adapted to this operator's audience size — the thresholds are the published practitioner numbers, and they are the point:

- waitlist email → **50+ signups** before anything else happens
- one-question survey to the waitlist → **30–50 responses** harvested for exact language
- **~10 short interviews** with waitlisters (including the trigger question: what moment put you in the market for this?)
- **3–10 person founding cohort**, at the founding price, co-creating against testimonials
- **No list?** Swap the front of the sequence for the service-first path: sell a small consulting engagement on this exact problem first — it validates with money and manufactures the product's assets.

Each gate gets a written **go / kill / re-angle** rule. A missed threshold is the system working — the plan must say what happens then (usually: re-angle the problem and re-test, or kill and return to the brainstorm doc), so a weak signal doesn't get rationalized in the moment.

**Draft the two validation assets now**, into `workspace/product/<slug>/validation/`:

- `waitlist-email.md` — the one-email waitlist test
- `survey.md` — the single survey question and where it lives

**The voice rule applies here — this is audience-facing copy.** Check for the operator's voice-profile skill and invoke it before drafting. If no voice profile exists: say so, offer the two paths — build one (the voice plugin) or proceed with voice inferred from the context profiles — and never draft in a generic default voice. Drafts are saved, never sent; sending is the operator's button to press.

## Step 8 — Write the build plan

The phased plan Claude executes with the operator inside this system, gated by validation:

- **Phases keyed to gates:** nothing past the waitlist gate gets built before the waitlist clears, except the validation assets themselves and (if chosen) the free companion asset.
- **Every task labeled:** `[claude]` (drafting modules, turning SOPs into templates, encoding the process as prompts/skills, assembling the companion sequence — done in working sessions, output into `workspace/product/<slug>/build/`) or `[operator]` (sending the email, platform setup, recording, pricing buttons, every publish).
- **Timebox the build** small-bets style — a first version measured in days or a few weeks, not a quarter; the documented practitioner pattern is that the work *begins* at launch (relaunch, iterate, judge over multiple cycles), so the plan ends with the first iteration loop, not the first sale.

## Step 9 — Write scope.md and hand off

Write `workspace/product/<slug>/scope.md` with the frontmatter and required content in [references/scope-doc-template.md](references/scope-doc-template.md) — frontmatter status starts at `scoped` (vocabulary: `scoped | validating | building | launched | killed`, tracked in frontmatter as this folder's convention). Record today's choices in the decision log; on revisions, append, never erase. Present it however relays the information best — tables, charts, visuals, plain prose: whatever you judge serves the reader.

Share the scope however reads best; make the single next action unmistakable (and whose it is).

## What this skill never does

- Never publishes, sends, lists, or sells anything — drafts and plans only; the operator executes every outward action.
- Never green-lights building past an unmet gate silently — the operator can choose to skip a gate, but the choice is theirs and it's recorded in the decision log.
- Never fabricates market numbers — bands and benchmarks carry their mid-2026 provenance and self-reported flags; scan findings carry citations and dates; gaps stay `[NO EVIDENCE FOUND]`.
- Never borrows a competitor's framework names, product names, or wording — facts about them are intelligence; their language is theirs.
- Never writes audience-facing copy without the voice rule — matching voice profile, or the explicit fallback offer.
- Never invents the audience's language — module titles and copy phrases stay provisional until the survey harvest exists.
