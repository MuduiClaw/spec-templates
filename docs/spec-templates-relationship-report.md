# 说明文档模板关系说明

仓库：<https://github.com/MuduiClaw/clawd-workspace>

## 一句话结论

当前对外公开、建议直接使用的，只有 `docs/templates/` 这套正式模板层。

旧的 `tasks/SPEC-TEMPLATE*.md` 只属于历史背景，不再作为当前公开仓库的推荐入口；如果你只是要选模板，直接看 `docs/templates/` 就够了。

---

## 一、当前应该怎么看这套体系

如果只看当前正式体系，可以把它理解成这棵树：

- 说明文档体系
  - `spec-charter.md`
  - `spec-epic.md`
  - 普通 `spec`
    - `spec-feature.md`
    - `spec-bugfix.md`
    - `spec-infra.md`
    - `spec-generic.md`

也就是说，当前真正需要用的关系是：
- 先看纵向层级：`charter → epic → spec`
- 再看普通 `spec` 的横向分类：`feature / bugfix / infra / generic`

---

## 二、`docs/templates/` 这层：正式模板层

这层是现在更标准、也更清晰的一层。

### 1) `spec-feature.md`

用途：新功能说明文档。

它关心的是：
- 为什么要做
- 哪些用户能到达
- 用户场景怎么走
- 哪些东西明确不做
- 怎么验收

本质上它是**面向用户行为和交互结果**的模板。

适用：
- 新页面
- 新接口
- 新能力
- 新交互

它和其他模板的关系：
- 和 `spec-bugfix.md` 是并列关系：一个“做新东西”，一个“修坏东西”
- 和 `spec-generic.md` 是特化关系：它是 generic 在“功能类问题”上的专用化

---

### 2) `spec-bugfix.md`

用途：问题修复说明文档。

它不是先讲“要做什么功能”，而是先讲：
- 怎么复现
- 现象是什么
- 根因是什么
- 改哪里
- 如何证明修好了

本质上它是**面向缺陷闭环**的模板。

适用：
- 报错
- 回归
- 行为异常
- 逻辑错误

它和其他模板的关系：
- 和 `spec-feature.md` 并列
- 和 `spec-infra.md` 也并列，但关注点不同：`bugfix` 是修一个错，`infra` 是定规则/改底座

---

### 3) `spec-infra.md`

用途：基础设施、流程、工具链、治理约束类说明文档。

它最显著的特征是：
- 核心章节不是 user case，而是 **规则 / 方案**
- 强调 R1、R2 这种编号规则
- 强调执行方式、违反后果、阻断点

本质上它是**面向系统规则和运行底座**的模板。

适用：
- 网关
- 配置
- 部署
- 权限
- 自动化链路
- hook / script / CI 治理

它和其他模板的关系：
- 和 `feature` / `bugfix` 并列
- 当事情不是“做功能”也不是“修具体 bug”，而是在改运行规则时，优先用它

---

### 4) `spec-generic.md`

用途：通用兜底模板。

这个模板最重要的意义不是“常用”，而是**防止分类不清时卡住不写**。

适用：
- 重构计划
- 迁移计划
- 调研报告
- 文档更新
- 一时说不清应该归 feature / bugfix / infra 的任务

它和其他模板的关系：
- 是 `feature` / `bugfix` / `infra` 的**上位兜底版本**
- 能承接杂项，但不如专用模板表达力强

所以一般是：
- 能明确分类，就不用 generic
- 分不清时先用 generic，别空着

---

### 5) `spec-epic.md`

用途：大主题拆分容器。

它和前面几个最大的不同是：
- 它不是普通 `level: spec`
- 它是 `level: epic`
- 它主要负责拆分，不负责承载具体实现细节

它关注的是：
- 为什么要拆成多个执行说明文档
- 子说明文档列表
- 执行顺序
- 整体边界和风险

本质上它是**父级容器**。

它和其他模板的关系：
- `spec-feature` / `spec-bugfix` / `spec-infra` / `spec-generic` 都可以做它的子项
- 它不是同级替代，而是**上层编排器**

你可以把它理解成：
- `epic` 管组合
- 普通 `spec` 管单点执行

---

### 6) `spec-charter.md`

用途：方向、边界、原则的定义文档。

它甚至比 epic 更抽象一点。它不关心立即执行什么，而关心：
- 我们到底要统一什么方向
- 边界画在哪里
- 哪些决策以后都要遵守

本质上它是**宪章层**。

它和其他模板的关系：
- 它不是执行说明文档
- 它给后续 epic / spec 提供方向约束
- 可以把它看成比 `epic` 还更上游的一层

如果说：
- `charter` 是定打法
- `epic` 是拆战役
- `spec` 是打单仗

这就顺了。

---

## 三、当前关系的核心结论

### 1) `charter → epic → spec` 是纵向层级

这条层级是当前体系里最关键的主线：

- `charter`：定方向、边界、原则
- `epic`：把大主题拆成多个执行项
- `spec`：落单个可执行改动

---

### 2) 普通 `spec` 再横向分成四类

- `feature`：新功能
- `bugfix`：修问题
- `infra`：基础设施 / 配置 / 流程 / 治理
- `generic`：通用兜底

---

### 3) 旧 `tasks` 模板现在还要不要用？

对外公开场景下，**不需要**。

它们属于历史执行模板，主要价值只在于解释这套体系是怎么演进过来的；但对今天要选模板的人来说，继续强调它们只会增加理解成本。

所以当前公开口径是：
- 直接用 `docs/templates/`
- 不再把 `tasks/SPEC-TEMPLATE*.md` 作为推荐入口

---

## 四、最实用的人话判断法

如果你只是想快速选，不想看一堆概念，直接用这个：

- 在定长期规则、方法论、边界？
  - 用 `spec-charter.md`

- 在拆一个大主题，下面会有多个子说明文档？
  - 用 `spec-epic.md`

- 在做单点执行？
  - 继续往下分：
    - 新功能 → `spec-feature.md`
    - 修问题 → `spec-bugfix.md`
    - 改底座/治理/配置/流程 → `spec-infra.md`
    - 分不清 → `spec-generic.md`

---

## 五、结论

一句话收口：

- 当前真正需要用的，就是 `docs/templates/` 这套正式模板体系。
- 这套体系先按纵向层级组织：`charter → epic → spec`。
- 普通 `spec` 再按横向语义分类：`feature / bugfix / infra / generic`。
- 旧 `tasks` 模板不再是当前公开口径的一部分。

---

## GitHub 链接

- 仓库：<https://github.com/MuduiClaw/spec-templates>
- 正式模板目录：<https://github.com/MuduiClaw/spec-templates/tree/main/docs/templates>
- `spec-charter.md`：<https://github.com/MuduiClaw/spec-templates/blob/main/docs/templates/spec-charter.md>
- `spec-epic.md`：<https://github.com/MuduiClaw/spec-templates/blob/main/docs/templates/spec-epic.md>
- `spec-feature.md`：<https://github.com/MuduiClaw/spec-templates/blob/main/docs/templates/spec-feature.md>
- `spec-bugfix.md`：<https://github.com/MuduiClaw/spec-templates/blob/main/docs/templates/spec-bugfix.md>
- `spec-infra.md`：<https://github.com/MuduiClaw/spec-templates/blob/main/docs/templates/spec-infra.md>
- `spec-generic.md`：<https://github.com/MuduiClaw/spec-templates/blob/main/docs/templates/spec-generic.md>
