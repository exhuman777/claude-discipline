# New Machine Setup

Full walkthrough: fresh machine to fully configured Claude Code with discipline.

## Step 1: Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

## Step 2: Core Settings

Create `~/.claude/settings.json`:

```json
{
  "env": {
    "ENABLE_TOOL_SEARCH": "true"
  }
}
```

## Step 3: Install claude-discipline

**Option A: Plugin install:**
```bash
claude  # start a session
/plugin marketplace add exhuman777/claude-discipline
/plugin install claude-discipline@exhuman777-claude-discipline
```

**Option B: Manual skill install:**
```bash
git clone https://github.com/exhuman777/claude-discipline.git
cp -r claude-discipline/skills/* ~/.claude/skills/
```

Restart Claude Code.

## Step 4: Set Up Your CLAUDE.md

```bash
/claude-discipline:customize
```

Follow the interactive prompts. Or copy a template manually:

```bash
git clone https://github.com/exhuman777/claude-discipline.git

# Minimal (10 rules)
cp claude-discipline/templates/minimal.CLAUDE.md ~/CLAUDE.md

# Standard (25 rules, recommended)
cp claude-discipline/templates/standard.CLAUDE.md ~/CLAUDE.md

# Maximal (38 rules)
cp claude-discipline/templates/maximal.CLAUDE.md ~/CLAUDE.md
```

## Step 5: Install Complementary Plugins (Optional)

```bash
# Process discipline (TDD, debugging, brainstorming)
/plugin marketplace add obra/superpowers
/plugin install superpowers

# Cross-session memory
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem

# Strategic planning
/plugin marketplace add EveryInc/compound-engineering-plugin
/plugin install compound-engineering

# Voice (optional)
/plugin marketplace add mbailey/voicemode
/plugin install voicemode
/voicemode:install

# Knowledge graphs (optional)
/plugin marketplace add agenticnotetaking/arscontexta
/plugin install arscontexta@agenticnotetaking
```

Restart Claude Code after installing plugins.

## Step 6: Voice Setup (Optional, Offline)

```bash
voicemode service install whisper   # ~250MB
voicemode service install kokoro    # ~250MB
voicemode service start whisper
voicemode service start kokoro
```

Fully offline after install. ~500MB total.

## Step 7: Verify

Start a new Claude Code session and run:
- `/discipline:efficiency` -- should analyze your session
- `/discipline:customize` -- should offer interactive setup

You're done.
