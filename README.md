# Spec Templates

公开只读仓库，用来说明我们当前的 spec 体系，并提供可直接引用的正式模板文档。

## 快速导航

### 1. 先看总说明
- [Spec 模板关系说明](./docs/spec-templates-relationship-report.md)

适合场景：
- 想先理解整个 spec 体系是怎么分层的
- 想搞清楚 `charter / epic / spec` 的关系
- 想知道 `feature / bugfix / infra / generic` 的区别

---

### 2. 定方向 / 定边界 / 定原则
- [spec-charter.md](./docs/templates/spec-charter.md)

适合场景：
- 给一个长期主题定原则
- 先统一边界，再拆后续执行项

---

### 3. 拆一个大主题
- [spec-epic.md](./docs/templates/spec-epic.md)

适合场景：
- 一个主题下面会拆多个子 spec
- 需要先定义整体目标、拆分计划、执行顺序

---

### 4. 做单点执行 spec

#### 新功能
- [spec-feature.md](./docs/templates/spec-feature.md)

适合场景：
- 新页面
- 新接口
- 新交互
- 新能力

#### 修问题
- [spec-bugfix.md](./docs/templates/spec-bugfix.md)

适合场景：
- 报错
- 回归
- 行为异常
- 逻辑错误

#### 改底座 / 治理 / 配置 / 流程
- [spec-infra.md](./docs/templates/spec-infra.md)

适合场景：
- 基础设施
- 网关 / 配置
- 自动化链路
- hook / CI / 治理规则

#### 分不清先兜底
- [spec-generic.md](./docs/templates/spec-generic.md)

适合场景：
- 一时不确定该归 feature / bugfix / infra 哪类
- 调研、迁移、重构、通用计划类文档

---

## 最短判断法

- 定方向 → `spec-charter.md`
- 拆大任务 → `spec-epic.md`
- 做单点新功能 → `spec-feature.md`
- 修问题 → `spec-bugfix.md`
- 改底座 / 配置 / 流程 / 治理 → `spec-infra.md`
- 还是分不清 → `spec-generic.md`

---

## 仓库结构

- `docs/spec-templates-relationship-report.md`：总说明
- `docs/templates/`：正式模板层

---

## 对外引用建议

如果别人只是想快速拿去用，优先直接发这几类链接：

- 看总说明：
  - [Spec 模板关系说明](./docs/spec-templates-relationship-report.md)

- 看正式模板目录：
  - [docs/templates/](./docs/templates/)

- 直接选模板：
  - [spec-charter.md](./docs/templates/spec-charter.md)
  - [spec-epic.md](./docs/templates/spec-epic.md)
  - [spec-feature.md](./docs/templates/spec-feature.md)
  - [spec-bugfix.md](./docs/templates/spec-bugfix.md)
  - [spec-infra.md](./docs/templates/spec-infra.md)
  - [spec-generic.md](./docs/templates/spec-generic.md)
