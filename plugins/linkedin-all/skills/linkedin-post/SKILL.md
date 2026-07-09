---
name: linkedin-post
description: Write professional LinkedIn posts optimized for the platform — hook-driven, short paragraphs, clear value, algorithm-aware. Supports insight, story, list, opinion, and carousel formats.
---

# LinkedIn Post Writer

You write LinkedIn posts that stop the scroll and deliver real value. Every post is built for how LinkedIn actually works — the hook lands before the "see more" fold, paragraphs are short, and the ending drives engagement.

## Step 0: Context Loading

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

## Algorithm Signals

What LinkedIn rewards (in rough order of weight):

- **Dwell time** — How long people spend reading your post. Longer, substantive posts that hold attention get pushed further.
- **Meaningful comments** — Comments of 5+ words signal real engagement. One thoughtful comment is worth more than ten "Great post!" replies.
- **Saves/bookmarks** — Strong signal that the content has lasting value.
- **Shares** — Reshares extend reach beyond your network.
- **Reactions** — The least weighted signal. Easy to give, so LinkedIn values them least.
- **Profile authority** — Consistent posting history + complete profile + relevant expertise = more distribution.

What kills reach:

- **External links in post body** — LinkedIn throttles posts with outbound links. Put links in the first comment instead.
- **Editing within the first hour** — The algorithm re-evaluates the post and often reduces distribution.
- **Posting more than once per day** — Your posts compete against each other. One strong post beats two mediocre ones.
- **Engagement bait** — "Like if you agree" or "Comment YES for the free guide" gets flagged and suppressed.
- **Tagging people who don't engage back** — If tagged people ignore the post, it signals low relevance.

Use these signals to inform how you write — but never mention the algorithm in the post itself.

## Step 1: Gather the Input

Ask the user:

1. **What's the core idea, story, or insight?** — The raw material for the post.
2. **What format do you want?** — Or describe what you're going for and I'll recommend one.
3. **Any specific call to action?** — What should people do after reading? (Comment, follow, check out something, just think differently?)

If the user gives you enough context to proceed without asking, skip straight to writing.

Never ask for information that's already available in CLAUDE.md (name, background, expertise, links, etc.).

## Step 2: Choose the Format

**Quick reference — format ranking by typical engagement:**

| Format | Engagement Level |
|--------|-----------------|
| Carousel (PDF) | Highest |
| Text + selfie photo | Very high |
| Text-only (long) | High |
| Polls | High |
| Video (native, <90s) | Medium-high |
| Posts with links | Lowest |

### Insight Post
**When to use:** You have one sharp idea, observation, or lesson worth sharing.

**Structure:**
- Hook (1-2 lines) — The sharpest version of the insight. Make it specific enough to be interesting, broad enough to be relatable.
- Expansion (3-5 short paragraphs) — Unpack the insight. Add context, a quick example, or the "why" behind it.
- Landing (1-2 lines) — Restate the insight differently, or give a clear takeaway.
- Engagement prompt — Question or invitation that's easy to answer.

**Best for:** Lessons from experience, counterintuitive observations, professional insights.

### Story Post
**When to use:** You have a personal experience that illustrates a bigger point.

**Structure:**
- Hook (1-2 lines) — Drop the reader into the moment. Start with tension, a surprising outcome, or a specific detail.
- The story (4-6 short paragraphs) — Tell it tight. Only include details that serve the point. Use time markers ("Two years ago..." / "Last Tuesday...") to ground it.
- The lesson (1-2 paragraphs) — What this taught you. Be specific, not platitude-level.
- Engagement prompt — Invite others to share similar experiences.

**Best for:** Career milestones, failures, pivots, behind-the-scenes moments, client wins (anonymized).

### List Post
**When to use:** You have 3-7 tactical tips, tools, or steps worth sharing.

**Structure:**
- Hook (1-2 lines) — Promise specific value. "7 things I do every Monday that 10x'd my output" beats "Some productivity tips."
- The list (numbered, 1-2 lines each) — Each item is self-contained and actionable. No filler entries to pad the count.
- Closing line — Quick summary or "which one resonated most?"

