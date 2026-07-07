<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/banner.svg">
    <img alt="Thariq Workflow" src="assets/banner.svg" width="900">
  </picture>
</p>

<p align="center">
  <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-yellow.svg"></a>
  <a href="https://github.com/NousResearch/hermes-agent"><img alt="Hermes Skill" src="https://img.shields.io/badge/Hermes-Skill-f0b429"></a>
  <a href="#"><img alt="Phases" src="https://img.shields.io/badge/Phases-7-e67e22"></a>
  <a href="README.zh-CN.md"><img alt="简体中文" src="https://img.shields.io/badge/README-简体中文-red"></a>
</p>

---

> **"Fable is the first model where the quality of the work is bottlenecked by my ability to clarify its unknowns."**
> — Thariq, Claude Code @ Anthropic

A **Hermes skill** that encodes a 7-phase agentic coding workflow. When the model is strong enough that **the bottleneck is no longer the AI — it's your ability to surface and manage unknowns** — this workflow helps you do exactly that.

---

## 🧭 The Workflow

| # | Phase | Trigger Phrase | What It Does |
|---|-------|---------------|-------------|
| 1 | **Blind Spot Pass** | *blindspot scan* / *what am I missing* | Find what you don't know you don't know |
| 2 | **Brainstorm** | *show me options* / *brainstorm this* | Generate 4 wildly different approaches |
| 3 | **Interview** | *interview me* / *ask me questions* | Agent asks YOU one question at a time |
| 4 | **References** | *reference this* / *like X but for Y* | Anchor in real code/design examples |
| 5 | **Plan** | *plan this* / *implementation plan* | Lead with decisions most likely to change |
| 6 | **Implement** | *build it* / *implement this* | Build + track every deviation from plan |
| 7 | **Deliver + Quiz** | *package + quiz me* / *deliver this* | Package for buy-in, then test yourself |

## ⚡ Quick Start

```bash
git clone https://github.com/ennheng/hermes-thariq-workflow.git ~/.hermes/skills/thariq-workflow
```

Then say **"go Thariq mode"** in any Hermes session.

## 🎯 When to Use

✅ Complex multi-file features · unfamiliar codebase areas · new domains/tech stacks · failed attempts with unclear causes · research and analysis tasks

❌ Single-line bug fixes · trivial mechanical changes · fully-scoped tasks

## 🧠 The Framework

| Known Knowns | Known Unknowns |
|---|---|
| What you told the agent | What you know you haven't figured out |
| **Unknown Knowns** 🚨 | **Unknown Unknowns** |
| Obvious to you, never written down | Haven't considered at all |

The entire pipeline converts ⬜ red cells into 🟩 green ones.

## 📄 License

MIT — use it, remix it, share it.

## 🌐 Language

[English](README.md) · [简体中文](README.zh-CN.md)
