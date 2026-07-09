# Ideation method — audit, generate, score, write

The working method for the brainstorm skill, distilled from the practitioners with public product receipts as of mid-2026 (Dan Koe's productize-yourself derivation, Nicolas Cole's specificity-and-mechanism standard, Jay Clouse's premise-first architecture, Daniel Vassallo's small-bets counter-philosophy, Jack Butcher's productize-the-service pattern). The mechanics below are the synthesis; no one's copyrighted wording is reproduced.

---

## Part 1 — The asset scan: where to look, what it yields

| Location (skip silently if absent) | What to extract | Which asset dimension it feeds |
|---|---|---|
| `context/user.md` | expertise, origin story, transformations personally completed | 5 (transformations), 6 (intersection) |
| `context/business.md` | existing offers + prices (the current ladder), positioning | existing-product map; ladder-fit scoring |
| `context/ICP.md` | frustrations, aspirations, objections, exact language | 2 (audience questions), demand evidence |
| `context/tools.md` | platform stack, where things live | platform-fit scoring |
| `workspace/content/pieces/` | topics published (frontmatter: `status: published`), recurring themes, formats that repeat | 3 (traction topics) |
| `wiki/pages/` (if the wiki exists) | topic and pattern pages — the operator's own distilled knowledge | 1 (processes), 3 (topics), 6 (intersection) |
| `workspace/specs/` | SOPs and standing process docs — prime product material | 1 (processes) |
| `skills/` (top level, if present) | skills the operator built for themselves — encoded process, the strongest 2026-shaped asset for this audience | 1 (processes), 4 (artifacts) |
| `workspace/projects/` | systems built, dashboards, internal tooling | 1, 4 |
| `workspace/clients/` | the *generalized* method behind client work — never the deliverables, data, or (under codenames) names | 1, 4, 5 |
| `workspace/product/` | what already exists — extend or ladder around, never duplicate | ladder-fit scoring |
| `workspace/competitors/` | what the lane already sells, at what price; gaps and collisions | positioning context (facts about them only — never their framework names or wording as material) |
| `workspace/research/` | past research runs touching audience or market | 2, demand evidence |

Read economically: Glob for the map, then frontmatter and headings; full reads only where a candidate is taking shape.

## Part 2 — Candidate generation

**The spine (non-negotiable):** every candidate = **specific person × specific problem × named mechanism.**

- *Specific person* — a real segment of the ICP, in the profile's own words. "Creators" fails; the ICP's named trait and stage passes.
- *Specific problem* — one thing they'd pay to have removed. A problem the operator has evidence of (filed questions, ICP frustrations, client requests) beats one inferred from topic interest.
- *Named mechanism* — the systematic way THIS operator solves it. Working name only at this stage, invented fresh; the real name gets settled in scope. The test: does the name make the outcome feel doable and differentiated, or is it a generic label?

**Generation moves (use several, not one):**

1. **Asset-first:** take a strong row from the inventory and ask "who pays for this, packaged how?" — an SOP becomes a template system; a client method becomes a course; a personal transformation becomes a guided program; a skill the operator built becomes an installable product.
2. **Problem-first:** take the ICP's loudest frustration and generate 2–3 mechanism variants for it, differing in format (template pack / mini-course / membership), segment (beginner vs. operating), or model (one-time vs. recurring). Variants are how you find the right shape — present them as separate candidates.
3. **Ladder-gap:** look at `business.md`'s current offers and find the missing rung — no entry product under a flagship, no recurring layer, no free asset engineered to sell the paid one (the educational-email-course pattern: a short email course that delivers a real taste of the paid outcome, proven at scale by the Ship 30 operators).
4. **Service-first (thin workspace):** when assets are sparse, the credible sequence is a small consulting or done-for-you offer (commonly $500–$1,000 for a short engagement, per the practitioners who teach this path) — it pays now and *manufactures* the worksheets, dashboards, and process docs that become the product. Present this as a candidate, not an apology.
5. **AI-hybrid (the 2026 lane):** for an operator whose asset is a process Claude can execute, the emergent product shape is curriculum + the encoded process itself (prompts, a skill, a workspace template) — "the thing only this operator would think to build." Flag honestly: this lane is emergent with few public revenue receipts yet; it scores high on differentiation, unknown on demand unless the operator's own audience has asked for it.

**Volume:** 6–10 candidates. Fewer means the scan was thin (say so); more means you didn't filter.

## Part 3 — The scoring rubric

Six criteria, each 1–5, each with a justification grounded in the system. Scores are judgment calls made visible — the justifications exist so the operator can disagree with specifics.

| Criterion | 5 looks like | 1 looks like |
|---|---|---|
| **Receipts** | derived from an asset that exists at a path you can cite, already in real use | brainstormed from thin air; nothing in the workspace backs it |
| **Specificity** | named buyer + one paying problem + a mechanism you could explain in a sentence | "helpful content for my audience" |
| **Demand evidence** | repeated, filed questions or client requests for exactly this; ICP frustrations name it | none found — **score `?`, not a guess** |
| **Platform fit** | sellable today on the stack in `tools.md`, no new infrastructure | requires a platform, audience, or capability the operator doesn't have |
| **Effort to first sale** | deployable asset, shippable in days; small-bet sized | months of production before anyone can pay |
| **Ladder fit** | fills a real gap in the current price architecture or feeds an existing offer | duplicates an existing offer or floats free of the ladder |

**Rules:**
- `?` is a score. Any candidate with a `?` shows its total as a range (e.g. "21–25 of 30").
- Demand evidence can only come from the system (profiles, filed questions, client asks, traction data the operator actually has). Outward demand checking is scope's evidence scan.
- Effort scoring leans implementation-first: the mid-2026 buyer signal across independent sources is deployable systems over long-form video courses (one widely-cited "templates outsell courses 3:1" figure exists but is weakly sourced — treat as directional, never cite as fact).

## Part 4 — The brainstorm doc: frontmatter + required content

File: `workspace/product/ideas/YYYY-MM-DD-<focus-or-"product-brainstorm">.md`

Frontmatter (required, exactly these fields):

```markdown
---
title: "Product brainstorm — <YYYY-MM-DD>"
type: product-brainstorm
date: <YYYY-MM-DD>
focus: <the operator's focus argument, or "open">
profiles-missing: <list any empty/missing context profiles, or "none">
---
```

The doc must carry all of the following — compose it however reads best:

- The standing disclaimer, stated up front: scores are judgment calls made visible, not measurements; `?` = no evidence found in the system; ranges reflect unknowns.
- **The asset inventory** — all six dimensions, what was found (with workspace paths), and each dimension's honest strength mark (strong / thin / empty), plus what the inventory means, including what's empty.
- **The ranked candidates** — each carrying its full spine (specific person in ICP language; the one problem they'd pay to remove, with the evidence or "(hypothesis)"; the working mechanism name), its type and price band from the taxonomy, the workspace paths of its source assets, the honest case for why now, and the open question validation must test first.
- **The scoring** — every candidate against all six criteria, each score with its justification; candidates with a `?` show their total as a range.
- **What I didn't suggest, and why** — ideas considered and cut, with the reasoning.
- **The next step** — pick one → `/digital-products:scope <candidate name>`.
