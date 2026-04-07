---
title: Memory
description: Persistent memory across sessions using the Palace architecture. Spatial organization (wings/halls/rooms), AAAK compression (30x lossless), temporal knowledge graphs, and 4-layer memory stacks.
type: moc
cluster: memory
source: "[MemPalace](https://github.com/milla-jovovich/mempalace) by milla-jovovich (MIT). Adapted for claude-discipline methodology format."
---

# Memory

The biggest waste in AI-assisted development isn't tokens -- it's amnesia. Every session starts from zero. Decisions get re-debated. Architecture gets re-explained. Debugging insights vanish. Six months of work, gone.

MemPalace solves this with three innovations: a spatial structure that makes memories findable, a compression dialect that makes them cheap to load, and a temporal knowledge graph that tracks how facts evolve. Combined with claude-discipline's efficiency methodology, this means an agent that remembers everything and wastes nothing.

## Architecture
- [[palace-architecture]] -- wings, halls, rooms, drawers, tunnels. Spatial structure that boosts retrieval by 34%.
- [[aaak-compression]] -- 30x lossless shorthand dialect. Months of context in ~120 tokens. Any model reads it natively.

## Storage
- [[knowledge-graph]] -- temporal knowledge graph (entities + triples). Facts have time windows. Query "what was true on March 15th."
- [[memory-layers]] -- 4-layer stack: L0 identity, L1 essential story, L2 on-demand, L3 deep search. Wake-up cost ~170-900 tokens.

## Practice
- [[session-persistence]] -- when to save, what to save, how to save. Auto-save hooks, pre-compact saves, diary patterns.

## Related Clusters
- [[../token-efficiency/_moc]] -- memory loading costs tokens; AAAK compression and layered loading minimize the cost
- [[../agent-discipline/_moc]] -- palace prevents failure mode 1 (incomplete context) by making prior decisions retrievable
- [[../verification/_moc]] -- knowledge graph enables fact verification across sessions
