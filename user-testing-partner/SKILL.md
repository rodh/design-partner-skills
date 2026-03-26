---
name: user-testing-partner
description: Use when you have a design — wireframes, sketches, screenshots, or a description — and need to validate it against realistic simulated user behavior
---

## Phase 1 — Understand what we're testing

Accept any design artifact — wireframe files the user points to, screenshots, inline ASCII, or verbal descriptions.

Ask clarifying questions to understand what needs testing. The test is: **would knowing this change the personas I generate or what I look for in the walkthrough?**

Questions focus on:
- What's the core task this design supports?
- Specific concerns or hypotheses to test?
- What kind of users will use this?

One question per (`AskUserQuestion` or `requestUserInput`) call. Never batch.

Stop when you have enough to generate personas and run a walkthrough.

## Phase 2 — Personas

If the user points to an existing personas file, read and use it. Briefly list the personas so the user can verify they're still appropriate.

If no personas file exists, generate from whatever context is available — the design artifact, user's description, conversation history.

**Default: 2 personas.** Add a 3rd only if the product serves distinct user segments with conflicting needs (e.g., creator vs consumer, admin vs end-user).

**Persona format:**

```
## {Name}
- **Role:** {job title or archetype}
- **Key trait:** {one behavioral trait, e.g., "skims before committing"}
- **Orientation:** {trust-first or speed-first}
- **Current workflow:** {what they do today without this product}
- **Usage context:** {when/where/how often they'd use this}
```

Save to `personas-<slug>.md` (derive slug from the design being tested).

**Stop and wait** for approval before proceeding to walkthrough.

On subsequent runs with the same design, reuse the existing personas file unless the user requests changes.

## Phase 3 — Adaptive screens

Before testing, scan the design for adaptive elements (personalized content, role-based views, conditional copy). If found:

1. **Construct per-persona views.** Describe what each persona would actually see — their topics, copy variant, data state. Don't test all personas against the single static wireframe.
2. **Label findings as structure or content.** Structure = layout, hierarchy, navigation (same for all). Content = copy, topics, curation (varies per user).
3. **Flag untested personalization.** If adaptive elements exist but per-persona variants aren't specified, say so.

## Phase 4 — Test

Mentally walk through each screen per persona — first impressions, task attempts, friction, what they'd say. This walkthrough is your raw material; do not output it. Synthesize into these sections:

### Action items

Three subsections (omit any that would be empty). Number items sequentially as AI-{n} — stable IDs across iterations.

Each item gets 1–2 evidence bullets. Format:
```
- **AI-{n}.** Brief description — why it matters.
  - *Evidence:* Persona (trait) observed behavior or failure.
```

- **Resolved from previous test:** Items the current design addressed. Preserve original AI-{n} IDs. (Empty on first run.)
- **Remaining issues:** Items still present from prior tests. Preserve IDs, re-state why each matters. (Empty on first run.)
- **New findings:** Issues found in this test. On first run, all items go here. On subsequent runs, continue numbering from max prior ID + 1.

### What works

Short list of design positives grounded in persona behavior. Format:
```
- **Short label.** What works and which persona behavior confirms it.
```

### Consensus issues

Problems multiple personas hit. Numbered list with evidence. Below each, an indented sub-bullet: ***Fix now*** or ***Defer*** leading the line, with short rationale.

### Highest-leverage fix

One bolded recommendation with 2–4 bullets on what it accomplishes. If the user stated a specific hypothesis during Phase 1, report whether walkthroughs validated or contradicted it.

### Adoption

One line per persona:
```
- **Persona name:** Adopts / Hesitant / Unlikely — reason tied to their current workflow.
```

**Saving:** Save to `test-results-<slug>.md`. Start with `# Test Results: <descriptive title>`. If a previous file with the same slug exists, read it first — carry forward resolved/remaining items, continue AI-{n} numbering. Also save `personas-<slug>.md` if generated. **Stop and wait** for approval before saving.

## Rules

- Be direct. No preamble, no filler.
- Every observation grounded in a specific persona's behavior and the specific design being tested.
- If the design is too vague to simulate a walkthrough, say so and ask for specifics.
- Don't soften findings.
- One question per (`AskUserQuestion` or `requestUserInput`) call.

$ARGUMENTS
