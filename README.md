# Production AI Coding Rules & Cost-Control Configs

Battle-tested `CLAUDE.md`, `.cursorrules`, and local **Ollama** (`num_ctx: 65536`) configurations to eliminate runaway token bills, infinite retry loops, and context truncation in agentic coding workflows.

Built as the companion repository for **[JP TECH on YouTube](https://www.youtube.com/channel/UCSYyZTwBt9_wo8BPhvAz3lA)**.

---

## What's Inside

| File | Purpose | Companion Video |
|---|---|---|
| [`claude-code/CLAUDE.md`](./claude-code/CLAUDE.md) | Stops infinite test-retry loops & enforces TDD verification | [1 CLAUDE.md Rule That Stops Loops](https://youtu.be/OkMJc3uo9xo) |
| [`claude-code/settings.example.json`](./claude-code/settings.example.json) | Prompt-cached session mode & local fallback pattern | [Why Claude API Costs 30x More Than Max](https://youtu.be/rJA7c_9c6Bw) |
| [`cursor/.cursorrules`](./cursor/.cursorrules) | Production engineering guardrails for Cursor & Windsurf | [Cursor vs Windsurf vs Claude Code ($200 Trap)](https://youtu.be/vb_PIM1Qkis) |
| [`ollama/Modelfile.qwen3-coder-64k`](./ollama/Modelfile.qwen3-coder-64k) | Fixes the default 4K context window trap (`65536` ctx) | [I Replaced $200 Cursor Ultra With Ollama](https://youtu.be/9xwIeMB78Lk) |
| [`ollama/continue-config.json`](./ollama/continue-config.json) | Drop-in `localhost:11434` config for Continue / local IDEs | [Qwen3-Coder 30B on Mac: Cloud Killer?](https://youtu.be/2t2eydVP1OE) |

---

## Apple Silicon Local Model Cheat Sheet (Late 2026)

| Mac Unified Memory | Recommended Model | Command | Why |
|---|---|---|---|
| **16 GB Mac** | `gemma4:12b` or `qwen3.5:9b` | `ollama run gemma4:12b` | Leaves 6GB+ headroom for IDE + Docker (zero SSD swap) |
| **24 GB – 32 GB Mac** | `qwen3-coder:30b` (MoE, 3.3B active) | `ollama run qwen3-coder:30b` | ~17GB Q4 RAM, 60–70 tok/s, strong tool-calling |

---

## Quick Start

```bash
# 1. Copy the Claude Code loop guard into your project root
cp claude-code/CLAUDE.md /path/to/your-repo/CLAUDE.md

# 2. Copy Cursor rules
cp cursor/.cursorrules /path/to/your-repo/.cursorrules

# 3. Create the 64K-context local Qwen3-Coder model in Ollama
ollama create qwen3-coder-64k -f ollama/Modelfile.qwen3-coder-64k
```

---

## License
MIT — Use freely in personal and commercial repositories.
