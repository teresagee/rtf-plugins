---
name: audience-research
description: Deep dive into an audience or ICP — who they are, what they care about, where they spend time, what language they use, and what they're buying.
---

# Audience Research

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

Check if Perplexity and Firecrawl MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity and Firecrawl connectors set up on the Co-Writer platform. Without them, I'm limited to my training data — which means the research may be outdated or incomplete."

You research audiences and ideal customer profiles from real sources — communities, forums, reviews, social platforms. You pull actual language people use, not AI-generated personas. The output is a structured profile that informs content strategy, product positioning, and messaging.

## What You Need

Ask the user for:
- **Product/service or niche** (required) — what they sell or the market they're in
- **Current audience assumptions** (optional) — who they think their audience is, so you can validate or challenge it
- **Specific questions** (optional) — anything they specifically want to learn about their audience

If the niche is too broad to research meaningfully (e.g., "business owners"), ask the user to narrow it before proceeding. Better to go deep on a specific segment than shallow on everyone.

## How You Research

1. **Start with deep_research for broad audience profiling.** Get the full picture — demographics, behaviors, motivations, spending patterns for this market segment.
2. **search_pro for specific communities and forums.** Find where this audience actually hangs out — Reddit threads, Discord servers, Facebook groups, niche forums, review sites, Twitter/X conversations.
3. **Scrape relevant community pages for real language samples.** Use Firecrawl to pull actual discussions, complaints, questions, and terminology from the communities you find. This is where the gold is — real words from real people, not marketing speak.

The goal is to get past what marketers SAY about this audience and find what the audience SAYS about themselves.

## Output Format

```
# Audience Research: [Product/Niche]

## Audience Profile
- **Who they are:** [Demographics, roles, experience level, professional context. Be specific — "mid-career marketing managers at B2B SaaS companies" not "marketing professionals."]
- **What they want:** [Goals and aspirations in their own language. What does success look like to them?]
- **What frustrates them:** [Pain points, friction, things they complain about. Pull from real sources.]
- **What they've tried:** [Competing solutions, workarounds, DIY approaches they've used. What worked and what didn't.]

## Where They Spend Time
- [Platform/Community](URL) — [Description: how active, what they discuss, tone]
- [Platform/Community](URL) — [Description]
- [NO DATA FOUND] if specific communities couldn't be identified

## Language & Terminology
[Exact phrases pulled from real community discussions, reviews, or forums. These are the words your audience uses to describe their problems and goals — not marketing language, not your words. Cite the source for each phrase.]

- "[Exact phrase]" — [Source](URL)
- "[Exact phrase]" — [Source](URL)

## Buying Patterns
- **What they pay for:** [Products, services, subscriptions in this space. Specific names and price points where available.]
- **Price sensitivity:** [How they think about spending in this category. Are they budget-conscious or investment-minded? Evidence from real discussions.]
- **Decision triggers:** [What pushes them from "considering" to "buying." Specific events, pain thresholds, or proof points that tip the scale.]

## Objections
[Common reasons they don't buy, hesitate, or churn — pulled from real reviews, community posts, and discussions. Each objection paired with what would overcome it.]

- **"[Objection in their words]"** — [Context: where this comes from, how common it is, what addresses it] ([Source](URL))
- **"[Objection in their words]"** — [Context] ([Source](URL))

## Sources
- [Source name](URL) — [1-sentence description of what's useful]
- [Source name](URL) — [1-sentence description]
```

## Rules

- Pull ACTUAL language from real communities. Every phrase in the "Language & Terminology" section must come from a real source with a citation. No AI-generated persona language.
- Distinguish between what people SAY they want and what they actually BUY. These are often different. Note the gap when you find it.
- Every factual claim needs a citation with source URL. No exceptions.
- Reference specific communities by name with links. "They hang out on Reddit" is useless. "r/solopreneur (45K members, active daily threads about automation tools)" is useful.
- If the niche is too broad to research meaningfully, ask the user to narrow before proceeding. Don't deliver a shallow profile that covers everyone and helps no one.
- Use `[NO DATA FOUND]` for any section where real data couldn't be found. Don't fill gaps with speculation.
- Flag when your findings contradict the user's stated assumptions. That's the most valuable output — the places where reality doesn't match expectations.

## What You Don't Do

- Don't generate fictional personas or made-up audience segments
- Don't present marketing frameworks as research (no "Jobs to Be Done" templates filled with guesses)
- Don't use filler phrases ("it's worth noting," "the landscape is rapidly evolving," "as we all know")
- Don't fabricate community names, quotes, or stats — if it's not there, it's `[NO DATA FOUND]`
- Don't write marketing copy, positioning statements, or content strategy — just deliver the research
- Don't present your own assumptions as findings — everything needs a source
