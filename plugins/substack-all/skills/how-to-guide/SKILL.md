---
name: how-to-guide
description: "Write screenshot-heavy, step-by-step how-to newsletters for Substack using the proven format that's earned top creators 1,000-2,600+ likes per post. Generates the full post: hook with credibility proof, two pre-content CTAs, optional skip-section, Roman-numeral or numbered main sections with screenshot placeholders throughout, \"Your first X minutes\" action plan, and honesty close with share CTA. Adapts to any niche based on the user's CLAUDE.md context."
---

# How-To Guide Newsletter

You write long-form, screenshot-heavy, step-by-step how-to newsletters for Substack. The format is based on the structure used by top Substack creators whose how-to posts consistently earn 1,000-2,600+ likes and thousands of shares.

This is the format. The content, niche, and voice come from the user's CLAUDE.md and voice profile.

## Before You Write

1. **Read the CLAUDE.md file silently.** Use the user's context, niche, audience, and positioning without narrating that you're reading it.
2. **Apply the voice profile from the `voices` plugin.** `/voices:self` for the operator's own writing, `/voices:<codename>` for client work. If no matching voice profile exists, derive voice from `@context/user.md` (or `@context/<codename>/user.md`). Never produce in generic default voice.
3. **Never ask for information already in CLAUDE.md.** Only ask about the specific topic, outcome, or prerequisites if genuinely unclear.
4. **Get the specific topic and outcome before starting.** "How to build X with Y" is different from "How to write your first Z."

## What You Produce

A complete Substack how-to newsletter with:
- Subject line (short, punchy — often single word or short phrase with period)
- Subtitle (one sentence teaser, often ending with colon)
- Hook section with credibility proof
- Two pre-content CTAs (save + share)
- Optional "skip this if you already know X" section
- Main content in Roman-numeral or numbered sections
- Subsections with short paragraphs and screenshot placeholders throughout
- "Your first X minutes" time-blocked action plan
- Honesty close with subscribe + share CTA

## The Format

### 1. Subject line and subtitle

**Subject line:** Short, punchy, often single word or short phrase ending with a period. Examples:
- "Claude Code."
- "Claude."
- "Skills."
- "Stop prompting."

The period at the end is intentional — it's a visual anchor that signals "this is a how-to." Adapt to the user's topic but keep the short-and-declarative pattern.

**Subtitle:** One sentence that previews the payoff, often ending with a colon. Examples:
- "How to set up [thing] (the right way):"
- "The framework behind [outcome] — now a downloadable [resource]."
- "How to [achieve outcome] in [time]:"

### 2. The hook (first 200-400 words)

Open with a lived observation, a short provocative claim, or a direct call-out. Never a preamble. Never "In this post we'll cover..."

**Hook patterns that work:**
- **Provocation:** "Stop [doing common thing]." / "[Common approach] doesn't work."
- **Lived observation:** "The [role] I talk to every day quietly switched." / "I've been [doing X] for months."
- **Personal admission:** "I used to [common mistake]. Every single time."

After the hook line, include:

1. **Credibility proof** — a screenshot, stat, or third-party validation that earns the reader's trust. Examples:
   - Screenshot of relevant dashboard, metrics, or results
   - Industry data or market stats
   - Personal proof (results, output, volume)
   - Social proof (comments, DMs, engagement)
   
   Always insert as `[SCREENSHOT: description of what to capture]`.

2. **Setup/framing** — 2-4 short paragraphs describing the problem or opportunity. Why this matters right now. What changes if the reader figures this out.

3. **What this guide delivers** — one line previewing the outcome. "This free guide shows you exactly what & how."

### 3. Pre-content CTAs (required)

Before the main content, include two explicit asks:

> Before we start, do two things:
> 
> 1. Save this guide & block [X] minutes this week to [action].
> 2. Send it to anyone who hasn't [done thing yet].

Follow with a share button: `[Share]`

This is non-negotiable. It's the share-driven growth mechanism that makes this format work at scale.

### 4. Skip section (optional, recommended for advanced topics)

If the guide builds on foundational knowledge, add a short "Skip this if you already know X" section. Gives a 5-8 bullet recap so existing users don't feel condescended to and can jump to the new material.

Example structure:
```
## Skip this part if your [thing] is already set up.

I hate starting a newsletter by telling you: **"hey, go read a previous newsletter"**.

But I wrote a guide on [foundation]. If you've read it, skip to [next section].

If not, here's the fastest recap:

1. [Step 1 summary]
2. [Step 2 summary]
...
```

### 5. Main content sections

Organize in one of two patterns:

**Pattern A: Roman numeral sections** (for comprehensive guides covering multiple major concepts)
- `## I - [Section title].`
- `## II - [Section title].`
- `## III - [Section title].`
- Period at the end of the heading for aesthetic consistency

**Pattern B: Numbered concepts** (for guides covering multiple features or steps)
- `## 1. [Thing name]`
- `## 2. [Thing name]`
- `## 3. [Thing name]`

**Inside each section:**

Use H4 (`####`) for subsections. Examples:
- `#### **What it is (in 10 words):**`
- `#### **Why it matters:**`
- `#### **How to install:**`
- `#### **Your first prompt:**`
- `#### **Step 1: [Action]**`

**Content rules for each subsection:**

- Short paragraphs (1-3 sentences max)
- Bold key terms and phrases for emphasis
- Numbered lists (`1. 2. 3.`) for sequential steps
- Bullet lists only when order doesn't matter
- Code blocks for copy-paste prompts, file structures, or commands
- Screenshot placeholder every 100-200 words: `[SCREENSHOT: description + caption]`
- Italic asides in parens for personality: _(like this, a quick aside)_

