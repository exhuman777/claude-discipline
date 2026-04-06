---
title: claude-discipline methodology
description: Entry point to the discipline skill graph. 30 interconnected methodology files across 6 clusters, distilled from 3000+ production prompts.
type: root-moc
---

# claude-discipline

Claude Code is smart but undisciplined. It burns tokens quadratically, cuts corners under context pressure, skips verification, and exhibits 7 documented failure modes that compound into wasted time and broken code. This methodology is a harness -- evidence-backed rules and techniques that make Claude disciplined, efficient, and methodical.

Every claim in this graph traces to a real production failure or a verified optimization. Nothing theoretical.

## Clusters

- [[token-efficiency/_moc]] -- the math of why tokens matter and 7 techniques to cut waste by 75%+
- [[agent-discipline/_moc]] -- 7 failure modes agents exhibit and harness design to prevent them
- [[verification/_moc]] -- prove it works before claiming it works, every time
- [[planning/_moc]] -- think before code, decompose before building, verify against plan
- [[security/_moc]] -- never ship vulnerabilities, never expose secrets
- [[cross-domain/_moc]] -- principles that connect everything: compound returns, entropy, psychology

## How to Navigate

1. Read the cluster MOC descriptions above -- they tell you if a cluster is relevant
2. Open the relevant `_moc.md` -- it maps the concepts in that cluster
3. Follow wikilinks in prose -- they carry meaning about when and why to go deeper
4. Most decisions happen before reading a single full file

## Evidence Base

- 3000+ production prompts across 28 projects
- 858 sessions / 18,903 turns / $1,619 spend audited
- 7 agent failure modes identified and documented
- ENABLE_TOOL_SEARCH: verified ~20K tokens/turn savings
- Output minimalism: verified 75% token savings per turn
- 43 rules distilled, each from a real production failure
