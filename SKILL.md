---
name: thariq-workflow
description: Thariq's full-cycle agentic coding workflow for complex tasks.
version: 1.0.0
author: Adapted from Thariq's "A Field Guide to Fable: Finding Your Unknowns"
license: MIT
platforms: [windows, linux, macos]
metadata:
  hermes:
    tags: [workflow, planning, code-quality, agentic-coding]
    category: software-development
    related_skills: [plan, spike, test-driven-development]
---

# Thariq Workflow Skill

A complete agentic-coding workflow distilled from Thariq's "Field Guide to Fable:
Finding Your Unknowns." When the user says "启动 Thariq 模式", "开始探索模式",
"按 Thariq 流程来", or "go Thariq mode", follow this phased pipeline.

## Core Philosophy

The map (your prompts/skills/context) is NOT the territory (the codebase/reality).
The gap = **unknowns**. Better models mean the bottleneck shifts from model
capability to YOUR ability to clarify unknowns.

Four unknowns quadrants to keep in mind throughout:
- **Known Knowns**: what you told the agent
- **Known Unknowns**: what you know you haven't figured out
- **Unknown Knowns**: obvious to you, never written down (most dangerous)
- **Unknown Unknowns**: haven't considered at all

## When to Use

Trigger this workflow when:
- Starting a complex, multi-file feature
- Working in an unfamiliar part of the codebase
- Working in an unfamiliar domain/technology
- A previous attempt failed and you don't know why
- The user says "启动 Thariq 模式" or similar trigger phrases
- The user explicitly asks for this workflow
- **Complex research, analysis, or content-creation tasks** — the same unknown-surfacing logic applies to writing long-form analysis, designing visual frameworks, or producing publishable content.

Do NOT use for:
- Single-line bug fixes
- Trivial mechanical changes
- Tasks the user clearly has fully scoped

## Procedure

The workflow has 7 phases. Guide the user through them sequentially, but allow
skipping phases the user says they've already done. At each phase, present the
canonical prompt pattern and adapt it to the user's specific task.

### Phase 1: Blind Spot Pass (盲点扫描)

**Goal**: Surface unknown unknowns before any work begins.

**When**: Always start here for unfamiliar domains/codebases.

**Canonical prompt pattern**:
> "I'm working on [TASK] but I know [LITTLE/NOTHING] about [RELEVANT AREA].
> Do a blindspot pass to find my unknown unknowns and help me prompt you better.
> Give me context on: what I should know about this area, common pitfalls,
> and questions I should be asking but haven't."

**What to do**:
1. Ask the user what they know vs. what's unfamiliar
2. Run a `blindspot pass`: use `search_files` to explore the relevant code area,
   `web_search` if domain knowledge is needed, then present findings
3. Deliver findings as a structured HTML artifact with:
   - Key concepts the user should understand
   - Codebase areas that will be touched
   - Common pitfalls in this domain
   - Questions the user should answer before proceeding
4. Ask: "哪些是你已经知道的？哪些是新发现？有什么想深入的吗？"

### Phase 2: Brainstorms & Prototypes (头脑风暴 / 原型)

