---
name: strategy-partner
description: Use when you have an initiative, ticket, or brief and need to plan what design work to do — which questions to answer, what to learn, and in what order
---

## Phase 1 — Ingest

Scan `design-artifacts/` (and one level of subfolders) for existing work — sensemaking artifacts, research artifacts, thinking sessions, briefs, concepts. Read whatever input is provided.

**Strategy consumes design surfaces from a sensemaking artifact — it does not re-derive them.** Look specifically for a `*--sense.md` artifact relevant to this initiative.

**Bounce conditions:**

- **No sense artifact + thin input** — if there's no sensemaking artifact and the input is too thin to plan from (just a sentence, a vague brief, no decomposition), stop and recommend running `/sensemaking-partner` first. Do not guess at surfaces.
- **Slice is small enough to act directly** — if the sense artifact's slice is small enough that one workstream covers it, say so and recommend going straight to the appropriate next skill (`/research-partner`, `/thinking-partner`, `/ideation-partner`, or `/scoping-partner`). Do not invent additional workstreams to justify strategizing.

**Calibration:** Propose depth before probing.

- **Just go** — skip Probe; produce the workstream and Start Here in one pass, no stops
- **Standard** — full Probe → Frame → Workstream flow with stops at Probe and Workstream
- **Deep** — multi-workstream initiatives; stops after Probe, after Frame, after Workstream, and before Capture

If the user says "just go" at any point, switch to the compact path and flag assumptions.

## Phase 2 — Probe

Read the sense artifact carefully. Before framing, pressure-test what sensemaking landed on. **This is the deepest user-engagement moment in the skill — make it count.**

Lead with: *"The sense artifact frames the slice as X. Here's what I'd pressure-test before planning:"*

Then provocations from the toolkit below. **No cap on number.** Run as many as genuinely move the needle. If 5 things warrant pushback, raise 5. If 1 does, raise 1. If nothing does, say so explicitly (*"the sense artifact looks clean — proceeding to Frame"*) and skip the phase.

The rule is: **every provocation must meaningfully change what the workstream and Start Here look like.** If a provocation wouldn't change anything downstream, don't raise it.

**Don't re-raise probes the sense artifact already resolved.** Before surfacing a challenge, check the sense artifact's `Probes` section. If sensemaking already raised and resolved that challenge with the user, don't re-litigate it — assume the resolution holds and move on. Only raise it again if you have new evidence that the prior resolution was wrong.

