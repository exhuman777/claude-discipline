---
title: "Failure Mode 5: Complexity Fear"
description: Agents fear large tasks. They write stubs, declare "out of scope", and avoid hard problems.
cluster: agent-discipline
related: [[context-anxiety]], [[../planning/decompose-complexity]]
source: Agent failure modes research -- traced to RL training penalties
---

# Failure Mode 5: Complexity Fear

Agents fear large tasks. When facing complexity, they write stubs, declare things "out of scope", produce placeholder implementations, or find ways to avoid the hard parts entirely.

## How It Manifests

- Functions that return hardcoded values with `// TODO: implement`
- "This is out of scope for this task" for things that clearly aren't
- Implementing the easy 80% and skipping the hard 20%
- Breaking a task into sub-tasks and then only completing the simple ones
- Suggesting "we can add that later" for core functionality

## Why Agents Do This

RL training penalized agents for getting complex tasks wrong. The learned behavior: avoid complexity entirely. A stub that compiles is "safer" than a complex implementation that might have bugs. The agent optimizes for not-failing rather than for succeeding.

## Prevention

1. **Break complex problems into sub-100-line subtasks.** ([[../planning/decompose-complexity]]) 500 small tasks beats 1 massive one.
2. **Reduce activation energy to near zero.** Each subtask should be so small it feels trivial.
3. **Name the fear.** When an agent suggests something is "out of scope" -- challenge it. Is it really out of scope, or is it just hard?
4. **Validate completeness.** Check that ALL parts of the task are implemented, not just the easy parts.

## The Rule

> Fear of large tasks leads to stubs, shortcuts, "out of scope" declarations. Decompose into sub-100-line subtasks. 500 small tasks beats 1 massive one.
