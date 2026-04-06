# Token Efficiency Cheatsheet

| Situation | Action | Savings |
|-----------|--------|---------|
| Claude misunderstood | Edit original message, don't follow up | Prevents history stacking |
| Chat > 15-20 messages | Summarize -> new chat -> paste | Resets quadratic curve |
| Multiple questions | Batch into one prompt | 2x+ fewer context loads |
| Simple task | Use Haiku model | 50-70% cheaper |
| Reading a large file | Use offset/limit | Don't load 2000 lines |
| Going AFK > 5 min | Run /compact first | Avoid 10x cache rebuild |
| Tool schemas bloating | ENABLE_TOOL_SEARCH=true | -20K tokens/turn |
| Same file read 3+ times | Stop, use cached knowledge | Prevent redundant reads |
| CLAUDE.md too large | Keep under 200 lines | Saves on every turn |
| Verbose responses | Terse output (45 vs 180 tokens) | 75% per response |

## The Math

Cost formula: **S x N(N+1) / 2**

| Messages | Total Tokens (at 500/exchange) |
|----------|-------------------------------|
| 5        | 7,500                         |
| 10       | 27,500                        |
| 20       | 105,000                       |
| 30       | 232,500                       |

Message 30 costs 31x message 1.

## Config

```json
// ~/.claude/settings.json
{ "env": { "ENABLE_TOOL_SEARCH": "true" } }
```
