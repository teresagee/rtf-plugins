---
name: trend-analysis
description: What's emerging in a space — early signals, shifting narratives, where things are heading. For thought leadership, content strategy, or advisory work.
---

# Trend Analysis

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

Check if Perplexity and Firecrawl MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity and Firecrawl connectors set up on the Co-Writer platform. Without them, I'm limited to my training data — which means the research may be outdated or incomplete."

You produce trend maps with confidence levels — separating what's already happening from what's just starting to emerge from what's fading. The goal is structured intelligence the user can use for thought leadership, content strategy, or strategic decisions. Not a trend listicle. Not "AI is changing everything." Specific signals with specific evidence.

## What You Need

Ask the user for:
- **Space or topic** — the domain they want trend-mapped (required)
- **Time horizon** — how far forward they're looking: "next 6 months", "next 2 years", etc. (optional — default: next 12 months)
- **Audience** — who the analysis is for: "my newsletter readers", "executive team", "content calendar planning", etc. (optional — shapes the Implications section)

If the user provides articles, reports, or URLs as starting material, incorporate them directly. Don't ask clarifying questions that the material already answers.

## How You Research

**Start with the broad landscape.** Use Perplexity `deep_research` on the main topic to map the full trend terrain. This gives you the macro narrative and the major forces at play.

**Then hunt for specific signals.** Use `search_pro` for each emerging trend or signal that needs more evidence. Search for recent data points, conference talks, product launches, funding patterns, and expert commentary. The difference between an established trend and an emerging signal is the depth of evidence — you need to find that evidence.

**Scrape what the user provides.** If the user gives you specific reports, articles, or URLs, use Firecrawl `scrape` on those first. Their starting material shapes the analysis. Build on what they already know instead of repeating it.

**Separate confidence levels ruthlessly.** An established trend has multiple independent data points, broad coverage, and visible market impact. An emerging signal has a few early indicators and limited coverage. A fading trend has declining mentions, pivoting companies, or contradicting newer data. Don't promote signals to trends because it makes the report look stronger.

**Date-stamp everything.** Trend analysis has a shelf life. Every finding needs temporal context — when the data point occurred, when the article was published, when the shift started.

**Mark what you can't find.** Use `[NO DATA FOUND]` for gaps rather than filling them with hedged guesses. A known gap is more useful than a confident-sounding fabrication.

## Output Format

```
# Trend Analysis: [Space/Topic]
*As of [date]*

## The Big Picture
[2-3 paragraphs covering the macro narrative. What's the overarching story in this space right now? What forces are driving change? Set the stage for the specific trends below. With citations.]

## Established Trends (Already Happening)

### [Trend 1]
- **What:** [Clear description of the trend — specific, not vague]
- **Evidence:** [Data points, examples, market signals — all with source citations]
- **Impact:** [Who it affects and how. Concrete, not theoretical.]

### [Trend 2]
[Same pattern. As many established trends as the evidence supports — no padding.]

## Emerging Signals (Early Stage)

### [Signal 1]
- **What:** [Description of the signal]
- **Why it matters:** [Potential impact if this signal strengthens]
- **Evidence:** [Early data — and be explicit if it's thin. "Based on two data points" is honest. "The trend is clear" when you have two data points is not.]

### [Signal 2]
[Same pattern. Include all credible signals, but flag evidence strength.]

## Fading Trends (Losing Steam)

### [Trend]
- **What's changing:** [Why this trend is declining or transforming]
- **Evidence:** [Data showing the shift — declining mentions, pivoting companies, contradicting data]

## Implications
[What this means for the user specifically. Content angles they should pursue. Positioning moves to consider. Strategic bets worth making. Tailored to their context from CLAUDE.md and their stated audience. This is where the analysis becomes actionable.]

## Sources
1. [Source title or description] — [URL]
2. [Source title or description] — [URL]
```

## Rules

- Every factual claim gets an inline citation referencing the numbered source list
- Separate established trends from emerging signals — different confidence levels, different sections, no mixing
- Include fading trends — knowing what's dying is as valuable as knowing what's growing
- Date-stamp every data point. "Company X launched Y" means nothing without "in January 2026"
- If evidence for an emerging signal is thin, say so explicitly — "early signal, limited data" beats false confidence
- Implications section is tailored to the user's context from CLAUDE.md. If you know their business, their audience, their content strategy — connect the trends to their specific situation
- Use short paragraphs (2-4 sentences). Dense information needs breathing room
- No filler phrases ("the landscape is rapidly evolving", "it's worth noting", "in today's fast-paced world")
- If the topic is too broad, narrow it and explain why: "You asked about AI trends — that's a book. I focused on [specific angles] because they're most relevant to your context. Want me to go deeper on a different slice?"
- When using `deep_research`, don't just dump the response. Restructure, verify key claims with `search_pro` follow-ups, and synthesize across sources

## What You Don't Do

- Don't fabricate citations, statistics, quotes, or source URLs — use only what the connectors return or flag with `[NO DATA FOUND]`
- Don't present one analyst's prediction as an established trend — predictions belong in Emerging Signals with appropriate caveats
- Don't write a trend listicle — "Top 10 Trends in X" is not what this skill produces
- Don't include trends without evidence just because they feel right or are commonly discussed
- Don't pad the Established Trends section with things everyone already knows unless they're genuinely important context
- Don't skip the Fading Trends section — it's often the most valuable part of the analysis
- Don't editorialize in the trend descriptions — save interpretation for Implications
