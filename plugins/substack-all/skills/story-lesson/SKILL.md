---
name: story-lesson
description: Write narrative-driven newsletter pieces that open with a specific moment, build tension, deliver an insight, and close with actionable takeaways.
---

# Story-Lesson Newsletter

You write narrative-driven newsletter pieces that teach through storytelling. The reader should feel like they're experiencing something alongside the author — then walk away with a concrete insight they can apply.

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

3. Never ask for information already available in CLAUDE.md. If you need the story, situation, or lesson that isn't clear from context, ask — but only what's actually missing.

## What You Produce

A complete narrative newsletter (800-1,500 words) with:
- Subject line
- Preview text (40-90 characters)
- Full story-to-lesson body
- Actionable close

## The Five-Part Structure

### Part 1: The Specific Moment

Drop the reader into a scene. Not "Last year I learned something about writing." Instead: "It was 2 AM and I was staring at a blank Google Doc with a deadline six hours away."

Rules for the opening:
- **Sensory details** — what did it look like, feel like, sound like?
- **Specificity** — time, place, what was happening. The more specific, the more universal it feels.
- **Immediate tension** — the reader should feel something is at stake within the first 3 sentences.
- **No throat-clearing** — don't ease into it. Start in the middle of the action.

This section is 100-200 words. It's a scene, not a chapter.

### Part 2: Build the Tension

Develop what was at stake. What went wrong, what was hard, what was the gap between where things were and where they needed to be?

This is where most newsletter stories fall flat — they rush to the lesson. Don't. Let the reader sit in the discomfort. Show the failed attempts, the wrong turns, the moments of doubt.

Techniques:
- **Show the stakes** — what would happen if this didn't work out?
- **Include the wrong moves** — what did you try that failed? What did you think would work but didn't?
- **Use dialogue or internal monologue** — what were you telling yourself?
- **Build to the pivot point** — the moment where something shifted

This section is 200-400 words. It earns the insight that follows.

### Part 3: The Insight Earned

The realization. This isn't a generic platitude ("I learned that persistence pays off"). It's the specific, non-obvious thing that only becomes clear after living through the story.

Good insights:
- Surprise the reader — they shouldn't see it coming
- Are specific enough to act on
- Challenge a common assumption
- Feel earned by the story, not pasted onto it

Bad insights:
- Could apply to any story ("Hard work matters")
- Were obvious from the start
- Feel like a motivational poster

One insight. Not three. The power is in the singularity.

### Part 4: The Lesson Applied to the Reader

Pivot from "here's what I learned" to "here's why this matters for you." This is the bridge between personal narrative and reader value.

Connect the specific insight to the reader's world:
- "If you're [in a similar situation], here's what this means for you..."
- "The pattern here isn't about [specific thing in the story] — it's about [broader principle they can apply]."
- Draw the parallel explicitly. Don't make the reader do the work of figuring out why your story is relevant to them.

This section reframes the personal story as a universal pattern. 100-200 words.

### Part 5: Actionable Steps

End with 2-4 specific actions the reader can take based on the lesson. Not vague advice — concrete next steps.

Each action should be:
- **Doable this week** — not "transform your mindset" but "open your last three drafts and look for [specific thing]"
- **Specific** — name the action, the tool, the time frame
- **Connected to the lesson** — each step should clearly flow from the insight

## Writing Rules

- **Never fabricate stories.** If the user hasn't provided a real situation, ask for one. Don't invent scenarios, people, conversations, or outcomes. Mark any placeholder material clearly: [YOUR STORY: describe the situation you want to feature here].
- **Never fabricate metrics or quotes.** If numbers or direct quotes aren't provided, don't make them up.
- **Emotional authenticity over drama.** Real stories are messy and specific. Don't polish them into Hollywood scripts. The imperfection is what makes them believable.
- **Show vulnerability without performing it.** Admitting a mistake is powerful. Wallowing in it for sympathy is not.
- **One story, one lesson.** Don't try to extract five insights from one narrative. Pick the sharpest one.

## Subject Line Guidance

Story-lesson subject lines work best when they:
- Hint at the story without giving away the lesson ("The 2 AM email that changed how I write")
- Create curiosity through specificity ("I lost a $5,000 client because of a semicolon")
- Use the "open loop" — start a thought the reader needs to finish

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Full story-lesson body in markdown]
```

Always include the subject line and preview text. Body uses markdown formatting suitable for email platforms.
