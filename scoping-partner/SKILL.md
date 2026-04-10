---
name: scoping-partner
description: Use when you have raw project context — PRDs, tickets, Slack threads, wireframes, screenshots, or verbal dumps — and need to understand the design problem before starting work
---

# Scoping Partner

## Overview

Turns raw context into structured design understanding, then converges on the load-bearing slice. Core principle: **probe the framing before decomposing, then propose what to work on first — don't map the whole space and leave the user to pick.**

## When to Use

- User drops raw context (ticket, PRD, Slack thread, screenshot, verbal dump) and needs to understand the design problem
- User asks "what should I design for this?" or "break this down"
- Kicking off design work where problem, users, and surface aren't yet aligned
- Need to figure out where complexity hides and what level of effort each part warrants

**When NOT to use:**
- Single focused question — use thinking-partner
- Already have a slice and need execution steps — use planning-partner
- Exploring solution directions — use ideation-partner
- Investigating a specific unknown — use research-partner

## Workflow

```dot
digraph scoping_flow {
    "Parse input" [shape=box];
    "Sufficient context?" [shape=diamond];
    "User opted in?" [shape=diamond];
    "Ask ONE question" [shape=box];
    "Probe framing" [shape=box];
    "Produce sections" [shape=box];
    "Propose slice" [shape=box];
    "Save" [shape=doublecircle];

    "Parse input" -> "Sufficient context?";
    "Sufficient context?" -> "Probe framing" [label="yes"];
    "Sufficient context?" -> "User opted in?" [label="no"];
    "User opted in?" -> "Probe framing" [label="yes (with warning)"];
    "User opted in?" -> "Ask ONE question" [label="no"];
    "Ask ONE question" -> "Sufficient context?";
    "Probe framing" -> "Produce sections";
    "Produce sections" -> "Propose slice";
    "Propose slice" -> "Save";
}
```

Create one task per phase; complete in order:

### Phase 1 — Parse & Gate

Extract what's stated. No interpretation yet. Evaluate against four sufficiency dimensions:

- **Problem clarity** — What's broken, missing, or changing, and why now?
- **Design intent** — Why is it being built and what success looks like?
- **User signal** — Who is affected and what are they trying to do?
- **Design surface specificity** — Can you name at least one concrete screen, flow, component, or touchpoint?

If weak on any dimension, ask **one question per turn**. Never narrate your assessment — just ask. Include an escape hatch ("or just say go and I'll proceed with assumptions flagged").

Accept any format. Don't ask for reformatting. Length ≠ clarity — a 500-word brief with seven bullets can still fail all four dimensions.

**Calibration:** Propose depth before probing.

- **Just go** — skip Probe, produce above-the-divider sections and slice in one pass, flag assumptions inline. Omit on-demand sections unless context is rich enough to populate them without guessing.
- **Standard** — full Probe → Sections → Slice flow with stops at Probe and Slice

### Phase 2 — Probe

Before decomposing, challenge the framing. **This is the deepest user-engagement moment — make it count.**

Lead with: *"Here's what I'm reading this as, and what I'd pressure-test:"*

