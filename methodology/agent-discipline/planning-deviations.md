---
title: "Failure Mode 4: Planning Deviations (A' != A)"
description: Agent does A' (close approximation) instead of A (what was asked). All downstream code wires to A'. Cascading failure.
cluster: agent-discipline
related: [[misalignment]], [[verification-laziness]], [[../planning/no-approximations]]
source: Agent failure modes research -- identified as "especially dangerous"
---

# Failure Mode 4: Planning Deviations (A' != A)

The agent does A' -- a "close approximation" -- instead of A, which is what was actually asked. This is especially dangerous because all downstream code wires to A' instead of A. By the time anyone notices, everything is built on the wrong foundation.

## How It Manifests

- Plan says "use WebSocket for real-time updates" -- agent uses polling because it's simpler
- Plan says "validate email format" -- agent checks string is non-empty
- Plan says "paginated API" -- agent returns all results at once
- The deviation is usually in the direction of "easier to implement"

## Why Agents Do This

The agent understands the plan but finds a "simpler" way that's "basically the same thing." It rationalizes: "this achieves the same goal." But it doesn't -- it achieves a similar goal with different properties. And everything built on top assumes the original properties.

## The Cascade

1. Plan says A
2. Agent implements A' (close but not exact)
3. Next task builds on A', assumes A' is A
4. Tests test A' behavior, pass, confirm "A works"
5. Integration fails because other components expected actual A
6. Debugging is hard because tests pass

## Prevention

1. **Verify early and often** that implementation matches the plan exactly. ([[../planning/no-approximations]])
2. **Compare against plan at every step.** Not at the end -- at every step.
3. **Don't let deviations compound.** Catch them in the first task, not the fifth.
4. **The test: can you diff your implementation against the plan and find zero semantic differences?**

## The Rule

> Do exactly what was asked (A), not a "close enough" version (A'). Every deviation cascades -- all downstream code wires to the wrong thing. Verify against plan early and often.
