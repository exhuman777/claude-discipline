---
title: Fresh-Context Verification
description: A separate agent with no sunk-cost bias verifies the work. The builder should not be the sole judge.
cluster: verification
related: [[validate-before-claiming]], [[../agent-discipline/harness-design]]
source: Harness design principle 3 (Independent Verification)
---

# Fresh-Context Verification

The builder should not be the sole judge of their own work. A fresh-context agent -- one that didn't write the code -- provides honest verification without sunk-cost bias.

## Why Fresh Context

The agent that built a feature has spent tokens on it. It has rationalized design decisions. It has seen the tests pass (even if they're weak). It's invested in "this works." A fresh agent has none of that baggage.

## Implementation

1. **After completing a feature:** Dispatch a verification subagent
2. **Give it:** The requirements (not the implementation decisions) and the code to verify
3. **Ask it to:** Run tests, check edge cases, verify the feature actually works as specified
4. **Trust its judgment** over the builder's "it works" claim

## When To Use

- After any non-trivial feature implementation
- Before merging or deploying
- When the builder has been working in a long session (high [[../agent-discipline/context-anxiety]] risk)
- When the feature touches multiple systems

## Lightweight Alternative

If a full verification agent is overkill: start a fresh chat, paste the requirements, ask it to review the diff. Even this level of fresh-context review catches issues the builder missed.
