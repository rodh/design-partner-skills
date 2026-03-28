---
name: orienting-partner
description: Use when you need to break down and map a ticket, task, or project context — what the parts are, where complexity hides, and what level of effort each part warrants
---

## 1. Scope

Ingest context from `$ARGUMENTS` — tickets, docs, task descriptions, conversation threads, flows. Scan CWD for related code, docs, existing `artifacts/**/orient-*.md` artifacts, `artifacts/**/thinking-*.md` sessions, `artifacts/**/research-*.md` artifacts, plans, and recent commits. Read what's relevant — don't deep-read everything. If a prior artifact already covers this, surface it instead of re-decomposing.

Classify:

- **Specific artifact understanding** — a ticket, task, or defined piece of work that needs decomposition.
- **Broader project/domain understanding** — mapping a larger space to figure out what's going on.

For **broader understanding**: present the scope (what's in, what's out) and **stop — wait for user confirmation** before proceeding.

For **specific artifact**: proceed directly to Decompose with no stop.

## 2. Decompose

Four-part analysis:

1. **Breakdown** — decompose the problem into constituent parts, name each clearly
2. **Landscape** — what exists already, what's new, what's uncertain
3. **Design surface** — identify which parts carry design effort (UI, interaction patterns, information architecture, data modeling, API surface, etc.). Call out where design complexity hides — the parts that look simple but require real design thinking. Rate each: no design needed / light design / significant design effort.
4. **Effort assessment** — overall level of engagement each part warrants (light touch vs. deep dive), informed by the design surface analysis

**Stop and wait** after presenting the decomposition. Present labeled options (A/B/C) for what to dig into or confirm, not open-ended questions.

## 3. Synthesize

Present a scoped problem statement with 2-3 labeled next moves reflecting the actual situation. Suggest downstream skills as appropriate:

- Planning what design work to do for a larger initiative (`/strategy-partner` if available)
- Thinking through a decision, tradeoff, or stress-testing assumptions (`/thinking-partner` if available)
- Deeper investigation into unknowns (`/research-partner` if available)
- Exploring solution directions (`/ideation-partner` if available)
- Breaking work into prioritized scope (`/scoping-partner` if available)

**Stop and wait.**

## 4. Save

Save to `artifacts/orient-<descriptive-name>.md` with:

- H1 title: `# Orient: <title>` summarizing what was decomposed
- Date
- **Question/Context** — the original ticket, task, or domain being understood
- **Decomposition** — breakdown, landscape, design surface, effort assessment (compressed)
- **Problem Statement** — the scoped statement arrived at
- **Next Moves** — recommended paths forward with skill references
- **Open Threads** — anything surfaced but not resolved

The artifact must be **self-contained** — readable without conversation context.

**No Act phase.** Orient produces understanding; downstream skills produce action.

**Anti-pattern: "I already understand this."** The temptation to skip decomposition is strongest on tasks that look straightforward. Those are exactly where hidden design complexity and unstated assumptions do the most damage. The decomposition can be compact, but it must exist.

## Artifact Directory

Skills save artifacts to `artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders.

## Rules

- Be direct. No preamble, no filler. Labeled bullets for discrete items, prose for narrative.
- Quote sources, don't summarize — the user needs to see exactly what you're referencing.
- Steel-man all positions. Don't lead the user toward a predetermined answer.
- Prefer labeled options (A/B/C) over open-ended questions — reduces friction and shows you've done enough thinking to enumerate the space.
- If decomposition reveals that research is needed before understanding is possible, say so. Don't fake understanding with shallow analysis.
- Artifacts must be self-contained. Someone reading the file with no conversation context should understand the decomposition.

$ARGUMENTS
