---
title: Memory Layers
description: 4-layer memory stack from identity (50 tokens) to deep search (unlimited). Wake-up cost ~170-900 tokens for months of accumulated context.
cluster: memory
related: [[aaak-compression]], [[palace-architecture]], [[../token-efficiency/context-hygiene]]
source: "[MemPalace](https://github.com/milla-jovovich/mempalace) by milla-jovovich (MIT). Adapted for claude-discipline methodology format."
---

# Memory Layers

Loading all memory at session start would burn thousands of tokens before any work happens. Not loading any memory means starting from zero. The solution: a layered stack where cost scales with need.

## The 4 Layers

| Layer | What | Size | When Loaded |
|-------|------|------|-------------|
| L0 | Identity | ~50-100 tokens | Always (session start) |
| L1 | Essential story | ~500-800 tokens | Always (session start) |
| L2 | On-demand | ~200-500 each | When topic comes up |
| L3 | Deep search | Unlimited | When explicitly asked |

**L0: Identity** -- who the user is, core preferences, non-negotiable rules. Plain text. Costs almost nothing. Always loaded.

**L1: Essential story** -- the top drawers by importance, compressed with [[aaak-compression]]. Active projects, recent decisions, key relationships. 500-800 tokens covers months of history when compressed.

**L2: On-demand** -- wing/room filtered retrieval from the [[palace-architecture]]. When a topic comes up in conversation, pull the relevant room's contents. Each load costs 200-500 tokens.

**L3: Deep search** -- full semantic search across all drawers. Used when the user asks "didn't we discuss X?" or when a topic can't be found in the palace structure. Unlimited results but highest token cost.

**Wake-up cost:** L0 + L1 = ~170-900 tokens. For comparison, a typical CLAUDE.md alone is 500-2000 tokens. The memory system adds less context than most configuration files.

## Connection to Context Hygiene

This directly implements [[../token-efficiency/context-hygiene]]. Don't load what you don't need. The layer system ensures memory cost scales with actual need, not with total accumulated knowledge.

L2 on-demand loading mirrors the skill graph's own navigation: scan MOC descriptions (cheap), open relevant files only (targeted), follow wikilinks if deeper context needed (progressive).

## Loading Protocol

1. **Session start:** Load L0 + L1 automatically
2. **Topic detected:** Check if an L2 wing/room exists. Load if relevant.
3. **User asks about past:** Search L3. Pull the specific drawer.
4. **New fact learned:** File immediately into the appropriate wing/hall/room. Don't wait for session end.

## The Rule

> Load memory in layers. Identity always, story always, details on demand, deep search when asked. Never load everything.
