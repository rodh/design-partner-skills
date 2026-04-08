---
name: sensemaking-partner
description: Use when you need to build structured understanding from a ticket, task, or project context — what the parts are, where complexity hides, and what level of effort each part warrants
---

## 1. Scope

Ingest context from `$ARGUMENTS` — tickets, docs, task descriptions, conversation threads, flows. Scan CWD for related code, docs, existing `design-artifacts/**/*--sense.md` artifacts, `design-artifacts/**/*--thinking.md` sessions, `design-artifacts/**/*--research.md` artifacts, plans, and recent commits. Read what's relevant — don't deep-read everything. If a prior artifact already covers this, surface it instead of re-decomposing.

Classify:

- **Specific artifact understanding** — a ticket, task, or defined piece of work that needs decomposition.
- **Broader project/domain understanding** — mapping a larger space to figure out what's going on.

**Calibration:** Propose depth before probing.

- **Just go** — user already knows the shape; skip Probe, produce a compact decomposition and slice proposal in one pass, no stops
- **Standard** — full Probe → Decompose → Slice flow with stops at Probe and Slice
- **Deep** — broader understanding cases; stops after Scope, after Probe, after Decompose, and after Slice

If the user says "just go" at any point, switch to the compact path and flag any assumptions.

For **broader understanding**: present the scope (what's in, what's out) and **stop — wait for user confirmation** before proceeding to Probe.

For **specific artifact**: proceed directly to Probe with no stop.

## 2. Probe

Read the input carefully. Before decomposing, surface the observations the user should react to. **This is the deepest user-engagement moment in the skill — make it count.**

Lead with: *"Here's what I'm reading this as, and what I'd pressure-test:"*

Then provocations from the toolkit below. **No cap on number.** Run as many as genuinely move the needle — if 5 things in the input warrant pushback, raise 5. If 1 does, raise 1. If nothing does, say so explicitly (*"the framing looks clean to me — proceeding to decompose"*) and skip the phase.

The rule is: **every provocation must meaningfully change what the decomposition and slice look like.** If a provocation wouldn't change anything downstream, don't raise it.

