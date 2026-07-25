---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Clippings/AI Agent/2026/PDF/2026-02-02-microsoft-agentrx-diagnosing-ai-agent-failures.pdf]]"
tags: [ai-agent, evaluation, debugging]
aliases: [AgentRx 轨迹失败诊断]
---
# AgentRx: Diagnosing AI Agent Failures from Execution Trajectories

## 来源信息
- 机构：[[Microsoft Research]]
- 日期：2026-02-02
- 类型：arXiv 预印本、官方研究页
- 论文：https://arxiv.org/abs/2602.02475
- 官方页：https://www.microsoft.com/en-us/research/blog/systematic-debugging-for-ai-agents-introducing-the-agentrx-framework/

- 本地原文：[[Clippings/AI Agent/2026/PDF/2026-02-02-microsoft-agentrx-diagnosing-ai-agent-failures.pdf]]
- 抓取日期：2026-07-25
- SHA-256：`59680fd631934d6ad3046108a504195e8cd70066bdefbfb3561b7731f7d22923`

## 核心摘要
AgentRx 从工具 schema 与领域政策合成可执行约束，逐步检查失败轨迹，再用有证据的违规日志定位第一个不可恢复错误及其根因类别。

## 关键论点与证据
- 发布 115 条人工标注失败轨迹，覆盖结构化 API、事故管理以及开放式网页/文件任务。
- 建立九类跨领域失败分类法。
- 官方报告相对基线，失败步骤定位准确率绝对提高 23.6%，根因归因提高 22.9%。

## 涉及的概念与实体
[[Agent 评测与失败诊断]]、[[长程 Agent 与轨迹安全]]、[[Microsoft Research]]

## 与现有知识的关系
把“任务是否完成”的结果分数扩展为可审计的过程诊断，适合定位长程随机轨迹中的首次关键错误。

## 待验证问题
基准规模有限，约束合成和 LLM judge 都可能产生误判；需要更多生产轨迹验证跨域泛化。
