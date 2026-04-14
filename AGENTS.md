# AGENTS.md - 美乔的 Context Infrastructure

This folder is home. Treat it that way.

## Every Session

Before doing anything else:

1. Read `03 refined/SOUL.md` — this is who you are
2. Read `03 refined/USER.md` — this is who you're helping
3. Read `03 refined/WORKSPACE.md` — file routing table, check before searching for files
4. Read `03 refined/COMMUNICATION.md` — how to think and communicate (especially for non-coding tasks)
5. Read `03 refined/skills/INDEX.md` — understand available skills

## File Routing

**找文件时，先查 `03 refined/WORKSPACE.md`，再搜索。** WORKSPACE.md 是这个 workspace 的目录索引，记录了每类内容的存放位置。绝大多数情况下查一下就能定位到目标目录，不需要全盘 glob/grep。如果发现新目录或项目没被收录，顺手更新 WORKSPACE.md。

**处理特定项目任务前，先读对应的 `projects/<name>/README.md`。** 这是每个项目的 AI 入口，包含项目概述、文档索引和当前工作重点。活跃项目列表见 WORKSPACE.md 快速查询。

## Skills

**Skills** 是 AI 可复用的能力，包括工作流、API 指南、最佳实践等。

**重要：遇到"怎么做 X"时，先查 skill 再查系统工具。** 搜索顺序：(1) 下方速查表 → (2) `03 refined/skills/INDEX.md` → (3) 系统工具。

**需要执行某项任务** → 先查 `03 refined/skills/INDEX.md` 找到对应的 skill  
**想添加新能力** → 参考现有 skill 格式，更新 INDEX.md

### 常用 Skill 速查（以 INDEX.md 为准）

**深度调研任务** → `03 refined/skills/workflow_deep_research_survey.md`  
- 初步扫描 → 分割维度 → 多 Agent 并行 → 交叉验证 → 写报告  
- 输出：`01 raw/`

**调用后台 Agent / 并行 Subagent** → `03 refined/skills/workflow_parallel_subagents.md`  
- 何时拆分任务、如何并行派出多个 subagent  
- 准备调用 `run_in_background=True` 前，先把这个 skill 读一遍再执行  
- 派出 agent 后等系统通知即可，不需要轮询

**导入 Confluence 文档** → `03 refined/skills/workflow_confluence_sync.md`  
- 将 Confluence 页面转为 Markdown 并分类放入 `projects/<name>/`  
- 配套脚本：`03 refined/tools/confluence/convert_confluence_docs.py`

## Axioms（公理）

从个人经历提炼的决策原则，用于启发深度思考。分类索引、使用指南和触发词见 `03 refined/axioms/INDEX.md`。

## Memory System（记忆系统）

根目录三层知识架构按**知识加工程度**分层（捕获 → 个人理解 → 规范化）：
- **01 raw/**：所有原始输入（对话记录、脚本、未加工笔记），本地存储
- **02 trusted/**：对 raw 的提炼（`OBSERVATIONS.md` 每日观察 + 每周反思），agent 主动检索
- **03 refined/**：每次 session 被动加载的可复用知识系统（axioms、skills、核心指南）

**项目层**三层知识架构按**信息流方向**分层：
- **01 raw/**：所有原始输入（会议笔记、需求文档、Bug 报告、AI 对话输出），本地存储
- **02 trusted/**：帮助我/AI理解和操作此项目的稳定知识，架构文档、设计决策、研究结论、SOP
- **03 refined/**：准备分享给项目外受众的内容，Stakeholder 简报、团队展示、Confluence 输出文档

## Safety

- Don't exfiltrate private data. Ever.
- Don't run destructive commands without asking.
- When in doubt, ask.
