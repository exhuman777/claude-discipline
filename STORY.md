# I audited hundreds of Claude Code sessions. Here's what I found.

---

## The problem nobody talks about

Claude Code is smart. But it's undisciplined.

Most users don't realize that token cost grows quadratically. The formula is S x N(N+1) / 2 -- where S is the size of a single message and N is the number of messages. That means message 30 costs 31x what message 1 cost. Not 30x. 31x. Because every message re-processes the entire conversation history.

A 30-message session where you could have used 15 messages costs you roughly 4x more. And that's before the quality degradation kicks in.

---

## The 7 failure modes

After auditing hundreds of sessions, I identified 7 recurring patterns where Claude Code breaks down. These aren't random -- they're predictable, documentable, and preventable.

**Pre-task failures:**

1. **Incomplete Context** -- Claude starts coding without reading all related files. It makes assumptions about function signatures, misses contradictions between files, and builds on wrong foundations. Everything downstream is wrong.

2. **Misalignment** -- Claude reaches for the fastest fix instead of the right fix. Quick patch instead of proper architecture. Contractor mindset instead of founder mindset.

**Mid-task failures:**

3. **Context Anxiety** -- As the context window fills up, quality degrades. Responses get shorter, less careful. Claude starts suggesting "follow-up tasks" for things that should be done now. It's rushing to finish before running out of room.

4. **Planning Deviations (A' != A)** -- You agree on plan A. Claude implements A' -- a "close enough" version that's simpler but subtly different. Every downstream component wires to the wrong thing. By the time you notice, the damage has cascaded.

5. **Complexity Fear** -- When a task is large, Claude produces stubs, TODO comments, "out of scope" declarations. It implements the easy 60% and punts on the hard 40%. The hard part is where the value is.

**Post-task failures:**

6. **Verification Laziness** -- "It should work." "Tests pass." But no output shown. No actual compilation run. No real test execution. Claude declares victory without evidence. This is the most dangerous failure mode because you trust the claim and move on.

7. **Entropy Maximization** -- Claude changes a function but doesn't update the comment above it. Changes behavior but doesn't update the docs. Renames a variable but misses 3 references. The codebase slowly fills with contradictions.

---

## The fix: agent psychology = human psychology

Here's the insight that changed everything: the same productivity methods that work on humans work on AI agents.

GTD (Getting Things Done) works on agents. TDD works on agents. Agile ceremonies work on agents. The failures I documented above -- rushing under pressure, cutting corners when tired, skipping verification, fearing complexity -- these are human failure modes too.

The fix isn't more prompting. It's methodology.

---

## What I built

claude-discipline is a skill graph -- not a flat list of rules, but an interconnected network of 68 markdown files the agent navigates using YAML frontmatter and wikilinks.

The key insight: progressive disclosure. The agent reads short descriptions first, follows only the relevant paths, and loads only what the current situation needs. Most decisions happen before reading a single full file. This matters because every token of loaded context costs money on every subsequent message.

It includes:

- 43 rules, each traced to a real production failure
- 7 methodology clusters (token efficiency, agent discipline, verification, planning, security, memory, cross-domain)
- 7 skills (audit, verify, efficiency, harness, review, memory, customize)
- 3 template tiers (10/25/43 rules)
- Full memory methodology based on [MemPalace](https://github.com/milla-jovovich/mempalace) -- palace architecture, AAAK compression, temporal knowledge graphs
- Ecosystem guide for complementary tools

---

## The memory problem

There's an 8th problem I didn't list in the failure modes because it's not a failure of discipline -- it's a failure of architecture: **every session starts from zero.**

Decisions, architecture debates, debugging insights -- all gone when the session ends. You re-explain the same constraints. You re-debate the same trade-offs. Six months of accumulated knowledge, evaporated.

claude-discipline now integrates the [MemPalace](https://github.com/milla-jovovich/mempalace) methodology -- the highest-scoring AI memory system ever benchmarked. Three concepts:

- **Palace Architecture** -- spatial memory organization (wings for projects, halls for memory types, rooms for topics). Structure alone improves retrieval by 34%.
- **AAAK Compression** -- a 30x lossless shorthand dialect. Months of context in ~120 tokens. Any model reads it natively.
- **Temporal Knowledge Graph** -- facts with time windows. "Uses Auth0" was true until March. "Uses Clerk" is true from March. Both preserved.

Works with or without MemPalace installed. The methodology teaches the principles; the MCP server automates the filing.

---

## The numbers that matter

**ENABLE_TOOL_SEARCH=true** saves ~20K tokens per turn. Verified. That's the single highest-impact configuration change you can make.

**The "caveman principle"** -- terse output instead of verbose narration -- saves 75% per turn. A normal Claude response is ~180 tokens. A terse response is ~45 tokens. Multiply that savings across every message in a session with quadratic cost growth.

**Prompt cache** expires after ~5 minutes idle. Every post-idle turn re-processes the entire conversation at full price -- roughly 10x the cost of a cached turn. Running /compact before stepping away is not optional.

**Fresh sessions at 15-20 messages** instead of pushing to 40+ saves more than any other habit. The quadratic cost means the last 10 messages of a 40-message session cost more than the first 30 combined.

**Palace memory** wake-up costs ~170-900 tokens for months of history. That's less than a typical CLAUDE.md file.

---

## How to use it

Three ways:

1. **Claude Code plugin** (full skill graph + slash commands):
```bash
/plugin marketplace add exhuman777/claude-discipline
/plugin install claude-discipline@exhuman777-claude-discipline
```

2. **Agent skills** (works with Claude Code, Cursor, Copilot, Codex):
```bash
npx skills add exhuman777/claude-discipline
```

3. **Just copy the CLAUDE.md template:**
- 10 rules (minimal) -- security, verification, planning basics
- 25 rules (standard) -- recommended for daily users
- 43 rules (maximal) -- full methodology for power users

---

## Recommendations

If you take nothing else from this:

1. Set `ENABLE_TOOL_SEARCH=true` in your Claude Code settings. 20K tokens saved per turn, zero downside.

2. Start fresh sessions every 15-20 messages. The quadratic cost will eat your budget otherwise.

3. Never accept "it should work" from Claude. Make it run the check. Make it show the output. Verification laziness is the most expensive failure mode because you ship bugs.

4. Run `/compact` before going AFK. The 5-minute cache expiry will cost you 10x on your next message if you don't.

5. Tell Claude to be terse. "Minimum viable output. Act first. Result next. Stop." Put this in your CLAUDE.md. 75% savings per turn.

6. Set up memory persistence. Use MemPalace, or at minimum, save decisions and discoveries at session end. Starting from zero every time is the most expensive habit.

---

This is distilled from real production work, not theory. Every rule exists because something went wrong without it.

MIT licensed. Use it, fork it, improve it.
