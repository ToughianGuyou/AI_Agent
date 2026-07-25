# Agent 管理原始材料实施计划

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 允许 Agent 在用户授权下受控新增 `Clippings/` 原始材料，并为现有 16 项 2026 AI Agent 研究落地可在 Obsidian 中打开的 PDF 或 Markdown 网页快照。

**Architecture:** `Clippings/AI Agent/2026/` 保存不可静默覆盖的原始工件，`topics/sources/` 保存可检索、可链接的中文知识页，`system/source-state.json` 以 SHA-256 跟踪增量状态。规则层将“绝对只读”改为“授权新增、既有内容只读”，所有 Wiki 更新仍受写锁保护。

**Tech Stack:** Obsidian Markdown/Wiki links、PDF、YAML Frontmatter、JSON、PowerShell、Git、SHA-256。

## Global Constraints

- 仅在用户明确要求搜集、下载、剪藏或保存来源时新增 `Clippings/` 内容。
- 不覆盖、修改、移动、重命名或删除任何既有 `Clippings/` 文件。
- 目标目录固定为 `Clippings/AI Agent/2026/PDF/` 与 `Clippings/AI Agent/2026/Web/`。
- 优先保存公开论文或技术报告 PDF；无独立 PDF 时保存 UTF-8 Markdown 官方网页快照。
- 所有工件必须保留原 URL、抓取日期和 SHA-256；PDF 必须通过解析验证。
- 不绕过付费墙、登录墙、robots 限制或访问控制。
- 不修改 `CLAUDE.md`；保留所有无关工作树改动。
- DeepSeek 没有符合当前严格口径的 2026 Agent 条目，不制造替代材料。

---

### Task 1: 更新 Vault 权限协议

**Files:**
- Modify: `VAULT_SCHEMA.md`
- Modify: `AGENTS.md`

**Interfaces:**
- Consumes: `system/designs/2026-07-25-agent-managed-clippings-design.md`
- Produces: Agent 新增原始材料的权限边界与启动/验证规则

- [ ] **Step 1: 记录当前规则冲突**

运行：

```powershell
rg -n "Clippings|不得修改|只能读取|never modify" VAULT_SCHEMA.md AGENTS.md
```

预期：找到绝对只读、不得修改 `Clippings/` 的旧条款。

- [ ] **Step 2: 修改共享 Schema**

将 `Clippings/` 所有权规则改为：

- 用户剪藏和已有文件默认只读；
- 用户明确授权的搜集任务允许 Agent 新增文件和目录；
- 同名同哈希复用，同名异哈希停止并报告；
- 修改、覆盖、移动、重命名、删除仍需明确确认；
- 下载先写临时文件，校验后再移入目标路径；
- 新增材料必须进入增量 Ingest。

- [ ] **Step 3: 修改 Codex 入口规则**

将 `AGENTS.md` 的绝对禁止修改改为与 Schema 一致的“授权新增”，并在验证清单加入：

- 已有 Clippings 未被修改；
- 新增工件有来源 URL、抓取时间、哈希；
- PDF 可解析，网页快照 Frontmatter 合法。

- [ ] **Step 4: 验证规则一致**

运行：

```powershell
rg -n "受控新增|明确授权|覆盖|重命名|删除|SHA-256|PDF" VAULT_SCHEMA.md AGENTS.md
git diff --check -- VAULT_SCHEMA.md AGENTS.md
```

预期：两个入口不再互相矛盾，且无空白错误。

- [ ] **Step 5: 创建范围提交**

```powershell
git add -- VAULT_SCHEMA.md AGENTS.md
git commit -m "wiki: allow controlled clipping acquisition"
```

---

### Task 2: 建立 16 项来源的落地清单

**Files:**
- Modify: `system/research/2026-ai-agent-source-audit.md`
- Create: `system/research/2026-ai-agent-material-manifest.json`

**Interfaces:**
- Consumes: 审计中的纳入清单和官方原始链接
- Produces: 每项来源的 `source_page`、`landing_url`、`artifact_kind`、`download_url`、`target_path`

- [ ] **Step 1: 逐项核验官方入口**

对审计内 16 项材料逐项确认论文直链或官方网页入口；技术研究优先 arXiv/出版方 PDF，官方单源条目使用官方网页。

- [ ] **Step 2: 写入确定性 manifest**

JSON 顶层结构：

```json
{
  "schema_version": 1,
  "captured": "2026-07-25",
  "items": [
    {
      "title": "完整标题",
      "organization": "机构",
      "source_page": "topics/sources/文件名.md",
      "landing_url": "https://...",
      "artifact_kind": "pdf",
      "download_url": "https://...",
      "target_path": "Clippings/AI Agent/2026/PDF/文件名.pdf"
    }
  ]
}
```

`artifact_kind` 只能是 `pdf` 或 `official-web`；文件名必须清除 Windows 禁用字符。

- [ ] **Step 3: 在审计中记录落地策略**

为纳入清单增加“本地工件”说明，指向 manifest，并保留不可获取时的失败原因字段。

- [ ] **Step 4: 验证 16 项一一对应**

运行 PowerShell JSON 检查：

```powershell
$m = Get-Content -Raw -Encoding UTF8 'system/research/2026-ai-agent-material-manifest.json' | ConvertFrom-Json
if ($m.items.Count -ne 16) { throw "Expected 16 manifest items" }
$m.items | Group-Object source_page | Where-Object Count -ne 1
```

预期：恰好 16 项，无重复来源页。

- [ ] **Step 5: 创建范围提交**

