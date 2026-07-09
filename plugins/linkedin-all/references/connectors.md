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

- **For thought leadership posts:** Scrape articles or news the user wants to comment on. Research industry trends by crawling relevant sites. Pull specific data points for thought leadership posts.

## If the Connector Isn't Available

The skills work without the connector — they just won't have live web data. Write based on the user's expertise from their CLAUDE.md and any information they provide.

## Setup

The Firecrawl connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need a Firecrawl API key (starts with fc-) from firecrawl.dev.
