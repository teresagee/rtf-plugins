---
name: build-page
description: Use when approved page copy needs to become a real page — "build the page", "turn the copy into HTML", "make this something I can put online" — after /landing-pages:page-copy has produced copy.md in a piece folder, or when the operator brings final page copy and wants a clean single-file page plus free deploy instructions.
argument-hint: "[piece folder — e.g. 2026-06-11-course-sales-page]"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebFetch, TodoWrite
---

# Build Page — approved copy into a page that can go live

Turn finished page copy into one clean, self-contained HTML file the operator can deploy for free — no frameworks, no build step, no dependencies that rot. This skill is a builder, not a writer: the copy goes in **verbatim**. If the copy needs changing, that's a `/landing-pages:page-copy` revision, not a quiet edit during the build.

**Output home:** the same piece folder the copy lives in — `workspace/content/pieces/<date>-<slug>/` gains `page.html` and `deploy.md`. Nothing is ever deployed or published by this skill.

Track progress with `TodoWrite` — one todo per step.

## Step 1 — Read the context profiles

Read all four:

1. `context/user.md`
2. `context/business.md`
3. `context/ICP.md`
4. `context/tools.md`

`tools.md` is load-bearing here: the email platform (for wiring the form), the domain situation, and any hosting the operator already has decide real choices below. If a profile is missing or empty, say which one and continue — ask directly for the facts you needed from it.

## Step 2 — Locate the copy

- Default: the piece folder the operator names, or the most recent `workspace/content/pieces/*/copy.md` with `type: page-copy`.
- If no page copy exists anywhere, stop and point to `/landing-pages:page-copy` — this skill doesn't draft.
- **Proof-gap check:** scan the copy for `[PROOF GAP: ...]` markers. Any found get listed, and the operator chooses per gap: supply the proof now, or cut that claim from the built page. A proof-gap placeholder never renders into HTML — a page can ship without a claim, never with a hole where its proof should be.
- If the copy's `status:` is still `draft`, confirm the operator considers it final before building.

## Step 3 — Design direction (three questions, not thirty)

Check `workspace/assets/` for brand material first (logo, colors, fonts, photos) — use what exists. Then ask only what's still open, at most:

1. **Accent color** — one. From their brand, or their pick.
2. **Type** — the system font stack (fast, safe default) or one named webfont they already use.
3. **Photos** — what real images exist: their headshot, product shots, work samples. For a solo operator the person is the trust signal; a page with their actual face beats any illustration.

Everything else follows the standards in [references/build-standards.md](references/build-standards.md) — including the anti-slop design guardrails (the template tells that make visitors discount a page on sight: stock gradient heroes, the identical three-card layout, default-font sameness).

## Step 4 — Build `page.html`

One file, everything embedded. Full standards in [references/build-standards.md](references/build-standards.md); the non-negotiables:

- **Copy verbatim** — every headline, sentence, and button word exactly as approved. The only text this skill writes is invisible plumbing: `<title>`, meta description (drawn from the hero, shown to the operator for a yes), and alt text for image slots.
- **Semantic structure** — real headings in order (one `h1`: the headline), sections matching the copy's anatomy, an actual `<footer>` with the legal/contact lines the operator wants.
- **Mobile first** — most traffic is phones; the page is designed at phone width and enhanced up, not the reverse.
- **Fast by construction** — no external JS, no font flashing, no thousand-line framework CSS. The whole file should stay light enough to load instantly on a bad connection.
- **Image slots, honestly marked** — where a real photo belongs, a clearly labeled placeholder block with exact dimensions and what must go there ("YOUR HEADSHOT — square, ≥800px"). Never a stock-photo stand-in presented as real, never a generated face.
- **AEO basics** — title and meta description that say plainly what the offer is; FAQ as real text in the page (machine-readable by being readable); the entity statement intact above the fold. Frame as AEO, never SEO.

## Step 5 — Wire the form

Read `tools.md` for the operator's email platform and use its embed pattern (per-platform patterns in [references/build-standards.md](references/build-standards.md)). The honest rule: **this skill cannot create a working form endpoint** — it builds the form to the platform's documented shape and marks exactly where the operator's real form ID/URL goes, then `deploy.md` walks them through getting that value (usually two minutes in their platform's dashboard).

If their platform is unknown or they have none: build the layout with a visibly marked non-functional form (`<!-- FORM NOT WIRED -->` plus a banner comment in deploy.md), and say so out loud. A form that silently swallows emails is worse than no form. If the embed pattern looks stale, verify against the platform's current docs with WebFetch.

## Step 6 — Preview and check

- Open it locally: `open workspace/content/pieces/<folder>/page.html` on macOS (on other systems, tell the operator to double-click the file — it opens in their browser).
- Walk the operator through the look at phone width and desktop width (resize the window, or use the browser's device toolbar).
- Verify: every CTA button present and pointing where it should · no `[PROOF GAP]` or placeholder text rendering · headings in order · image slots labeled · the page reads top to bottom as the approved copy.
- Apply visual fixes the operator asks for (spacing, color, size). Copy change requests get routed back: update `copy.md` via page-copy thinking first, then rebuild the section — the two files never drift apart.

## Step 7 — Write `deploy.md` and close out

Write deploy instructions **personalized to this operator** — their platform from tools.md, their domain situation — using [references/deploy-options.md](references/deploy-options.md) for the current free options (drag-and-drop hosting, Git-based hosting, and the put-it-on-your-existing-site path). Include the form-wiring step with their specific platform's dashboard path. Present it however relays the information best — tables, charts, visuals, plain prose: whatever you judge serves the reader.

Share the results in chat; make clear what still needs the operator before the page can go live. The deploy itself is always the operator's move.

## Guardrails

- **Never rewrites copy.** Approved words go in verbatim; edits route back through the copy file, never happen silently in HTML.
- **Never fakes function or proof.** No decorative forms that go nowhere unmarked, no invented logos/faces/screenshots, no placeholder testimonials. Unfinished things are visibly labeled unfinished.
- **One file, no dependencies.** No frameworks, no build tools, no CDN scripts — the page must still work, unchanged, years from now.
- **Never deploys, never publishes.** The skill ends at `page.html` + `deploy.md` in the piece folder. Going live is the operator's click.
- **Brand over template.** When in doubt, plainer and more personal beats glossier and more generic — generic-template polish reads as untrustworthy on operator pages.
