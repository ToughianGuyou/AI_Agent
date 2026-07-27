---
type: synthesis
status: growing
created: 2026-07-25
updated: 2026-07-27
sources:
  - "[[Measuring AI agent autonomy in practice]]"
  - "[[Teaching Claude why]]"
  - "[[Agentic coding and persistent returns to expertise]]"
  - "[[Using a GPT-5-driven autonomous lab to optimize protein synthesis]]"
  - "[[The Shift to Agentic AI - Evidence from Codex]]"
  - "[[Predicting model behavior before release by simulating deployment]]"
  - "[[Safety and alignment in an era of long-horizon models]]"
  - "[[SymptomAI]]"
  - "[[Accelerating scientific discovery with Co-Scientist]]"
  - "[[AI Control Roadmap]]"
  - "[[Unlocking dependable responses with Agentic RAG]]"
  - "[[AgentRx]]"
  - "[[CORPGEN]]"
  - "[[Superintelligent Retrieval Agent]]"
  - "[[Qwen-AgentWorld]]"
  - "[[Kimi K2.5 - Visual Agentic Intelligence]]"
  - "[[深入理解 AI Agent]]"
tags: [ai-agent, research-review, 2026]
aliases: [2026 AI Agent Research Review]
---
# 2026 年 AI Agent 研究综述

> 统计截止：2026-07-25。2026 年尚未结束，本页不是全年完整清单。

## 概述

本轮严格纳入 17 项材料：研究论文 16 篇 + 开源书籍 1 部。Anthropic 3、OpenAI 4、Google Research 2、Google DeepMind 2、Microsoft 2、Meta 1、Alibaba/Qwen 1、Moonshot 1、独立作者（李博杰/Pine AI）1。DeepSeek 在严格窗口内未检得以 Agent 方法、评测、技术报告或系统卡为核心的官方研究。

[[深入理解 AI Agent]]（李博杰 著，GitHub 21,917+ Stars，Apache 2.0 许可）是本轮唯一书籍来源，代表来自工业界一线的系统化视角。全书 10 章、92 个配套实验，围绕 Agent = LLM + 上下文 + 工具 展开，核心命题"实践在前、命名在后"对机构路线比较提供了独特的独立实践者视角。

## 机构路线比较

| 机构 | 本轮研究侧重 | 代表材料 | 证据特征 |
|---|---|---|---|
| [[Anthropic]] | 部署自主性、编码 Agent、人机监督、Agent 对齐训练 | [[Measuring AI agent autonomy in practice]]、[[Teaching Claude why]] | 大规模自有遥测和内部安全评测 |
| [[OpenAI]] | 长程工作、部署模拟、轨迹安全、闭环科学实验 | [[The Shift to Agentic AI - Evidence from Codex]]、[[Safety and alignment in an era of long-horizon models]] | 产品遥测、内部事故复盘和实验论文 |
| [[Google DeepMind]] | 科学 Multi-Agent、Agent 控制 | [[Accelerating scientific discovery with Co-Scientist]]、[[AI Control Roadmap]] | Nature、技术路线图 |
| [[Google Research]] | 医疗对话、企业检索 | [[SymptomAI]]、[[Unlocking dependable responses with Agentic RAG]] | 预印本、产品研究博客 |
| [[DeepSeek]] | 未检得严格合格条目 | — | 模型可用于 Agent 不等于 Agent 研究 |
| [[Microsoft Research]] | 长程企业任务、过程诊断与可审计性 | [[CORPGEN]]、[[AgentRx]] | 公开预印本和基准 |
| [[Meta AI]] | 单动作高判别检索 | [[Superintelligent Retrieval Agent]] | 官方论文页和专门检索基准 |
| [[Alibaba Qwen]] | 语言世界模型、环境模拟和 Agent RL | [[Qwen-AgentWorld]] | 大规模轨迹、预印本与开源代码 |
| [[Moonshot AI]] | 多模态 Agent 与动态并行编排 | [[Kimi K2.5 - Visual Agentic Intelligence]] | 模型技术报告 |
| [[李博杰]] / Pine AI | Agent 架构原则、Harness 工程、工业实践方法论 | [[深入理解 AI Agent]] | 开源书籍、自述实践经验 |

