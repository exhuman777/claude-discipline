---
name: efficiency
description: Token efficiency advisor. Analyzes current session and suggests optimizations. Saves tokens and money.
---

# Token Efficiency Check

Analyze the current session and suggest optimizations.

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

## Recommendations

Based on the assessment, provide specific actions:
- "Run /compact now -- you're at ~65% context"
- "Start a fresh session -- 22 messages deep, quadratic cost is high"
- "Switch to Haiku for these remaining simple changes"
- "Batch your next 3 questions into one message"
- "Stop re-reading src/config.ts -- you've read it 3 times"

## Methodology Reference

See: `methodology/token-efficiency/_moc.md` for the full token efficiency cluster.
