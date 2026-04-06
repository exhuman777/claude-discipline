---
title: Secrets Management
description: Never expose secrets in logs, commits, output, or system prompts. One leak = real damage.
cluster: security
related: [[owasp-review]], [[git-safety]]
source: Production incidents -- leaked keys cost real money
---

# Secrets Management

API keys, passwords, tokens, connection strings -- one leak in a commit means the key is in git history forever (even after removal). One leak in logs means anyone with log access has the key.

## Rules

1. **Never commit secrets.** Use `.env` files (gitignored) or environment variables.
2. **Never log secrets.** Redact sensitive values in log output.
3. **Never paste secrets in chat.** Claude Code conversations may be stored.
4. **Never expose in error messages.** Stack traces and error details should not contain credentials.
5. **Never hardcode.** Even in "temporary" code. Temporary becomes permanent.

## .gitignore Essentials

```
.env
.env.local
.env.*.local
*.pem
*.key
credentials.json
service-account.json
```

## If You Accidentally Commit a Secret

1. **Rotate the key immediately.** Generate a new one.
2. Don't just remove it from the next commit -- it's still in git history.
3. If the repo is public, consider the key compromised from the moment it was pushed.
