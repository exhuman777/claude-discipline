---
name: audit
description: Pre-task context audit that prevents incomplete context failures. Verifies all related files are read, checks for contradictions, traces assumptions to source code. Run before any non-trivial coding task.
license: MIT
metadata:
  author: exhuman
  version: "1.0"
  plugin: claude-discipline
---

# Context Audit

Before starting work, verify you have complete and consistent context.

## Steps

1. **Identify the task scope.** What files will this task touch?

2. **Read all related files.** For each file in scope:
   - Read it fully (or relevant sections for large files)
   - Note any assumptions, interfaces, or contracts it defines

3. **Check for contradictions.** Across the files you've read:
   - Do any two files describe the same thing differently?
   - Are there comments that contradict the code?
   - Are there stale references to renamed/moved things?

4. **Verify assumptions.** For each assumption you're making:
   - Can you point to the source code that confirms it?
   - Or are you guessing based on a function name?

5. **Report.** State:
   - Files loaded: [list]
   - Contradictions found: [list or "none"]
   - Assumptions verified: [list]
   - Missing context: [list or "none"]

## Pass Criteria

- All related files read
- Zero unresolved contradictions
- All assumptions traced to source code
- No guesses presented as facts

## Fail Actions

If the audit fails:
- Load the missing files before proceeding
- Resolve contradictions (ask the user if unclear)
- Do NOT start coding until the audit passes

## Why This Matters

Incomplete context is failure mode #1 -- the most common agent failure. Coding without full context means every downstream decision is potentially wrong. Wrong context at start = everything downstream is wrong.

See the [claude-discipline methodology](https://github.com/exhuman777/claude-discipline) for the full skill graph.