**Goal**: Explore the solution space before committing. Surface unknown knowns
(things you'll recognize when you see them).

**When**: When the solution approach isn't obvious, or involves UI/UX/design,
or when you "know it when you see it."

**Canonical prompt pattern**:
> "Before implementing, make me an HTML page with [N] wildly different
> approaches to [PROBLEM]. I need to react to them before we commit."

**What to do**:
1. Generate 3-4 distinct approaches as an HTML artifact (use `write_file`)
2. Each approach should show: the core idea, trade-offs, complexity, fit
3. For UI tasks: visual mockups with fake data
4. For architecture tasks: component diagrams + data flow
5. For algorithm tasks: approach comparison with time/space complexity
6. Present the HTML file and ask the user to react

**Example variants**:
- Design: 4 different visual directions
- Architecture: monolith vs microservice vs hybrid
- Algorithm: brute force → optimized → library-based → novel

### Phase 3: Interview (面试式澄清)

**Goal**: Let the agent ask YOU questions to surface ambiguities you haven't
articulated.

**When**: After brainstorming, when there are still fuzzy requirements or the
user keeps saying "I'm not sure."

**Canonical prompt pattern**:
> "Interview me one question at a time about anything ambiguous in [TASK].
> Prioritize questions where my answer would change the architecture or
> implementation approach. Stop when I have no more answers to give."

**What to do**:
1. Based on everything learned in Phases 1-2, ask the user ONE question at a time
2. Questions should be ranked by: architecture impact > data model impact >
   UX impact > naming/convention
3. After each answer, decide: follow up deeper, or move to next topic
4. Stop when the user says they're done or answers become thin
5. Summarize all decisions made during the interview

### Phase 4: References (参考锚定)

**Goal**: Ground the implementation in concrete examples. Source code is the
best reference.

**When**: When the user has existing code/styles/patterns they want to match,
or a third-party implementation they admire.

**Canonical prompt pattern**:
> "This [FILE/MODULE/REPO] at [PATH/URL] implements the exact [BEHAVIOR/PATTERN]
> I want. Read it and reimplement the same semantics in our [TARGET]."

**What to do**:
1. Ask the user: "有没有现成的参考？代码、设计、文档、甚至其他项目的实现？"
2. If they provide references, read them thoroughly with `read_file`
3. Extract: patterns, conventions, API shapes, error handling style
4. Note these as constraints for the implementation phase
5. If no references exist, skip this phase

### Phase 5: Implementation Plan (实现计划)

**Goal**: Create a plan that surfaces the decisions most likely to change,
not just a mechanical step list.

**When**: Ready to implement — you've done Phases 1-4 (or skipped appropriately).

**Canonical prompt pattern**:
> "Write an implementation plan (as HTML). Lead with the decisions I'm most
> likely to tweak: data model changes, new type interfaces, and anything
> user-facing. Bury mechanical refactoring at the bottom — I trust you on that."

**What to do**:
1. Create `implementation-plan.html` with `write_file`
2. Structure:
   - **Section 1**: Decisions most likely to change (data model, types, API surface)
   - **Section 2**: User-facing changes (UI, behavior, error messages)
   - **Section 3**: Key implementation steps (ordered, with dependencies)
   - **Section 4**: Mechanical/boilerplate changes (list but don't detail)
   - **Section 5**: Risk register (what could go wrong, mitigation)
3. Present the plan and ask: "哪些决策你想调整？"
4. Revise until the user approves

### Phase 6: Implementation + Deviation Log (实现 + 偏差日志)

**Goal**: Execute the plan while tracking every place reality diverged from it.

**When**: Plan is approved.

**Canonical prompt pattern**:
> "Implement the plan. Keep an `implementation-notes.md` file. If you hit an
> edge case that forces you to deviate from the plan, pick the conservative
> option, log it under 'Deviations' with the reason, and keep going."

**What to do**:
1. Create `implementation-notes.md` at the start
2. Execute the plan step by step
3. For every deviation from the plan:
   - Log: what was planned, what actually happened, why
   - Pick the conservative path when in doubt
4. After implementation, review deviations with the user

### Phase 7: Post-Implementation (交付 + 验证)

**Goal**: Package the work so others understand it, and verify YOUR understanding.

**Sub-phase 7a: Pitch / Explainer**

**Canonical prompt pattern**:
> "Package the prototype, the spec, the implementation notes, and the key
> decisions into a single HTML doc I can share. Lead with the demo/screenshot.
> Structure it so someone with my same starting unknowns can understand
> what was done and why."

**Sub-phase 7b: Quiz (自测)**

**Canonical prompt pattern**:
> "Give me an HTML report covering: what changed, why, design intuition,
> edge cases handled. At the bottom, add a quiz I must pass before merging.
> I won't merge until I get 100%."

**What to do**:
1. Generate `deliverable-summary.html` — the pitch doc
2. Generate `understanding-quiz.html` — the self-test
3. For the quiz: 5-8 questions covering:
   - Why specific decisions were made
   - What edge cases are handled
   - What would break if a specific change were reverted
   - Where to look for related code
4. Grade the user's answers honestly. If they fail, explain and retest.

## Quick Reference

| Phase | Trigger phrase | Deliverable |
|-------|---------------|-------------|
| 1. Blind Spot | "盲点扫描" / "what am I missing" | HTML findings report |
| 2. Brainstorm | "给我几个方向" / "prototype this" | Multi-approach HTML |
| 3. Interview | "采访我" / "ask me questions" | Clarified requirements |
| 4. References | "参考这个" / "like X but for Y" | Extracted patterns |
| 5. Plan | "出实现计划" / "plan this" | implementation-plan.html |
| 6. Implement | "开始实现" / "build it" | Code + implementation-notes.md |
| 7. Deliver | "打包" / "quiz me" | deliverable-summary.html + quiz |

## Pitfalls

- **Don't skip Phase 1 in unfamiliar territory.** The most expensive bugs come from unknown unknowns.
- **Phase 2 prototypes should be throwaway.** Don't let the user fall in love with prototype code. The goal is to surface preferences, not to start implementation.
- **Phase 3 interview must be one question at a time.** Don't dump 10 questions at once — the user will answer the first and forget the rest.
- **Phase 5 plan must lead with decisions, not steps.** A mechanical step list ("1. add field, 2. update handler, 3. write test") is NOT an implementation plan in this framework. Lead with WHAT MIGHT CHANGE.
- **Phase 6 deviation log is for learning, not blame.** The goal is to improve the NEXT plan, not to flag "mistakes."
- **Phase 7 quiz is mandatory for complex changes.** If the user can't explain why a change was made, they don't understand the code they're about to merge.
- **Adapt depth to task complexity.** A 2-hour feature doesn't need a 1-hour planning phase. A 2-week feature does.

## Verification

After the workflow completes, verify:
- [ ] User can articulate ALL key decisions made
- [ ] User passed the Phase 7 quiz with 100%
- [ ] implementation-notes.md exists and captures every plan deviation
- [ ] deliverable-summary.html is shareable with teammates
