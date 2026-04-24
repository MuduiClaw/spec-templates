---
status: draft          # draft → review → approved → in_progress → delivered
type: feature
level: spec
title: <一句话标题>
# atomization_waive: "仅在超标但仍需保留 level: spec 时填写"
thread: ""             # Discord thread ID（可选）
depends: []            # 前置 spec slug 列表（可选）
acceptance:
  mode: manual         # manual | auto
required_evidence:
  report: true
  assertions: auto
  browser: auto
  commands: auto
  receipt: auto
user_cases: []        # 运行时行为的用户路径契约；至少覆盖 normal + exception/recovery
scope:
  allow: []            # 可写的文件/目录
  deny: []             # 禁止触碰的路径（可选）
assertions: []         # Gate 12 断言（delivered 时必填，见底部示例）
---
# <slug> — <一句话标题>
<!-- UI Intent: [UI] | [NO_UI] | [NO_UI_LOGIC] -->

> Status: draft
> Parent: <父 spec 或 wave>
> Depends: <前置 spec，无则写 —>
> Created: YYYY-MM-DD

---

> Atomization: 默认按单 worktree 原子 spec 设计。若正文 >300 行、`scope.allow` 顶层模块 >3 或显式阶段 >2，优先拆分；确需保留单 spec 时再写有效 `atomization_waive`。

## 背景

为什么要做这个？用户碰到了什么问题，或者缺了什么能力？
2-3 句话说清楚。不写代码，不写架构。

## 目标

一句话：做完之后用户能干什么？

## 可达性审视

> **⚠️ 必填。写 User Case 之前先回答这个问题。**
> 这个功能面向哪些用户身份？不在列表里的身份，**不应该看到入口、不应该到达此页面**。
> 如果某个身份不该到达，入口隐藏/拦截方案写在这里，不要在 User Cases 里为不该存在的场景设计 UI。

| 用户身份 | 能否到达 | 入口/拦截方式 |
|---------|---------|-------------|
| 已登录用户 | ✅ | 正常导航 |
| Guest / 未登录 | ❌ | 入口不可见 / 重定向登录 |
| ... | ... | ... |

## User Cases

> 每个 case 是一个**可独立验证的最小用户场景**。
> 不写实现细节。写用户看到什么、做什么、期望什么。
> **User Case 只覆盖可达性审视中标 ✅ 的身份。** 不为不该到达的用户设计体验。

### UC-01: <场景标题>

**前置条件**: 用户已连接到 Gateway，处于 Main 频道

**操作**: 在输入框输入"你好"，点击发送

**期望结果**:
- 消息气泡立即出现（发送中状态）
- 1-3 秒内开始出现流式回复
- 回复完成后气泡变为实色

**验证方式**: e2e | store | unit | manual | screenshot（至少标注一个）
**验证环境**: Electron 客户端（Mac mini）→ 真实 Gateway（M3 Pro / ClawKing）

---

### UC-02: <场景标题>

**前置条件**: Gateway WS 已断开

**操作**: 用户尝试发送消息

**期望结果**:
- 发送按钮 disabled 或点击后显示"连接中…"
- 消息不会静默丢失

**验证方式**: e2e | unit | manual（至少标注一个）

---

### UC-03: <边界/异常场景>

**前置条件**: ...

**操作**: ...

**期望结果**:
- ...

**验证方式**: e2e | unit | manual（至少标注一个）

---

<!-- spec-lint: 有 [UI] 标签时，至少一个 UC 必须标 e2e -->

## 不做什么

<!-- spec-lint: 此 section 不能为空，至少列 1 项 -->
- 明确列出**不在本 spec 范围**的事情
- 尤其是容易被"顺手做了"的相邻功能

## 设计决策（可选）

> 只写**会影响 case 行为**的关键决策，不写实现代码。

| 决策 | 选项 | 结论 | 原因 |
|------|------|------|------|
| 数据拉取策略 | 轮询 vs 事件驱动 | 事件驱动 | ReadyPayload 已 hydrate，WS 增量更新 |

## 风险（可选）

- 风险 1：...
- 风险 2：...

## 验收环境要求

> **⚠️ 所有涉及 UI/交互的验收必须在真实环境完成。具体验收拓扑（客户端、Server、数据源）见项目 AGENTS.md。**

## Assertions（delivered 时补充）

```yaml
assertions:
  - id: <Spec>-A1
    type: store        # store | e2e | unit
    desc: <对应 UC-01 的可执行断言>
  - id: <Spec>-A2
    type: e2e
    desc: <对应 UC-02 的可执行断言>
```

---

## 变更日志

| 日期 | 版本 | 变更 |
|------|------|------|
| YYYY-MM-DD | v1 | 初始版本 |
