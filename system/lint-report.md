# Lint Report

## 2026-07-27 light | ingest 深入理解 AI Agent

- 范围：4 个新建页面（1 来源、2 概念、1 实体）+ 8 个更新页面。
- Frontmatter：通过；新建与更新页面的 type/status/created/updated/sources/tags 字段均合法。
- Wiki 链接：通过；新建页面内 25 个 Wiki 链接全部可解析，更新页面新增链接指向已存在页面。
- 来源可追溯性：通过；原始文件 SHA-256 校验通过，来源 URL 已记录。
- 索引覆盖：通过；4 个新页面均出现在 `topics/index.md`，8 个更新页面的来源数/日期已同步。
- 来源状态 JSON：通过；`system/source-state.json` 新增 2 个 Clippings 条目，JSON 格式有效。
- 重复页与孤立页：未发现。
- 冲突与过时主张：未发现。
- 深度 Lint：未触发；`deep_lint_counter=19`，距阈值（20）差 1，建议下一次新增资料后触发深度 Lint。

## 2026-07-25 light | source provenance correction

- 审计状态与来源页直链已校正，18/18 URL coverage。
- 范围：16/16 主条目、18/18 本地工件（PDF 14、网页快照 4）；失败 0、冲突 0。
- 来源直链：每个来源页均保留原有 URL 与本地 Wiki 链接，并覆盖 manifest 的 landing_url、download_url、acquired_from_url（如有）及 supplementary_artifacts 下载 URL。
- Frontmatter、页面结构与 Wiki 链接：通过；未修改 `system/source-state.json` 或 `Clippings/`。

## 2026-07-25 light | 2026 AI Agent original materials

- 范围：16 个来源页与 18 个本地原始工件。
- Frontmatter：通过；16 个来源页均为 type: source，且 sources 仅包含可解析的库内工件 Wiki 链接。
- 工件链接：通过；18 个本地工件均可解析，其中 PDF 14 份、网页快照 4 份。
- manifest/source-state：通过；路径、大小与 SHA-256 三方一致，18 个工件均可追溯至外部 URL。
- 工件可读性：通过；14 份 PDF 可解析，4 份网页快照 Frontmatter 合法。
- 索引与页面关系：通过；topics/index.md 已覆盖全部 16 个来源页，无需变更；未发现重复页、孤立页或非预期断链。
- 深度 Lint：未触发；deep_lint_counter=19。

# Lint Report

## 2026-07-25 light | 2026 AI Agent knowledge section

- 范围：16 个外部研究来源页、7 个概念页、9 个实体页、2 个综合页，以及既有 `llm-wiki` 来源页。
- Frontmatter：通过；35 个内容页均包含必填字段，`type` 与目录一致。
- 来源状态 JSON：通过；`system/source-state.json` 和活动写入锁均可解析。
- 索引覆盖：通过；35 个内容页均出现在 `topics/index.md`。
- Wiki 链接：通过；新增和修改页面中的内部链接均解析到真实文件。
- 来源可追溯性：通过；16 个研究条目均记录论文原文或机构官方页面。
- 重复页与孤立页：未发现。
- 冲突与过时主张：未发现；Google Research 与 Google DeepMind 已分别归属其 2 项材料，Google 两项 2025 首发论文和 DeepSeek 0 条结果已明确记录日期边界。
- 证据缺口：多数厂商材料仍是预印本、内部遥测或官方自评，跨论文结果不可直接排名。
- 深度 Lint：未触发；本轮 `Clippings/` 增量 Ingest 仅处理 1 个新来源，未达到 20 个阈值。

## 2026-07-25 light

- 范围：首次 Ingest（`Clippings/llm-wiki.md`）
- Frontmatter：通过。
- 来源状态 JSON：通过。
- 索引覆盖：通过。
- Wiki 链接：通过；链接目标均存在。
- 来源可追溯性：通过；来源页链接到 `[[Clippings/llm-wiki]]`，并记录该资料 Frontmatter 提供的原始网页地址。
- 重复页与孤立页：未发现。
- 冲突与过时主张：未发现。
