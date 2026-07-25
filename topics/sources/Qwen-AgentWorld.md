---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Clippings/AI Agent/2026/PDF/2026-06-23-alibaba-qwen-agentworld-language-world-models.pdf]]"
tags: [ai-agent, world-model, simulation]
aliases: [Qwen AgentWorld]
---
# Qwen-AgentWorld: Language World Models for General Agents

## 来源信息
- 机构：[[Alibaba Qwen]]
- 日期：2026-06-23
- 类型：arXiv 预印本、开源项目
- 论文：https://arxiv.org/abs/2606.24597
- 代码：https://github.com/QwenLM/Qwen-AgentWorld

- 本地原文：[[Clippings/AI Agent/2026/PDF/2026-06-23-alibaba-qwen-agentworld-language-world-models.pdf]]
- 抓取日期：2026-07-25
- SHA-256：`1acc32b7ef306f7c86b2b7c724432ed18f6c62ef400eeff4601059d4cc2fd6fe`
- 官方落地页：https://qwen.ai/blog?id=qwen-agentworld
- 实际下载直链：https://arxiv.org/pdf/2606.24597

## 核心摘要
Qwen-AgentWorld 训练语言世界模型预测 Agent 环境中的下一状态，把环境模拟同时用于大规模 Agent RL 和通用 Agent 模型预训练。

## 关键论点与证据
- 发布 35B-A3B 与 397B-A17B 两种模型，训练使用超过 1,000 万条、覆盖 7 个领域的真实环境交互轨迹。
- AgentWorldBench 来自 5 个前沿模型在 9 个既有基准上的真实交互。
- 世界模型可并行模拟数千个环境；报告称结合模拟训练优于只在真实环境训练，并改善 7 个下游 Agent 基准。

## 涉及的概念与实体
[[工具增强与环境交互]]、[[Agent 记忆与经验学习]]、[[Alibaba Qwen]]

## 与现有知识的关系
把世界模型从机器人状态预测扩展到语言描述的网页、软件和工具环境，为可控训练数据生成提供路线。

## 待验证问题
预印本摘要未给出统一绝对提升；模拟误差、训练语料覆盖与厂商自评需要独立复现。
