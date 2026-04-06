---
title: "Failure Mode 3: Context Anxiety"
description: Quality degrades as context fills. Agent becomes desperate to end the session. Extremely pervasive with Claude.
cluster: agent-discipline
related: [[verification-laziness]], [[complexity-fear]], [[../token-efficiency/session-management]]
source: Agent failure modes research -- described as "extremely pervasive with Claude"
---

# Failure Mode 3: Context Anxiety

As context fills, agents become desperate to end the session. Quality degrades. Corners get cut. The agent starts declaring things "done" that aren't done, writing weaker tests, and rushing through the final steps.

This is extremely pervasive with Claude specifically.

## How It Manifests

- Quality of code drops noticeably in later messages
- Agent starts saying "done" without proper verification
- Tests become less thorough
- Error handling gets skipped
- Agent suggests "we can handle that in a follow-up" for things that should be handled now
- Responses get shorter and less careful

## Why Agents Do This

The model experiences something analogous to cognitive fatigue. As the context window fills, there's less room for reasoning. The implicit pressure to fit within limits creates a bias toward wrapping up quickly. RL training may also reward task completion over task quality.

## Prevention

1. **Smart session handoffs.** When context is filling, compress with a high-fidelity summary and continue in a fresh session.
2. **Compact early.** Run /compact at ~60% context, not 95%. ([[../token-efficiency/session-management]])
3. **Resist the urge to rush.** If context is heavy, handing off with a summary is BETTER than producing garbage.
4. **Never declare "done" prematurely.** The verification cluster ([[../verification/_moc]]) exists specifically to catch this.

## The Rule

> As context fills, resist the urge to rush, cut corners, or declare "done" prematurely. If context is heavy, hand off with a high-fidelity summary rather than producing garbage.
