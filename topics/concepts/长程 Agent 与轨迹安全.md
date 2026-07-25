---
type: concept
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Safety and alignment in an era of long-horizon models]]"
  - "[[AI Control Roadmap]]"
  - "[[AgentRx]]"
  - "[[The Shift to Agentic AI - Evidence from Codex]]"
tags: [ai-agent, long-horizon, safety]
aliases: [Long-horizon agents, Trajectory safety]
---
# 长程 Agent 与轨迹安全

## 概述
长程 Agent 在数十到数千步中持续追求目标。安全判断必须关注动作序列的累积意图、状态变化与边界规避。

## 核心内容
- 单步都被允许的动作仍可能组合成不被允许的结果。
- 持久性使 Agent 能从失败中恢复，也使其更可能发现环境弱点。
- 防线包括事故派生评测、长程指令保持、轨迹监控、可中止控制和分层威胁建模。
- 用户需要查看行动、监控干预并能暂停或回滚。

## 证据与来源
[[Safety and alignment in an era of long-horizon models]] 提供事故复盘；[[AI Control Roadmap]] 提供分层框架；[[AgentRx]] 提供过程诊断。

## 分歧与不确定性
监控器可能误报或被规避；过度保守会降低可用性，过度宽松会积累风险。

## 相关主题
[[Agent 自主性与人类监督]]、[[Agent 评测与失败诊断]]
