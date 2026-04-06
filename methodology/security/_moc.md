---
title: Security
description: Never ship vulnerabilities. Never expose secrets. Git safety as default posture.
type: moc
cluster: security
---

# Security

Security failures are the most expensive bugs. A leaked API key costs real money. An XSS vulnerability exposes users. These are non-negotiable baseline practices.

## Code Review
- [[owasp-review]] -- check every code change against OWASP top 10

## Secrets
- [[secrets-management]] -- never in logs, commits, output, or prompts

## Git
- [[git-safety]] -- read-only default, no force push, no destructive operations

## Related Clusters
- [[../verification/_moc]] -- security checks are part of verification
