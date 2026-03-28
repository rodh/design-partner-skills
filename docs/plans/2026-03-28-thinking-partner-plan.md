# Thinking Partner Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Rename reasoning-partner to thinking-partner, rewrite SKILL.md with calibrated depth and composable analytical moves, and update all cross-references across the skill set.

**Architecture:** Rename directory, rewrite the skill file from the design spec, update references in 4 other files (README, orient-partner, next-move-partner, scoping-partner). install.sh uses `*-partner` globs so it requires no changes.

**Tech Stack:** Markdown skill files, bash install script

---

### Task 1: Rename reasoning-partner directory to thinking-partner

**Files:**
- Rename: `reasoning-partner/` → `thinking-partner/`

**Step 1: Rename the directory**

Run: `git mv reasoning-partner thinking-partner`

**Step 2: Verify rename**

Run: `ls -la thinking-partner/SKILL.md`
Expected: file exists

**Step 3: Commit**

```bash
git add -A
git commit -m "Rename reasoning-partner directory to thinking-partner"
```

---

### Task 2: Rewrite thinking-partner SKILL.md

**Files:**
- Modify: `thinking-partner/SKILL.md` (full rewrite)

**Step 1: Write the new SKILL.md**

Replace the entire contents of `thinking-partner/SKILL.md` with the skill definition from the design spec (`docs/plans/2026-03-28-thinking-partner-design.md`, "Skill Structure" section). The file should contain:

```markdown
---
name: thinking-partner
description: Use when you need to think something through — a decision, a hunch, a tradeoff, a strategy question, or anything that needs structured clarity before action
---

## 1. Read context

Scan CWD for context related to the topic: code, docs, existing `artifacts/**/thinking-*.md` sessions, `artifacts/**/research-*.md` artifacts, `artifacts/**/orient-*.md` artifacts, plans, and recent commits. Read what's relevant — don't deep-read everything. Note what exists and what's absent; both inform the Frame. If the user references specific files, prioritize those.

## 2. Frame

Read the request. Restate what we're thinking through.

**Scope check:** If the request contains multiple entangled questions, flag it. Propose decomposing into separate topics. Don't dive into analysis on a question that needs to be broken apart first.

**Calibrate:** Propose depth and shape, then select 2-4 analytical moves.

**Depth:**
- **Quick check** — restate, direct take, one risk. One exchange. For sanity checks and gut-check requests.
- **Working session** — frame, 2-4 analytical moves, pauses between blocks. Typical weight.
- **Deep session** — multiple rounds, more moves, more pressure-testing. High-stakes or genuinely complex tradeoffs.

**Shape:**
- **Convergent** — narrowing toward a decision or position
- **Divergent** — exploring implications, tracing consequences, opening up
- **Diagnostic** — something feels off, need to find what and why

**Analytical moves** — propose 2-4 from this toolkit based on calibration:

| Move | What it does | Good for |
|------|-------------|----------|
| Evidence | Pull relevant content from files/context, quote specific lines | Grounding any session in reality |
| Stakes | Trace concrete downstream effects of each direction | Convergent decisions, high-stakes calls |
| Steel-man | Strongest argument for each position | Decisions, pressure-testing hunches |
| Assumptions | Name what you'd need to believe for each direction to be right | Decisions, what-ifs |
| Decompose | Break a tangled thing into named parts | Diagnostic, complex tradeoffs |
| Trace | Follow one idea forward — what happens next, then next | Divergent exploration, what-ifs |
| Pressure-test | Actively try to break the leading position | Before committing to anything |
| Reframe | Restate the problem from a different angle | When stuck, when the framing itself is the issue |

Present the frame: restated question + calibration + proposed moves. **Stop and wait** for confirmation or adjustment.

If the request is ambiguous about what kind of thinking is needed, ask one question with labeled options (`AskUserQuestion` or `requestUserInput`) rather than guessing.

Calibration is a proposal, not a gate. If the user wants to skip straight to thinking, let them — but restate depth/shape so both sides know the plan.

## 3. Think

Execute the proposed moves in blocks of 1-2.

**Quick check:** All moves in one block. One exchange.

**Working session:** Blocks of 1-2 moves with pauses between. 2-4 exchanges total.

**Deep session:** Blocks of 1-2 moves with pauses and pressure-testing. Multiple rounds.

When convergent: after analysis, propose 2-3 approaches with trade-offs and lead with your recommendation. Don't just present balanced analysis — have a point of view.

Each pause = **stop and wait** — do not continue to the next phase in the same message. Prefer labeled options (A/B/C) over open-ended questions.

## 4. Act

If thinking leads to file changes: list each file and proposed change, get approval per file via interactive question (`AskUserQuestion` or `requestUserInput`) (approve / reject / modify), then apply.

If thinking surfaces that the user needs a different skill next, name it explicitly. Don't auto-invoke.

If no changes needed: skip to Capture.

## 5. Capture

Write a session note to `artifacts/thinking-<descriptive-name>.md`, where `<descriptive-name>` is 2-4 hyphenated words describing the artifact's focus (e.g., `artifacts/thinking-auth-token-expiry.md`).

Start the file with an H1 title in the format `# Thinking: <title>`, where `<title>` summarizes the session content.

