# Voice Profile SKILL.md Template

The structure for the generated voice profile. Fill `{{PLACEHOLDERS}}` from the interview answers and the sample analysis. The depth bar is high — every pattern carries a real quote, vocabulary is a table with context, quirks are named and explained. A thin profile produces generic output.

---

```markdown
---
name: Voice — {{SUBJECT_DISPLAY_NAME}}
description: Use this skill when writing in the voice of {{SUBJECT_DISPLAY_NAME}} — {{FORMATS_AND_CONTEXTS_THIS_VOICE_COVERS}}. Triggers when Claude is asked to draft, edit, or rewrite anything that should sound like {{SUBJECT_DISPLAY_NAME}}.{{IF_CONTEXT_PROFILE: Auto-activates when {{CONTEXT_PROFILE_PATH}} is loaded.}}
voice-type: {{self | client | brand}}
subject: {{SUBJECT_KEBAB_CASE}}
context-profile: {{CONTEXT_PROFILE_PATH_OR_OMIT_FIELD}}
source-material-summary: {{ONE_LINE — count, types, date range, low-confidence flag if under 3 samples, known gaps}}
version: 1
last-updated: {{YYYY-MM-DD}}
---

# Voice — {{SUBJECT_DISPLAY_NAME}}

## Subject identification

{{ONE_PARAGRAPH — who this voice belongs to, what they do, what content this voice serves, who the reader is and what relationship the voice holds with them. Concrete facts from the context profiles and interview — nothing invented.}}

## Source material summary

Analyzed {{COUNT}} samples — {{TYPES_AND_ROUGH_SIZES}}. Range: {{DATE_RANGE_IF_KNOWN}}.

{{WHICH_REGISTER_THE_PROFILE_LEANS_ON (e.g. "leans spoken — refresh with published written pieces when available") AND_ANY_LOW_CONFIDENCE_NOTE}}

## Signature patterns

### Sentence rhythm

{{The signature rhythm patterns, each stated specifically (averages, variance), backed by a verbatim quote from the samples, with any usage guidance ("use sparingly", "spoken mode only").}}

### Paragraph structure

{{The recurring paragraph moves, with quoted examples.}}

### Openings

{{The typical opening moves, each named (e.g. "narrative cold open", "direct claim") with a verbatim quoted example.}}

### Closings

{{The typical closing moves with quoted examples. Note any signoffs the subject does NOT use.}}

### Transitions

{{HOW_THIS_VOICE_MOVES_BETWEEN_IDEAS — invisible flow vs signposts, recurring bridge phrases, with quotes.}}

## Vocabulary

### Use

| Word / phrase | Context |
| --- | --- |
| {{TERM}} | {{WHEN_AND_HOW_THE_SUBJECT_USES_IT}} |
| {{...AS_MANY_ROWS_AS_THE_SAMPLES_EVIDENCE — favorite words, coined terms, phrasal verbs, domain terms, emphasis words}} | |

### Avoid

{{Standard AI tells, plus everything the interview and samples show this subject never says: banned words, throat-clearing, hedge filler, tones (e.g. "tutorial-pupil framing"). Be specific about WHY where it helps.}}

## Voice signals

- **Humor:** {{TYPE_AND_FREQUENCY_WITH_EXAMPLE_IF_AVAILABLE}}
- **Self-reference (I / me):** {{FREQUENCY_AND_PATTERN}}
- **Reader address (you):** {{FREQUENCY_AND_PATTERN — imperatives? questions?}}
- **Contractions:** {{POLICY_WITH_EXAMPLES}}
- **Abbreviations / shorthand:** {{POLICY}}
- **Tone (three words):** {{ENERGY. AUTHORITY. WARMTH.}}

## Quirks

{{THE SECTION THAT SEPARATES THIS VOICE FROM A GENERIC ONE. Name each quirk, explain it, quote it. Recurring rhetorical devices, punctuation habits, signature proof moves, recurring framings, catchphrases. Preserve oddities — do not sanitize.}}

## AI tells to actively avoid

In addition to the Avoid vocabulary above:

{{The AI-default patterns most dangerous for THIS voice, each with what the correct version looks like instead (e.g. "em-dash as rhythmic crutch — this voice uses at most 2 per 500 words, always as a clarifier").}}

**Exception:** {{IF_APPLICABLE — patterns that look like AI tells but are genuinely this subject's voice (em-dashes, first-person density, parallel lists with substance). Name them and instruct: preserve, strip only the AI-default form. OMIT_SECTION_IF_NONE.}}

## Examples

### Good — sounds like the voice

> {{VERBATIM_QUOTE_FROM_SAMPLES_1}}
> *Why it works:* {{THE_PATTERNS_IT_DEMONSTRATES}}

> {{VERBATIM_QUOTE_FROM_SAMPLES_2}}
> *Why it works:* {{...}}

{{2-4 GOOD EXAMPLES TOTAL — all copied verbatim from the samples.}}

### Bad — sounds off

> {{COUNTER_EXAMPLE_1 — written to demonstrate the failure modes, clearly labeled as a counter-example}}
> *Why it's off:* {{NAME_EVERY_FLAW}}

{{2-3 BAD EXAMPLES — these are the one place composed text is allowed, because they exist to show what to avoid. Build them from the AI tells and the interview's "off version" answers.}}

## Update policy

Refresh this profile when:

- {{COUNT}} new substantial pieces exist in a register this profile is thin on
- Produced output drifts noticeably from how {{SUBJECT_DISPLAY_NAME}} actually sounds
- A new format gets added that this profile doesn't cover with examples
- {{CUSTOM_TRIGGERS_FROM_THE_INTERVIEW_IF_ANY}}

Run `/voice-creation:import {{SUBJECT_KEBAB_CASE}}` to refresh. Never edit the installed copy of this skill — rebuild from the source under `workspace/voices/{{SUBJECT_KEBAB_CASE}}/`, then install the fresh zip.

## Update log

- {{YYYY-MM-DD}} — Created (v1). {{ONE_LINE_ON_THE_INITIAL_SAMPLE_SET_AND_KNOWN_GAPS}}
```

---

## Filling rules

- **Every quoted example is verbatim from the samples on disk.** Direct copy-paste, not paraphrase, not reconstruction. The only composed text allowed is the "Bad — sounds off" counter-examples, which are labeled as such.
- **No real quote, no pattern.** If a pattern can't be evidenced with a quote, it doesn't go in the profile.
- **Be specific.** "Uses short sentences" is useless. "Sentences average 12 words; longest in this batch was 23" is usable.
- **Respect the naming convention.** If the operator uses codenames for clients, the codename is the display name — the real name appears nowhere in the profile.- **voice-type is non-negotiable.** Always set `self`, `client`, or `brand` honestly — downstream skills rely on it.
- **Note the gaps.** If the profile leans on one register (all spoken, all social), say so in the source summary and the update policy so the first refresh knows where to aim.