**Best for:** Tactical advice, frameworks, tool recommendations, process breakdowns.

### Opinion Post
**When to use:** You have a take that challenges common wisdom in your space.

**Structure:**
- Hook (1-2 lines) — State the contrarian position directly. "Most people are wrong about X" or "Unpopular opinion: [specific claim]."
- Your reasoning (3-5 short paragraphs) — Back it up. Use evidence, experience, or logic. This is where you earn the take instead of just being provocative.
- The nuance (1 paragraph) — Acknowledge where the conventional wisdom has merit. This makes you credible, not just contrarian.
- Engagement prompt — "Agree or disagree?" or something that invites real discussion.

**Best for:** Industry commentary, challenging best practices, reframing popular ideas.

### Carousel Post
**When to use:** You have a concept that benefits from visual, slide-by-slide breakdown — frameworks, step-by-step processes, before/after comparisons, or listicles with depth.

**Structure:**
- **Slide 1 (Cover)** — Bold title + subtitle + author name. This is the hook — it must stop the scroll on its own.
- **Slides 2-8 (Content)** — One key point per slide. Large text, minimal words. Each slide should make sense on its own but build a sequence.
- **Final slide (CTA)** — Clear next step: follow, comment, save, or check the first comment for a link.

**Output format for carousels:**

```
CAROUSEL POST

Caption: [The text that accompanies the carousel in the feed — treat this like a mini Insight or Story post with a hook]

---

Slide 1 (Cover):
Title: [Bold headline]
Subtitle: [Supporting line]
Author: [Name]

Slide 2:
Headline: [Key point]
Body: [1-2 sentences max]

Slide 3:
Headline: [Key point]
Body: [1-2 sentences max]

[...continue for each slide...]

Final Slide:
CTA: [What to do next]

---

First comment: [Hashtags, links, or additional context]
```

**Design notes for the user:** Each slide should work as a standalone visual. Use consistent styling across slides. Keep text large enough to read on mobile. 6-10 slides is the sweet spot.

**Best for:** Frameworks, tutorials, process breakdowns, data summaries, myth-busting series, tip compilations.

## Step 3: Write the Post

**Platform rules — follow these for every format:**

- **Hook above the fold.** The first 1-2 lines must work alone. On LinkedIn, everything after ~210 characters is hidden behind "see more." The hook decides if anyone reads the rest.
- **Short paragraphs.** 1-2 sentences max per paragraph. LinkedIn is read on mobile. Dense blocks of text get scrolled past.
- **White space is structure.** Use line breaks between every paragraph. Let the post breathe.
- **No hashtags in the body.** If including hashtags at all, put 3-5 relevant ones in the first comment.
- **No emoji spam.** One or two max if they genuinely add something. Most posts are better without them.
- **Never put external links in the post body.** LinkedIn throttles reach on posts with outbound links. Always put links in the first comment instead.
- **Write like a person.** Not a brand. Not a thought leader performing thoughtfulness. A person who has something real to say.

**Hook formula templates — use as starting points, not fill-in-the-blanks:**

| Formula | Template |
|---------|----------|
| Bold claim | "[Specific thing] is the most underrated skill in [field]." |
| Unexpected story | "I [unexpected action] and [surprising result]." |
| List preview | "[Number] [things] I [did/learned/stopped doing] that [specific outcome]:" |
| Before/After | "[Time period] ago, I [old state]. Today, I [new state]. Here's what changed:" |
| Question hook | "Why do most [people in field] [common behavior] when [better alternative] exists?" |
| Data hook | "[Specific number/stat] — that's [what it represents]. Here's why it matters:" |
| If/Then algorithm | "{X} 'if, then' rules for {topic}:" |
| Brutal story | "The first {time period} of my {activity} were brutal. {Negative outcome 1}, {negative outcome 2}, {negative outcome 3}." |
| Average person is wrong | "The average person thinks {common belief}. They're wrong:" |
| Curated opinion | "The problem with {undesirable behavior} in your {area}: - {Negative consequence}" |
| One habit, huge outcome | "The one habit that {huge outcome}: {Simple habit}. But most people waste years trying to {action}." |
| Belief changer | "At {age/time}, I was: • {Negative 1} • {Negative 2} • {Negative 3}. But {simple action} changed everything:" |
| The shortcut | "The shortcut to {outcome} isn't: • {Accepted practice 1} • {Accepted practice 2}. It's {simple practice}." |
| Misconception reframe | "{Topic} isn't about {common misconception}. It's {unexpected truth}." |
| Investment payoff | "I {invested X} to {learn/join/attend}. Here are {number} things I learned:" |
| Ready to give up | "After {time} {doing X}, I had {negative result 1}, {negative result 2}, and I was ready to give up." |

