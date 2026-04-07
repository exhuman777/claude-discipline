---
name: discipline-memory
description: Session memory management using the MemPalace architecture. Classifies session knowledge into palace structure (wings/halls/rooms), persists decisions and discoveries, updates temporal knowledge graph. Run periodically (~15 messages), before /compact, and at session end.
license: MIT
metadata:
  author: exhuman
  version: "1.0"
  plugin: claude-discipline
---

# Memory Save

Persist session knowledge so the next session doesn't start from zero.

## Steps

1. **Scan recent context.** Review the last 15 exchanges (or since last save). Identify:
   - Decisions made ("let's use X", "we decided", "instead of")
   - Preferences stated ("I prefer", "always", "never", "my rule")
   - Milestones hit ("it works", "shipped", "figured out")
   - Problems solved ("the fix was", "root cause", "workaround")
   - Architecture defined ("the pattern is", "connects to", "the flow")

2. **Classify each memory.** Assign a hall type:
   - `hall_facts` -- decisions, locked-in choices
   - `hall_events` -- milestones, debugging sessions
   - `hall_discoveries` -- breakthroughs, insights
   - `hall_preferences` -- habits, opinions, rules
   - `hall_advice` -- recommendations, patterns, solutions

3. **Route to wing and room.** Which project (wing) and topic (room)?
   - Wing = the project or person this relates to
   - Room = the specific topic (be specific: "clerk-auth-migration" not "auth")

4. **Store verbatim.** Save the memory with its surrounding context. Don't summarize -- the context around a decision is often more valuable than the decision itself.

5. **Update knowledge graph (if applicable).** If a fact changed state:
   - New tool adopted -> add triple, invalidate old
   - Team change -> invalidate old role, add new
   - Architecture shift -> invalidate old pattern, add new

6. **Report.** State:
   - Memories saved: [count by hall type]
   - Knowledge graph updates: [list or "none"]
   - Next save trigger: [message count or event]

## Pass Criteria

- All decisions from the scan window identified and saved
- Each memory classified into the correct hall
- Each memory routed to the correct wing/room
- Knowledge graph updated for any state changes
- No session ends with unsaved decisions

## Fail Actions

If memories are missed:
- Re-scan with broader markers
- Check for implicit decisions (actions taken without explicit "we decided")
- If unsure about classification, default to `hall_facts`

## Why This Matters

Every conversation produces decisions, discoveries, and preferences that vanish when the session ends. The MemPalace architecture provides a spatial structure (wings/halls/rooms) that makes stored memories 34% more retrievable than flat storage. Combined with AAAK compression, months of context load in ~120 tokens.

See the [claude-discipline methodology](https://github.com/exhuman777/claude-discipline) for the full skill graph.
Based on [MemPalace](https://github.com/milla-jovovich/mempalace) by milla-jovovich (MIT).
