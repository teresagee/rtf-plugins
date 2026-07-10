---
name: create
description: Use when the operator wants to capture a voice as a reusable skill — their own, a client's, or a brand's. Triggers on "create my voice profile", "capture my voice", "build a voice profile for {name}", "make Claude sound like me", or when a content skill reports that no matching voice profile exists for the work at hand.
argument-hint: "[subject — e.g. self, or a client/brand name]"
allowed-tools: Read, Write, Edit, Bash, Glob, Grep, TodoWrite, WebFetch
---

# Voice Creation

Build a voice profile skill from real samples: gather raw material, interview the operator, analyze the voice, write the profile as skill source under `workspace/voices/`, zip it to `outbox/` for the operator to install, then test-drive it.

**Working folder:** the operator's workspace root is the current directory. All paths relative to it. Never change directories permanently.

**Owned workspace folder:** `workspace/voices/` — one subfolder per voice subject (`workspace/voices/<subject>/`), holding `samples/` (the raw material), `skill/` (the profile source), and `notes.md` (test-drive verdicts and refinement notes). Shared home with `/voice-creation:import`. Create folders idempotently with `mkdir -p`.

## Step 1 — Read the context first

Before anything else, read the four context profiles:

1. `context/user.md`
2. `context/business.md`
3. `context/ICP.md`
4. `context/tools.md`

Use them throughout: the operator's name and origin story (for a `self` profile's subject identification), their formats and channels (what the profile must cover), their audience (who the voice talks to), and their naming conventions for clients.

If a profile is missing or empty, say which one and continue with what exists. Never stop, never silently invent what's missing.

## Step 2 — Announce and identify the subject

