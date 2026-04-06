---
title: Model Selection
description: Right model for right task. Haiku for drafts, Sonnet for implementation, Opus for architecture.
cluster: token-efficiency
related: [[quadratic-cost]], [[context-hygiene]]
source: Anthropic pricing documentation + production experience
---

# Model Selection

You don't need Opus to fix a typo. Switching models per task saves 50-70% on simple operations.

## Decision Matrix

| Task Type | Model | Why |
|-----------|-------|-----|
| Drafts, formatting, grammar | Haiku | 50-70% cheaper, fast enough |
| Simple code changes, translations | Haiku | Doesn't need deep reasoning |
| Real implementation work | Sonnet | Good balance of capability and cost |
| Medium complexity, most coding | Sonnet | Default for daily work |
| Deep architecture decisions | Opus | Needs full reasoning capability |
| Complex debugging, system design | Opus | Worth the cost for correctness |

## In Claude Code

```bash
# Per-session model override
claude --model haiku

# In subagent tasks
# Set model: "haiku" for simple tasks in Task tool calls
```

## Subagent Model Selection

When dispatching subagents, match model to task complexity:
- File search, simple grep, formatting: Haiku
- Code modification, test writing: Sonnet
- Architecture review, complex analysis: Opus

This stacks with [[context-hygiene]] -- smaller models process context faster and cheaper.