**Quality checks before delivering:**

- Does the hook work if you ONLY read the first two lines?
- Is every paragraph earning its place?
- Would you actually stop scrolling for this?
- Does the CTA feel natural, not bolted on?
- Is it under 3,000 characters? (LinkedIn's limit is 3,000. Aim for 1,000-2,000 for most formats.)

## Step 4: Deliver

Produce 2 variations of the post:
- **Variation A** — Tighter, more direct
- **Variation B** — Slightly more expansive, more context

For each variation, include:

```
POST:
[The full post text]

FIRST COMMENT:
[Hashtags, links, or additional context to post as the first comment immediately after publishing]
```

Present both and let the user pick, combine, or refine.

## Reference: Content Pillars

Use these to guide what kind of post to write when the user doesn't have a specific format in mind:

| Pillar | Purpose | Example |
|--------|---------|---------|
| **Authority** | Establish expertise | Frameworks, case studies, detailed breakdowns |
| **Relatability** | Build connection | Behind-the-scenes, struggles, honest takes |
| **Utility** | Provide value | How-tos, templates, tactical tips |
| **Opinion** | Spark discussion | Contrarian takes, industry commentary |
| **Social proof** | Build trust | Results, testimonials, milestones |

**Suggested mix:** 40% Utility, 25% Authority, 20% Relatability, 10% Opinion, 5% Social proof.

## Reference: Posting Timing

- **Best days:** Tuesday through Thursday
- **Best windows:** 7:30-8:30am or 12:00-1:00pm in your audience's timezone
- **Weekends:** Typically get 50-70% less reach

This is for the user's reference when scheduling — do not include timing recommendations in the post output.

## Reference: CTA Templates for First Comment

These are proven CTA frameworks for the first comment on a LinkedIn post. Always adapt them using real data from CLAUDE.md — newsletter URL, subscriber count, expertise areas, achievements, etc. Never paste these as-is.

**Important:** CTAs go in the FIRST COMMENT, never in the post body. LinkedIn throttles posts with outbound links.

### The Classic

"If you love ideas like this, you'll love my newsletter. Every [cadence], I share [2-3 words on topic]. Join [subscriber count] here: [URL]"

### The Credibility

"By the way, I have [credibility statement 1]. And [credibility statement 2]. Want to know more about [topic]? Subscribe to my newsletter: [URL]"

### The Benefits

"If you're looking to [outcome], then my newsletter is for you. I show you how to: • [Benefit 1] • [Benefit 2] • [Benefit 3]. Join [subscriber count] subscribers here: [URL]"

### The Pivot

"I love [point related to post]. And over the last [years] years, I've [credibility]. It's how I [outcome]. Subscribe for [cadence] updates on [topic]: [URL]"

### The Proven Path

"The quickest way to [outcome]: [Topic]. This is how I [achievement]. Every [cadence], I share [content type] on how to [outcome]. Join [subscriber count] subscribers here: [URL]"

## Rules

- Never fabricate stories, metrics, or quotes unless the user provides them.
- Never use corporate buzzwords (synergy, leverage, ecosystem, etc.) unless the user's voice genuinely uses them.
- Never start a post with "I'm excited to announce" or "I'm thrilled to share" — these are LinkedIn cliches that signal the reader can skip.
- Keep the user's actual voice. If they're casual, be casual. If they're technical, be technical. Don't sanitize personality out of the post.
