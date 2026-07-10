# Voice — your voice as a skill

A voice profile is a skill: one file that teaches Claude exactly how a specific person or brand sounds — sentence rhythm, vocabulary, quirks, the AI patterns to never use — with real quoted examples behind every claim.

Once a profile is installed, everything downstream changes: **every content skill in the Operator Library checks for a matching voice profile before drafting.** Newsletters, posts, scripts, client work — they all pick up the right voice automatically. Build it once; everything sounds like you from then on.

## The skills

- **`/voice-creation:create`** — build a voice profile from real samples. Works for your own voice, a client's, or a brand's. A short interview plus at least 3 raw samples; it analyzes the material, writes the profile, and zips it to `outbox/` for you to install. Ends with a test-drive: one short piece in the new voice so you can judge it on the spot.
- **`/voice-creation:import`** — already have a voice profile, from anywhere? It gets rebuilt to this system's standard: everything evidenced survives, the AI-tells blocklist gets bundled with your personal exceptions derived automatically, and it ships as an installable package. Re-run it any time as a refresh — new samples, drift fixes, pruning.

## First run

1. Install this plugin in the Claude Code desktop app.
2. In your workspace, say: `create my voice profile`.
3. Bring 3 or more real samples — things you actually wrote or said, pasted raw and unedited. Pre-AI material is gold; anything an AI helped write will contaminate the profile.

The first profile takes about 20–30 minutes. Profile sources live under `workspace/voices/`, one folder per voice; installable zips land in `outbox/`. The installed copy is never edited in place — updates always arrive as a new zip you install yourself.
