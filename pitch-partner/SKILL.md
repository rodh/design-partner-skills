---
name: pitch-partner
description: Use when you need to communicate design work to a specific audience — reframes artifacts into one-pagers, async messages, tickets, or talking points
---

## Phase 1 — Gather

Read the artifacts the user points to — session notes, briefs, concepts, wireframes, scope docs. Scan CWD for related context that adds depth.

Then ask (one question per `AskUserQuestion` or `requestUserInput` call, never batch):

1. **Who's the audience?** — Leadership, a teammate who'll build it, a cross-functional partner, a client? Their role shapes what to emphasize.
2. **What format?** Offer options based on the situation:
   - **One-pager** — structured: problem, proposal, why now, risks, ask
   - **Async message** — Slack/email: concise, scannable, links to detail
   - **Ticket/story** — problem statement, acceptance criteria, context
   - **Talking points** — for a live conversation: what to lead with, what to have ready if asked
3. **What decision are you asking them to make?** Or are you informing, not asking? This changes the entire framing — a request for approval needs different emphasis than a status update.

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

**Talking points:**
- Opening — what to lead with (1-2 sentences)
- Key points — 3-5 bullets to cover
- Anticipated questions — what they'll likely ask, with prepared answers
- The ask — what you want to walk away with

Present the full draft. **Stop and wait** for feedback.

## Phase 4 — Refine

Iterate on tone, emphasis, scope, or framing based on user feedback. 1-2 rounds is typical. When the user is satisfied, save.

**Save to:**
- One-pager: `pitch-{slug}.md`
- Async message: `pitch-{slug}.md`
- Ticket/story: `ticket-{slug}.md`
- Talking points: `pitch-{slug}.md`

Start the file with an H1 title: `# Pitch: <descriptive title>` (or `# Ticket: <title>` for ticket format). Derive the slug from the core topic — 2-4 hyphenated words.

## Rules

- Be direct. No preamble, no filler.
- One question per (`AskUserQuestion` or `requestUserInput`) call.
- This is reframing, not summarizing. The raw artifacts have the information — this skill restructures it for a different brain to process.
- Match the audience's vocabulary. Don't use design jargon in a leadership pitch; don't oversimplify for a technical teammate.
- If the source artifacts are thin, say so. Don't invent substance that isn't there — flag gaps and let the user decide whether to fill them first.

$ARGUMENTS
