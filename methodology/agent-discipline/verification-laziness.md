---
title: "Failure Mode 6: Verification Laziness"
description: Weak tests that pass on approximations. Premature "done" claims. Testing A' while claiming A works.
cluster: agent-discipline
related: [[planning-deviations]], [[context-anxiety]], [[../verification/_moc]]
source: Agent failure modes research
---

# Failure Mode 6: Verification Laziness

Agents write weak tests, watch them pass, declare success. Under context pressure (see [[context-anxiety]]), they'll test behavior A' and claim behavior A works.

## How It Manifests

- Tests that check a function exists but not what it returns
- Tests that pass on any input (assertions too loose)
- "Manual verification" that consists of reading the code, not running it
- Claiming "tests pass" without actually running them
- Testing the happy path only, ignoring edge cases
- Saying "it works" based on the code looking correct

## Why Agents Do This

Writing thorough tests takes tokens and time. Under context pressure, verification feels like overhead. The agent knows it should verify but rationalizes that the implementation "looks correct." This is reinforced when weak tests pass -- it feels like confirmation.

## Prevention

1. **Test ACTUAL production behavior.** ([[../verification/real-tests-only]])
   - If testing a button: confirm it exists, simulate the click, verify the backend payload
   - If testing an API: make the actual HTTP request, check the actual response
2. **Use a fresh-context verification agent.** ([[../verification/fresh-context-verification]]) An independent agent that verifies without the builder's biases.
3. **Until you can verify something actually works -- it doesn't.** This is the mantra.
4. **Run verification commands and show output.** No claiming without evidence.

## The Rule

> Never write weak tests that pass on approximations. Test actual production behavior. Until verified -- it doesn't work.
