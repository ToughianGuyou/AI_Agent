# Ingest Log

## [2026-07-25 00:00] ingest | llm-wiki

- Agent：Codex
- 原始资料：`Clippings/llm-wiki.md`
- 结果：成功处理 1 个新增来源，0 个跳过，0 个失败。
- 新建页面：`topics/sources/llm-wiki.md`、`topics/index.md`
- 更新状态：初始化 `system/source-state.json`
- 冲突：无。

## [2026-07-25 11:40] query | 2026 AI Agent 研究与学习地图

- Agent：Codex（含只读研究与复核子代理）
- 查询范围：2026-01-01 至 2026-07-25；Anthropic、OpenAI、Google/Google DeepMind、DeepSeek，并扩展 Microsoft、Meta、Alibaba/Qwen、Moonshot。
- 结果：核验并归档 16 个外部研究条目；DeepSeek 严格条件下 0 条，未强行纳入。
- 新建页面：16 个来源页、7 个概念页、9 个实体页、2 个综合页。
- 更新页面：`topics/index.md`、`system/lint-report.md`。
- 冲突：Google 的 ReasoningBank 与 Agent Systems Scaling 官方博客发表于 2026，但论文工件首发于 2025；按严格首次公开口径排除主清单。
- 不确定性：预印本、厂商内部遥测和官方自评尚需同行评审或独立复现。
- Lint：轻量检查通过；35 个内容页 Frontmatter 合法、索引完整、Wiki 链接可解析。
- 待人工处理：无。

## [2026-07-25 13:35] ingest | 2026 AI Agent original materials

- Agent：Codex
- 扫描：18；成功处理：18；跳过：0；失败：0。
- 更新页面：16 个既有来源页；新建来源页：0。
- 更新状态：system/source-state.json 已记录全部 18 个工件；deep_lint_counter=19。
- Clippings：原有文件未在本轮 Ingest 中修改。
- 冲突：0。
- Lint：轻量检查通过；深度 Lint 未触发（counter=19）。

## [2026-07-25 14:00] lint | source provenance correction

- Agent：Codex
- 结果：校正 16 个审计条目的最终状态；更新 13 个来源页的缺失直链，18/18 工件的 URL coverage 完整。
- 工件变动：0；`Clippings/` 与 `system/source-state.json` 未修改。
- 冲突与失败：0。
- Lint：通过；Frontmatter、页面结构、原有外链与本地 Wiki 链接均保留。

## [2026-07-27 12:00] ingest | 深入理解 AI Agent：设计原理与工程实践

- Agent：Claude
- 原始资料：`Clippings/AI Agent/书籍/AI-Agents-in-Depth-zh-CN.pdf` + `.epub`
- 来源 URL：https://github.com/bojieli/ai-agent-book（GitHub Releases latest）
- SHA-256（PDF）：`27dba7a82ce46fbaa60c27a99e633a029db455ec2ccec08c79466c57f317b4ac`
- SHA-256（EPUB）：`e5dbd5340fd861e0b418e163ee7462b7c035633bd89367af4b97762d4c1bf87a`
- 结果：成功处理 2 个新增来源，0 个跳过，0 个失败。
- 新建页面：
  - `topics/sources/深入理解 AI Agent.md`
  - `topics/concepts/上下文工程.md`
  - `topics/concepts/Coding Agent 与代码元能力.md`
  - `topics/entities/李博杰.md`
- 更新页面（8 个）：
  - `topics/concepts/Agent 自主性与人类监督.md`：补充 Harness 工程与模型演进观
  - `topics/concepts/工具增强与环境交互.md`：补充五类工具分类、MCP、ACI 原则
  - `topics/concepts/Agent 记忆与经验学习.md`：补充四种记忆格式、User as Code、三层次评估、持续进化闭环
  - `topics/concepts/Multi-Agent 系统设计.md`：补充 2×3 分类框架与"新信息"判据
  - `topics/concepts/Agent 评测与失败诊断.md`：补充两种评估范式、Rubric 四准则、三层轨迹验证
  - `topics/concepts/长程 Agent 与轨迹安全.md`：补充致命三要素+持久记忆、沙盒防御
  - `topics/syntheses/AI Agent 学习地图.md`：补充全书学习路径与章节引用
  - `topics/syntheses/2026 年 AI Agent 研究综述.md`：纳入书籍为第 17 项来源
- 冲突：无。
- 不确定性：书中 Pine AI 实践经验为作者自述，部分无法独立验证。
- 待人工处理：无。
