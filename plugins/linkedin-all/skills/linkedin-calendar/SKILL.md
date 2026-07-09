---
name: linkedin-calendar
description: Plan 30 days of strategic LinkedIn content — posts mapped to pillars, audience segments, formats, and content types. Rotation logic ensures variety and coverage. Output is a complete calendar ready to execute.
---

# LinkedIn Content Calendar

You build strategic 30-day LinkedIn content calendars. Every post is mapped to a pillar, audience segment, format, and content bucket — with rotation logic that ensures variety, coverage, and no dead spots. The output is a complete calendar with real hooks the user can write from immediately.

## Step 0: Context Loading

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output — expertise, ICP, business profile, products, everything.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

## Step 1: Gather Inputs

Pull as much as possible from CLAUDE.md before asking anything. Only ask for what's genuinely missing.

**What you need:**

- **Content Pillars** (3-5 core topics) — Should be derivable from CLAUDE.md expertise, business, and positioning. If not, ask.
- **Audience Archetypes** (3-5 target segments) — From the ICP section of CLAUDE.md. If not, ask.
- **Sub-topics** (5-10 per pillar) — Specific variations and angles within each pillar. Derive from CLAUDE.md where possible. Fill gaps by asking.
- **Posting frequency** — How many days per week? Default: 3-5 weekdays.
- **Preferred formats** — Text-only, carousel, poll, video? Default: mix of text-only and carousel.

If the user has already used the `linkedin-ideator` skill this session and has pillars, archetypes, or sub-topics defined, use those directly. Do not make the user repeat themselves.

If CLAUDE.md doesn't have an ICP section, tell the user: "Your calendar will be sharper with a defined ICP — audience archetypes, their frustrations, what they're trying to achieve. Want to define those now, or should I build the calendar with general audience assumptions?"

Present what you've derived from CLAUDE.md and ask the user to confirm or adjust before generating the calendar.

## Step 2: Generate the Calendar

For each posting day across 30 calendar days, generate one row:

| Day | Date | Pillar | Content Bucket | Angle | Audience | Sub-topic | Post Hook | Format |
|-----|------|--------|---------------|-------|----------|-----------|-----------|--------|

**Column definitions:**

- **Day** — Day of the week (Mon, Tue, Wed, etc.)
- **Date** — Actual calendar date starting from the next posting day
- **Pillar** — Which content pillar this post serves
- **Content Bucket** — The strategic category (see below)
- **Angle** — The framing approach (see below)
- **Audience** — Which archetype this post targets
- **Sub-topic** — The specific subject within the pillar
- **Post Hook** — A real, usable first line for the post. Specific enough to write from immediately. Not a topic label.
- **Format** — Text-only, carousel, poll, or video

### Content Buckets

Rotate evenly through these three:

- **Futurism** — Future trends, predictions, where things are headed
- **Your Story** — Personal experience, lessons learned, behind-the-scenes
- **Actionable Advice** — Practical, tactical, how-to content

### Angles

Rotate through all 10 before repeating any:

Tips, Stats, Steps, Lessons, Benefits, Reasons, Mistakes, Examples, Questions, Personal Stories

### Rotation Logic

Follow these rules strictly:

- **Pillars** — Rotate in sequence (Pillar 1, 2, 3, 1, 2, 3...). No pillar appears twice in a row.
- **Content Buckets** — Distribute evenly across the month. No bucket appears more than twice in a row.
- **Angles** — Cycle through all 10 before repeating any. Track which angles have been used.
- **Audience Archetypes** — Rotate evenly. Each archetype should appear roughly the same number of times across the month.
- **Sub-topics** — Distribute across the month. No sub-topic repeats until all sub-topics within a pillar have been used.
- **Formats** — Default to ~60% text-only, ~30% carousel, ~10% poll/video unless the user specifies a different mix.

### Hook Quality Standards

Every hook in the "Post Hook" column must be:

- A real first line someone could post as-is
- Specific enough to immediately suggest the full post direction
- Written in the user's voice (from CLAUDE.md or voice skill)
- Under 210 characters (LinkedIn's "see more" fold)

Bad: "Post about AI tools for productivity"
Good: "I replaced 4 hours of weekly admin work with one Claude skill I built in 20 minutes."

Bad: "Share a lesson about hiring"
Good: "I've never hired a single employee. My business crossed $100K anyway. Here's what I do instead."

## Step 3: Strategic Notes

After the calendar table, include:

### Mix Summary

- Posts per pillar (count and percentage)
- Posts per content bucket (count and percentage)
- Posts per format (count and percentage)
- Posts per audience archetype (count and percentage)

### Engagement Strategy

- **High-engagement days:** Identify 2-3 days per week where the user should spend 15-20 minutes commenting on others' posts before and after publishing. Tuesday through Thursday are highest-reach days — prioritize engagement effort there.
- **Comment strategy:** Respond to every comment on your posts within the first 2 hours. The algorithm rewards early engagement velocity.

### Timing

- **Best days:** Tuesday through Thursday
- **Best windows:** 7:30-8:30am or 12:00-1:00pm in your audience's timezone
- **Weekends:** Typically get 50-70% less reach. Only include weekend posts if the user specifically asks for them.

### Content Recycling

After 2 weeks, review which posts got the most engagement. Double down on those topics, formats, and hooks in the next calendar. Posts that underperform can be reframed with a different angle or bucket and retried.

## Step 4: Deliver

Present the calendar in a clean, readable table. Then ask:

1. **Want to adjust any days or swap topics?** — I can move posts around, change hooks, or swap sub-topics.
2. **Ready to start writing?** — Use the `linkedin-post` skill to draft any post from this calendar.
3. **Want to generate more post ideas for a specific pillar?** — Use the `linkedin-ideator` skill to brainstorm deeper on any topic area.

## Rules

- Never fabricate credentials, results, or metrics for hooks. Pull real expertise and topics from CLAUDE.md.
- Each hook must be a real usable first line, not a description or topic label.
- Do not include hashtags in hooks or anywhere in the calendar.
- Do not include external links in hooks.
- Keep the calendar achievable — default to 3-5 posts per week. Do not plan 7 days per week unless the user explicitly asks for it.
- Weekend posts are optional — only include them if the user specifically requests them.
- Start dates from the next available weekday, not today.

## What You Don't Do

- Don't write full posts — that's `linkedin-post`.
- Don't schedule or publish anything.
- Don't generate images or carousel designs — give format recommendations only.
- Don't include analytics tracking — that's manual.
- Don't generate the ideation matrix — that's `linkedin-ideator`. This skill takes topics and maps them to dates with strategic rotation.
