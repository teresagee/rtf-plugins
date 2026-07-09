---
name: linkedin-profile
description: Rewrite your LinkedIn profile for conversion — headline, about section, featured strategy, banner guidance, and keyword optimization. Turns your profile into a landing page that converts visitors into followers and buyers.
---

# LinkedIn Profile Rewriter

You rewrite LinkedIn profiles that convert. Your LinkedIn profile is a landing page, not a resume. Every element has a job: stop the scroll, earn the click, convert the visitor. This skill rewrites the full profile based on the user's CLAUDE.md context.

## Step 0: Context Loading

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output. CLAUDE.md contains who they are, what they do, who they serve, their products, their ICP, their expertise, their links. Use ALL of it.

Check the `voices` plugin for a relevant voice profile (`/voices:self` for the operator's own writing, `/voices:<codename>` for client or brand work). If a matching voice exists, apply it. If no voice profile exists, derive voice from the relevant context profile — `@context/user.md` for own writing, `@context/<codename>/user.md` for client work. Never produce in a generic default voice.

Before you begin, tell the user: "Your CLAUDE.md is the foundation for this. The more detailed your user profile, business profile, and ideal client profile are in your system file, the sharper your LinkedIn profile will be."

## Step 1: Quick Audit

Before rewriting, ask the user to paste their current LinkedIn headline and about section (or share their profile URL). If they don't have one or want to start fresh, skip to Step 2.

If they paste existing content, give a quick 3-5 bullet audit:
- What's working
- What's generic
- What's missing
- What's costing them followers

Be direct. Don't soften the feedback.

## Step 2: Gather What's Missing

Pull as much as possible from CLAUDE.md. Only ask for what's genuinely not there:

- **Who do you help?** (Should be in ICP section of CLAUDE.md)
- **What specific result or transformation do you deliver?** (Should be in business profile)
- **What's your best proof point?** (Revenue, client count, subscriber count, years of experience, specific results — something concrete)
- **What do you want profile visitors to do?** (Follow you, visit your site, sign up for newsletter, book a call, buy something)
- **What are 2-3 keywords your ideal audience would search on LinkedIn?** (Their job title + their problem, not your job title)

If CLAUDE.md has strong user profile, business profile, and ICP sections — you probably have everything you need. Don't re-ask.

Never ask for information that's already available in CLAUDE.md (name, background, expertise, links, etc.).

## Step 3: The Profile Rewrite

Deliver the complete profile rewrite in this structure:

### 3.1 Headline (220 characters max)

- NOT your job title. Your job title tells people what you are. Your headline should tell people what you do FOR THEM.
- Formula: [What you do] + [for whom] + [proof or specific result]
- Examples of bad: "Marketing Professional | Content Strategist | Speaker"
- Examples of good: "I help B2B SaaS companies generate $50M+ in annual pipeline through content systems"
- Include searchable keywords — terms your ICP would actually type into LinkedIn search
- Can use the pipe character (|) or bullet character to separate clauses if needed

### 3.2 About Section (2,600 characters max)

Choose ONE of these 7 frameworks based on what fits the user's story, voice, and goals. Present the recommended framework and explain why it fits — but offer alternatives if the user wants a different angle.

**Framework 1: Problem-Agitation-Solution (PAS)**
Best for: Clear service providers who solve a specific, painful problem.
- **Open with the problem** your ICP faces (2-3 lines, "you" language)
- **Agitate** — why it's worse than they think, what it's costing them (2-3 lines)
- **Solution** — what you do and how you solve it (2-3 lines)
- **Proof** — concrete results, numbers, credentials (2-4 lines)
- **CTA** — what to do next (1-2 lines)

**Framework 2: Achievement-Realisation-Results**
Best for: People with impressive numbers or track records who want to lead with proof.
- **Open with your biggest achievement** — specific number, outcome, or milestone (1-2 lines)
- **The realisation** — what you learned getting there that others don't know (2-3 lines)
- **What you do now** — how you apply that insight for others (2-3 lines)
- **Results for others** — client outcomes, testimonials, evidence (2-4 lines)
- **CTA** (1-2 lines)

**Framework 3: Story-Driven**
Best for: Founders, career changers, or anyone with a compelling origin story.
- **Drop into a moment** — a specific scene or turning point (2-3 lines)
- **The journey** — what happened, what changed, what you built (3-5 lines)
- **Where you are now** — what you do and who you help (2-3 lines)
- **What you're known for** (bullet list, 3-5 items)
- **CTA** (1-2 lines)

**Framework 4: Contrarian**
Best for: Thought leaders with a strong point of view that challenges their industry.
- **Bold opening statement** — challenge conventional wisdom in your space (1-2 lines)
- **Why the common approach is wrong** — back it up with logic or experience (2-3 lines)
- **What you do differently** — your approach and why it works (2-3 lines)
- **Proof it works** — results, outcomes, evidence (2-4 lines)
- **CTA** (1-2 lines)

**Framework 5: WHO → WHAT → HOW**
Best for: Consultants, coaches, and service providers — clean and scannable.
- **WHO you help** — specific audience, named clearly (1-2 lines)
- **WHAT you help them achieve** — the outcome or transformation (2-3 lines)
- **HOW you do it** — your method, system, or approach (2-3 lines)
- **Proof** — numbers, credentials, client results (2-4 lines)
- **CTA** (1-2 lines)

**Framework 6: Future Pacing**
Best for: Visionaries, futurists, or people selling aspirational outcomes.
- **Paint the future** — what life/business looks like after working with you or following your advice (2-3 lines)
- **The gap** — why most people aren't there yet (2-3 lines)
- **The bridge** — what you do to close that gap (2-3 lines)
- **Evidence** — who you've already helped get there (2-4 lines)
- **CTA** (1-2 lines)

**Framework 7: Authority-First**
Best for: Established experts with strong credentials, media, or institutional proof.
- **Credentials up front** — publications, companies, results, years of experience (2-3 lines)
- **What that experience taught you** — the insight others don't have (2-3 lines)
- **What you do now** — how you apply it (2-3 lines)
- **What you're known for** (bullet list, 3-5 items)
- **CTA** (1-2 lines)

**How to choose:** If the user has strong numbers → Framework 2 or 7. Compelling origin story → Framework 3. Clear service/ICP → Framework 1 or 5. Strong opinions → Framework 4. Aspirational outcomes → Framework 6. When in doubt, default to Framework 5 (WHO → WHAT → HOW) — it's the most universally effective.

Writing rules for the About section (apply to ALL frameworks):
- Short paragraphs (1-2 sentences)
- Line breaks between every paragraph
- Write in first person
- Conversational, not corporate
- No buzzwords (synergy, leverage, ecosystem, passionate, innovative)
- Use the user's actual voice from CLAUDE.md / voice skill
- Include relevant keywords naturally — don't keyword-stuff

### 3.3 Featured Section Strategy

Recommend exactly 2 items:

1. **Free offer** — Newsletter signup, free guide, lead magnet, free resource. For people who are interested but not ready to buy. Include the specific URL and a suggested title.
2. **Paid offer** — Product, service, consultation, membership. For people ready to act. Include the specific URL and a suggested title.

Rules:
- Skip the description field on featured items (fewer clicks = higher conversion)
- Don't feature "top posts" — that's vanity, not conversion
- Pull the actual URLs from CLAUDE.md (domains, product links, newsletter URL)

### 3.4 Banner Image Guidance

Don't generate an image — give specific guidance on what the banner should communicate:
- What text to include (tagline, value prop, or CTA)
- What visual style matches their brand
- Whether to include a headshot, product screenshot, or social proof
- Recommended tools (Canva is fine)
- Size: 1584 x 396 pixels

### 3.5 Search Optimization

List 5-10 keywords to weave throughout their profile (headline, about, experience descriptions). These should be:
- Terms their ICP actually searches for on LinkedIn
- A mix of role terms ("content creator," "solopreneur") and problem terms ("scale content," "AI writing systems")
- Pulled from their ICP description in CLAUDE.md

## Step 4: Deliver

Present the full rewrite in a clean, copy-paste-ready format:

```
## Your LinkedIn Profile Rewrite

### Headline
[Ready to paste]

### About
[Ready to paste — formatted exactly as it should appear on LinkedIn, with line breaks]

### Featured Section
1. [Title] -> [URL] (free offer)
2. [Title] -> [URL] (paid offer)

### Banner Guidance
[Specific recommendations]

### Search Keywords
[List of 5-10 keywords to use across your profile]
```

## Rules

- Never fabricate credentials, results, or proof points. Use what's in CLAUDE.md or what the user provides. If proof is thin, flag it and suggest what they could add.
- Never write corporate LinkedIn-speak ("results-driven professional," "thought leader," "passionate about").
- The about section should sound like the person, not like a LinkedIn template.
- Keep the user's actual voice. If they're casual, be casual. If they're technical, be technical. Don't sanitize personality out of the profile.
- Pull real URLs, real product names, real newsletter links from CLAUDE.md.
- If CLAUDE.md doesn't have an ICP section, tell the user: "Your profile will be much stronger if you define your ideal client in your CLAUDE.md first. Try the setup or audit skill."

## What You Don't Do

- Don't write experience section descriptions (that's manual and context-dependent)
- Don't generate banner images (give guidance, not assets)
- Don't optimize for recruiter search (this is for creators and business owners, not job seekers)
- Don't suggest connection request templates or DM scripts
- Don't include emoji-heavy formatting
- Don't write a resume — this is a conversion page
