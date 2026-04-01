# Design Partner Skills

AI agent skills for design work — reason through decisions, explore problem spaces, generate divergent directions, scope into buildable work, and share the result.

## Skills

**`/sensemaking-partner`** — Build structured understanding from a ticket, task, or project context. Decomposes problems into constituent parts, maps the landscape, identifies hidden design complexity, and signals level of effort. Produces understanding; downstream skills produce action.

**`/strategy-partner`** — Plan what design work to do for an initiative. Takes any input — sensemaking artifact, ticket, PRD, verbal description — and produces a prioritized design action plan organized into parallel workstreams, with strategic questions surfaced as reasoning behind the actions.

**`/ideation-partner`** — Explore a problem space and generate genuinely different solution directions. Works from tickets, notes, screenshots, or a verbal description. Asks targeted questions to frame the problem, then produces multiple distinct concepts — not variations on one idea.

**`/scoping-partner`** — Break a chosen direction into prioritized scope tiers (MVP, should-have, nice-to-have). Decomposes features, sequences by dependencies, and produces tickets with acceptance criteria and T-shirt sizing.

**`/sharing-partner`** — Communicate design work to a specific audience — stakeholders, teammates, clients, or cross-functional partners. Restructures artifacts into one-pagers, async messages, tickets, or talking points tuned to the reader's mental model.

**`/research-partner`** — Look into a topic: competitor patterns, technical approaches, how something works, or focused factual questions. Produces self-contained research artifacts that feed into reasoning, ideation, and scoping.

**`/thinking-partner`** — Think something through: a decision, a hunch, a tradeoff, a strategy question, or anything that needs structured clarity before action. Calibrates depth and selects from composable analytical moves to match what you bring it.

**`/testing-partner`** — Simulate lightweight user testing on a wireframe or flow. Generates personas, walks each through the flow step by step, and reports where they complete tasks, where they struggle, and where they drop off. Results stay in chat by default with an option to save.

### How they fit together

```
Sense — Strategize — Ideate — Scope — Share
                     |
          Research · Thinking · Testing
```

## Install

```bash
git clone https://github.com/rodh/design-partner-skills.git ~/.local/share/design-partner-skills
~/.local/share/design-partner-skills/install.sh
```

The install script detects supported platforms and symlinks each skill into the appropriate skills directory. Symlinks keep them updatable with `git pull`.

### Other commands

```bash
./install.sh status      # Show what's linked where
./install.sh update      # git pull + re-install + prune stale links
./install.sh uninstall   # Remove symlinks (leaves the clone intact)
```

## Usage

Invoke any skill by name — e.g., `/sensemaking-partner [link or paste a ticket]`

Skills scan the working directory for existing artifacts and build on prior work automatically.
