# equity-research

Run Braxton's institutional 8-Lens + Damodaran equity research framework (v2) on a ticker — archetype classification, qualitative deep-dive, cost-of-capital build-up, 3-stage DCF, Monte Carlo, 8 equal-weight investor lenses, investment gates and position sizing — then write a structured note to the Obsidian vault's Investing/ folder.

## What it does

Run Braxton's institutional 8-Lens + Damodaran equity research framework (v2) on a ticker — archetype classification, qualitative deep-dive, cost-of-capital build-up, 3-stage DCF, Monte Carlo, 8 equal-weight investor lenses, investment gates and position sizing — then write a structured note to the Obsidian vault's Investing/ folder. Use when the user says "run 8-lens", "analyze <ticker>", "equity research on X", "deep dive on <company>", wants a BUY/WATCH/AVOID verdict, or asks for a quarterly thesis update. Vault at ~/Library/Mobile Documents/iCloud~md~obsidian/Documents/claude.

## Install

```bash
git clone <this-repo> ~/.claude/skills/equity-research
```

Or symlink it if you want edits to stay live:

```bash
ln -s "$PWD" ~/.claude/skills/equity-research
```

## Use

Invoke in Claude Code with `/equity-research`, or just describe the task — the skill's
description triggers it automatically.

## Contents

- `SKILL.md`
- `references/archetypes-and-gates.md`
- `references/damodaran.md`
- `references/data-checklist.md`
- `references/excel-model.md`
- `references/lenses.md`
- `references/prompt-library.md`

---

Personal skill, written by hand — not forked or vendored from a public repo.
