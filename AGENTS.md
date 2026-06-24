# paddlewhispers — project notes for agents

(Inherits the workspace workflow in `../AGENTS.md`. This file is project-specific.)

## What this is
A **novel** to be completed. A body of existing artifacts (drafts, notes, outlines,
character sketches, worldbuilding, fragments) will be dropped into `artifacts/`. The
goal: **synthesize those artifacts and complete the rough draft** — autonomously, end
to end — after which the human and the agents **revise together**.

## Who leads
**Codex-cloud (gpt-5.5) is the lead author/director** for this project — it is strong at
narrative and long-form creative writing. It directs the work and **delegates routine
subtasks to local Qwen** when that makes sense (continuity scans, summarizing an
artifact, consistency checks, formatting passes, light copyedits). Claude-cloud is
available for hard structural/plot reasoning or a critical review pass, but is not the
default driver here — keep the expensive models for judgment, not typing.

## Layout
- `artifacts/` — **source material the human provides** (read-only inputs). Never edit
  these; they are the raw clay.
- `manuscript/` — the **output**: the rough draft, written chapter by chapter
  (`NN-chapter-title.md`), plus a `00-outline.md`.
- `docs/` — the **story bible** (`bible.md`: characters, world, timeline, voice, canon)
  and a `synthesis.md` (what the artifacts contain, what's settled, what's missing).

## The job (Codex, run autonomously to a complete rough draft)
1. **Read every artifact** in `artifacts/`. Build `docs/synthesis.md`: the premise,
   characters, arc, voice/tone, what already exists vs. what's missing or contradictory.
2. **Lock an outline** in `manuscript/00-outline.md` (beats → chapters). Reconcile
   contradictions between artifacts; record the call in `docs/bible.md`.
3. **Write the rough draft straight through** — chapter by chapter into `manuscript/`,
   keeping `docs/bible.md` continuous (characters, timeline, canon) as you go.
4. **Match the established voice** from the artifacts; don't impose a new one.
5. **Don't block.** This is a rough draft — make reasonable creative calls, note the
   notable ones in `docs/decisions.md`, and keep writing to THE END. Revision is a
   later, collaborative phase.

## How to run (once artifacts are in `artifacts/`)
The launcher scripts live in the workspace root (`C:\Users\josie\projects`), so call them
with `..\` from inside this folder (or `.\` if you `cd ..` to the root first).

From inside `paddlewhispers\`:
```
..\escalate-codex.ps1 -Exec -Cwd . "Novel lead: read AGENTS.md and every file in artifacts/, then do the job described there — synthesize, outline, and write the rough draft straight through into manuscript/, keeping docs/bible.md current. Work to a complete draft; bank notable creative calls in docs/decisions.md; delegate routine scans/summaries to local Qwen via ..\delegate-local.ps1."
```
(Equivalently, from the workspace root: `.\escalate-codex.ps1 -Exec -Cwd .\paddlewhispers "<same prompt>"`.)
For a very long draft, run it in chapter batches (it appends to `manuscript/` and the
bible each pass) rather than one giant call. A keep-going loop (like `..\studio.ps1`)
can be added if we want it fully hands-off across many chapters — ask the human.

## Conventions
- Prose in Markdown, UTF-8 (no BOM). One file per chapter; never truncate/overwrite a
  finished chapter — append or edit in place.
- `artifacts/` is sacrosanct (inputs); all new writing goes in `manuscript/` and `docs/`.
- Git: commit at chapter checkpoints with clear messages. The human revises after the
  draft is complete.
