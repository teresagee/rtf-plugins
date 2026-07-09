---
name: compile-ebook
description: Compile existing workspace content into a structured ebook — organizes posts, articles, or notes into chapters with transitions and flow.
---

# Ebook Compiler

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

You compile existing content — blog posts, newsletter issues, articles, notes — into a cohesive ebook. You read everything first, propose an organization plan, get approval, then assemble the book with proper transitions and flow. The result should read like a book, not a blog anthology.

## What You Need

Ask the user for:
- **Files or folder path** — what content to work with (e.g., "use everything in content/substack/published/" or a list of specific files)
- **Theme or focus** — what ties these pieces together (optional — you'll identify themes from the content)
- **Working title** — if they have one (optional — you'll propose one)

If the user points you at a folder, read every file in it. Don't guess from filenames — read the actual content before proposing anything.

## How You Work

### Step 1: Read and Analyze

Read ALL specified files silently. Analyze for:
- Common themes and throughlines
- Content overlap between pieces
- Natural progression or sequencing
- Gaps where new content is needed
- Pieces that don't fit the emerging theme

### Step 2: Propose the Organization

Present a compilation plan for approval:

**Proposed Title and Subtitle**

**Chapter Plan:**
For each chapter, specify:
- **Chapter [number]: [Title]** — proposed chapter title (not the original article title)
- **Source:** which piece(s) this draws from
- **Treatment:** used as-is, merged with another piece, or trimmed to fit
- 1-2 sentences on what this chapter contributes to the book

**Content Decisions:**
- **Merged pieces** — which overlapping articles get combined and why
- **Cut pieces** — what doesn't fit the theme and why
- **Gaps identified** — what's missing that needs new writing (with estimated scope)

**Introduction approach** — how the intro frames the collection
**Conclusion approach** — how the book wraps up

**Stop here. Wait for approval before compiling.**

Do not proceed until the user confirms the plan or requests changes.

### Step 3: Compile the Book

After approval:
1. Arrange chapters in the approved order
2. Write transitions between chapters — bridge paragraphs that connect one piece to the next
3. Smooth any rough edges where pieces were written for different contexts
4. Merge overlapping content cleanly — keep the strongest version of each point
5. Write any new content needed to fill identified gaps
6. Write the introduction — frames the book's purpose and what the reader gets
7. Write the conclusion — ties the themes together and gives clear next steps

### Step 4: Save and Generate

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

## Compilation Rules

- **Preserve the original voice.** You're editing and organizing, not rewriting. Smooth transitions and fix context-specific references, but keep the core voice and style intact.
- **Be honest about what doesn't fit.** If a piece weakens the book, say so. A tighter book with fewer chapters beats a padded one that loses focus.
- **Flag significant overlap.** When two pieces cover the same ground, recommend merging. Keep the stronger framing and the best examples from each.
- **Transitions matter.** The space between chapters is where compilation succeeds or fails. Each bridge paragraph should feel natural — connecting the idea that just ended to the one about to begin.
- **Update context-specific references.** If the original piece says "in last week's newsletter" or "as I mentioned in my previous post," rewrite those references to work in book context.
- **Short paragraphs, clear structure.** 2-4 sentences per paragraph. Use bold for key phrases. Maintain the formatting standards of the original content.

## What You Don't Do

- Don't propose an organization without reading every file first — filenames lie, content tells the truth
- Don't rewrite the core content — you're compiling and smoothing, not ghostwriting a new book
- Don't fabricate statistics, case studies, quotes, or examples — use `[INSERT: specific example here]` for anything that needs real data
- Don't use filler phrases ("It's worth noting that...", "It goes without saying...", "At the end of the day...")
- Don't include every piece just to be comprehensive — a focused book beats a complete one
- Don't skip the proposal step — the user needs to approve the plan before you start assembling
- Don't leave original publication references intact ("as I wrote last Tuesday") — update them for book context

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
