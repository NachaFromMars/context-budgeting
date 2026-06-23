# context-budgeting — Keep OpenClaw context lean and recoverable

> Manage your context window with a clear partition model and pre-compression checkpointing. Prevents memory loss after compaction and cuts token costs before they spike.

[![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blueviolet)](https://github.com/NachaFromMars)

## Overview
context-budgeting brings discipline to OpenClaw's context window using a four-partition model that allocates space deliberately across objective, recent history, decision logs, and background knowledge. Before the window fills, it checkpoints critical state so nothing important is lost during compaction. It integrates with heartbeats to monitor usage and trigger cleanup automatically when context crosses 80%.

## Features
- **4-partition model** — Objective 10% / Short-term History 40% / Decision Logs 20% / Background Knowledge 20%
- **Pre-compression checkpoint** — write status, key decision, next step to `memory/hot/HOT_MEMORY.md`
- **Checkpoint script** — `scripts/gc_and_checkpoint.sh`
- **Heartbeat integration** — `/status` check every 30 min → if context >80%, trigger checkpoint

## Usage / Quick Start
1. Monitor via `/status` (heartbeat checks every ~30 min)
2. When context >80%, update `memory/hot/HOT_MEMORY.md` with current status, key decision, next step
3. Run:
```bash
scripts/gc_and_checkpoint.sh
```

## Trigger Keywords (OpenClaw)
context near limit, context >80%, memory loss after compaction, reduce token costs

## Related Skills
- [core-brain-mula](https://github.com/NachaFromMars/core-brain-mula) — zero-decay neural memory backend
- [memory-tiering](https://github.com/NachaFromMars/memory-tiering) — tiered memory management

---
Part of the [NachaFromMars](https://github.com/NachaFromMars) OpenClaw skill ecosystem.
