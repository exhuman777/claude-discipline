---
title: ENABLE_TOOL_SEARCH
description: Defer unused tool schemas to save ~20K tokens per turn. One setting, massive impact.
cluster: token-efficiency
related: [[quadratic-cost]], [[context-hygiene]]
source: Verified measurement -- context dropped from 45K to 20K baseline after enabling
---

# ENABLE_TOOL_SEARCH

By default, Claude Code loads ALL tool schemas into context on every turn. Most tools are never used in a given session. This wastes ~20K+ tokens per turn.

## The Fix

Add to `~/.claude/settings.json`:

```json
{
  "env": {
    "ENABLE_TOOL_SEARCH": "true"
  }
}
```

This defers tool definitions that exceed 10% of context window. Tools load on-demand only when needed.

## Impact

- Context baseline dropped from 45K to 20K tokens
- Over 858 sessions, estimated 264M tokens saved
- Zero functionality loss -- tools still available, just loaded when called

## Why This Matters

Because of [[quadratic-cost]], those 20K saved tokens compound across every message. In a 20-message session, that's roughly 400K fewer tokens processed total. This single setting is the highest-ROI optimization available.

## Interaction with Skills

This works with [[context-hygiene]] -- skills loaded speculatively also waste context. ENABLE_TOOL_SEARCH handles tool schemas; skill discipline handles skill schemas.
