---
title: Decompose Complexity
description: Break problems into sub-100-line subtasks. 500 small tasks beats 1 massive one. Reduce activation energy.
cluster: planning
related: [[plan-before-code]], [[../agent-discipline/complexity-fear]], [[../agent-discipline/agent-psychology]]
source: Agent failure modes research + GTD methodology
---

# Decompose Complexity

Fear of large tasks leads to stubs and shortcuts ([[../agent-discipline/complexity-fear]]). The fix: make every task so small it feels trivial.

## The Target

Each subtask should be:
- **Under 100 lines of code change**
- **Completable in 2-5 minutes**
- **Independently testable**
- **Self-contained** (doesn't depend on unwritten code)

## How To Decompose

1. List all the things that need to change
2. Group related changes into logical units
3. Order by dependency (what must exist before what)
4. Each group becomes a subtask
5. If any subtask feels large, decompose it further

## Why This Works

Same principle as human productivity ([[../agent-discipline/agent-psychology]]): reduce activation energy to near zero. "Write a 3-line test" has near-zero activation energy. "Implement authentication" has massive activation energy.

500 small tasks > 1 massive task. Each small task:
- Is easy to start (low activation energy)
- Is easy to verify (small blast radius)
- Produces a commit (progress is visible)
- Can be handed off (any agent can pick it up)
