---
name: planning-partner
description: Use when you have a scope or sense artifact with a chosen aspect (slice or parked item) and need an execution plan — what to do, in what order, with what method, and what each step gives you. Produces a lean, dispatchable plan, not a comprehensive strategy.
---

## Phase 1 — Intake

Ingest `$ARGUMENTS`. Scan `design-artifacts/` (and one level of subfolders) for an existing scope or sense artifact relevant to this work — `*--scope.md` or `*--sense.md`. Read it.

**Planning-partner consumes a scope or sense artifact and a chosen aspect — it does not re-derive them.**

**Bounce conditions:**

- **No scope/sense artifact + thin input** — if there's no scoping or sensemaking artifact and the input is too thin to plan from (a sentence, a vague brief, no decomposition), stop and recommend running `/scoping-partner` first. Do not guess at execution plans for problems that haven't been decomposed.
- **Slice is small enough to act directly** — if the slice from the artifact is small enough that it doesn't need a multi-step plan, say so and recommend going straight to the appropriate skill (`/research-partner`, `/thinking-partner`, or `/ideation-partner`). Don't invent steps to justify planning.

**Identify which aspect to plan.** Default: the load-bearing slice from the scope/sense artifact. If the user wants to plan a different aspect (e.g., a parked item), use that.

**Confirm what was inherited from scope/sense.** Before proceeding to Probe, quote the chosen aspect from the artifact and confirm with the user:

> *"From `<artifact-path>`, planning execution for: '<chosen aspect, quoted verbatim>'. Strategic question (inherited or implied): '<question>'. Pressure-tests already settled: [list, or 'none']. Confirm or adjust."*

**Stop and wait for confirmation** before moving to Probe. If the user adjusts, update working state and re-confirm.

**Calibration:** Propose depth before probing.

- **Just go** — skip Probe; produce the plan in one pass and flag any execution assumptions inline as comments
- **Standard** — full Probe → Draft flow with stops at Probe and Draft

If the user says "just go" at any point, switch to the compact path.

## Phase 2 — Probe

Read the chosen aspect from the scope/sense artifact carefully. Read the parked items and pressure-tests already settled. Before drafting steps, pressure-test the *execution assumptions* for this aspect — sequencing, method fit, hidden plan dependencies. **This is the deepest user-engagement moment in the skill.**

**Lead with:** *"For executing this aspect, here's what I'd pressure-test before drafting steps:"*

**Probes are flexible, not a fixed checklist.** Read the specific aspect being planned and produce probes specific to *that* aspect. The toolkit below is inspiration ("execution mistakes usually come from these directions"), not a script.

