# Deep mode — parallel fan-out, honestly priced

Deep mode splits the question into independent angles and researches them in parallel, then verifies and merges the results in the main session. It exists because long single-session research has measured failure modes — incomplete coverage, favoring early findings, losing constraints over a long context — and because parallel agents demonstrably outperform a single session on multi-angle questions (Anthropic's own evals showed a large win for multi-agent research). It also costs real money. Both facts go to the operator before anything fans out.

## When deep mode earns its cost — and when it doesn't

**Earns it:** 3+ genuinely independent angles (different markets, different vendors, different sub-questions that don't feed each other); contested or high-stakes decisions where independent passes reduce one-sidedness; breadth that would blow a single session's context.

**Doesn't:** a single question, anything a standard run answers in 20 minutes, vague goals (fan-out multiplies a bad brief — sharpen the brief first), or anything needing the operator's judgment mid-stream (parallel agents can't ask questions; checkpoints happen between stages, in the main session).

The working rule from the better practitioners: a single round of parallel, independent lookups → subagents are enough; only multi-stage pipelines where stage N's output shapes stage N+1 justify heavier machinery.

## The cost warning (give it before fanning out, every time)

Say, in substance:

> Deep mode runs several research agents in parallel. Multi-agent work costs up to ~15x the tokens of a normal chat (Anthropic's own figure), and your usage is one shared pool across Claude Code and claude.ai — a big run today taxes everything else this week. There are public reports of large fan-outs eating a 5-hour plan window in under half an hour. I'll use [N] agents with capped budgets. Want the parallel run, or the cheaper sequential version?

Never escalate agent count beyond what was agreed. If the operator hesitates, default to sequential.

## Option A — subagent fan-out (the standard deep run)

Use the agent/subagent facility (the Agent tool — called the Task tool in pre-2026 material) to spawn **3–5 parallel researchers, one per angle from the brief.** State the number explicitly — "research these four angles in parallel using separate subagents" — parallelism doesn't happen by default. Anthropic's effort-scaling guidance applies: simple comparison = 2–4 agents at 10–15 tool calls each; don't exceed 5 angles without re-confirming cost with the operator.

**Each delegation is the agent's entire world — brief it like that.** Every spawn includes, explicitly:

1. **Objective** — the one angle, as a sharp question. No overlap with sibling agents; name what's out of scope ("vendor pricing only — another agent has integrations").
2. **Output format** — exactly the read-time capture from the main skill: per source kept → URL, publisher, author, date, source-type tag; per claim → the claim + a short verbatim quote from the fetched page + claim markers where they apply; then a "could not verify" list. **A findings summary, never a transcript** — verbose returns defeat the point of fan-out.
3. **Source guidance** — the source hierarchy and anti-content-farm rules from `verification-rules.md`, condensed into the prompt (subagents don't inherit this file; paste the rules, don't reference them). Broad-to-narrow searching. Never construct URLs; never cite an unread page.
4. **Budget and stopping criteria** — ~10–15 tool calls; stop when the last two searches add nothing new; report "thin coverage" rather than dredging aggregators to fill space.

Vague delegations produce duplicated work and unusable returns — most fan-out failures are briefing failures, not execution failures.

**Cost trims:** read-only research agents can run on a smaller/cheaper model where the harness allows choosing one — say so in the spawn. Keep all file writes in the main session (background agents can silently fail permission prompts; agents return findings, the main session writes).

## Option B — the bundled `/deep-research` workflow (if available)

Claude Code's dynamic workflows (research preview, v2.1.154+, paid plans — Pro enables it under Dynamic workflows in `/config`) ship a `/deep-research` command: fan-out searches → fetch sources → extract claims → adversarial cross-check where claims refuted by multiple checkers get filtered → cited report. That claim-vote-filter structure does part of this skill's verification mechanically, at scale, in the background (`/workflows` to watch; runs can be stopped without losing finished agents' work).

If the operator's setup has it and the question suits it, offer it as an alternative to Option A — same cost warning. Two honest caveats: it's a research preview and behaves like one, and its output still gets **this skill's treatment afterward** (see "After the fan-out"). If `/deep-research` isn't available on their version or plan, say so plainly and use Option A — never pretend to have run a workflow.

Writing custom workflows is beyond this skill's scope; the official Claude Code docs cover it.

## Option C — the sequential fallback (always available, always offered)

Same angles, same briefs, same budgets — run one at a time in the main session. After each angle, compress findings to the capture format before starting the next, so context stays manageable. Slower by wall-clock, far cheaper in tokens, identical discipline. This is the right answer on a Pro plan, near a usage cap, or whenever the operator says "cheap." A deep question answered sequentially is still a deep answer.

## After the fan-out (non-negotiable, all options)

Merged findings are raw material, not a report. **"AI verifying AI is still AI"** — the main session runs the full discipline on the merged set:

- **Re-verify the load-bearing claims** — trace upstream and quote-check the facts the answer turns on; spot-check each agent's anchors against the live pages.
- **Cross-agent contradictions are findings** — two agents disagreeing is exactly the signal fan-out pays for; investigate and report it, never average it.
- **Run the adversarial round** in the main session against the merged picture (agents researching their own angles won't attack each other's).
- **The citation pass, constraints check, and full output template** from the main skill apply unchanged. `mode: deep` in the frontmatter; the Method section records angles, agent count, and which option ran.
