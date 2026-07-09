# Verification rules — the research discipline

This is the discipline behind every run. It adapts the verification frameworks that actually have evidence behind them — chiefly **SIFT** and lateral reading (Mike Caulfield and Sam Wineburg's fact-checking work, the standard taught in university libraries) plus Caulfield's newer AI-era extensions, and the engineering findings from Anthropic's own multi-agent research system — applied to what the 2025–26 audits show AI research actually gets wrong.

The orienting fact: **most AI research errors are not wild hallucination.** Caulfield's error taxonomy from systematic fact-checking work: the dominant failures are *conflation* (merging two adjacent claims into one wrong one), *misweighting* (treating a content farm like a primary study), and *bad synthesis* — plus, per large 2025–26 audits, claims whose own citations don't support them, ignored constraints, one-sided answers, and stale numbers. Every rule below targets one of those.

---

## 1. Source hierarchy (work down it; cite the highest rung you reached)

1. **Primary** — whoever measured, did, decided, or published the thing: the study itself, the official docs, the filing, the actual pricing page, the original reporting outlet, the dataset, the person's own statement on the record. *Prefer people who measured the thing over institutions repeating the number.*
2. **Named practitioners with receipts** — identifiable authors with a track record who show their work (data, method, worked examples).
3. **Reputable secondary** — established press and analysts. Usable, but trace the load-bearing facts upstream; cite the original, not the retelling. (Measured failure: AI engines routinely cite syndicated copies and misattribute the publisher — find the original.)
4. **Aggregators, SEO content, anonymous summaries** — leads only. Never the citation for a claim.

**Anti-content-farm tells** (left untold, models prefer SEO farms over authoritative sources — Anthropic found this in its own agents, so the filter is mandatory): no named author; no dates; listicle-shaped everything; affiliate links throughout; text that summarizes other coverage without adding a single firsthand fact. The 2025–26 web also carries **laundered synthetic content** — AI-written "reporting" on real-looking sites, and citation networks of sites quoting each other in a loop. The tell for both: no chain back to a primary act of finding-something-out. If you can't trace it, don't cite it.

## 2. The four verification moves

1. **Stop.** Fluency is not evidence. Before a claim moves toward the report, it needs a source that passes the moves below.
2. **Investigate the source — laterally.** Judge an unfamiliar source by what *others* say about it (search the outlet/author name, add "Wikipedia" to the query for unfamiliar outlets), never by its own about page. The evidence here is stark: in the Stanford studies behind this technique, professional fact-checkers reading laterally evaluated sites correctly almost every time, while most PhD historians and students reading the site itself were fooled by a polished front.
3. **Find better coverage.** Don't evaluate the page in front of you — ask "what is the *best* source on this claim?" and go read that. Click restraint: scan the whole result set, predict what good looks like, then fetch.
4. **Trace to the original, then quote-check.** Follow statistics, quotes, and strong claims upstream until you hit the primary source. Then search the fetched text for the claimed fact and confirm it's actually there *and means the same thing in context*. This mechanizes Caulfield's "track it down" move, and it targets the most common measured failure: across 2025–26 audits, links resolve and look topically relevant while the specific fact isn't in the source. His own field note applies — the error often shows up "around the 10th or 11th link"; only methodical checking catches it.

## 3. The three tests every citation must pass

1. The link resolves (and you actually fetched and read it — never cite from a search snippet, never construct a URL from memory).
2. The content is topically relevant.
3. **The specific fact is in the source.** Systems routinely pass tests 1–2 and fail 3. Test 3 is the one that matters; the verbatim anchor captured at read time is how you prove it.

## 4. Claim markers (attach inline; they travel with the claim everywhere it goes)

| Marker | Means |
|---|---|
| **(self-reported)** | the subject's own claim about itself, unconfirmed elsewhere |
| **(single source)** | exactly one independent source; treat as provisional |
| **(unverified)** | found it, couldn't confirm it — and the report says what was tried |
| **(inference)** | your deduction from evidence — state the evidence |
| **(contested)** | sources disagree — both sides reported with dates, never averaged |
| **(secondary only)** | the primary source was unreachable; cited from reputable secondary coverage |
| `[NO DATA FOUND]` | searched, found nothing — the only acceptable filler |

Same marker vocabulary as the rest of the Operator Library (the Competitor Tracker uses it too), so every file in the system reads the same way.

## 5. Numbers and dates

- **Date every number.** Prices, counts, versions, market sizes are snapshots — write the as-of date next to each ("$99/mo (their pricing page, 2026-06)").
- **No fabricated numbers.** Not rounded, not "approximately," not interpolated between two sources. Two sources disagree → report both with dates.
- **Recency is a requirement, not a vibe.** If the question needs current data (prices, versions, leadership, policy, anything "as of now"), confirm on a live official page. The measured pattern: when recency is explicit, accuracy stabilizes; when it's merely implied, models serve stale cached figures as current.

## 6. Depth over breadth (the budget is a quality control)

Read few sources fully rather than many shallowly. The sharpest 2026 ablation on this (stats as reported): scaling a research agent from a handful of searches to ~150 dropped fact-check accuracy by roughly 40 points while the surface metrics — working links, relevant-looking citations — held steady. Volume manufactures false confidence. Budgets: quick = 3–10 tool calls; standard = 10–20, with 5–8 sources read end to end; deep = per-angle budgets in the deep-mode reference. **Stopping rule:** when the last two searches added nothing new, stop — don't search endlessly for a source that may not exist.

## 7. The adversarial round (mandatory before writing)

Borrowed from the "another round" command in Caulfield's Deep Background fact-checking design: before the report is written, run searches built to *disprove* the top findings — the opposite framing, "X criticism", "X failed", "X alternatives", the strongest opposing practitioner. Audits consistently find even premium deep-research modes one-sided on contested questions; this round is the structural fix. Whatever it surfaces goes in the report — a contradiction found is a finding, not a problem.

## 8. Confidence and contested questions

- Label confidence honestly; **"could not verify" is an acceptable answer** and goes in its own section. The measured trap runs the other way — premium tiers were *more* confidently wrong because they declined less.
- On contested questions, present the strongest evidence on each side, with sources, and let the operator decide — **perspective over verdict.** (Deep Background deliberately dropped its verdict section because users fixated on it; the perspective format survived.)

## 9. Fetch-failure ladder (403s, paywalls, 404s)

Bot-blocking on news and publisher sites is now routine. When a fetch fails:

1. **Alternate reputable coverage** of the same fact — then trace toward the original from there.
2. **Archive or cached copy** of the page (e.g. an archive.org URL for the same address) — mark the access path in the source table.
3. Still nothing → the claim carries **(unverified)** or **(secondary only)**, or gets cut. Never present a claim as verified on the strength of a page you couldn't read.

Also: fetch the specific article URL, not interactive or index pages — there's no browser here, one shot per page.

## 10. Constraints check (the last gate before shipping)

Re-read the brief. Walk every constraint — the operator's stated ones and the ones drawn from the context profiles — and mark each: honored / not applicable / could not satisfy (with why). The single most common practitioner complaint about deep-research products is silently ignored constraints (wrong location, wrong eligibility, wrong budget). A report that fails a constraint and says so plainly is useful; one that hides it is worse than no report.
