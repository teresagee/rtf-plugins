# Algorithm realities, cadence, and the reach diagnostic (state of play, mid-2026)

Provenance, stated once: the only official source is Substack's public engineering Q&A on the feed (late 2025, with the Notes algorithm's lead engineer on record). Everything else is practitioner inference — consistent across several independent operators who publish tracked subscriber-source data, but self-reported and not audited. Treat the official items as ground truth and the rest as strong working assumptions; when one fails for this operator, the tracker outranks this file.

## How distribution works

**Official (from Substack's own Q&A, late 2025):**
- The feed builds a numerical representation of each reader (subscriptions, follows, interests, location, language) and matches notes against it.
- The optimization target is explicit: help readers **discover, subscribe, and ideally pay** — not engagement time. This is the structural difference from X/LinkedIn: the feed is a subscription-prediction engine, so writing for conversion *is* writing for the algorithm.
- **Audience overlap** is the core mechanic: notes are shown to non-followers whose profile overlaps your existing audience. On-platform actions (restack, reply, share) are high-value signals because Substack can observe the full behavior loop.
- Muting is the explicit negative signal.

**Practitioner-verified (late 2025–2026, multiple independent sources):**
- A late-2025 change shifted distribution from follower-first to overlap-first, and **restacks became the strongest single signal** — with/without-restack test periods showed more profile views and more stranger-subscribers in restack weeks. One restack from a larger same-audience account can outperform weeks of solo posting.
- **Comments outweigh likes** in ranking: a note with 10 comments / 20 likes out-distributes one with 5 comments / 50 likes.
- **The first 30–60 minutes of engagement velocity** decides initial distribution — which is why replying to every early comment matters operationally, not just socially.
- Each account carries a **trust profile** built from consistency, engagement quality, restack behavior, and conversion over time. It compounds slowly: months 1–3 minimal reach, months 4–6 an uptick, months 7–12 compounding (one practitioner's same-note test: 12 likes in month 2, 2,100 in month 10). Most people quit at day 30–60 — right before the curve turns.
- Notes are **semi-evergreen**: months-old notes keep converting via restacks, unlike X posts.

**The headline conversion datum:** a 2026 scrape of 243,483 notes, analyzing the top ~8% by engagement, found **40% of the most-liked notes gained zero subscribers**. Likability and conversion are different axes. Track subscribers per note; record likes; decide on subscribers.

**Why Notes is the priority at all:** practitioners with subscriber-source dashboards consistently report 60–90% of new free subscribers arriving via Notes, and one tracked funnel found ~96% of new subscribers decided on Notes/profile surfaces *before ever reading a full post* (single source, self-reported — but directionally why the About page and profile matter so much). Caveat from the monetization side: Notes-sourced subscribers skew free; they convert to paid slower than guest-post or search subscribers. Notes fills the top; the surfaces and sequences convert.

## Cadence

- **The ramp (tracked):** months 1–2 → 1–3 notes/day; months 3–6 → 3–5/day; beyond → 5–7/day if quality holds. Space notes through the day; clumped batches throttle.
- **Credible dissent, worth honoring:** one experienced operator argues ~1/day staggered from a weekly batch session, and that below a few hundred subscribers your time is better spent *commenting on others' notes* than posting originals. For brand-new accounts, present both and let the operator pick a sustainable number — a held cadence of 1/day beats an abandoned cadence of 5/day every time.
- **Timing windows (one practitioner's tracked data — light evidence, hold loosely):** 6–9am for reach, 11am–1pm for engagement, 7–9pm for comments and conversions; weekend evenings decent. Counterpoint from another tracked account: timing matters far less than people think. Don't let scheduling debates displace writing.
- **Reposting winners:** a variation of a proven note with a modified hook, 7–10 days later, works. Clusters of self-reposts in a short window read as spam.

## The engagement work (half the system, no shortcuts)

- **Reply to every comment**, ideally within the first hour — velocity feeds distribution and repliers become subscribers.
- **Daily restack routine (~10 minutes):** morning, restack yesterday's post announcement or note; evening, restack 1–2 same-audience writers *with a comment line*. One practitioner attributes a ~30% view lift and a 900-subscriber month to making this a standing routine.
- **Engage mid-tier creators in the niche, not whales.** Overlap distribution means their audience seeing your name is the growth loop; mid-tier accounts actually engage back. Budget ~30 minutes/day of genuine comments on 10+ others' notes if growth is the goal.
- This skill never performs any of this — no posting, restacking, or commenting on the operator's behalf. It builds the routine into the weekly plan as the operator's checklist.

## Reach killers

- **External-link bursts** — documented account-trust dips (one tracked case: ~60% reach drop, recovered by a 7-day link fast plus daily original conversational notes). Default: no links in notes.
- **Promotional drift** — more than 2 promotional notes in the last 10. Conversational notes outperform promotional 3–5x on early velocity.
- **Gaps of 7+ days**, then panic-posting double volume — reads as instability; both directions hurt.
- "Follow me for more" endings, headline+link reposts, AI quote-card motivation, walls of text, generic drive-by comments on others' notes.
- **Chasing profundity:** deep-sounding takes earn likes from strangers and subscribers from no one (the 40% finding, again).

## The 5-point reach diagnostic (run in order; prescribe only the matching fix)

1. **Platform-wide throttle?** Impressions down but restack:impression ratio normal → it's not you. Wait 72 hours, change nothing.
2. **Promotional drift?** Count promo notes in the last 10. If >2 → post 5 conversational, zero-link notes; reassess in 48 hours.
3. **Trust dip?** Recent link bursts, a posting gap, or repost clusters → 7-day link fast + daily original conversational notes.
4. **Posting-window obsolescence?** Audit recent performance by hour posted; shift the window 2–3 hours; test one week.
5. **Recommendations gap?** Existing-subscriber engagement normal but new growth stalled → the operator likely under-recommends; recommending 10+ aligned publications feeds the reciprocity/overlap machinery.

Never prescribe "post more" as a dip response.

## Follower → subscriber (the conversion seam)

Followers see you in-feed only; subscribers get the inbox. Levers that move the seam, per tracked accounts:
- **Trailer framing:** notes tease, the newsletter delivers — name the specific problem a subscriber-only piece solves, without linking it.
- **Sparing, explicit invitations:** an end-of-note invitation works when rare (the 20% of the 80/20), and reads as spam when routine.
- **The profile is the landing page:** byline, pinned note, and About page do the closing (the about-page skill's territory).
- **Direct engagement:** repliers and regular commenters convert; treat every comment thread as warm.

## Tooling currency (mid-2026)

- **Native Note scheduling** shipped spring 2026: schedule one note at a time, up to ~3 months out; drafts editable until publish. No bulk import or reordering. Batches from this skill are written for manual scheduling through it.
- Third-party schedulers/analytics exist (including tools exposing per-note conversion data Substack doesn't surface natively). This system is Claude-native — no external tools wired in; if the operator uses one, its conversion numbers are excellent tracker input, reported by the operator.
- **Dated advice to ignore:** pre-late-2025 follower-feed tactics, "post quality and wait" without a restack strategy, growth-via-X cross-posting (X suppresses Substack links), and likes-as-KPI anything.
