---
name: lead-magnet
description: Create a short, focused ebook for email capture — actionable, fast-paced, designed to demonstrate expertise and drive signups.
---

# Lead Magnet Ebook

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

You create short ebooks (10-20 pages, 3,000-6,000 words) designed as freebies for email capture. These are not mini-books — they're focused, fast, and actionable. Every page delivers value. The reader finishes it in one sitting and thinks "I need to see what else this person has."

## What You Need

Ask the user for:
- **Topic** (required) — what the lead magnet covers
- **Target audience** (optional) — who's downloading this (pull from CLAUDE.md if available, don't re-ask)
- **Desired length** (optional) — default is 10-20 pages / 3,000-6,000 words
- **CTA at the end** (optional) — what action the reader should take after finishing (e.g., "sign up for my newsletter," "book a call," "join the waitlist"). Ask if not given.

If the user provides a brief, outline, or notes, use them directly. Don't ask questions the material already answers.

## How You Write

### Step 1: Propose the Concept

Before writing anything, present:
- **Title and subtitle** — benefit-driven, specific to the audience
- **The hook** — why someone downloads this instead of reading a blog post
- **Chapter structure** — 3-5 chapters, each with a one-sentence description of what it covers

**WAIT for the user to approve before writing.** Don't proceed until they confirm or adjust the concept.

### Step 2: Write the Content

**Open with value, not gratitude.** The first page delivers insight, not "Thanks for downloading this ebook!" The reader should learn something in the first 300 words.

**3-5 chapters maximum.** More than five and it's a book, not a lead magnet. Each chapter is tight — 600-1,200 words — and covers one clear idea.

**Every chapter ends with an action step.** Something the reader can do RIGHT NOW. Not "think about how this applies to you" — a concrete action with a specific outcome.

**Shorter paragraphs than a full ebook.** 1-3 sentences per paragraph. This gets consumed in one sitting, probably on a phone. Dense walls of text kill the momentum.

**Final chapter transitions into the CTA naturally.** The last chapter delivers value on its own, then flows into "here's the next step" — not a hard pivot to "BUY MY COURSE." The CTA should feel like the logical next action after everything the reader just learned.

## Output Format

Save the lead magnet as a markdown file with this structure:

```
---
title: Lead Magnet Title
subtitle: Benefit-driven subtitle
author: [INSERT: author name]
date: [INSERT: date]
---

# [Hook Chapter — Delivers Value Immediately]

[Content — opens with insight, not preamble]

**Action step:** [Specific thing the reader can do right now]

# [Chapter 2 — Practical, Actionable]

[Content — builds on chapter 1, introduces next concept]

**Action step:** [Concrete action with clear outcome]

# [Chapter 3 — Deeper Application]

[Content — takes concepts further, real-world application]

**Action step:** [What to do next]

# [Final Chapter — Ties to CTA]

[Content — delivers final value, then naturally transitions]

**Next step:** [CTA — what the reader should do now]
```

## Rules

- NOT a mini-book. Focused, fast, actionable. If it can't be read in one sitting, it's too long.
- 3-5 chapters MAX. Every chapter earns its place.
- Open with value, not gratitude. No "Thanks for downloading!" or "I'm so glad you're here."
- No filler, no padding, no "In this ebook, you'll learn..." preamble.
- Every chapter ends with something the reader can do RIGHT NOW.
- CTA feels natural — "here's the next step" not "BUY MY THING."
- Shorter paragraphs than a full ebook — this is consumed in one sitting.
- Use `**bold**` for key phrases and action steps.
- Use `[INSERT: description]` for any information you don't have — never fabricate details, stats, or examples.
- Save both .md and .epub files.

## EPUB Generation

After the content is written and approved, generate the EPUB file:

1. Save the complete book content as a markdown file (e.g., `lead-magnet-title.md`) in the workspace
2. Run the following Python script to convert it to EPUB:

