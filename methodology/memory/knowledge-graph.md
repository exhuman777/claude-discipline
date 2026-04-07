---
title: Knowledge Graph
description: Temporal knowledge graph that tracks entities, relationships, and how facts evolve over time. Query what was true at any point in history.
cluster: memory
related: [[palace-architecture]], [[session-persistence]], [[../verification/validate-before-claiming]]
source: "[MemPalace](https://github.com/milla-jovovich/mempalace) by milla-jovovich (MIT). Adapted for claude-discipline methodology format."
---

# Knowledge Graph

Facts change. You migrate from Auth0 to Clerk. A team member leaves. A dependency gets deprecated. A flat memory system treats old facts and new facts the same, creating contradictions that poison decisions.

A temporal knowledge graph solves this by storing facts as triples with time windows. "Kai works on Driftwood" is true from 2024-01 to 2025-06. "Kai works on Lighthouse" starts 2025-07. Query any point in time, get the truth as it was then.

## Structure

Two core tables:

**Entities** -- people, projects, tools, concepts. Each has a type, properties, and a creation date.

**Triples** -- relationships between entities. Subject-predicate-object with temporal validity.

```
Entity: kai (person, {role: "backend", seniority: "senior"})
Entity: driftwood (project, {type: "saas", domain: "analytics"})

Triple: kai -> works_on -> driftwood
        valid_from: 2024-01-15
        valid_to: 2025-06-30
        confidence: 1.0
        source: "onboarding conversation"
```

## Key Operations

- **Add entity** -- create or update a node (person, project, tool)
- **Add triple** -- add a relationship with `valid_from`. Auto-deduplicates.
- **Invalidate** -- mark a fact as ended (`valid_to`). Preserves history, doesn't delete.
- **Query entity** -- get all relationships (outgoing, incoming, or both) as of a specific date
- **Timeline** -- chronological story of an entity across all its relationships

## Why Temporal Matters

Without temporal validity, the graph accumulates contradictions:
- "Uses Auth0" AND "Uses Clerk" -- which is current?
- "Kai is on Driftwood" AND "Kai is on Lighthouse" -- which is now?

With temporal validity, both are true -- at different times. Query with `as_of="2025-03-01"` gets the right answer.

## Connection to Verification

The knowledge graph directly supports [[../verification/validate-before-claiming]]. Instead of guessing or searching chat history, query the graph: "What database does project X use?" The answer comes with a source reference and confidence score.

## The Rule

> Facts have lifespans. Store when they became true and when they stopped. Never overwrite -- invalidate and add new.
