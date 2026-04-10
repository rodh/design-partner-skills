# Design Partner Skills

AI agent skills for design work — reason through decisions, explore problem spaces, generate divergent directions, scope into buildable work, and share the result.

## Skills

**`/scoping-partner`** — Build structured understanding from raw project context (tickets, PRDs, Slack threads, wireframes, verbal dumps). Probes framing assumptions, decomposes into design surfaces, and converges on the load-bearing slice to work on first. Produces a scoping artifact with on-demand depth sections.

**`/planning-partner`** — Take a chosen aspect from a scoping artifact (the load-bearing slice or any parked item) and produce a focused execution plan: 3–6 sequenced steps, each with a method and a decision-relevant outcome, plus the one piece of hidden complexity worth flagging. Purely additive over the scope doc — no restatement.

**`/ideation-partner`** — Explore a problem space and generate genuinely different solution directions. Works from tickets, notes, screenshots, or a verbal description. Asks targeted questions to frame the problem, then produces multiple distinct concepts — not variations on one idea.

**`/sharing-partner`** — Communicate design work to a specific audience — stakeholders, teammates, clients, or cross-functional partners. Restructures artifacts into one-pagers, async messages, tickets, or talking points tuned to the reader's mental model.

**`/research-partner`** — Look into a topic: competitor patterns, technical approaches, how something works, or focused factual questions. Produces self-contained research artifacts that feed into reasoning, ideation, and scoping.

**`/thinking-partner`** — Think something through: a decision, a hunch, a tradeoff, a strategy question, or anything that needs structured clarity before action. Calibrates depth and selects from composable analytical moves to match what you bring it.

### How they fit together

```
Scope — Plan — Ideate — Share
           |
     Research · Thinking
```

`/planning-partner` is the typical next step after `/scoping-partner` when the slice is big enough to need a multi-step execution plan.

## Install

```bash
git clone https://github.com/rodh/design-partner-skills.git ~/.local/share/design-partner-skills
~/.local/share/design-partner-skills/install.sh
```

The install script detects supported platforms and symlinks each skill into the appropriate skills directory. Symlinks keep them updatable via `update`.

Already installed? Run `~/.local/share/design-partner-skills/install.sh update` to pull latest and prune removed skills.

### Other commands

```bash
./install.sh status      # Show what's linked where
./install.sh update      # git pull + re-install + prune stale links
./install.sh uninstall   # Remove all symlinks (leaves the clone intact)
```

## Usage

Invoke any skill by name — e.g., `/scoping-partner [link or paste a ticket]`

Skills scan the working directory for existing artifacts and build on prior work automatically.
