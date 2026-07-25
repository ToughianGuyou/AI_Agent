---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Clippings/AI Agent/2026/PDF/2026-02-02-moonshot-kimi-k2-5-visual-agentic-intelligence.pdf]]"
tags: [ai-agent, multimodal, multi-agent]
aliases: [Kimi K2.5]
---
# Kimi K2.5: Visual Agentic Intelligence

## 来源信息
- 机构：[[Moonshot AI]]
- 日期：2026-02-02
- 类型：arXiv 技术报告
- 论文：https://arxiv.org/abs/2602.02276

- 本地原文：[[Clippings/AI Agent/2026/PDF/2026-02-02-moonshot-kimi-k2-5-visual-agentic-intelligence.pdf]]
- 抓取日期：2026-07-25
- SHA-256：`06811e2d0e7a68cfc4e6b081963f4efcc84f5c05a376ed62b05440978db264e9`

## 核心摘要
Kimi K2.5 把文本与视觉联合训练、强化学习和 Agent Swarm 结合，由 orchestrator 动态拆解异构任务并并行调度子 Agent。

## 关键论点与证据
- Agent Swarm 覆盖编程、视觉、推理和 Agent 任务。
- 官方报告相对单 Agent 最多降低 4.5 倍延迟。
- 设计强调异构子任务的动态分解，而非固定数量或固定角色的多 Agent 流程。

## 涉及的概念与实体
[[Multi-Agent 系统设计]]、[[工具增强与环境交互]]、[[Moonshot AI]]

## 与现有知识的关系
代表“并行编排降低墙钟时间”的系统路线，与仅追求准确率的 Multi-Agent 研究形成互补。

## 待验证问题
技术报告缺少统一成本与逐基准绝对成绩；并行可能减少延迟但增加总 token 和算力，需要独立复现。
