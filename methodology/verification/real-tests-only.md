---
title: Real Tests Only
description: Test actual production behavior. No tests that pass on approximations. If testing a button, simulate the click.
cluster: verification
related: [[validate-before-claiming]], [[../agent-discipline/verification-laziness]]
source: Production failures where weak tests passed but features were broken
---

# Real Tests Only

Never write weak tests that pass on approximations. Test actual production behavior.

## What Makes a Test "Real"

A real test verifies the actual behavior a user would experience:

- **Testing a button?** Confirm it exists in the DOM, simulate the click, verify the backend receives the correct payload.
- **Testing an API endpoint?** Make an actual HTTP request, check the status code AND the response body.
- **Testing a calculation?** Use real-world inputs, not just trivial cases. Check edge cases.
- **Testing a UI component?** Render it, check the output, interact with it.

## What Makes a Test "Weak"

- Checking that a function exists without calling it
- Assertions so loose they pass on any input (`expect(result).toBeTruthy()` when you should check the value)
- Only testing the happy path
- Mocking so much that you're testing the mocks, not the code
- Testing implementation details instead of behavior

## The Standard

For each test, ask: "If the feature was completely broken, would this test catch it?"

If the answer is "maybe" or "depends" -- the test is too weak.

## The Rule

> Never write weak tests that pass on approximations. Test actual production behavior. If testing a button: confirm it exists, simulate the click, verify the backend payload.
