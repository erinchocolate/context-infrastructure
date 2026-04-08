# Observations（观察记录）

> 三层记忆系统的 L1/L2 层。每日观察在这里积累，每周反思在这里蒸馏。
>
> 红黄绿优先级系统：
> - 🔴 红：跨项目的方法论/约束洞察，3 个月后仍有复用价值
> - 🟡 黄：活跃项目的决策/进展，未来几周内需要
> - 🟢 绿：常规任务完成记录，1-2 周后可清理

---

<!-- 观察记录从这里开始，格式如下：

## YYYY-MM-DD

🔴 [跨项目洞察内容]

🟡 [项目决策/进展]

🟢 [常规任务完成]

---

## 周反思：YYYY-MM-DD 至 YYYY-MM-DD

### 本周模式
[从本周观察中识别的重复模式]

### 晋升候选
[满足晋升条件的观察，候选成为 axiom 或 skill]

### 清理
[已过期的绿色条目，已处理的黄色条目]

-->

## 2026-04-08

🟡 Confluence 双向同步工具完成：`pull_from_confluence.py` 和 `sync_docs_to_confluence.py` 均已落地，并配套更新了 `workflow_confluence_import.md` skill。Confluence ↔ 本地文档的完整工作流现在有可执行的脚本支撑。

🟡 AI Heartbeat 系统完整配置完成：替换所有占位符路径、修复 `.env` 变量名不匹配 bug（`OPENCODE_API_URL` vs `OPENCODE_BASE_URL`）、配置 venv、新增 SETUP_LOG.md 记录全过程。每日 observer + 每周 reflector 的定时任务链路已就绪。

🔴 `.env.example` 中的变量名与代码实际读取的变量名不一致是常见坑：发布 template 时变量名对不上，配置者按示例文件走却无法生效。维护工具类 repo 时，`.env.example` 要与代码同步更新，不能只改代码忘了示例。

🔴 Delta 表全量 overwrite 会让 CDF 记录所有行删除+插入，导致下游 CDF 监听者（如 vector search index）每次全量重跑——即使数据没变化。凡是有下游 CDF 消费者的 Delta 表，写入策略应优先考虑 merge，让 CDF 只记录真正变化的行，避免级联浪费。

🟡 Marvin：设计了两项 pipeline 优化（增量 chunking 用 merge 替代 overwrite、Airflow ShortCircuitOperator 自动跳过无变更日的 chunking 触发），文档已落地但均未实现，等待下一步排期。

🟡 Marvin prod 迁移：主要依赖和待确认事项已整理为 meeting agenda（`meetings/20260409_vector_search_prod_migration.md`），核心阻塞是 prod workspace 能否启用 Foundation Model API `databricks-gte-large-en`——需 Data Architect 确认后才能推进代码改动。

---
