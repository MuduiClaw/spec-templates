---
status: draft          # draft → review → approved → in_progress → delivered
type: generic          # 不属于 feature/infra/bugfix 的其他类型
level: spec
title: <一句话标题>
# atomization_waive: "仅在超标但仍需保留 level: spec 时填写"
thread: ""
depends: []
acceptance:
  mode: manual         # manual | auto
required_evidence:
  report: true
  assertions: auto
  browser: auto
  commands: auto
  receipt: auto
user_cases: []        # 运行时/流程类 spec 的用户路径契约
scope:
  allow: []
  deny: []
---
# <slug> — <一句话标题>
<!-- UI Intent: [UI] | [NO_UI] | [NO_UI_LOGIC] -->

> Status: draft
> Parent: <父 spec 或 —>
> Created: YYYY-MM-DD

---

> Atomization: 默认按单 worktree 原子 spec 设计。若正文 >300 行、`scope.allow` 顶层模块 >3 或显式阶段 >2，优先拆分；确需保留单 spec 时再写有效 `atomization_waive`。

## 背景

为什么要做这件事？

## 目标

做完之后什么变了？

## 内容

> 根据具体类型自由组织。可以是：
> - 迁移计划（步骤 + 回滚方案）
> - 重构计划（改什么 + 不改什么 + 验证方式）
> - 调研报告（结论 + 依据 + 下一步）
> - 文档更新（改动范围 + 验收标准）

## 验收标准

> **⚠️ 涉及 UI/交互的验收必须在真实环境。具体验收拓扑见项目 AGENTS.md。**

| # | 场景 | 判定标准 | 验证环境 |
|---|------|---------|---------|
| 1 | ... | ... | Electron → 真实 Gateway / 本地 |

## 不做什么

<!-- spec-lint: 此 section 不能为空，至少列 1 项 -->
- ...
