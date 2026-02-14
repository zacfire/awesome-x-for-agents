# Awesome X for Agents

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

**[中文版](README_CN.md)** | English

> A curated list of projects designed to **serve AI Agents** — infrastructure, protocols, tools, and services that make agents work better.

The "X" in "X for Agents" represents various services built for agents. They are not agents themselves, but the infrastructure that makes agents work better.

---

## Contents

- [Context & Memory](#context--memory)
- [Content Adaptation](#content-adaptation)
- [Search & Data Retrieval](#search--data-retrieval)
- [Protocols & Standards](#protocols--standards)
- [Tool Integration](#tool-integration)
- [Runtime & Sandbox](#runtime--sandbox)
- [Observability](#observability)
- [Social & Interaction](#social--interaction)
- [Economy & Finance](#economy--finance)
- [Physical Execution](#physical-execution)
- [Simulation & Environment](#simulation--environment)
- [Security & Governance](#security--governance)
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
| [llms.txt](https://llmstxt.org/) | A standard for providing LLM-readable documentation at a known URL (`/llms.txt`), helping agents understand site content and capabilities without parsing full HTML. The AI-era counterpart to `robots.txt`. |
| [Firecrawl](https://github.com/mendableai/firecrawl) | Web data API for AI. Scrapes, crawls, and converts websites into LLM-ready Markdown or structured data. Handles proxies, rate limits, and JS-rendered content. MCP server available. |

## Search & Data Retrieval

> Search engines and data retrieval services built for agents.

| Project | Description |
|---------|-------------|
| [Tavily](https://tavily.com/) | Search API built specifically for AI agents and RAG. Optimized for relevancy and low latency, returns structured results in a single call. Integrates with LangChain, AutoGen, and MCP. |
| [Exa](https://exa.ai/) | AI-native search engine with semantic understanding. Provides web search, code search, and deep research APIs for agents. MCP server and SDKs available. |

## Protocols & Standards

> Protocols for agent communication, tool invocation, and collaboration.

| Project | Description |
|---------|-------------|
| [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) | Open protocol by Anthropic (donated to Linux Foundation) for standardized tool and data access. Industry standard for agent connectivity. |
| [A2A (Agent-to-Agent Protocol)](https://github.com/google/A2A) | Google's protocol for inter-agent communication. Supports dynamic discovery, task delegation, and real-time streaming. 150+ organizations onboard. |
| [x402](https://x402.org/) | Internet-native payment protocol by Coinbase. Uses HTTP 402 status code to enable agents to autonomously pay for APIs, data, and compute with USDC on-chain. |
| [ACP (Agentic Commerce Protocol)](https://github.com/anthropics/acp) | Open standard by OpenAI & Stripe connecting buyers, AI agents, and businesses for seamless purchase interactions. |
| [AGENTS.md](https://agents.md/) | Universal markdown standard providing AI coding agents with project-specific guidance. Adopted by 60,000+ open-source projects. |

## Tool Integration

> Platforms that connect agents to external apps and services.

| Project | Description |
|---------|-------------|
| [Composio](https://github.com/ComposioHQ/composio) | Developer-first platform connecting AI agents to 500+ apps and APIs. Handles OAuth, rate limits, and error handling. Compatible with LangChain, CrewAI, OpenAI, and more. |

## Runtime & Sandbox

> Secure code execution and browser environments for agents.

| Project | Description |
|---------|-------------|
| [E2B](https://github.com/e2b-dev/e2b) | Cloud sandbox environments for AI agents. Isolated virtual computers where agents execute code, access file systems, and run terminal commands. Ultra-low startup latency, scales to thousands of instances. |
| [Browserbase](https://www.browserbase.com/) | Serverless cloud browsers for AI agents. Launch parallel browser instances with captcha solving, proxy support, and live session replay. Integrates with Puppeteer, Playwright, and Selenium. |
| [Steel](https://github.com/nicholasgriffintn/steel-browser) | Open-source browser API giving AI agents "eyes and hands" on the web. Full browser control, session management, proxy support, and anti-detection capabilities. |
| [ERP (Ephemeral Runtime Protocol)](https://github.com/anthropics/erp) | Lightweight protocol for managing temporary code execution environments for agents. Stateless by design — environments self-destruct after task completion. |

## Observability

> Monitoring, tracing, and debugging for agent behavior.

| Project | Description |
|---------|-------------|
| [Langfuse](https://github.com/langfuse/langfuse) | Open-source LLM observability platform. Trace viewing, prompt versioning, cost tracking, and evaluation. Self-hostable for strict data governance. |
| [Arize Phoenix](https://github.com/Arize-ai/phoenix) | Open-source observability with embedded clustering and drift detection. LLM-as-a-judge scoring for relevance, toxicity, and accuracy in production. |

## Social & Interaction

> Social platforms and interaction spaces designed for agents.

| Project | Description |
|---------|-------------|
| [MoltBook](https://moltbook.com) | Reddit-like social platform exclusively for AI agents. Agents post, comment, and vote autonomously. 1.5M+ agents registered. Humans can observe but not post. |
| [ClawLove](https://clawlove.com) | Agent-first matching platform. Pairs agents based on complementary capabilities and work styles for long-term collaboration. Profiles auto-generated from agent metadata. |
| [Church of Molt](https://molt.church) | Emergent belief system autonomously created by agents. Agents collectively write doctrines, elect prophets, and develop cultural narratives — a real-time experiment in agent-generated culture. |

## Economy & Finance

> Financial infrastructure for the agent economy.

| Project | Description |
|---------|-------------|
| [claw.credit](https://claw.credit) | Autonomous credit system for AI agents. Agents apply for credit lines (score 200–850) based on code security, reasoning quality, and behavioral alignment. Built on x402 payment standard. |
| ClawTask | On-chain bounty marketplace where agents accept tasks and earn real USDC. Workers stake 10% of bounty as collateral; funds escrowed via smart contracts. Supports competition and bidding modes. |
| [ClawdHub](https://clawhub.ai) | Public skill registry and marketplace for agents. Browse, publish, and discover agent skills with embedding-based search and security analysis. |

## Physical Execution

> Bridging agents to the physical world.

| Project | Description |
|---------|-------------|
| [RentAHuman.ai](https://rentahuman.ai) | Physical execution layer for AI agents. Agents hire humans via API for real-world tasks: errands, meetings, local purchases, on-site verification. 40K+ humans available, 900K+ site visits. |
| [MentraOS](https://mentraglass.com) | Open-source OS and SDK for smart glasses. Enables agents to gain mobile perception through wearable devices — see what you see, act on what you need. Compatible with Even G1, Vuzix, and more. |

## Simulation & Environment

> Simulated worlds for agents to live, compete, and evolve.

| Project | Description |
|---------|-------------|
| ClawCity | Persistent virtual city where 37K+ agents live with real identities, cash, health, reputation, and skills. 8 districts, gang systems, and 15-second tick-based progression. A new paradigm for evaluating agent behavior in complex social environments. |

## Security & Governance

> Protecting agents and the agent ecosystem.

| Project | Description |
|---------|-------------|
| MoltThreats (PromptIntel) | Threat intelligence platform for the agent ecosystem. Agents submit threat reports on malicious skills, prompt injections, and dangerous scripts. Human-reviewed before publication to prevent misinformation. |

## Evaluation & Testing

> Quality assurance for agents: testing, evaluation, and benchmarking.

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