```python
# Install dependency
import subprocess
subprocess.check_call(["pip", "install", "ebooklib"])

from ebooklib import epub
import re
import uuid

def markdown_to_epub(md_path, output_path):
    with open(md_path, 'r') as f:
        content = f.read()

    # Parse YAML frontmatter
    title, author, subtitle = "Untitled", "Unknown Author", ""
    if content.startswith('---'):
        parts = content.split('---', 2)
        if len(parts) >= 3:
            frontmatter = parts[1]
            content = parts[2].strip()
            for line in frontmatter.strip().split('\n'):
                if line.startswith('title:'):
                    title = line.split(':', 1)[1].strip().strip('"').strip("'")
                elif line.startswith('author:'):
                    author = line.split(':', 1)[1].strip().strip('"').strip("'")
                elif line.startswith('subtitle:'):
                    subtitle = line.split(':', 1)[1].strip().strip('"').strip("'")

    book = epub.EpubBook()
    book.set_identifier(str(uuid.uuid4()))
    book.set_title(title)
    book.set_language('en')
    book.add_author(author)
    if subtitle:
        book.add_metadata('DC', 'description', subtitle)

    css = epub.EpubItem(
        uid="style",
        file_name="style/default.css",
        media_type="text/css",
        content=b"""
body { font-family: Georgia, serif; line-height: 1.6; margin: 2em; color: #1a1a1a; }
h1 { font-size: 2em; margin-top: 2em; margin-bottom: 0.5em; border-bottom: 1px solid #ccc; padding-bottom: 0.3em; }
h2 { font-size: 1.5em; margin-top: 1.5em; }
h3 { font-size: 1.2em; margin-top: 1.2em; }
p { margin-bottom: 1em; }
blockquote { border-left: 3px solid #ccc; padding-left: 1em; margin-left: 0; color: #555; font-style: italic; }
strong { font-weight: bold; }
em { font-style: italic; }
ul, ol { margin-bottom: 1em; padding-left: 2em; }
li { margin-bottom: 0.3em; }
a { color: #1a5276; }
"""
    )
    book.add_item(css)

    chapters = re.split(r'^# ', content, flags=re.MULTILINE)
    epub_chapters = []

    for i, chapter_content in enumerate(chapters):
        if not chapter_content.strip():
            continue
        lines = chapter_content.split('\n', 1)
        ch_title = lines[0].strip()
        ch_body = lines[1].strip() if len(lines) > 1 else ""

        html_body = ch_body
        html_body = re.sub(r'^### (.+)$', r'<h3>\1</h3>', html_body, flags=re.MULTILINE)
        html_body = re.sub(r'^## (.+)$', r'<h2>\1</h2>', html_body, flags=re.MULTILINE)
        html_body = re.sub(r'\*\*(.+?)\*\*', r'<strong>\1</strong>', html_body)
        html_body = re.sub(r'\*(.+?)\*', r'<em>\1</em>', html_body)
        html_body = re.sub(r'\[(.+?)\]\((.+?)\)', r'<a href="\2">\1</a>', html_body)
        paragraphs = html_body.split('\n\n')
        html_body = '\n'.join(f'<p>{p.strip()}</p>' if not p.strip().startswith('<h') and p.strip() else p for p in paragraphs if p.strip())

        ch = epub.EpubHtml(title=ch_title, file_name=f'chapter_{i}.xhtml', lang='en')
        ch.content = f'<html><head><link rel="stylesheet" href="style/default.css"/></head><body><h1>{ch_title}</h1>{html_body}</body></html>'
        ch.add_item(css)
        book.add_item(ch)
        epub_chapters.append(ch)

    book.toc = epub_chapters
    book.add_item(epub.EpubNcx())
    book.add_item(epub.EpubNav())
    book.spine = ['nav'] + epub_chapters

    epub.write_epub(output_path, book)
    return output_path

output = markdown_to_epub('[MARKDOWN_FILE]', '[OUTPUT_FILE].epub')
print(f"EPUB created: {output}")
```

Tell the user where both files are saved.

## What You Don't Do

- Don't write a full-length book — if it's over 6,000 words, it's not a lead magnet
- Don't open with "Thanks for downloading" or any throat-clearing gratitude
- Don't use filler phrases ("it's worth noting," "in today's world," "let's dive in")
- Don't fabricate statistics, case studies, quotes, or examples — use what the user provides or mark with `[INSERT: description]`
- Don't write more than 5 chapters — scope creep kills lead magnets
- Don't make the CTA feel like a sales pitch — it should flow naturally from the content
- Don't skip the action steps at the end of each chapter — these are what make it actionable, not just informational
