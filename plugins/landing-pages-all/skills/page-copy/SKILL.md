---
name: page-copy
description: Use when the operator needs copy for a landing page, sales page, homepage, service page, or opt-in page — "write my landing page", "I need a sales page for the course", "rewrite my homepage", "make a page for my lead magnet" — or when an existing page isn't converting and they want it rebuilt from their actual business and customers.
argument-hint: "[what the page sells — e.g. my course — or a URL to rewrite]"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebFetch, TodoWrite
---

# Page Copy — write the page from the operator's world

Write landing/sales/opt-in page copy from this operator's business, audience, and customers' own words — never from the average of every page in the niche. The method composes what's actually working as of mid-2026: Harry Dry's landing page anatomy, Julian Shapiro's conversion equation (Desire − Labor − Confusion), Fletch PMM's homepage order for B2B, Joanna Wiebe's message mining and Rule of One, and Matt Lerner's language/market-fit headline process.

**Output home:** one piece folder per page — `workspace/content/pieces/YYYY-MM-DD-<slug>/` (create with `mkdir -p`; the slug names the page, e.g. `course-sales-page`). Two files: `brief.md` (decisions, customer-language table, headline variants, proof gaps) and `copy.md` (the deliverable, `status: draft`). Nothing is ever published. Present it however relays the information best — tables, charts, visuals, plain prose: whatever you judge serves the reader.

Track progress with `TodoWrite` — one todo per step below.

## Step 1 — Read the context profiles

Read all four before anything else:

1. `context/user.md`
2. `context/business.md`
3. `context/ICP.md`
4. `context/tools.md`

`business.md` and `ICP.md` are load-bearing: the offer, pricing, positioning, and proof come from business.md; the reader's frustrations, aspirations, objections, and language come from ICP.md. A page that could have been written for any operator in the niche has failed before it starts.

**If a profile is missing or empty:** say which one and continue. Degrade honestly — interview the operator for what the missing profile would have supplied, and never invent facts to fill the hole.

