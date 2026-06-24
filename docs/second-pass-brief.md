# Second-Pass Brief — Review & Literary Rewrite

> The standing brief for the novel's second pass. Hand this to the lead (Codex) for both
> steps below. The first draft is archived read-only at
> `archive/first-draft-2026-06-23.md` and in git — never edit the archive.

## Goal
Take the complete first draft and make it **as strong and well-written as possible —
literary-grade** — by strengthening its **themes and motifs**, deepening character and
prose, and finishing the under-developed chapters, **all strictly within the parameters
the project was given in `artifacts/`.** This is not a polish pass; it is a full,
purposeful rewrite toward a confident literary final draft.

## Parameters (the source of truth — obey these)
The `artifacts/` are canon and set the boundaries. Treat them as binding:
- **`Horror_Canoe_Style_Guide_UPDATED.md`** — the prose style, POV, tense, diction, and
  tonal rules. The rewrite's literary target is *this guide's* register, applied
  consistently across all 30 chapters.
- **`Horror_Canoe_Working_Story_Bible_UPDATED.txt`** and **`..._Character_Bible_UPDATED.txt`**
  — world, plot canon, character truths and arcs. Don't contradict them.
- **`Horror_Canoe_Mimicry_Ledger_UPDATED.txt`** — the rules of the central horror
  mechanic (what mimics, what it can/can't do, how it escalates). The motif work hangs
  off this; keep its logic exact and escalate it deliberately.
- **`Horror_Canoe_Route_and_Day_Map_UPDATED.txt`** — geography and day-by-day timeline.
  Continuity must match it.
- **`Horror_Canoe_30_Chapter_Working_Outline_UPDATED.md`** — the intended structure and
  the intended *scope* of each chapter (key signal for how developed the back half should be).
- Also honor the first pass's `docs/bible.md`, `docs/synthesis.md`, `docs/decisions.md`.

## Known weaknesses to fix (from the first-draft analysis)
1. **Severe unevenness of development.** Chapters 1–5 are full literary chapters
   (~3,500–4,000 words each); chapters 6–30 are compressed to ~400–600 words each — strong
   in bones but **under-written**. **Develop chapters 6–30 up to full chapters** matching
   the front half's depth, sensory texture, and interiority, and the outline's intent for
   each. Preserve the good material already there (e.g. the notebook-rules / "writing
   removes tone" beat in ch. 18) — build on it, don't discard it.
2. **Theme & motif throughlines must run the whole book**, not fade after the front:
   voice/mimicry, authority (Mike) vs. evidence/the written word, naming and "the planted
   phrase," trust between Joel and Will, the wilderness as indifferent. Seed and pay these
   off across all 30 chapters with intention.
3. **Consistent voice, POV, and tense** per the Style Guide, front to back.
4. **Escalation discipline** for the horror mechanic per the Mimicry Ledger — the dread
   should compound chapter to chapter, not plateau.

## The process: a 10-pass, chapter-chunked mentor chain (`..\paddle.ps1`)
The rewrite runs as **ten consecutive passes**, driven by `..\paddle.ps1`. Each pass is a
full cycle that treats the previous pass as a collaborator/mentor (improving its work, not
restarting), and works **chapter by chapter** so every chapter gets the model's full
attention. The edit units are `manuscript/chapters/*.md`; the unified `manuscript/novel.md`
is **re-assembled from them after each pass** (for reading + stable line citations).

Within a pass, for each chapter the agent:
1. **Reads & synthesizes** this brief, the artifacts, the previous pass's notes
   (`docs/passes/pass-(N-1)-notes.md`), the whole-arc synopsis from last pass
   (`docs/synopsis-prev.md`), the story-so-far synopsis this pass (`docs/synopsis.md`),
   and the previous (already-revised) chapter.
2. **Reviews, then fixes** that chapter in place toward the goals above
   (weakest-material-first: develop under-written chapters to full length, deepen
   themes/motifs and interiority, elevate prose, tighten horror escalation, keep canon),
   and appends a short entry to the running synopsis.
After the chapter sweep, a closing step **leaves a hand-off note** `docs/passes/pass-N-notes.md`
(good/strong · controversial · unfinished · murky · character work remaining). The script
then **commits the pass** and snapshots `novel.md` to `archive/passes/`.

After the final pass it writes **`docs/REVIEW_SUMMARY.md`** for human review — what was
controversial across passes, what's unfinished/murky/strong, what character development is
still needed — **citing specific line numbers in `novel.md`**.

Honor the **broad spirit** of the original guidelines; you needn't follow every outlined
detail literally, but keep the world, canon, and intent coherent. The archived first draft
(`archive/first-draft-2026-06-23.md`) and the per-pass snapshots stay untouched.

## Constraints
- Stay inside the artifacts' world, style, and canon — strengthen within the box, don't
  reinvent it.
- Markdown, UTF-8 (no BOM). The whole novel is the single file `manuscript/novel.md`;
  edit it in place and never truncate it mid-write.
- Delegate routine work (continuity scans, motif-occurrence searches, summaries) to local
  Qwen via `..\delegate-local.ps1`; keep the expensive judgment for the prose itself.