- **Session summary** — 2-3 sentences
- **Trigger** — the user's opening statement
- **Calibration** — depth and shape as proposed/adjusted
- **Moves applied** — which moves were used, key points from each (compressed)
- **Resolution** — what was decided, understood, or surfaced
- **Changes made** — what was modified, or "None"
- **Open threads** — anything surfaced but not resolved

**Self-review:** After writing, scan for: vague conclusions, resolution that doesn't follow from analysis, open threads that should have been resolved. Fix inline before finalizing.

**Anti-pattern: "This doesn't need structured thinking."** The temptation to skip framing is strongest on decisions that feel obvious. Those are exactly where unexamined assumptions do the most damage. The frame can be one sentence and the depth can be "quick check," but calibration must exist.

## Artifact Directory

Skills save artifacts to `artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders.

## Rules

- Be direct. No preamble, no filler. Labeled bullets for discrete items, prose for narrative.
- Quote sources, don't summarize — the user needs to see exactly what you're referencing.
- Steel-man all positions. Don't lead toward a predetermined answer.
- When convergent, have a point of view. Propose approaches with trade-offs and lead with your recommendation.
- Prefer labeled options (A/B/C) over open-ended questions — reduces friction and shows you've done enough thinking to enumerate the space.
- Every piece of analysis maps to a named move. If you can't name the move, don't do it.
- YAGNI: if thinking resolves without needing file changes, don't invent changes to make.
- If thinking reveals an upstream problem, name it. Don't patch downstream files to work around it.
- Calibration is a proposal, not a gate. Meet the user where they are.
- Don't skip thinking because it "seems obvious." The user invoked it for a reason.

$ARGUMENTS
```

**Step 2: Review the written file**

Read back `thinking-partner/SKILL.md` and verify:
- Frontmatter has `name: thinking-partner` and updated description
- All 5 phases present (Read context, Frame, Think, Act, Capture)
- Moves table is complete (8 moves)
- Calibration dimensions present (depth + shape)
- Self-review in Capture phase
- Scope check in Frame phase
- "Propose approaches with recommendation" in Think phase
- Anti-pattern warning present
- Rules section complete

**Step 3: Commit**

```bash
git add thinking-partner/SKILL.md
git commit -m "Rewrite thinking-partner SKILL.md with calibration and composable moves"
```

---

### Task 3: Update README.md

**Files:**
- Modify: `README.md`

**Step 1: Update the skill entry**

Replace the reasoning-partner entry (line 11) with:

```markdown
**`/thinking-partner`** — Think something through: a decision, a hunch, a tradeoff, a strategy question, or anything that needs structured clarity before action. Calibrates depth and selects from composable analytical moves to match what you bring it.
```

**Step 2: Update the flow diagram**

Replace `Reason` with `Think` and `(decide)` with `(think)` in the flow diagram (lines 26-28). The updated diagram:

