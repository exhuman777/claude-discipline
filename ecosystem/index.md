# Ecosystem

claude-discipline works standalone. These complementary plugins cover capabilities that discipline doesn't -- memory, voice, strategic planning, knowledge graphs.

## Recommendation Matrix

| Plugin | What It Adds | Priority | Token Impact |
|--------|-------------|----------|-------------|
| **superpowers** | Think-before-code skills (TDD, debugging, brainstorming) | High | ~200-500/skill invocation |
| **claude-mem** | Cross-session memory (SQLite, automatic) | High | ~500-2000 at session start |
| **compound-engineering** | Strategic planning (brainstorm->plan->work->review->extract) | Medium | ~200-500/command |
| **voicemode** | Voice input/output (Whisper + Kokoro, offline) | Optional | 0 (runs external) |
| **arscontexta** | Knowledge graph builder for any domain | Optional | ~1000 at session start |

## Install Order

1. **claude-discipline** (this plugin) -- the foundation
2. **superpowers** -- process discipline (TDD, debugging workflows)
3. **claude-mem** -- memory across sessions
4. **compound-engineering** -- strategic planning for larger tasks
5. **voicemode** -- if you prefer voice interaction
6. **arscontexta** -- if you want to build knowledge graphs

## Detailed Guides

- [[superpowers]] -- think-before-code discipline
- [[claude-mem]] -- cross-session memory
- [[voicemode]] -- voice interface
- [[compound-engineering]] -- strategic planning
- [[arscontexta]] -- knowledge graph building
- [[new-machine-setup]] -- full machine setup from scratch
