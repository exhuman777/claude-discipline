---
title: Compound Discipline
description: Each disciplined session makes the next one easier. Rules compound like interest.
cluster: cross-domain
related: [[../planning/plan-before-code]], [[../agent-discipline/harness-design]]
source: Compound engineering philosophy + production observation
---

# Compound Discipline

Traditional development accumulates technical debt. Disciplined development inverts this -- each session leaves the codebase better than it found it.

## The Compound Effect

- **Session 1:** Clean code, good tests, updated docs
- **Session 2:** Starts with clean context, less re-reading needed, builds faster
- **Session 3:** Patterns are established, less decision-making overhead
- **Session N:** The codebase practically writes itself because conventions are clear

Each disciplined session makes the next one cheaper (fewer tokens), faster (less context loading), and more reliable (established patterns).

## The Inverse

Without discipline, the opposite compounds:
- **Session 1:** Quick fix, no tests, docs not updated
- **Session 2:** Confusion about what Session 1 actually did, re-reads everything
- **Session 3:** Contradictory information, tests that don't test, growing uncertainty
- **Session N:** Agent can't trust anything in the codebase, everything takes 3x longer

## The Rule

Every session should leave the codebase in a state where the next session starts with better context, clearer patterns, and less uncertainty.
