# MemPalace

**Repo:** [github.com/milla-jovovich/mempalace](https://github.com/milla-jovovich/mempalace)
**License:** MIT
**Stack:** Python 3.9+, ChromaDB, SQLite
**What it adds:** Persistent memory across sessions with spatial organization and 30x lossless compression

## Why

claude-discipline makes Claude efficient and disciplined within a session. MemPalace makes knowledge persist across sessions. Together: a disciplined agent with perfect memory.

## Install

```bash
pip install mempalace
# or from source
git clone https://github.com/milla-jovovich/mempalace.git
cd mempalace && pip install -e .
```

## MCP Server Setup

MemPalace exposes 19 tools via an MCP server that Claude Code can use directly:

```bash
claude mcp add mempalace -- python -m mempalace.mcp_server
```

This gives Claude access to palace search, memory filing, knowledge graph queries, AAAK compression, and diary writes -- all within the conversation.

## First Run

```bash
mempalace init
```

Guided onboarding creates:
- `~/.mempalace/config.json` -- palace path, collection name, topic wings
- `~/.mempalace/identity.txt` -- L0 identity (write this yourself)
- `~/.mempalace/entity_registry.json` -- known people, projects, aliases
- `~/.mempalace/aaak_entities.md` -- entity code reference

## Mining Existing Conversations

```bash
# Import Claude conversations
mempalace mine convos ~/path/to/claude-exports/

# Import project files
mempalace mine projects ~/path/to/project/ --config mempalace.yaml
```

## Auto-Save Hooks

MemPalace provides two Claude Code hooks that automate memory persistence:

**Save hook** (fires every 15 messages):
```json
{
  "hooks": {
    "Stop": [{
      "matcher": "*",
      "hooks": [{
        "type": "command",
        "command": "/path/to/hooks/mempal_save_hook.sh",
        "timeout": 30
      }]
    }]
  }
}
```

**Pre-compact hook** (fires before context compression):
```json
{
  "hooks": {
    "PreCompact": [{
      "hooks": [{
        "type": "command",
        "command": "/path/to/hooks/mempal_precompact_hook.sh",
        "timeout": 30
      }]
    }]
  }
}
```

Add these to `~/.claude/settings.local.json`.

## Integration with claude-discipline

The `/discipline:memory` skill works with or without MemPalace installed:

- **Without MemPalace:** The skill teaches the palace methodology. You organize memory manually using the wing/hall/room structure in whatever storage you have (markdown files, CLAUDE.md, etc.).
- **With MemPalace:** The skill uses MCP tools to file memories directly into the palace, compress with AAAK, and update the knowledge graph.

## Token Impact

| Action | Cost |
|--------|------|
| L0 + L1 wake-up | ~170-900 tokens |
| L2 room retrieval | ~200-500 tokens per room |
| L3 deep search | Variable (depends on results) |
| AAAK compressed context | ~30x smaller than raw |

For comparison: a typical CLAUDE.md is 500-2000 tokens. MemPalace's wake-up costs less than most config files while carrying months of history.

## Key Concepts

See the claude-discipline methodology for detailed explanations:
- `methodology/memory/palace-architecture.md` -- spatial structure
- `methodology/memory/aaak-compression.md` -- 30x compression dialect
- `methodology/memory/knowledge-graph.md` -- temporal fact tracking
- `methodology/memory/memory-layers.md` -- 4-layer loading stack
- `methodology/memory/session-persistence.md` -- save patterns and hooks
