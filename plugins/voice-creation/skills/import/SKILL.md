---
name: import
description: Use when the operator already HAS a voice profile — from anywhere — and wants it rebuilt to the Co-Operating System standard, or wants an existing system profile refreshed. Triggers on "import my voice profile", "redo my voice profile in this system", "upgrade my old profile", "rebuild my voice profile", "refresh my voice profile with new samples".
argument-hint: [subject or path to the existing profile]
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Voice — Import an Existing Profile

The operator already has a voice profile — an old skill from another system, a style-guide markdown doc, a "how I write" file, or a profile built by an earlier version of this plugin. This skill rebuilds it to the full Co-Operating System standard: template depth, the bundled AI-tells blocklist with personal exceptions, packaged as an installable plugin. **Nothing evidenced is lost — everything captured in the old profile survives the rebuild.**

Re-running import on a profile this system already built = a refresh: fold in new samples, fix drift, prune stale examples. Same flow, lighter pass.

**Working folder:** the operator's workspace root. **Owned workspace folder:** `workspace/voices/` (shared with `/voice-creation:create`).

## Step 1 — Read the context first

Read the four context profiles (`context/user.md`, `business.md`, `ICP.md`, `tools.md`). Missing or empty → say so, continue with what exists.

## Step 2 — Locate and read the existing profile

Ask where it lives if not given: a file path, a pasted document, an installed skill, anything readable. Common spots to check before asking: `workspace/voices/*/skill/`, `.claude/skills/`, files named `voice*.md` / `*style*.md` in the workspace. Read ALL of it, plus anything alongside it (sample files, notes, update logs).

Identify the **subject** (self / a client / a brand — same kebab-case + naming-convention rules as `/voice-creation:create`, Step 3) and confirm with the operator: "Rebuilding <subject>'s profile to the system standard — right?"

## Step 3 — Inventory what survives

Map the old profile against [the system template](../create/references/voice-profile-template.md) (read it now). Sort everything into three rulings and show the operator what you found:

1. **Keeps** — everything evidenced and voice-true in the old profile: signature patterns, quoted examples, vocabulary lists, quirks, named rules. These move over **verbatim or near-verbatim** — the old profile's captured knowledge is the asset; rebuilding is not rewriting.
2. **Gaps** — template sections the old profile lacks (commonly: AI-tells exceptions, annotated good/bad examples, the update policy/log, voice signals it never captured).
3. **Suspect** — anything in the old profile that contradicts itself, reads generic, or lacks evidence (no quotes behind a claimed pattern). Flag, don't silently delete — the operator rules on each.

## Step 4 — Fill the gaps (lightest possible touch)

- **Derive first.** Most gaps fill from the old profile's own content: its "use" vocabulary and quoted examples often contain everything needed for the exceptions list and good-examples section.
- **Personal AI-tells exceptions — the automatic pass:** cross-reference the old profile's preferred vocabulary and quoted samples against [references/ai-tells.md](../create/references/ai-tells.md) (read it now). Anything the human evidently uses that's ON the blocklist becomes a **personal exception**, each backed by a quote pulled from the old profile. (Example shape: a writer whose samples show purposeful em-dashes or three-item lists gets those as documented exceptions — the list bans the default, never the human.)
- **Ask only for true gaps:** if a template section can't be derived, ask 1–3 targeted questions, or request 1–2 fresh raw samples (pasted verbatim — warn that chat-composed samples contaminate). If the operator has nothing handy, mark the section "to deepen — refresh with samples later" rather than padding.

## Step 5 — Confirm, write, package

Show the operator the rebuild plan — keeps, filled gaps, suspect rulings — and get their confirmation. Then write the complete package — identical structure and standards to `/voice-creation:create` Step 7:

```
workspace/voices/<SUBJECT>/skill/
  .claude-plugin/plugin.json              ← name "voice-<SUBJECT>", version 1.0.0 (or bump if a system profile already exists)
  skills/<SUBJECT>/SKILL.md               ← the rebuilt profile, full template depth
  skills/<SUBJECT>/references/ai-tells.md ← copy of the blocklist, verbatim
```

The rebuilt profile's update log opens with: "vN — imported and rebuilt to system standard from <source description>, <date>." Preserve the old profile's own update history beneath it if it had one. Archive the original source file untouched at `workspace/voices/<SUBJECT>/imported-original.md` — never destroy the input.

## Step 6 — Zip, verify, hand off

Same as `/voice-creation:create` Step 8: stage, zip to `outbox/voice-<SUBJECT>-v<N>.zip`, **verify the zip contains `.claude-plugin/plugin.json`**, tell the operator to install it in the desktop app (replacing the old one if a previous version is installed).

## Step 7 — Test-drive

One short sample (100–200 words) in the rebuilt voice, on a real subject from the operator's world. Their verdict: small fixes → apply + re-zip (max two passes); bigger drift → note in `workspace/voices/<SUBJECT>/notes.md` for the next import refresh, after they've used it on real pieces.

## Guardrails

- **The old profile's evidence is sacred.** Quoted examples and documented patterns transfer; never "improve" a quote, never drop an evidenced pattern without the operator's explicit ruling.
- **No padding.** A template section without material stays marked "to deepen" — a thin-but-honest profile beats an invented one.
- **Never edit the installed copy.** Source → zip → outbox → operator installs. Always.
- One profile per subject: importing onto an existing system profile is a versioned refresh (bump, log), not a duplicate.
