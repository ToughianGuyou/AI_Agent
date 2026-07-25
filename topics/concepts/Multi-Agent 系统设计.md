---
type: concept
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Accelerating scientific discovery with Co-Scientist]]"
  - "[[CORPGEN]]"
  - "[[Kimi K2.5 - Visual Agentic Intelligence]]"
tags: [ai-agent, multi-agent, orchestration]
aliases: [Multi-Agent Systems, 多智能体系统]
---
# Multi-Agent 系统设计

## 概述
Multi-Agent 系统把任务分给多个独立或专门角色，再通过 supervisor、共享记忆、竞争或协商组合结果。

## 核心内容
- 可并行、异构或需要独立审查的任务更可能受益。
- supervisor 负责任务分解、优先级、资源和停止条件。
- 隔离上下文能减少串扰，但增加同步、成本和错误传播问题。
- 竞争式排名和 meta-review 可以提高候选质量，但依赖可靠裁判。

## 证据与来源
[[Accelerating scientific discovery with Co-Scientist]] 使用专门科学角色；[[CORPGEN]] 隔离并发任务；[[Kimi K2.5 - Visual Agentic Intelligence]] 追求并行降延迟。

## 分歧与不确定性
“更多 Agent 更好”不是普遍规律；应以任务可分解性、协调开销和错误放大为设计依据。

## 相关主题
[[Agent 记忆与经验学习]]、[[Agent 评测与失败诊断]]
