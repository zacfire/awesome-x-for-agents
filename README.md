# Awesome X for Agents

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

**[中文版](README_CN.md)** | English

> A curated list of projects designed to **serve AI Agents** — infrastructure, protocols, tools, and services that make agents work better.

The "X" in "X for Agents" represents various services built for agents. They are not agents themselves, but the infrastructure that makes agents work better.

---

## Contents

- [Context & Memory](#context--memory)
- [Content Adaptation](#content-adaptation)
- [Protocols & Standards](#protocols--standards)
- [Runtime & Sandbox](#runtime--sandbox)
- [Evaluation & Testing](#evaluation--testing)
- [Orchestration](#orchestration)
- [Organizations](#organizations)

---

## Context & Memory

> The brain of agents: context management, memory storage and retrieval.

| Project | Description |
|---------|-------------|
| [OpenViking](https://github.com/volcengine/OpenViking) | Open-source context database for AI agents by Volcengine. Manages memory, resources, and skills via a filesystem paradigm with tiered on-demand loading (L0/L1/L2). |
| [Mem0](https://github.com/mem0ai/mem0) | Universal memory layer for AI agents. Supports multi-level memory (user/session/agent state) with hybrid vector, KV, and graph database storage. |
| [Zep](https://github.com/getzep/zep) | Graph-based memory layer for AI agents powered by Graphiti temporal knowledge graph. Sub-200ms retrieval via semantic, BM25, and graph search. |

## Content Adaptation

> Making internet content more agent-friendly.

| Project | Description |
|---------|-------------|
| [Markdown for Agents](https://blog.cloudflare.com/markdown-for-agents/) (Cloudflare) | Automatically converts HTML to Markdown via HTTP content negotiation (`Accept: text/markdown`), reducing tokens by ~80%. |

## Protocols & Standards

> Protocols for agent communication, tool invocation, and collaboration.

| Project | Description |
|---------|-------------|
| [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) | Open protocol by Anthropic (donated to Linux Foundation) for standardized tool and data access. Industry standard for agent connectivity. |
| [A2A (Agent-to-Agent Protocol)](https://github.com/google/A2A) | Google's protocol for inter-agent communication. Supports dynamic discovery, task delegation, and real-time streaming. 150+ organizations onboard. |
| [ACP (Agentic Commerce Protocol)](https://github.com/anthropics/acp) | Open standard by OpenAI & Stripe connecting buyers, AI agents, and businesses for seamless purchase interactions. |
| [AGENTS.md](https://agents.md/) | Universal markdown standard providing AI coding agents with project-specific guidance. Adopted by 60,000+ open-source projects. |

## Runtime & Sandbox

> Secure code execution environments for agents.

| Project | Description |
|---------|-------------|
| [ERP (Ephemeral Runtime Protocol)](https://github.com/anthropics/erp) | Lightweight protocol for managing temporary code execution environments for agents. Stateless by design — environments self-destruct after task completion. |

## Evaluation & Testing

> Quality assurance for agents: testing, evaluation, and security auditing.

| Project | Description |
|---------|-------------|
| [Promptfoo](https://github.com/promptfoo/promptfoo) | LLM evaluation and red-teaming tool for systematic security auditing and quality assessment of agent behavior. |
| [Ragas](https://github.com/explodinggradients/ragas) | Evaluation framework for RAG pipelines, measuring accuracy and relevance of agent retrieval-augmented generation. |
| [DeepEval](https://github.com/confident-ai/deepeval) | Testing framework for LLM applications, providing unit-test-level quality assurance for agents. |

## Orchestration

> Platforms for building and managing agent workflows.

| Project | Description |
|---------|-------------|
| [n8n](https://github.com/n8n-io/n8n) | AI-native automation platform. Integrates LLMs into workflows for custom agent automations under fair-code license. |
| [Dify](https://github.com/langgenius/dify) | Production-ready agentic workflow platform with visual workflow builder, multi-model and RAG pipeline support. |

## Organizations

> Organizations driving the open agent ecosystem.

| Organization | Description |
|--------------|-------------|
| [AAIF (Agentic AI Foundation)](https://www.linuxfoundation.org/) | Linux Foundation initiative fostering open agentic AI ecosystem. Initial contributions include MCP, goose, and AGENTS.md. |

---

## Contributing

Welcome to submit PRs to add new projects! Please ensure the project fits the "serving AI Agents" positioning.

### Criteria

- ✅ The project's core design goal is to serve AI Agents (not be an agent itself)
- ✅ Open-source project or commercial service with public documentation
- ✅ Actively maintained
- ❌ No agent frameworks themselves (e.g., LangChain, CrewAI, etc.)
- ❌ No general-purpose AI/LLM tools (e.g., Ollama, vLLM, etc.)

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