```
Orient →  Research →  Think →   Ideate →   Scope →  Pitch
(map)     (learn)     (think)   (explore)  (plan)   (share)
```

**Step 3: Update the description paragraph**

Replace "**Reasoning** works through decisions and assumptions" (line 30) with "**Thinking** works through decisions, hunches, tradeoffs, and assumptions."

**Step 4: Review changes**

Read back `README.md` and verify no stale references to "reasoning" remain (the design doc in `docs/plans/` is fine — it's historical).

**Step 5: Commit**

```bash
git add README.md
git commit -m "Update README for reasoning-partner → thinking-partner rename"
```

---

### Task 4: Update cross-references in orient-partner

**Files:**
- Modify: `orient-partner/SKILL.md`

**Step 1: Update artifact scan pattern**

Line 8: replace `artifacts/**/reasoning-*.md` with `artifacts/**/thinking-*.md`

**Step 2: Update skill reference**

Line 34: replace:
```
- Reasoning through a decision or stress-testing assumptions (`/reasoning-partner` if available)
```
with:
```
- Thinking through a decision, tradeoff, or stress-testing assumptions (`/thinking-partner` if available)
```

**Step 3: Commit**

```bash
git add orient-partner/SKILL.md
git commit -m "Update orient-partner cross-references for thinking-partner rename"
```

---

### Task 5: Update cross-references in next-move-partner

**Files:**
- Modify: `next-move-partner/SKILL.md`

**Step 1: Update artifact scan pattern**

Line 11: replace `reasoning-*.md` with `thinking-*.md` and update the label from "session notes" to "session notes"

**Step 2: Update skill reference on line 44**

Replace:
```
- Concepts exist but assumptions are untested? A reasoning session on the riskiest bet would help — e.g., "Run `/reasoning-partner` to stress-test the progressive-elicitation concept."
```
with:
```
- Concepts exist but assumptions are untested? A thinking session on the riskiest bet would help — e.g., "Run `/thinking-partner` to stress-test the progressive-elicitation concept."
```

**Step 3: Update skill reference on line 61**

Replace `/reasoning-partner` with `/thinking-partner` and update the description from "to reason through a decision" to "to think through a decision"

**Step 4: Update status map label on line 20**

Replace "significant reasoning sessions" with "significant thinking sessions" if present.

**Step 5: Update status map display**

Line 31 area: replace `Reasoning` with `Thinking` in the example status map display.

**Step 6: Commit**

```bash
git add next-move-partner/SKILL.md
git commit -m "Update next-move-partner cross-references for thinking-partner rename"
```

---

### Task 6: Update cross-reference in scoping-partner

**Files:**
- Modify: `scoping-partner/SKILL.md`

**Step 1: Update artifact reference**

Line 8: replace "reasoning sessions" with "thinking sessions"

**Step 2: Commit**

```bash
git add scoping-partner/SKILL.md
git commit -m "Update scoping-partner cross-reference for thinking-partner rename"
```

---

### Task 7: Verify install.sh compatibility

**Files:**
- Read only: `install.sh`

**Step 1: Verify glob patterns**

Confirm that `install.sh` uses `*-partner` glob patterns (line 31, 132) that will automatically pick up `thinking-partner` and that the stale symlink pruning in `do_update` will clean up old `reasoning-partner` links.

Run: `grep -n 'partner' install.sh`
Expected: glob patterns like `*-partner`, no hardcoded `reasoning-partner`

No changes needed — just verification.

---

### Task 8: Final verification

**Step 1: Check for any remaining stale references**

Run: `grep -r "reasoning-partner" --include="*.md" . | grep -v docs/plans/`
Expected: no results (design doc references are historical and fine)

Run: `grep -r "reasoning-\*" --include="*.md" . | grep -v docs/plans/`
Expected: no results

**Step 2: Verify directory structure**

Run: `ls -la thinking-partner/SKILL.md`
Expected: file exists

Run: `ls -la reasoning-partner/ 2>&1`
Expected: no such directory

**Step 3: Commit plan file**

```bash
git add docs/plans/2026-03-28-thinking-partner-plan.md
git commit -m "Add thinking-partner implementation plan"
```
