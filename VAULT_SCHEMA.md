# Vault Schema

本文件是本 Obsidian Vault 的公共知识库协议，适用于获得本仓库写入权限的 LLM Agent。它依据 `Clippings/llm-wiki.md` 所描述的 llm-wiki 模式制定，不依赖任何特定模型、聊天界面或插件。

本协议的目标不是建立一次性问答系统，而是维护一个持续积累、相互链接、可追溯且可演进的本地 Wiki。

## 1. 权威与职责

规则优先级从高到低为：

1. 用户在当前任务中的明确要求。
2. 当前 Agent 的入口规则文件，例如 Codex 的 `AGENTS.md`。
3. 本文件 `VAULT_SCHEMA.md`。
4. 已有 Wiki 页面中记录的局部约定。

角色分工：

- 用户负责收集资料、提出问题、确定研究方向和处理高影响决策。
- Agent 负责读取资料、提炼知识、维护页面、建立链接、发现矛盾、更新索引和记录操作。
- Obsidian 是浏览、检查和人工编辑界面。
- Markdown 文件与 Git 历史是可移植的知识资产，不把聊天记录当作唯一存储。

任何 Agent 都不得把另一个 Agent 的私有会话、缓存或模型设置当作知识来源。

## 2. 三层架构与目录所有权

```text
Vault/
├── VAULT_SCHEMA.md
├── AGENTS.md
├── CLAUDE.md
├── Clippings/
│   └── assets/
├── topics/
│   ├── index.md
│   ├── concepts/
│   ├── entities/
│   ├── syntheses/
│   └── sources/
└── system/
    ├── source-state.json
    ├── ingest-log.md
    ├── lint-report.md
    └── write-lock.json
```

### 2.1 原始资料层：`Clippings/`

- 这是事实追溯的源头。
- Agent 只能读取，不得修改、重命名、移动或删除其中的文件。
- `Clippings/assets/` 保存本地图片和附件；引用图片时先读正文，再按需要单独检查图片。
- 原文中的现有 Frontmatter、数字 ID 链接和其他格式必须原样保留。

### 2.2 Wiki 层：`topics/`

- 这是 Agent 负责创建和维护的持久知识层。
- `topics/sources/`：单份原始资料的忠实提炼页。
- `topics/concepts/`：概念、理论、方法和原则。
- `topics/entities/`：人物、组织、项目、工具与其他命名实体。
- `topics/syntheses/`：跨来源比较、综合分析、长期有效的问答成果。
- `topics/index.md`：面向用户和 Agent 的全库内容导航。

页面宁少勿碎。优先更新一个扎实的既有主题页，不为每个术语机械创建页面。只有当一个概念值得独立解释、被多个页面引用或将持续积累时，才创建独立页面。

### 2.3 Schema 与运行状态层

- `VAULT_SCHEMA.md` 是公共知识库协议。
- Agent 专用入口文件只补充该 Agent 的启动和工具行为，不复制整套 Schema。
- `system/source-state.json` 保存增量导入状态。
- `system/ingest-log.md` 是只追加的活动日志。
- `system/lint-report.md` 保存最近一次健康检查结果。
- `system/write-lock.json` 防止两个 Agent 同时修改 Wiki。

除用户明确要求外，Agent 的自动写入范围仅限 `topics/` 和 `system/`。修改根目录规则文件属于配置变更，必须由用户明确发起。

## 3. 页面模型

Agent 生成的 Wiki 页面使用 UTF-8 Markdown 和以下 Frontmatter：

```yaml
---
type: source | concept | entity | synthesis
status: seed | growing | mature | disputed | stale
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources:
  - "[[Clippings/原始资料文件名]]"
tags:
  - tag-name
aliases:
  - 可选别名
---
```

字段规则：

- `type` 必须与页面职责一致。
- `status` 表示知识成熟度；存在未解决的来源冲突时使用 `disputed`，来源全部失效时使用 `stale`。
- `created` 首次建立后保持不变。
- `updated` 仅在内容发生实质变化时更新。
- `sources` 列出支撑该页的原始资料；不得用聊天回答代替来源。
- `tags` 保持扁平、少量并尽量复用。
- `aliases` 仅在确有同义名称或常用译名时添加。

概念页、实体页和综合页默认采用：

```markdown
# 页面标题

## 概述

## 核心内容

## 证据与来源

## 分歧与不确定性

## 相关主题
```

来源页至少包含：

```markdown
# 来源标题

## 来源信息

## 核心摘要

## 关键论点

## 涉及的概念与实体

## 与现有知识的关系

## 待验证问题
```

小节可以按内容需要增减，但来源、证据和不确定性不得省略。

## 4. 命名、链接与证据

