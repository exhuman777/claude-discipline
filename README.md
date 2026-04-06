# claude-discipline

A harness that makes Claude Code disciplined, efficient, and methodical.

Skill graph methodology. Evidence-backed. Customizable.

---

## The Problem

Claude Code out of the box:
- **Burns tokens** -- message 30 costs 31x message 1, most users don't realize this
- **Cuts corners** -- 7 documented failure modes that get worse under context pressure
- **Skips verification** -- says "done" without evidence, writes weak tests that pass on approximations

## The Evidence

This isn't theory. It's distilled from:

- **3,000+ production prompts** across 28 projects
- **858 sessions / 18,903 turns / $1,619 spend** audited for waste
- **7 agent failure modes** identified, documented, and fixed
- **ENABLE_TOOL_SEARCH**: verified ~20K tokens/turn savings
- **Output minimalism**: verified 75% token savings per turn

## Quick Start

```bash
/plugin marketplace add exhuman/claude-discipline
/plugin install claude-discipline
# Restart Claude Code
/discipline:customize   # generate your CLAUDE.md
```

Or copy a template directly:
```bash
# 10 essential rules
cp templates/minimal.CLAUDE.md ~/CLAUDE.md

# 25 rules (recommended)
cp templates/standard.CLAUDE.md ~/CLAUDE.md

# Full 43 rules
cp templates/maximal.CLAUDE.md ~/CLAUDE.md
```

## Skills

| Skill | Purpose | When |
|-------|---------|------|
| `/discipline:audit` | Pre-task context check | Before non-trivial coding |
| `/discipline:verify` | Post-task verification | Before any commit or "done" claim |
| `/discipline:efficiency` | Token efficiency advisor | Mid-session or every ~15 messages |
| `/discipline:harness` | Failure mode detection | When quality feels like it's dropping |
| `/discipline:review` | Methodology-backed code review | After completing a feature |
| `/discipline:customize` | CLAUDE.md generator | Once, during setup |

## The Methodology

claude-discipline is built as a **skill graph** -- not a flat list of rules, but an interconnected network of methodology files the agent navigates.

```
methodology/
  index.md                  <- entry point
  token-efficiency/         <- 7 files on reducing waste
  agent-discipline/         <- 9 files on failure modes
  verification/             <- 4 files on proving it works
  planning/                 <- 4 files on thinking before coding
  security/                 <- 3 files on never shipping vulns
  cross-domain/             <- 3 files connecting everything
```

**Progressive disclosure:** The agent reads YAML descriptions first, follows relevant wikilinks, and loads only what the current situation needs. Most decisions happen before reading a single full file.

Each file is one atomic concept with:
- YAML frontmatter (title, description, cluster, related links)
- Prose with `[[wikilinks]]` woven in, carrying meaning about when and why to go deeper
- Actionable rules and examples

Inspired by [arscontexta](https://github.com/agenticnotetaking/arscontexta)'s skill graph architecture.

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
| [claude-mem](https://github.com/thedotmack/claude-mem) | Cross-session memory (SQLite) | `/plugin install claude-mem` |
| [compound-engineering](https://github.com/EveryInc/compound-engineering-plugin) | Strategic planning pipeline | `/plugin install compound-engineering` |
| [voicemode](https://github.com/mbailey/voicemode) | Voice input/output (offline) | `/plugin install voicemode` |
| [arscontexta](https://github.com/agenticnotetaking/arscontexta) | Knowledge graph builder | `/plugin install arscontexta` |

See `ecosystem/` for detailed setup guides and `ecosystem/new-machine-setup.md` for a full machine setup walkthrough.

## The 7 Failure Modes

| # | Mode | What Happens |
|---|------|-------------|
| 1 | Incomplete Context | Codes without reading all files. Everything downstream is wrong. |
| 2 | Misalignment | Quick fix instead of right fix. Tech debt accumulates. |
| 3 | Context Anxiety | Quality drops as context fills. Premature "done." |
| 4 | Planning Deviations | Does A' instead of A. All downstream code wires to wrong thing. |
| 5 | Complexity Fear | Stubs, TODOs, "out of scope." Avoids hard parts. |
| 6 | Verification Laziness | "Should work." Weak tests. No evidence. |
| 7 | Entropy Maximization | Changes code but leaves docs/comments stale. |

Each has a dedicated methodology file with causes, signs, and prevention.

## Contributing

To add a new methodology claim:

1. Create a markdown file in the appropriate cluster directory
2. Include YAML frontmatter: `title`, `description`, `cluster`, `related`, `source`
3. Write the claim with `[[wikilinks]]` to related concepts
4. Update the cluster's `_moc.md` to reference your new file
5. Submit a PR

To propose a new rule for the templates, open an issue with:
- The rule text
- The production failure that motivated it
- Which template tier(s) it belongs in

## License

MIT
