# mc-context-infrastructure

美乔的个人 AI context 基建系统，基于 [grapeot/context-infrastructure](https://github.com/grapeot/context-infrastructure) 的设计哲学搭建。

## 设计理念

AI 的价值不来自模型智力，而来自你为它构建的 context 环境。这个环境必须随时间持续积累，形成"观察 -> 反思 -> 蒸馏 -> 改善工作"的飞轮。

## 三层记忆架构

```
L3（全局约束）: rules/ 下所有文件 -> 每次 session 被动加载
L1（每日观察）: contexts/memory/OBSERVATIONS.md -> 手动触发记录
L2（每周反思）: 从 L1 蒸馏，晋升到 L3
```

## 目录结构

```
CLAUDE.md                        # Session 入口（Claude Code 自动加载）
rules/
  SOUL.md                        # AI 身份与行为准则
  USER.md                        # 用户画像
  COMMUNICATION.md               # 沟通风格指南
  WORKSPACE.md                   # 目录路由速查
  axioms/                        # 从经历中蒸馏的决策原则
    INDEX.md
  skills/                        # 可复用的工作流和最佳实践
    INDEX.md
contexts/
  memory/                        # 记忆系统
    OBSERVATIONS.md              # 每日观察 + 每周反思
    PROMPTS.md                   # Observer/Reflector prompt 模板
  research/                      # 调研报告
  learning/                      # 学到的东西 / 复盘
  daily_log/                     # 每日个人活动记录
adhoc_jobs/                      # 临时项目
```

## 致谢

架构设计参考了 [grapeot/context-infrastructure](https://github.com/grapeot/context-infrastructure)。
