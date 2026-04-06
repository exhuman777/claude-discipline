---
title: Harness Design Principles
description: Orchestration principles that prevent failure modes structurally, not just through rules.
cluster: agent-discipline
related: [[agent-psychology]], [[incomplete-context]], [[verification-laziness]]
source: "How To Solve Problems Of Long Running, Autonomous Agentic Engineering Workflows"
---

# Harness Design Principles

Rules tell agents what to do. A harness makes it structurally difficult to do the wrong thing. These principles guide how to build systems around agents that prevent failure modes.

## The 6 Principles

### 1. Orchestration Layer Above Task Lists
Don't bloat the working agent with orchestration context. A separate layer manages task ordering, dependencies, and progress tracking. The working agent focuses on one task at a time.

### 2. Algorithmic Contracts
Every session has a contract that must be fulfilled before it can end. "Build feature X" is not a contract. "Feature X compiles, passes tests, handles errors, and docs are updated" is a contract.

### 3. Independent Verification
Fresh-context agents judge quality and verify "doneness." The builder should not be the sole judge of their own work. A separate agent with no sunk-cost bias provides honest assessment. ([[../verification/fresh-context-verification]])

### 4. Complexity Classification
Detect high-complexity prompts automatically. Auto-decompose into bite-sized tasks before the working agent sees them. This prevents [[complexity-fear]] by removing the fear trigger.

### 5. Blast Radius Analysis
After changes, ensure everything touched is contradiction-free. Automated checks for stale references, broken links, inconsistent naming. This prevents [[entropy-maximization]] structurally.

### 6. Telemetry on Everything
Collect prompts, traces, outcomes. Build rubrics. Iterate. You can't improve what you don't measure. Track which failure modes occur most and tighten the harness there.

## Key Insight

The harness should make the right behavior the path of least resistance. Don't rely on the agent choosing discipline -- make discipline the default.
