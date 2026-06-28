# token-optimization

Token optimization notes and configuration for Claude Code workflows.

## Files

- [GP.md](./GP.md) — General principles
- [reference.md](./reference.md) — RTK reference
- [tools.md](./tools.md)

## Pre-push Hook

Syncs `GP.md` to `~/.claude/` on every push. Place at `.git/hooks/pre-push`:

```bash
#!/usr/bin/env bash
set -e
PROJECT_DIR="$(git rev-parse --show-toplevel)"
cp "$PROJECT_DIR/GP.md" ~/.claude/GP.md
echo "[pre-push] GP.md synced to ~/.claude/"
exit 0
```

`.git/hooks/` is not version-controlled — set up manually on each clone.