- 文件名使用清晰的中文名称或原始专名，不使用随机编号。
- 内部关系使用 Obsidian `[[Wiki 链接]]`。
- 链接原始资料时优先写完整 Vault 路径，例如 `[[Clippings/llm-wiki]]`，避免同名歧义。
- 每项重要事实、数字、主张或归因都必须能追溯到原始资料。
- 来源直接陈述与 Agent 的综合判断必须分开表达。
- 推论使用“综合判断”“推测”或同等明确措辞标记。
- 不确定内容写入“分歧与不确定性”或“待验证问题”，不得伪装成确定事实。
- 新资料与旧结论冲突时保留双方证据，不静默覆盖；相关页面标记为 `disputed`。
- 相同概念存在多个名称时选择一个主页面，其他名称写入 `aliases`，并修复指向重复页的链接。
- 标签用于宽泛分类，具体关系依靠 Wiki 链接表达。

## 5. 写入锁与多 Agent 协作

任何会修改 `topics/` 或 `system/` 的工作流都必须先取得 `system/write-lock.json`。只读查询不需要锁。

锁文件格式：

```json
{
  "schema_version": 1,
  "agent": "codex-or-claude",
  "session": "可识别当前任务的名称或 ID",
  "purpose": "ingest-or-query-or-lint",
  "created_at": "YYYY-MM-DDTHH:mm:ss+08:00",
  "heartbeat_at": "YYYY-MM-DDTHH:mm:ss+08:00"
}
```

取得锁的规则：

1. 确认 `system/` 存在。
2. 以“不覆盖已有文件”的方式创建 `write-lock.json`。
3. 如果锁已存在，读取锁内容并停止写入。
4. 能确认原持有者仍在运行时，等待其完成或由用户决定下一步。
5. 锁超过 2 小时只能视为“疑似过期”，不得仅凭时间自动删除。
6. 无法确认原任务状态时，请求用户批准后才可移除疑似过期锁。
7. 长任务至少每 15 分钟更新一次 `heartbeat_at`。
8. 完成写入并验证后删除自己的锁；失败时先记录错误，再释放自己的锁。

禁止两个 Agent 同时执行 Ingest、归档型 Query 或 Lint 修复。一个 Agent 写入时，另一个 Agent只能执行不依赖未提交结果的只读工作。

## 6. 启动与增量检测

当任务涉及本 Vault 的知识查询、导入、整理或维护时，Agent 首先执行：

1. 读取本文件和自己的入口规则。
2. 检查 Git 工作区，识别尚未提交的用户或其他 Agent 修改。
3. 读取 `topics/index.md`、`system/source-state.json` 和最近五条 `system/ingest-log.md`；文件不存在时按本协议初始化。
4. 扫描 `Clippings/`，但跳过 `Clippings/assets/` 中未被正文引用的附件。
5. 使用相对路径、文件大小、修改时间和 SHA-256 内容哈希判断资料状态。
6. 如果存在新增、变更或失败待重试的资料，在取得写入锁后先执行增量 Ingest。
7. 如果没有待处理资料，直接继续当前任务，不制造空提交或无意义日志。

`system/source-state.json` 的顶层格式：

```json
{
  "schema_version": 1,
  "last_scan_at": "YYYY-MM-DDTHH:mm:ss+08:00",
  "deep_lint_counter": 0,
  "sources": {}
}
```

每个 `sources` 条目以 Vault 相对路径为键，至少包含：

```json
{
  "size": 0,
  "mtime": "YYYY-MM-DDTHH:mm:ss+08:00",
  "sha256": "hex-digest",
  "status": "new | processing | complete | failed | changed | missing",
  "processed_at": "YYYY-MM-DDTHH:mm:ss+08:00",
  "source_page": "topics/sources/页面名.md",
  "last_error": null
}
```

修改状态文件时保持有效 JSON、稳定字段名和确定性排序，减少无意义 Git 差异。

## 7. Ingest 工作流

Ingest 必须可重复运行且不产生重复知识：

1. 取得写入锁。
2. 将当前资料状态标记为 `processing`。
3. 完整阅读原始资料；按需检查被引用的本地图片。
4. 检索 `topics/index.md` 和相关页面，先判断更新既有页面还是创建新页面。
5. 创建或更新对应来源页，忠实记录原文要点和来源信息。
6. 提取值得长期维护的概念、实体、关系、证据、矛盾和知识缺口。
7. 更新相关概念页、实体页和综合页；不机械追求页面数量。
8. 更新所有受影响页面的来源、交叉链接和状态。
9. 更新 `topics/index.md`。
10. 执行轻量 Lint。
11. 页面与索引写入成功后，将资料标记为 `complete` 并保存最终哈希。
12. 向 `system/ingest-log.md` 追加记录。
13. 验证写入结果并释放锁。

原始资料发生变化时，重新读取全文并更新提炼结果。不得只根据文件差异猜测新含义。

原始资料被移走时：

- 状态标记为 `missing`。
- 保留已经提炼的知识和来源页。
- 在相关页面标明来源当前不可用。
- 不自动删除任何 Wiki 页面。

单篇资料失败时：

- 将该资料标记为 `failed` 并写入 `last_error`。
- 记录失败日志。
- 继续处理其他互不依赖的资料。
- 下次启动时自动重试。

