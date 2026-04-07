---
name: discipline-harness
description: Agent discipline enforcer that detects which of the 7 documented failure modes are active and provides specific redirects. Use when quality feels like it is dropping or as a proactive checkpoint.
license: MIT
metadata:
  author: exhuman
  version: "1.0"
  plugin: claude-discipline
---

# Discipline Harness

Identify and correct active failure modes.

## The 7 Failure Modes

### 1. Incomplete Context
**Signs:** Starting to code without reading all related files. Making assumptions about function signatures.
**Redirect:** Stop. Run a context audit before continuing.

### 2. Misalignment
**Signs:** Implementing the fastest solution rather than the best. Not considering scale or maintainability.
**Redirect:** Propose 2-3 approaches with trade-offs. Ask which fits the bigger picture.

### 3. Context Anxiety
**Signs:** Responses getting shorter and less careful. Suggesting "follow-up" for things that should be done now. Saying "done" without verification.
**Redirect:** Run /compact or hand off with a summary. Quality > speed.

### 4. Planning Deviations (A' != A)
**Signs:** Implementation differs from plan in "minor" ways. Using simpler alternatives without discussing.
**Redirect:** Re-read the plan. Compare each implementation step against it. Fix deviations before they cascade.

### 5. Complexity Fear
**Signs:** Stubs, TODO comments, "out of scope" declarations, implementing only the easy parts.
**Redirect:** Decompose the hard part into sub-100-line tasks. Tackle each one.

### 6. Verification Laziness
**Signs:** "It should work." "Tests pass" (without running them). No actual output shown.
**Redirect:** Run verification. Show evidence.

### 7. Entropy Maximization
**Signs:** Changed a function but didn't update the comment. Changed behavior but didn't update docs.
**Redirect:** Run blast radius check. Search for all references to changed things.

## Output

State which failure mode(s) are active and the specific redirect action. If none detected, say "No failure modes detected. Proceed."

## Why This Matters

Agent psychology = human psychology. The same failure modes that affect human developers (rushing under pressure, cutting corners, skipping verification) affect AI agents. This harness catches them in real time.

See the [claude-discipline methodology](https://github.com/exhuman777/claude-discipline) for the full skill graph.
