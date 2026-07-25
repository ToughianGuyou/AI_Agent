# 2026 AI Agent 来源审计

统计窗口：2026-01-01 至 2026-07-25
核验原则：优先论文原文、正式出版页和机构官方研究页面；搜索结果与二手报道不作为长期证据。

## 纳入清单

| 机构 | 材料 | 日期 | 类型 | 主题 | 核验 |
|---|---|---:|---|---|---|
| Anthropic | Measuring AI agent autonomy in practice | 2026-02-18 | 官方研究博客/部署测量 | 自主性、监督、工具使用 | 官方单源 |
| Anthropic | Teaching Claude why | 2026-05-08 | 官方对齐研究博客 | Agent 错位、训练、安全评测 | 官方单源 |
| Anthropic | Agentic coding and persistent returns to expertise | 2026-06-16 | 官方经济研究报告 | 编码 Agent、人机协作、采用 | 官方报告 |
| OpenAI + Ginkgo | Using a GPT-5-driven autonomous lab to optimize the cost and titer of cell-free protein synthesis | 2026-02-05 | 论文/官方研究页 | 自主实验室、闭环科学发现 | 论文 + 官方页 |
| OpenAI | The Shift to Agentic AI: Evidence from Codex | 2026-06-25 | arXiv/官方经济研究 | 长程工作、并行 Agent、采用 | arXiv + 官方页 |
| OpenAI | Predicting model behavior before release by simulating deployment | 2026-06-16 | 论文/官方研究页 | 部署模拟、Agent 安全评测 | 论文入口 + 官方页 |
| OpenAI | Safety and alignment in an era of long-horizon models | 2026-07-20 | 官方安全研究博客 | 长程安全、轨迹监控 | 官方单源 |
| Google | SymptomAI: Toward a Conversational AI Agent for Everyday Symptom Assessment | 2026-05-05 | arXiv/官方研究索引 | 对话 Agent、医疗、人类评测 | arXiv + 官方索引 |
| Google DeepMind | Accelerating scientific discovery with Co-Scientist | 2026-05-19 | Nature/官方研究页 | Multi-Agent、科学发现、工具使用 | Nature + 官方页 |
| Google DeepMind | AI Control Roadmap / Three Layers of Agent Security | 2026-06-18 | 官方技术报告 | Agent 安全、监控、治理 | 官方报告 |
| Google Research + Google Cloud | Unlocking dependable responses with Agentic RAG | 2026-06-05 | 官方产品研究博客 | Agentic RAG、多跳检索 | 官方单源 |
| Microsoft Research | AgentRx: Diagnosing AI Agent Failures from Execution Trajectories | 2026-02-02 | arXiv/官方研究页 | 失败诊断、轨迹评测 | arXiv + 官方页 |
| Microsoft | CORPGEN: Simulating Corporate Environments with Autonomous Digital Employees in Multi-Horizon Task Environments | 2026-02-15 | arXiv/官方研究页 | 长程任务、记忆、规划 | arXiv + 官方页 |
| Meta AI | Superintelligent Retrieval Agent: The Next Frontier of Agentic Retrieval | 2026-06-05 | 论文/官方研究页 | 检索 Agent、效率、可解释性 | 官方论文页 |
| Alibaba/Qwen | Qwen-AgentWorld: Language World Models for General Agents | 2026-06-23 | arXiv/开源项目 | 世界模型、环境模拟、Agent RL | arXiv + 官方代码 |
| Moonshot AI | Kimi K2.5: Visual Agentic Intelligence | 2026-02-02 | arXiv 技术报告 | 多模态、并行 Multi-Agent | arXiv |

## 本地原始材料落地

- Manifest：`system/research/2026-ai-agent-material-manifest.json`。
- 落地规则：优先保存公开可访问的论文、技术报告或出版方 PDF；没有完整独立 PDF 的条目保存官方网页 Markdown 快照。第 1 条的 PDF 是附录而非正文，作为网页快照的补充材料；第 10 条保留两份配套官方 PDF。
- 最终状态：16/16 条目、18/18 工件均为 `complete`；其中 PDF 14 份、网页快照 4 份、失败 0、冲突 0。逐项落地路径、SHA-256、抓取时间与外部直链见 `system/research/2026-ai-agent-material-manifest.json`。
- 无获取失败或待处理工件；若未来获取失败，保留外部链接，并在 manifest 的 `error` 中记录原因；不得将未成功获取的材料表述为本地原文。

## 关键排除与边界判断