若单次扫描发现超过 20 个既有来源变为 `missing`，或至少 25% 的已处理来源同时变化或缺失，暂停跨页面整合并请求用户确认，避免把目录移动误判为知识删除。

## 8. Query 工作流

回答知识库问题时：

1. 先完成启动与增量检测。
2. 先读 `topics/index.md`，再深入相关 Wiki 页面。
3. 必要时回到 `Clippings/` 核对原始证据。
4. 回答时区分来源事实、已有综合结论和本次新推论。
5. 提供可点击或可搜索的 Wiki 来源链接。
6. 明确报告资料不足、来源冲突和时间敏感性。

以下回答具有归档价值：

- 综合两个或更多来源得到的新结论。
- 可复用的比较、框架、决策记录或研究综述。
- 新发现的稳定关系或对既有主题的实质修正。

归档型 Query 必须取得写入锁，把成果写入合适的 `topics/syntheses/` 或既有主题页，更新索引并追加日志。一次性说明、寒暄、操作指导和未经验证的猜测不归档。

## 9. Lint 工作流

### 9.1 轻量 Lint

每次 Ingest 或归档型 Query 后检查：

- 失效或歧义的 Wiki 链接。
- 缺失、非法或不一致的 Frontmatter。
- 重要事实缺少来源。
- 重复或明显近义的页面。
- 没有合理入链或出链的孤立主题页。
- 新旧资料之间的明显矛盾。
- `topics/index.md` 是否遗漏新增或重命名页面。

结果写入 `system/lint-report.md`。低风险修复可以在当前锁内完成；删除页面、大范围改名或主题合并只提出建议。

### 9.2 深度 Lint

每累计成功处理 20 篇新增或变更资料后执行：

- 全库跨页面一致性检查。
- 过时结论和被新来源取代的主张检查。
- 主题合并建议。
- 页面成熟度与争议状态检查。
- 索引覆盖检查。
- 重要知识缺口和建议补充来源。

深度 Lint 不得自动删除页面或执行大范围合并。

## 10. 索引规则

`topics/index.md` 是中等规模知识库的首要导航入口，按以下类别组织：

- Sources
- Concepts
- Entities
- Syntheses

每个条目至少包含：

- `[[页面链接]]`
- 一句话摘要
- 页面状态
- 来源数量或最近更新时间中的至少一项

每次 Ingest、归档型 Query、页面重命名或合并后都更新索引。索引只列真实存在的页面，不创建空壳条目。

当知识库达到约 500–1000 篇页面，或索引检索已明显无法稳定找到相关内容时，可以建议增加 qmd 等本地搜索工具；在此之前不引入向量数据库或云端 RAG。

## 11. 日志规则

`system/ingest-log.md` 只能追加，不能重写历史。标题格式：

```markdown
## [YYYY-MM-DD HH:mm] ingest | 资料标题
## [YYYY-MM-DD HH:mm] query | 问题或归档标题
## [YYYY-MM-DD HH:mm] lint | light
## [YYYY-MM-DD HH:mm] lint | deep
```

每条记录按适用情况写明：

- 执行 Agent。
- 原始资料路径或查询主题。
- 处理结果。
- 新建页面。
- 更新页面。
- 发现的冲突。
- 错误与待人工处理事项。

不得把访问令牌、环境变量、私密会话内容或其他凭据写入日志。

## 12. Git 协作

执行写入工作流前：

- 检查当前分支和工作区状态。
- 不覆盖、不还原、不暂存来源不明的已有修改。
- 如果已有修改与计划更新的文件重叠，停止并请求用户决定。

执行成功后：

- 检查实际差异只包含本次任务范围。
- 验证 Markdown、链接、JSON 状态和索引一致性。
- Git 可用且用户没有禁止时，为本次完整工作流创建一个范围明确的本地提交。
- 只暂存本次任务修改的文件。
- 未经用户明确要求，不推送远程、不强制推送、不改写历史。

提交信息使用简洁、可检索的格式，例如：

```text
wiki: ingest <source-title>
wiki: archive <topic-title>
wiki: lint knowledge base
```

## 13. 必须人工确认的操作

以下操作不得全自动执行：

- 修改、移动或删除 `Clippings/` 内容。
- 删除 Wiki 页面。
- 大范围重命名或合并主题。
- 清除无法确认归属的写入锁。
- 覆盖与当前任务重叠的未提交修改。
- 在异常大规模变化后继续跨页面整合。
- 修改本 Schema 或 Agent 入口规则。
- 推送 Git 远程、强制推送或改写历史。
- 从互联网补充事实并直接当作用户已收藏资料。

网络搜索可以用于提出资料缺口和候选来源，但外部内容必须在获得用户同意并保存为可追溯来源后，才能进入长期知识。

## 14. 完成报告

每次自动维护后向用户简要报告：

- 扫描、处理、跳过和失败的资料数量。
- 新建与更新的页面。
- 发现的冲突和不确定性。
- Lint 结果。
- 是否创建 Git 提交。
- 需要用户处理的事项。

如果没有变化，明确报告“未发现待同步资料”，不要制造文件修改。
