# Output template — `workspace/research/YYYY-MM-DD-<slug>.md`

Every section below appears in every run's output file — quick mode shortens them, never drops them. The two sections members consistently won't find elsewhere are **Could not verify** and the **Constraints check**; they are the trust signal. Plain prose, no voice profile — this is an internal working document. Present it however relays the information best — tables, charts, visuals, plain prose: whatever you judge serves the reader.

```markdown
---
title: "<the question, short> — Research"
type: research-report
date: <YYYY-MM-DD>
mode: quick | standard | deep
status: final | partial
---

# <The question as scoped>

**As of <YYYY-MM-DD>.** <one line on how time-sensitive this answer is —
"prices and versions below will drift; re-check before acting after <rough horizon>"
or "largely stable findings.">

## The brief
<the question restated + every constraint, exactly as confirmed with the
operator, marked (stated) or (from profiles).>

## Findings
<the answer, organized however best answers the brief. Every nontrivial claim
cited inline as a markdown link or named source, with claim markers —
(self-reported), (single source), (unverified), (inference), (contested),
(secondary only) — attached where they apply, and every number dated.
Load-bearing claims carry their short verbatim anchor: a quoted phrase from
the source, so the operator can confirm in one search of the page.>

## Where sources disagree
<each contradiction: who says what, dated, with a note on which source has
more authority and why — or "No material disagreements found (and the
adversarial round looked: <what it searched for>)."> 

## Could not verify
<claims encountered but not confirmed, each with what was tried — "primary
page 403'd, no archive copy, one secondary mention only." Empty is fine;
absent is not.>

## Constraints check
- [x] <constraint> — honored: <how>
- [ ] <constraint> — could not satisfy: <why, honestly>

## What this means for you
<implications for THIS operator — their offer, pricing,
stack, audience, next decision — derived from context/business.md and
context/ICP.md. If those profiles are empty: "(implications limited —
business.md is empty; tell me your model and I'll complete this section.)"
Never generic takeaways.>

## Source table
| Source | Type | Date | Used for | Quality note |
|---|---|---|---|---|
| <linked name> | primary / official / practitioner / secondary / aggregator | <pub date> | <which findings> | <named author? lateral-checked? read fully or partial? access path if archived> |

## Method
<searches run (themes, not every query), sources fetched vs. read fully,
what the adversarial round hunted for, anything that shaped confidence —
e.g. "deep mode: 4 angles in parallel, merged and re-verified here.">
```

**Filing notes**

- Slug: kebab-case, specific enough to find later (`2026-06-11-course-platform-move`, not `2026-06-11-research`).
- If the filename exists, sharpen the slug — never overwrite a previous run.
- `status: partial` is for runs the operator cut short or that hit hard verification walls; say at the top what's missing.
- Corrections after the fact: prepend a flagged block — `> **CORRECTION (<YYYY-MM-DD>):** <what was wrong, what's true, how verified>` — and leave the original body intact. Filed research is evidence; evidence doesn't get retouched.
