---
title: Git Safety
description: Read-only by default. No force push. No destructive operations without explicit approval.
cluster: security
related: [[secrets-management]], [[../verification/validate-before-claiming]]
source: Production git incidents -- force pushes that overwrote work, hard resets that lost changes
---

# Git Safety

Git commands that destroy history or overwrite remote state are dangerous. Default to read-only. Escalate destructive operations to the user.

## Read-Only (Always Safe)

These commands never modify state:
```bash
git status
git diff
git log
git branch
git show
```

## Write (Require Intent)

These modify local state:
```bash
git add <files>    # Stage specific files, not -A
git commit -m ""   # Simple message, no heredoc
git checkout -b    # Create branch
```

## Destructive (Require Explicit Approval)

Never run these without the user explicitly requesting them:
```bash
git push --force     # Overwrites remote history
git reset --hard     # Destroys local changes
git checkout .       # Discards all modifications
git clean -f         # Deletes untracked files
git branch -D        # Force-deletes branch
```

## Push Protocol

Never auto-push. Instead:
1. Stage and commit locally
2. Give the user the exact push command with a summary
3. Let the user decide when to push

This prevents accidental pushes of incomplete work, wrong branches, or sensitive content.
