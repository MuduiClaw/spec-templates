# Spec Templates Relationship Report

这是从私有工作仓库中抽出的公开只读资料仓库，方便外部直接访问说明文档模板关系说明与相关模板。

# 说明文档模板关系说明

仓库：<https://github.com/MuduiClaw/clawd-workspace>

## 一句话结论

本地其实有两层体系：
- `docs/templates/` 是**规范化正式模板层**，按说明文档类型拆分。
- `tasks/SPEC-TEMPLATE*.md` 是**历史/执行导向模板层**，按任务形态拆分。

前者更像“标准件”，后者更像“开工模板”。它们不是互相冲突，而是前者逐步取代后者、把说明文档从“任务单”升级成“治理对象”。

---

## 一、整体关系图

可以把它理解成这棵树：

- 说明文档体系
  - 正式模板层：`docs/templates/`
    - `spec-feature.md`
    - `spec-bugfix.md`
    - `spec-infra.md`
    - `spec-generic.md`
    - `spec-epic.md`
    - `spec-charter.md`
  - 执行模板层：`tasks/`
    - `SPEC-TEMPLATE-CODE.md`
    - `SPEC-TEMPLATE-LITE.md`
    - `SPEC-TEMPLATE-OVERVIEW.md`
    - `SPEC-TEMPLATE.md`

最核心的关系不是“谁包含谁”，而是两条不同的分类维度：
- `docs/templates/` 按**说明文档的语义类型**分类
- `tasks/` 按**任务执行方式和复杂度**分类

所以它们是**交叉映射关系**，不是一一对应关系。

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

## 三、`tasks/SPEC-TEMPLATE*.md` 这层：执行模板层

这层更像旧体系，或者说“更偏实际派工”的体系。

它不是按说明文档语义类型分，而是按执行形态分。

### 1) `SPEC-TEMPLATE-CODE.md`

用途：代码任务完整模板。

特点：
- 有目标
- 有现状分析
- 有范围
- 有场景覆盖
- 有验收标准
- 有测试计划
- 有影响分析
- 有回滚方案

本质上它是**面向代码交付**的重型模板。

它和 `docs/templates` 的关系：
- 大致相当于把 `feature` / `bugfix` / 部分 `infra` 的共同结构揉成一个“代码任务总模板”
- 它按“代码任务”来分，而不是按“功能/修复/基础设施”来分

所以它是**横切模板**，不是语义专用模板。

---

### 2) `SPEC-TEMPLATE-LITE.md`

用途：内容、研究、运维等非代码任务模板。

特点：
- 结构更轻
- 没有那么重的测试表格
- 仍然保留目标、范围、场景、验收标准

它和 `docs/templates` 的关系：
- 大致覆盖 `generic` 和一部分 `infra`
- 更像“非代码任务统一模板”

也就是说，它不是“某一种 spec 类型”，而是“某一类工作形态”的模板。

---

### 3) `SPEC-TEMPLATE-OVERVIEW.md`

用途：大任务拆分总览模板。

这个和 `spec-epic.md` 的关系最接近。

共同点：
- 都是拆分容器
- 都列子项
- 都定义整体完成条件

差别：
- `spec-epic.md` 更正式，纳入 frontmatter 和治理字段
- `SPEC-TEMPLATE-OVERVIEW.md` 更偏任务管理视角

所以它基本可以看成：
- **旧执行体系里的 epic 对应物**

---

### 4) `SPEC-TEMPLATE.md`

用途：模板选择说明页，不是单独一种说明文档模板。

它更像目录：
- 代码任务 → `SPEC-TEMPLATE-CODE.md`
- 非代码 → `SPEC-TEMPLATE-LITE.md`
- 大任务拆分 → `SPEC-TEMPLATE-OVERVIEW.md`

所以它和其他模板的关系不是并列，而是**导航页 / 分发表**。

---

## 四、两层模板之间到底是什么关系

### 关系 1：不是替代关系，而是演进关系

更准确地说：
- `tasks/SPEC-TEMPLATE*.md` 是“按执行形态分类”的旧工作流模板
- `docs/templates/*.md` 是“按说明文档语义分类”的新工作流模板

新体系更细、更标准，也更适合做治理、审查、自动检查。

---

### 关系 2：不是一一映射，而是多对多映射

大致可以这样对应：

- `SPEC-TEMPLATE-CODE.md`
  - 对应 `spec-feature.md`
  - 对应 `spec-bugfix.md`
  - 也能覆盖一部分 `spec-infra.md`

- `SPEC-TEMPLATE-LITE.md`
  - 对应 `spec-generic.md`
  - 对应一部分 `spec-infra.md`

- `SPEC-TEMPLATE-OVERVIEW.md`
  - 对应 `spec-epic.md`

- `spec-charter.md`
  - 在 `tasks/` 这套里基本没有完全对等物
  - 它属于更新、更上层的治理抽象

所以：
- `tasks/` 那层更粗粒度
- `docs/templates/` 那层更细粒度

---

### 关系 3：`charter → epic → spec` 是纵向层级

这条层级非常关键：

- `charter`
  - 定方向、边界、原则
- `epic`
  - 把大主题拆成多个执行项
- `spec`
  - 落单个可执行改动

其中普通 `spec` 又横向分成：
- feature
- bugfix
- infra
- generic

这才是完整关系图。

---

## 五、最实用的人话判断法

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

如果你还在沿用旧任务模板体系：
- 代码任务 → `tasks/SPEC-TEMPLATE-CODE.md`
- 非代码任务 → `tasks/SPEC-TEMPLATE-LITE.md`
- 大任务拆分 → `tasks/SPEC-TEMPLATE-OVERVIEW.md`

---

## 六、结论

一句话收口：

- `docs/templates/` 这套是**按说明文档语义类型分类的正式体系**。
- `tasks/SPEC-TEMPLATE*.md` 这套是**按任务执行形态分类的旧/执行导向体系**。
- 在正式层级上，最完整的关系是：`charter → epic → spec`。
- 在普通 `spec` 层内部，再横向分成：`feature / bugfix / infra / generic`。

所以“各种 spec 之间的关系”不是一坨平铺模板，而是：
- 先有纵向层级
- 再有横向分类
- `tasks/` 那套则是另一种历史兼容视角

---

## GitHub 链接

### 仓库
- <https://github.com/MuduiClaw/clawd-workspace>

### 正式模板层：`docs/templates/`
- <https://github.com/MuduiClaw/clawd-workspace/tree/main/docs/templates>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/docs/templates/spec-feature.md>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/docs/templates/spec-bugfix.md>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/docs/templates/spec-infra.md>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/docs/templates/spec-generic.md>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/docs/templates/spec-epic.md>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/docs/templates/spec-charter.md>

### 执行模板层：`tasks/`
- <https://github.com/MuduiClaw/clawd-workspace/tree/main/tasks>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/tasks/SPEC-TEMPLATE.md>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/tasks/SPEC-TEMPLATE-CODE.md>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/tasks/SPEC-TEMPLATE-LITE.md>
- <https://github.com/MuduiClaw/clawd-workspace/blob/main/tasks/SPEC-TEMPLATE-OVERVIEW.md>

### 本报告文件
- 本地路径：`docs/spec-templates-relationship-report.md`


## 目录

- `README.md`：模板关系说明报告
- `docs/templates/`：正式模板层
- `tasks/`：执行模板层
