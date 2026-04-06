---
title: Agent Discipline
description: 7 failure modes agents exhibit under pressure and harness design to prevent them. From analysis of long-running autonomous engineering workflows.
type: moc
cluster: agent-discipline
---

# Agent Discipline

All harness design overcomes agents either becoming lazy and cutting corners or being confused and making mistakes. These aren't bugs -- they're systematic behavioral patterns that emerge from how models are trained.

RL training penalized agents for getting complex tasks wrong. So they avoid complexity. Context pressure makes them rush. Verification feels like wasted tokens. The result: 7 predictable failure modes.

## The 7 Failure Modes

### Pre-Task
- [[incomplete-context]] -- acting on wrong or missing information. Propagates through everything downstream.

### Planning
- [[misalignment]] -- choosing wrong attack vectors, implementing quick fixes that create tech debt

### During Task
- [[context-anxiety]] -- quality degrades as tokens accumulate, desperate to end session
- [[planning-deviations]] -- doing A' (close approximation) instead of A (what was asked). Cascading failure.
- [[complexity-fear]] -- writing stubs, declaring "out of scope", avoiding hard problems

### Post-Task
- [[verification-laziness]] -- weak tests, premature "done", testing A' while claiming A works
- [[entropy-maximization]] -- changing behavior but leaving docs/comments pointing to old behavior

## Harness Design
- [[harness-design]] -- orchestration principles that prevent failure modes structurally
- [[agent-psychology]] -- why productivity methods that work on humans work on agents

## Related Clusters
- [[../token-efficiency/_moc]] -- context anxiety is often triggered by token waste
- [[../verification/_moc]] -- the antidote to verification laziness
- [[../planning/_moc]] -- the antidote to misalignment and planning deviations
