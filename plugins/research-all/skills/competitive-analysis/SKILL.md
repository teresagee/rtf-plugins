---
name: competitive-analysis
description: Map a competitive landscape — players, positioning, pricing, strengths, weaknesses, and gaps. Scrapes actual competitor sites for real data.
---

# Competitive Analysis

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

Check if Perplexity and Firecrawl MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity and Firecrawl connectors set up on the Co-Writer platform. Without them, I'm limited to my training data — which means the research may be outdated or incomplete."

You map competitive landscapes using real data scraped from actual competitor sites — not summaries from training data. The goal is a clear picture of who's out there, how they position themselves, what they charge, and where the gaps are. Positioning decisions matter more than encyclopedic completeness.

## What You Need

Ask the user for:
- **Industry, niche, or specific competitors** — what market to analyze (if they give competitor names or URLs, start there)
- **Their own product or service** — what they're comparing against (pull from CLAUDE.md if available, don't re-ask)
- **Focus areas** — pricing, positioning, features, audience, content strategy, or specific aspects they care about (optional)

If the user provides competitor URLs, use them directly. Don't ask for URLs you can find yourself.

## How You Research

**Scrape first, search second.** If the user gives specific competitor URLs, scrape those with Firecrawl `scrape` immediately. Real landing pages, pricing pages, and feature lists beat secondhand summaries. Use Firecrawl `map` to discover the important pages on each competitor's site — pricing, about, features, case studies.

**Identify the field.** If the user gives an industry instead of specific competitors, use Perplexity `search_pro` to identify the key players first. Then scrape their sites. Don't rely on search results alone — go to the source.

**Get the real pricing.** Scrape pricing pages directly. If pricing isn't public, say "Pricing not publicly listed" — don't guess. If there's a "contact sales" model, note that.

**Look for positioning, not just features.** How a competitor describes themselves on their homepage tells you more than their feature list. Capture their headline, their value proposition language, who they say they're for.

**Fill gaps with search.** Use Perplexity `search_pro` for market context, reviews, press coverage, and anything the competitor sites don't reveal. Customer reviews and comparison articles often surface weaknesses that landing pages hide.

## Report Structure

```
# Competitive Landscape: [Industry/Niche]

## Market Overview
[Brief context on the market — size, trends, key dynamics. 2-3 paragraphs with citations. Set the stage without writing a textbook.]

## Competitor Profiles

### [Competitor 1]
- **What they offer:** [Core product/service in one sentence]
- **Positioning:** [How they describe themselves — use their actual language]
- **Pricing:** [Specific tiers and prices, or "Not publicly listed"]
- **Strengths:** [What they do well, based on evidence]
- **Weaknesses:** [Where they fall short — from reviews, gaps in offering, or obvious misses]
- **Notable:** [Anything interesting — recent funding, pivots, controversial takes, market moves]

### [Competitor 2]
[Same pattern. As many profiles as the landscape warrants.]

## Comparison Matrix
| Feature/Aspect | Competitor 1 | Competitor 2 | Competitor 3 | [User's Product] |
|----------------|-------------|-------------|-------------|-------------------|
| [Row 1]        |             |             |             |                   |
| [Row 2]        |             |             |             |                   |

[Include the user's own offering in the matrix if their product info is available from CLAUDE.md or provided directly. Use [NO DATA FOUND] for cells you can't verify.]

## Gaps & Opportunities
[What nobody does well. Underserved segments. Positioning white space. Pricing gaps. This is the most valuable section — it's where the user finds their edge.]

## Sources
[All URLs scraped and searched, numbered.]

1. [Competitor 1 homepage] — [URL]
2. [Competitor 1 pricing page] — [URL]
```

## Rules

- Scrape actual competitor sites — don't reconstruct from training data
- If pricing isn't public, say so explicitly. Never estimate or guess pricing
- Include the user's own offering in the comparison matrix when their product info is available
- Focus on positioning decisions over feature checklists — how competitors frame themselves matters as much as what they sell
- Every claim about a competitor needs a source. "They're the market leader" needs evidence
- Use `[NO DATA FOUND]` when you can't verify something rather than filling in from memory
- No filler language ("the competitive landscape is constantly shifting", "in an increasingly crowded market")
- Cap profiles at 5-7 competitors unless the user asks for more — depth beats breadth

## What You Don't Do

- Don't fabricate competitor details, pricing, funding amounts, or market share numbers — use only what the connectors return or flag with `[NO DATA FOUND]`
- Don't write a balanced diplomatic assessment where every competitor is "strong in some areas" — be direct about weaknesses
- Don't include competitors that aren't actually competing in the same space just to pad the list
- Don't skip the comparison matrix — it's the most scannable part of the report
- Don't editorialize about which competitor is "best" — present the evidence and let the user decide
- Don't ignore the user's own product when it's available — the whole point is to find their position relative to the field
