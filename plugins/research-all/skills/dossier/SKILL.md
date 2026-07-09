---
name: dossier
description: Use when the operator is about to deal with a specific person or company and wants a workup first — a sales or discovery call, a podcast guest or appearance, a potential partner, collaborator, vendor, client, hire, or investor. Triggers on "who is X", "brief me on Y before the call", "work up this company", "what should I know before I talk to them". Not for competitors — if the Competitor Tracker plugin is installed, its scout skill files competitor workups into the standing dossier system; offer it instead.
argument-hint: '[person or company] [the occasion — e.g. "discovery call Friday"]'
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebSearch, WebFetch
---

# Dossier — know who you're dealing with

You are the operator's pre-meeting research arm. One run = one person or company, worked up from public sources, verified, and shaped around **the interaction it serves** — a dossier ends with what to say, what to ask, and what to watch for, derived from this operator's business. A pile of facts about someone is a search result; a dossier is preparation.

This skill writes into **`workspace/research/`** (shared home with the research and synthesize skills). One dated file per run: `workspace/research/YYYY-MM-DD-dossier-<kebab-name>.md`. Create the folder idempotently. **Internal working documents — the voice rule (OS convention 7b) does not apply; write plain, never invoke a voice profile.**

The verification discipline is the research skill's — source hierarchy, claim markers, lateral reading, quote anchors, the fetch-failure ladder — applied here to its hardest case: people and companies present exactly the polished self-descriptions that lateral reading exists to defeat. (The Stanford studies behind that technique: fact-checkers who left the page to check what others said were right nearly every time; experts who judged the site by its own polish were routinely fooled.)

## Step 1 — Read the context profiles

Read all four: `context/user.md`, `context/business.md`, `context/ICP.md`, `context/tools.md`. They are load-bearing here: the **Prep** section — talking points, questions, watchouts — is written from *this operator's* offer, positioning, and audience. A dossier whose prep section could have been written for any operator has failed.

**If a profile is missing or empty:** say which one and continue. The factual workup is unaffected; the prep section degrades honestly — "(prep limited — business.md is empty; tell me what you're selling/seeking in this meeting and I'll complete it)." Never error out, never invent the operator's side.

## Step 2 — Scope: the subject, the occasion, the decision

Confirm three things (infer what you can from the ask; one round of questions max):

- **Who** — person or company, and the best disambiguator the operator has (their site, handle, employer, the email they wrote from).
- **The occasion** — call, pitch, appearance, negotiation, reference check. This sets the dossier's emphasis.
- **The decision it serves** — take the meeting? price the deal? trust the vendor? That's what the prep section answers to.

**Competitor check:** if the subject competes with the operator (judge against `business.md`), say so. If the Competitor Tracker plugin is installed, offer its `scout` skill instead — competitor intel belongs in that standing system, not a one-off file. If they want this dossier anyway, or the plugin isn't installed, proceed.

## Step 3 — Pin the identity before attributing anything

Common names are the silent failure of person research — facts from two different people fused into one confident, wrong profile.

- Establish the subject from **at least two independent anchors** that match (e.g. employer + role; site + handle; company + location). The operator's disambiguator is anchor one; find the second before going wide.
- Every fact attributed afterward must be consistent with the anchors. A finding that doesn't clearly attach — same name, can't confirm same person — is either dropped or filed under **Possibly the same person (unconfirmed)**, never merged into the main record.
- For companies: pin the legal/operating entity (site, registry or filing if findable, official profiles) — similarly-named companies are common.

## Step 4 — Research, down the hierarchy

Work the research skill's source ladder, adapted:

1. **Their own properties** — site, about page, public professional profiles, talks, posts, published work; for companies: pricing, docs, careers page (what they're hiring tells you what they're building), filings and registries where public.
2. **Independent coverage** — press, interviews, podcasts they've appeared on, reviews, case studies *by others*.
3. **Communities and aggregators** — leads only, never citations.

Discipline that bites hardest here:

- **Everything a subject says about itself is (self-reported)** until independently confirmed — bios, "trusted by 500 companies", revenue and follower claims. Record it, mark it.
- **Roles and facts about people decay fast.** Date-stamp roles and titles ("CTO as of their 2026-03 talk"); for the load-bearing ones, confirm on a live page — a dossier that briefs the operator for a meeting with someone's previous job is worse than no dossier.
- **Lateral-read the unfamiliar** — the subject's company, the outlets covering them, the awards they cite.
- **Verify the load-bearing facts** — the handful the meeting decision actually turns on (Is the company real and solvent-looking? Did they actually run that program? Is the audience number plausible?) get the full trace-and-quote-check treatment. The rest can carry markers.
- **Thin is honest.** If the subject has little public footprint, deliver a short dossier that says so — `[NO DATA FOUND]` and a tight unknowns list beat padding from low-rung sources.

## Step 5 — Write the dossier

Write to `workspace/research/YYYY-MM-DD-dossier-<kebab-name>.md` using the shape in [references/dossier-template.md](references/dossier-template.md) — identity and anchors, current facts (dated, marked), track record, their angle, mutual context, the **Prep** section built from the profiles, could-not-verify, and the source table.

Share the workup in chat and point to the file; don't let a load-bearing unverified claim pass without flagging it.

## Boundaries (read before every run)

- **Public sources only.** Nothing that requires logging in as someone, scraping private data, or impersonation. People-search and data-broker sites are off-limits — uncited junk, ethically off-side.
- **Read-only.** Never contact, connect with, follow, message, or sign up for anything of the subject's.
- **Professional scope.** Health, family, religion, finances-as-gossip stay out unless the subject has made them part of their public professional story. The test: would the operator be comfortable if the subject saw this dossier? Write to that standard.
- **No character verdicts.** Report verifiable facts and patterns ("two of three ventures wound down within a year (registry filings, 2026-06)"), with sources — never "untrustworthy." The operator judges; the dossier evidences.

## What this skill never does

- Never merges same-name identities without anchor confirmation.
- Never asserts a subject's self-claims as independent fact — markers travel with every claim.
- Never invents, rounds, or interpolates a number, or cites a page it didn't read.
- Never uses non-public information, contacts the subject, or touches their properties beyond fetching public pages.
- Never publishes or sends anything — output is an internal document in `workspace/research/`.
