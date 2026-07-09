# Build Standards — the single-file page

What `page.html` is made of. The goal is a page that loads instantly, reads as one person's real offer, and survives unchanged for years.

## File shape

- One HTML file. CSS embedded in a single `<style>` block using CSS custom properties (`--accent`, `--text`, `--bg`, `--max-width`) so the operator can re-skin by editing four lines.
- No JavaScript by default. The page is copy, proof, and a form — none of that needs JS. (Exception: a platform's form embed sometimes requires its own snippet; use the platform's HTML-form variant when one exists, the script variant only when it doesn't.)
- No CDN links, no icon fonts, no analytics by default. If the operator wants analytics, add their platform's snippet at the end and note it in deploy.md — never add tracking they didn't ask for.

## Layout system

- **Mobile first.** Base styles target ~375px; one `@media (min-width: 720px)` tier covers desktop. Mobile converts worse than desktop across every published benchmark — don't make it worse by designing desktop-down.
- Single column, generous whitespace, content max-width ~42rem for prose sections (line lengths over ~75 characters hurt reading).
- Section rhythm: alternate background tints (e.g. `--bg` and a 3–4% shade) to delimit sections instead of borders and dividers.
- The hero fits a phone screen with headline, subhead, and CTA visible — the fold's only job is earning the scroll, so the scroll cue (start of the next section) should peek.

## Type

- Default: the system font stack — `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif`. Zero load time, never flashes, looks native everywhere.
- If the operator has one brand webfont, load that one (and only that one) with `font-display: swap`, headings only — body stays system.
- Scale: one `h1` (clamp ~2–3rem), restrained heading steps, 1.6 line-height body, 16–18px base.

## Anti-slop design guardrails

Visitors now pattern-match "AI template page" and discount it on sight. The documented tells to avoid:

- **The stock-gradient hero** — purple-to-blue gradient backgrounds are the recognized default; use the operator's accent on a quiet background instead.
- **The identical layout** — hero / three feature cards / testimonial wall / pricing, every section centered, every card identical. Vary section layouts; let proof sit beside claims (the copy's claim-proof adjacency should be visible in the layout, not collected into a wall).
- **Default-font sameness** — the reason the system stack is safe is that it reads native, not branded-generic; if they have a brand font, use it in headings.
- **Fake-human imagery** — no stock smiling teams, no generated faces. Real photos or labeled placeholder slots, nothing else.
- The positive version: a real face, a real product shot, one accent color used with restraint, and copy doing the work. Plain and personal beats glossy and generic on operator pages.

## Image slots

Until the operator supplies real images, each slot is an obviously-unfinished labeled block:

```html
<div class="img-slot" style="aspect-ratio: 1/1">
  <!-- REPLACE: your headshot — square, at least 800×800px -->
  <p>YOUR HEADSHOT HERE</p>
</div>
```

Every `<img>` that does exist gets real alt text (what the image shows, plainly), `loading="lazy"` below the fold, and explicit `width`/`height` or `aspect-ratio` so the page never jumps while loading.

## Form embed patterns

The form posts to the operator's existing email platform. Pattern by platform (from `tools.md`); in every case the operator's real form ID/URL is a clearly marked `REPLACE-ME` value, and `deploy.md` says exactly where in their dashboard to find it. These shapes are current as of mid-2026 — if a platform's docs disagree at build time, the docs win (check with WebFetch when in doubt).

- **Kit (ConvertKit):** plain HTML form posting to `https://app.kit.com/forms/REPLACE-FORM-ID/subscriptions` with an `email_address` field — the form's ID comes from their Forms dashboard. Kit also offers a JS embed; prefer the HTML form.
- **Substack:** no on-page form API for arbitrary sites — link the CTA button to the publication's subscribe URL (`https://REPLACE-PUBLICATION.substack.com/subscribe`), or use Substack's iframe embed (`/embed`) where a true inline form matters.
- **Mailchimp:** their "embedded form" HTML (Audience → Signup forms) pasted in and restyled to the page's CSS — keep their `action` URL and field names exactly.
- **Buttondown:** plain HTML form posting to `https://buttondown.com/api/emails/embed-subscribe/REPLACE-USERNAME`.
- **MailerLite / Beehiiv / others:** use the platform's documented HTML embed, restyled; if only a script embed exists, isolate it in its own section and note it as the page's one external dependency.
- **No platform yet:** visibly-unwired form + a note in deploy.md that picking an email platform comes before deploying a page that collects emails.

Always include a `success` note: where the subscriber lands after submitting (platform default page, or a `?subscribed=true` message section) — set per the platform's mechanism, stated in deploy.md.

## Head section

- `<title>`: the offer, plainly — "Offer Name — what it is, for whom", not a slogan.
- `<meta name="description">`: 1–2 sentences from the hero's claim, written for a human deciding whether to click. Shown to the operator before final.
- `<meta name="viewport" content="width=device-width, initial-scale=1">` always.
- Open Graph basics (`og:title`, `og:description`, `og:image` pointing at a real image slot) so shared links unfurl properly.
- FAQ stays in the visible page as real text — that, plus the plain entity statement in the hero, is the AEO foundation. Optional extra: FAQPage JSON-LD mirroring the visible FAQ verbatim (never content that isn't on the page).