**Toolkit** (use what fits, ignore what doesn't):

- **Framing challenge** — "You called this X but it reads more like Y. Which is it?"
- **Scope challenge** — "This says A, but B is implicated. Is B in scope or deferred?"
- **Missing-piece challenge** — "Nothing addresses Z, which I'd expect here. Intentional?"
- **Ticket-expansion challenge** — "This might be too narrow. The underlying problem looks like W."
- **Hidden-assumption challenge** — "This only works if X is true. Is it?"
- **Wrong-ticket challenge** — "The real ask might be P. Worth re-scoping?"

**No cap on probes.** Raise every one that would meaningfully change the decomposition or slice. If nothing warrants pushback, say so explicitly and proceed.

Ask probes **one at a time** via `AskUserQuestion`. Wait for each answer before deciding if the next probe still applies — one answer can collapse two probes into none.

Skip only if calibration is "just go."

### Phase 3 — Produce Sections

Produce the scoping artifact using the template below. Tag every inference `[assumed]` / `[inferred]` / `[implied]`. Default toward fewer items — 2-3 design surfaces, not 5-6.

**Above the divider** (always-read): Problem & Why Now, Design Surfaces, Strategic Questions, Slice, Next, Pressure-tested.

**Below the divider** (on-demand depth): Users & Jobs, Gaps & Clarifications, Effort Shape, Business Outcome & Metrics.

### Phase 4 — Propose Slice

**Do not ask the user what to focus on. Propose it.**

Pick the **load-bearing** part from the design surfaces — the one whose answer most changes what the rest become. Present:

- **The slice** — named clearly, one sentence
- **Why this one** — what it unblocks, what it teaches, what it defers
- **Parked** — other parts, each with a one-line note on why they wait

Then ask via `AskUserQuestion` with labeled options:

- **A** — accept the slice, proceed
- **B** — different slice (pick from parked)
- **C** — adjust size (too big / too small)
- **D** — need the comprehensive version, not a slice

### Phase 5 — Next & Save

Recommend **one** next move — not a menu:

- `/planning-partner` — if slice warrants a multi-step execution plan
- `/thinking-partner` — if there's a decision or tradeoff inside the slice
- `/research-partner` — if there's a specific unknown to investigate
- `/ideation-partner` — if you need to explore solution directions

If the slice is small enough to just go, say so.

**Stop and wait** for user confirmation before saving.

Save to `design-artifacts/<descriptive-name>--scope.md`. Format:

```markdown
# Scope: <short title>
*<YYYY-MM-DD>*

## Problem & Why Now
<!-- Narrative prose, 1-3 paragraphs. Synthesize; don't restate inputs. -->

## Design Surfaces
<!-- Each: name · kind of design work · weight (no design / light / significant). Mark load-bearing. Cap 2-3. -->
- **<Surface>** — <kind of design work> · **<weight>** *(load-bearing)*
- **<Surface>** — <kind of design work> · <weight>

## Strategic Questions
<!-- 2-4 questions whose answers most reshape scope. One sentence each + why it matters. -->
1. **<question>?** <why it matters>
2. **<question>?** <why it matters>

## Slice
**<one sentence — the load-bearing part>**

**Why:** <1-3 sentences — what makes this load-bearing, what it unblocks, what it defers>

**Parked:**
- <part> — <why later>

## Next
<one action — name the skill or doable verb, not a menu>

**Pressure-tested:**
- <assumption challenged → outcome only>
*(hard cap 3 bullets, omit if nothing challenged)*

---
*On-demand depth*

## Users & Jobs
<!-- JTBD format. Tag inferred users [inferred]. -->
| User | Job |
|---|---|
| <user> | **When** <situation> **I want to** <motivation> **so I can** <outcome> |

## Gaps & Clarifications
<!-- One gap per row. If user signaled completeness, convert to assumptions. -->
| Gap | Impact | Default assumption |
|---|---|---|
| <gap> | <impact> | <assumption> |

## Effort Shape
<!-- Not a plan. Shape only: surfaces, sequencing, rough size (afternoon/multi-day/multi-week), external dependencies. -->
- <number of surfaces, sequencing, rough size, dependencies>

## Business Outcome & Metrics
<!-- Propose 2-4 if inputs don't specify; mark [assumed]. -->
| Metric | What it measures |
|---|---|
| <metric> | <what it measures> |
```

**Word budget:**
- Simple problem: ~200-300 words (above the divider)
- Complex problem: ~400-600 words (full artifact)
- Past ~600: compress or cut on-demand sections

## Rationalization Table

| Excuse | Reality |
|--------|---------|
| "Input is long — that's enough." | Length ≠ clarity. Check the four dimensions. |
| "I'll ask two — they're related." | One question. Reassess, then ask. |
| "Let me explain what I'm evaluating." | Never narrate. Just ask. |
| "I already understand this." | Strongest temptation on clean-looking inputs. Probe anyway. |
| "Map the whole space first." | Comprehensiveness enables over-design. Find the slice. |
| "Skip Probe — input looks clean." | Clean tickets hide framing assumptions. Say so explicitly if skipping. |
| "Adding one nice-to-have surface." | No scope inflation. Implied = necessary, not aspirational. |
| "I'll organize by role." | Organize by what you need to learn, not job title. |

## Red Flags — STOP and reassess

- More than one question mark in your response
- About to narrate your sufficiency assessment
- Producing sections without having probed (unless "just go")
- Adding a surface "because it would be nice"
- Letting the user pick the slice from a comprehensive map
- Skipping Gaps because input seemed strong

## Artifact Directory

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. Check `design-artifacts/` and one level of subfolders for existing artifacts. Before writing, check if an artifact already exists at the target path — reflect awareness of prior work, don't blindly replace it.

## Rules

- Be direct. No preamble, no filler.
- **One question per call** via `AskUserQuestion`. Never batch.
- Quote sources, don't summarize. Steel-man all positions.
- Labeled options (A/B/C) in convergence phases. Probes can be open-ended.
- If decomposition reveals research is needed first, say so.
- No scope inflation — implied surfaces must be necessary, not aspirational.

$ARGUMENTS