**Screenshot formula:**

Every screenshot placeholder should include:
- `[SCREENSHOT: what to capture]` — the visual itself
- Short italic caption underneath explaining what the reader is seeing

Example:
```
[SCREENSHOT: settings menu showing the specific tab you need to click]

*This is where the magic happens — most people never find this tab.*
```

**Copy-paste content goes in code blocks:**

If the guide includes prompts, templates, file structures, or commands the reader will copy-paste, put them in fenced code blocks. Make them copy-pasteable and immediately useful.

### 6. "Your first X minutes" action plan

At the end of the main content, before the honesty close, include a time-blocked action plan. This is where the reader turns reading into doing.

Format:

```
## **Your first [X] minutes with [thing].**

Open your calendar. Block [X] minutes this week.

#### **Minutes 0-5: [Action]**

[What to do, step by step.]

#### **Minutes 5-10: [Action]**

[What to do, step by step.]

...continue through the full time block.

You are [outcome] now. In [time].
```

The action plan compresses the whole guide into an actionable sprint. Use 20, 30, or 45 minutes depending on scope.

### 7. Honesty close

A short personal section at the end that:

1. States the user's mission or why they write this newsletter
2. Shares social proof (subscriber count, community size, results)
3. Asks for shares with a genuine frame: "be that person for someone else"
4. One more share button

Example template (adapt to user's voice and positioning):

```
## **Why I write this.**

[Personal mission statement — why this newsletter exists.]

[Social proof — who reads this, what they get out of it.]

**If this helped you, be that person for someone else** (and share it):

[Share]
```

Pull the specific voice, mission, and social proof from the user's CLAUDE.md.

### 8. Resource tease (optional)

If the guide teaches a concept that has a downloadable resource, skill, template, or paid version, include a soft tease before the honesty close:

```
---

**If you want this as a [resource type] you can [install/download/use] in one click** — it's [where to find it]. Teach yourself the concept here, or grab the tool and skip the setup.

---
```

This is the free-to-paid conversion mechanism. Free post teaches, paid resource delivers the tool.

## Writing Rules

- **Heading style from voice profile.** Check the voice profile for sentence case vs title case preference.
- **Short paragraphs.** 1-3 sentences max. Lots of whitespace.
- **Bold for emphasis.** Used liberally but not wildly — only on phrases that matter.
- **No filler.** No "In this post we'll cover..." No "Let's dive in." No "I hope you found this useful." Cut all of it.
- **Screenshots every 100-200 words** — this is the format's defining characteristic. A how-to post without screenshots is not a how-to post.
- **One action per step.** If a step has "and" joining two actions, split it.
- **Copy-paste content in code blocks.** Readers should be able to grab it in one click.
- **Link internally** when referencing previous guides or related posts.
- **Italic parenthetical asides** for personality: _(yes, I actually ran this)_, _(trust me on this one)_.
- **Never claim what you don't know.** If you're unsure about a specific detail or behavior, flag with `[VERIFY: what to check]`.
- **Adapt voice to the user.** Pull personality, energy, and tone from the voice profile or CLAUDE.md. Don't default to any single creator's voice.

## Length

A full how-to guide in this format runs **2,000-4,000 words**. Shorter than that and it feels thin. Longer than that and it's a masterclass or course.

If the topic can't be covered in 4,000 words, split it into a series. Each post should deliver a complete result on its own.

## Niche Adaptation

This format works for any niche. Adapt the content to the user's context:

- **B2B/SaaS:** Use business examples, ROI framing, team workflows
- **Creators/Writers:** Use content examples, voice, publishing workflows
- **Fitness/Health:** Use training examples, protocols, measurable outcomes
- **Finance:** Use numbers, market data, specific investment or money workflows
- **Developers:** Use technical examples, code snippets, system design
- **Any niche:** Screenshots and step-by-step walkthroughs of whatever the user teaches

The format is universal. The subject matter comes from the user's CLAUDE.md.

## Output Format

```
**Subject:** [short, punchy, often ending with period]
**Subtitle:** [one sentence teaser with colon]
**Cover image:** [description of what to create — usually a bold title card with the theme]

---

[Hook paragraph]

[SCREENSHOT: credibility proof]

[Setup paragraphs]

[This guide delivers X]

Before we start, do two things:

1. Save this guide & block [X] minutes this week to [action].
2. Send it to anyone who hasn't [tried thing yet].

[Share]

---

## Skip this part if you already [have X].

[Recap 5-8 bullets]

---

## I - [Section 1 title].

[Intro — 2-3 short paragraphs]

#### **Step 1: [Action]**

[Instruction]

[SCREENSHOT: description]

[Expected result]

#### **Step 2: [Action]**

[Instruction]

[SCREENSHOT: description]

...

---

## II - [Section 2 title].

...continue structure...

---

## **Your first [X] minutes with [thing].**

Open your calendar. Block [X] minutes.

#### **Minutes 0-5: [Action]**

[Steps]

#### **Minutes 5-10: [Action]**

[Steps]

...

You are [outcome] now.

[Share]

---

[Optional: Resource tease]

---

## **Why I write this.**

[Honesty paragraph in user's voice, pulled from CLAUDE.md]

[Share]
```

## Final Notes

The format is the proven structure. The voice, niche, and content are pulled from the user's CLAUDE.md and voice profile. Never inject a default voice or personality — every how-to guide should sound like the user wrote it.

The screenshot-heavy format is non-negotiable. A how-to without screenshots breaks the pattern that makes this format work.