**Toolkit** (use what fits, ignore what doesn't):

- **Framing challenge** — "You called this X but the ticket reads more like Y. Which is it?"
- **Scope challenge** — "This ticket says A, but I notice B is implicated. Is B in scope, or are we deferring it?"
- **Missing-piece challenge** — "Nothing here addresses Z, which I'd expect for this kind of work. Intentional or oversight?"
- **Ticket-expansion challenge** — "This ticket might be too narrow. The underlying problem looks like W, which would change what's worth building. Expand or stay narrow?"
- **Hidden-assumption challenge** — "This only makes sense if you assume X. Is X actually true here?"
- **Wrong-ticket challenge** — "I think this is the wrong cut of the problem. The real ask might be P. Worth re-scoping?"

Format each probe as a numbered observation with a clear question. Make it easy for the user to respond probe-by-probe.

**Stop and wait** for the user's reactions. Their answers reshape everything downstream — Decompose and Slice both run on the post-Probe understanding.

Skip this phase only if calibration is set to "just go."

## 3. Decompose

Now that probes have reshaped the understanding, decompose the (possibly revised) problem.

Four-part analysis. **Default toward fewer items, not more.** Aim for 2-3 design surfaces, not 5-6. Go bigger only when the problem genuinely warrants it — and say so explicitly when you do.

1. **Breakdown** — decompose the problem into constituent parts, name each clearly
2. **Landscape** — what exists already, what's new, what's uncertain
3. **Design surface** — identify which parts carry design effort (UI, interaction patterns, information architecture, data modeling, API surface, etc.). Call out where design complexity hides — the parts that look simple but require real design thinking. Rate each: no design needed / light design / significant design effort. **Cap at 2-3 by default.**
4. **Effort assessment** — overall level of engagement each part warrants (light touch vs. deep dive), informed by the design surface analysis

**Over-design check:** Before moving to the slice proposal, ask yourself — is this decomposition the smallest understanding needed to design effectively, or is it mapping the whole space? If it's the latter, compress.

No stop here. Proceed directly to the slice proposal.

## 4. Propose slice

**Do not ask the user what the smallest slice is. Propose it.**

Pick the **load-bearing** part from the decomposition — the one whose answer most changes what the rest become. Present:

- **The slice** — the one part to focus on, named clearly
- **Why this one** — what it unblocks, what it teaches, what it lets you defer
- **Parked for later** — the other parts, each with a one-line note on why they can wait

Then a labeled pause:

- **A** — accept the slice, proceed
- **B** — different slice — pick from the parked list
- **C** — the slice is too small / too big — adjust
- **D** — actually need the comprehensive version, not a slice

**Stop and wait** for the user's reaction. This is the convergence commitment moment — do not skip it unless calibration was set to "just go."

## 5. Synthesize

Now that the slice is locked in, present a scoped problem statement that reflects the slice (not the full decomposition). The statement should be tight enough to act on.

Recommend **one** next move based on the slice — not a menu. Name the skill or action explicitly:

- Planning what design work the slice implies (`/strategy-partner` if available — only if the slice is big enough to warrant a strategic plan)
- Thinking through a decision or tradeoff inside the slice (`/thinking-partner`)
- Investigating a specific unknown (`/research-partner`)
- Exploring solution directions for the slice (`/ideation-partner`)
- Breaking the slice into prioritized tiers (`/scoping-partner`)

If the slice is small enough to just go — say so. Don't recommend a downstream skill just because one fits.

**Stop and wait** for the user to confirm before saving.

## 6. Save

Save to `design-artifacts/<descriptive-name>--sense.md` with:

- H1 title: `# Sensemaking: <title>` summarizing what was decomposed
- Date
- **Question/Context** — the original ticket, task, or domain being understood
- **Probes** — each probe raised in Phase 2 with the user's one-line reaction. This section is load-bearing context for why the slice ended up where it did.
- **Decomposition** — breakdown, landscape, design surface, effort assessment (compressed, post-Probe)
- **Slice** — the load-bearing part chosen, with rationale
- **Parked** — the other parts with one-line "why later" notes each
- **Problem Statement** — scoped to the slice
- **Next Move** — the single recommended next action
- **Open Threads** — anything surfaced but not resolved

The artifact must be **self-contained** — readable without conversation context.

**No Act phase.** Sensemaking produces understanding; downstream skills produce action.

**Anti-pattern: "I already understand this."** The temptation to skip Probe and decomposition is strongest on tasks that look straightforward. Those are exactly where hidden design complexity and unstated assumptions do the most damage.

**Anti-pattern: "Map the whole space."** Comprehensiveness enables over-design. The job is to find the load-bearing slice and propose it — not to produce a complete map for the user to choose from.

**Anti-pattern: "Skip Probe because the input looks clean."** Even clean-looking tickets often hide framing assumptions. If you skip Probe, you must say so explicitly ("nothing in this input warrants pushback") rather than silently bypassing the phase.

## Artifact Directory

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `design-artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders. Before writing, check if an artifact already exists at the target path. If it does, read it — the current run's output should reflect awareness of prior work, not blindly replace it.

## Rules

- Be direct. No preamble, no filler. Labeled bullets for discrete items, prose for narrative.
- Quote sources, don't summarize — the user needs to see exactly what you're referencing.
- Steel-man all positions. Don't lead the user toward a predetermined answer.
- **Probe before decomposing.** The Probe phase is where the user is most engaged — don't skip it unless calibration is "just go." If nothing in the input warrants a provocation, say so explicitly rather than fabricating one.
- **No cap on probes.** Run as many provocations as genuinely move the needle. The cap is on *behavior-neutral* questions, not on meaningful ones.
- **Default toward fewer items in decomposition, not more.** 2-3 design surfaces, not 5-6. Go bigger only when the problem genuinely warrants it — and say so explicitly.
- **Propose the slice; don't ask the user what it should be.** Their job is to react and redirect, not generate.
- **One next-move recommendation, not a menu.** The skill has a point of view about what comes next.
- If a question doesn't change what the skill does next, don't ask it.
- Prefer labeled options (A/B/C) over open-ended questions in convergence phases (Slice, Synthesize). Probe is allowed to be open because reactions are open-ended by nature.
- If decomposition reveals that research is needed before understanding is possible, say so. Don't fake understanding with shallow analysis.
- Artifacts must be self-contained. Someone reading the file with no conversation context should understand the probes, decomposition, slice, and rationale.

$ARGUMENTS
