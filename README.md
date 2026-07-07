# 🧭 Thariq Workflow for Hermes

> A 7-phase agentic coding workflow that turns "I don't know what I don't know" into a structured pipeline.
> Distilled from [Thariq's "A Field Guide to Fable: Finding Your Unknowns"](https://x.com/trq212/status/2073100352921215386).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Hermes Skill](https://img.shields.io/badge/Hermes-Skill-f0b429)](https://github.com/NousResearch/hermes-agent)

---

## What is this?

This is a **Hermes skill** that encodes Thariq's full-cycle workflow for working with advanced AI coding agents. When the model is strong enough that **the bottleneck is no longer the AI — it's your ability to clarify unknowns** — this workflow helps you systematically surface and resolve those unknowns.

## The 7 Phases

| # | Phase | What it does |
|---|-------|-------------|
| 1 | **Blind Spot Pass** | Find what you don't know you don't know |
| 2 | **Brainstorm & Prototype** | Generate 3-4 wildly different approaches before committing |
| 3 | **Interview** | Let the agent ask YOU one question at a time to surface ambiguities |
| 4 | **References** | Anchor the work in concrete examples (source code is best) |
| 5 | **Implementation Plan** | Lead with decisions most likely to change, not mechanical steps |
| 6 | **Implementation + Deviation Log** | Build it, track every place reality diverged from the plan |
| 7 | **Pitch + Quiz** | Package for buy-in, then test your own understanding before merging |

## Quick Start

### Installation

```bash
# Clone into your Hermes skills directory
git clone https://github.com/ennheng/hermes-thariq-workflow.git ~/.hermes/skills/thariq-workflow
```

Or just copy `SKILL.md` to `~/.hermes/skills/software-development/thariq-workflow/SKILL.md`.

### Usage

Just say any of these in a Hermes session:

- **"启动 Thariq 模式"** — full 7-phase pipeline
- **"盲点扫描"** — jump to Phase 1
- **"给我几个方向"** — jump to Phase 2 (multi-direction brainstorm)
- **"采访我"** — jump to Phase 3 (agent interviews you)
- **"出实现计划"** — jump to Phase 5
- **"打包 + 考我"** — jump to Phase 7 (deliver + quiz)

### When to Use

- Starting a complex, multi-file feature
- Working in an unfamiliar part of the codebase
- Working in an unfamiliar domain or technology
- A previous attempt failed and you don't know why
- Complex research, analysis, or content-creation tasks

### When NOT to Use

- Single-line bug fixes
- Trivial mechanical changes
- Tasks you've already fully scoped

## The Core Insight

From the original article:

> "Fable is the first model where I find the quality of the work is bottlenecked by my ability to clarify its unknowns."

The workflow is built on the **Rumsfeld unknowns matrix** applied to coding:

| | |
|---|---|
| **Known Knowns** | What you told the agent |
| **Known Unknowns** | What you know you haven't figured out |
| **Unknown Knowns** 🚨 | Obvious to you, never written down (most dangerous) |
| **Unknown Unknowns** | Haven't considered at all |

The entire workflow is designed to systematically convert red cells into green ones.

## License

MIT — use it, remix it, share it.

## Credits

Adapted from [Thariq's "A Field Guide to Fable: Finding Your Unknowns"](https://x.com/trq212/status/2073100352921215386) (July 2026). Thariq works on Claude Code at Anthropic.
