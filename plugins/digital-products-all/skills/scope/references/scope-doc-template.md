# File shapes — the product folder

One folder per scoped product: `workspace/product/<slug>/`. Created idempotently; `<slug>` is the product's working name in kebab-case. Frontmatter blocks are required schemas; `[NO EVIDENCE FOUND]` and claim markers stay literal where they apply. Body content below is listed as *what each file must capture* — compose each doc however reads best for a human.

```
workspace/product/<slug>/
  scope.md                      ← the plan (this file's main shape)
  validation/
    evidence.md                 ← the problem-evidence scan, cited
    waitlist-email.md           ← Gate 1 draft (voice rule applies)
    survey.md                   ← Gate 2 question + placement
  build/                        ← created by build sessions, not by scope
```

**Status vocabulary** (frontmatter of `scope.md`, this folder's convention):
`scoped | validating | building | launched | killed`. Status moves only with the operator's say-so; a `killed` product keeps its folder — the reasoning in its decision log is worth more than the disk space.

---

## 1. `scope.md`

Frontmatter (required, exactly these fields):

```markdown
---
title: "<Product name> — Scope"
type: product-scope
status: scoped
date: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
brainstorm-source: <path to the ideas doc + candidate name, or "direct">
---
```

The doc must capture all of the following:

- **The spine**, stated up front: for the specific person (in ICP language), who has the problem they'd pay to remove, via the named mechanism.
- **Format — and why:** the chosen type from the taxonomy with the fit-filter reasoning made visible (platform stack, audience size, capacity mode), plus the runner-up format and why it lost — kept so a revision can re-decide cleanly.
- **The outline** (titles provisional until the survey harvest — say so in the doc): every module/part with its provisional title, the workspace path it's built from (or **[NEW WORK]**), and the concrete thing the buyer deploys. Plus the free companion asset — its shape and rough sequence — or "none for v1, because <reason>".
- **Price:** the ladder position (which rung this fills, feeds, or starts, mapped against the offers in `business.md`); the pole (cheap-volume / ascension-ladder / behind-the-subscription, and why); the band from the taxonomy file and the number inside it, with reasoning and cited competitive prices from the evidence scan where they exist; the founding price (discounted Gate-4 price, explicitly temporary); and what must be re-verified at build time (platform fees, anything priced from observation rather than a checkout page).
- **The validation plan:** every gate — waitlist email (50+ signups, read against list size), one-question survey (30–50 responses), interviews (~10 conversations), founding cohort (3–10 buyers at founding price) — each with its written go / re-angle / kill rule. If the no-list path applies, Gates 1–2 are replaced by the service-first engagement with its own go/kill terms.
- **The build plan:** phases keyed to gates, every task labeled `[claude]` or `[operator]` (build output into `build/`; the operator does every send, publish, recording, and platform setup), ending with the first iteration loop — and a stated timebox (first version in days/weeks).
- **Evidence & unknowns:** the load-bearing findings from `validation/evidence.md`, plus everything still marked `[NO EVIDENCE FOUND]`, `(single source)`, or `(hypothesis)` — the honest section the operator re-reads before each gate.
- **Decision log (append-only):** each entry dated, with the decision, who made it, and the reasoning. Gate skips are recorded here with the operator's reasoning.

---

## 2. `validation/evidence.md`

Frontmatter (required, exactly these fields):

```markdown
---
title: "<Product name> — Problem evidence scan"
type: product-evidence
date: <YYYY-MM-DD>
method: "<searches run, pages fetched>"
---
```

The doc must capture, with every claim cited:

- **People discussing the problem** — findings with citations, and the exact phrases buyers use, quoted as language data. `[NO EVIDENCE FOUND]` if the scan came up empty.
- **Competing / adjacent products** — each with format, price (with as-of date), and source.
- **Failed attempts, in buyers' words** — what they tried that didn't work, cited; this is where the mechanism earns its difference.
- **Uncertainties** — single-source items marked `(single source)`, conflicts between sources, what to re-check.
- **Sources** — every page consulted, linked.

Corrections to an archived scan: prepend a flagged block at the top — `> **CORRECTION (<YYYY-MM-DD>):** <what was wrong, what's true>` — and leave the original intact.

---

## 3. `validation/waitlist-email.md`

Drafted under the voice rule (matching voice profile, or the explicit fallback). Never sent by Claude.

```markdown
---
title: "<Product name> — waitlist email (Gate 1)"
type: validation-asset
status: draft
date: <YYYY-MM-DD>
voice: "<voice profile used, or 'inferred from context profiles — no voice
skill installed'>"
---

Subject: <in the operator's voice>

<Short body: what's being considered, for whom, one link to join the
waitlist. No selling, no fake scarcity, no invented claims — the email
tests demand; it doesn't manufacture it.>

CTA: <single link/action — operator fills in the actual destination>
```

---

## 4. `validation/survey.md`

```markdown
---
title: "<Product name> — survey (Gate 2)"
type: validation-asset
date: <YYYY-MM-DD>
---

**The question:** "What's the #1 thing you'd want covered about <topic>?"
(one question only — response rate is the asset)

**Placement:** <where it lives: post-signup redirect, reply-to-this-email, form link>

**Harvest protocol:** at 30–50 responses, cluster the exact phrases →
they replace the provisional module titles in scope.md and seed the
landing copy. The operator's jargon loses to the audience's words every time.
```
