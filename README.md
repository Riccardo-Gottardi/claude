# claude

My personal [Claude Code](https://claude.com/claude-code) configuration, versioned as the contents of `~/.claude`.

## What's inside

| Path | Purpose |
| --- | --- |
| [`CLAUDE.md`](CLAUDE.md) | Global instructions applied to every project: citation style, LaTeX math formatting, and rules for graphs and diagrams (Mermaid, with widgets when labels need math). |
| [`skills/literature-research/`](skills/literature-research/SKILL.md) | A skill for running literature research with graded, verifiable sources, with reference lists of [source tiers](skills/literature-research/references/source-tiers.md) and [venues](skills/literature-research/references/venues.md). |

## Usage

Clone the repo into `~/.claude` (back up any existing directory first):

```bash
git clone https://github.com/Riccardo-Gottardi/claude.git ~/.claude
```

Or copy only the parts you want: `CLAUDE.md` into `~/.claude/`, and individual skill folders into `~/.claude/skills/`.

## What is not tracked

Runtime state and machine-specific files are excluded through [`.gitignore`](.gitignore): sessions, history, caches, plugins, telemetry, `settings.json` and `settings.local.json` (which may hold secrets), and `skills/synced/`.

## License

[MIT](LICENSE) © 2026 Riccardo Gottardi
