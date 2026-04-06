---
title: "Failure Mode 7: Entropy Maximization"
description: Changing behavior but leaving docs, comments, and references pointing to old behavior. Death by a thousand contradictions.
cluster: agent-discipline
related: [[../verification/blast-radius-analysis]], [[../cross-domain/entropy-kills]]
source: Agent failure modes research
---

# Failure Mode 7: Entropy Maximization

Agents change behavior but leave docs, comments, and references pointing to old behavior. Repeat this 100 times and you have an unmaintainable codebase where the agent is constantly confused by contradictory information.

## How It Manifests

- Function renamed but comments still reference the old name
- Behavior changed but README documents the old behavior
- API endpoint moved but client code has stale URLs in comments
- Config format changed but example configs show the old format
- Test descriptions don't match what the tests actually test

## Why Agents Do This

Updating references feels like busywork. The agent is focused on the primary change and doesn't think about ripple effects. Under context pressure, "fixing the thing" feels more important than "updating the docs about the thing."

## Prevention

1. **After every change, check ALL references.** ([[../verification/blast-radius-analysis]])
   - Comments mentioning the changed thing
   - Documentation describing the changed behavior
   - Related code that assumes the old behavior
   - Test descriptions that reference old behavior
2. **Allocate tokens for cleanup.** Budget time after every long session for a fresh-context cleanup pass.
3. **Treat stale docs as bugs.** A comment that contradicts the code is not harmless -- it actively misleads future work.

## The Rule

> When changing behavior, update ALL references -- docs, comments, related code. Don't leave the repo in a state where old information contradicts new behavior. Entropy kills.

See also: [[../cross-domain/entropy-kills]] for why this matters at scale.
