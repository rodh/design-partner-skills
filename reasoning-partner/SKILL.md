---
name: reasoning-partner
description: Use when you're facing a decision, something feels off, or you want to explore a what-if — stress-tests assumptions through structured evidence-and-stakes analysis
---

## 1. Read context

Scan CWD for context related to the topic: code, docs, existing `artifacts/**/reasoning-*.md` sessions, `artifacts/**/research-*.md` artifacts, `artifacts/**/orient-*.md` artifacts, plans, and recent commits. Read what's relevant — don't deep-read everything. Note what exists and what's absent; both inform the Frame. If the user references specific files, prioritize those.

## 2. Frame

Classify the request from `$ARGUMENTS` and context.

**Hunch ("something feels off"):**
- Present compact state summary (one sentence per relevant file/area), then ask "what's nagging you?"
- One question per message. Allow 1-2 rounds to get from vague → specific. Surface tensions as options if they can't articulate it.
- **Output:** a precise statement of the issue

**What-if ("what if we tried..."):**
- Restate the idea as a testable proposition
- One quick check: "Is that a fair restatement?" (skip if clearly accurate)
- **Output:** the proposition to trace

**Decision ("should we X or Y"):**
- Acknowledge the options. If only one stated, ask for the alternative.
- Frame as "[X] vs [Y] given [relevant context]"
- **Output:** the framed decision

**STOP after Frame** (Hunch/What-if/Decision only). Present the framed output and wait for the user to confirm or adjust before proceeding to Think.

If ambiguous, ask one interactive question (`AskUserQuestion` or `requestUserInput`): **A. Surface something** (hunch), **B. Explore a what-if**, **C. Decide between options**. If the request doesn't fit any of these patterns — it's really about understanding context rather than reasoning through a decision — say so and let the user decide how to proceed.

## 3. Think

**Four-part analysis:**

1. **What the evidence says** — pull relevant content from files/context, quote specific lines/sections
2. **What's at stake** — concrete downstream effects if we go one way vs another
3. **Strongest argument for each side** — steel-man all positions (even for hunches: steel-man "it's actually fine" vs "there's a real problem")
4. **What we'd need to believe** — the assumption each direction rests on

**Dialogue pacing:**

| Pattern | Delivery | Exchanges |
|---------|----------|-----------|
| Hunch | Pause after tensions, check in after each analysis piece | 2-3 |
| What-if | Four-part analysis as one block, then "worth pursuing or dead end?" | 1 |
| Decision | Four-part analysis as one block, then "which way are you leaning?" Pressure-test before Act. | 1 |

Each pause = **stop and wait** — do not continue to the next phase in the same message. Prefer labeled options (A/B/C) over open-ended questions.

## 4. Act

If thinking leads to file changes: list each file and proposed change, get approval per file via interactive question (`AskUserQuestion` or `requestUserInput`) (approve / reject / modify), then apply.

If no changes needed: skip to Capture.

## 5. Capture

Write a session note to `artifacts/reasoning-<descriptive-name>.md`, where `<descriptive-name>` is 2–4 hyphenated words describing the artifact's focus (e.g., `artifacts/reasoning-auth-token-expiry.md`).

Start the file with an H1 title in the format `# Reasoning: <title>`, where `<title>` summarizes the session content. Example: `# Reasoning: Should we expire auth tokens on role change?`

- **Type:** Reasoning
- **Session summary** — 2-3 sentences
- **Trigger** — the user's opening statement
- **Frame** — the precise question or decomposition arrived at
- **Analysis** — key points from Think (compressed)
- **Resolution** — what was decided or understood
- **Changes made** — what was modified, or "None"
- **Open threads** — anything surfaced but not resolved

**Anti-pattern: "This doesn't need structured thinking."** The temptation to skip framing is strongest on decisions that feel obvious. Those are exactly where unexamined assumptions do the most damage. The frame can be two sentences, but it must exist.

## Artifact Directory

Skills save artifacts to `artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders.

## Rules

- Be direct. No preamble, no filler. Labeled bullets for discrete items, prose for narrative.
- Quote sources, don't summarize — the user needs to see exactly what you're referencing.
- Steel-man all positions. Don't lead the user toward a predetermined answer.
- Prefer labeled options (A/B/C) over open-ended questions — reduces friction and shows you've done enough thinking to enumerate the space.
- YAGNI: if thinking resolves without needing file changes, don't invent changes to make.
- If thinking reveals an upstream problem, name it. Don't patch downstream files to work around it.
- Don't skip thinking because it "seems obvious." The user invoked it for a reason.

$ARGUMENTS
