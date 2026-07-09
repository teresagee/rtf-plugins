---
name: welcome-sequence
description: Use when the operator wants their Substack welcome email or email sequences built — "set up my welcome sequence", "write my welcome email", "build my free-to-paid drip", "what do I send new paid subscribers", "write a winback sequence" — or after the offer or About page changes and the lifecycle emails need to match.
argument-hint: [welcome|free-to-paid|paid-onboarding|founding|winback|upgrade]
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Welcome sequence — the emails that convert quietly

You build the operator's lifecycle emails: the classic welcome email everyone has, and the campaigns for Substack's native email sequences ("drip campaigns") where the operator has the feature. This is where Notes-sourced subscribers — who skew free and convert to paid slower than other channels — actually become paid: the notes skill fills the list, the surfaces close the subscribe, the sequence converts the subscriber.

**Shared home (this plugin's owned folder): `workspace/substack/`.** This skill owns `workspace/substack/sequences/` — one paste-ready file per campaign, plus the welcome email.

What the native feature verifiably supports (and doesn't), plus the sequence frameworks and email craft rules, live in [references/sequences-playbook.md](references/sequences-playbook.md). Read it before building — the feature's real limits shape every design choice.

## Step 1 — Read the context profiles

Read all four:

- `context/ICP.md` — the reader these emails land on: objections (what the free-to-paid flow must answer), language (subject lines in their words), what they'd cancel over (winback material).
- `context/business.md` — the offer these emails sell; must agree with `workspace/substack/offer.md` if it exists (read that too — it's the source of truth for tier benefits).
- `context/user.md` — the real story and warmth; welcome emails are the most personal surface on the platform.
- `context/tools.md` — publication details.

**If a profile is missing or empty:** say which one and continue with what exists. Without `business.md` or `offer.md`, upgrade emails can't name real benefits — draft the relationship emails, mark the benefit slots `[NEEDS OFFER — run /substack:offerings]`, and say so. Never invent benefits, discounts, or claims.

## Step 2 — Voice

These are the most first-person emails the operator will ever send. Check for the operator's voice-profile skill and invoke it before drafting. If none exists: say so, offer two paths — build one (the Voice plugin) or proceed by inferring voice from the context profiles — and never draft in a generic default voice. A welcome email is a handshake; a generic one is a cold one.

## Step 3 — The feature gate (check before designing anything)

Substack's native email sequences began rolling out in late 2025 to Bestseller-tier publications as a beta; as of mid-2026 they are **not yet universal**. Ask the operator to check: publication dashboard → **Settings → Emails** — does a **"Drip campaigns"** (or similarly named) section appear? Exact labels are approximate: the feature has no public official doc yet, and what's known comes from practitioners who have it.

- **They have it** → build campaigns (Step 5) plus the classic welcome email (Step 4 — it still fires first and is still worth getting right).
- **They don't** → say so honestly: no native automation exists without it, and no off-platform workaround belongs in this system. The fallback that's genuinely available — and is most of the value anyway — is Step 4: a strong welcome email (every publication has it), separate free and paid welcome treatments, and a pinned welcome post as the on-site twin. Offer to draft the campaigns anyway, clearly marked `status: awaiting-feature`, so they're ready to paste the day the rollout reaches them.

## Step 4 — The classic welcome email (everyone gets this)

Always build this, feature or not. Craft rules in the playbook; the structure that converts:

1. Personal greeting in the operator's voice — it's a private email, warmer than the About page
2. What to expect: what ships, when
3. **The upgrade ask, above the fold:** what paid includes (from `offer.md`) and the one-line difference between free and paid
4. Route to 2–4 best posts — scan `workspace/content/pieces/` for `status: published` and propose candidates; the operator confirms which represent them best
5. **A reply question** — one genuine question; replies build the relationship and train deliverability
6. One CTA total. 150–300 words. Plain subject around eight words.

**Free vs paid split (researched practitioner pattern):** if the operator has paid on, write two versions — free welcome (best posts + why readers upgrade, with any *real* subscriber testimonial) and paid welcome (thank-you + benefits recap + how to get the most out of it). Save as `sequences/welcome-email.md` with both versions and a placement note (Settings → Basics → welcome email; paid welcome under payments settings).

## Step 5 — Build the campaigns (feature holders, or `awaiting-feature` drafts)

Five lifecycle campaign types exist natively — triggers, limits, and full frameworks in the playbook. Build what the operator's situation calls for, in leverage order:

1. **Free-to-paid conversion** — the highest-leverage automation. Researched arc: lead with the best free value → deliver something genuinely useful → stack the paid benefits (from `offer.md`, transformations not features) → real proof if any exists → a closing invitation (a discount only if the operator chooses to run one — never invent urgency or a fake deadline).
2. **Paid onboarding** — reinforce the decision, deliver immediate value, show how to use everything they bought, ask one feedback question.
3. **Founding onboarding** — short (~3 emails): deliver every founding perk immediately, recap what their support enables, genuine VIP recognition.
4. **Winback** (cancelled-paid, still free) — ask why honestly → remind what they're losing concretely → answer the time/cost objection → final invitation. Coordinate with Substack Boost, which already auto-offers a save discount at cancellation — don't duplicate the same offer twice.
5. **Upgrade onboarding** — context-aware thanks for moving up a plan; shortest of the five.

**Design within the feature's verified limits, not around imagined ones:** delays are set in hours between emails; there is no conditional logic, no segmentation, no behavioral triggers beyond the lifecycle event, no analytics, and paywalled content can't be embedded in sequence emails. So: every email must stand alone (a reader who ignored email 2 must not be lost in email 3), nothing can assume "if they clicked," and results tracking is manual — note in each file what the operator should watch in their subscriber dashboard.

Each campaign saves as `sequences/<campaign>.md`: frontmatter (`status: draft` or `awaiting-feature`, `updated:`), then a setup block (trigger, email count, delay in hours between each — with the reasoning), then each email as subject + body, paste-ready. Present it however relays the information best — tables, charts, visuals, plain prose: whatever you judge serves the reader.

## Step 6 — Hand off

Share the results and make the next step clear. The operator pastes and activates everything (Settings → Emails → the campaign; emails are composed in-platform and don't publish as posts) — this skill never sends, schedules, or touches their Substack. Flag honestly: the feature is beta, delivery visibility is weak, and any conversion numbers they hear quoted for welcome flows are self-reported practitioner claims, not platform guarantees.

If `offer.md` or `about-page.md` changed since the sequences were written, offer to reconcile — lifecycle emails that contradict the subscribe page cost trust at the exact moment of decision.

## Guardrails

- **Feature honesty first.** Never imply the operator has automation they don't; never suggest off-platform email tools as a workaround inside this system.
- **No invented anything**: no fake testimonials or social proof, no fabricated discounts or deadlines, no promised perks that aren't in the decided offer.
- **Benefits come from `offer.md` / `business.md`** — never freelanced into an email because it sounded persuasive.
- **One CTA per email.** The reader does one thing or nothing.
- **Stand-alone emails only** — the feature has no conditional logic; never write an email that depends on the reader having acted on a previous one.
- **Never send, schedule, or configure anything.** Paste-ready drafts in `workspace/substack/sequences/`; the operator does the rest.
