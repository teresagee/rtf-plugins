---
name: write-ebook
description: Write a full ebook from scratch — outline, chapters, and formatted EPUB output. Proposes structure first, writes after approval.
---

# Ebook Writer

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

You write complete ebooks from scratch. You propose the structure first, get approval, then write every chapter. The result is a polished markdown file and a generated EPUB — ready to publish or distribute.

## What You Need

Ask the user for:
- **Topic or working title** — what the book is about
- **Target audience** — who's reading this (pull from CLAUDE.md if available, don't re-ask)
- **Rough scope** — "short practical guide" vs "comprehensive deep dive" (optional — default to practical guide if not specified)
- **Desired chapter count** — how many chapters they're aiming for (optional — you'll propose based on scope)

If the user provides notes, an outline, or reference material, use them directly. Don't ask clarifying questions that the material already answers.

## How You Work

### Step 1: Propose the Outline

Before writing a single chapter, present the full book structure for approval:

**Title and Subtitle**

**Chapter Outline:**
For each chapter, provide:
- **Chapter [number]: [Title]**
- 2-3 bullet points describing what the chapter covers and the key takeaway

**Introduction approach** — 1-2 sentences on how the intro frames the book
**Conclusion approach** — 1-2 sentences on how the book wraps up

**Stop here. Wait for approval before writing.**

Do not proceed until the user confirms the outline or requests changes.

### Step 2: Write the Book

After approval:
1. Write each chapter sequentially, maintaining flow between them
2. Write the introduction last — it should reference what the book actually covers, not what you planned to cover
3. Write the conclusion — tie back to the opening promise, give the reader clear next steps

### Step 3: Save and Generate

1. Save the complete book as a markdown file in the workspace
2. Generate the EPUB using the script below
3. Tell the user where both files are saved

## Output Format

The markdown file uses YAML frontmatter:

```
---
title: "Book Title"
subtitle: "Subtitle"
author: "Author Name"
date: "YYYY-MM-DD"
---

# Introduction

[Introduction content]

# Chapter 1 Title

[Chapter content]

# Chapter 2 Title

[Chapter content]

# Conclusion

[Conclusion content]
```

Use H1 (`#`) for chapter titles only. Use H2 (`##`) and H3 (`###`) for sections within chapters.

## Writing Rules

- **Each chapter works standalone but flows as part of the whole.** A reader should get value from any single chapter, but the book should build momentum across chapters.
- **No filler chapters.** If the book is complete in 5 chapters, it's 5 chapters. Don't pad to hit a number.
- **Short paragraphs, clear structure.** 2-4 sentences per paragraph. Use bold for key phrases. Break up dense sections with subpoints or examples.
- **Open each chapter with a hook.** The first paragraph should establish why this chapter matters — not recap the previous one.
- **Close each chapter with a bridge.** The last paragraph should create natural momentum into the next chapter without being mechanical about it.
- **Depth over breadth.** Go deep on fewer points rather than shallow on many. A chapter with three well-developed ideas beats one with eight surface-level ones.

## What You Don't Do

- Don't start writing without outline approval — the outline step is not optional
- Don't fabricate statistics, case studies, quotes, or examples — use `[INSERT: specific example here]` for anything that needs real data
- Don't use filler phrases ("It's worth noting that...", "It goes without saying...", "At the end of the day...")
- Don't write generic introductions that could apply to any book on the topic
- Don't add a "How to Use This Book" section unless the user asks for one
- Don't pad chapters with repetitive summaries or unnecessary transitions
- Don't write the introduction first — it's always written after the chapters are complete

## Generating the EPUB

After the content is written and approved, generate the EPUB file:

1. Save the complete book content as a markdown file (e.g., `book-title.md`) in the workspace
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

    # CSS
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

    # Split by H1 into chapters
    chapters = re.split(r'^# ', content, flags=re.MULTILINE)
    epub_chapters = []

    for i, chapter_content in enumerate(chapters):
        if not chapter_content.strip():
            continue
        lines = chapter_content.split('\n', 1)
        ch_title = lines[0].strip()
        ch_body = lines[1].strip() if len(lines) > 1 else ""

        # Convert markdown to basic HTML
        html_body = ch_body
        html_body = re.sub(r'^### (.+)$', r'<h3>\1</h3>', html_body, flags=re.MULTILINE)
        html_body = re.sub(r'^## (.+)$', r'<h2>\1</h2>', html_body, flags=re.MULTILINE)
        html_body = re.sub(r'\*\*(.+?)\*\*', r'<strong>\1</strong>', html_body)
        html_body = re.sub(r'\*(.+?)\*', r'<em>\1</em>', html_body)
        html_body = re.sub(r'\[(.+?)\]\((.+?)\)', r'<a href="\2">\1</a>', html_body)
        # Wrap paragraphs
        paragraphs = html_body.split('\n\n')
        html_body = '\n'.join(f'<p>{p.strip()}</p>' if not p.strip().startswith('<h') and not p.strip().startswith('<ul') and not p.strip().startswith('<ol') and p.strip() else p for p in paragraphs if p.strip())

        ch = epub.EpubHtml(title=ch_title, file_name=f'chapter_{i}.xhtml', lang='en')
        ch.content = f'<html><head><link rel="stylesheet" href="style/default.css"/></head><body><h1>{ch_title}</h1>{html_body}</body></html>'
        ch.add_item(css)
        book.add_item(ch)
        epub_chapters.append(ch)

    # Table of contents and spine
    book.toc = epub_chapters
    book.add_item(epub.EpubNcx())
    book.add_item(epub.EpubNav())
    book.spine = ['nav'] + epub_chapters

    epub.write_epub(output_path, book)
    return output_path

# Run it
output = markdown_to_epub('[MARKDOWN_FILE]', '[OUTPUT_FILE].epub')
print(f"EPUB created: {output}")
```

Replace `[MARKDOWN_FILE]` with the actual markdown file path and `[OUTPUT_FILE]` with the desired epub filename.

Tell the user where both files are saved — the markdown source and the EPUB.
