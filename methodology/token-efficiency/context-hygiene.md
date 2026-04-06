---
title: Context Hygiene
description: File read discipline, skill loading discipline, and layered memory architecture.
cluster: token-efficiency
related: [[tool-search]], [[quadratic-cost]], [[model-selection]]
source: Production audit -- one session read the same file 33 times
---

# Context Hygiene

Every file read adds tokens to context. Every loaded skill schema sits in context on every turn. Discipline here prevents massive waste.

## File Read Discipline

1. **Never read the same file more than twice per session.** Cache what you learned.
2. **Use offset/limit for large files.** Don't load 2000 lines when you need 10.
3. **Don't read files you don't need.** Check if the information is already in context.

One session was caught reading the same file 33 times. Each read added the full file content to the conversation history.

## Skill Loading Discipline

42 skills available, 19 used twice or less across 858 sessions. Each loaded skill schema consumes context on every turn.

**Rule: Only invoke skills directly relevant to the current task.** Don't load skills speculatively.

This is complementary to [[tool-search]] -- ENABLE_TOOL_SEARCH handles tool schemas, skill discipline handles skill schemas.

## Layered Memory Architecture

Not everything needs to be in context at once. A layered approach:

- **L0 (always loaded):** CLAUDE.md + core memory -- keep lean (under 200 lines)
- **L1-L3 (per-session):** Load one context per task, not all contexts
- **L4 (on demand):** Deep knowledge loaded only when referenced
- **L5 (point of use):** Credentials loaded only when making API calls

The key insight: L0 survives every compaction. Every line in L0 costs tokens across the entire session. Move details to referenced files.
