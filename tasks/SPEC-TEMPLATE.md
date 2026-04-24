# Spec 模板选择

| 场景 | 模板 |
|------|------|
| 代码任务 | [SPEC-TEMPLATE-CODE.md](SPEC-TEMPLATE-CODE.md) — 完整版（含测试计划、影响分析） |
| 内容/研究/运维 | [SPEC-TEMPLATE-LITE.md](SPEC-TEMPLATE-LITE.md) — 精简版（砍测试表格，保留验收+场景） |
| 大任务拆分 | [SPEC-TEMPLATE-OVERVIEW.md](SPEC-TEMPLATE-OVERVIEW.md) — 只有目标+拆分计划，子 spec 各自独立 |

## 规则

- **≥3 步复杂任务**必须写 spec，不分代码还是内容
- 代码用完整版，非代码用精简版
- 交付物 >5 个或跨 >2 模块 → 先写 overview 拆分，每个子 spec 控制在单模块
- Spec 状态：`draft → reviewed → approved → in_progress → done | abandoned`
- `abandoned` 必须写原因
- `done` / `abandoned` 定期移到 `tasks/archive/`
