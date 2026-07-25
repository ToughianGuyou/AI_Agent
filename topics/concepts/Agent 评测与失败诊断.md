---
type: concept
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[AgentRx]]"
  - "[[Predicting model behavior before release by simulating deployment]]"
  - "[[CORPGEN]]"
tags: [ai-agent, evaluation, reliability]
aliases: [Agent evaluation]
---
# Agent 评测与失败诊断

## 概述
Agent 评测必须覆盖结果、过程、成本、时间、权限和完整轨迹，不能只用最终答案准确率。

## 核心内容
- 失败诊断应定位第一个不可恢复错误，而不是只解释最后一步。
- 部署模拟可减少静态评测的选择偏差和测试识别。
- 长程与并发环境会暴露上下文饱和、记忆串扰、依赖和重排开销。
- 评测应区分真实环境、模拟环境、内部流量和厂商自评。

## 证据与来源
[[AgentRx]] 提供轨迹诊断；[[Predicting model behavior before release by simulating deployment]] 连接评测与部署分布；[[CORPGEN]] 测量多任务负载退化。

## 分歧与不确定性
LLM judge、合成任务和厂商私有数据都可能形成系统性偏差。

## 相关主题
[[长程 Agent 与轨迹安全]]、[[Agent 自主性与人类监督]]
