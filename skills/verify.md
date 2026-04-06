---
name: verify
description: Post-task verification. Prevents premature "done" claims (failure mode 6). Run before any commit or completion claim.
---

# Verification

Before claiming work is complete, prove it with evidence.

## Steps

1. **Identify what changed.** Run `git diff --stat` to see all modified files.

2. **Run compilation check.**
   - TypeScript: `npx tsc --noEmit`
   - Python: `python -m py_compile <file>`
   - Go: `go build ./...`
   - Other: language-appropriate compile/lint check
   - Show the output.

3. **Run tests.**
   - Run the full test suite (or relevant subset for large projects)
   - Show the output including pass/fail counts
   - If tests fail: fix them. Do not claim success.

4. **Verify the feature works.**
   - For UI changes: render it, check visual output
   - For API changes: make a request, check the response
   - For CLI changes: run the command, check the output
   - Show the actual output.

5. **Blast radius check.** Search for references to changed functions/variables:
   - Comments mentioning old behavior
   - Docs describing old behavior
   - Related code assuming old behavior
   - Update anything stale.

6. **Report evidence.**
   - Compilation: [output]
   - Tests: [pass/fail counts]
   - Feature verification: [actual output]
   - Blast radius: [references checked and updated]

## Pass Criteria

- Compilation passes with zero errors
- All tests pass
- Feature verified with actual output (not "it should work")
- Blast radius checked, references updated

## Fail Actions

If verification fails at any step:
- Fix the issue
- Re-run from that step
- Do NOT skip to "done"

## Methodology Reference

This skill implements prevention for failure mode 6 (verification laziness).
See: `methodology/verification/validate-before-claiming.md`
