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

## 评测与测试

> Agent 的质量保障：测试、评估与安全审计。

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
