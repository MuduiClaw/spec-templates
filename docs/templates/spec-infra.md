---
status: draft          # draft → review → approved → in_progress → delivered
type: infra            # 基建/流程/工具链
level: spec
title: <一句话标题>
# atomization_waive: "仅在超标但仍需保留 level: spec 时填写"
thread: ""             # Discord thread ID（可选）
depends: []
acceptance:
  mode: manual         # manual | auto
required_evidence:
  report: true
  assertions: auto
  browser: auto
  commands: auto
  receipt: auto
user_cases: []        # 运行时行为的用户路径契约；纯静态治理也先保留占位，按需补齐
scope:
  allow: []
  deny: []
---
# <slug> — <一句话标题>
<!-- UI Intent: [NO_UI] -->

> Status: draft
> Parent: <父 spec>
> Depends: —
> Created: YYYY-MM-DD

---

> Atomization: 默认按单 worktree 原子 spec 设计。若正文 >300 行、`scope.allow` 顶层模块 >3 或显式阶段 >2，优先拆分；确需保留单 spec 时再写有效 `atomization_waive`。

## 问题

当前出了什么问题？有什么数据/证据？
写清楚根因，不只是症状。

## 目标

做完之后解决什么问题？对谁有影响？

## 规则 / 方案

> Infra spec 的核心是**规则和约束**，不是 user case。
> 用编号规则（R1、R2...）列清楚。

### R1: <规则名>

**内容**: ...
**执行方式**: hook / script / CI
**违反后果**: 阻断 push / 警告

### R2: <规则名>

...

## 验收标准

> **⚠️ 涉及运行时行为的验收必须在真实环境（具体拓扑见项目 AGENTS.md）。**
> 纯脚本/hook/CI 类可用本地 `pnpm test` + `bats` 验证。

| # | 场景 | 判定标准 | 验证环境 |
|---|------|---------|---------|
| 1 | ... | ... | 本地 / Electron → 真实 Gateway |
| 2 | ... | ... | ... |

## 不做什么

<!-- spec-lint: 此 section 不能为空，至少列 1 项 -->
- ...

---

## 变更日志

| 日期 | 版本 | 变更 |
|------|------|------|
| YYYY-MM-DD | v1 | 初始版本 |
