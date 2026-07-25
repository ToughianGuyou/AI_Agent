---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Clippings/AI Agent/2026/PDF/2026-06-05-meta-superintelligent-retrieval-agent.pdf]]"
tags: [ai-agent, retrieval, efficiency]
aliases: [SIRA]
---
# Superintelligent Retrieval Agent: The Next Frontier of Agentic Retrieval

## 来源信息
- 机构：[[Meta AI]]
- 日期：2026-06-05
- 类型：官方论文页
- 原文：https://ai.meta.com/research/publications/superintelligent-retrieval-agent-the-next-frontier-of-agentic-retrieval/

- 本地原文：[[Clippings/AI Agent/2026/PDF/2026-06-05-meta-superintelligent-retrieval-agent.pdf]]
- 抓取日期：2026-07-25
- SHA-256：`0bb669da3990ac30402f90bfce83bce74ab5551d7fea227da2ffc28abdb310e6`
- 实际下载直链：https://arxiv.org/pdf/2605.06647

## 核心摘要
SIRA 将检索“超级智能”定义为把多轮探索压缩成一次能区分目标证据与语料混淆项的检索动作，通过离线扩充文档词汇、在线预测证据词汇和语料统计过滤实现。

## 关键论点与证据
- BrowseComp-Wikipedia 包含 232 个难检索查询和 25,587,229 篇英文 Wikipedia 文档。
- 报告 Recall@1/10/100 分别为 9.70%、15.27% 和 36.14%。
- 在不同检索预算下优于多轮 Perplexity Agent，并降低成本、增加查询可解释性。

## 涉及的概念与实体
[[工具增强与环境交互]]、[[Agent 评测与失败诊断]]、[[Meta AI]]

## 与现有知识的关系
提出与“多轮才更 Agentic”不同的路线：把语料结构与判别性先验注入检索工具，以减少交互轮数。

## 待验证问题
绝对召回率仍低，评测只覆盖 Wikipedia 和 232 个查询；不是通用端到端研究 Agent。
