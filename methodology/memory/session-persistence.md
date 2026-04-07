---
title: Session Persistence
description: When to save, what to save, how to save. Auto-save hooks, pre-compact saves, diary patterns. No session should end with unsaved decisions.
cluster: memory
related: [[knowledge-graph]], [[palace-architecture]], [[../token-efficiency/cache-management]]
source: "[MemPalace](https://github.com/milla-jovovich/mempalace) by milla-jovovich (MIT). Adapted for claude-discipline methodology format."
---

# Session Persistence

The most common memory failure isn't retrieval -- it's saving. A session produces 20 decisions, 5 architecture choices, and 3 debugging insights. If none are saved, the next session starts from zero regardless of how good the retrieval system is.

## What to Save

Five memory types, classified by hall:

| Type | Markers | Hall |
|------|---------|------|
| **Decisions** | "let's use", "we decided", "instead of", "because" | hall_facts |
| **Preferences** | "I prefer", "always use", "never", "my rule is" | hall_preferences |
| **Milestones** | "it works", "shipped", "breakthrough", "figured out" | hall_events |
| **Problems** | "bug", "root cause", "workaround", "the fix was" | hall_discoveries |
| **Architecture** | "the pattern is", "this connects to", "the flow is" | hall_advice |

## When to Save

Three save triggers, ordered by reliability:

1. **Periodic (every 15 messages).** A hook or manual check. Scan the last 15 exchanges for decisions, preferences, and discoveries. File them.

2. **Pre-compact.** Before any context compression or `/compact` command. This is the safety net -- if context is about to be compressed, save everything worth keeping first. Connects to [[../token-efficiency/cache-management]].

3. **Session end.** Write a diary entry summarizing what happened, what was decided, what's next. This becomes the resume note for the next session.

## Save Protocol

For each memory worth saving:

1. **Classify** -- which hall? (decision, preference, milestone, problem, architecture)
2. **Route** -- which wing and room? Use the [[palace-architecture]] structure.
3. **Store** -- file as a drawer with verbatim context. Don't summarize.
4. **Graph** -- if it's a fact that changes state (new tool, team change, architecture shift), update the [[knowledge-graph]] with a new triple.

## Auto-Save Hooks

MemPalace provides Claude Code hooks that automate saves:

- **Stop hook** -- fires after every assistant response. Every 15 messages, blocks and tells the AI to save.
- **PreCompact hook** -- fires before context compression. Always blocks. Always saves.

These ensure no session ends with unsaved context, even if the user forgets to save manually.

## The Rule

> Save as you go. Every 15 messages, before every compact, at every session end. The best memory system is useless if you don't write to it.
