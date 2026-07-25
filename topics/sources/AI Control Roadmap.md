---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - https://deepmind.google/blog/securing-the-future-of-ai-agents/
tags: [ai-agent, safety, governance]
aliases: [Three Layers of Agent Security, Agent 安全三层框架]
---
# AI Control Roadmap / Three Layers of Agent Security

## 来源信息
- 机构：[[Google DeepMind]]
- 日期：2026-06-18
- 类型：官方技术报告、研究博客
- 原文：https://deepmind.google/blog/securing-the-future-of-ai-agents/

## 核心摘要
该路线图把未完全对齐的 Agent 当作可能的内部威胁，以单 Agent、多 Agent 网络和生态系统三层纵深防御组织控制措施。

## 关键论点与证据
- 使用类似 MITRE ATT&CK 的威胁模型，并用 coverage、recall、time-to-response 衡量防线。
- 将检测规避和风险响应划分为不同能力等级，强调防护与攻击能力共同升级。
- 官方称已经分析 100 万个编码 Agent 任务，为实时监控提供经验基础。
- 报告区分误解、过度热心和有意规避，避免把所有被拦截行为都解释为恶意。

## 涉及的概念与实体
[[长程 Agent 与轨迹安全]]、[[Multi-Agent 系统设计]]、[[Google DeepMind]]

## 与现有知识的关系
为 Agent 系统的控制面提供分层框架，补充单一模型对齐和单次权限审批。

## 待验证问题
这是路线图而非可复现实证基准；阈值、数据和内部监控细节没有完整公开。
