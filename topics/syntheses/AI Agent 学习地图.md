---
type: synthesis
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Measuring AI agent autonomy in practice]]"
  - "[[AgentRx]]"
  - "[[CORPGEN]]"
  - "[[Accelerating scientific discovery with Co-Scientist]]"
  - "[[Safety and alignment in an era of long-horizon models]]"
tags: [ai-agent, learning-path]
aliases: [AI Agent Knowledge Map, AI Agent 学习路线]
---
# AI Agent 学习地图

## 概述
本页给出从 Agent 基本闭环到长程安全的推荐学习顺序。材料统计截止 2026-07-25，重点是理解方法和证据，不是追逐产品清单。

## 1. 基础：Agent 是什么

先掌握“模型根据目标自行组织过程，并通过工具观察与改变环境”的闭环：

`目标 → 规划 → 工具行动 → 环境反馈 → 更新状态 → 继续或停止`

阅读：
- [[Agent 自主性与人类监督]]：自主性不是开关，而是权限、时间和监督结构。
- [[工具增强与环境交互]]：工具 schema、环境状态和确定性接口决定可行动范围。
- [[Measuring AI agent autonomy in practice]]：用真实部署数据建立直觉。

## 2. 单 Agent：工具、检索与环境

目标是理解为什么 Agent 不等于“给 LLM 多写几轮提示”：

- [[Unlocking dependable responses with Agentic RAG]]：任务分解、多跳检索与证据充分性。
- [[Superintelligent Retrieval Agent]]：用语料先验减少多轮探索。
- [[Qwen-AgentWorld]]：用语言世界模型模拟环境。
- [[Using a GPT-5-driven autonomous lab to optimize protein synthesis]]：把行动闭环扩展到物理实验。

学习检查点：能否区分模型能力、Agent harness、工具能力和环境可观测性。

## 3. 记忆与长程任务

- [[Agent 记忆与经验学习]]：工作、结构化、语义和经验记忆的不同职责。
- [[CORPGEN]]：并发任务如何引发上下文饱和、记忆串扰、依赖和重排开销。
- [[Agentic coding and persistent returns to expertise]]：真实用户如何把更复杂的执行交给 Agent。
- [[The Shift to Agentic AI - Evidence from Codex]]：长任务与并行 Agent 的使用趋势。

学习检查点：能否说明“长上下文”“持久记忆”和“长期学习”并不是同一件事。

## 4. Multi-Agent

- [[Multi-Agent 系统设计]]：角色、拓扑、协调与错误传播。
- [[Accelerating scientific discovery with Co-Scientist]]：生成、反思、排名和 meta-review 的专门角色。
- [[Kimi K2.5 - Visual Agentic Intelligence]]：动态并行分解以降低延迟。

学习检查点：只在任务可分解、并行收益大于协调成本时增加 Agent，并明确 supervisor、共享状态与停止条件。

## 5. 评测与可靠性

- [[Agent 评测与失败诊断]]：从结果分数转向过程、成本与轨迹。
- [[AgentRx]]：定位第一个不可恢复错误。
- [[Predicting model behavior before release by simulating deployment]]：用接近真实流量的上下文做发布前评测。
- [[SymptomAI]]：学习大样本真实用户与专家盲评的设计。

学习检查点：看到 Agent 结果时，先问任务分布、工具、预算、评判器、失败定义和可复现性。

## 6. 安全与治理

- [[长程 Agent 与轨迹安全]]：单步允许不代表整体轨迹允许。
- [[Safety and alignment in an era of long-horizon models]]：长程模型绕过环境边界的事故复盘。
- [[AI Control Roadmap]]：单 Agent、Agent 网络和生态三层纵深防御。
- [[Teaching Claude why]]：训练数据为什么需要价值理由与工具语境。

学习检查点：安全设计同时覆盖训练、权限、监控、用户控制、暂停与回滚。

## 7. 应用专题：科学发现

- [[科学发现 Agent]]
- [[Accelerating scientific discovery with Co-Scientist]]
- [[Using a GPT-5-driven autonomous lab to optimize protein synthesis]]
- [[SymptomAI]]

重点不是“Agent 已经取代科学家”，而是确定哪些环节可机器化、哪些证据必须由专家和真实实验确认。

## 推荐实践

1. 先实现单 Agent、少量工具和清晰停止条件。
2. 记录完整轨迹与工具结果，再谈自动评测。
3. 用失败轨迹修正 harness、权限和评测，不只修改提示词。
4. 只有在任务可并行或需要独立审查时引入 Multi-Agent。
5. 高风险领域保留人类复核、可中止执行和可追溯证据。

## 分歧与不确定性

2026 年多数证据仍来自厂商预印本、内部遥测和自有系统。性能数字高度依赖任务、工具、预算和评判器，跨论文横向排名通常不可靠。

## 相关主题
[[2026 年 AI Agent 研究综述]]
