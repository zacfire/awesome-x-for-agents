# Awesome X for Agents

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of projects designed to **serve AI Agents** — infrastructure, protocols, tools, and services that make agents work better.
>
> 为 AI Agents 服务的项目精选列表 —— 基础设施、协议、工具和服务，让 Agent 工作得更好。

**"X for Agents"** 中的 X 代表各种为 Agent 而生的服务。它们不是 Agent 本身，而是让 Agent 更好运行的"水电煤"。

The "X" in "X for Agents" represents various services built for agents. They are not agents themselves, but the infrastructure that makes agents work better.

---

## Contents / 目录

- [Context & Memory / 上下文与记忆](#context--memory--上下文与记忆)
- [Content Adaptation / 内容适配](#content-adaptation--内容适配)
- [Protocols & Standards / 协议与标准](#protocols--standards--协议与标准)
- [Runtime & Sandbox / 运行时与沙箱](#runtime--sandbox--运行时与沙箱)
- [Evaluation & Testing / 评测与测试](#evaluation--testing--评测与测试)
- [Orchestration / 编排与工作流](#orchestration--编排与工作流)
- [Organizations / 组织与基金会](#organizations--组织与基金会)

---

## Context & Memory / 上下文与记忆

> Agent 的大脑：上下文管理、记忆存储与检索。
>
> The brain of agents: context management, memory storage and retrieval.

| Project | Description |
|---------|-------------|
| [OpenViking](https://github.com/volcengine/OpenViking) | 火山引擎开源的 Agent 上下文数据库，用文件系统范式统一管理 Agent 的记忆、资源和技能，支持分层按需加载（L0/L1/L2）。<br>Open-source context database for AI agents by Volcengine. Manages memory, resources, and skills via a filesystem paradigm with tiered on-demand loading. |
| [Mem0](https://github.com/mem0ai/mem0) | AI Agent 的通用记忆层，支持多级记忆（用户/会话/Agent 状态），混合向量、KV 和图数据库存储。<br>Universal memory layer for AI agents. Supports multi-level memory (user/session/agent state) with hybrid vector, KV, and graph database storage. |
| [Zep](https://github.com/getzep/zep) | 基于时序知识图谱的 Agent 记忆层，通过 Graphiti 框架构建，支持语义搜索、BM25 和图搜索，延迟低于 200ms。<br>Graph-based memory layer for AI agents powered by Graphiti temporal knowledge graph. Sub-200ms retrieval via semantic, BM25, and graph search. |

## Content Adaptation / 内容适配

> 让互联网内容对 Agent 更友好。
>
> Making internet content more agent-friendly.

| Project | Description |
|---------|-------------|
| [Markdown for Agents](https://blog.cloudflare.com/markdown-for-agents/) (Cloudflare) | 通过 HTTP 内容协商（`Accept: text/markdown`）自动将网页 HTML 转换为 Markdown，token 减少约 80%。<br>Automatically converts HTML to Markdown via HTTP content negotiation (`Accept: text/markdown`), reducing tokens by ~80%. |

## Protocols & Standards / 协议与标准

> Agent 通信、工具调用和协作的协议规范。
>
> Protocols for agent communication, tool invocation, and collaboration.

| Project | Description |
|---------|-------------|
| [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) | Anthropic 创建并捐赠给 Linux Foundation 的开放协议，为 Agent 提供标准化的工具和数据接入方式，已成为行业标准。<br>Open protocol by Anthropic (donated to Linux Foundation) for standardized tool and data access. Industry standard for agent connectivity. |
| [A2A (Agent-to-Agent Protocol)](https://github.com/google/A2A) | Google 发起的 Agent 间通信协议，支持动态发现、任务委托和实时流式通信，已获 150+ 组织支持。<br>Google's protocol for inter-agent communication. Supports dynamic discovery, task delegation, and real-time streaming. 150+ organizations onboard. |
| [ACP (Agentic Commerce Protocol)](https://github.com/anthropics/acp) | OpenAI 与 Stripe 维护的开放标准，连接买家、AI Agent 和商家，实现无缝购买交互。<br>Open standard by OpenAI & Stripe connecting buyers, AI agents, and businesses for seamless purchase interactions. |
| [AGENTS.md](https://agents.md/) | 通用的 Markdown 格式标准，为 AI 编码 Agent 提供项目级指引（构建步骤、测试流程、代码风格等），已被 60,000+ 开源项目采用。<br>Universal markdown standard providing AI coding agents with project-specific guidance. Adopted by 60,000+ open-source projects. |

## Runtime & Sandbox / 运行时与沙箱

> Agent 的安全代码执行环境。
>
> Secure code execution environments for agents.

| Project | Description |
|---------|-------------|
| [ERP (Ephemeral Runtime Protocol)](https://github.com/anthropics/erp) | 为 Agent 管理临时代码执行环境的轻量协议，无状态设计，任务完成即销毁，补充 MCP 的运行时生命周期管理。<br>Lightweight protocol for managing temporary code execution environments for agents. Stateless by design — environments self-destruct after task completion. |

## Evaluation & Testing / 评测与测试

> Agent 的质量保障：测试、评估与安全审计。
>
> Quality assurance for agents: testing, evaluation, and security auditing.

| Project | Description |
|---------|-------------|
| [Promptfoo](https://github.com/promptfoo/promptfoo) | LLM 评测与红队测试工具，支持对 Agent 行为进行系统化安全审计和质量评估。<br>LLM evaluation and red-teaming tool for systematic security auditing and quality assessment of agent behavior. |
| [Ragas](https://github.com/explodinggradients/ragas) | RAG 管线评测框架，衡量 Agent 检索增强生成的准确性和相关性。<br>Evaluation framework for RAG pipelines, measuring accuracy and relevance of agent retrieval-augmented generation. |
| [DeepEval](https://github.com/confident-ai/deepeval) | LLM 应用测试框架，为 Agent 提供单元测试级别的质量保障。<br>Testing framework for LLM applications, providing unit-test-level quality assurance for agents. |

## Orchestration / 编排与工作流

> Agent 工作流的搭建与管理平台。
>
> Platforms for building and managing agent workflows.

| Project | Description |
|---------|-------------|
| [n8n](https://github.com/n8n-io/n8n) | AI-native 自动化平台，支持将 LLM 集成到工作流中创建自定义 Agent 自动化，fair-code 许可。<br>AI-native automation platform. Integrates LLMs into workflows for custom agent automations under fair-code license. |
| [Dify](https://github.com/langgenius/dify) | 生产就绪的 Agentic 工作流平台，提供可视化工作流构建器，支持多模型和 RAG 管线。<br>Production-ready agentic workflow platform with visual workflow builder, multi-model and RAG pipeline support. |

## Organizations / 组织与基金会

> 推动 Agent 开放生态的组织。
>
> Organizations driving the open agent ecosystem.

| Organization | Description |
|--------------|-------------|
| [AAIF (Agentic AI Foundation)](https://www.linuxfoundation.org/) | Linux Foundation 旗下基金会，推动 Agentic AI 开放生态，初始贡献包括 MCP、goose、AGENTS.md。<br>Linux Foundation initiative fostering open agentic AI ecosystem. Initial contributions include MCP, goose, and AGENTS.md. |

---

## Contributing / 贡献

欢迎提交 PR 来添加新项目！请确保项目符合 "为 AI Agents 服务" 的定位。

Welcome to submit PRs to add new projects! Please ensure the project fits the "serving AI Agents" positioning.

### 收录标准 / Criteria

- ✅ 项目的核心设计目标是为 AI Agents 服务（而非 Agent 本身）
- ✅ 开源项目或有公开文档的商业服务
- ✅ 项目处于积极维护状态
- ❌ 不收录 Agent 框架本身（如 LangChain、CrewAI 等）
- ❌ 不收录通用 AI/LLM 工具（如 Ollama、vLLM 等）

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
