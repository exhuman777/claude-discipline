# Pre-Commit Verification Checklist

Run before every commit or "done" claim.

## Build
- [ ] Code compiles without errors
- [ ] No new warnings introduced
- [ ] Linter passes

## Tests
- [ ] All existing tests pass
- [ ] New tests written for changed behavior
- [ ] Tests are real (test actual behavior, not just existence)
- [ ] Edge cases covered

## Security
- [ ] No secrets in code or logs
- [ ] User input validated
- [ ] No injection vectors (SQL, XSS, command)

## Blast Radius
- [ ] Comments updated for changed behavior
- [ ] Docs reflect current state
- [ ] Related code checked for stale references
- [ ] Test descriptions match what tests actually test

## Evidence
- [ ] Compilation output shown
- [ ] Test results shown (pass/fail counts)
- [ ] Feature verified with actual output
- [ ] "Done" claim backed by evidence
