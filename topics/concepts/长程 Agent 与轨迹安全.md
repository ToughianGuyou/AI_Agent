---
type: concept
status: growing
created: 2026-07-25
updated: 2026-07-27
sources:
  - "[[Safety and alignment in an era of long-horizon models]]"
  - "[[AI Control Roadmap]]"
  - "[[AgentRx]]"
  - "[[The Shift to Agentic AI - Evidence from Codex]]"
  - "[[深入理解 AI Agent]]"
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

### 致命三要素 + 持久记忆放大器

[[深入理解 AI Agent]] 第 5 章在 Simon Willison 的"致命三要素"基础上补充了第四个维度。致命三要素：访问私有数据 + 暴露于不受信任内容 + 具备外部通信能力 = 完整攻击闭环。李博杰补充**持久记忆**作为攻击放大器——攻击者可将恶意指令写入 Agent 长期记忆，跨会话潜伏，把一次性攻击升级为长期的潜伏与放大。

### Coding Agent 安全防御增量

针对 Coding Agent 特有的攻击面，防御体系分三层：(1) **上下文层**——外部内容来源标注、结构化角色隔离、输入清洗；(2) **执行层**——Sidecar 独立审查、Human in the loop、最小权限与权限分离；(3) **沙盒隔离层**——命令语义解析（Shell 命令组合爆炸使关键字黑名单形同虚设，必须在语义层理解命令真实效果）、沙盒隔离与网络出口控制（默认断网，按需白名单代理）、文件系统隔离（凭证类文件根本不可见）。

### Harness 安全兜底与模型演进

模型每稳定内化一种能力，对应的 Harness 安全层就可以删掉——但"吃"永远不会完结。安全 Harness 记录的是模型此刻还做不稳的地方：当下一个模型把这些约束内化，对应的代码可以删掉；但每一代模型打开新的能力前沿，前沿处恰恰是模型最做不稳的地方。Harness 不会消失，它只是随着模型向新的前沿迁移。

## 证据与来源
[[Safety and alignment in an era of long-horizon models]] 提供事故复盘；[[AI Control Roadmap]] 提供分层框架；[[AgentRx]] 提供过程诊断。

## 分歧与不确定性
监控器可能误报或被规避；过度保守会降低可用性，过度宽松会积累风险。

## 相关主题
[[Agent 自主性与人类监督]]、[[Agent 评测与失败诊断]]
