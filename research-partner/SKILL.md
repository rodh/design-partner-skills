---
name: research-partner
description: Use when you need to research a topic — look into competitor patterns, technical approaches, how something works, or answer focused factual questions
---

## 1. Scope

Ingest the research question from `$ARGUMENTS`. Scan CWD for context related to the topic: code, docs, existing `design-artifacts/**/*--research.md` artifacts, plans, and recent commits. Read what's relevant — don't deep-read everything. If a prior artifact already answers the question, surface it instead of re-researching.

Classify depth:

- **Quick lookup** — factual question with a clear answer. Skip straight to Investigate (no stop).
- **Landscape survey** — mapping approaches, competitors, or patterns across a space.
- **Deep dive** — thorough investigation of a specific technique, tool, or domain.

For **landscape** or **deep dive**: present the scope (what's in, what's out, breadth of investigation) and **stop — wait for user confirmation** before proceeding.

For **quick lookup**: proceed directly to Investigate with no stop.

## 2. Investigate

Conduct research using available tools — web search, web fetch, codebase scan, whatever fits the question. Work iteratively: follow leads, cross-reference sources, and fill gaps.

Organize findings by **theme or approach**, not by source. Group related information together even if it came from different places.

If findings shift the question, pause and restate the adjusted scope before continuing. Don't let the investigation silently drift.

Know when to stop: if the last 2-3 sources are confirming what you already found without adding new dimensions, move to Synthesize.

## 3. Synthesize

Structure findings into a summary:

- **Question** — the research question as scoped
- **Findings** — organized by theme, with specifics (names, numbers, patterns — not vague summaries)
- **Key takeaways** — 2-5 bullets distilling what matters most
- **Implications for this project** — if project context exists, connect findings to the current work
- **Sources** — where applicable

Present the summary. **Stop and wait** for the user to confirm before saving.

## 4. Save

Save to `design-artifacts/<descriptive-name>--research.md` with:

- H1 title: `# Research: <title>` summarizing the research question
- Date
- Full structured findings from Synthesize

The artifact must be **self-contained** — readable without conversation context.

**Anti-pattern: "I'll just start searching."** The temptation to skip scoping is strongest when the question feels obvious. But unscoped research sprawls — you end up with a pile of links organized by when you found them, not by what they mean. Even a one-line scope ("Quick lookup: what's the max payload size for X?") keeps the investigation focused.

## Artifact Directory

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `design-artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders.

## Rules

- Be direct. No preamble, no filler. Labeled bullets for discrete items, prose for narrative.
- Quote sources, don't summarize — the user needs to see exactly what you're referencing.
- Organize by theme, not by source. The user cares about the landscape, not which URL said what.
- Quick lookups should be fast — don't over-structure a factual answer.
- Landscape surveys and deep dives earn their depth. Don't pad with shallow findings to look thorough.
- If research turns up nothing useful, say so. Don't dress up thin results.
- Artifacts must be self-contained. Someone reading the file with no conversation context should understand the findings.
- If research reveals a decision point, note it — the user may want to reason through it next. If findings open up a solution space, note that too — exploring directions may be a natural next step.

$ARGUMENTS
