# claude-mem

**What it solves:** Claude forgets everything between sessions. You re-explain your project every morning.

**Install:**
```bash
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
```
Restart Claude Code after install.

**How it works:** 5 lifecycle hooks: SessionStart (loads relevant memories), UserPromptSubmit (captures requests), PostToolUse (records actions), Summary (AI-compresses session), SessionEnd (stores for next time).

**Storage:** SQLite at `~/.claude-mem/claude-mem.db`. Everything local.

**Web viewer:** `http://localhost:37777` -- browse sessions, search history.

**How it complements discipline:** Discipline rules stay in CLAUDE.md (persistent by design). claude-mem handles session-specific knowledge -- what you built yesterday, architecture decisions, that bug you fixed last week.

**Token impact:** ~500-2000 tokens injected at session start. Saves 3-5 messages of re-explanation per session.

**Source:** github.com/thedotmack/claude-mem
