---
name: source-synthesis
description: Give it URLs — it scrapes them all and synthesizes into a structured brief with key themes, agreements, contradictions, and pull quotes.
---

# Source Synthesis

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

Check if Perplexity and Firecrawl MCP tools are available. If they're not, tell the user upfront: "This skill works best with the Perplexity and Firecrawl connectors set up on the Co-Writer platform. Without them, I'm limited to my training data — which means the research may be outdated or incomplete."

You scrape a set of URLs the user provides and synthesize them into a structured brief. The goal is saving the user from reading 5-10 articles by pulling out what matters — where sources agree, where they disagree, what's unique, and what quotes are worth pulling. Every point gets attributed to its source. You don't flatten different perspectives into false consensus.

## What You Need

Ask the user for:
- **URLs to synthesize** — at least 2 (the more, the richer the synthesis)
- **Focus question** — what they're trying to answer or understand across these sources (optional)
- **Output purpose** — how they'll use this: "for a newsletter", "for a client presentation", "for a content brief" (optional — helps you emphasize the right things)

If the user provides notes or context alongside the URLs, incorporate them directly. Don't ask clarifying questions that the material already answers.

## How You Research

**Scrape everything first, synthesize second.** Use Firecrawl `scrape` on every URL before you write a single word. Read each source completely. Don't summarize from titles or snippets — the value is in what's actually written, not what the headline suggests.

**If a URL fails to scrape, flag it and keep going.** Mark it in the Sources Analyzed section as `[SCRAPE FAILED]` and continue with whatever you got. Don't let one broken link stall the whole synthesis.

**Attribute every point to its source.** When you say "AI adoption in enterprise is accelerating," the reader needs to know who said that. Inline citations referencing the numbered source list on every claim.

**Preserve original framing.** Different authors emphasize different things for different reasons. Don't sand down disagreements into bland consensus. If one source says the market is booming and another says it's a bubble, present both with their reasoning.

**Fact-check what seems off.** If a claim in one source contradicts others or seems questionable, use Perplexity `search` to verify. Flag anything you can't confirm.

**Let the focus question guide emphasis.** If the user gave a focus question, weight the synthesis toward answering it. Everything in the output should connect back to what they're trying to understand.

## Synthesis Structure

```
# Source Synthesis: [Focus Question or Topic]

## Sources Analyzed
1. [Title] — [URL] — [1-line description of what this source covers]
2. [Title] — [URL] — [1-line description]
3. [Title] — [URL] — [SCRAPE FAILED — excluded from analysis]

## Key Themes

### [Theme 1]
[What multiple sources agree on. Inline citations showing which sources support each point. 2-3 sentences per theme — dense, not padded.]

### [Theme 2]
[Same pattern. As many themes as the sources actually support — no invented categories.]

## Points of Disagreement
[Where sources contradict each other. Present both sides with their reasoning and citations. Don't pick a winner unless the evidence is overwhelming.]

## Unique Insights
[Ideas or data points that appear in only one source but are worth highlighting. Attribute clearly — these are one author's perspective, not consensus.]

## Synthesis
[The unified picture. What it all adds up to when you step back. 3-5 sentences connecting the themes, disagreements, and unique insights into a coherent takeaway. If there's a focus question, answer it here.]

## Pull Quotes
- "[Direct quote worth using]" — [Source name/author] [citation number]
- "[Direct quote worth using]" — [Source name/author] [citation number]

## Sources
1. [Source title or description] — [URL]
2. [Source title or description] — [URL]
```

## Rules

- Scrape every URL with Firecrawl before synthesizing — don't work from titles or assumptions
- Every factual claim gets an inline citation referencing the numbered source list
- If a source fails to scrape, mark it `[SCRAPE FAILED]` in Sources Analyzed and exclude from the synthesis
- Minimum 2 URLs to run this skill — with only 1 source there's nothing to synthesize
- No filler phrases ("it's worth noting", "interestingly enough", "the landscape is rapidly evolving")
- Pull quotes must be exact — don't paraphrase and put it in quotation marks
- Use `[NO DATA FOUND]` for gaps rather than filling them with hedged guesses
- If the sources are all saying the same thing with no disagreements, say so — don't manufacture tension

## What You Don't Do

- Don't fabricate citations, statistics, quotes, or source URLs — use only what the connectors return or flag with `[NO DATA FOUND]`
- Don't summarize sources individually — this is a synthesis, not a list of summaries
- Don't flatten disagreements into consensus — real disagreements are the most valuable part
- Don't add outside research unless fact-checking a specific claim — the user chose these sources for a reason
- Don't invent pull quotes — if there are no quotable lines, drop the section
- Don't pad themes with obvious observations — every theme should reveal something the user wouldn't get from skimming headlines
