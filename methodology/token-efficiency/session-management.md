---
title: Session Management
description: Fresh chat every 15-20 messages, batch questions, edit-not-followup. Combat quadratic cost growth.
cluster: token-efficiency
related: [[quadratic-cost]], [[cache-management]], [[output-minimalism]]
source: Mathematical analysis + production experience
---

# Session Management

At 15-20 messages, token costs are still manageable. Beyond that, [[quadratic-cost]] makes every message exponentially more expensive.

## Fresh Chat Protocol

When a session hits 15-20 messages:
1. Ask Claude to summarize the full context (what was done, what's pending, key decisions)
2. Copy the summary
3. Start new chat
4. Paste summary as first message
5. Continue working with a clean quadratic curve

## Batch Questions

Three separate prompts = three context loads. One prompt with three tasks = one context load.

**Wasteful:**
- "Summarize this article"
- "Now list the main points"
- "Now suggest a headline"

**Efficient:**
- "Summarize this article, list the main points, and suggest a headline."

Bonus: answers are often better because Claude sees the full picture upfront.

## Edit, Don't Follow Up

When Claude misunderstands, the instinct is to send "No, I meant..."

Every follow-up stacks onto conversation history. Claude re-reads ALL of it.

Instead: click Edit on your original message, fix it, regenerate. The old exchange gets replaced, not stacked. This prevents history accumulation.

## Rolling 5-Hour Window

Claude uses a rolling 5-hour window for rate limits, not midnight reset. Messages from 9 AM stop counting by 2 PM. Divide work into 2-3 sessions: morning, afternoon, evening.

## Off-Peak Hours

Since March 2026: rate limits consume faster during peak hours (5:00-11:00 AM Pacific, weekdays). Schedule heavy work for off-peak when possible.
