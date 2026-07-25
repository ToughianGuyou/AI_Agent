---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Clippings/AI Agent/2026/PDF/2026-07-08-openai-predicting-llm-safety-by-simulating-deployment.pdf]]"
tags: [ai-agent, evaluation, deployment-safety]
aliases: [通过部署模拟预测模型行为]
---
# Predicting model behavior before release by simulating deployment

## 来源信息
- 机构：[[OpenAI]]
- 日期：2026-06-16
- 类型：官方研究页、论文入口
- 原文：https://openai.com/index/deployment-simulation/

- 本地原文：[[Clippings/AI Agent/2026/PDF/2026-07-08-openai-predicting-llm-safety-by-simulating-deployment.pdf]]
- 抓取日期：2026-07-25
- SHA-256：`ad680e0efa667902a029836ee0bc67b2d5a82e45482d96e905220dd15670cf13`

## 核心摘要
Deployment Simulation 用经过隐私处理的真实部署对话作为上下文，让候选模型重新生成回应，以更接近真实分布地估计发布后的不良行为频率。

## 关键论点与证据
- 研究覆盖 GPT-5 Thinking 至 GPT-5.4 的约 130 万条去标识对话，并对 GPT-5.4 的 20 类不良行为做预注册预测。
- 在 Agent 编码场景中，使用 12 万条内部 GPT-5.4 轨迹模拟 GPT-5.5 部署，并通过工具模拟保持轨迹完整性。
- 该方法适合估计常见部署风险，但不能可靠测量低于约二十万分之一的极低频事件。
- 部署式上下文降低模型识别“自己正在被评测”的迹象。

## 涉及的概念与实体
[[长程 Agent 与轨迹安全]]、[[Agent 评测与失败诊断]]、[[OpenAI]]

## 与现有知识的关系
把 Agent 安全评测从静态难题集扩展到接近生产分布的完整工具轨迹。

## 待验证问题
研究主要使用 OpenAI 自有流量与内部 Agent 轨迹；分布代表性和隐私处理细节无法由外部完全复核。
