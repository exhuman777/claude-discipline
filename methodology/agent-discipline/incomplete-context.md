---
title: "Failure Mode 1: Incomplete Context"
description: Acting on wrong or missing information before the task begins. Everything downstream inherits the error.
cluster: agent-discipline
related: [[misalignment]], [[planning-deviations]], [[../planning/plan-before-code]]
source: Agent failure modes research + production failures
---

# Failure Mode 1: Incomplete Context

Acting on wrong or missing information before the task begins. This is the most dangerous failure mode because it propagates through everything downstream. Wrong context at start = every file touched, every test written, every decision made is building on a flawed foundation.

## How It Manifests

- Agent reads 2 of 5 relevant files, then starts coding
- Agent assumes a function signature without checking the actual code
- Agent misses a constraint documented in a different file
- Agent doesn't check for contradictory information across files

## Why Agents Do This

Context loading feels like wasted time. The agent wants to start producing output. Reading more files means more tokens spent before any visible progress. This creates a bias toward action over understanding.

## Prevention

1. **Read ALL related files before planning or coding.** Not most. All.
2. **Check for contradictory information.** Two files might describe the same thing differently.
3. **Verify assumptions against actual code.** Don't assume -- read the source.
4. **Use the `/discipline:audit` skill** before starting non-trivial tasks.

## The Rule

> Full context before action. Wrong context at start = everything downstream is wrong.

This connects to [[../planning/plan-before-code]] -- the planning phase should INCLUDE context gathering as an explicit step, not assume it happened.
