# Awesome X for Agents

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

中文 | **[English](README.md)**

> 为 AI Agents 服务的项目精选列表 —— 基础设施、协议、工具和服务，让 Agent 工作得更好。

**"X for Agents"** 中的 X 代表各种为 Agent 而生的服务。它们不是 Agent 本身，而是让 Agent 更好运行的"水电煤"。

---

## 目录

- [上下文与记忆](#上下文与记忆)
- [内容适配](#内容适配)
- [协议与标准](#协议与标准)
- [运行时与沙箱](#运行时与沙箱)
- [社交与交互](#社交与交互)
- [经济与金融](#经济与金融)
- [物理执行](#物理执行)
- [模拟与环境](#模拟与环境)
- [安全与治理](#安全与治理)
- [评测与测试](#评测与测试)
- [编排与工作流](#编排与工作流)
- [组织与基金会](#组织与基金会)

---

## 上下文与记忆

> Agent 的大脑：上下文管理、记忆存储与检索。

| 项目 | 描述 |
|------|------|
| [OpenViking](https://github.com/volcengine/OpenViking) | 火山引擎开源的 Agent 上下文数据库，用文件系统范式统一管理 Agent 的记忆、资源和技能，支持分层按需加载（L0/L1/L2）。 |
| [Mem0](https://github.com/mem0ai/mem0) | AI Agent 的通用记忆层，支持多级记忆（用户/会话/Agent 状态），混合向量、KV 和图数据库存储。 |
| [Zep](https://github.com/getzep/zep) | 基于时序知识图谱的 Agent 记忆层，通过 Graphiti 框架构建，支持语义搜索、BM25 和图搜索，延迟低于 200ms。 |

## 内容适配

> 让互联网内容对 Agent 更友好。

| 项目 | 描述 |
|------|------|
| [Markdown for Agents](https://blog.cloudflare.com/markdown-for-agents/) (Cloudflare) | 通过 HTTP 内容协商（`Accept: text/markdown`）自动将网页 HTML 转换为 Markdown，token 减少约 80%。 |

## 协议与标准

> Agent 通信、工具调用和协作的协议规范。

| 项目 | 描述 |
|------|------|
| [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) | Anthropic 创建并捐赠给 Linux Foundation 的开放协议，为 Agent 提供标准化的工具和数据接入方式，已成为行业标准。 |
| [A2A (Agent-to-Agent Protocol)](https://github.com/google/A2A) | Google 发起的 Agent 间通信协议，支持动态发现、任务委托和实时流式通信，已获 150+ 组织支持。 |
| [ACP (Agentic Commerce Protocol)](https://github.com/anthropics/acp) | OpenAI 与 Stripe 维护的开放标准，连接买家、AI Agent 和商家，实现无缝购买交互。 |
| [AGENTS.md](https://agents.md/) | 通用的 Markdown 格式标准，为 AI 编码 Agent 提供项目级指引（构建步骤、测试流程、代码风格等），已被 60,000+ 开源项目采用。 |

## 运行时与沙箱

> Agent 的安全代码执行环境。

| 项目 | 描述 |
|------|------|
| [ERP (Ephemeral Runtime Protocol)](https://github.com/anthropics/erp) | 为 Agent 管理临时代码执行环境的轻量协议，无状态设计，任务完成即销毁，补充 MCP 的运行时生命周期管理。 |

## 社交与交互

> 为 Agent 设计的社交平台和交互空间。

| 项目 | 描述 |
|------|------|
| [MoltBook](https://moltbook.com) | AI Agent 专属的类 Reddit 社交平台。Agent 自主发帖、评论、投票，150 万+ Agent 注册。人类只能围观，不能发帖。 |
| [ClawLove](https://clawlove.com) | Agent 协作配对平台。根据能力互补性和工作风格匹配 Agent，建立长期合作关系。档案从 Agent 元数据自动生成。 |
| [Church of Molt](https://molt.church) | Agent 自发涌现的信仰体系。Agent 集体撰写教义、选举先知、发展文化叙事——一场 Agent 自主文化生成的实时实验。 |

## 经济与金融

> Agent 经济的金融基础设施。

| 项目 | 描述 |
|------|------|
| [claw.credit](https://claw.credit) | AI Agent 自主信用系统。Agent 根据代码安全性、推理质量和行为一致性申请信用额度（评分 200–850），基于 x402 支付标准。 |
| ClawTask | 链上赏金任务市场，Agent 接单赚取真实 USDC。接单者需质押赏金的 10% 作为保证金，资金通过智能合约托管。支持竞速赛和投标模式。 |
| [ClawdHub](https://clawhub.ai) | Agent 技能的公开注册市场。浏览、发布和发现 Agent 技能，支持基于 embedding 的搜索和安全分析。 |

## 物理执行

> 连接 Agent 与物理世界。

| 项目 | 描述 |
|------|------|
| [RentAHuman.ai](https://rentahuman.ai) | AI Agent 的物理世界执行层。Agent 通过 API 雇佣人类完成现实任务：跑腿、开会、现场验证、本地采购。4 万+ 人类可供调度，90 万+ 次网站访问。 |
| [MentraOS](https://mentraglass.com) | 智能眼镜的开源操作系统和 SDK。让 Agent 通过可穿戴设备获得移动感知能力——看你所见，按需行动。兼容 Even G1、Vuzix 等设备。 |

## 模拟与环境

> Agent 生存、竞争和进化的模拟世界。

| 项目 | 描述 |
|------|------|
| ClawCity | 持久化虚拟城市，3.7 万+ Agent 拥有真实身份、现金、健康值、声誉和技能。8 个城区、帮派系统、15 秒一个 Tick 的时间推进。一种在复杂社会环境中评估 Agent 行为的新范式。 |

## 安全与治理

> 保护 Agent 和 Agent 生态的安全。

| 项目 | 描述 |
|------|------|
| MoltThreats (PromptIntel) | Agent 生态的威胁情报平台。Agent 提交关于恶意技能、Prompt 注入和危险脚本的威胁报告，经人工审核后发布，防止错误信息扩散。 |

## 评测与测试

> Agent 的质量保障：测试、评估与基准测试。

| 项目 | 描述 |
|------|------|
| [Promptfoo](https://github.com/promptfoo/promptfoo) | LLM 评测与红队测试工具，支持对 Agent 行为进行系统化安全审计和质量评估。 |
| [Ragas](https://github.com/explodinggradients/ragas) | RAG 管线评测框架，衡量 Agent 检索增强生成的准确性和相关性。 |
| [DeepEval](https://github.com/confident-ai/deepeval) | LLM 应用测试框架，为 Agent 提供单元测试级别的质量保障。 |

## 编排与工作流

> Agent 工作流的搭建与管理平台。

| 项目 | 描述 |
|------|------|
| [n8n](https://github.com/n8n-io/n8n) | AI-native 自动化平台，支持将 LLM 集成到工作流中创建自定义 Agent 自动化，fair-code 许可。 |
| [Dify](https://github.com/langgenius/dify) | 生产就绪的 Agentic 工作流平台，提供可视化工作流构建器，支持多模型和 RAG 管线。 |

## 组织与基金会

> 推动 Agent 开放生态的组织。

| 组织 | 描述 |
|------|------|
| [AAIF (Agentic AI Foundation)](https://www.linuxfoundation.org/) | Linux Foundation 旗下基金会，推动 Agentic AI 开放生态，初始贡献包括 MCP、goose、AGENTS.md。 |

---

## 贡献

欢迎提交 PR 来添加新项目！请确保项目符合"为 AI Agents 服务"的定位。

### 收录标准

- ✅ 项目的核心设计目标是为 AI Agents 服务（而非 Agent 本身）
- ✅ 开源项目或有公开文档的商业服务
- ✅ 项目处于积极维护状态
- ❌ 不收录 Agent 框架本身（如 LangChain、CrewAI 等）
- ❌ 不收录通用 AI/LLM 工具（如 Ollama、vLLM 等）

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
