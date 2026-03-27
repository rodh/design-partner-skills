# Design Framing Skills

AI coding agent skills for the design framing loop — reason through decisions, explore problem spaces, generate divergent directions, scope into buildable work, and pitch the result to stakeholders.

## Skills

**`/orient-partner`** — Understand a ticket, task, or project context. Decomposes problems into constituent parts, maps the landscape, identifies hidden design complexity, and signals level of effort. Produces understanding; downstream skills produce action.

**`/reasoning-partner`** — Reason through a decision, stress-test a hunch, or explore a what-if. Works with or without existing project context. Reads your codebase and docs to ground the conversation, then follows structured reasoning (evidence, stakes, steel-man, assumptions) to help you reach clarity.

**`/research-partner`** — Look into a topic: competitor patterns, technical approaches, how something works, or focused factual questions. Produces self-contained research artifacts that feed into reasoning, ideation, and scoping.

**`/ideation-partner`** — Explore a problem space and generate genuinely different solution directions. Works from tickets, notes, screenshots, or a verbal description. Asks targeted questions to frame the problem, then produces multiple distinct concepts — not variations on one idea.

**`/next-move-partner`** — Figure out what design move to make next when you're unclear where to focus or what's been missed. Scans artifacts, shows a compact status map, and recommends which skill to invoke.

**`/pitch-partner`** — Communicate design work to a specific audience — stakeholders, teammates, clients, or cross-functional partners. Restructures artifacts into one-pagers, async messages, tickets, or talking points tuned to the reader's mental model.

**`/scoping-partner`** — Break a chosen direction into prioritized scope tiers (MVP, should-have, nice-to-have). Decomposes features, sequences by dependencies, and produces tickets with acceptance criteria and T-shirt sizing.

## How they fit together

The skills follow a natural design progression, though you can enter at any point:

```
Orient → Research → Reason → Ideate → Scope → Pitch
(map)     (learn)     (decide)  (explore) (plan)  (share)
```

**Orient** maps the problem. **Research** fills knowledge gaps. **Reasoning** works through decisions and assumptions. **Ideation** generates divergent directions. **Scoping** breaks a chosen direction into buildable tiers. **Pitch** communicates the result.

Use `/next-move-partner` at any point to see where you are and what to do next.

## Install

```bash
git clone https://github.com/rodh/design-framing-skills.git ~/.local/share/design-framing-skills
~/.local/share/design-framing-skills/install.sh
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
