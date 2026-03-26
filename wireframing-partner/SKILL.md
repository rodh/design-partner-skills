---
name: wireframing-partner
description: Use when you have a concept, ticket, or design idea and need to make it concrete as structural ASCII wireframes with full flows, states, and edge cases
---

## Phase 1 — Understand

Accept any starting input — a concept file the user points to, a ticket, verbal description, or screenshots.

Ask clarifying questions to understand what needs wireframing. Don't assess against a fixed checklist — different designs have different shapes. The test is: **would knowing this change what I wireframe?**

**Depth rules:**
- **Always ask at least one question.** Even rich input has assumptions worth surfacing.
- **Pick the question whose answer would most change the wireframes you'd produce.** If knowing the answer wouldn't meaningfully alter the layout, don't ask it.
- **Stop when answers start confirming what you already know.** Diminishing returns = move on.
- **If the user says "let's go" or similar — move on immediately.** Wireframe with what you have.

Questions focus on:
- Interaction model — how do users move through this?
- Key user tasks — what must be accomplishable?
- Essential vs secondary screens — what's core, what's support?
- Constraints — platform, density, existing patterns to match
- New flow vs revision of something existing

One question per (`AskUserQuestion` or `requestUserInput`) call. Never batch.

When understanding is sufficient, present an inline **wireframing brief** — what we're wireframing, key tasks, assumptions, expected screens. This is conversation-only, not saved to file.

**Stop and wait** for approval before wireframing.

## Phase 2 — Wireframe

**Structure:** Use box-drawing characters: `┌ ─ ┐ │ └ ┘ ├ ┤ ┬ ┴ ┼`

Follow conventions in `wireframe-conventions.md` for component labeling, interactive elements, width tiers, and stub format.

**Content:** Use realistic placeholder text, never lorem ipsum. Placeholders should reference the actual domain — not generic filler.

**Annotations:** Place `// comment` after the right border: `│ // comment`. Annotations sit outside the box — the right `│` stays at the ruler-line column regardless of annotation length.

**Naming:** Label each screen: `Screen 1: [Name]` with a one-line description of what the user is doing here.

**First-pass depth:** Produce full wireframes for **2–3 key screens** and stubs for everything else (state variations, empty states, secondary flows, edge cases). A screen is key if removing it would make the core interaction model unclear — if the flow still reads without a full wireframe, it's a stub. Default to stub; promote to key only when necessary. If you're producing more than 3 key screens, state why each is essential before proceeding.

**States:** Identify relevant state variations — empty, loaded, error, loading — and include them as stubs on first pass. States are always stubs, never key screens. Show which states exist and their key elements, but don't produce full wireframes for them until hydration.

Present wireframes in conversation. **Stop and wait** for approval before saving.

**Saving:** Save to `wireframes-<slug>.md`. Derive the slug from the flow or feature — 2–4 hyphenated words. Start the file with `# Wireframes: <descriptive title>`. If a file with the same slug already exists, confirm overwrite or ask for a new slug.

## Phase 3 — Iterate

After the first pass, the user will direct changes. Common patterns:

- "Move X above Y" → adjust hierarchy
- "This is too dense" → split into separate screens, promote sections to their own wireframe, or increase spacing between groups
- "Show me the empty state" → generate that variation
- "What happens when they click [element]?" → show the next screen in the flow
- "Add a filter panel" → show expanded and collapsed states

**Scope assessment:** After user feedback, assess whether the change is targeted (affects 1–2 specific screens) or broad (affects shared elements like navigation, headers, or the overall layout approach). For targeted changes, show only the affected screens in conversation. For broad changes, show all screens. In both cases, always write the complete updated set to the file — the file is always the full wireframe set.

Save after each iteration round.

**Limit: 3 rounds of structural changes.** If the wireframe isn't converging, the problem is usually upstream — ambiguity in the concept direction, not the layout. Say so directly.

If the user asks for something that contradicts the original concept or wireframing brief, flag the contradiction.

## Phase 4 — Hydrate

When the user asks, expand stubs into full wireframes.

Read each stub's description and key elements as the spec. Produce full ASCII wireframes matching the style and conventions of existing key screens in the same file. Apply the same width tier, annotation style, and component labeling.

Hydration can be targeted ("hydrate the empty state") or full ("hydrate all stubs"). For targeted hydration, show only the newly expanded screens in conversation. For full hydration, show all screens.

Save the complete updated file after hydration.

## Rules

- Be direct. No preamble, no filler.
- Structure over prettiness — don't aestheticize.
- If concept direction is unclear, ask before wireframing.
- Flag contradictions with the original direction.
- One question per (`AskUserQuestion` or `requestUserInput`) call.

$ARGUMENTS
