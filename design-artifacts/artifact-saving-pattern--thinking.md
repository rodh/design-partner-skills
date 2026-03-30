# Thinking: Artifact Saving Pattern — Overkill or Strength?

## Session summary

Sanity-checked whether the design-partner-skills toolkit's aggressive artifact-saving pattern is overkill, then pressure-tested naming, directory structure, and capture mechanics for improvement opportunities. Concluded the current system is well-designed and no changes are needed.

## Trigger

"In this skills toolkit I pretty aggressively save generated output as durable artifacts...I just want a sanity check, is this overkill or a strength?"

## Calibration

Started as quick check (sanity check on the pattern), escalated to working session when the user wanted to explore improvements to naming/structure. Convergent then diagnostic shape.

## Moves applied

**Evidence:** Catalogued the full artifact pattern across all 7 skills. Every skill writes structured markdown to `design-artifacts/{topic}--{stage}.md`. Ideation writes two (brief + concept). Skills cross-reference each other's artifacts via hardcoded glob patterns on startup.

**Stakes (initial sanity check):** The artifact pattern does three things that would break without it: (1) cross-skill continuity — artifacts are the shared memory between skills, (2) context window independence — artifacts survive across sessions, (3) the `{topic}--{stage}` naming clusters a full design journey together. Removing artifacts turns 7 composable tools into 7 isolated prompts.

**Pressure-test (improvement search):** Identified three potential friction points:
1. **Collision on repeat runs** — same topic + same stage overwrites silently. Real but rare; when it happens, overwriting is usually the desired behavior.
2. **No temporal signal** — filenames don't encode when artifacts were created. Nice-to-have, but git history and file dates cover this.
3. **Scanning brittleness** — each skill hardcodes which suffixes it scans. Theoretical risk; the skill set is stable and updating patterns is a one-time edit.

**Stakes (on fixes):** Evaluated two fix options for the collision problem:
- **Option A (version filenames):** Preserves history but degrades directory clustering, complicates scanning globs, and duplicates what git already does.
- **Option B (fold prior work into new artifact):** Keeps directory clean but adds conditional merge logic to every skill's capture section — complexity on every invocation to handle a rare edge case.

## Resolution

**Do nothing.** The current pattern is a strength, not overkill. The system's value comes from its simplicity: one file, one predictable location, simple globs for cross-referencing. The collision risk is real but rare, and git already provides version history. Adding merge logic or versioning would trade clarity for marginal safety. If overwrite pain actually materializes (especially outside git-tracked repos), Option B (fold in prior work) would be the right fix — but not preemptively.

## Changes made

None.

## Open threads

- If artifacts are ever used outside a git repo, the collision/overwrite risk becomes more acute and would warrant revisiting Option B.
