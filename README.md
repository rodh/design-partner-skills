# Design Framing Skills

AI coding agent skills for the design framing loop — reason through decisions, explore problem spaces, generate divergent directions, scope into buildable work, and pitch the result to stakeholders.

## Skills

**`/orienting-partner`** — Understand a ticket, task, or project context. Decomposes problems into constituent parts, maps the landscape, identifies hidden design complexity, and signals level of effort. Produces understanding; downstream skills produce action.

**`/strategy-partner`** — Plan what design work to do for an initiative. Takes any input — orient artifact, ticket, PRD, verbal description — and produces a prioritized design action plan organized into parallel workstreams, with strategic questions surfaced as reasoning behind the actions.

**`/research-partner`** — Look into a topic: competitor patterns, technical approaches, how something works, or focused factual questions. Produces self-contained research artifacts that feed into reasoning, ideation, and scoping.

**`/thinking-partner`** — Think something through: a decision, a hunch, a tradeoff, a strategy question, or anything that needs structured clarity before action. Calibrates depth and selects from composable analytical moves to match what you bring it.

**`/ideation-partner`** — Explore a problem space and generate genuinely different solution directions. Works from tickets, notes, screenshots, or a verbal description. Asks targeted questions to frame the problem, then produces multiple distinct concepts — not variations on one idea.

**`/scoping-partner`** — Break a chosen direction into prioritized scope tiers (MVP, should-have, nice-to-have). Decomposes features, sequences by dependencies, and produces tickets with acceptance criteria and T-shirt sizing.

**`/pitch-partner`** — Communicate design work to a specific audience — stakeholders, teammates, clients, or cross-functional partners. Restructures artifacts into one-pagers, async messages, tickets, or talking points tuned to the reader's mental model.

## How they fit together

The skills follow a natural design progression, though you can enter at any point:

```
Orient → Strategize → Research → Think  → Ideate →  Scope →  Pitch
(map)    (plan)       (learn)    (think)  (explore) (build)  (share)
```

**Orient** maps the problem. **Strategize** plans what design work to do. **Research** fills knowledge gaps. **Thinking** works through decisions, hunches, tradeoffs, and assumptions. **Ideation** generates divergent directions. **Scoping** breaks a chosen direction into buildable tiers. **Pitch** communicates the result.

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
