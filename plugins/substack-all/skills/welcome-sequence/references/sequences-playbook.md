# Email sequences playbook — verified feature state + the frameworks (compiled 2026-06)

Provenance, stated once: Substack has published **no official documentation** of the drip-campaign feature that could be retrieved as of this compilation (the support page was unreachable); everything below about mechanics comes from multiple independent practitioners who have the feature and documented it hands-on, cross-confirmed. Treat exact UI labels as approximate and re-verify limits when the feature exits beta. Welcome-email guidance is from Substack's own published advice plus practitioner consensus. Conversion figures are self-reported practitioner claims — flagged where they appear, never to be promised to the operator.

## Verified feature state (as of mid-2026)

- **It's real**, confirmed by multiple independent hands-on walkthroughs: native, lifecycle-triggered email sequences ("drip campaigns") inside Substack.
- **Rollout:** began quietly ~October 2025 to **Bestseller-tier publications, as a beta**. Substack signaled availability for all creators "in 2026," but it is **not universal as of June 2026**. The gate check: if no drip/sequence section appears under the publication's email settings, that account doesn't have it yet. There is nothing to configure around this — the feature is there or it isn't.
- **Where it lives:** publication dashboard email settings. Emails are composed in-platform like normal emails but **do not publish as posts**.

### The five native campaign types (lifecycle-triggered)

| Campaign | Trigger |
|---|---|
| Free-to-paid conversion | runs to free subscribers (until they convert) |
| Paid onboarding | new paid subscriber |
| Upgrade onboarding | moved from monthly/regular paid to a higher plan |
| Founding member onboarding | new founding-tier subscriber |
| Winback | cancelled paid, still on the free list |

### Verified mechanics and limits (beta — design to these)

- Delays between emails are set **in hours**, per step
- **No analytics or stats** on sequence emails — results tracking is manual (watch paid conversions and cancellations in the subscriber dashboard)
- **No conditional logic, no tagging, no segmentation** — one linear sequence per lifecycle event, same for everyone it fires for
- **No behavioral triggers** beyond the lifecycle events above (nothing fires on clicks, opens, or reads)
- **No paywalled content embedded** inside sequence emails
- Weak delivery visibility (practitioner-reported)

**Design consequences:** every email must stand alone; never reference "as you saw in my last email" as a dependency; never branch ("if you grabbed the template…"); keep sequences short enough that a linear, identical-for-everyone flow stays welcome rather than noisy.

## The classic welcome email (always available; configured under basic settings, separate from drips)

Substack's own guidance plus practitioner consensus, converged:

- **Personal greeting in the publication's voice** — it's a private email; it can be warmer than any public surface
- **Upgrade button above the fold**, with the free-vs-paid difference spelled out in a line (official guidance)
- **Route to 2–4 best posts** — the proof of quality, chosen deliberately
- **Ask a reply question** — observed reply rates around 2–3% (practitioner-reported); replies build relationship and train inbox placement; asking readers to move the email to their primary inbox is standard deliverability practice
- **150–300 words, plain subject around eight words, exactly one CTA** (community consensus numbers)
- An instant useful asset (a checklist, a template) lifts it where one genuinely exists — never promise one that doesn't
- **Split free and paid welcomes** (documented practitioner pattern): free = best posts + why readers upgrade (+ a *real* paid-subscriber testimonial if one exists); paid = thank-you + benefits recap + how to use everything
- **The pinned welcome post** is the on-site twin of the welcome email — same promise, public surface
- Circulating claim that top welcome emails convert 15–30% of free subscribers in week one vs ~2–3% typical: **self-reported, unverified, formula paywalled** — do not promise anything like this to the operator

## Sequence frameworks (practitioner-built for the native feature; adapt, never copy wording)

**Free-to-paid conversion** — consensus highest-leverage automation:
1. Welcome + the single best free piece (prove quality first)
2. Deliver a genuinely useful standalone asset or insight (generosity before the ask)
3. Stack the paid benefits — from the decided offer, as transformations
4. Proof: a real case, result, or testimonial — only if one exists; skip the email otherwise
5. The invitation — a clear ask; a launch-style discount **only if the operator actually runs one** (fabricated urgency is both dishonest and, on a lifecycle trigger, instantly stale)

Spacing: practitioner setups run delays of roughly 1–3 days (24–72 hours) between steps — set in hours; tune to the operator's cadence so sequence emails don't pile onto publish days.

**Paid onboarding** (~3–4 emails): reinforce the decision (what they unlocked, immediately usable) → the best of the archive for *them* → how to use every benefit (chat, comments, archive) → one feedback question.

**Upgrade onboarding** (short): context-aware thank-you — they were already paying; acknowledge that, deliver what the higher plan adds, nothing generic.

**Founding onboarding** (~3 emails): deliver every founding perk immediately → what their support concretely enables → genuine recognition. Founding members bought belief; the sequence's job is to honor it fast.

**Winback** (3–6 emails; practitioner-claimed recovery rates of 10–20% — self-reported):
1. Honest "why did you go?" — a real question, not a guilt trip
2. What they're losing, concretely (the specific paid material since they left)
3. Answer the actual objection (usually time or cost) plainly
4. Final invitation — discount if the operator chooses
**Boost interplay:** Substack Boost (on by default with payments) already auto-offers a save discount at the cancellation moment. The winback sequence runs *after* that moment — don't repeat the same discount Boost just showed; differentiate or skip the discount step.

## Craft rules across every lifecycle email

- One idea, one CTA, operator's voice throughout
- Subject lines: plain, specific, no clickbait mechanics — these readers already subscribed
- Benefits language comes from the decided offer file; emails never freelance new promises
- Every factual claim in an email (numbers, results, testimonials) is real and operator-confirmed — the anti-fabrication rule applies hardest on the surfaces where trust converts to money
- The sequence must agree with the About page and subscribe page; contradiction at the decision moment is the most expensive copy bug on the platform
