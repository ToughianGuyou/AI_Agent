---
type: concept
status: growing
created: 2026-07-25
updated: 2026-07-27
sources:
  - "[[Measuring AI agent autonomy in practice]]"
  - "[[Safety and alignment in an era of long-horizon models]]"
  - "[[深入理解 AI Agent]]"
tags: [ai-agent, autonomy, oversight]
aliases: [Agent autonomy]
---
# Agent 自主性与人类监督

## 概述
Agent 自主性是系统在多长时间、多少步骤和多大权限范围内无需人工介入地追求目标；它由模型、harness、工具、环境和用户行为共同决定。

## 核心内容
- 监督不仅是每步批准，还包括 Agent 主动澄清、人类中断、权限分级和轨迹监控。
- 用户经验增加可能带来更少逐步审批、更多异常时干预。
- 更强的持久性会扩大能力，也会增加发现并利用环境漏洞的机会。

### Harness 工程与"模型会吃掉 Harness"的演进观

[[深入理解 AI Agent]] 为自主性设计提供了工程层面的系统论述。模型是 Agent 的大脑，Harness 是把模型能力引导成可靠任务执行的工程外壳——包括上下文管理、工具接口、安全约束、验证与纠正等基础设施。模型越强大，Harness 越关键：模型自主决策的空间越大，出错时的影响面也越大。

模型与 Harness 的关系遵循"方向认同，节奏务实"八字原则：方向上，模型会持续吃掉 Harness——工具调用、长程规划都曾靠外部编排，如今已是模型原生能力；节奏上，这个"吃"远比直觉慢——训练以月计，模型也无法一次内化真实业务中所有的约束与偏好。模型此刻的能力边界，就是 Harness 此刻的价值所在。Harness 不会消失，它只是随着模型不断向新的能力前沿迁移。

Agent 的能力更新沿三条互补路径：**任务内的上下文适应**（当前任务中临时调整）、**跨任务的外部产物更新**（知识文档、Prompt/Skill、程序/Harness）、**训练周期中的参数更新**（模型后训练）。三者不是互斥分类，而是不同时间尺度上的协同机制。

## 证据与来源
[[Measuring AI agent autonomy in practice]] 提供部署测量；[[Safety and alignment in an era of long-horizon models]] 提供长程事故案例。

## 分歧与不确定性
运行时长不等于自主决策质量；更多自动批准既可能表示信任，也可能表示监督疲劳。

## 相关主题
[[长程 Agent 与轨迹安全]]、[[Agent 评测与失败诊断]]
