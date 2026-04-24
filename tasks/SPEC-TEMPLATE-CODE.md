# SPEC: [任务标题]

> **Status**: `draft` → `reviewed` → `approved` → `in_progress` → `done` | `abandoned`  
> **Type**: code  
> **Module**: [影响哪个模块/项目]  
> **Parent**: [overview spec slug，无则留空]  
> **Created**: YYYY-MM-DD  
> **Oracle Review**: —  
> **Approved**: —  

---

## 目标

[解决什么问题？为什么现在做？对准哪条战线（💰量化/📢内容/🚀产品）？]

## 现状分析

[当前是什么状态？已有哪些相关模块/功能？]

- 涉及模块：[列出已有模块]
- 操作类型：增 / 删 / 改（不要默认"新建"，优先改已有的）

## 范围

### 做什么

> **UI 标记约定**: 涉及 UI 展示/交互的交付物加 `[UI]`，Gate 7 会据此计算截图最低数量。
> - `[UI]` — 交付物涉及可视化变更，必须有对应截图/CDP 验证
> - `[NO_UI]` — 整个 spec 无任何 UI 变更（frontmatter 或"不做什么"中声明）
> - `[NO_UI_LOGIC]` — 改了视图文件但仅改逻辑（提取 util、改 API endpoint 等），放行但留审计日志

- [ ] 交付物 1（具体到可独立验证）`[UI]`
- [ ] 交付物 2

### 不做什么
- 明确排除项（不写 = 没画线 = 范围会蔓延）
- *如整个 spec 无 UI 变更: 在此声明 `[NO_UI]`*

## 场景覆盖

### 正常场景
1. [用户/系统正常使用路径]

### 边界场景
1. [空输入/超长/并发/网络中断/权限不足...]

### 错误场景
1. [依赖服务挂了/数据格式错/配置缺失...]

## 验收标准

1. [ ] `curl /api/xxx` 返回 200 且 body 包含 [具体字段]
2. [ ] `npm test` 全绿，覆盖以上所有场景
3. [ ] 截图/vision 确认 UI 渲染正确（如涉及 UI）
4. [ ] `docs/acceptance/<slug>/report.md` 存在且 `showboat verify` exit 0（如涉及脚本/API/配置）

## 测试计划

| 场景 | 输入 | 期望输出 | 测试方式 |
|------|------|---------|---------|
| 正常路径 | ... | ... | 单元/集成/e2e |
| 边界 - 空输入 | ... | ... | 单元 |
| 错误 - 服务不可用 | ... | ... | 单元 mock |

## 影响分析

- **改了什么**：[文件/模块列表]
- **谁受影响**：[依赖该模块的其他功能]
- **回滚方案**：[如果出问题怎么回退]

## 风险 / 依赖

- [关键假设和可能翻车的点]

## 时间预估

- 预计 Loop 轮次：[N 轮]（每轮 = plan→execute→verify→ship，分钟级）

---

*流转: draft → spec-review → Oracle PASS → Mudui 确认 → task-start → 执行 → task-selftest → spec-verify → task-deliver*
