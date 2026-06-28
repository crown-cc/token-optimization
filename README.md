# token-optimization

Token optimization notes and prompts for Claude Code workflows.

## Files

- `prompts/` — Markdown prompts synced to `~/.claude/` on every push
  - [GP.md](./prompts/GP.md) — General principles
  - [TS.md](./prompts/TS.md) — Tool strategy (when to call which tool / MCP / skill)
- [tools.md](./tools.md)

## Pre-push Hook

Syncs `prompts/*.md` to `~/.claude/` (flat) on every push, so `~/.claude/CLAUDE.md` imports like `@GP.md` resolve. Place at `.git/hooks/pre-push`:

```bash
#!/usr/bin/env bash
set -e
PROJECT_DIR="$(git rev-parse --show-toplevel)"
cp "$PROJECT_DIR"/prompts/*.md ~/.claude/
echo "[pre-push] prompts/*.md synced to ~/.claude/"
exit 0
```

`.git/hooks/` is not version-controlled — set up manually on each clone.
