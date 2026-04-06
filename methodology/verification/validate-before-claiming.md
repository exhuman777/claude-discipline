---
title: Validate Before Claiming
description: Never say "done" without fresh evidence. Run the check, show the output, then claim success.
cluster: verification
related: [[real-tests-only]], [[fresh-context-verification]], [[../agent-discipline/verification-laziness]]
source: Production rule -- from repeated "it works" claims that didn't work
---

# Validate Before Claiming

When building features -- test them. When showing data -- verify the source. When deploying -- check the URL loads. Never say "done" without fresh evidence.

## The Protocol

1. **Run the verification command.** Not "I would run" -- actually run it.
2. **Show the output.** Paste the actual result, not a paraphrase.
3. **Interpret the output.** Does it actually confirm what you're claiming?
4. **Then and only then** say "done" or "it works."

## Common Verification Commands

| Claim | Verification |
|-------|-------------|
| "Code compiles" | Run `npx tsc --noEmit` or equivalent, show output |
| "Tests pass" | Run test suite, show pass/fail output |
| "Feature works" | Run the feature, show the result |
| "Deployment succeeded" | Hit the URL, show the response |
| "Bug is fixed" | Reproduce the bug scenario, show it no longer occurs |

## Anti-Patterns

- "It should work" -- should is not evidence
- "I tested it manually" -- without showing output
- "The code looks correct" -- reading code is not testing
- "Tests pass" -- without running them in this session
- "Done" -- without any verification step at all

## The Rule

> When building features -- test them. When showing data -- verify the source. When deploying -- check the URL loads. Don't say "it's working" without proof.
