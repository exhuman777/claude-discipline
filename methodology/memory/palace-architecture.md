---
title: Palace Architecture
description: Spatial memory organization using wings, halls, rooms, drawers, and tunnels. Structure alone improves retrieval by 34%.
cluster: memory
related: [[memory-layers]], [[aaak-compression]], [[../agent-discipline/incomplete-context]]
source: "[MemPalace](https://github.com/milla-jovovich/mempalace) by milla-jovovich (MIT). Adapted for claude-discipline methodology format."
---

# Palace Architecture

Ancient Greek orators memorized entire speeches by placing ideas in rooms of an imaginary building. Walk through the building, find the idea. MemPalace applies the same principle to AI memory: conversations are organized into a spatial hierarchy that makes them searchable without AI deciding what matters.

No summarization. No lossy extraction. Store everything, then make it findable.

## The Hierarchy

```
Palace
  Wing (person or project)
    Hall (memory type)
      Room (specific topic)
        Drawer (verbatim content)
          Closet (compressed summary)
```

**Wings** -- top-level containers. One per person, project, or domain. `wing_kai`, `wing_driftwood`, `wing_code`.

**Halls** -- five memory type corridors within each wing:
- `hall_facts` -- decisions, locked-in choices
- `hall_events` -- sessions, milestones, debugging
- `hall_discoveries` -- breakthroughs, insights
- `hall_preferences` -- habits, likes, opinions
- `hall_advice` -- recommendations, solutions

**Rooms** -- specific topics within a hall. `auth-migration`, `graphql-switch`, `ci-pipeline`. Created from folder structure or keyword detection.

**Drawers** -- the verbatim original content. Never summarized. Each drawer has an ID: `drawer_{wing}_{room}_{hash}`.

**Tunnels** -- cross-wing connections. When the same room name appears in multiple wings, a tunnel links them automatically. This is how "auth-migration" in the backend project connects to "auth-migration" in the frontend project.

## Why Structure Matters

Retrieval benchmarks from MemPalace show structure alone -- before any semantic search -- dramatically improves accuracy:

```
Search all closets:          60.9%  R@10
Search within wing:          73.1%  (+12%)
Search wing + hall:          84.8%  (+24%)
Search wing + room:          94.8%  (+34%)
```

The implication: you don't need smarter search. You need better organization.

## Applying the Palace (without MemPalace installed)

Even without the full MemPalace system, the palace metaphor improves any memory setup:

1. **Organize by wing first.** Separate memory by project or person, not by date.
2. **Classify into halls.** Is this a decision? A preference? A discovery? The type determines where to look later.
3. **Name rooms specifically.** "auth" is bad. "clerk-auth-migration" is good. Specificity enables tunnels.
4. **Keep drawers verbatim.** Don't let AI summarize your memory. The context around a decision is often more valuable than the decision itself.
5. **Let tunnels form naturally.** When the same topic appears across projects, the connection is the insight.

## The Rule

> Structure beats search. Organize spatially, find instantly.
