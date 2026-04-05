# Skills Index

本索引指向可复用的 Skills（技能）—— AI 可以调用的工具、流程和最佳实践。

- **想使用某个能力** -> 浏览下方分类，找到对应的 skill 文件
- **想添加新 skill** -> 参考现有文件格式，添加到对应分类

---

## 组件状态

### Tier 1: 核心（可直接使用）
- ✅ Rules 框架（SOUL/USER/COMMUNICATION/WORKSPACE）
- ✅ Skills 框架（本目录）
- ✅ 三层记忆系统（手动触发 observer/reflector）

### Tier 2: 扩展（需要额外配置）
<!-- 随着需求出现，在这里添加 -->

### 说明
✅ = 可直接使用
⚙️ = 需要额外配置

---

## 分类索引

### BestPractice（最佳实践）

通用的最佳实践和经验教训。

- [AI 编程核心方法论](./bestpractice_ai_programming_mindset.md) ✅ — 70% 问题、成功标准、可验证性
- [分阶段工作法](./bestpractice_staged_approach.md) ✅ — 隔离-处理-验证闭环，破坏性操作前 Dry Run

### Workflow（工作流）

特定任务的完整工作流程。

<!-- 随着实践积累，在这里添加你自己的 workflow -->

### API Guide（API 指南）

调用外部系统或工具的操作手册。

<!-- 随着集成需求出现，在这里添加 -->

---

## 如何添加你自己的 Skill

1. 参考现有 skill 文件的格式
2. 以 `<category>_<name>.md` 命名（例如 `workflow_my_process.md`、`bestpractice_my_insight.md`）
3. 在 INDEX.md 对应分类下添加一行

Skill 格式参考（最简版）：

```markdown
# Skill: 名称

## When to Use
什么情况下触发这个 skill

## Prerequisites
需要什么工具/配置

## Steps
1. 步骤一
2. 步骤二
```

## Progressive Disclosure

Skills 采用渐进式披露原则：
- **INDEX.md** 提供概览，快速定位
- **具体 skill 文件** 包含完整的操作步骤和示例
