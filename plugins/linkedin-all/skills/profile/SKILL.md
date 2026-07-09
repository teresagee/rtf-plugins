---
name: profile
description: Use when the operator wants their LinkedIn profile worked on — "rework my LinkedIn profile", "write me a better headline", "fix my About section", "my profile gets views but nothing happens", "set up my Featured section" — or before they start posting seriously, when the profile should be rebuilt as the landing page their posts will send traffic to.
argument-hint: [optional focus — headline, about, featured, banner — or blank for the full rebuild]
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebFetch
---

# Profile — your LinkedIn profile as a landing page

You rebuild the operator's LinkedIn profile so it works like a landing page with exactly one job. The principle (Justin Welsh's profile system, still the genre's foundation): a visitor reads a profile top-down like a sales page — so decide first what one action they should take, then make every element point at it. Mid-2026 raises the stakes: LinkedIn's ranking model reads the profile and posting history *semantically* and rewards topical match — the profile now also tells the algorithm what lane this person owns.

This skill owns one folder, shared with the other linkedin skills: **`workspace/linkedin/`**. The live profile copy lands at `workspace/linkedin/profile.md`. Create the folder idempotently (`mkdir -p`). Nothing is ever posted or published — the operator pastes the copy into LinkedIn themselves.

## Step 1 — Read the context profiles

Read all four before writing a word:

- `context/user.md` — name, origin story, expertise, voice signals
- `context/business.md` — the offer, pricing, channels, positioning
- `context/ICP.md` — who the profile talks to, their frustrations, their language
- `context/tools.md` — where things live (email platform, lead magnet, product pages)

All four are load-bearing here: the headline is built from `business.md` + `ICP.md`, the About story from `user.md` + `ICP.md`, the Featured section from whatever the operator actually has to link (`business.md` / `tools.md`). A profile rewrite that could belong to any operator has failed.

**If a profile is missing or empty:** say which one and continue. Degrade honestly — if `ICP.md` is empty, ask the operator two quick questions (who is this profile for, what's their main frustration?) and use their answers; never substitute a generic audience. Never error out, never invent facts the profiles don't contain.

## Step 2 — The voice rule

Profile copy is content in the operator's voice — the About section especially. Check for a matching voice-profile skill (the operator's own voice). If one exists, invoke it before drafting. If none exists: say so, and offer the two paths — build one first (the Voice plugin), or proceed with voice inferred from `context/user.md`'s voice signals and origin story. Never write the profile in a generic default voice. This matters double on LinkedIn in 2026: generic AI-pattern writing is detected and suppressed; first-person specificity is the antidote.

## Step 3 — Gather the current state

Ask the operator to paste their current profile — headline, About, Featured items, banner description, and (if they know it) which action they currently ask visitors to take. **Be straight about why you're asking:** LinkedIn profiles sit behind a login wall, so fetching their profile URL directly usually fails — pasted text is the reliable path. You may WebFetch the operator's *own* pages outside LinkedIn (lead magnet page, product page, newsletter landing page) to write accurate Featured copy.

If `workspace/linkedin/profile.md` already exists, read it first — it's the last known copy. Ask what's changed since.

## Step 4 — Decide the one action

Before drafting anything, agree with the operator on the single action a visitor should take. Derive the default from `business.md`: for most operators it's **joining the email list** — the top practitioners run LinkedIn as top-of-funnel into email, not as the destination (Lara Acosta, the biggest current LinkedIn-craft creator, reports ~80% of her revenue comes from email, not her 300K+ followers). If the operator's model points elsewhere (booked calls, a product page), use that. One action. Everything in Step 5 points at it.

Also name the **lane** — the one topic LinkedIn should associate with this profile. If `workspace/linkedin/strategy.md` exists (written by `/linkedin:plan`), use the lane it declares; don't invent a second one. If it doesn't exist, derive a lane from `business.md`, confirm it with the operator, and note that `/linkedin:plan` will make it official.

## Step 5 — Build the elements

Structures, formulas, and the dated-practices list are in [references/profile-structures.md](references/profile-structures.md) — follow it. In brief:

- **Headline** — a value proposition, not a job title: who you help, what they get, with the specificity only this operator can claim. Lane keywords live here naturally (search + semantic match), never stuffed.
- **About** — a PAS story (Pain → Agitate → Solution) written to one reader: the ICP. Their pain in their words, the stakes, then the operator as the proof-backed answer. First ~3 lines must survive truncation. Ends with the one action and exactly how to take it.
- **Featured** — exactly two items: one free (the email-capture asset) for visitors who aren't ready, one paid for those who are. Skip the item descriptions — less friction. Describe the image concept for each.
- **Banner** — a concept brief, not an image: the headline words, a sub-line, the visual direction, and where the CTA sits. It reinforces the same one action. The operator (or their designer, or an image tool) produces it from the brief.

**Anti-fabrication rule:** every claim, number, and credential in the copy comes from the context profiles or from the operator's mouth in this session. If a proof point would help but you don't have it, ask — or write around it. Never round, never embellish, never invent a result.

Give the operator real choices where they matter — headline variants worth comparing, for instance — and full drafts, not previews. Walk them through the reasoning and revise on their feedback.

## Step 6 — Save the live copy

Write the agreed copy to `workspace/linkedin/profile.md`:

```markdown
---
title: "LinkedIn Profile — live copy"
type: linkedin-profile
updated: <YYYY-MM-DD>
one-action: "<the single visitor action>"
lane: "<the topic lane>"
---

# LinkedIn profile

## Headline
<the live headline>

## About
<the live About copy, exactly as pasted into LinkedIn>

## Featured
1. **Free:** <item, link, image concept>
2. **Paid:** <item, link, image concept>

## Banner
<the concept brief — and, once made, where the asset lives>

## Changelog
- <YYYY-MM-DD> — <what changed and why>
```

Rewrite in place on later runs; append one changelog line per run. This file is what `/linkedin:posts` and `/linkedin:plan` read to keep the lane consistent. Present it however relays the information best — tables, charts, visuals, plain prose: whatever you judge serves the reader.

## Step 7 — Hand it over

Hand over the copy paste-ready and make the next step clear. Two practical notes to pass on, honestly sourced: Creator Mode is gone (retired March 2024 — follow-primary, newsletters, and analytics are now ordinary settings, so any old advice about "toggling Creator Mode" is stale), and the profile photo should be a clear face — LinkedIn's 2025 algorithm data shows images of real people significantly outperform faceless ones.

## What this skill never does

- Never logs into LinkedIn or changes the profile itself — the operator pastes everything.
- Never invents credentials, numbers, or results — profile copy is built only from the context profiles and what the operator said.
- Never writes in a generic default voice — voice skill first, or inferred from `user.md` with the operator's knowledge.
- Never gives the profile two jobs — one action, agreed before drafting.
- Never ships dated mechanics (Creator Mode references, "talks about" hashtags, keyword stuffing) — the blocklist in the reference file is binding.
