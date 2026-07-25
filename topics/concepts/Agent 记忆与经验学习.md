---
type: concept
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[CORPGEN]]"
  - "[[Qwen-AgentWorld]]"
  - "[[Unlocking dependable responses with Agentic RAG]]"
tags: [ai-agent, memory, learning]
aliases: [Agent memory]
---
# Agent 记忆与经验学习

## 概述
Agent 记忆用于在任务步骤、并发任务或多次会话之间保存事实、进度、策略和失败经验。

## 核心内容
- 工作记忆支持当前步骤，结构化记忆保存任务状态，语义或经验记忆支持跨任务复用。
- 隔离不同任务的记忆可减少串扰；摘要和检索控制上下文增长。
- 环境轨迹可用来学习策略或训练世界模型，但错误经验也可能被固化。

## 证据与来源
[[CORPGEN]] 展示多层记忆和任务隔离；[[Qwen-AgentWorld]] 用大规模轨迹训练环境模型。

## 分歧与不确定性
更多存储不等于更好记忆；关键问题是形成、筛选、更新、冲突消解和遗忘。

## 相关主题
[[长程 Agent 与轨迹安全]]、[[工具增强与环境交互]]
