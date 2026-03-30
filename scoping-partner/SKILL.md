---
name: scoping-partner
description: Use when you have a chosen direction and need to break it into prioritized scope tiers
---

## Phase 1 — Understand

Read the concept, brief, wireframes, or other artifacts the user points to. Scan `design-artifacts/` (and one level of subfolders) for related context — prior sensemaking or thinking sessions, research, test results — that informs scope decisions.

Ask clarifying questions (one per `AskUserQuestion` or `requestUserInput` call, never batch). The test for each question: **would knowing this change how I'd scope this?** Stop when answers stop changing your thinking.

Areas to probe as needed — not a sequential checklist:

- **Team** — who's building this, how many people, what skills
- **Timeline** — is there a deadline, a release train, or open-ended
- **Technical unknowns** — what hasn't been built before, what needs spikes
- **What exists** — what's already built that this extends or replaces
- **Dependencies** — external teams, APIs, approvals that gate work

If the user says "just go" or similar, proceed with reasonable assumptions and flag them.

## Phase 2 — Decompose

Break the work into features or capabilities. For each:

- **What it is** — one sentence
- **What it enables** — why this matters to the user or system
- **What depends on it** — downstream features that can't start without this

Present as a flat list — don't tier yet. This is the raw material for prioritization. **Stop and wait** for the user to add, remove, or adjust items before prioritizing.

## Phase 3 — Prioritize

Sort features into tiers:

**MVP** — the minimum set that proves the core bet and is usable. The bar: if you cut any one of these, the thing doesn't work or doesn't make sense.

**Should-have** — high-value features that meaningfully improve the experience but aren't required for launch. These are the first things you'd add after MVP ships.

**Nice-to-have** — features that can wait. Explicitly name what you're deferring and why it's safe to defer.

Present the tiers clearly. For each item, include a one-line rationale for its placement — especially for items on the MVP boundary where the decision is tightest.

**Stop and wait** for the user to agree on tiers before drafting tickets. The prioritization conversation is where the real value is — tickets are the output, not the point.

## Phase 4 — Draft tickets

For each feature in MVP and Should-have tiers, produce a ticket:

- **Title** — clear, action-oriented
- **Description** — the problem this solves + the approach (2-4 sentences)
- **Acceptance criteria** — testable conditions that define done (bulleted list)
- **Tier** — MVP / Should-have / Nice-to-have
- **Dependencies** — other tickets that must complete first (by title)
- **Size** — T-shirt estimate: S (< 1 day), M (1-3 days), L (3-5 days)

Group tickets by tier. Sequence within each tier by dependencies — things that unblock other work come first.

MVP tickets should be detailed enough to start work. Should-have tickets can be lighter — enough to understand scope and effort, not implementation detail.

Nice-to-have items get a one-line entry in a deferred list, not full tickets.

Present all tickets. **Stop and wait** for feedback before saving.

## Phase 5 — Capture

Save to `design-artifacts/<descriptive-name>--scope.md`, where `<descriptive-name>` is 2-4 hyphenated words describing the artifact's focus.

Start the file with an H1 title: `# Scope: <descriptive title>` (e.g., `# Scope: Onboarding Flow MVP`).

Structure:
- **Overview** — 2-3 sentences on what's being scoped and the core bet
- **Tier breakdown** — MVP, Should-have, Nice-to-have with item lists
- **Tickets** — full ticket details, grouped by tier
- **Deferred items** — nice-to-haves with rationale for deferral
- **Open questions** — unknowns that need spikes or decisions before work starts

**Anti-pattern: "Scope the whole vision."** Scoping works on a chosen direction, not a feature wish list. If the input hasn't converged on a direction, say so — the user needs to explore and converge before scoping will be productive.

## Artifact Directory

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `design-artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders.

## Rules

- Be direct. No preamble, no filler.
- One question per (`AskUserQuestion` or `requestUserInput`) call.
- MVP is the smallest thing that works, not the smallest thing you can ship. "Works" means a user can accomplish the core task end-to-end.
- Don't pad MVP with "foundation" work that doesn't deliver user value. Infrastructure belongs in tickets, not tier justifications.
- If the source artifacts are too vague to scope concretely, say so — name what's missing (problem understanding, direction convergence, or both) rather than guessing.
- T-shirt sizes are rough signals, not commitments. Don't pretend to precision you don't have.

$ARGUMENTS
