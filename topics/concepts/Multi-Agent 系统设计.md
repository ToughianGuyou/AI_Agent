---
type: concept
status: growing
created: 2026-07-25
updated: 2026-07-27
sources:
  - "[[Accelerating scientific discovery with Co-Scientist]]"
  - "[[CORPGEN]]"
  - "[[Kimi K2.5 - Visual Agentic Intelligence]]"
  - "[[深入理解 AI Agent]]"
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

### 2×3 分类框架

[[深入理解 AI Agent]] 第 10 章提出两个核心设计维度：

**维度一：上下文是否共享**
- 共享上下文：Agent 继承前序 Agent 的完整轨迹，信息零损耗但上下文快速膨胀，拓扑退化为角色切换序列
- 不共享上下文：每个 Agent 维护独立上下文，通过工具调用参数、共享文件系统或消息总线显式通信。通信机制对应操作系统 IPC 两大范式——共享文件系统是"共享内存"，消息总线是"消息传递"

**维度二：协作拓扑**（不共享上下文时的三种形态）
- **对等协作**（Peer）：2-3 个 Agent 平等交互、迭代改进
- **管理者模式**（Orchestration）：中心化 Manager 负责任务规划和调度
- **去中心化**（Decentralized）：无运行时中心控制者，Agent 之间直接沟通

### 多 Agent 何时真正优于单 Agent："新信息"判据

核心判据只有一条：**协作过程是否引入了单个 Agent 在生成时无法获得的新信息？** 同一模型自我审查通常无效甚至有害；不同 Agent 辩论同一段文本在等计算量下与单 Agent 持平；但 Reviewer 使用测试执行结果审查代码、查看渲染截图审查前端、使用外部工具验证事实——这些引入了真实外部反馈的协作模式效果显著提升。RLEF 和 WebGen-Agent 的实验证据支持这一判断。这解释了学术研究"单 Agent 就够了"与工程实践"多 Agent 更好"之间的矛盾：前者讨论的是多个 Agent 看同一段文本互相对论，后者包含外部反馈环路。

## 证据与来源
[[Accelerating scientific discovery with Co-Scientist]] 使用专门科学角色；[[CORPGEN]] 隔离并发任务；[[Kimi K2.5 - Visual Agentic Intelligence]] 追求并行降延迟。

## 分歧与不确定性
“更多 Agent 更好”不是普遍规律；应以任务可分解性、协调开销和错误放大为设计依据。

## 相关主题
[[Agent 记忆与经验学习]]、[[Agent 评测与失败诊断]]
