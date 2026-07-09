# Perplexity Connector

If the Perplexity connector is set up, you have access to tools that perform web research with citations. Check if Perplexity MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| search | Quick web search with cited sources |
| search_pro | Advanced search with more comprehensive results |
| deep_research | In-depth research reports with full citations |

## How Skills Should Use These

- **deep-research and trend-analysis:** Use deep_research as the primary investigation tool. These skills need the most comprehensive sourcing available.
- **competitive-analysis and audience-research:** Use search_pro for comprehensive coverage across multiple angles — competitors, positioning, audience behavior, community discussions.
- **content-research-brief and industry-briefing:** Use search and search_pro for pulling current data, recent articles, and relevant stats.
- **source-synthesis:** Use search to fact-check claims found in the provided sources and fill gaps.
- **company-research:** Use search_pro to find recent news, funding, leadership changes, and public sentiment.

## If the Connector Isn't Available

The skills work without the connector — but research quality drops significantly. Without live web access, all findings are limited to Claude's training data. No current sources, no citations, no recent developments. Reports will be general knowledge summaries rather than research.

## Setup

The Perplexity connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need a Perplexity API key (starts with pplx-) from perplexity.ai/settings/api.

---

# Firecrawl Connector

If the Firecrawl connector is set up, you have access to tools that scrape and crawl web pages. Check if Firecrawl MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| scrape | Scrape a URL and get clean markdown — articles, docs, any web page |
| crawl | Crawl an entire site or section (async, returns job ID) |
| crawl_status | Check crawl progress and retrieve results |
| map | Discover all URLs on a website |
| extract | Pull structured data from a page using a schema |

## How Skills Should Use These

- **competitive-analysis:** Scrape competitor websites to analyze messaging, features, and positioning. Use map to discover site structure and key pages. Use extract to pull structured pricing and feature data for comparison.
- **source-synthesis:** Scrape all provided URLs to get full content for analysis. This is the primary intake method — users give URLs, Firecrawl pulls the content.
- **company-research:** Scrape the company's website and use map to understand their full web presence. Use extract for structured data like team info, product details, and pricing.
- **content-research-brief and audience-research:** Scrape specific URLs the user provides as reference material. Scrape community pages, forums, or review sites for audience insights.
- **deep-research and trend-analysis:** Scrape specific sources found via Perplexity for deeper analysis when search snippets aren't enough.

## If the Connector Isn't Available

The skills work without the connector — but lose the ability to read web pages directly. Competitive analysis can't scrape competitor sites, source synthesis can't pull URL content, and company research can't analyze websites. Users would need to paste content manually.

## Setup

The Firecrawl connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need a Firecrawl API key (starts with fc-) from firecrawl.dev.
