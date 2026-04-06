---
title: Token Efficiency
description: The math of why tokens matter and 7 techniques to cut waste by 75%+. Covers cost model, caching, tool search, output minimalism, context hygiene, model selection, and session management.
type: moc
cluster: token-efficiency
---

# Token Efficiency

Claude doesn't count messages -- it counts tokens. Every message re-reads the entire conversation history. Message 30 costs 31x what message 1 cost. Understanding this cost model transforms how you use Claude Code.

## Core Concept
- [[quadratic-cost]] -- the mathematical reality that makes everything else in this cluster matter

## Configuration
- [[tool-search]] -- ENABLE_TOOL_SEARCH saves ~20K tokens/turn by deferring unused tool schemas
- [[cache-management]] -- prompt cache expiry after 5 min idle = 10x cost spike; /compact timing

## Session Habits
- [[session-management]] -- fresh chat every 15-20 messages, batch questions, edit-not-followup
- [[output-minimalism]] -- the caveman principle: 45 tokens beats 180 tokens, 75% savings per turn

## Context Hygiene
- [[context-hygiene]] -- file read discipline, skill loading discipline, layered memory
- [[model-selection]] -- haiku for drafts, sonnet for implementation, opus for architecture

## Related Clusters
- [[../agent-discipline/_moc]] -- context anxiety (failure mode 3) is often triggered by token waste
- [[../verification/_moc]] -- verification costs tokens too; do it efficiently
