---
name: next-move-partner
description: Use when you want to know what design move to make next — unclear where to focus or what's been missed
---

## 1. Scan

Scan `artifacts/` (and one level of subfolders) for artifacts by filename prefix:

- `orient-*.md` orientation artifacts
- `reasoning-*.md` session notes
- `research-*.md` findings
- `brief-*.md` problem briefs
- `concept-*.md` concept explorations
- `scope-*.md` scoping documents
- `pitch-*.md` / `ticket-*.md` pitch artifacts

Also scan CWD for READMEs, docs, plans, tickets, and other project context.

Read each artifact's title and opening section — enough to know what it covers, not a deep read. Note what exists, what's missing, and what looks stale (e.g., a brief that predates significant reasoning sessions).

## 2. Status map

Present a compact status map grouped by artifact type, showing what exists:

```
Briefs      1 (onboarding-flow)
Concepts    2 (onboarding-progressive, onboarding-wizard)
Orient      1 (login-complexity)
Reasoning   None
Research    1 (enterprise-onboarding)
Scoping     None
Pitches     None
Tickets     None
```

Keep it tight — this is a glanceable dashboard, not a report.

## 3. Recommend

Based on the status map, recommend the **single highest-value next move** with brief reasoning. Follow a natural design progression but respond to the actual state, not a rigid sequence:

- Brief exists but no concepts? Ideation gives you directions to evaluate — e.g., "Run `/ideation-partner` to explore directions for prompt-specificity."
- Concepts exist but assumptions are untested? A reasoning session on the riskiest bet would help — e.g., "Run `/reasoning-partner` to stress-test the progressive-elicitation concept."
- Wireframes exist but haven't been validated? User testing would surface problems before you scope.
- Design is validated but not scoped? Scoping breaks it into buildable pieces — e.g., "Run `/scoping-partner` on the interaction-patterns concept."
- Problem framed but key assumptions lack evidence? Run `/research-partner` to investigate before committing to a direction.
- Work is scoped but stakeholders haven't bought in? A pitch gets alignment.

Name the specific skill to invoke, reference the relevant artifacts, and suggest input.

If the user has a different instinct, respect it. This skill advises — it doesn't dictate.

**Anti-pattern: "I already know what's next."** The value isn't confirming your plan — it's surfacing what the status map reveals that you aren't seeing. If you skip the scan, you build on stale context or miss that an artifact has drifted out of alignment.

## Rules

- Be direct. Status map + one recommendation + suggested invocation. No preamble.
- This is a diagnostic, not a workflow. Fast in, fast out.
- Don't deep-read artifacts — skim titles and structure to assess completeness.
- If nothing exists yet, say so and recommend starting with `/orient-partner` to understand the problem, `/reasoning-partner` to reason through a decision, or `/ideation-partner` if the problem is already clear.
- If multiple moves are equally high-value, say so and let the user choose. Don't force a single recommendation when the situation is genuinely ambiguous.

$ARGUMENTS
