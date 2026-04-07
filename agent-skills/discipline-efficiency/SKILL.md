---
name: discipline-efficiency
description: Token efficiency advisor that analyzes session state and suggests optimizations. Checks message count, context usage, output verbosity, file read patterns, and model selection. Saves tokens and money.
license: MIT
metadata:
  author: exhuman
  version: "1.0"
  plugin: claude-discipline
---

# Token Efficiency Check

Analyze the current session and suggest optimizations.

## The Cost Problem

Token cost per message = ALL previous messages + new one.
Formula: S x N(N+1) / 2
Message 30 costs 31x message 1.

## Assessment

1. **Message count.** How many messages in this session?
   - Under 10: green -- low cost zone
   - 10-20: yellow -- consider batching remaining work
   - Over 20: red -- start a fresh session soon

2. **Context usage.** Estimate current context utilization:
   - Under 50%: green -- plenty of room
   - 50-70%: yellow -- run /compact soon
   - Over 70%: red -- run /compact now or start fresh

3. **Output pattern.** Review recent responses:
   - Are responses terse and direct? Good.
   - Are responses verbose with filler? Suggest trimming.
   - Is there narration between tool calls? Eliminate it.

4. **File read pattern.** Check for repeated reads:
   - Has any file been read more than twice? Flag it.
   - Are large files being read fully when only sections are needed? Flag it.

5. **Model appropriateness.** Is the current model right for the task?
   - Simple changes on Opus? Suggest Haiku.
   - Complex architecture on Haiku? Suggest Opus.

## Quick Reference

| Situation                 | Action                           | Savings         |
|---------------------------|----------------------------------|-----------------|
| Claude misunderstood      | Edit original, don't follow up   | No history stack|
| Chat > 15-20 messages     | Summarize -> new chat -> paste   | Reset quadratic |
| Multiple questions        | Batch into one prompt            | 2x+ fewer loads |
| Simple task               | Use Haiku model                  | 50-70% cheaper  |
| Going AFK > 5 min         | Run /compact first               | Avoid 10x spike |
| Tool schemas bloating     | ENABLE_TOOL_SEARCH=true          | -20K tokens/turn|
| Verbose responses         | Terse output (45 vs 180 tokens)  | 75% per turn    |

## Recommendations

Based on the assessment, provide specific actions:
- "Run /compact now -- you're at ~65% context"
- "Start a fresh session -- 22 messages deep, quadratic cost is high"
- "Switch to Haiku for these remaining simple changes"
- "Batch your next 3 questions into one message"
- "Stop re-reading src/config.ts -- you've read it 3 times"

See the [claude-discipline methodology](https://github.com/exhuman777/claude-discipline) for the full skill graph.
