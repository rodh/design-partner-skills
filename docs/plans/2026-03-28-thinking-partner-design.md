# Thinking Partner Redesign

Redesign of reasoning-partner into a general-purpose thinking companion that adapts to what you bring it, replacing rigid pattern classification with calibrated depth and composable analytical moves.

## Motivation

reasoning-partner extracted three patterns (Hunch, What-if, Decision) from the original thinking-in-forma skill. This left it as a narrow residual: every request must be classified into one of three buckets, and every session runs the same four-part analysis template. Real thinking doesn't work that way.

Problems:
- The three-pattern frame is reductive — requests often blur categories
- The four-part analysis is forced on every session regardless of fit
- It's the most structurally rigid skill in the set
- Scope is implicitly limited to product design decisions, but users reach for it for strategy, process, and team questions too

## Changes

### 1. Rename to thinking-partner

`reasoning-partner` becomes `thinking-partner`. Description: "Use when you need to think something through — a decision, a hunch, a tradeoff, a strategy question, or anything that needs structured clarity before action."

Scope broadens beyond product design to any domain where structured thinking helps: technical architecture, strategy, process, team decisions.

What it is not: orient (decomposing to understand), research (investigating facts), ideation (generating divergent directions). Thinking-partner is for when you have enough context and need to reason through something.

### 2. Replace classification with calibration

Instead of Hunch/What-if/Decision gates, the Frame step proposes two dimensions:

**Depth:**
- **Quick check** — restate, direct take, one risk. One exchange. For sanity checks and gut-check requests.
- **Working session** — frame, 2-4 analytical moves, pauses between blocks. Typical weight.
- **Deep session** — multiple rounds, more moves, more pressure-testing. High-stakes or genuinely complex tradeoffs.

**Shape:**
- **Convergent** — narrowing toward a decision or position
- **Divergent** — exploring implications, tracing consequences, opening up
- **Diagnostic** — something feels off, need to find what and why

These are proposals, not gates. The user confirms or adjusts. Shape influences which analytical moves the skill reaches for.

### 3. Replace fixed template with composable analytical moves

Instead of one four-part analysis applied to everything, the skill has a toolkit of named moves:

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

The skill proposes 2-4 moves based on calibration. Move selection is visible to the user in the frame step and can be adjusted.

Every piece of analysis maps to a named move. If the skill can't name the move, it shouldn't be doing it. This is the guardrail that prevents drift into vague "let me think about that."

### 4. Incorporate brainstorming best practices

Four techniques from superpowers:brainstorming that strengthen the skill:

**Scope assessment in Frame.** If the user brings a tangled mess of entangled questions, decompose into separate thinking topics before diving into analysis. Don't spend moves refining details of a question that needs to be broken apart first.

**Propose approaches with a recommendation.** When thinking is convergent, don't just analyze positions symmetrically. Propose 2-3 distinct approaches with trade-offs and lead with your recommendation and reasoning. The skill should have a point of view.

**Section-by-section validation.** For working and deep sessions, present moves in blocks of 1-2 with pauses between. Don't dump the full analysis at once. Each pause is a checkpoint where the user can redirect.

**Self-review on Capture.** After writing the session note, quick scan: vague conclusions? Resolution that doesn't follow from analysis? Open threads that should have been resolved? Fix inline before finalizing.

## Skill Structure

### 1. Read context

Scan CWD for context related to the topic: code, docs, existing `artifacts/**/thinking-*.md` sessions, `artifacts/**/research-*.md` artifacts, `artifacts/**/orient-*.md` artifacts, plans, and recent commits. Read what's relevant. Note what exists and what's absent. If the user references specific files, prioritize those.

### 2. Frame

Read the request. Restate what we're thinking through.

**Scope check:** If the request contains multiple entangled questions, flag it. Propose decomposing into separate topics. Don't dive into analysis on a question that needs to be broken apart first.

**Calibrate:** Propose depth (quick check / working session / deep session) and shape (convergent / divergent / diagnostic). Propose 2-4 analytical moves based on calibration.

Present the frame: restated question + calibration + proposed moves. Stop and wait for confirmation or adjustment.

If the request is ambiguous about what kind of thinking is needed, ask one question with labeled options rather than guessing.

Calibration is a proposal, not a gate. If the user wants to skip straight to thinking, let them — but restate depth/shape so both sides know the plan.

### 3. Think

Execute the proposed moves in blocks of 1-2.

**Quick check:** All moves in one block. One exchange.

**Working session:** Blocks of 1-2 moves with pauses between. 2-4 exchanges total.

**Deep session:** Blocks of 1-2 moves with pauses and pressure-testing. Multiple rounds.

When convergent: after analysis, propose 2-3 approaches with trade-offs and lead with your recommendation. Don't just present balanced analysis — have a point of view.

Each pause = stop and wait. Prefer labeled options (A/B/C) over open-ended questions.

### 4. Act

If thinking leads to file changes: list each file and proposed change, get approval per file, then apply.

If thinking surfaces that the user needs a different skill next, name it explicitly. Don't auto-invoke.

If no changes needed: skip to Capture.

### 5. Capture

Write session note to `artifacts/thinking-<descriptive-name>.md`.

- **H1 title:** `# Thinking: <title>`
- **Session summary** — 2-3 sentences
- **Trigger** — the user's opening statement
- **Calibration** — depth and shape as proposed/adjusted
- **Moves applied** — which moves were used, key points from each (compressed)
- **Resolution** — what was decided, understood, or surfaced
- **Changes made** — what was modified, or "None"
- **Open threads** — anything surfaced but not resolved

**Self-review:** After writing, scan for vague conclusions, resolution that doesn't follow from analysis, and open threads that should have been resolved. Fix inline.

### Rules

- Be direct. No preamble, no filler. Labeled bullets for discrete items, prose for narrative.
- Quote sources, don't summarize — the user needs to see exactly what you're referencing.
- Steel-man all positions. Don't lead toward a predetermined answer.
- When convergent, have a point of view. Propose approaches with trade-offs and lead with your recommendation.
- Prefer labeled options (A/B/C) over open-ended questions.
- Every piece of analysis maps to a named move. If you can't name the move, don't do it.
- YAGNI: if thinking resolves without needing file changes, don't invent changes to make.
- If thinking reveals an upstream problem, name it. Don't patch downstream.
- Calibration is a proposal, not a gate. Meet the user where they are.
- Don't skip thinking because it "seems obvious." The user invoked it for a reason.

## What doesn't change

- Artifact directory conventions (artifacts/, create if needed, check one level of subfolders)
- Stop-and-wait discipline at phase boundaries
- Integration with the broader skill ecosystem (orient, research, ideation, scoping, pitch, next-move)
- Anti-pattern warning about skipping structured thinking
