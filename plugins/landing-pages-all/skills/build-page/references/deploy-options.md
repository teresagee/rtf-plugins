# Deploy Options — free paths to live

Source material for the personalized `deploy.md`. Pick the path that fits this operator (from `tools.md`: do they have a domain? GitHub? an existing site?), write only that path plus one fallback, and keep it step-by-step at non-developer level. All free tiers described here are current as of mid-2026 — if a screen doesn't match the steps at deploy time, the platform changed; verify against their docs (WebFetch) and update deploy.md, never guess.

## Path 1 — Drag and drop (fastest; no Git, no terminal)

**Netlify Drop** (`app.netlify.com/drop`): drag the folder containing `page.html` (renamed `index.html` — say this explicitly in deploy.md) onto the page; it's live on a `*.netlify.app` URL in seconds. A free account is required to keep the site permanently and to set a custom domain; anonymous drops are temporary. Free tier is generous for a single static page.

Best for: first deploy, validating an offer this week, operators with no domain yet.

## Path 2 — Git-based (best long-term; pairs with the workspace git habit)

**Cloudflare Pages** or **GitHub Pages** — both free for static pages, both deploy automatically when the file changes in a GitHub repo.

- **GitHub Pages:** a repo with `index.html` at the root → Settings → Pages → deploy from branch. Live at `username.github.io/repo-name`. Free, including custom domains.
- **Cloudflare Pages:** connect the GitHub repo at `pages.cloudflare.com`; free tier covers far more than one page needs; strong custom-domain and HTTPS handling.

Best for: operators already comfortable letting Claude manage a repo. Note honestly: this puts the page's repo on GitHub (public or private) — a separate small repo for the page, never the operator's whole workspace.

## Path 3 — Onto an existing site

- **Existing static host / web hosting:** upload `page.html` as a new path (e.g. `/course/index.html` → `site.com/course`). Steps depend on their host — name it from `tools.md` and write the actual steps for that host.
- **Site builders (Squarespace/Wix/Framer/WordPress):** these mostly can't ingest a raw HTML file cleanly. Two honest options: host the page on Path 1/2 under a subdomain (`go.theirdomain.com` — a DNS CNAME, give the registrar-level steps), or transplant the *copy* into their builder's blocks manually. Don't pretend the HTML pastes in.

## Custom domain (any path)

A custom domain is bought (~$10–15/yr — the one cost in this whole flow), then pointed at the host: each host's dashboard has an "add custom domain" flow that states the exact DNS records. Subdomains of a domain the operator already owns are free and usually the right move (`course.theirdomain.com`). HTTPS is automatic on all hosts above.

## After it's live — the checklist for deploy.md

1. Replace every `REPLACE-ME` (form ID/URL) — include the dashboard path for their platform.
2. Drop real images into the labeled slots; re-upload.
3. Submit the form once with a real email — confirm it lands in their email platform.
4. Open the live URL on a phone.
5. Optional: add their analytics snippet if they use one.

And the standing rule, stated in deploy.md too: the operator clicks deploy. Claude prepares everything up to that click.
