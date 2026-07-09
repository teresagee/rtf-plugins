---
name: about-page
description: Use when the operator wants to write or rework their Substack About page, publication one-liner/tagline, or profile byline/bio — "write my About page", "my About page doesn't convert", "fix my tagline", "what should my bio say" — or when reworking the publication's positioning surfaces after a pivot.
argument-hint: [optional: URL of the current About page]
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebFetch
---

# About page — the page that closes the subscribe

You write the operator's About page, publication one-liner, and profile byline. These surfaces matter more than they look: tracked funnel data from one practitioner found ~96% of new subscribers decided on Notes and profile surfaces *before ever reading a full post* (self-reported, single source — but it matches how in-app discovery works). The About page is the landing page of the publication, and the one-liner is the highest-leverage sentence on it.

**Shared home (this plugin's owned folder): `workspace/substack/`.** This skill maintains one living file: `workspace/substack/about-page.md` — the current draft of the one-liner, byline, and full page, with `status:` and `updated:` frontmatter. Revisions edit this file; they don't spawn new ones.

The researched structures, formulas, and benchmarks live in [references/about-page-playbook.md](references/about-page-playbook.md). Read it before drafting.

## Step 1 — Read the context profiles

Read all four. Two are load-bearing:

- `context/ICP.md` — **read it hard.** The page is structured around the reader's 60-second evaluation, the one-liner must make the right reader say "that's me," and that's impossible without their frustrations, aspirations, objections, and language. Hooks and benefit lines get written in the ICP's own words.
- `context/user.md` — the origin story and real credentials; the only legitimate source of bio material.
- `context/business.md` — what the publication feeds (offer, pricing, paid tier if one exists — the page must agree with `workspace/substack/offer.md` if the offerings skill has run).
- `context/tools.md` — publication name, URL, where things live.

**If a profile is missing or empty:** say which one and continue. An empty `ICP.md` guts this page — draft what `user.md` and `business.md` support, mark every audience-dependent passage `[NEEDS ICP — who is this for?]`, and recommend filling the profile (or a 5-minute interview now) before the page goes live. Never invent an audience, a credential, or a subscriber count.

## Step 2 — Voice

This page is content — first-person, load-bearing. Check for the operator's voice-profile skill and invoke it before drafting. If none exists: say so, offer two paths — build one (the Voice plugin) or proceed by inferring voice from the context profiles — and never draft in a generic default voice. A technically perfect About page in nobody's voice converts nobody.

## Step 3 — Audit what exists

- If the operator gave a URL (or `context/tools.md` has the publication URL), fetch the live About page with WebFetch. If `workspace/substack/about-page.md` exists, read it.
- Score what's there against the playbook in one short pass: does line 1 pass the "that's me" test? Are the five core elements present? Does anything load-bearing appear in the first 200 words? How many subscribe buttons? Is there a single real proof point?
- Share what the audit found before proposing anything. If the page is genuinely good, say so and ask what prompted the rework — don't manufacture problems.

## Step 4 — Gather the true raw material

Interview briefly (5–8 questions max), only for what the profiles don't already hold:

- **Proof:** real numbers and receipts — years doing the thing, results produced, notable outcomes, subscriber count *if the operator wants it shown and it flatters*. Anything they can't back stays out.
- **Testimonials/press:** only ones that actually exist, quoted verbatim with permission. Never compose a testimonial.
- **Logistics:** what ships, how often, what's free vs paid (from `business.md` / `offer.md`, confirmed).
- **The origin moment:** the specific scene that explains why this publication exists — usually already in `user.md`; confirm the telling.

## Step 5 — Write the one-liner and byline first

These are the smallest, highest-leverage artifacts — and they discipline the page.

1. **Publication one-liner** (the description field): build it with the three-element formula in the playbook — *specific audience + the core need it serves + tangible outcome*. Test: would the ICP read it and say "that's me"? Draft 3 candidates, recommend one, let the operator pick. Note where it renders: homepage, recommendation cards, search results, welcome page — it works everywhere or nowhere.
2. **Discovery note (tell the operator):** Substack search indexes publication *titles*, not taglines — if discoverability matters, the operator's keywords belong in the title field, e.g. as a parenthetical. Flag it; the title is their call.
3. **Profile byline** (the personal bio, ~1–2 lines): pick the frame from the playbook that fits the operator's proof — who-you-help + transformation leads; credentials trail. Real headshot recommendation stands: people subscribe to people.

## Step 6 — Draft the page

Structure per the playbook — the reader runs *credibility check → value evaluation → belonging* in under a minute, so:

- **Open with one of the four researched moves** (bold claim, origin moment, the problem you solve, community welcome) — never "Hi, I'm [name], I'm a [title]."
- **Everything load-bearing in the first 200 words:** who it's for, what they get, why the operator, first subscribe button.
- **Three layers in order:** about you (story and stake, not résumé) → about the publication (what subscribers concretely receive: formats, cadence, free vs paid) → about the reader (their problem, the belonging line).
- **Five core elements present** (focus, bio, logistics, paid benefits, multiple subscribe CTAs — typically 3 buttons down the page).
- **Paid benefits as one stacked, bundle-framed list** — pull from `workspace/substack/offer.md` if it exists; otherwise from `business.md`, and suggest the offerings skill if the tier structure itself is fuzzy.
- **Social proof only where real.** A real count, a real testimonial, a real press mention. Nothing decorative, nothing invented.
- Optional layers (manifesto, featured posts, the B2B expense-it email template) only where the playbook's conditions genuinely apply.

## Step 7 — Save, hand off, set expectations

1. Write `workspace/substack/about-page.md`: frontmatter (`status: draft`, `updated:` today), then one-liner candidates, byline, and the full page in paste-ready blocks, each with a placement instruction (where in Substack settings it goes). Present it however relays the information best — tables, charts, visuals, plain prose: whatever you judge serves the reader.
2. The operator pastes it in — this skill never touches their Substack.
3. Set honest expectations once: typical About-page visitor→subscriber conversion runs ~1–3%, strong pages ~5% (practitioner-reported figures, not guarantees). The page compounds with Notes traffic; revisit it after pivots, or when the offer changes.

## Guardrails

- **Nothing invented:** no fabricated credentials, counts, results, testimonials, or press. A thin true page beats a rich fake one — gaps get marked, not filled.
- **ICP language over operator jargon.** If the page uses insider vocabulary the ICP wouldn't search for, rewrite it in their words (from `ICP.md`).
- **The page agrees with the system:** free/paid claims match `offer.md` and `business.md`; if they conflict, stop and reconcile rather than shipping a contradiction.
- **One living file** — revisions edit `about-page.md`, bump `updated:`, and note what changed at the bottom; no v2/v3 file litter.
- **Never auto-publish.** Draft in the workspace; the operator pastes.
