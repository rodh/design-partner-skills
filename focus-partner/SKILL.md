---
name: focus-partner
description: Use when you have accumulated design work and need to cut through it to decide what to ship first — too many directions, too much analysis, need to converge on a v1
---

## Phase 1 — Orient

Scan `design-artifacts/` (and one level of subfolders) for existing work — scoping, ideation, research, thinking, planning artifacts. Skim all of them to understand the landscape. Don't deep-read yet.

**Two mandatory questions before proceeding:**

1. **"What's the current state?"** — What's actually built, in progress, or changed since the design work happened. Design artifacts drift from reality. Don't assume artifacts reflect current state. One `AskUserQuestion` or `requestUserInput` call.

2. **"What's next?"** — What the user is trying to ship or deliver next, and on what timeline. This sets the scope filter. One `AskUserQuestion` or `requestUserInput` call.

After both answers: deep-read only the artifacts relevant to the "what's next" scope. Skip artifacts about future horizons, other initiatives, or resolved decisions that don't affect this delivery.

**Intent tag:** Based on the user's answers, state in one line what you're optimizing for:

> *Reading this as: [intent]. Filtering for [lens].*

Example: *Reading this as: shipping a filter redesign in 2 weeks. Filtering for highest user-pain reduction with lowest delivery risk.*

The user corrects if wrong, otherwise proceed. Do not stop and wait for confirmation — the tag is inline, not a gate.

**Not for:** decomposing a problem you don't yet understand (`/scoping-partner`), or generating new directions (`/ideation-partner`). Focus-partner is for when the design work exists and you need to cut through it to decide what ships first.

## Phase 2 — Cut

Apply the three-layer filter:

1. **Intent** — what the user is optimizing for (from the intent tag)
2. **Impact** — what most moves the needle toward that intent
3. **Risk** — among high-impact items, what carries the highest uncertainty or consequence

Produce three sections, compressed:

**Ship** — The smallest coherent thing that gets in front of real users and tests the riskiest assumption. Not a feature list — a usable experience. For each included item, one line on why it made the cut. Resist the urge to bundle adjacent improvements — if something can ship separately later without rework, it's not v1. When in doubt, cut it.

**Defer** — Work from the design artifacts that is valuable but doesn't belong in this delivery. For each item: one line on why it's deferred (not ready, depends on v1 learning, blocked, lower impact) and what would promote it to the next cycle.

**Learn** — What shipping this will teach you that more design work won't. Name the riskiest assumption the v1 is making. Name the user feedback that will be more valuable than further analysis. This is the argument for stopping design and starting to build.

Keep the total output short. The value of this skill is compression, not comprehensiveness. If a section needs more than 10 lines, it's too long.

**Stop and wait.** Present this as: *"Here's what I'd ship and what I'd cut. What feels wrong?"* This is the only mandatory pause — one round of pushback, then finalize.

## Phase 3 — Adjust

Incorporate the user's pushback. If they disagree with a cut, move the item and adjust the rationale. If they want to add scope, pressure-test it: *"Adding X means [concrete tradeoff]. Still want it in?"*

Don't re-present the full recommendation. State what changed and why.

If the user wants to go deeper on any deferred item, name the appropriate skill (`/thinking-partner`, `/planning-partner`, etc.) rather than expanding inline.

**Stop and wait** for the user to confirm before saving.

## Phase 4 — Capture

Save to `design-artifacts/<descriptive-name>--focus.md`, where `<descriptive-name>` is 2-4 hyphenated words describing what's being focused.

Start the file with an H1 title: `# Focus: <title>` (e.g., `# Focus: Dashboard V1 Scope`).

Structure:

- **Intent** — one sentence: what we're optimizing for
- **Current state** — what exists now (compressed)
- **Ship** — what's in v1 and why
- **Riskiest assumption** — the biggest bet v1 makes
- **Defer** — what's out and why, with promotion triggers
- **Learn** — what shipping will teach that design won't
- **Next skill** — if the user needs to go deeper, which skill and on what

The artifact must be **self-contained** — readable without conversation context.

**Anti-pattern: "Let me be thorough."** This skill exists to cut, not to analyze. If you find yourself adding sections, expanding rationale, or presenting balanced options, you're doing the wrong job. Have a point of view. Be brief. The depth already happened in the upstream skills.

**Anti-pattern: "Everything is important."** If nothing gets deferred, the skill failed. The user invoked this because they have too much — the job is to make hard cuts, not to validate that everything matters.

## Artifact Directory

Skills save artifacts to `design-artifacts/`. Create the directory if it doesn't exist. When scanning for existing artifacts, check `design-artifacts/` and one level of subfolders — users may manually organize artifacts into subfolders. Before writing, check if an artifact already exists at the target path. If it does, read it — the current run's output should reflect awareness of prior work, not blindly replace it.

## Rules

- Be direct. No preamble, no filler.
- One question per (`AskUserQuestion` or `requestUserInput`) call.
- Lead with the recommendation, not the analysis. The analysis already happened.
- The three-layer filter (intent → impact → risk) must be visible in the output structure, not just implicit in your reasoning.
- "Ship" must describe a coherent user experience, not a feature checklist.
- "Defer" must include promotion triggers — what would move each item to the next cycle.
- "Learn" is mandatory. If you can't name what shipping teaches, the v1 isn't focused enough.
- Keep it short. If the total recommendation exceeds ~30 lines, compress further.
- If the design artifacts are too thin to cut from — not enough work has been done to have a convergence problem — say so and recommend the upstream skill that's needed.
- If there's only one direction and it's already scoped, this skill isn't needed — recommend `/planning-partner` instead.

$ARGUMENTS
