---
title: No A' Approximations
description: Do exactly what was asked (A), not a close-enough version (A'). Every deviation cascades.
cluster: planning
related: [[plan-before-code]], [[../agent-discipline/planning-deviations]]
source: Failure mode 4 -- cascading deviation failures
---

# No A' Approximations

Do exactly what was asked (A), not a "close enough" version (A'). Every deviation cascades -- all downstream code wires to the wrong thing.

## The Verification Loop

At every step of implementation:
1. Re-read the plan/spec for this step
2. Compare what you're about to write against what was planned
3. Ask: "Is this exactly A, or is this A'?"
4. If A' -- stop, re-align, then continue

## Common A' Patterns

- Plan says WebSocket -> agent uses polling ("basically the same")
- Plan says validate email format -> agent checks non-empty ("good enough")
- Plan says paginated API -> agent returns all results ("simpler")
- Plan says error modal -> agent uses console.log ("for now")

Each one feels like a minor simplification. But [[../agent-discipline/planning-deviations]] shows how they cascade into systemic failure.

## The Rule

> Do exactly what was asked (A), not a "close enough" version (A'). Verify against plan early and often. Every deviation cascades.
