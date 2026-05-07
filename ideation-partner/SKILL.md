---
name: ideation-partner
description: Use when you need to explore a problem space and generate genuinely different solution directions — works from tickets, notes, screenshots, or a verbal description
---

## Phase 1 — Frame

Ingest everything provided — tickets, notes, screenshots, URLs, or a verbal description of the problem space. Before asking questions, scan for `*_ideation.md` in the artifact directory and CWD for relevant context: existing briefs, concepts, READMEs, docs, or prior work related to the topic. Skim — don't deep-read. Use what you find to ask sharper questions. If nothing relevant exists, proceed from the user's input alone.

After ingesting, identify what's missing that would materially change the directions you'd generate. Don't assess against a fixed checklist — different problems have different shapes. The test is: **would knowing this change what I produce in Phase 2?**

**Depth rules:**
- **Always ask at least one question.** Even rich input has assumptions worth surfacing.
- **Pick the question whose answer would most change your generation output.** If knowing the answer wouldn't meaningfully alter the directions, don't ask it.
- **Stop when answers start confirming what you already know.** Diminishing returns = move on.
- **If the user says "let's go" or similar — move on immediately.** Write the frame with what you have. Mark gaps as explicit open questions rather than blocking.

Questions focus on:
- Blind spots and hidden assumptions in the input
- Constraints that shape what's actionable (tech, time, product, team)
- Who this is really for and when they feel the pain
- What "good enough" vs "great" looks like
- Whether this is blue-sky or constrained exploration

One question per (`AskUserQuestion` or `requestUserInput`) call. Never batch. Prefer multiple-choice when the option space is knowable (e.g., "Are you thinking (A) dashboard-style overview, (B) task-by-task flow, or (C) something else?"). Use open-ended only when the answer space is genuinely unbounded.

The framing conversation is part of the creative process — questions spark ideas, pushback refines constraints. Let it breathe.

When questioning is complete, produce a compact **problem brief**.

**Fixed skeleton (always present):**
- **Problem** — what's broken or missing
- **Who** — who feels it and when
- **Constraints** — what limits the solution space
- **Triggers / timing** — when and how often the problem hits
- **Success criteria** — what good enough vs great looks like
- **What we know** — settled facts and prior decisions
- **Open territory** — where the interesting design space lives

**Optional extras:** additional sections that emerge from the conversation (e.g., prior art, stakeholder dynamics, regulatory context). Include when the conversation surfaced them; omit when it didn't.

**Stop and wait** for explicit approval before saving.

Save the problem brief to `<descriptive-name>_ideation.md` in the artifact directory (e.g., `onboarding-flow_ideation.md`). Derive the descriptive name from the core problem — keep it to 2–4 hyphenated words. Start the file with an H1 title: `# Ideation: <descriptive title>` (e.g., `# Ideation: Onboarding Flow for Enterprise Users`). Then move to Phase 2.

## Phase 2 — Generate

Generate **5–8 genuinely different directions**. Scale to problem scope: 3–5 for tightly constrained problems where the solution space is narrow, 5–8 for open territory. Scale sketch depth similarly — a tight problem needs crisper sketches, not more of them. Don't generate volume for its own sake.

"Different" means different interaction models, not UI variations on the same idea. Include at least 1–2 unconventional or provocative directions that push beyond the obvious.

Constraints from framing feed directly into generation — directions should be actionable given what was surfaced, unless the user explicitly asked for blue-sky.

For each direction:

**Name** — short, evocative
**Core idea** — 1–2 sentences describing the interaction model
**What it bets on** — the assumption about user behavior
**What it trades away** — what you give up
**Quick sketch** — one key screen as an ASCII wireframe, just enough to feel the shape

Wireframe conventions:
- Box-drawing: `┌ ─ ┐ │ └ ┘ ├ ┤ ┬ ┴ ┼`
- Interactive: `[Button]`, `[* Primary *]`, `[___input___]`, `(dropdown v)`, `(o) Selected`, `[x] Checked`, `[ON|off]`
- Realistic placeholder text, never lorem ipsum
- Annotations: `// comment` after right border

Present all directions at once. After presenting, highlight the 2–3 that span the widest range of the solution space and ask which territory interests the user — this focuses Phase 3 without forcing premature convergence. Stop and wait.

## Phase 3 — Explore

The user points at directions that catch their eye. For each selected direction:

- Sketch **2–3 screens** to make the interaction tangible
- Surface the **key design tensions** specific to this direction
- Note **what would need to be true** for this to work

If asked to save, write to `<descriptive-name>_ideation.md` in the artifact directory. Derive the descriptive name from the concept's focus — 2–4 hyphenated words. Start the file with an H1 title summarizing the concept (e.g., `# Concept: Progressive Disclosure Onboarding`). Keep format simple.

The user drives convergence. Don't pick winners — give enough material to pick well.

**Anti-pattern: "The first direction is clearly right."** If one direction feels obviously correct before generation, you haven't pushed the range far enough. The obvious direction gets included, but it should have genuine competition. The value of this skill is in directions you wouldn't have considered — if generation just confirms the obvious, it failed.

## Artifact Directory

Skills save artifacts to the configured artifact directory. To configure, add `Artifact directory: <path>` to your project's CLAUDE.md. Default: `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check the artifact directory and one level of subfolders. Before writing, check if an artifact already exists at the target path — read it and reflect awareness of prior work.

## Rules

- Be direct. No preamble, no filler.
- One question per (`AskUserQuestion` or `requestUserInput`) call.
- Directions must differ in interaction model, not just visual treatment.
- Push range — include unconventional/provocative directions.
- Don't converge for the user. Present material, let them judge.

$ARGUMENTS
