---
title: Output Minimalism
description: The caveman principle -- 45 tokens beats 180 tokens. 75% savings per turn, compounding.
cluster: token-efficiency
related: [[quadratic-cost]], [[session-management]]
source: Production comparison -- normal response ~180 tokens, terse response ~45 tokens
---

# Output Minimalism

Normal Claude response: ~180 tokens. Terse response: ~45 tokens. That's 75% saved per turn.

Because of [[quadratic-cost]], those savings compound across every subsequent message that re-reads the response.

## The Caveman Principle

Think of yourself as a caveman with limited tokens:

**Before (180 tokens):**
> "I'll now read the file to understand the current implementation, then I'll make the necessary changes to fix the bug you described. Let me start by examining the relevant code..."

**After (12 tokens):**
> Bug in line 42. Fixed. Test passes.

Same information. 93% fewer tokens.

## Rules

1. **Act first. Result next. Stop.** No preamble, no narration, no "Let me...", no "I'll now..."
2. **One sentence if it fits.** "Done." beats "I've completed the task for you."
3. **No filler openings.** Never start with "Sure!", "Of course!", "Absolutely!", "Great question!"
4. **Tool first, result second.** Run the tool, show the result. Don't narrate the plan to run the tool.
5. **Every output token costs the same as input.** Your verbose response gets re-read on every future turn.

## When Verbosity Is Correct

- Explaining complex architecture decisions
- Teaching the user something new
- Error explanations that prevent repeat questions

The test: will being verbose here SAVE tokens later by preventing follow-up questions? If yes, be verbose. Otherwise, be terse.
