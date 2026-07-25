---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Clippings/llm-wiki]]"
tags:
  - knowledge-base
  - llm-agent
aliases:
  - LLM Wiki
---

# llm-wiki

## 来源信息

- 原始资料：[[Clippings/llm-wiki]]
- 原始网页：https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- 类型：个人知识库方法说明

## 核心摘要

该资料提出一种由 LLM Agent 持续维护个人 Wiki 的模式：原始资料保持不可变，Agent 在其上方维护结构化、互相链接且可持续修订的 Markdown 知识层。与查询时临时检索片段的传统 RAG 不同，这种方式把已经完成的总结、交叉引用、冲突标记和综合判断保存为长期资产。

## 关键论点

- 知识库分为原始资料、Wiki 和工作协议三层。
- Ingest 不只是索引，而是读取、提炼并将新证据整合进已有页面。
- Query 的高价值综合结果也应归档，避免只存在于聊天记录。
- Lint 用来发现冲突、过时主张、孤立页面、缺少交叉链接和证据缺口。
- 内容索引与追加式日志分别承担导航和审计职责。

## 证据与来源

- 本页的事实性摘要和论点均以 [[Clippings/llm-wiki]] 为依据。
- “原始网页”链接来自该资料的 Frontmatter；本次未对该链接所指向的外部页面进行独立核验。
- 本页不引入其他外部来源；关于本 Vault 与该模式的对应关系，限于对本仓库 `VAULT_SCHEMA.md` 的说明。

## 涉及的概念与实体

- 增量知识编译
- 持久化 Wiki
- 来源可追溯性
- Ingest、Query 与 Lint 工作流
- Obsidian
- LLM Agent

## 与现有知识的关系

本 Vault 的 `VAULT_SCHEMA.md` 将该模式具体化为三层目录、Frontmatter、来源状态、写入锁、增量 Ingest、归档型 Query 和 Lint 协议。本页记录原始思想，不替代 Schema 的规范性要求。

## 待验证问题

- 在来源和页面规模显著增长后，纯索引导航何时需要升级为全文或向量检索。
- 多 Agent 并发维护时，文件锁与 Git 协作是否足以避免语义冲突。
- 自动综合内容的长期质量如何通过抽样复核和来源级证据约束来衡量。
