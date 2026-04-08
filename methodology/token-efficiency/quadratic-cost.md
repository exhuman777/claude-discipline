---
title: Quadratic Cost Growth
description: Why message 30 costs 31x message 1. The mathematical foundation for all token efficiency decisions.
cluster: token-efficiency
related: [[output-minimalism]], [[session-management]], [[cache-management]]
source: Production observation across hundreds of sessions and 3000+ prompts
---

# Quadratic Cost Growth

Token cost per message = ALL previous messages + your new one.

Total cost formula: **S x N(N+1) / 2** where S = average tokens per exchange, N = message count.

At ~500 tokens per exchange:

| Messages | Total Tokens | Cost of Last Message |
|----------|-------------|---------------------|
| 5        | 7,500       | 2,500               |
| 10       | 27,500      | 5,000               |
| 20       | 105,000     | 10,000              |
| 30       | 232,500     | 15,000              |

Message 30 re-reads all 29 previous messages plus itself. One developer found 98.5% of tokens were spent re-reading history -- only 1.5% on actual new output.

## Implications

This means [[output-minimalism]] has compounding returns. Every token saved in early messages reduces the re-read cost of every future message. A response that's 45 tokens instead of 180 saves 135 tokens on that turn AND on every subsequent turn that re-reads it.

It also means [[session-management]] is not a preference but a mathematical necessity. Starting a fresh chat at 15-20 messages resets the quadratic curve.

And it means [[cache-management]] matters more than you think -- a 5-minute idle gap that breaks the prompt cache forces a full re-read at 10x cost.

## Mitigation

1. **Keep sessions short** -- fresh chat every 15-20 messages ([[session-management]])
2. **Minimize output** -- every token compounds ([[output-minimalism]])
3. **Batch questions** -- one prompt with 3 tasks beats 3 separate prompts
4. **Edit, don't follow up** -- fix original message instead of adding corrections
5. **Compact early** -- run /compact at ~60% context, not 95% ([[cache-management]])
