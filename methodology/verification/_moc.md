---
title: Verification
description: Prove it works before claiming it works. Real tests, fresh-context verification, blast radius analysis.
type: moc
cluster: verification
---

# Verification

The gap between "I think it works" and "I can prove it works" is where most bugs ship. This cluster closes that gap with concrete verification practices.

## Core Principle
- [[validate-before-claiming]] -- the foundation: never say "done" without fresh evidence

## Testing
- [[real-tests-only]] -- no weak tests that pass on approximations

## Independent Verification
- [[fresh-context-verification]] -- a separate agent verifies without builder bias

## Post-Change
- [[blast-radius-analysis]] -- after changes, check all references for contradictions

## Related Clusters
- [[../agent-discipline/_moc]] -- verification laziness (failure mode 6) is what this cluster prevents
- [[../planning/_moc]] -- good plans include verification steps
