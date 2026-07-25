---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Clippings/AI Agent/2026/PDF/2026-05-19-google-deepmind-accelerating-scientific-discovery-with-co-scientist.pdf]]"
tags: [ai-agent, multi-agent, scientific-agent]
aliases: [Google Co-Scientist]
---
# Accelerating scientific discovery with Co-Scientist

## 来源信息
- 机构：[[Google DeepMind]]
- 日期：2026-05-19
- 类型：Nature 论文、官方研究页
- 论文：https://www.nature.com/articles/s41586-026-10644-y
- 官方页：https://deepmind.google/blog/co-scientist-a-multi-agent-ai-partner-to-accelerate-research/

- 本地原文：[[Clippings/AI Agent/2026/PDF/2026-05-19-google-deepmind-accelerating-scientific-discovery-with-co-scientist.pdf]]
- 抓取日期：2026-07-25
- SHA-256：`e603a77c9d2bdfb528313e4cf35405b72261e018a70da724fcebca94c96e4716`
- Nature PDF 端点：https://www.nature.com/articles/s41586-026-10644-y.pdf
- 实际获取的备用版本：https://arxiv.org/pdf/2502.18864；Nature PDF 端点返回 3,038-byte 非 PDF 响应，故保留完整公开 arXiv v2 工件；该研究 2025 年以预印本首次发布，并于 2026 年由 Nature 正式发表。

## 核心摘要
Co-Scientist 用 supervisor 异步调度生成、邻近性、反思、排名、进化与 meta-review 等专门 Agent，并连接科学数据库和结构工具以生成、竞争和修订研究假设。

## 关键论点与证据
- 在 15 个专家提出的开放科学目标上优于对照 Agentic 与推理模型。
- Evolution 组件把 GPQA precision 从 70.9 提高到 75.4，自动假设质量从 4.7 提高到 5.6。
- Meta-review 的正确性 AUC 在构造集上从 0.521 提高到 0.597，在 GPQA Diamond 上从 0.629 提高到 0.634。
- 研究还报告三个生物医学方向的端到端实验验证。

## 涉及的概念与实体
[[科学发现 Agent]]、[[Multi-Agent 系统设计]]、[[工具增强与环境交互]]、[[Google DeepMind]]

## 与现有知识的关系
展示专门角色、竞争式选择、工具链和专家复核如何共同构成科学研究 Agent。

## 待验证问题
部分质量由自动评测给出，湿实验验证数量有限；系统输出需要专家审查并可能产生生物安全风险。
