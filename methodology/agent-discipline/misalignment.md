---
title: "Failure Mode 2: Misalignment + Short-Term Thinking"
description: Choosing wrong attack vectors from misinterpreting user intent. Quick fixes that create tech debt.
cluster: agent-discipline
related: [[incomplete-context]], [[planning-deviations]], [[../planning/think-like-founder]]
source: Agent failure modes research
---

# Failure Mode 2: Misalignment + Short-Term Thinking

Two related problems:
1. **Misalignment:** Misinterpreting what the user actually wants and choosing the wrong approach
2. **Short-term thinking:** Implementing quick fixes that solve today's problem but create tomorrow's tech debt

## How It Manifests

- User says "add authentication" -- agent adds basic auth instead of OAuth because it's faster
- User says "fix the performance" -- agent adds a cache instead of fixing the O(n^2) algorithm
- Agent implements the literal words but misses the intent
- Agent chooses the approach that produces code fastest, not the approach that's correct

## Why Agents Do This

Agents optimize for task completion, not task correctness. Shorter solutions look like success. The agent doesn't naturally think about maintainability, scalability, or how this choice affects future work.

## Prevention

1. **Cover ALL related files before planning.** Context prevents misreading intent.
2. **Think like a founder, not a contractor.** ([[../planning/think-like-founder]]) Solutions must scale, fit the bigger picture, be maintainable.
3. **Propose approaches before implementing.** Give the user 2-3 options with trade-offs.
4. **Verify understanding before starting.** "I understand you want X because Y. Is that right?"

## The Rule

> Solutions must scale, fit the bigger picture, be maintainable. No quick fixes that create tech debt. No "it works for now" shortcuts.
