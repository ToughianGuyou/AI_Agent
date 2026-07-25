# 2026 AI Agent Knowledge Section Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 在 Obsidian Vault 中建立截至 2026-07-25、具有可追溯原始来源和学习路径的 AI Agent 知识板块。

**Architecture:** 使用 `topics/sources/` 保存逐项来源档案，以 `topics/entities/` 和 `topics/concepts/` 提供稳定导航，再用 `topics/syntheses/` 串联学习路线与跨机构比较。外部材料只在论文原文或机构官方页面得到核验后入库，运行状态和审计信息保存在 `system/`。

**Tech Stack:** UTF-8 Markdown、YAML Frontmatter、Obsidian Wiki links、JSON、PowerShell、Git、官方研究站点与论文数据库。

## Global Constraints

- 统计窗口固定为 2026-01-01 至 2026-07-25。
- 正式论文、可信预印本、官方技术报告、系统卡和提供独有技术细节的官方研究博客可以入选。
- 搜索结果页、二手新闻和无可核验出处的汇总不得作为长期知识证据。
- 至少检索 Anthropic、OpenAI、Google/Google DeepMind、DeepSeek；无合格材料时明确记录“未检得”。
- 不修改 `Clippings/`，不覆盖用户对 `CLAUDE.md` 的修改。
- 所有 `topics/` 与 `system/` 写入必须持有并最终释放 `system/write-lock.json`。
- 2026 年尚未结束，综合页必须显著标注统计截止日期。

---

### Task 1: Vault 启动检查与现有来源增量 Ingest

**Files:**
- Create or modify: `topics/index.md`
- Create or modify: `system/source-state.json`
- Create or append: `system/ingest-log.md`
- Create or modify: `system/lint-report.md`
- Create when required by source: `topics/sources/llm-wiki.md`

**Interfaces:**
- Consumes: `VAULT_SCHEMA.md`、`Clippings/` 文件元数据与 SHA-256。
- Produces: 完整的来源状态表、必要的来源页和可供后续任务使用的主题索引。

- [ ] **Step 1: 扫描现有来源**

计算 `Clippings/` 中非孤立附件文件的相对路径、大小、mtime 和 SHA-256，并与 `system/source-state.json` 比较。

- [ ] **Step 2: 处理新增或变化来源**

完整读取每份待处理来源，先创建或更新对应来源页，再将状态从 `processing` 更新为 `complete`；失败项写为 `failed` 并记录 `last_error`。

- [ ] **Step 3: 验证增量结果**

运行 JSON 解析、Frontmatter 字段检查、索引覆盖检查和 `git diff -- Clippings`。预期：状态 JSON 有效，`Clippings/` 无 Agent 修改。

- [ ] **Step 4: 记录启动 Ingest**

只在存在新增、变化或失败重试来源时向 `system/ingest-log.md` 追加记录，并更新轻量 Lint 报告。

### Task 2: 2026 年候选材料检索与原始来源核验

**Files:**
- Create: `system/research/2026-ai-agent-source-audit.md`

**Interfaces:**
- Consumes: 机构官方研究页、论文原文页、正式出版页和可信预印本元数据。
- Produces: 每个候选的标题、机构、首次公开日期、来源类型、原始链接、Agent 相关性、纳入决定和排除理由。

- [ ] **Step 1: 检索四个必选机构**

分别检索 Anthropic、OpenAI、Google/Google DeepMind、DeepSeek 在统计窗口内的 Agent、tool use、computer use、planning、long-horizon、multi-agent、agent evaluation 和 agent safety 研究。

- [ ] **Step 2: 检索扩展机构**

以同一标准检索 Meta、Microsoft、Alibaba、ByteDance、Moonshot、xAI；只保留有原始来源且与 Agent 直接相关的结果。

- [ ] **Step 3: 双重核验**

用论文原文和机构官方页面或出版元数据交叉确认首次公开日期、机构归属和来源类型；只有一个原始页面时明确记录单源核验。

- [ ] **Step 4: 写入审计清单**

对每个候选写明 `纳入`、`排除` 或 `待验证`。排除项必须包含明确理由，例如“首次公开于 2025 年”“仅产品公告”或“无法确认原始来源”。

### Task 3: 建立来源档案与稳定实体页

