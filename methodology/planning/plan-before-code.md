---
title: Plan Before Code
description: AUDIT -> ARCHITECT -> BUILD+REVIEW -> REFINE -> COMPOUND. No code without a plan.
cluster: planning
related: [[decompose-complexity]], [[think-like-founder]], [[no-approximations]]
source: Production methodology refined over 3000+ prompts
---

# Plan Before Code

Unless it's literally a one-line change, there's a plan first. Always.

## The Phases

1. **AUDIT** -- Read all related files. Understand current state. Check for contradictions. ([[../agent-discipline/incomplete-context]])
2. **ARCHITECT** -- Design the solution. Consider alternatives. Choose the approach that scales. ([[think-like-founder]])
3. **BUILD + REVIEW** -- Implement in small steps with continuous verification. ([[decompose-complexity]])
4. **REFINE** -- Clean up, update references, check blast radius. ([[../verification/blast-radius-analysis]])
5. **COMPOUND** -- Extract patterns, update documentation, leave the codebase better than you found it.

## Why Each Phase Matters

- **Skip AUDIT** -> incomplete context -> everything downstream is wrong
- **Skip ARCHITECT** -> first idea gets implemented -> often the wrong approach
- **Skip REVIEW during BUILD** -> deviations compound unnoticed -> ([[../agent-discipline/planning-deviations]])
- **Skip REFINE** -> entropy accumulates -> ([[../agent-discipline/entropy-maximization]])
- **Skip COMPOUND** -> same problems solved repeatedly -> no learning

## The Rule

> Plan mode for code. AUDIT -> ARCHITECT -> BUILD+REVIEW -> REFINE -> COMPOUND. No exceptions for "simple" tasks -- simple tasks are where unexamined assumptions cause the most waste.