Briefly tell the operator what's being built — a voice profile skill that teaches every future session how this voice sounds — then ask whose voice it is: their own (pulled from their real material), a client's (a specific person they produce content for, pulled from that person's published and spoken material), or a brand's (a company or publication voice, theirs or a client's, rather than one person's).

Set `VOICE\\\_TYPE` to `self`, `client`, or `brand`. Track progress with `TodoWrite` (one todo per major step) so the operator sees where they are and the wizard recovers if interrupted.

## Step 3 — Name the subject

The subject name becomes the folder under `workspace/voices/<subject>/` and the name on the installable skill. Always kebab-case.

* **Self:** default `self`. Confirm; the operator can override (e.g. their first name).
* **Client:** match the operator's existing naming. If `context/<client-name>/` exists, use that exact name. **Check the naming convention:** if `context/clients.md` exists, the operator chose codenames — use the codename and keep the real name out of every file, filename, and zip this skill produces. If real names are their convention, the client's real name in kebab-case is fine.
* **Brand:** the brand name in kebab-case. If it's a client's brand and the codename convention is on, codename it.

Set `SUBJECT`. Then check for an existing profile: if `workspace/voices/<SUBJECT>/skill/skills/<SUBJECT>/SKILL.md` already exists, say so and offer two paths — rebuild it to the current standard with `/voice-creation:import` (the usual answer — keeps everything evidenced), or rebuild from scratch (only on explicit confirmation; the old profile gets overwritten).

## Step 4 — Gather the samples

Ask for source material. Full guide, including what works best per subject type: [references/sample-guide.md](references/sample-guide.md).

**Give the contamination warning before collecting anything — verbatim in spirit:**

> One rule about samples: they have to be raw. Things you (or the client) actually wrote or said, pasted as-is — not cleaned up, not improved, and especially not anything an AI helped write. Text composed in a chat with Claude or any other AI is contaminated: it teaches the profile to sound like an AI's idea of you, and that gets baked in permanently. Pre-AI material is gold.

If a sample's origin is unclear, ask when and how it was written before accepting it.

Accept samples as:

* **Pasted text** — the default and the most reliable.
* **File paths** — files already in the workspace. Don't copy them; record their paths.
* **Public URLs** — for client/brand published material, fetch with WebFetch. If a fetch fails (paywall, script-heavy site), ask the operator to paste the text instead.

**Minimum bar: 3 substantial samples (over 200 words each).** Sweet spot is 5–8 across varied formats. If the operator has fewer than 3:

* Push gently once — even one more real piece sharpens the profile a lot.
* If they genuinely don't have more, proceed, but mark the profile **low-confidence** in its `source-material-summary` (e.g. "2 samples — low-confidence profile; refresh via /voice-creation:import when more material exists").

**Save what was gathered.** Write each pasted or fetched sample to `workspace/voices/<SUBJECT>/samples/YYYY-MM-DD-<slug>.md` with a short frontmatter block (`source:` type, `origin:` pasted/url/file, `gathered:` date). Samples already living elsewhere in the workspace are recorded by path in the profile's source summary, not copied.

## Step 5 — Voice interview

A short interview to capture intent the samples can't show. Use the question set matching `VOICE\\\_TYPE` in [references/interview-prompts.md](references/interview-prompts.md). 4–6 questions, paraphrased, conversational. Skip what doesn't fit; probe thin answers once.

## Step 6 — Analyze

Read every sample in full. Extract patterns across all dimensions in [references/analysis-heuristics.md](references/analysis-heuristics.md) — sentence rhythm, paragraph structure, vocabulary, openings/closings, transitions, voice signals, AI tells, tone, quirks. Trust that file for the method; don't duplicate its dimension list here.

Hard rules:

* **Confidence rule:** a pattern must appear in at least 2 samples to count as signature. Single-sample patterns are coincidence, not voice.
* **Anti-fabrication rule:** every quoted example in the profile must be copied verbatim from the samples on disk — never composed, paraphrased, or "reconstructed." If no real quote exists for a pattern, the pattern doesn't go in.
* **Weighting:** the subject's own material always outweighs anything labeled as reference or inspiration.

## Step 7 — Confirm, then write the profile

Show the operator what the analysis found — the strongest patterns, the vocabulary, the quirks, evidenced with real quotes — and ask whether it reads like the voice. Nothing gets written until they confirm.

Once confirmed, write the profile as a complete installable package under `workspace/voices/<SUBJECT>/skill/`:

```
workspace/voices/<SUBJECT>/skill/
  .claude-plugin/plugin.json              ← {"name": "voice-<SUBJECT>", "version": "1.0.0", "description": "<Subject>'s voice profile — invoked by content skills when writing in this voice.", "author": {"name": "<operator's name from context/user.md>"}}
  skills/<SUBJECT>/SKILL.md               ← the profile itself
  skills/<SUBJECT>/references/ai-tells.md ← COPY this plugin's references/ai-tells.md in, verbatim
```

The profile (`SKILL.md`) follows [references/voice-profile-template.md](references/voice-profile-template.md). Match the template's depth — quoted examples under every pattern, a vocabulary table, named quirks, AI tells with the exception rule, annotated good/bad examples, an update policy, an update log. A thin profile produces generic output; depth is the whole product. The profile's AI-tells section cites its bundled `references/ai-tells.md` as the standing blocklist and records THIS voice's **personal exceptions** — items on the list this human genuinely uses (each backed by a quote from the samples), which stay allowed for this voice.

Also create `workspace/voices/<SUBJECT>/notes.md` with a one-line header ("Refinement notes for /voice-creation:import") if it doesn't exist.

## Step 8 — Zip to outbox

Package the profile for installation. Run from the workspace root:

```
Bash rm -rf outbox/.voice-stage \\\&\\\& mkdir -p outbox/.voice-stage/voice-<SUBJECT> \\\&\\\& cp -R workspace/voices/<SUBJECT>/skill/. outbox/.voice-stage/voice-<SUBJECT>/ \\\&\\\& (cd outbox/.voice-stage \\\&\\\& zip -rq ../voice-<SUBJECT>-v1.zip voice-<SUBJECT> -x "\\\*.DS\\\_Store") \\\&\\\& rm -rf outbox/.voice-stage
```

Verify before reporting: the zip exists AND carries the manifest — `Bash unzip -l outbox/voice-<SUBJECT>-v1.zip | grep ".claude-plugin/plugin.json"` must match (without the manifest the desktop app cannot install it). Then point the operator at the zip — they install it themselves in the Claude Code desktop app, and once it's in, every content skill in their library finds it automatically.

## Step 9 — Test-drive

After they've installed it (or while they do — read the source at `workspace/voices/<SUBJECT>/skill/skills/<SUBJECT>/SKILL.md` directly for this step), produce **one short sample (100–200 words) in the new voice**, on a subject from the operator's actual world:

* **Self:** a hook or opening for their next piece, aimed at their actual audience (from `context/ICP.md`).
* **Client:** a short post or email opening on something the client actually covers.
* **Brand:** a paragraph in the brand voice on one of its real topics.

Use only facts from the context profiles in the sample — if you need a fact you don't have, write around it. Never invent numbers, names, or claims.

Show it and get a verdict — push for specifics, because specific complaints are fixable right now and vague ones aren't:

* **Small, specific fixes** (a word to ban, a pattern to soften): apply them to the source profile now, re-run the zip command (same filename, overwrite), and tell the operator to install the fresh zip instead. At most two quick passes.
* **Bigger or vaguer complaints** ("close but not quite"): append them to `workspace/voices/<SUBJECT>/notes.md` with today's date and tell the operator that's exactly what an `/voice-creation:import` refresh is for — usually after they've used the voice on a few real pieces and can point at real output.

## Step 10 — Close out

Share where everything lives (source under `workspace/voices/<SUBJECT>/`, zip in `outbox/`) and make the maintenance path clear: `/voice-creation:import <SUBJECT>` is the refresh pass for drift, new samples, new formats, or pruning. Don't chain into other skills or prompt next actions.

## Guardrails

* **Raw samples only.** AI-assisted text is contaminated — warn before collecting, and ask about origin when unsure.
* **Real quotes only.** Every example in the profile is copy-pasted from the samples. No real quote, no pattern.
* **Confirm before writing.** Show the analysis summary and get a yes before the profile file is written.
* **Preserve quirks.** Don't sanitize quirks into generic patterns — quirks are what make a voice recognizable.
* **Respect the naming convention.** If the operator uses codenames for clients, real names never appear in this skill's files, filenames, or zips.
* **Never edit the installed copy.** The source under `workspace/voices/` is the only thing this skill touches. Updates reach the installed skill exclusively as a new zip the operator installs — never by writing into Claude Code's plugin directories.
* **Never auto-publish, never install on the operator's behalf.** The operator installs every zip themselves.

