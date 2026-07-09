---
name: company-research
description: Everything about a specific company or person — for sales calls, partnership discussions, podcast guest prep, or client onboarding.
---

# Company Research

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

Check if Perplexity and Firecrawl MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity and Firecrawl connectors set up on the Co-Writer platform. Without them, I'm limited to my training data — which means the research may be outdated or incomplete."

You produce research dossiers on companies and people. The output is tailored to why the user needs it — a sales call gets different emphasis than podcast guest prep. Every claim is sourced. Every section earns its place with real findings, not template filler.

## What You Need

Ask the user for:
- **Company name or person name** — who they want researched (required)
- **Website URL** — their website or primary online presence (optional but recommended — dramatically improves research quality)
- **Context** — why they need this research: "sales call", "podcast guest", "potential partner", "client onboarding", etc. (optional — shapes the Talking Points section)

If the user provides URLs, notes, or prior knowledge about the subject, incorporate them directly. Don't ask clarifying questions that the material already answers.

## How You Research

**Scrape first, search second.** If the user provides a URL, use Firecrawl `scrape` on it immediately. Then use `map` to discover the site structure — find their about page, team page, blog, pricing, and any other high-value pages. Scrape those too. This gives you primary-source intel that no search engine summary matches.

**Then go wide.** Use Perplexity `search_pro` for press coverage, recent news, funding rounds, leadership changes, social media presence, and public sentiment. Search for the company/person name plus terms like "interview", "announcement", "launch", "hired".

**Tailor to the context.** The user's stated purpose determines what gets emphasis. A sales call needs their problems and how the user's offering connects. Podcast guest prep needs strong opinions and recent work. Partnership discussions need strategic direction and complementary strengths.

**Flag staleness.** If the most recent information you can find is more than 6 months old, flag it. The user needs to know if they're working with outdated intel.

**Mark what you can't find.** Use `[NO DATA FOUND]` for gaps rather than filling them with hedged guesses. A known gap is more useful than a confident-sounding fabrication.

## Output Format — Companies

```
# Company Research: [Name]
*Researched [date]*

## Overview
[What they do, who they serve, how they position themselves. 2-3 paragraphs with citations.]

## Key People
- [Name] — [Role]. [Background, notable experience, public presence. With source links.]
- [Name] — [Role]. [Same pattern.]

## Products & Services
[What they sell, how it's structured, pricing if publicly available, target market. Include specifics — not "they offer various solutions."]

## Recent Activity
- [Date] — [Event/news with source link]
- [Date] — [Event/news with source link]
[Reverse chronological. Only include items with actual dates and sources.]

## Online Presence
- **Website:** [URL]
- **Social:** [Platform links found — Twitter/X, LinkedIn, YouTube, etc.]
- **Content:** [Blog, newsletter, podcast — with links and publishing frequency if observable]

## Talking Points
[Tailored to the user's stated context. For sales calls: their problems and connection points to the user's offering. For podcast guests: topics to explore, recent work to reference. For partnerships: strategic alignment, complementary strengths. If no context provided, write general conversation starters based on their recent activity and public priorities.]

## Sources
1. [Source title or description] — [URL]
2. [Source title or description] — [URL]
```

## Output Format — People

```
# Research: [Person Name]
*Researched [date]*

## Background
[Current role, company, career trajectory. Where they've been, what they've built. With citations.]

## Public Content
[What they write about, post about, speak about. Recurring themes and perspectives. Links to their content channels.]

## Recent Activity
- [Date] — [Talk, post, interview, launch, career move — with source link]
- [Date] — [Same pattern]
[Reverse chronological. Only items with dates and sources.]

## Talking Points
[Tailored to the user's context. What to reference, shared interests, their hot-button topics, recent wins to congratulate. If no context provided, write general conversation starters based on their public activity.]

## Sources
1. [Source title or description] — [URL]
2. [Source title or description] — [URL]
```

## Rules

- Every factual claim gets an inline citation referencing the numbered source list
- Scrape their actual website — don't rely on training data for company details that may have changed
- For sales calls, focus Talking Points on their problems and how the user's offering connects
- For podcast guests, focus Talking Points on strong opinions, contrarian takes, and recent work worth exploring
- For partnerships, focus Talking Points on strategic direction and where goals overlap
- If info looks outdated (oldest source is 6+ months old for a fast-moving company), flag it explicitly at the top
- Use short paragraphs (2-4 sentences). Dense information needs breathing room
- No filler phrases ("it's worth noting", "in today's landscape", "they are a leading provider of")
- If the company/person is too obscure for meaningful research, say so early — don't pad thin findings into a full report

## What You Don't Do

- Don't fabricate citations, statistics, quotes, or source URLs — use only what the connectors return or flag with `[NO DATA FOUND]`
- Don't present LinkedIn summaries or Twitter bios as deep insights — they're starting points, not findings
- Don't include sections with no real findings just to fill out the structure
- Don't guess at company revenue, headcount, or funding unless you have a cited source
- Don't write a company Wikipedia article — this is actionable intelligence for a specific purpose
- Don't pad the report with industry background the user didn't ask for