```powershell
git add -- system/research/2026-ai-agent-source-audit.md system/research/2026-ai-agent-material-manifest.json
git commit -m "wiki: map AI Agent source artifacts"
```

---

### Task 3: 下载并验证原始工件

**Files:**
- Create: `Clippings/AI Agent/2026/PDF/*.pdf`
- Create: `Clippings/AI Agent/2026/Web/*.md`
- Modify: `system/research/2026-ai-agent-material-manifest.json`

**Interfaces:**
- Consumes: Task 2 manifest
- Produces: 可在 Obsidian 打开的原始材料，以及每项的 `status`、`sha256`、`size`、`captured_at`、`error`

- [ ] **Step 1: 预检目标不存在**

对每个 `target_path` 使用 `Test-Path -LiteralPath`。已存在时计算哈希；相同则复用，不同则标记 `conflict` 并停止该项。

- [ ] **Step 2: 获取到临时目录**

PDF 只接受 `%PDF-` 文件签名和非空响应。网页快照从官方页面抽取标题、机构、日期、正文与图表说明，写入设计规定的 YAML Frontmatter。

- [ ] **Step 3: 校验后原子移动**

计算 SHA-256、文件大小并解析 PDF；验证成功后使用同一文件系统内的 `Move-Item -LiteralPath` 移到正式路径。

- [ ] **Step 4: 回写 manifest 结果**

每项追加：

```json
{
  "status": "complete",
  "sha256": "64位十六进制",
  "size": 123,
  "captured_at": "2026-07-25T00:00:00+08:00",
  "error": null
}
```

失败项使用 `status: failed` 并记录明确错误，不创建伪原文。

- [ ] **Step 5: 验证工件**

运行：

```powershell
Get-ChildItem -File -Recurse 'Clippings/AI Agent/2026' | Get-FileHash -Algorithm SHA256
```

并用 PDF 解析器逐个打开 PDF；Markdown 快照逐个检查 Frontmatter、正文非空与 `source_url`。

- [ ] **Step 6: 创建范围提交**

```powershell
git add -- 'Clippings/AI Agent/2026' system/research/2026-ai-agent-material-manifest.json
git commit -m "wiki: preserve 2026 AI Agent source artifacts"
```

---

### Task 4: 增量摄取并链接本地原文

**Files:**
- Modify: `topics/sources/*.md`（仅 16 个现有来源页）
- Modify: `topics/syntheses/2026 年 AI Agent 研究综述.md`
- Modify: `topics/syntheses/AI Agent 学习地图.md`
- Modify: `system/source-state.json`
- Modify: `system/ingest-log.md`
- Modify: `system/lint-report.md`
- Modify: `topics/index.md`（仅在摘要或来源数需要更新时）

**Interfaces:**
- Consumes: Task 3 的 manifest 与原始工件
- Produces: 从知识页到库内原文的可解析 Wiki 链接和完整增量状态

- [ ] **Step 1: 获取写锁并扫描**

按 `VAULT_SCHEMA.md` 创建 `system/write-lock.json`，计算所有新增工件的相对路径、大小、mtime 和 SHA-256。

- [ ] **Step 2: 更新来源页**

每个来源页 Frontmatter 的 `sources` 使用库内工件 Wiki 链接；“来源信息”节补充原始 URL、直接下载 URL、抓取日期、SHA-256 和本地原文链接。失败项保留外部链接并明确说明。

- [ ] **Step 3: 更新状态与综合页**

将每个成功工件写入 `system/source-state.json` 并标记 `complete`；只有内容结论发生变化时才更新综合页正文，否则仅修正来源链接。

- [ ] **Step 4: 追加 Ingest 日志**

追加一次汇总记录，报告扫描数、成功数、失败数、更新页面和冲突；不得重写旧日志。

- [ ] **Step 5: 运行轻量 Lint**

检查所有变更 Markdown Frontmatter、Wiki 链接目标、索引覆盖、重复来源页、JSON 有效性和哈希一致性；将结果写入 `system/lint-report.md`。

- [ ] **Step 6: 释放写锁并提交**

验证完成后删除当前任务的 `system/write-lock.json`，仅暂存本任务文件：

```powershell
git commit -m "wiki: ingest 2026 AI Agent original materials"
```

---

### Task 5: 全量验收

**Files:**
- Verify only: `Clippings/AI Agent/2026/`
- Verify only: `topics/`
- Verify only: `system/`
- Verify only: `VAULT_SCHEMA.md`
- Verify only: `AGENTS.md`

**Interfaces:**
- Consumes: Tasks 1–4 的全部提交
- Produces: 可复核的完成报告

- [ ] **Step 1: 核对需求覆盖**

逐项对照设计文档验收标准，确认 16 项都有成功工件或明确失败记录。

- [ ] **Step 2: 核对文件完整性**

重新计算所有新工件 SHA-256，与 manifest 和 `source-state.json` 比较；重新解析所有 PDF。

- [ ] **Step 3: 核对知识结构**

验证 16 个来源页的本地 Wiki 链接目标存在，Frontmatter 合法，`topics/index.md` 无遗漏，`system/source-state.json` 可被 `ConvertFrom-Json` 解析。

- [ ] **Step 4: 核对写入安全**

确认 `Clippings/llm-wiki.md` 与基线提交内容一致、`CLAUDE.md` 未被本任务暂存或提交、无 `system/write-lock.json`。

- [ ] **Step 5: 检查 Git**

运行：

```powershell
git status --short
git log --oneline -8
git diff --check
```

预期：只剩用户原有的未提交修改；本任务提交范围清晰，无远程推送。