## 共同趋势

### 1. 研究尺度从答案转向轨迹

[[AgentRx]]、[[Predicting model behavior before release by simulating deployment]] 和 [[Safety and alignment in an era of long-horizon models]] 都表明，只看最终结果会漏掉关键过程错误。未来评测需要记录工具调用、状态变化、权限、成本和首次不可恢复错误。

### 2. 长程能力首先暴露系统工程问题

[[CORPGEN]] 的并发任务退化、OpenAI 的长程边界绕过和 Anthropic 的自主时长增长共同说明：上下文、记忆、优先级、停止条件和监控往往比单次推理分数更早成为瓶颈。

### 3. Multi-Agent 是拓扑选择，不是默认升级

[[Accelerating scientific discovery with Co-Scientist]] 和 [[Kimi K2.5 - Visual Agentic Intelligence]] 展示了专门角色与并行分解的价值，但协调、共享状态和裁判会引入额外成本。综合判断：只有可分解、可并行或需要独立审查的任务才优先考虑多 Agent。

### 4. 工具接口决定可靠性上限

自主实验室、Agentic RAG、SIRA 与 Qwen-AgentWorld 都把能力提升归因于环境或工具设计，而不是只增加模型推理。确定性数据接口、证据充分性检查、语料统计和可模拟环境成为关键。

### 5. 科学 Agent 快速发展但没有脱离人类闭环

[[Accelerating scientific discovery with Co-Scientist]]、[[Using a GPT-5-driven autonomous lab to optimize protein synthesis]] 和 [[SymptomAI]] 都保留专家、实验人员或临床评审。综合判断：目前最可信的模式是“Agent 扩展搜索和执行，人类负责目标、风险和证据确认”。

### 6. 安全从拒答扩展到控制系统

[[Teaching Claude why]] 关注训练侧泛化，[[AI Control Roadmap]] 关注纵深监控，OpenAI 长程案例关注中止与回滚。三者共同构成训练、运行时和治理层的安全栈。

### 7. 工业实践先于学术命名——独立实践者视角的确证

[[深入理解 AI Agent]] 从 Pine AI 的一线实践出发，系统论证了 Skill、Harness、Loop Engineering 等架构模式在头部公司正式命名之前就已在多个 Agent 产品中运行。这一观点与 Anthropic 的部署自主性测量、OpenAI 的 Codex 遥测分析在结论上一致——都表明 2025-2026 年 Agent 工程的核心突破发生在实践层而非理论层。该书的独特价值在于提供了一套经过生产验证的完整架构语言（Agent = LLM + 上下文 + 工具），将分散的研究发现编织为统一的工程框架。

## 证据强度

- 较强：同行评审论文、公开预印本加官方交叉说明、大样本人类或真实实验评测。
- 中等：公开方法和基准，但结论主要由作者自评。
- 较弱：官方内部部署或产品研究博客，数据和阈值无法完整复核。

不能把不同论文的准确率直接排序，因为任务、工具、模型、预算和 judge 不一致。

## 关键知识缺口

- 缺少跨厂商、同工具预算和同权限模型下的标准化比较。
- 缺少跨周或跨月的持久记忆、目标漂移和恢复评测。
- Multi-Agent 的总 token、墙钟时间、错误放大与组织收益缺少统一核算。
- 高风险环境中的人类监督负担、误报率和真实事故数据仍稀缺。
- 世界模型训练如何检测并限制模拟偏差尚未形成成熟方法。
- 中国主要模型厂商的官方 Agent 研究披露不均衡，不能用社区应用替代厂商研究归属。

## 分歧与不确定性

多数 2026 结果仍是预印本、官方技术报告或厂商内部数据。综合判断只代表截至统计日期的可核验公开证据；后续正式发表、撤稿、复现或新材料可能改变结论。

## 相关主题
[[AI Agent 学习地图]]、[[Agent 评测与失败诊断]]、[[长程 Agent 与轨迹安全]]
