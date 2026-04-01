---
name: testing-partner
description: Use when you have a wireframe, flow, or prototype and want to simulate how real users would navigate it — where they complete tasks, where they struggle, and where they drop off
---

## 1. Ingest

Read the flow or wireframe to test. This can be provided as `$ARGUMENTS` (a file path, pasted content, or description) or identified from conversation context.

Scan `design-artifacts/` and one level of subfolders for upstream artifacts that establish context — briefs (`*--brief.md`), sensemaking (`*--sense.md`), strategy (`*--strategy.md`), scope (`*--scope.md`), concepts (`*--concept.md`), personas (`*--personas.md`), and prior test results (`*--testing.md`). Read whatever helps you understand who this flow is for and what it should accomplish.

Identify from the artifact:

- **The flow** — the sequence of screens, steps, or states the user moves through
- **The primary task** — what a user is trying to accomplish (e.g., "sign up for a new account", "change billing info")

If the flow contains multiple distinct tasks, list them and ask which to test. If the task isn't discernible from the artifact, ask.

If the flow is too abstract to walk through step by step (no clear screens, no clear states), say so — suggest `/ideation-partner` or `/scoping-partner` to develop it further before testing.

**Not for:** evaluating concept viability before a flow exists (`/thinking-partner`), generating alternative approaches (`/ideation-partner`), or assessing strategy (`/strategy-partner`). Testing-partner tests task completion through a defined flow.

If the flow and task are clear, proceed directly to Phase 2 without stopping.

## 2. Personas

Check `design-artifacts/` for an existing `*--personas.md`. If found, read and use it.

If not found, generate 2 personas from the upstream artifacts and the flow itself. Add a third only if the user base has genuinely distinct segments that would navigate the flow differently (e.g., power user vs. first-timer).

**Persona format:**

```
## {Name}
- **Role:** {job title or archetype}
- **Tech comfort:** {low / moderate / high}
- **Goal:** {what they're trying to accomplish in this flow}
- **Behavior:** {one navigation trait — e.g., "reads every label before acting" or "clicks the most prominent element immediately"}
```

Present personas. **Stop and wait** for confirmation before proceeding. If the user says "just go" or similar, move on immediately with the personas as presented.

## 3. Test

Simulate each persona walking through the flow step by step. For each persona, reason through what they would do at each screen or state — what they'd tap, what they'd read, what they'd skip, where they'd hesitate, what they'd expect to happen. This walkthrough is your raw material; do not output it unless the user asks to see it.

Synthesize into:

### Findings

Number items sequentially as `UT-{n}` — stable IDs for tracking across iterations.

Each finding gets a severity (blocker / friction / minor) and evidence grounded in a specific persona's behavior at a specific step:

```
- **UT-{n}.** Brief description — severity.
  - *Evidence:* {Persona} at {step/screen} — what they did and what went wrong.
```

Organize into three subsections (omit any that would be empty):

- **Resolved from prior testing:** Items addressed since the last test. Preserve original `UT-{n}` IDs. (Empty on first run.)
- **Remaining issues:** Items still present from prior tests. Preserve IDs. (Empty on first run.)
- **New findings:** Issues found in this round. On first run, all items go here. On subsequent runs, continue numbering from max prior ID + 1. If the flow was substantially redesigned, mark all prior items as resolved and start fresh.

### What works

Short list of what the flow does well, grounded in persona behavior:

```
- **Short label.** What works and which persona's behavior confirms it.
```

### Highest-impact fix

One bolded recommendation — the single change that would unblock the most personas or remove the most friction. 2-3 bullets on what it accomplishes. If the problem is upstream (the flow solves the wrong problem, the information architecture is off), say so and name the relevant skill (`/thinking-partner`, `/strategy-partner`).

**Self-review:** Before presenting, check that every finding names a specific persona at a specific step. Remove any that don't.

Present the results. **Stop and wait** before proceeding.

## 4. Save

Results stay in chat by default. After presenting, offer:

- **(A) Done** — results stay in chat only
- **(B) Save to design-artifacts/** — saves as a standalone artifact
- **(C) Append to source file** — appends a findings summary to the wireframe/flow file that was tested
- **(D) Both B and C**

**If A:** End.

**If B:** Save to `design-artifacts/<descriptive-name>--testing.md`, where `<descriptive-name>` is 2-4 hyphenated words describing the flow's focus (e.g., `design-artifacts/onboarding-flow--testing.md`). Start the file with `# Testing: <title>`. Include the Phase 3 output (Findings, What works, Highest-impact fix) plus: Flow tested (with reference to source), Task, Personas, and Open threads. The artifact must be **self-contained** — readable without conversation context.

**If C:** Append to the source file under a horizontal rule:

```
---

## Simulated testing — {YYYY-MM-DD}

### Findings
- **UT-1.** ...
- **UT-2.** ...

### Highest-impact fix
...
```

Keep the appended section compressed — session details live in chat, the append is a summary for future reference when reading the flow.

**If D:** Do both B and C.

**Anti-pattern: "Generic usability heuristics."** Every finding must come from a specific persona getting stuck at a specific step. "Consider adding a progress indicator" is not a finding. "Alex (clicks the most prominent element) tapped Continue at step 3 expecting a confirmation screen but landed on payment with no way back" is a finding.

**Anti-pattern: "Testing the concept, not the flow."** This skill tests task completion through a specific sequence of steps. If the flow is too abstract to walk through step by step (no clear screens, no clear states), say so — the artifact needs more definition before it can be tested.

**Anti-pattern: "Inventing screens that aren't there."** If the wireframe has gaps (no error state, no empty state, no edge case), flag the missing screen as a finding — do not fabricate what it would look like and test the fabrication.

## Artifact Directory

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `design-artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders. Before writing, check if an artifact already exists at the target path. If it does, read it — the current run's output should reflect awareness of prior work, not blindly replace it.

## Rules

- Be direct. No preamble, no filler.
- Severity matters. Blockers first, friction second, minor last.
- `UT-{n}` IDs are stable across iterations. Never renumber resolved or remaining items.
- Results print in chat by default. Only save when the user asks.
- Artifacts must be self-contained. Someone reading the file with no conversation context should understand the test results.
- When the source flow has multiple tasks, test one at a time. Offer to test additional tasks after the first round completes.
- One question per call. Never batch multiple questions.
- Prefer labeled options (A/B/C) over open-ended questions when the answer space is bounded.

$ARGUMENTS
