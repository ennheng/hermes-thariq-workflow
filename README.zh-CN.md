# 🧭 Thariq 工作流 · Hermes 技能

> 一套 7 阶段 AI 编程工作流，把"我不知道我不知道什么"变成结构化的探索管道。
> 提炼自 [Thariq《A Field Guide to Fable: Finding Your Unknowns》](https://x.com/trq212/status/2073100352921215386)。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Hermes Skill](https://img.shields.io/badge/Hermes-Skill-f0b429)](https://github.com/NousResearch/hermes-agent)

---

## 这是什么？

这是一个 **Hermes 技能**，将 Thariq 的完整 AI 编程工作流编码为可复用的自动化流程。核心洞察：

> 当模型足够强时，瓶颈不再是 AI——而是你表达需求、管理不确定性的能力。

## 7 个阶段

| # | 阶段 | 做什么 |
|---|------|--------|
| 1 | **盲点扫描** | 找出你不知道自己不知道的东西 |
| 2 | **头脑风暴 & 原型** | 在动手前，生成 3-4 种完全不同的方案 |
| 3 | **面试式澄清** | 让 Agent 一次一个问题地采访你，挖掘模糊点 |
| 4 | **参考锚定** | 用真实代码/设计作为锚点（源代码是最好的参考）|
| 5 | **实现计划** | 优先暴露最可能被推翻的决策，而非机械罗列步骤 |
| 6 | **实现 + 偏差日志** | 开干，记录每一个偏离计划的地方 |
| 7 | **交付 + 自测** | 打包成分享文档，然后出题考自己，全对再合并 |

## 快速开始

### 安装

```bash
git clone https://github.com/ennheng/hermes-thariq-workflow.git ~/.hermes/skills/thariq-workflow
```

或者直接把 `SKILL.md` 复制到 `~/.hermes/skills/software-development/thariq-workflow/SKILL.md`。

### 使用

在 Hermes 对话中说以下任意一句：

- **"启动 Thariq 模式"** — 走完整 7 阶段流程
- **"盲点扫描"** — 直接跳到 Phase 1
- **"给我几个方向"** — 直接跳到 Phase 2（多方向头脑风暴）
- **"采访我"** — 直接跳到 Phase 3（Agent 采访你）
- **"出实现计划"** — 直接跳到 Phase 5
- **"打包 + 考我"** — 直接跳到 Phase 7（交付 + 自测）

### 适用场景

- 开始一个复杂的多功能特性
- 在代码库的陌生区域工作
- 在你不熟悉的领域或技术栈中工作
- 上次尝试失败了，你不知道为什么
- 复杂的研究、分析或内容创作任务

### 不适合的场景

- 单行 bug 修复
- 简单的机械性改动
- 你已经完全想清楚的任务

## 底层框架

工作流建立在 **Rumsfeld 未知矩阵** 之上：

| | |
|---|---|
| **已知的已知** | 你在 prompt 里已经说清楚的 |
| **已知的未知** | 你知道自己还没想清楚的 |
| **未知的已知** 🚨 | 你觉得太明显所以没写（最危险）|
| **未知的未知** | 你完全没意识到的问题 |

整个流程的目标就是系统性地把红色格子变成绿色格子。

## License

MIT — 随便用、改、分享。

## Credits

改编自 [Thariq《A Field Guide to Fable: Finding Your Unknowns》](https://x.com/trq212/status/2073100352921215386)（2026 年 7 月）。Thariq 就职于 Anthropic Claude Code 团队。
