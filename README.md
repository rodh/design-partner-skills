# Design Partner Skills

AI agent skills for creative exploration — generate divergent concepts and wireframe them before committing to code.

## Skills

**`/ideation-partner`** — Explore a problem space and generate genuinely different
solution directions. Works from tickets, notes, screenshots, or a verbal description.
Produces multiple distinct concepts — not variations on one idea.

**`/wireframing-partner`** — Produce self-contained HTML wireframes that communicate
proposed page changes through a fidelity gradient. Pairs naturally with ideation-partner
to visualize concepts before building.

### How they fit together

```
Ideate → Wireframe → Build
```

## Install

```bash
DEST=~/.local/share/design-partner-skills
[ -d "$DEST" ] && git -C "$DEST" pull --ff-only || git clone https://github.com/rodh/design-partner-skills.git "$DEST"
"$DEST/install.sh"
```

### Other commands

```bash
./install.sh status      # Show what's linked where
./install.sh update      # git pull + re-install + prune stale links
./install.sh uninstall   # Remove all symlinks (leaves the clone intact)
```

## Usage

Invoke any skill by name — e.g., `/ideation-partner [describe the problem space]`

Skills scan the working directory for existing artifacts and build on prior work automatically.
Artifacts are saved to `artifacts/` by default. To use a different directory, add
`Artifact directory: <path>` to your project's CLAUDE.md.
