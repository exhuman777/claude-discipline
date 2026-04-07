```
     _ _          _       _ _
  __| (_)___  ___(_)_ __ | (_)_ __   ___
 / _` | / __|/ __| | '_ \| | | '_ \ / _ \
| (_| | \__ \ (__| | |_) | | | | | |  __/
 \__,_|_|___/\___|_| .__/|_|_|_| |_|\___|
                    |_|
```

<p align="center">
  <strong>claude-discipline</strong>
</p>

<p align="center">
  <em>A harness that makes Claude Code disciplined, efficient, and methodical.</em>
</p>

<p align="center">
  <a href="#the-problem">Problem</a> &middot;
  <a href="#quick-start">Quick Start</a> &middot;
  <a href="#skills">Skills</a> &middot;
  <a href="#the-methodology">Methodology</a> &middot;
  <a href="#the-7-failure-modes">Failure Modes</a> &middot;
  <a href="#ecosystem">Ecosystem</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/format-skill_graph-orange?style=flat-square" alt="Format">
  <img src="https://img.shields.io/badge/files-68_markdown-black?style=flat-square" alt="Files">
  <img src="https://img.shields.io/badge/evidence-3000%2B_prompts-amber?style=flat-square" alt="Evidence">
  <img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="License">
</p>

---

## The Problem

Claude Code out of the box is smart but undisciplined:

- **Burns tokens** -- message 30 costs 31x message 1, most users don't realize this
- **Cuts corners** -- 7 documented failure modes that get worse under context pressure
- **Skips verification** -- says "done" without evidence, writes weak tests that pass on approximations
- **Forgets everything** -- every session starts from zero. Decisions, architecture, debugging insights -- gone

## The Evidence

This isn't theory. It's distilled from real production use:

```
3,000+ production prompts    across 28 projects
  858  sessions audited      18,903 turns / $1,619 spend
    7  failure modes         identified, documented, and fixed
  20K  tokens/turn saved     via ENABLE_TOOL_SEARCH (verified)
  75%  output savings        via caveman principle (verified)
   43  rules distilled       each from a real production failure
```

## Quick Start

**Claude Code plugin** (full skill graph + slash commands):
```bash
/plugin marketplace add exhuman777/claude-discipline
/plugin install claude-discipline@exhuman777-claude-discipline
# Restart Claude Code
/discipline:customize   # generate your CLAUDE.md
```

**Agent Skills** (works with any agent -- Claude Code, Cursor, Copilot, Codex):
```bash
npx skills add exhuman777/claude-discipline
```

**Or copy a template directly:**
```bash
cp templates/minimal.CLAUDE.md ~/CLAUDE.md     # 10 essential rules
cp templates/standard.CLAUDE.md ~/CLAUDE.md    # 25 rules (recommended)
cp templates/maximal.CLAUDE.md ~/CLAUDE.md     # full 43 rules
```

## Skills

7 skills that enter the methodology graph at the right point:

| Skill | Purpose | When |
|-------|---------|------|
| `/discipline:audit` | Pre-task context check | Before non-trivial coding |
| `/discipline:verify` | Post-task verification | Before any commit or "done" claim |
| `/discipline:efficiency` | Token efficiency advisor | Mid-session or every ~15 messages |
| `/discipline:harness` | Failure mode detection | When quality feels like it's dropping |
| `/discipline:review` | Methodology-backed code review | After completing a feature |
| `/discipline:memory` | Session memory persistence | Every ~15 messages, before /compact, session end |
| `/discipline:customize` | CLAUDE.md generator | Once, during setup |

## The Methodology

claude-discipline is built as a **skill graph** -- not a flat list of rules, but an interconnected network of methodology files the agent navigates.

```
methodology/
  index.md                     <- entry point (root MOC)
  token-efficiency/            <- 7 files on reducing waste
    quadratic-cost.md              why message 30 costs 31x message 1
    cache-management.md            5-minute cache expiry awareness
    tool-search.md                 ENABLE_TOOL_SEARCH saves 20K/turn
    output-minimalism.md           caveman principle (75% savings)
    context-hygiene.md             file read + skill loading discipline
    model-selection.md             right model for right task
    session-management.md          fresh chat protocol
  agent-discipline/            <- 9 files on failure modes
    incomplete-context.md          failure mode 1
    misalignment.md                failure mode 2
    context-anxiety.md             failure mode 3
    planning-deviations.md         failure mode 4 (A' != A)
    complexity-fear.md             failure mode 5
    verification-laziness.md       failure mode 6
    entropy-maximization.md        failure mode 7
    harness-design.md              orchestration principles
    agent-psychology.md            why GTD works on agents
  verification/                <- 4 files on proving it works
  planning/                    <- 4 files on thinking before coding
  security/                    <- 3 files on never shipping vulns
  memory/                      <- 5 files on persistent memory (MemPalace)
    palace-architecture.md         spatial organization (wings/halls/rooms)
    aaak-compression.md            30x lossless compression dialect
    knowledge-graph.md             temporal fact tracking
    memory-layers.md               4-layer loading stack (L0-L3)
    session-persistence.md         save patterns and hooks
  cross-domain/                <- 3 files connecting everything
```

**How it works:**

```
Agent receives task
        |
        v
+------------------+     +------------------+     +------------------+
| 1. SCAN          |---->| 2. NAVIGATE      |---->| 3. APPLY         |
| Read YAML        |     | Follow relevant  |     | Use rules from   |
| descriptions     |     | [[wikilinks]]    |     | loaded files     |
+------------------+     +------------------+     +------------------+
        |                         |                         |
   Most decisions            Only relevant            Actionable
   happen here               paths followed           rules applied
```

Each file is one atomic concept with:
- YAML frontmatter (title, description, cluster, related links)
- Prose with `[[wikilinks]]` woven in, carrying meaning about when and why to go deeper
- Actionable rules and examples

Inspired by [arscontexta](https://github.com/agenticnotetaking/arscontexta)'s skill graph architecture.

## The 7 Failure Modes

```
+---------------------+     +---------------------+     +---------------------+
|    PRE-TASK          |     |    DURING TASK       |     |    POST-TASK         |
|                      |     |                      |     |                      |
| 1. Incomplete        |     | 3. Context Anxiety   |     | 6. Verification      |
|    Context           |     |    (quality drops)    |     |    Laziness           |
|                      |     |                      |     |    ("should work")    |
| 2. Misalignment      |     | 4. Planning          |     |                      |
|    (wrong approach)   |     |    Deviations        |     | 7. Entropy           |
|                      |     |    (A' != A)          |     |    Maximization       |
|                      |     |                      |     |    (stale docs)       |
|                      |     | 5. Complexity Fear   |     |                      |
|                      |     |    (stubs, "out of    |     |                      |
|                      |     |     scope")           |     |                      |
+---------------------+     +---------------------+     +---------------------+
```

| # | Mode | Signs | Fix |
|---|------|-------|-----|
| 1 | **Incomplete Context** | Coding without reading all files | Read ALL related files first |
| 2 | **Misalignment** | Quick fix instead of right fix | Think founder, not contractor |
| 3 | **Context Anxiety** | Quality drops late in session | /compact or hand off summary |
| 4 | **Planning Deviations** | A' instead of A | Verify against plan each step |
| 5 | **Complexity Fear** | Stubs, "out of scope" | Decompose to sub-100-line tasks |
| 6 | **Verification Laziness** | "Should work", no evidence | Run checks, show output |
| 7 | **Entropy Maximization** | Stale docs after changes | Update ALL references |

Each has a dedicated methodology file with causes, signs, and prevention. Key insight: **agent psychology = human psychology.** Same fixes that make humans productive (GTD, TDD, Agile) work on agents.

## Memory (MemPalace Integration)

claude-discipline now includes a full memory methodology based on [MemPalace](https://github.com/milla-jovovich/mempalace) -- the highest-scoring AI memory system ever benchmarked. Open source, MIT licensed, runs entirely local.

**The problem:** Every session starts from zero. Decisions, architecture debates, debugging insights -- gone.

**The solution:** Three innovations adapted into the discipline methodology:

| Concept | What | Impact |
|---------|------|--------|
| **Palace Architecture** | Spatial memory: wings (projects), halls (memory types), rooms (topics) | +34% retrieval accuracy from structure alone |
| **AAAK Compression** | 30x lossless shorthand dialect for AI agents | Months of context in ~120 tokens |
| **Temporal Knowledge Graph** | Facts with time windows (valid_from/valid_to) | Query what was true at any point in history |

**With MemPalace installed:** Use the MCP server for automated memory filing, search, and compression.
**Without MemPalace:** Apply the palace methodology manually with any storage (markdown, SQLite, etc.).

See `methodology/memory/` for the full knowledge cluster and `ecosystem/mempalace.md` for the setup guide.

## Templates

Three tiers of CLAUDE.md:

| Template | Rules | For |
|----------|-------|-----|
| `minimal.CLAUDE.md` | 10 | Anyone -- security, verification, planning basics |
| `standard.CLAUDE.md` | 25 | Daily users -- adds token efficiency, failure mode guards |
| `maximal.CLAUDE.md` | 43 | Power users -- everything, with customizable sections |

Use `/discipline:customize` for an interactive generator that asks about your workflow and produces a tailored CLAUDE.md.

## Ecosystem

claude-discipline works standalone. These complementary plugins extend it:

| Plugin | Adds | Install |
|--------|------|---------|
| [superpowers](https://github.com/obra/superpowers) | TDD, debugging, brainstorming workflows | `/plugin install superpowers` |
| [MemPalace](https://github.com/milla-jovovich/mempalace) | Palace memory + AAAK compression + knowledge graph | `pip install mempalace` |
| [claude-mem](https://github.com/thedotmack/claude-mem) | Cross-session memory (SQLite) | `/plugin install claude-mem` |
| [compound-engineering](https://github.com/EveryInc/compound-engineering-plugin) | Strategic planning pipeline | `/plugin install compound-engineering` |
| [voicemode](https://github.com/mbailey/voicemode) | Voice input/output (offline) | `/plugin install voicemode` |
| [arscontexta](https://github.com/agenticnotetaking/arscontexta) | Knowledge graph builder | `/plugin install arscontexta` |

See `ecosystem/` for detailed setup guides and `ecosystem/new-machine-setup.md` for a full machine setup walkthrough.

## Token Efficiency Quick Reference

```
+---------------------------+----------------------------------+-----------------+
| Situation                 | Action                           | Savings         |
+---------------------------+----------------------------------+-----------------+
| Claude misunderstood      | Edit original, don't follow up   | No history stack|
| Chat > 15-20 messages     | Summarize -> new chat -> paste   | Reset quadratic |
| Multiple questions        | Batch into one prompt            | 2x+ fewer loads |
| Simple task               | Use Haiku model                  | 50-70% cheaper  |
| Going AFK > 5 min         | Run /compact first               | Avoid 10x spike |
| Tool schemas bloating     | ENABLE_TOOL_SEARCH=true          | -20K tokens/turn|
| Verbose responses         | Terse output (45 vs 180 tokens)  | 75% per turn    |
+---------------------------+----------------------------------+-----------------+

Cost formula: S x N(N+1) / 2
Message 30 costs 31x message 1.
```

## Contributing

To add a new methodology claim:

1. Create a markdown file in the appropriate cluster directory
2. Include YAML frontmatter: `title`, `description`, `cluster`, `related`, `source`
3. Write the claim with `[[wikilinks]]` to related concepts
4. Update the cluster's `_moc.md` to reference your new file
5. Submit a PR

To propose a new rule for the templates, open an issue with the rule text, the production failure that motivated it, and which template tier(s) it belongs in.

## License

MIT
