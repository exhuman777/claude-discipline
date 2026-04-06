---
title: Entropy Kills Codebases
description: Without active maintenance, codebases drift toward confusion. Stale docs + changed code = misleading context.
cluster: cross-domain
related: [[../agent-discipline/entropy-maximization]], [[../verification/blast-radius-analysis]]
source: Thermodynamic metaphor applied to software maintenance
---

# Entropy Kills Codebases

In thermodynamics, entropy always increases without energy input. In codebases, confusion always increases without active maintenance.

Every change that doesn't update its references adds entropy. A comment that contradicts the code. A README that describes yesterday's API. A test description that doesn't match what the test does.

Individually, each one is harmless. Collectively, they make the codebase unnavigable -- for humans AND agents.

## Why This Is Worse for Agents

Agents take documentation at face value. A human might think "this comment looks stale, I'll check the actual code." An agent reads the comment, treats it as truth, and builds on it. Stale docs actively poison agent context.

## Prevention

This is why [[../verification/blast-radius-analysis]] exists -- checking references after every change is the energy input that prevents entropy.

And why [[../agent-discipline/entropy-maximization]] is a named failure mode -- agents naturally tend toward entropy because cleanup feels like overhead.
