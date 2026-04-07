# Ecosystem

claude-discipline works standalone. These complementary plugins cover capabilities that discipline doesn't -- memory, voice, strategic planning, knowledge graphs.

## Recommendation Matrix

| Plugin | What It Adds | Priority | Token Impact |
|--------|-------------|----------|-------------|
| **superpowers** | Think-before-code skills (TDD, debugging, brainstorming) | High | ~200-500/skill invocation |
| **MemPalace** | Palace memory + AAAK compression + temporal knowledge graph | High | ~170-900 at wake-up (L0+L1) |
| **claude-mem** | Cross-session memory (SQLite, automatic) | Medium | ~500-2000 at session start |
| **compound-engineering** | Strategic planning (brainstorm->plan->work->review->extract) | Medium | ~200-500/command |
| **voicemode** | Voice input/output (Whisper + Kokoro, offline) | Optional | 0 (runs external) |
| **arscontexta** | Knowledge graph builder for any domain | Optional | ~1000 at session start |

## Install Order

1. **claude-discipline** (this plugin) -- the foundation
2. **superpowers** -- process discipline (TDD, debugging workflows)
3. **MemPalace** -- persistent memory with palace architecture and AAAK compression
4. **claude-mem** -- simple cross-session memory (alternative to MemPalace)
4. **compound-engineering** -- strategic planning for larger tasks
5. **voicemode** -- if you prefer voice interaction
6. **arscontexta** -- if you want to build knowledge graphs

## Detailed Guides

- [[superpowers]] -- think-before-code discipline
- [[mempalace]] -- palace memory + AAAK compression + knowledge graph
- [[claude-mem]] -- cross-session memory
- [[voicemode]] -- voice interface
- [[compound-engineering]] -- strategic planning
- [[arscontexta]] -- knowledge graph building
- [[new-machine-setup]] -- full machine setup from scratch
