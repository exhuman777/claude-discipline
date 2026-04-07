---
title: AAAK Compression
description: A 30x lossless shorthand dialect for AI agents. Months of context in ~120 tokens. Any model reads it natively -- no decoder, no fine-tuning.
cluster: memory
related: [[palace-architecture]], [[memory-layers]], [[../token-efficiency/output-minimalism]]
source: "[MemPalace](https://github.com/milla-jovovich/mempalace) by milla-jovovich (MIT). Adapted for claude-discipline methodology format."
---

# AAAK Compression

AAAK is a lossless shorthand dialect designed for AI agents. Not meant to be read by humans -- meant to be read by your AI, fast. 30x compression, zero information loss. Your AI loads months of context in ~120 tokens.

Because AAAK is just structured text with a universal grammar, it works with any model that reads text -- Claude, GPT, Gemini, Llama, Mistral. No decoder, no fine-tuning, no cloud API required.

## Format

```
Header:   FILE_NUM|PRIMARY_ENTITY|DATE|TITLE
Zettel:   ZID:ENTITIES|topic_keywords|"key_quote"|WEIGHT|EMOTIONS|FLAGS
Tunnel:   T:ZID<->ZID|label
Arc:      ARC:emotion->emotion->emotion
```

**Entity codes** -- 3-letter uppercase. `ALC=Alice`, `KAI=Kai`, `PRI=Priya`. Auto-generated or configured.

**Emotion codes (18 universal):**
```
vul=vulnerability  joy=joy      fear=fear     trust=trust
grief=grief        wonder=wonder rage=rage     love=love
hope=hope          despair=despair peace=peace humor=humor
tender=tenderness  raw=honesty  doubt=doubt   relief=relief
anx=anxiety        exhaust=exhaustion
```

**Flags (7 types):**
```
ORIGIN    = birth of something
CORE      = identity pillar
SENSITIVE = handle with care
PIVOT     = emotional turning point
GENESIS   = led to something that exists
DECISION  = explicit choice
TECHNICAL = architecture or implementation
```

## Compression Example

```
Original (~1000 tokens):
  "Priya manages the Driftwood team: Kai (backend, 3 years), Soren
   (frontend), Maya (infrastructure), and Leo (junior, started last
   month). They're migrating auth from Auth0 to Clerk because of
   pricing and developer experience. Kai recommended the switch..."

AAAK (~120 tokens):
  TEAM: PRI(lead) | KAI(backend,3yr) SOR(frontend) MAY(infra) LEO(junior,new)
  PROJ: DRIFTWOOD(saas.analytics) | SPRINT: auth.migration->clerk
  DECISION: KAI.rec:clerk>auth0(pricing+dx) | ****
```

30x compression. Zero information loss. The AI reconstructs the full context from the structured shorthand.

## Connection to Token Efficiency

AAAK directly extends [[../token-efficiency/output-minimalism]]. Where output minimalism saves 75% on individual responses, AAAK saves 97% on stored memory. Combined effect: an agent that generates terse output AND loads compressed history costs a fraction of a verbose, forgetful one.

The [[memory-layers]] system uses AAAK for L1 (essential story) to keep wake-up cost under 900 tokens for months of accumulated context.

## The Rule

> Compress losslessly. 120 tokens should hold what 3000 tokens said.
