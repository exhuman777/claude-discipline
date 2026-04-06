# voicemode

**What it solves:** Typing context switches when debugging with both hands on keyboard. Voice is 3-5x faster for explanations.

**Install:**
```bash
/plugin marketplace add mbailey/voicemode
/plugin install voicemode
/voicemode:install
```

**Usage:** `/voicemode:converse` -- speak when you hear the chime.

**Offline mode (full privacy):**
```bash
voicemode service install whisper   # ~250MB
voicemode service install kokoro    # ~250MB
voicemode service start whisper
voicemode service start kokoro
```

**How it complements discipline:** No direct interaction with discipline rules. Voice input gets transcribed to text -- same token cost as typing, but faster input.

**Token note:** Faster input = more tokens per minute. Watch your session length.

**Source:** github.com/mbailey/voicemode
