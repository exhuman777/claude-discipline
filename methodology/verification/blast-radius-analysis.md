---
title: Blast Radius Analysis
description: After changes, check all references for contradictions. Comments, docs, related code, test descriptions.
cluster: verification
related: [[../agent-discipline/entropy-maximization]], [[validate-before-claiming]]
source: Failure mode 7 prevention
---

# Blast Radius Analysis

Every change has a blast radius -- the set of files, comments, docs, and references that might be affected. Checking this radius after every change prevents [[../agent-discipline/entropy-maximization]].

## The Checklist

After any behavioral change:

1. **Comments mentioning the changed thing** -- search for the old name/behavior
2. **Documentation** -- README, API docs, inline guides
3. **Related code** -- callers, consumers, anything that depends on the changed behavior
4. **Test descriptions** -- do they still describe what the tests actually test?
5. **Configuration** -- example configs, default values, environment variables
6. **Type definitions** -- interfaces, schemas, contracts

## How To Search

```bash
# Find references to the thing you changed
grep -r "oldFunctionName" --include="*.{ts,js,md,json}"

# Check for stale comments
grep -r "TODO\|FIXME\|HACK" --include="*.{ts,js}"
```

## The Rule

> When changing behavior, update ALL references -- docs, comments, related code. Don't leave the repo in a state where old information contradicts new behavior.

Treat stale docs as bugs. A comment that contradicts the code is not harmless -- it actively misleads future work.
