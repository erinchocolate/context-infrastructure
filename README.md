# mc-context-infrastructure

美乔的个人 AI context 基建系统，基于 [grapeot/context-infrastructure](https://github.com/grapeot/context-infrastructure) 的设计哲学搭建。

## 设计理念

AI 的价值不来自模型智力，而来自你为它构建的 context 环境。这个环境必须随时间持续积累，形成"输入 -> 提炼 -> 蒸馏 -> 改善工作"的飞轮。

## 三层知识架构

```
01 raw/       原始输入，不加工：对话记录、一次性脚本、未经过滤的笔记
02 trusted/   对 raw 的提炼：OBSERVATIONS.md、加了个人理解的复盘、结构化反思
03 refined/   对外公开、可复用：Axioms、Skills、核心指南
```

## 目录结构

```
AGENTS.md                        # Session 入口
README.md
01 raw/                          # 所有原始输入（本地，不上传）
02 trusted/                      # 提炼后的观察与反思（本地，不上传）
03 refined/                      # 对外公开的可复用知识系统
  SOUL.md                        # AI 身份与行为准则
  USER.md                        # 用户画像
  COMMUNICATION.md               # 沟通风格指南
  WORKSPACE.md                   # 目录路由速查
  SOP.md                         # 日常工作操作手册
  axioms/                        # 从经历中蒸馏的决策原则
    INDEX.md
  skills/                        # 可复用的工作流和最佳实践
    INDEX.md
  tools/                         # 工具脚本（Confluence 同步、语义搜索等）
projects/                        # 活跃项目上下文
archive/                         # 归档内容
```

## 致谢

架构设计参考了 [grapeot/context-infrastructure](https://github.com/grapeot/context-infrastructure)。
