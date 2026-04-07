# Memory Cheatsheet

## Palace Structure

```
Palace
  Wing (project/person)          -- "wing_driftwood", "wing_kai"
    Hall (memory type)           -- 5 types below
      Room (specific topic)      -- "clerk-auth-migration"
        Drawer (verbatim content)
        Closet (compressed)
    Tunnel (cross-wing link)     -- same room in 2+ wings
```

## 5 Hall Types

| Hall | Stores | Markers |
|------|--------|---------|
| `hall_facts` | Decisions, choices | "let's use", "we decided", "instead of" |
| `hall_events` | Milestones, sessions | "it works", "shipped", "figured out" |
| `hall_discoveries` | Breakthroughs, insights | "realized", "the trick is", "breakthrough" |
| `hall_preferences` | Habits, rules, opinions | "I prefer", "always", "never", "my rule" |
| `hall_advice` | Solutions, patterns | "the pattern is", "recommendation", "use X for Y" |

## Memory Layers

| Layer | What | Tokens | Loaded |
|-------|------|--------|--------|
| L0 | Identity | ~50-100 | Always |
| L1 | Essential story (AAAK) | ~500-800 | Always |
| L2 | On-demand (wing/room) | ~200-500 | When topic comes up |
| L3 | Deep search | Unlimited | When explicitly asked |

Wake-up: L0 + L1 = **~170-900 tokens**

## AAAK Format

```
Header:   FILE_NUM|PRIMARY_ENTITY|DATE|TITLE
Zettel:   ZID:ENTITIES|keywords|"quote"|WEIGHT|EMOTIONS|FLAGS
```

Entity codes: 3-letter uppercase (`KAI`, `PRI`, `ALC`)
Flags: `ORIGIN`, `CORE`, `SENSITIVE`, `PIVOT`, `GENESIS`, `DECISION`, `TECHNICAL`
Compression: **~30x** (1000 tokens -> ~33 tokens)

## Save Triggers

1. **Every 15 messages** -- scan and save
2. **Before /compact** -- safety net, save everything
3. **Session end** -- diary entry + resume note

## Knowledge Graph

```
Entity: name (type, {properties})
Triple: subject -> predicate -> object [valid_from, valid_to]
```

- Add new facts with `valid_from`
- Never delete -- **invalidate** with `valid_to`
- Query with `as_of` date for point-in-time truth

## Retrieval Accuracy

```
Flat search:       60.9%
+ Wing filter:     73.1%  (+12%)
+ Hall filter:     84.8%  (+24%)
+ Room filter:     94.8%  (+34%)
```

Structure alone improves retrieval by 34%.

---
Based on [MemPalace](https://github.com/milla-jovovich/mempalace) by milla-jovovich (MIT).
