---
title: Cache Management
description: Prompt cache expiry awareness and /compact timing. A 5-minute idle gap costs 10x.
cluster: token-efficiency
related: [[quadratic-cost]], [[session-management]]
source: Production measurement -- 12.3M tokens wasted on idle gaps in one audit period
---

# Cache Management

Prompt caching stores static context (system prompts, CLAUDE.md, repeated file content) so it doesn't get reprocessed every turn. This is automatic in Claude Code.

## The 5-Minute Rule

The prompt cache expires after approximately 5 minutes of inactivity. Every post-idle turn re-processes the entire conversation at full price -- a 10x cost spike.

In one audit: 54% of turns came after 5+ minute idle gaps. 12.3M tokens wasted on cache rebuilds alone.

## /compact Timing

Auto-compaction triggers at ~83.5% of context window. Claude summarizes older context to free space.

The problem: compacting at 95% produces worse summaries because there's less room to work. Compacting at 60% produces sharper summaries and preserves more critical context.

**Rule: Run /compact manually at ~60% capacity, not 95%.**

## Before Going AFK

If stepping away for more than 5 minutes:
1. Run `/compact` first -- reduces the re-read cost when you return
2. Or accept you'll pay full price on return

## Keep CLAUDE.md Stable

CLAUDE.md survives every compaction and loads into every request. Editing it mid-session breaks the prompt cache. Make CLAUDE.md changes between sessions, not during.

## Related

This interacts with [[quadratic-cost]] -- cache breaks compound the quadratic growth. And with [[session-management]] -- starting fresh after AFK is sometimes cheaper than paying the cache rebuild.