**Toolkit** (use what fits, ignore what doesn't):

- **Slice challenge** — "The slice is X, but Y looks like it might actually be load-bearing. Revisit?"
- **Surface gap** — "These surfaces are listed, but I notice Z isn't. Was that intentional?"
- **Strategic-question challenge** — "The implied question seems to be A, but the actual decision the team needs to make is B. Which is the real driver?"
- **Stakeholder-blind-spot challenge** — "This plans for users, but I notice no consideration of [stakeholder/constraint]. Does that change the slice?"
- **Initiative challenge** — "The initiative as scoped might be solving the wrong problem. The pattern looks more like P. Worth re-framing before we plan?"
- **Sequencing challenge** — "Doing X first assumes Y is solved. Is Y solved? If not, the sequence might be wrong."

Format each probe as a numbered observation with a clear question. Make it easy for the user to respond probe-by-probe.

**Stop and wait** for the user's reactions. Their answers reshape Frame, Workstream, and Start Here.

Skip this phase only if calibration is set to "just go."

## Phase 3 — Frame

Restate the initiative in one sentence. Reflect any reframing the Probe phase produced.

**Pull the design surfaces and slice directly from the sense artifact** (with any Probe-driven adjustments). Do not re-derive them. Design surfaces live inside the sense artifact's `Decomposition` section (under "Design surface"); the slice lives in its standalone `Slice` section. Quote both, then confirm:

> "From `<sense artifact path>`, working with these surfaces: [list]. Slice: [slice]. Probe adjustments: [list, or 'none']. Confirm or adjust."

If the user adjusts, update working state. If they confirm, proceed.

Surface **1-2 strategic questions** the design work needs to answer — the through-lines whose answers would most change what you build. **Default to one question.** Two only when there's a genuine fork.

If the input still requires clarifying questions after Probe, ask 1 — only if the answer would change the plan. Do not ask questions whose answers wouldn't change anything.

**Stop and wait.**

**Not for:** decomposing a problem you don't yet understand (`/sensemaking-partner`), working through a specific decision or tradeoff (`/thinking-partner`), or breaking a chosen direction into buildable tiers (`/scoping-partner`). Strategy-partner plans *what design work to do*, not *how to do it*.

## Phase 4 — Propose workstream

**Do not produce 2-4 workstreams. Propose THE workstream that unblocks the rest.**

Pick the load-bearing workstream — the one that, once advanced, makes the others either trivial or unnecessary. Present:

- **The workstream** — name and one-sentence scope
- **Covers** — which surfaces from the sense artifact it addresses
- **Strategic question it advances** — from Phase 3
- **Why this one** — what it unblocks, what it teaches, what it lets you defer
- **Parked for later** — other potential workstreams, each with a one-line note on why they can wait

Within the proposed workstream, sequence **2-4 design actions**:

| Action | Why | Method | Unblocks |
|--------|-----|--------|----------|
| What to do | Which strategic question it advances | Partner skill when one fits, or other method (stakeholder interview, analytics review, usability test, competitive audit, etc.) | What this enables next |

Then a labeled pause:

- **A** — accept the workstream, proceed to Start Here
- **B** — different workstream — pick from the parked list
- **C** — adjust scope (smaller / bigger)
- **D** — actually need multiple parallel workstreams, not one

**Stop and wait.** This is the convergence commitment moment.

If the user picks D, expand to 2-3 workstreams with dependencies mapped. Do not default to D.

## Phase 5 — Start Here

Highlight the **1-2 highest-value first actions** within the proposed workstream — if you do nothing else, do these. State for each: what it unblocks, what risk it retires, or what decision it enables.

Flag any time-sensitive or blocking actions separately.

Note open questions that could change the plan — places where new information would reshape priorities.

**Stop and wait** for the user to confirm before saving.

## Phase 6 — Capture

Save to `design-artifacts/<descriptive-name>--strategy.md`, where `<descriptive-name>` is 2-4 hyphenated words describing the artifact's focus.

Start the file with an H1 title: `# Strategy: <title>` (e.g., `# Strategy: Onboarding Redesign`).

Structure:

- **Initiative** — 2-3 sentences on what's being planned and why
- **Source sensemaking artifact** — path reference
- **Probes** — each probe raised in Phase 2 with the user's one-line reaction. This section is load-bearing context for why the workstream ended up where it did.
- **Strategic question(s)** — the 1-2 questions driving the plan
- **Workstream** — the proposed workstream with scope, rationale, and action table
- **Parked workstreams** — other potential workstreams with one-line "why later" notes
- **Start Here** — the 1-2 highest-value first actions with rationale
- **Open questions** — unknowns that could reshape the plan

The artifact must be **self-contained** — readable without conversation context.

**Anti-pattern: "Plan everything before acting."** Strategy plans design work, not the entire initiative. Don't include build/implementation actions — those belong in scoping. Don't treat the plan as final — flag where it's most likely to pivot based on what you learn.

**Anti-pattern: "Map all possible workstreams."** Comprehensiveness enables over-design. Propose the load-bearing workstream and park the rest. If you find yourself listing 4 workstreams, stop and ask which one is load-bearing.

**Anti-pattern: "Re-derive what sensemaking already produced."** If a sense artifact exists, consume its surfaces. Don't redo decomposition work in strategy.

**Anti-pattern: "Skip Probe because the sense artifact looks clean."** Even clean-looking artifacts often miss things. If you skip Probe, you must say so explicitly ("nothing in this artifact warrants pushback") rather than silently bypassing the phase.

## Artifact Directory

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `design-artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders. Before writing, check if an artifact already exists at the target path. If it does, read it — the current run's output should reflect awareness of prior work, not blindly replace it.

## Rules

- Be direct. No preamble, no filler.
- One question per (`AskUserQuestion` or `requestUserInput`) call.
- **Probe before framing.** The Probe phase is where the user is most engaged — don't skip it unless calibration is "just go." If nothing in the sense artifact warrants a provocation, say so explicitly rather than fabricating one.
- **No cap on probes.** Run as many provocations as genuinely move the needle. The cap is on *behavior-neutral* questions, not on meaningful ones.
- If a question doesn't change what the skill does next, don't ask it.
- Strategy consumes design surfaces from sensemaking artifacts. It does not re-derive them. If no sense artifact exists and input is thin, bounce to `/sensemaking-partner`.
- Default to one workstream, not many. Propose the load-bearing one and park the rest. Expand to multiple workstreams only when the user explicitly asks (option D in Phase 4) or the slice genuinely requires parallel work.
- Default to one strategic question. Two only when there's a genuine fork.
- Every action recommends a method — partner skill when one fits, other methods when they're better. Don't force actions into skills.
- "Start Here" is mandatory. Every strategy names 1-2 highest-value first actions.
- If the slice is small enough that one workstream covers it trivially, the initiative may not need strategizing — say so and recommend going straight to the appropriate skill (`/research-partner`, `/thinking-partner`, `/ideation-partner`, or `/scoping-partner`).
- Propose; don't ask. The user's job is to react and redirect, not generate.
- Prefer labeled options (A/B/C/D) over open-ended questions in convergence phases (Workstream). Probe is allowed to be open because reactions are open-ended by nature.

$ARGUMENTS
