# Workflow: Confluence 文档导入

## 元数据

- **类型**: Workflow
- **适用场景**: 将 Confluence 文档导出为 Markdown，放入 `projects/<name>/docs/` 作为 AI context
- **创建日期**: 2026-04-07
- **工具依赖**: `tools/convert_confluence_docs.py`（批量转换）、`html2text`（Python）

---

将 Confluence 文档导出为 Markdown 并放入 `projects/<name>/docs/` 的标准操作流程。

---

## 方法一：单页面导出（推荐，少量文档）

**适用**：一次导出 1-5 个页面，格式复杂（有表格、代码块）。

### 步骤

```bash
# 前置：安装 pandoc
sudo apt install pandoc   # Linux
brew install pandoc       # macOS

# 步骤 1：在 Confluence 页面点击 ··· → Export → Word (.docx) 下载
# 步骤 2：用 pandoc 转换
pandoc input.docx -t markdown-raw_html --wrap=none -o output.md

# 步骤 3：人工检查输出，清理多余的格式标记
# 步骤 4：按文档类型放入对应目录
#   PRD/设计文档  → projects/marvin/docs/prd/
#   架构/技术规范 → projects/marvin/docs/architecture/
#   SOP/操作手册  → projects/marvin/docs/sops/
#   调研报告      → projects/marvin/docs/research/
```

**命名规范**：`YYYY-MM-DD_<page-title-snake-case>.md`  
例：`2025-10-01_marvin_system_architecture.md`

---

## 方法二：浏览器复制（最快，纯文字页面）

**适用**：文档以文字为主，格式简单，1-2页。

1. Confluence 页面上 `Ctrl+A` 全选 → `Ctrl+C` 复制
2. 粘贴到编辑器，手动整理为 Markdown
3. 保存到对应 `docs/` 子目录

---

## 方法三：REST API 批量导出（多页面）

**适用**：整个 Confluence Space 下有 10+ 页面需要批量导入。

### 前置条件

- Atlassian Personal Access Token（PAT）
- 确认 Confluence 类型：Cloud（`*.atlassian.net`）还是 Server/Data Center（内部 URL）

### 安装工具

```bash
cd /opt/processes/mc_platform/context-infrastructure
# 激活工作区 venv
source /opt/processes/mc_platform/venv/bin/activate
pip install confluence-markdown-exporter
```

### 导出命令

```bash
# Atlassian Cloud
confluence-markdown-exporter \
  --url https://<your-domain>.atlassian.net \
  --token <your-PAT> \
  --space-key <SPACE_KEY> \
  --output projects/marvin/docs/

# Server/Data Center（内部部署）
confluence-markdown-exporter \
  --url https://<internal-confluence-url> \
  --token <your-PAT> \
  --space-key <SPACE_KEY> \
  --output projects/marvin/docs/
```

> **注意**：批量导出后需要手动将文件按类型分类到 `prd/`、`architecture/`、`sops/`、`research/` 子目录，并更新 `projects/marvin/README.md` 的文档索引表。

---

## 导入后的清理检查清单

- [ ] 文件命名符合 `YYYY-MM-DD_<title>.md` 格式
- [ ] 放置在正确的子目录中
- [ ] 检查图片：Confluence 导出的图片通常是附件路径，需要手动处理（截图重新粘贴或删除）
- [ ] 检查内部链接（Confluence 页面链接不可用，改为相对路径或注释说明）
- [ ] 更新 `projects/marvin/README.md` 的文档索引表
- [ ] 在 `context/status.md` 记录本次导入的时间和范围

---

## 从 Repo 输出回 Confluence 的工作流

当你在 repo 中积累了会议记录、决策文档后，定期生成更新的 Confluence 页面：

1. 让 AI 根据 `context/meetings/` 和 `context/decisions/` 生成摘要或更新版本的文档
2. 人工审查 + 调整格式
3. 在 Confluence 创建/更新对应页面（手动粘贴 Markdown，Confluence 支持 Markdown 粘贴）
4. 在 `context/status.md` 记录"已同步回 Confluence"

---

*此 Skill 存放于 `rules/skills/workflow_confluence_import.md`。*
