---
status: draft          # draft → review → approved → in_progress → delivered
type: generic
level: epic
title: <一句话标题>
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
wave: ""
line: ""
scope:
  allow:
    - tasks/<slug>.md
  deny: []
created: YYYY-MM-DD
---
# <slug> — <一句话标题>
<!-- UI Intent: [NO_UI] -->

> Status: draft
> Level: epic
> Created: YYYY-MM-DD

---

> Epic 是拆分容器，不受 spec 的 atomization 硬阈值约束。

## 背景

这组问题为什么值得拆成多个执行 spec？先说业务背景，再说治理/工程约束。

## 目标

- 说明 epic 完成后整体能力会如何变化
- 明确拆分完成的判断标准

## 拆分计划

1. 先做最小可交付的执行 spec
2. 再补依赖 spec / 风险收口 spec
3. 最后做验收与收尾 spec

## 执行 Spec 列表

- `spec-a`：解决主链路
- `spec-b`：补异常路径
- `spec-c`：补治理/验收

## 不做什么

- 不在这个 epic 里直接写代码
- 不把多个执行 spec 混成一个大 spec

## 影响评估

- 爆炸半径：列出受影响脚本/流程
- 风险：列出拆分遗漏或顺序依赖
- 回滚：说明如何撤销这次治理变更
