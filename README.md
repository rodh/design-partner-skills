# Framing Partner Skills

AI coding agent skills for the full design framing loop — reason through decisions, explore problem spaces, generate divergent directions, wireframe solutions, validate with simulated users, scope into buildable work, and pitch the result to stakeholders.

## Skills

**`/thinking-partner`** — Reason through a decision, understand a problem, explore a hunch, or compare options. Works with or without existing project context. Reads your codebase and docs to ground the conversation, then follows structured thinking patterns (orient, hunch, what-if, decision) to help you reach clarity.

**`/ideation-partner`** — Explore a problem space and generate genuinely different solution directions. Works from tickets, notes, screenshots, or a verbal description. Asks targeted questions to frame the problem, then produces multiple distinct concepts — not variations on one idea.

### Experimental skills

**`/next-move-partner`** — Scan your design artifacts and recommend the highest-leverage next step. Shows a compact status map of what exists and what's missing, then suggests which skill to invoke and with what input. A quick diagnostic, not a workflow.

**`/pitch-partner`** — Reframe your design work for a specific audience and format. Takes briefs, concepts, or session notes and restructures them into one-pagers, async messages, tickets, or talking points — tuned to whether you're pitching leadership, a teammate, or a cross-functional partner.

**`/scoping-partner`** — Break a chosen direction into prioritized scope tiers (MVP, should-have, nice-to-have) and draft tickets for the work. Decomposes features, sequences by dependencies, and produces Jira-style tickets with acceptance criteria and T-shirt sizing.

## Install

```bash
git clone https://github.com/rodhoward/framing-partner-skills.git ~/.local/share/framing-partner-skills
~/.local/share/framing-partner-skills/install.sh
```

The install script detects supported platforms and symlinks each skill into the appropriate skills directory. Symlinks keep them updatable with `git pull`.

### Other commands

```bash
./install.sh status      # Show what's linked where
./install.sh update      # git pull + re-install + prune stale links
./install.sh uninstall   # Remove symlinks (leaves the clone intact)
```

## Requirements

- An AI coding agent that supports skills (e.g., [Claude Code](https://claude.com/claude-code), [Codex CLI](https://github.com/openai/codex))
- Bash 3.2+ (macOS default works)
