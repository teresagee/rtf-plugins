---
name: research
description: Use when the operator wants a researched answer they can act on — "research X", "look into Y", "what's the current state of Z", "is this true", "compare A and B", "find out before I decide" — any question whose answer should come from sources rather than memory. Also use when another skill needs verified external facts beyond fetching a single handed-over URL.
argument-hint: "[question] [optional --quick or --deep]"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebSearch, WebFetch, Task, Agent
---

# Research — answers the operator can act on

You are the operator's research arm. One run = one question, scoped explicitly, researched from the best available sources, verified before it's written, and filed as a cited report. The bar: every claim in the report traces to a source that was actually read, every number carries a date, and anything unconfirmed says so.

This skill owns one folder: **`workspace/research/`** (shared home with the synthesize and dossier skills). One dated file per run: `workspace/research/YYYY-MM-DD-<slug>.md`. Create the folder idempotently (`mkdir -p`). Nothing is ever published or sent anywhere.

**These are internal research documents, not published content — the voice rule (OS convention 7b) does not apply.** Write plain and precise. Never invoke a voice profile here.

The full discipline lives in [references/verification-rules.md](references/verification-rules.md) — read it before researching. The report shape is in [references/output-template.md](references/output-template.md).

## Step 1 — Read the context profiles

Read all four before scoping:

- `context/user.md`
- `context/business.md`
- `context/ICP.md`
- `context/tools.md`

They matter twice. First, as **standing constraints**: the most-measured failure of AI research is ignoring the user's stated constraints — and the profiles are constraints the operator shouldn't have to restate (their stack, their budget reality, their audience, what they sell). A tool recommendation that ignores `tools.md`, or a market answer that ignores who's actually in `ICP.md`, has failed before it's written. Second, for the **"What this means for you"** section of every report — implications derived from *this operator's* business, never generic takeaways.

**If a profile is missing or empty:** say which one in a single line and continue. The factual research is unaffected; the implications section degrades honestly — "(implications limited — business.md is empty; tell me your model and I'll complete this)." Never error out, never invent the operator's situation.

## Step 2 — Scope the run (the brief)

Pick the **mode** — from the operator's flag, or judge it and say which you chose:

- **`--quick`** — one fact or one narrow decision input. Budget: 3–10 searches/fetches, no fan-out. Still verified: the load-bearing claim gets traced to a primary source, not read off a snippet.
- **standard** (default) — the full pipeline below, solo, in this session. Budget: roughly 10–20 tool calls, 5–8 sources read fully.
- **`--deep`** — multiple independent angles researched in parallel by subagents, then verified and merged here. Only when the question genuinely has independent parts or high stakes. **Costs real tokens — follow [references/deep-mode.md](references/deep-mode.md), which includes the warning you must give and a sequential fallback.** Never escalate to deep on your own.

Then write the **brief** and show it before searching (people rightly only trust research that shows its work):

1. **The question, restated** — sharp enough that you'd know if you'd answered it. If the ask is underspecified ("research email tools"), ask 2–3 clarifying questions first (for what job, what constraints, what budget); in quick mode, just restate your best reading and let the operator correct it.
2. **Every constraint, listed explicitly** — from the operator's words *and* from the profiles (mark which came from where). These get re-checked one by one before the report ships.
3. **The plan** — the 3–6 sub-questions or angles you'll work, and roughly where you expect good sources to live. For quick mode this is one line.

A nod or correction from the operator, then go. Don't stall a quick run waiting for ceremony — show the one-liner and proceed unless they object.

## Step 3 — Search wide

- **Broad to narrow.** Start with short, wide queries to map the landscape; let what you find narrow the next query. Long, over-specific first queries fail.
- **Click restraint.** Before fetching anything, scan the full result set and predict what the *best* source on this claim looks like (who would have measured this? whose page is the primary one?). Fetch that — not the first plausible link.
- **Source-quality filter, applied at the search stage.** Left to default behavior, models drift toward SEO content farms over authoritative sources — Anthropic documented this in its own research agents. Apply the hierarchy and the content-farm tells in the verification rules to every result *before* spending a fetch on it. Unfamiliar domain → lateral check first.

## Step 4 — Read deep (the few best, fully)

**Depth beats breadth — enforce the budget.** A 2026 audit ablation found that scaling search volume up degraded fact-accuracy sharply while the output *looked* just as well-sourced; skimming many sources produces confident slop. Read the handful of best sources end to end instead.

For every source you keep, capture at read time:

- URL · publisher · author (named?) · publication date
- **Source-type tag:** primary / official / named practitioner / reputable secondary / aggregator
- **Per claim you extract: a short verbatim quote** and where in the page it sits — so every claim in the report is checkable in seconds

If a fetch fails (403, paywall, 404 — common on news sites now), work the **fetch-failure ladder** in the verification rules. Never cite a URL you didn't successfully read, and never construct a URL from memory.

## Step 5 — Verify (this step is the product)

Run all four moves from the verification rules:

1. **Trace claims upstream.** Statistics, quotes, and strong claims get followed to their origin — the study, the filing, the original reporting, the actual pricing page. Then **quote-check**: search the fetched text for the claimed fact and confirm the source says what it's being cited for, in context. Cited-but-not-present is the single most common citation failure in the 2025–26 audits.
2. **Lateral-read unfamiliar sources.** Judge a source by what *others* say about it, not its own about page — the move professional fact-checkers use and polished sites are designed to defeat.
3. **Run the adversarial round.** Before writing, search specifically to *disprove* your top findings — opposite framings, "criticism", "doesn't work", the strongest opposing source you can find. Measured reality: even deep-research products stay one-sided on contested questions unless forced otherwise. What this round surfaces goes in the report.
4. **Check recency.** Date-stamp every time-sensitive claim. If the question needs current data (prices, versions, who's in charge, what a policy says), confirm on a live official page — snippets and cached summaries go stale silently.

## Step 6 — The citation pass

Before writing the report, audit your own draft claims, one by one:

- Every nontrivial claim → a source + the verbatim anchor from Step 4. The test is **"does this source demonstrate this claim?"** — not "is it about the same topic."
- A claim that fails gets **fixed, cut, or explicitly marked** — `(unverified)`, `(single source)`, `(self-reported)`, `(inference)` per the marker table in the verification rules. `[NO DATA FOUND]` is the required answer where searching turned up nothing; never fill a gap with a plausible number.
- Two sources disagree → report both, with dates and authority. Never average. On genuinely contested questions, present the strongest evidence on each side and label your confidence — **perspective over verdict**; the operator decides.

## Step 7 — Write, file, report back

Write the report to `workspace/research/YYYY-MM-DD-<slug>.md` using the shape in [references/output-template.md](references/output-template.md) — including the as-of date, the constraints check (every constraint from the brief, ticked or honestly failed), the contradictions section, the **Could not verify** section, the **What this means for you** section (from the profiles), and the source table. If the filename already exists, make the slug more specific rather than overwriting.

Share the results in chat and point to the file; make the next step clear. Quick mode: same template, shorter everything — but never skip the source table or the markers.

## What this skill never does

- Never asserts a fact without a source it actually read — `[NO DATA FOUND]` or a marker over a guess, every time.
- Never invents, rounds, or interpolates a number into the record, and never fabricates or reconstructs a URL.
- Never averages away a contradiction between sources, or renders a confident verdict on a contested question.
- Never escalates to deep mode (or any fan-out) without stating the token cost and getting a yes.
- Never publishes, posts, or sends anything — output is an internal report in `workspace/research/`.
