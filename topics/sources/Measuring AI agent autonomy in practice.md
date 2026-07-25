---
type: source
status: growing
created: 2026-07-25
updated: 2026-07-25
sources:
  - "[[Clippings/AI Agent/2026/Web/2026-02-18-anthropic-measuring-ai-agent-autonomy-in-practice]]"
  - "[[Clippings/AI Agent/2026/PDF/2026-02-18-anthropic-measuring-ai-agent-autonomy-appendix.pdf]]"
tags: [ai-agent, autonomy, safety]
aliases: [AI Agent 实际自主性测量]
---
# Measuring AI agent autonomy in practice

## 来源信息
- 机构：[[Anthropic]]
- 日期：2026-02-18
- 类型：官方研究博客、真实部署测量
- 原文：https://www.anthropic.com/research/measuring-agent-autonomy

- 正文快照：[[Clippings/AI Agent/2026/Web/2026-02-18-anthropic-measuring-ai-agent-autonomy-in-practice]]
- 抓取日期：2026-07-25
- SHA-256：`83ad680a8da0d9991d6739935c99026d7848da8e43a265aefea936c37e30c932`
- 官方附录：[[Clippings/AI Agent/2026/PDF/2026-02-18-anthropic-measuring-ai-agent-autonomy-appendix.pdf]]
- 抓取日期：2026-07-25
- SHA-256：`ee9d828c56322a5017f9adfa54be532ca9624edd2fb361a317b768cef14439e6`
- 官方附录直链：https://cdn.sanity.io/files/4zrzovbb/website/55e4d2de6eb39b3a9259c3f74843f86b1a12e265.pdf

## 核心摘要
Anthropic 用隐私保护方法分析 Claude Code 与公共 API 的数百万次人机交互，提出以工具调用和连续无人工介入时长来操作化测量 Agent 自主性。

## 关键论点与证据
- 最长一组 Claude Code 会话的连续自主工作时间在三个月内从不足 25 分钟增至超过 45 分钟。
- 新用户约 20% 的会话使用全自动批准，经验增加后超过 40%。
- 最复杂任务中，Claude 主动请求澄清的频率超过人类中断的两倍。
- 软件工程约占公共 API Agent 活动的一半，多数被测行动仍低风险且可逆。

## 涉及的概念与实体
[[Agent 自主性与人类监督]]、[[长程 Agent 与轨迹安全]]、[[Anthropic]]

## 与现有知识的关系
为“自主性不是单一模型能力，而是模型、权限、工具和用户行为共同形成的部署属性”提供生产数据。

## 待验证问题
风险和自主程度部分依赖模型分类器；数据集中编程任务占比高，不能直接外推到所有领域或其他厂商。
