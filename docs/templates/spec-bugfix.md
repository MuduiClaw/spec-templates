---
status: draft          # draft → review → approved → in_progress → delivered
type: bugfix
level: spec
title: <一句话标题>
# atomization_waive: "仅在超标但仍需保留 level: spec 时填写"
thread: ""
caused_by: ""          # 引入 bug 的源头 spec slug（修复后用 git blame 精确填写）
depends: []
acceptance:
  mode: manual         # manual | auto
required_evidence:
  report: true
  assertions: auto
  browser: auto
  commands: auto
  receipt: auto
user_cases: []        # 修复必须声明用户如何复现、被阻断、恢复推进
scope:
  allow: []
  deny: []
---
# <slug> — <Bug 一句话描述>
<!-- UI Intent: [UI] | [NO_UI] -->

> Status: draft
> Parent: <相关 spec>
> Created: YYYY-MM-DD

---

> Atomization: 默认按单 worktree 原子 spec 设计。若正文 >300 行、`scope.allow` 顶层模块 >3 或显式阶段 >2，优先拆分；确需保留单 spec 时再写有效 `atomization_waive`。

## 问题

**复现步骤**:
1. 做 X
2. 做 Y
3. 看到 Z（期望看到 W）

**证据**: 截图 / 日志 / 错误信息

## 根因

简要说明为什么出了这个问题。1-3 句话。

## 修复

**改什么**: 哪个文件 / 哪个逻辑
**怎么验证修好了**: 按复现步骤操作，期望结果变为 W

## 验收

> **⚠️ 必须在真实环境验收。具体验收拓扑见项目 AGENTS.md。**

| # | 场景 | 判定标准 | 验证环境 |
|---|------|---------|---------|
| 1 | 按复现步骤操作 | 不再出现 Z，正确显示 W | Electron → 真实 Gateway |
| 2 | 回归检查 | 相关功能没被破坏 | Electron → 真实 Gateway |
| 3 | 回归测试 | 新增测试覆盖修复点，防止再犯 | `pnpm test` |

<!-- spec-lint: 验收表格必须包含回归测试行 -->