| 机构 | 材料 | 日期 | 来源类型 | 原始链接 | Agent 相关性 | 决定 | 理由 |
|---|---|---:|---|---|---|---|---|
| DeepSeek | DeepSeek-V4 技术报告/模型卡 | 2026-04-24 | 模型卡/技术报告 | https://www.deepseek.com/en/transparency/ | 模型具备可被 Agent 框架调用的通用能力，但未核验到 Agent 方法、系统或专门评测贡献。 | 排除 | “可用于 Agent”不等于厂商发布 Agent 研究。 |
| DeepSeek | awesome-deepseek-agent | 2026-06-12（仓库更新） | 社区集成清单 | https://github.com/deepseek-ai/awesome-deepseek-agent | 汇总使用 DeepSeek API 的第三方 Agent 集成。 | 排除 | 不是 DeepSeek 的 Agent 方法、评测、技术报告或系统卡。 |
| Google | Towards a Science of Scaling Agent Systems | 2025-12-09（arXiv 首发）；2026-01-28（官方博客） | arXiv 预印本/官方研究博客 | https://arxiv.org/abs/2512.08296 | 研究单 Agent 与多种 Multi-Agent 拓扑的协调收益、开销和错误放大。 | 排除主清单 | 研究工件首次公开于 2025，超出严格窗口；保留为延伸阅读。 |
| Google | ReasoningBank | 2025-09-29（arXiv 首发）；2026（ICLR） | arXiv 预印本/会议论文 | https://arxiv.org/abs/2509.25140 | 从成功和失败轨迹提炼策略记忆，使 Agent 在部署后学习。 | 排除主清单 | 虽于 ICLR 2026 正式发表，但研究工件首次公开于 2025；本轮采用严格首次公开口径。 |
| Anthropic | Trustworthy agents in practice | 2026-04-09 | 官方治理研究博客 | https://www.anthropic.com/research/trustworthy-agents | 定义 Agent 的模型、harness、工具和环境边界，并讨论权限、提示注入和人类控制。 | 延伸阅读 | 高价值治理框架，但缺少独立实验或统一基准。 |
| Anthropic | Project Deal | 2026-04-24 | 官方真实世界实验博客 | https://www.anthropic.com/features/project-deal | 由 Agent 代表买卖双方进行真实物品协商和交易。 | 延伸阅读 | 样本小、内部员工自选且有补贴，外部效度有限。 |
| Anthropic | Coding agents in the social sciences | 2026-05-27 | 官方经济研究/调查 | https://www.anthropic.com/research/coding-agents-social-sciences | 调查科研人员采用编码 Agent 的用途、差异和产出关联。 | 延伸阅读 | 有 1,260 人调查，但重点是采用与社会差异，不是 Agent 方法或能力。 |
| OpenAI | Inside OpenAI's in-house data agent | 2026-01-29 | 官方工程博客 | https://openai.com/index/inside-our-in-house-data-agent/ | 描述内部数据 Agent 的上下文、记忆和工具架构。 | 延伸阅读 | 工程实践有价值，但无可复现实验、对照或系统量化。 |
| OpenAI | Operator System Card | 2025-01 | 系统卡 | https://cdn.openai.com/operator_system_card.pdf | 计算机使用 Agent 的能力和安全评测。 | 排除 | 发布于 2025，超出窗口。 |
| Anthropic | Bloom | 2025-12-19 | 技术报告/官方研究博客 | https://www.anthropic.com/research/bloom | 用多个 Agent 自动生成、执行和评判行为评测。 | 排除 | 发布于 2025，超出窗口。 |
| ByteDance | 本轮未形成单项候选 | 2026-07-25（检索截止） | 官方研究索引检索 | https://seed.bytedance.com/en/research | 检索 Agent 方法、工具使用、长程任务、Multi-Agent、评测与安全。 | 未检得 | 截至检索日期，未找到同时满足窗口、官方可核和 Agent 实证贡献的强候选。 |
| xAI | 本轮未形成单项候选 | 2026-07-25（检索截止） | 官方组织与论文索引检索 | https://github.com/xai-org | 检索 Agent 方法、工具使用、长程任务、Multi-Agent、评测与安全。 | 未检得 | 截至检索日期，未找到同时满足窗口、官方可核和 Agent 实证贡献的强候选。 |

## 证据强度说明

- “论文/官方页”表示方法和结果至少能由论文正文或出版元数据与机构页面交叉确认。
- “官方单源”适合记录厂商部署经验、治理框架或内部评测，但不能视为独立复现。
- 产品遥测中的 token、预计人类耗时、分类器标签和内部成功率都是代理指标，不能直接等同于因果生产率。
- 医疗、生命科学和自主实验室研究的结果只适用于报告的任务、工具链与人类监督条件。
- 预印本均未必经过同行评审；技术报告中的厂商自评结果需要外部复现。

## 原始链接

### Anthropic

- https://www.anthropic.com/research/measuring-agent-autonomy
- https://www.anthropic.com/research/teaching-claude-why
- https://www.anthropic.com/research/claude-code-expertise

### OpenAI

- https://openai.com/index/gpt-5-lowers-protein-synthesis-cost/
- https://arxiv.org/abs/2606.26959
- https://openai.com/index/how-agents-are-transforming-work/
- https://openai.com/index/deployment-simulation/
- https://openai.com/index/safety-alignment-long-horizon-models/

### Google 与 Google DeepMind

- https://arxiv.org/abs/2605.04012
- https://www.nature.com/articles/s41586-026-10644-y
- https://deepmind.google/blog/co-scientist-a-multi-agent-ai-partner-to-accelerate-research/
- https://deepmind.google/blog/securing-the-future-of-ai-agents/
- https://research.google/blog/unlocking-dependable-responses-with-gemini-enterprise-agent-platforms-agentic-rag/

### 其他机构

- https://arxiv.org/abs/2602.02475
- https://www.microsoft.com/en-us/research/blog/systematic-debugging-for-ai-agents-introducing-the-agentrx-framework/
- https://arxiv.org/abs/2602.14229
- https://www.microsoft.com/en-us/research/blog/corpgen-advances-ai-agents-for-real-work/
- https://ai.meta.com/research/publications/superintelligent-retrieval-agent-the-next-frontier-of-agentic-retrieval/
- https://arxiv.org/abs/2606.24597
- https://github.com/QwenLM/Qwen-AgentWorld
- https://arxiv.org/abs/2602.02276
