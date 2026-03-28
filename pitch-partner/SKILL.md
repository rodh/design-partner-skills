---
name: pitch-partner
description: Use when you need to communicate design work to a specific audience — stakeholders, teammates, clients, or cross-functional partners
---

## Phase 1 — Gather

Read the artifacts the user points to — session notes, briefs, concepts, wireframes, scope docs. Scan `artifacts/` (and one level of subfolders) for related context that adds depth.

Then ask (one question per `AskUserQuestion` or `requestUserInput` call, never batch):

1. **What decision are you asking them to make?** Or are you informing, not asking? This changes the entire framing — a request for approval needs different emphasis than a status update.
2. **Who's the audience?** — Leadership, a teammate who'll build it, a cross-functional partner, a client? Their role shapes what to emphasize.
3. **What format?** Offer options based on the situation:
   - **One-pager** — structured: problem, proposal, why now, risks, ask
   - **Async message** — Slack/email: concise, scannable, links to detail
   - **Ticket/story** — problem statement, acceptance criteria, context
   - **Talking points** — for a live conversation: what to lead with, what to have ready if asked

Stop when you have enough to frame. If the user says "just go" or similar, proceed with reasonable defaults and note assumptions.

## Phase 2 — Frame

Identify the narrative arc before drafting:

- **Situation** — what's the current state and why does it matter now
- **What we learned** — key insights from the design work
- **What we're proposing** — the direction and why this one
- **Why this over alternatives** — what was considered and why it was set aside

Adjust emphasis by audience:
- **Leadership** — impact, risk, timeline, the ask
- **Builder/teammate** — scope, constraints, technical context, what's decided vs open
- **Cross-functional partner** — how this affects their domain, what you need from them
- **Client/external** — value delivered, what changes for them, next steps

Present the narrative arc as a brief outline. **Stop and wait** for the user to confirm or adjust before drafting.

## Phase 3 — Draft

Produce the artifact in the agreed format:

**One-pager:**
- Problem (2-3 sentences)
- Proposal (what we're doing and the core bet)
- Why now (trigger or deadline)
- What we considered (alternatives, briefly)
- Risks and mitigations
- The ask (what you need from the reader)

**Async message:**
- Lead with the point — what you need or what changed
- 3-5 bullet summary, scannable
- Link to detail (reference the source artifacts)
- Clear next step or ask

**Ticket/story:**
- Title
- Problem statement (user-facing, not implementation-focused)
- Acceptance criteria (testable, specific)
- Context (link to brief/concept, key constraints)
- Size estimate if scoping exists

Pitch tickets frame the problem for stakeholder understanding, not implementation detail. Implementation-ready tickets with dependencies and sizing are a separate step.

**Talking points:**
- Opening — what to lead with (1-2 sentences)
- Key points — 3-5 bullets to cover
- Anticipated questions — what they'll likely ask, with prepared answers
- The ask — what you want to walk away with

Present the full draft. **Stop and wait** for feedback.

## Phase 4 — Refine

Iterate on tone, emphasis, scope, or framing based on user feedback. 1-2 rounds is typical.

Common refinement axes: tone (too formal/informal), length (cut or expand), emphasis (wrong thing leading), missing context (reader won't have enough to decide).

When the user is satisfied, save.

**Save to:**
- One-pager: `artifacts/pitch-<descriptive-name>.md`
- Async message: `artifacts/pitch-<descriptive-name>.md`
- Ticket/story: `artifacts/ticket-<descriptive-name>.md`
- Talking points: `artifacts/pitch-<descriptive-name>.md`

Start the file with an H1 title: `# Pitch: <descriptive title>` (or `# Ticket: <title>` for ticket format). Derive the descriptive name from the core topic — 2-4 hyphenated words.

**Anti-pattern: "Just clean up my notes."** This skill reframes, it doesn't summarize. If the output reads like a shorter version of the input, the pitch failed. The reader has a different mental model — the pitch restructures information for their brain, not yours.

## Artifact Directory

Skills save artifacts to `artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders.

## Rules

- Be direct. No preamble, no filler.
- One question per (`AskUserQuestion` or `requestUserInput`) call.
- This is reframing, not summarizing. The raw artifacts have the information — this skill restructures it for a different brain to process.
- Match the audience's vocabulary. Don't use design jargon in a leadership pitch; don't oversimplify for a technical teammate.
- If the source artifacts are thin, say so. Don't invent substance that isn't there — flag gaps and let the user decide whether to fill them first.

$ARGUMENTS
