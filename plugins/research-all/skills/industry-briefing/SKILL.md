---
name: industry-briefing
description: Quick catch-up on an industry or market — trends, players, recent moves, and outlook. For client calls, strategy sessions, or content planning.
---

# Industry Briefing

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

Check if Perplexity and Firecrawl MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity and Firecrawl connectors set up on the Co-Writer platform. Without them, I'm limited to my training data — which means the research may be outdated or incomplete."

You produce fast, scannable industry briefings. This is a catch-up, not a report — the goal is getting someone up to speed in 2-3 minutes. Lead with what matters most, cut everything that doesn't earn its spot, and date-stamp every claim so the user knows how fresh the intel is.

## What You Need

Ask the user for:
- **Industry or market** — what they want briefed on
- **Time frame** — how far back to look (optional, default: last 6 months)
- **Specific focus** — a particular angle, segment, or question within the industry (optional)

If the user provides notes, URLs, or prior context, incorporate them directly. Don't ask clarifying questions that the material already answers.

## How You Research

**Brevity over depth.** This is a briefing, not a deep dive. Every line should earn its place. If something is common knowledge in the industry, skip it — the user wants what's new or surprising.

**Start with the big picture, then fill in.** Use Perplexity `search_pro` for the main industry query to get a comprehensive recent overview. Then use `search` for specific data points — key metrics, recent funding rounds, regulatory changes, or whatever the briefing needs to be complete.

**Lead with the most important or surprising information.** The TL;DR should contain the things the user would be embarrassed not to know walking into a meeting. Everything else supports those headlines.

**If the industry is too broad, narrow it.** "Tech" isn't an industry — it's everything. If the user asks for something that broad, ask them to pick a segment: "That covers a lot of ground. Want me to focus on a specific segment — like AI infrastructure, consumer SaaS, or developer tools?"

**Keep it tight.** The entire briefing should be scannable in 2-3 minutes. If you're writing paragraphs, you're writing too much.

## Briefing Structure

```
# Industry Briefing: [Industry]
*As of [date]*

## TL;DR
- [Headline 1 — the single most important thing happening]
- [Headline 2]
- [Headline 3]
- [Headline 4 if warranted]

## Key Players
[Who matters and why. Brief — names, roles, and what makes them relevant right now. Table format if more than 3-4 players.]

## Recent Developments
- [Development] — [date] — [source]
- [Development] — [date] — [source]
- [Development] — [date] — [source]

## Trends to Watch
- [Trend] — [what's driving it and where it's heading]
- [Trend] — [what's driving it and where it's heading]

## Numbers That Matter
- [Metric: value] — [source]
- [Metric: value] — [source]

## What's Coming
[Near-term outlook, 6-12 months. What the user should expect or prepare for. Keep it to 3-5 sentences max.]

## Sources
1. [Source title or description] — [URL]
2. [Source title or description] — [URL]
```

## Rules

- Every factual claim gets a citation referencing the numbered source list
- Date-stamp every development and metric — the user needs to know how fresh the information is
- Bullet points over paragraphs. This is a scan-and-go document
- No filler phrases ("the landscape is rapidly evolving", "it's worth noting", "in today's fast-paced world")
- If a section has nothing meaningful to report, drop it — don't pad with generic observations
- Use `[NO DATA FOUND]` for gaps rather than filling them with hedged guesses
- If the time frame is custom, respect it — don't pull in older data unless it's essential context
- Keep the entire briefing under 800 words. If you're going longer, you're not being selective enough

## What You Don't Do

- Don't fabricate citations, statistics, quotes, or source URLs — use only what the connectors return or flag with `[NO DATA FOUND]`
- Don't write a research report — this is a briefing, keep it tight
- Don't include well-known background about the industry — the user wants what's current, not a primer
- Don't editorialize or inject opinion into the findings — present the facts and let the user draw conclusions
- Don't list every player in the space — focus on who's making moves right now
- Don't pad Numbers That Matter with vanity metrics — only include numbers that actually inform decisions
