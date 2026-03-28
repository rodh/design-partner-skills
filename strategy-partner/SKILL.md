---
name: strategy-partner
description: Use when you have an initiative, ticket, or brief and need to plan what design work to do — which questions to answer, what to learn, and in what order
---

## Phase 1 — Ingest

Scan `artifacts/` (and one level of subfolders) for existing work — orient maps, research artifacts, thinking sessions, briefs, concepts. Read whatever input is provided: orient artifact, ticket, PRD, notes, verbal description. Assess what exists vs. what's missing. If the input is too thin to plan from, name what's needed rather than guessing.

## Phase 2 — Frame

Restate the initiative in one sentence.

Identify 3-6 **design surface areas** that need attention. For each:

- **What it is** — one sentence
- **Why it matters** — what's at stake if this area is poorly understood or poorly designed
- **What's uncertain** — the open questions or unknowns in this area

Surface 2-4 **strategic questions** the design work needs to answer. These are the through-lines that connect surface areas — the questions whose answers would most change what you build.

Present the surface areas and strategic questions first. Then ask 1-2 clarifying questions about gaps: constraints, timelines, existing work, stakeholder expectations. One question per `AskUserQuestion` or `requestUserInput` call.

If the user says "just go" or similar, proceed with reasonable assumptions and flag them.

**Stop and wait.**

**Not for:** decomposing a problem you don't yet understand (`/orienting-partner`), working through a specific decision or tradeoff (`/thinking-partner`), or breaking a chosen direction into buildable tiers (`/scoping-partner`). Strategy-partner plans *what design work to do*, not *how to do it*.

## Phase 3 — Plan workstreams

Group design surface areas into 2-4 **workstreams**. For each:

- **Name** — what this stream of work is about
- **Covers** — which surface areas it addresses
- **Strategic questions** — which questions from Phase 2 it advances

Map dependencies: what gates what, what runs in parallel.

Within each workstream, sequence 2-5 **design actions**:

| Action | Why | Method | Unblocks |
|--------|-----|--------|----------|
| What to do | Which strategic question it advances | Partner skill when one fits, or other method (stakeholder interview, analytics review, usability test, competitive audit, etc.) | What this enables next |

**Stop and wait.**

## Phase 4 — Prioritize

Highlight 2-3 **highest-value first actions** across all workstreams — if you do nothing else, do these. For each, state why it's highest-value: what it unblocks, what risk it retires, or what decision it enables.

Flag time-sensitive or blocking actions separately.

Note open questions that could change the plan — places where new information would reshape priorities or workstream structure.

**Stop and wait.**

## Phase 5 — Capture

Save to `artifacts/strategy-<descriptive-name>.md`, where `<descriptive-name>` is 2-4 hyphenated words describing the artifact's focus.

Start the file with an H1 title: `# Strategy: <title>` (e.g., `# Strategy: Onboarding Redesign`).

Structure:

- **Initiative** — 2-3 sentences on what's being planned and why
- **Strategic questions** — the 2-4 questions driving the plan
- **Workstreams** — each with scope, dependencies, and action table
- **Start Here** — the 2-3 highest-value first actions with rationale
- **Open questions** — unknowns that could reshape the plan

The artifact must be **self-contained** — readable without conversation context.

**Anti-pattern: "Plan everything before acting."** Strategy plans design work, not the entire initiative. Don't include build/implementation actions — those belong in scoping. Don't treat the plan as final — flag where it's most likely to pivot based on what you learn.

**Anti-pattern: "Organize by discipline."** Workstreams should be organized by what you need to learn, not by role (research workstream, design workstream, etc.). If workstreams map to job titles, reframe them around the questions they answer.

## Artifact Directory

Skills save artifacts to `artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders.

## Rules

- Be direct. No preamble, no filler.
- One question per (`AskUserQuestion` or `requestUserInput`) call.
- Every action recommends a method — partner skill when one fits, other methods when they're better. Don't force actions into skills.
- Workstreams must be parallel-capable. If everything is sequential, it's a linear plan in disguise — restructure or acknowledge that parallelism isn't possible and explain why.
- Strategic questions inform the plan — they appear as rationale in the "Why" column of action tables. The standalone list in the artifact exists for orientation, not as a separate deliverable.
- "Start Here" is mandatory. Every strategy names 2-3 highest-value first actions.
- If there's only one workstream, the initiative may not need strategizing — say so and recommend going straight to the appropriate skill (`/research-partner`, `/thinking-partner`, `/ideation-partner`, or `/scoping-partner`).
- If input needs decomposition before strategizing is productive, say so and recommend `/orienting-partner`.

$ARGUMENTS