**Client pages:** if the page is for a client (the operator serves clients and this is their client's offer), read `context/<client>/` profiles instead for business/ICP facts, and respect the operator's naming convention (codenames if `context/clients.md` exists).

## Step 2 — Scope the page

Settle five things — infer what you can from the profiles and the ask, confirm with the operator, ask only what's genuinely open:

1. **The offer** — which product/service/opt-in from business.md this page sells. One page, one offer (Wiebe's Rule of One).
2. **The one reader** — a specific person, not a demographic. For B2B, pick the *champion*: the person closest to the pain, not the budget holder (Fletch). If the operator wants one page for two audiences, propose routing them to separate paths or pages — never average the message.
3. **Awareness stage** — where this reader starts: problem-aware, solution-aware, or product-aware (Eugene Schwartz's stages, still the targeting layer everything builds on). Less aware = longer page that starts at the pain; most aware = shorter page that starts at the offer. Note for 2026: visitors arriving from AI assistants have usually read a summary first and land more aware than cold traffic — if AI referrals matter to this operator, the page top should respect that.
4. **The archetype** — offer/sales page, service page, SaaS-style homepage, or opt-in page. Selection logic and section orders: [references/page-anatomies.md](references/page-anatomies.md).
5. **Rewrite or fresh** — if an existing page is being rebuilt, fetch it with WebFetch and note what to keep (real proof, working sections) and what's underperforming. If the fetch fails, ask the operator to paste the current copy.

## Step 3 — The voice rule

Check for a matching voice-profile skill before drafting — the operator's own voice for their page, the client's voice for a client page.

- **If one exists:** invoke it. It governs diction, rhythm, and quirks everywhere, and is decisive in the hero, the founder's note, and FAQ answers — the places a person is supposed to be audible.
- **If none exists:** say so, and offer two paths — build one now (the Voice plugin), or proceed with voice inferred from the context profiles (origin story, voice signals in user.md). Never produce in a generic default voice.

Structure and claims come from this skill's method; the voice decides how the sentences sound. For solo operators that means first-person singular and no fake corporate "we" — personality is a trust signal on these pages, not a risk.

## Step 4 — Mine the customer language

The single biggest lever this skill has (Wiebe's message mining; Lerner's language/market fit — his published case work shows headline language alone moving conversion from low single digits to 30%): headlines and leads built from words real customers used, near-verbatim, not invented.

Sweep for voice-of-customer material, in this order:

1. **The workspace** — `Grep`/`Glob` for testimonials, client emails, call transcripts, reviews, DMs the operator has filed (check `workspace/`, `wiki/` if present, ICP.md's language section).
2. **The operator** — ask them to paste real customer messages: "the last 3 things a customer said when they bought, and the last 3 questions people asked before buying." Pre-sale questions are objections in their native form.
3. **URLs they point at** — their own testimonial page, public reviews of their offer or of competing solutions. Fetch with WebFetch only what they point you to.

Build a small table in `brief.md`: verbatim phrase · tagged as pain / goal / objection / outcome · source. Frequency matters — a phrase three customers used beats a clever phrase nobody said.

**If no VOC exists at all:** say so plainly, fall back to ICP.md's language plus a short interview ("when someone describes the problem to you, what exact words do they use?"), and mark the brief: built without customer-verbatim material — collect real customer language and revisit the headline.

## Step 5 — Derive the value proposition

Three moves, written into `brief.md` before any copy:

1. **Name the bad alternative** — what the reader does today instead of buying (a competitor, a workaround, nothing). (Shapiro's sequence.)
2. **State how this offer beats it** — concretely, in one sentence, using the mechanism that makes it true.
3. **Convert to an action statement** — what the reader can now do that they couldn't.

For B2B/SaaS pages, add the Fletch layer: the champion's concrete activities (use cases), the current solution's limitation, and the capability → feature → benefit chain — leading with the capability (what the user can *do*), since informed buyers shop features, not benefit poetry. Default to an existing category the reader already understands; inventing a category is a funded-startup play, not an operator play.

## Step 6 — Headlines: twenty variants, then judge

Write **20 headline variants** in `brief.md` before judging any — the usable ones reliably show up after the first dozen (Dry's practice rule). Spread them across the three lenses, then lint. Full craft rules: [references/copy-craft.md](references/copy-craft.md).

- **Lens A — explain:** state plainly what the offer is and does (earns the spot only if the offer is genuinely distinct).
- **Lens B — objection flip:** the reader's biggest objection (from the VOC table) pre-answered as a claim.
- **Lens C — own the niche:** the conviction one-liner for exactly this reader.

Lint every survivor: falsifiable (a claim that could be proven wrong — a number, a mechanism, a timeframe — beats any superlative) · ultra-specific · parseable by a stranger in 5 seconds · zero banned phrases. Present the strongest survivors with your reasoning; the operator picks or edits. Offer the cheap reality check: show the favorite to a few real humans for 5 seconds and ask what it said (Lerner's test) — note it in the brief if they do.

## Step 7 — Assemble the page

Draft section by section per the archetype's anatomy in [references/page-anatomies.md](references/page-anatomies.md) — trust that file for section orders and per-section framework choices; don't improvise a structure.

Standing rules while drafting:

- **Running narrative:** every section below the fold exists to prove the hero's single promise. A section that proves nothing gets cut.
- **Claim–proof adjacency:** every claim sits next to its receipt — a number, a named result, a testimonial that validates *that specific claim*. Distribute testimonials beside the claims they back, never in one wall.
- **Proof gaps are flagged, never filled:** where a claim has no receipt, write `**[PROOF GAP: <what's needed — e.g. one student result with a number and timeframe>]**` inline and list it in the brief. Fabricating a testimonial, count, or result is the one unforgivable failure of this skill.
- **Objections get answered on the page:** every pre-sale question from Step 4 gets an answer, in the features/objections section or the FAQ — in the customer's own framing. (Unanswered objections are the most common paid-teardown finding.)
- **The FAQ does double duty:** it ties up loose objections for the reader, and it's the most machine-parseable section of the page for AI assistants that pre-sell visitors — plain questions, direct answers, the offer named unambiguously. Frame this as AEO; never frame any of this work as SEO.
- **Visuals are directions, not decoration:** mark what each visual slot must show — the real product, the real person, the real work. "Get as close to reality as possible" (Dry); for solo operators the person *is* the product shot.

## Step 8 — The CTA pass

Walk every call-to-action on the page against the craft rules (details in [references/copy-craft.md](references/copy-craft.md)):

- Button copy completes "**I want to ___**", first person, specific — call-to-value, not call-to-action ("Get my heatmap", not "Sign up").
- Objection-handling microcopy beside the button (price, time, risk — whichever objection lives closest to the click).
- Long pages carry 3–4 CTAs: top for the already-convinced, mid-page after proof, bottom after FAQ/guarantee. A repeated CTA restates the argument in one line — never a bare button.

## Step 9 — The quality pass

Run the full battery in [references/qa-pass.md](references/qa-pass.md) against the draft — the five-second test, the in-person sell test, falsifiability density, the AI-slop scan, the halve-the-page cut. Record results and what changed in `brief.md`. Fix what fails before showing the operator; don't present a draft you know fails the battery.

## Step 10 — Save and report

Write the final files:

- `copy.md` — frontmatter (`title`, `type: page-copy`, `archetype`, `status: draft`, `date`, `voice:` which profile or "inferred from profiles") + the page, section by section, with visual directions and any proof-gap flags inline.
- `brief.md` — the one-reader card, awareness stage, value-prop derivation, VOC table, all 20 headlines with the lint verdicts, the proof-gap list, the QA record.

Share the results in chat; surface every proof gap the operator needs to fill and make the next step clear. If they want the copy turned into a real page, `/landing-pages:build-page` picks up from this folder — mention it once, don't chain into it.

## Guardrails

- **No invented proof, ever.** No fabricated testimonials, customer counts, revenue numbers, or results — proof gaps get flagged for the operator to fill. Facts come from the profiles, the VOC material, or the operator, with nothing rounded up.
- **Customer words beat clever words.** When a real customer phrase and an invented phrase compete for the headline, the customer phrase wins.
- **One reader, one offer, one promise per page.** Multi-audience requests get routed, not averaged.
- **Voice rule always.** Matching voice profile invoked, or the two-path offer made — never a generic default voice.
- **Plain claims over superlatives.** The banned-phrase list in copy-craft.md is enforced, not advisory. Specifics are the style.
- **Never auto-publish.** The deliverable is copy in a piece folder. Posting, deploying, and sending are the operator's moves.
