# Voice Analysis Heuristics

When analyzing source material to build a voice profile, extract patterns across these dimensions. Be specific — vague patterns produce generic profiles.

---

## Sentence-level patterns

**Sentence length and rhythm.** Are sentences predominantly short (under 15 words) and punchy? Long and winding? Mixed with a deliberate rhythm? Count averages across samples — note the variance.

**Sentence structure.** Heavy on simple declaratives? Compound sentences with semicolons? Frequent fragments for emphasis? Long lead-ins?

**Sentence starters.** Common opener words (Most, Some, You, I, When, If). Note repetition — these are signature.

## Paragraph-level patterns

**Paragraph length.** Two sentences and out? Long blocks? Single-sentence paragraphs for impact?

**Paragraph rhythm.** Setup → punchline. Question → answer. Claim → evidence. Story → lesson.

## Vocabulary

**Favorite words.** Words the writer uses far more than baseline. Look for repetition across samples — these are signature.

**Unique phrases.** Idiomatic constructions, coined terms, distinctive phrasings.

**Avoided words.** What the writer never uses (formal "utilize", buzzwords, hedge words like "perhaps", abstractions like "synergy").

**Slang / informalism / contractions.** Frequency. Specific terms used.

**Technical vocabulary.** Does the writer use jargon? Define it? Avoid it?

## Openings

**Cold opens.** First-line patterns. Hook style — story, claim, question, observation, contrarian take?

**Throat-clearing.** Does the writer skip preamble or warm up? Note presence/absence.

## Closings

**Final beat.** Punchline? Call to action? Question to reader? Open loop? Signature signoff?

**Recurring closing patterns** (e.g., "See you next week", "Talk soon", a question to the reader).

## Transitions

**Within-paragraph transitions.** Mostly invisible (sentence flow)? Visible signposts ("First... Next... Finally...")?

**Between-paragraph transitions.** Bridge sentences? Hard cuts? Headings?

## Voice signals

**Humor.** Dry, wry, sarcastic, playful, none?

**Self-reference.** "I" frequency. First-person stories? Use of "we" for shared experience?

**Reader address.** "You" frequency. Direct address? Imperatives?

**Contractions.** Always, sometimes, never?

**Abbreviations / shorthand.** Casual ("vs", "etc", "btw") or formal?

## AI tells (the most important section)

These are patterns to flag in the profile so Claude (or the writer) knows to AVOID them in produced output:

- "Delve into", "navigate the landscape", "leverage", "robust", "comprehensive", "seamless"
- Em-dash overuse (more than 1–2 per piece)
- "It's important to note that..."
- "In conclusion..." / "To summarize..."
- "It's worth mentioning..."
- Three-item lists with parallel structure (sign of AI rhythm)
- "Crucial", "vital", "essential" as filler
- Hedge words that don't commit ("can be", "may be", "often")
- "Various", "numerous", "myriad"
- "Furthermore", "moreover", "additionally" as transitions

Document which ones appear in the source material (so the profile knows the writer STILL avoids them) and which ones the writer already avoids well.

**Voice-specific exception rule:** If the writer DOES use a pattern that's normally an AI tell (e.g., they love em-dashes), document the exception explicitly so Claude doesn't strip it out.

## Tone

**Energy level.** Calm, energetic, intense, cool?

**Authority.** Confident, hedged, exploratory, declarative?

**Warmth.** Warm, neutral, cold, intentionally distant?

## Specific quirks

Anything that doesn't fit the categories above but makes the voice recognizable:

- Unusual punctuation patterns (lots of dashes, parentheticals, ellipses)
- Recurring metaphors or imagery
- Recurring rhetorical devices (rule of three, antithesis, etc.)
- Recurring topics or angles
- Catchphrases
- Signature sign-offs

Capture these explicitly. Quirks separate a voice from a style.

---

## Confidence rules

- **Patterns must appear in at least 2 samples** to count as signature. Single-sample patterns are coincidence, not voice.
- **Document with quotes — real ones.** When you call out a pattern, include a quoted example copied verbatim from the source material. Never compose, paraphrase, or "reconstruct" a quote. Profiles without real examples produce generic output. No real quote, no pattern.
- **Weight the subject's own material heaviest.** If labeled reference pieces were supplied alongside the subject's own material, patterns from references never override patterns from the subject's own work — note explicitly which is which.
- **Watch for contamination.** If a sample reads suspiciously AI-flavored (uniform rhythm, tell-heavy vocabulary, tidy parallel lists throughout), ask the operator when and how it was written before treating it as voice evidence.

## Specificity rules

Bad: "Uses short sentences."
Good: "Sentences average 12 words. Frequently uses single-sentence paragraphs for emphasis. Longest sentence in this batch: 23 words."

Bad: "Has a friendly tone."
Good: "Warm, slightly self-deprecating. Uses 'you' direct address every 3–4 sentences on average. Asks the reader rhetorical questions to shift pace ('Sound familiar?', 'Make sense?')."

Bad: "Uses contractions."
Good: "Contractions in 90%+ of cases. 'It's', 'you're', 'I'd', 'don't' throughout. Never 'cannot' — always 'can't'."

Specific patterns produce voice-faithful output. Vague patterns produce AI-default output dressed in vague voice clothing.
