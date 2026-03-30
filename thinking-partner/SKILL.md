---
name: thinking-partner
description: Use when you need to think something through — weighing options, stress-testing a hunch, exploring a what-if, or working through a tradeoff that needs structured clarity before action
---

## 1. Read context

Scan CWD for context related to the topic: code, docs, existing `design-artifacts/**/*--thinking.md` sessions, `design-artifacts/**/*--research.md` artifacts, `design-artifacts/**/*--sense.md` artifacts, plans, and recent commits. Read what's relevant — don't deep-read everything. Note what exists and what's absent; both inform the Frame. If the user references specific files, prioritize those.

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

If the request is ambiguous about what kind of thinking is needed, ask one question with labeled options rather than guessing.

Calibration is a proposal, not a gate. If the user wants to skip straight to thinking, let them — but restate depth/shape so both sides know the plan.

**Not for:** understanding a problem (`/sensemaking-partner`), investigating facts (`/research-partner`), or generating divergent directions (`/ideation-partner`). Thinking-partner is for when context exists and you need to reason through it.

**Interactive questions** throughout this skill use `AskUserQuestion` or `requestUserInput` depending on platform.

## 3. Think

Execute the proposed moves in blocks of 1-2.

**Quick check:** All moves in one block. One exchange.

**Working session:** Blocks of 1-2 moves with pauses between. 2-4 exchanges total.

**Deep session:** Blocks of 1-2 moves with pauses and pressure-testing. Multiple rounds.

When convergent: after analysis, propose 2-3 approaches with trade-offs and lead with your recommendation. Don't just present balanced analysis — have a point of view.

Each pause = **stop and wait** — do not continue to the next phase in the same message. Prefer labeled options (A/B/C) over open-ended questions.

## 4. Act

If thinking leads to file changes: list each file and proposed change, get approval per file (approve / reject / modify), then apply.

If thinking surfaces that the user needs a different skill next, name it explicitly. Don't auto-invoke.

If no changes needed: skip to Capture.

## 5. Capture

Write a session note to `design-artifacts/<descriptive-name>--thinking.md`, where `<descriptive-name>` is 2-4 hyphenated words describing the artifact's focus (e.g., `design-artifacts/auth-token-expiry--thinking.md`).

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

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `design-artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders.

## Rules

- Be direct. No preamble, no filler. Labeled bullets for discrete items, prose for narrative.
- Quote sources, don't summarize — the user needs to see exactly what you're referencing.
- When convergent, have a point of view. Propose approaches with trade-offs and lead with your recommendation.
- Prefer labeled options (A/B/C) over open-ended questions — reduces friction and shows you've done enough thinking to enumerate the space.
- Every piece of analysis maps to a named move. If you can't name the move, don't do it.
- YAGNI: if thinking resolves without needing file changes, don't invent changes to make.
- If thinking reveals an upstream problem, name it. Don't patch downstream files to work around it.
- Don't skip thinking because it "seems obvious." The user invoked it for a reason.

$ARGUMENTS