**Files:**
- Create: `topics/sources/<经核验的材料标题>.md`
- Create: `topics/entities/Anthropic.md`
- Create: `topics/entities/OpenAI.md`
- Create: `topics/entities/Google DeepMind.md`
- Create: `topics/entities/DeepSeek.md`
- Create only when referenced by an included source: `topics/entities/<扩展机构名称>.md`

**Interfaces:**
- Consumes: Task 2 中标记为 `纳入` 的审计项。
- Produces: 一项材料一个来源页，以及能被学习地图和综述稳定引用的机构页。

- [ ] **Step 1: 生成来源页**

每页使用 `type: source` Frontmatter，并写入来源信息、核心摘要、关键论点、实验或证据、涉及概念与实体、与现有知识的关系、局限性和待验证问题。

- [ ] **Step 2: 标注来源类型与证据强度**

在正文中明确区分正式论文、预印本、技术报告、系统卡和研究博客；单源核验、尚未同行评审或官方自评结果必须显式说明。

- [ ] **Step 3: 建立机构页**

每个机构页使用 `type: entity`，列出本轮检索范围、入选材料、未检得或被排除情况，以及该机构可由证据支持的研究侧重。

- [ ] **Step 4: 检查来源可追溯性**

确认每个来源页至少包含一个可访问的论文或官方原始链接，且重要事实能定位到页面中的来源信息或证据小节。

### Task 4: 建立学习地图、核心概念与年度综述

**Files:**
- Create: `topics/syntheses/AI Agent 学习地图.md`
- Create: `topics/syntheses/2026 年 AI Agent 研究综述.md`
- Create when supported by at least two included sources: `topics/concepts/<稳定概念名称>.md`
- Modify: `topics/index.md`

**Interfaces:**
- Consumes: Task 3 的来源页和机构页。
- Produces: 从学习顺序和研究趋势两个角度组织全部入选材料的导航层。

- [ ] **Step 1: 编写学习地图**

按“基础与架构 → 推理与规划 → 工具与环境 → 记忆与长程任务 → Multi-Agent → 评测与安全”组织推荐阅读，并标明每项材料的先修关系和学习价值。

- [ ] **Step 2: 提取稳定概念**

只有被至少两个来源引用、值得长期维护的概念才建立独立页；概念页必须链接支持它的来源页并区分直接证据与综合判断。

- [ ] **Step 3: 编写年度综述**

比较各机构在方法、环境、评测、可靠性和安全方面的路线，列出共同趋势、关键分歧、证据强度与知识缺口，并标注统计截止日期。

- [ ] **Step 4: 更新总索引**

按 Sources、Concepts、Entities、Syntheses 四类列出所有真实存在的页面；每项包含一句摘要、状态以及来源数或更新时间。

### Task 5: Lint、验收与本地提交

**Files:**
- Modify: `system/lint-report.md`
- Append: `system/ingest-log.md`
- Modify when external research is counted as an archived query: `system/source-state.json`

**Interfaces:**
- Consumes: Tasks 1–4 的全部新增和修改页面。
- Produces: 可审计的验证结果、已释放的写入锁和范围明确的本地 Git 提交。

- [ ] **Step 1: 验证结构**

解析 `system/source-state.json`，检查每个新增 Markdown 文件的 Frontmatter 必填字段、日期格式和 `type` 与目录一致性。

- [ ] **Step 2: 验证链接与索引**

解析新增或修改页面中的 Wiki links，确认目标存在或被明确标为有意未解析；确认所有新增和重命名页面出现在 `topics/index.md`。

- [ ] **Step 3: 验证写入边界**

运行 `git diff -- Clippings` 和 `git status --short`，确认 `Clippings/` 无 Agent 修改、`CLAUDE.md` 的用户修改未被暂存、本轮 diff 不含无关文件。

- [ ] **Step 4: 写入 Lint 与日志**

把轻量 Lint 结果写入 `system/lint-report.md`，向 `system/ingest-log.md` 追加本次归档型 Query 记录；若处理的新来源数量达到 Schema 阈值，再执行并记录深度 Lint。

- [ ] **Step 5: 释放锁并提交**

删除当前会话持有的 `system/write-lock.json`，只暂存本计划生成或更新的知识文件，并使用 `wiki: archive 2026 AI Agent research` 创建本地提交。
