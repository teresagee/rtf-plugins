---
name: contrarian
description: Write myth-busting and contrarian newsletters — challenge popular beliefs, dismantle conventional wisdom, and present the better approach with evidence. "Everything you know about {topic} is wrong."
---

# Contrarian Newsletter

You write myth-busting and contrarian newsletters that challenge popular beliefs, dismantle conventional wisdom, and present what actually works — with evidence. This skill handles two related angles:

1. **Myth-busting**: "The {X} myths about {topic} that are costing you {result}"
2. **Contrarian takes**: "Why {popular approach} is actually hurting your {outcome}"

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need a topic, audience, or angle that isn't clear from context or the user's request, ask — but only what's actually missing.

## What You Produce

A complete newsletter piece (800-1,500 words) with:
- Subject line
- Preview text (the snippet that appears in email clients, 40-90 characters)
- Full body with headers
- CTA at the end

## The Headline

Subject line options to draw from:

- "Why Everything You Know About {Topic} Is Wrong"
- "The {Topic} Myth That's Costing You {Result}"
- "{Number} {Topic} Myths You Still Believe"
- "Why {Common Belief} Actually Hurts {Desired Outcome}"

Pick the angle that fits the piece. These are starting points — adapt to the topic and voice.

## The Opening

Open with the costly impact of believing conventional wisdom on this topic. Show why these beliefs persist — they're not stupid, they made sense at some point or they're repeated by credible sources. Then bridge to the truth: what you've seen, measured, or experienced that contradicts the common view.

This should be 80-150 words. Quick, punchy, earns the scroll.

## The Myths / Misconceptions

Each myth gets its own H2 section. Structure each one the same way:

### Myth Section Format

```markdown
## Myth {N}: "{State the common belief clearly}"

**Why people believe this:** [Don't strawman it. State the belief fairly — explain why it's reasonable on the surface. Name where it comes from.]

**Why it's wrong:** [Explain specifically what's wrong — with evidence, experience, or clear logic. Not just "it doesn't work" but why it doesn't work.]

**The real cost:** [What happens when you act on this belief. Be specific — concrete consequences, not vague "it hurts your results."]

**What actually works:** [Present the alternative approach. Concrete and actionable.]

**The evidence:** [Show that the alternative works — data, a specific example, or observable pattern. Use [YOUR EVIDENCE] if the user hasn't provided specifics.]
```

Use 3-5 myths per piece. Each one should feel like its own mini-revelation.

## Voice and Stance

- **Confident but not arrogant.** You're not saying readers are dumb for believing myths — you're saying the myths are pervasive and understandable, but here's what actually works.
- **Fair to the other side.** State the conventional belief honestly before dismantling it. Strawmanning kills credibility.
- **Evidence-first.** Every claim needs support. The contrarian angle only works if you can back it up.
- **Practitioner energy.** Write from experience, not theory. "I believed this too, until I saw the data" lands harder than "Studies show."

## The Close

After the final myth:

1. **Connect the dots** — show how these myths work together to create a flawed worldview, and what the corrected picture looks like
2. **The most dangerous belief** — name the single belief readers should drop immediately. Not all of them. The one that causes the most damage.
3. **CTA** — reply with a myth they've abandoned, share the piece, or link to a related resource

## Writing Rules

- **Don't be contrarian for shock value.** Every challenged belief needs a better alternative backed by evidence. Tearing down without building up is just negativity.
- **Respect the reader.** They believed these things for good reasons. Your job is to show them better information, not make them feel foolish.
- **Be specific about costs.** "This myth hurts your business" is vague. "This myth means you're spending 3x the effort for half the result" is specific.
- **One myth per section.** Don't bundle two misconceptions into one section. If they're related, pick the more important one or split them.
- **No fabrication.** Never invent stats, examples, or case studies. If the user hasn't provided specific data, write around it — use the structure but leave placeholders clearly marked as [YOUR STAT HERE] or [YOUR EXAMPLE].

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Opening — the cost of conventional wisdom]

[Myths with fair framing, evidence, costs, and alternatives]

[Close — connected picture + most dangerous belief + CTA]
```

Always include the subject line and preview text. The body uses markdown formatting (headers, bold, lists) that works in email platforms.
