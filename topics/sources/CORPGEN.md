---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - https://arxiv.org/abs/2602.14229
  - https://www.microsoft.com/en-us/research/blog/corpgen-advances-ai-agents-for-real-work/
tags: [ai-agent, long-horizon, memory]
aliases: [CORPGEN 多地平线企业 Agent]
---
# CORPGEN: Simulating Corporate Environments with Autonomous Digital Employees

## 来源信息
- 机构：[[Microsoft Research]]
- 日期：2026-02-15
- 类型：arXiv 预印本、官方研究页
- 论文：https://arxiv.org/abs/2602.14229
- 官方页：https://www.microsoft.com/en-us/research/blog/corpgen-advances-ai-agents-for-real-work/

## 核心摘要
CORPGEN 提出 Multi-Horizon Task Environments，让 Agent 在持续环境中同时管理数十个相互依赖的长任务，并用分层规划、隔离记忆和经验学习缓解负载退化。

## 关键论点与证据
- 环境包含 45 个以上任务和 500–1500 个以上步骤，持续数小时。
- 基线计算机 Agent 在负载从 25% 升到 100% 时完成率从 16.7% 降到 8.7%。
- CORPGEN 在最高负载上达到 15.2%，对比基线 4.3%，约为 3.5 倍。
- 消融显示经验学习贡献最大；作者区分工作记忆、结构化记忆和语义记忆。

## 涉及的概念与实体
[[Agent 记忆与经验学习]]、[[长程 Agent 与轨迹安全]]、[[Multi-Agent 系统设计]]、[[Microsoft Research]]

## 与现有知识的关系
把长程问题从“单个很长任务”扩展为“多个并发、依赖和持续重排优先级的任务组合”。

## 待验证问题
环境是合成企业场景，最高完成率仍低；尚未证明跨工作日记忆或真实团队协作效果。
