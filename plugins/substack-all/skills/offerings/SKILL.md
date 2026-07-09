---
name: offerings
description: Use when the operator needs to design or rework what their Substack tiers contain — "what should my paid tier include", "help me design my offer", "what do founding members get", "should this be free or paid" — or wants the subscribe page and tier benefit copy written once the structure is decided. Also use when pricing or tier questions surface mid-session and deserve a real working pass.
argument-hint: "[design|copy] [optional: what prompted this]"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, WebFetch
---

# Offerings — design the offer, then write it

You help the operator *figure out* their free/paid/founding structure first, and only then write the display copy. Most weak Substack offers aren't badly written — they're undesigned: a paid tier that's just "more posts," a founding tier that's the paid tier with a bigger number. The design data is clear about what top-earning publications actually do; this skill applies it to *this* operator's business and capacity.

**Shared home (this plugin's owned folder): `workspace/substack/`.** This skill maintains one living file: `workspace/substack/offer.md` — the decided structure plus the paste-ready copy, with `status:` and `updated:` frontmatter. Revisions edit this file.

The design data — perk-type prevalence from top earners, the four free/paid mixes, why readers actually pay, founding-tier norms — lives in [references/offer-design-playbook.md](references/offer-design-playbook.md). Read it before the design conversation.

## Step 1 — Read the context profiles

Read all four. Two are load-bearing:

- `context/business.md` — **read it hard.** The offer is an extension of the business model: what they sell, current pricing, products, capacity. The paid tier must fit what the operation can actually sustain, and must not cannibalize or contradict an existing product.
- `context/ICP.md` — what this reader would pay for: their frustrations (what a paid tier should solve), aspirations (what a transformation promise looks like in their words), objections (what the copy must answer), and whether they can expense it.
- `context/user.md` — the operator's real capacity and strengths (a community tier from someone who hates community management is a churn machine).
- `context/tools.md` — publication details, other platforms the offer must coexist with.

**If a profile is missing or empty:** say which one and continue. An empty `business.md` means the structure conversation starts from interview instead of file — ask, don't assume, and recommend filling the profile with what this session decides. Never invent prices, products, or capacity.

## Step 2 — Voice

The copy half of this skill is content. Check for the operator's voice-profile skill and invoke it before drafting tier copy or subscribe-page language. If none exists: say so, offer two paths — build one (the Voice plugin) or proceed by inferring voice from the context profiles — and never draft in a generic default voice. (The *design* half — the structure conversation — doesn't need the voice profile; don't block on it there.)

## Step 3 — Establish the starting point

`mkdir -p workspace/substack`. Read `workspace/substack/offer.md` if it exists (this is a revision — keep what holds). If the operator has live tiers, get the current state: what each tier costs and claims today (they can paste it, or give the subscribe page URL for WebFetch). Check `workspace/substack/about-page.md` and `workspace/substack/sequences/` if present — the offer must end up agreeing with both.

## Step 4 — Design the structure (the conversation, not a lecture)

Work through these decisions *with* the operator, using the playbook's data. Short questions, real trade-offs, one decision at a time:

1. **Pick the free/paid mix.** Four researched models: all-free (patronage), loosely defined paid (experiment), clearly defined paid (the growth default), all-paid (works mainly where readers expense it). Recommend one against `business.md` and the ICP — with the honest datum that publications paywalling at least some content earn several times more than fully-free ones (per Substack's own published data).
2. **Decide what free does.** Free is the growth engine and the trust builder — it must be good enough to prove the paid promise (the Notes→free pipeline depends on it). Name what stays free and why.
3. **Stack the paid tier.** Content alone is table stakes — nearly every top earner ships it, and the winners stack 2–3 perk *types* on top (community, access, assets, events — prevalence data in the playbook). The 2026 shift: paid reads as *membership*, not "extra articles." Pick perks the operator can sustain **forever, on a bad week** — run the sustainability test on each: "will you still happily deliver this in month 9?"
4. **Design founding as superfan capital, not a bigger paid.** 2–3 exclusive perks plus genuine recognition; typical range $150–250+/yr among researched publications (range, not a rule). If the operator can't name what founding members get beyond generosity, an "intrinsic support" framing is honest and common — say so plainly rather than inventing thin perks.
5. **Sanity-check pricing** against `business.md` (existing products, what the ICP pays for comparable things). This skill gives reasoning and researched ranges, never a fake-precise "optimal price."
6. **Check the seams.** Does the paid tier collide with any existing product? Does every promise survive the operator's real calendar? Anything that fails gets cut now, not after subscribers paid for it.

Close the design phase by reading the decided structure back and getting an explicit yes before writing copy.

## Step 5 — Write the display copy

With the structure decided, write the paste-ready surfaces (formats and craft rules in the playbook):

- **Per-tier benefit lists** (for Settings → payments, where tier descriptions live): each benefit written as a **transformation, not a feature** — what the reader gets *out of it*, not what the operator ships. Bundle-frame the stack. Free tier gets a real benefits list too (it sells the upgrade by proving the quality).
- **The "why pay" block** for the subscribe page and welcome surfaces — built on the reader-motive themes in the playbook, in the ICP's language.
- **Subscribe-page presentation notes**: tiers render side-by-side from the dashboard settings; Substack's customizable subscribe homepage block (shipped spring 2026) takes tier-specific messaging — provide the short message per tier. Social proof on this surface only if real.
- Every claim in the copy traces to a decided, sustainable perk. No decorative benefits.

## Step 6 — Save, hand off, close the loop

1. Write `workspace/substack/offer.md`: frontmatter (`status: draft`, `updated:` today), **Part 1 — the structure** (each tier: price, what's in it, why, the sustainability notes), **Part 2 — the copy** (paste-ready blocks, each with a placement instruction for the Substack dashboard). Present it however relays the information best — tables, charts, visuals, plain prose: whatever you judge serves the reader.
2. The operator pastes tiers and copy into Substack — this skill never touches their account or their Stripe.
3. **Offer the `business.md` update**: the decided tier structure is now a fact of the business — propose the exact lines to add to `context/business.md` and apply only on their yes. Future sessions should know the offer without re-deriving it.
4. If surfaces already exist, flag any now-stale spots: About page paid-benefits section, welcome sequence upgrade emails. Offer to reconcile.

## Guardrails

- **Design before copy — never skip to writing.** Tier copy for an undesigned offer is lipstick on a churn problem.
- **Nothing unsustainable ships.** Every perk passes the bad-week test; cut at design time, not after people paid.
- **No invented numbers**: no fake subscriber counts, no fabricated earnings claims in the copy, no fake-precise pricing science. Researched ranges with attribution; decisions belong to the operator.
- **Transformations, not features — but real ones.** The transformation promised must follow from the perk; aspirational copy that the deliverable can't cash is a refund waiting to happen.
- **The offer agrees with the system**: `business.md`, `about-page.md`, and `sequences/` must tell the same story; reconcile conflicts rather than shipping them.
- **Never auto-publish, never touch payments.** Drafts in the workspace; the operator configures Substack themselves.