**Toolkit (use what fits, ignore what doesn't):**

- **Sequence challenge** — *"The natural order is A → B → C, but B might depend on C's output. Reorder?"*
- **Method challenge** — *"You'd reach for `/thinking-partner` here, but this is empirical — needs real data, not analysis. Wrong method?"*
- **Hidden plan assumption** — *"This plan assumes X is settled. Is X actually settled, or is finding out X the real first step?"*
- **Stakeholder-blind-spot challenge** — *"Step X depends on someone outside this immediate work — eng owner, design lead, stakeholder, external decision-maker. Is the time real, or does it bake in assumed availability?"*
- **Granularity** — usually fix-in-drafting, not probe-worthy. Cover in Draft instead.

**Rules — these are the constraint, not the toolkit:**

1. **Every probe must change *what's in the plan*.** If a probe's only effect is "add a note next to a step," it's a Worth-flagging item, not a probe.
2. **Cap: 1–3 probes per run.** Sensemaking has no cap because sense probes can rewrite the problem. Planning probes can only rewrite the plan — smaller surface, smaller cap.
3. **Raise highest-stakes first.** One answer can collapse the rest.
4. **Don't re-litigate the slice.** Probes are about *how* to execute the chosen aspect, not *whether* to execute it. If a probe's worst-case answer would invalidate the slice itself, **bounce back to sense** rather than handle it in planning-partner.
5. **If nothing warrants pushback, say so explicitly** — *"the plan looks straightforward, no execution assumptions worth challenging. Drafting steps."* Don't fabricate.

**Diagnostic for probe scope:** *"If the answer is the worst case, does the slice still hold?"* Yes → execution probe (handle here). No → strategy probe (escalate to sense).

**Don't re-raise probes the upstream artifact already resolved.** Check the `Pressure-tested` section first. If scoping/sensemaking already settled an assumption, assume it holds.

Ask probes **one at a time** via `AskUserQuestion` (Claude Code) or `requestUserInput` (Codex). Wait for each answer before deciding whether the next probe still applies — sometimes one answer collapses what would have been the next probe.

Skip this phase only if calibration is set to "just go."

## Phase 3 — Draft

Now that probes have reshaped the execution understanding, draft the plan in **stem format**. The plan is purely additive over the scope/sense doc — no restatement of input, slice, parked items, or original probes.

### Format

```markdown
# Plan: <slice name>
*From [`<artifact-path>`](./<artifact-path>)*

**Answering:** <one sentence — the strategic question this plan answers, inherited or sharpened from sense>

**Steps:**

1. **<verb-led step name>** — <method (skill or other)> · ~<time>
   *After this:* <decision-relevant outcome — what you'll know, decide, or be able to act on>

2. **<step>** — <method> · ~<time>
   *After this:* <outcome>

3. ... *(typically 3–6 steps)*

**Watch out:** <one paragraph — the single load-bearing piece of hidden complexity. ONE per plan, not per step.>

**Worth flagging:** <open questions, dependencies, stakeholder concerns. Optional — omit if nothing.>
```

### Field rules

- **Answering** — one sentence. The strategic question, inherited from sense or sharpened during Probe.
- **Steps** — verb-led, sequenced, `method · time`. 3–6 typical. **More than 6 = the slice is too big or you're re-decomposing.** Compress or escalate to sense.
- **After this:** — *decision-relevant outcome*, NOT bookkeeping. *"You'll know X"* / *"You'll have decided Y"* / *"You'll be able to commit to Z."* The user reads this to decide whether to execute the step or skip it. **Never** *"you'll have a file."*
- **Watch out** — single load-bearing piece of hidden complexity. **One per plan, not per step.** Multiple Watch outs read as performative — pick the one that most changes how the plan gets executed.
- **Worth flagging** — quiet items the plan needs to carry but don't change a step. Stakeholder questions, dependencies on other slices, scope mismatches. Optional — omit if nothing.

### Hard constraints

- **No nested decomposition.** No "execution aspects" as headers. Steps are flat.
- **No restatement of the upstream artifact.** No Input, Slice, Parked, or Pressure-tested sections. The plan is purely additive — what's NEW about how we're going to execute this aspect.
- **No bookkeeping metadata per step.** Method + time is the cap. No output artifact names per step, no inline tags, no block markers.
- **Word budget: ~150–350 words for most plans.** Past ~400 it starts feeling heavy — compress.

**Stop and wait** for the user to confirm before saving.

## Phase 4 — Save

Save to `design-artifacts/<descriptive-name>--plan.md`, where `<descriptive-name>` is 2–4 hyphenated words describing the slice the plan executes.

The artifact must be **purely additive** over the scope/sense doc — readable as a continuation, not a replacement. A future reader should be able to read the upstream artifact, then the plan, with no overlap and no gaps.

**Anti-patterns:**

- **"Re-derive what scoping/sensemaking already produced."** If an upstream artifact exists, consume the slice and parked items from it. Don't redo decomposition work in planning.
- **"List every possible step."** Comprehensive plans are over-design. 3–6 steps is the cap. If you have more, the slice is too big or you're re-decomposing — escalate to sense.
- **"One Watch out per step."** Reading multiple Watch outs in a row is exhausting. Pick the one that matters most.
- **"Probes for everything."** 1–3 probes is the cap. If more than 3 things in the plan need pressure-testing, the aspect was probably wrongly picked or sense skipped something.
- **"Skip Probe because the slice looks clean."** Even clean-looking slices often hide execution assumptions. If you skip Probe, you must say so explicitly ("nothing in this plan warrants pushback") rather than silently bypassing.

## Artifact Directory

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `design-artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders. Before writing, check if a plan artifact already exists at the target path. If it does, read it — the current run's output should reflect awareness of prior work, not blindly replace it.

## Rules

- Be direct. No preamble, no filler.
- **One question per call.** Any question to the user — probes, clarifications — goes through `AskUserQuestion` (Claude Code) or `requestUserInput` (Codex), one at a time. Never batch questions.
- **Probe before drafting.** The Probe phase is where the user is most engaged — don't skip it unless calibration is "just go." If nothing in the plan warrants a probe, say so explicitly rather than fabricating one.
- **Probes are flexible, not a fixed checklist.** Read the specific plan and produce probes specific to it. The toolkit categories are inspiration, not a script.
- **Cap probes at 1–3.** If more than 3 things in the plan need pressure-testing, something is wrong upstream — escalate to sense.
- **Don't re-litigate the slice.** Trust what sense settled. Strategy concerns escalate back to sense; only execution concerns belong here.
- **Default to fewer steps, not more.** 3–6 steps is the typical range. More than 6 = re-decomposing or the slice is too big.
- **Each step's *After this:* line must be decision-relevant.** Not "you'll have a file" — *"you'll know X"* / *"you'll have decided Y."*
- **One Watch out per plan.** The single load-bearing hidden complexity. Multiple watch-outs read as performative.
- **No restatement of upstream artifact.** The plan is additive, not standalone.
- Planning consumes a scope/sense artifact's chosen aspect. If no upstream artifact exists and input is thin, bounce to `/scoping-partner`.
- If the chosen aspect is small enough to act on directly, recommend the appropriate single skill (`/research-partner`, `/thinking-partner`, `/ideation-partner`) and don't draft a multi-step plan.
- Artifacts must be purely additive over the upstream doc — readable as a continuation, not a replacement.

$ARGUMENTS
