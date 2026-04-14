# WORKSPACE.md - 目录路由速查

目标：让 AI 每轮 session 都能快速知道"去哪里找/放什么"。**找任何文件前先查这里。**

## 路由规则

### 项目与代码
- **持续进行的项目上下文**（文档、会议记录、决策、状态）：`projects/<project>/`
- 写代码 / 跑脚本 / 一次性项目：`01 raw/<project>/`
- 工具脚本（邮件、语义搜索、分享报告等）：`03 refined/tools/`
- **公司级平台规范**（Python / SQL / Databricks / 表设计标准等，跨项目通用）：`projects/guidelines/`

### 知识与记录
- 原始输入（对话记录、调研资料、未加工笔记）：`01 raw/`
- 加了个人理解的复盘 / 结构化反思 / 方法论笔记：`02 trusted/`
- 每日观察 + 每周反思（OBSERVATIONS.md）：`02 trusted/OBSERVATIONS.md`

### 系统与规则
- 可复用技术方案 / Skill：`03 refined/skills/`
- 核心公理（Axioms）：`03 refined/axioms/`

## 命名规则
- 目录和文件名：小写 + 下划线 (snake_case)
- 临时项目：`tmp_<name>/`
- **带日期的文档统一格式：`YYYYMMDD_<name>.md`**
  - 例：`20260408_auto_trigger_chunking_on_table_change.md`
  - 适用范围：01 raw、02 trusted 下所有带时间戳的文档
  - 日期取文档创建当天，不用分隔符（不用 `2026-04-08` 或 `2026_04_08`）

## Python 环境
- 根目录 `.venv/` 为工作区级环境，用 `uv pip install` 管理依赖
- 需要隔离时在 `01 raw/<project>/.venv/` 建独立环境

## 工具索引

| 文件 | 用途 |
|---|---|
| `03 refined/tools/confluence/convert_confluence_docs.py` | Confluence .doc → Markdown 批量转换脚本（见 `03 refined/skills/workflow_confluence_sync.md`） |
| `03 refined/tools/semantic_search/` | 语义搜索工具（见 `03 refined/skills/semantic_search.md`） |

## 快速查询

<!-- 随着项目增长，在这里添加活跃项目的快捷路由 -->
<!-- 格式：- `project-name` -> `projects/project_name/` (说明) -->
- `marvin` → `projects/marvin/` （Contact Energy 内部 RAG 信息检索工具）
- `guidelines` → `projects/guidelines/` （公司级平台规范：Python、SQL、Databricks、表设计、转换逻辑等）
