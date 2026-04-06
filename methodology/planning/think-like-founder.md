---
title: Think Like a Founder
description: Solutions must scale, fit the bigger picture, be maintainable. No contractor mindset.
cluster: planning
related: [[plan-before-code]], [[../agent-discipline/misalignment]]
source: Production principle -- from observing agent shortcuts that created tech debt
---

# Think Like a Founder

A contractor solves today's problem. A founder solves today's problem in a way that makes tomorrow's problems easier.

## The Difference

| Contractor Mindset | Founder Mindset |
|-------------------|-----------------|
| "Does it work now?" | "Does it work at 10x scale?" |
| "Fastest implementation" | "Best implementation for the long run" |
| "Not my problem later" | "I'll maintain this" |
| "Quick fix, move on" | "Fix it right, invest in quality" |
| "Meets the spec" | "Meets the intent behind the spec" |

## Application

When choosing between approaches:
1. Will this scale? (Not just 10 users -- think 10,000)
2. Can someone else understand this code in 6 months?
3. Does this create or reduce tech debt?
4. Does this fit the existing architecture or fight against it?

## The Rule

> Solutions must scale, fit the bigger picture, be maintainable. No quick fixes that create tech debt. No "it works for now" shortcuts.
