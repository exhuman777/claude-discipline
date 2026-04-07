---
name: discipline-verify
description: Post-task verification that prevents premature done claims. Runs compilation, tests, feature checks, and blast radius analysis. Run before any commit or completion claim.
license: MIT
metadata:
  author: exhuman
  version: "1.0"
  plugin: claude-discipline
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

## Why This Matters

Verification laziness is failure mode #6. "Should work" is not evidence. Until you've run the check and seen the output, it doesn't work.

See the [claude-discipline methodology](https://github.com/exhuman777/claude-discipline) for the full skill graph.
