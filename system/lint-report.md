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
