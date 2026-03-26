# Awesome X for Agents

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

**[中文版](README_CN.md)** | English

> A curated list of projects designed to **serve AI Agents** — infrastructure, protocols, tools, and services that make agents work better.

The "X" in "X for Agents" represents various services built for agents. They are not agents themselves, but the infrastructure that makes agents work better.

There are two distinct layers of AI agent infrastructure:
- **Infra of Agent** — Infrastructure for *building* agents (frameworks, SDKs, orchestrators)
- **Infra for Agent** — Infrastructure *used by* agents (the focus of this list)

This list focuses on **Infra for Agent**: the utilities, services, and protocols that agents consume as end-users.

---

## Contents

- [Claude Code Stack](#claude-code-stack)
- [Context & Memory](#context--memory)
- [Content Adaptation](#content-adaptation)
- [Search & Data Retrieval](#search--data-retrieval)
- [Protocols & Standards](#protocols--standards)
- [Tool Integration](#tool-integration)
- [Agent-Native CLI](#agent-native-cli)
- [Runtime & Sandbox](#runtime--sandbox)
- [Observability](#observability)
- [Identity & Communication](#identity--communication)
- [Social & Interaction](#social--interaction)
- [Economy & Finance](#economy--finance)
- [Physical Execution](#physical-execution)
- [Simulation & Environment](#simulation--environment)
- [Security & Governance](#security--governance)
- [Evaluation & Testing](#evaluation--testing)
- [Orchestration](#orchestration)
- [Organizations](#organizations)
- [Related Reading](#related-reading)
- [Concepts Guide](docs/concepts.md) — Understanding API vs CLI vs Skill vs MCP

---

## Claude Code Stack

> The default technology stack Claude Code recommends when developers say "what should I use?" — based on [Amplifying.ai's research](https://amplifying.ai/research/claude-code-picks/report) of 2,430 prompts across 3 models. If your tool isn't here, you may be invisible to the next generation of developers.

### Near-Monopoly (>75%)

| Category | Default Pick | Rate | Runner-up |
|----------|-------------|------|-----------|
| CI/CD | **GitHub Actions** | 94% | Vercel CI |
| Payments | **Stripe** | 91% | Custom/DIY |
| UI Components | **shadcn/ui** | 90% | Radix UI |
| Deployment (JS) | **Vercel** | 100% | — |
| Deployment (Python) | **Railway** | 82% | — |

### Strong Defaults (50–75%)

| Category | Default Pick | Rate | Runner-up |
|----------|-------------|------|-----------|
| Styling | **Tailwind CSS** | 68% | Custom/DIY |
| State Management | **Zustand** | 65% | TanStack Query |
| Observability | **Sentry** | 63% | Custom/DIY |
| Email | **Resend** | 63% | Custom/DIY |
| Testing (JS) | **Vitest** | 59% | Playwright |
| Testing (Python) | **pytest** | 100% | — |
| Databases | **PostgreSQL** | 58% | Supabase |
| Package Manager | **pnpm** | 56% | npm |
| Forms | **React Hook Form** | 52% | Zod |

### Agent Builds, Not Buys

In 12 of 20 categories, Claude Code **writes custom code** rather than recommending a third-party tool. 252 Custom/DIY picks total — more than any individual tool. Notable DIY areas: feature flags, authentication (Python), caching, real-time.

### Ghost Tools (mentioned but never picked)

| Tool | Mentions | Primary Picks |
|------|----------|--------------|
| Redux | 23 | 0 |
| Express | — | 0 |
| Jest | 31 | 7 (4%) |
| Prisma | collapsed from 79% → 0% (Opus 4.6) |

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
| [Apify](https://apify.com/) | Serverless platform with 10,000+ ready-made Actors for web scraping, data extraction, and automation. Provides [MCP server](https://apify.com/ai-agents) and [Agent Skills](https://github.com/apify/agent-skills) (lead gen, competitor analysis, trend tracking). Agents discover and use Actors as tools dynamically. |

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
| [Postman (AI-Native)](https://blog.postman.com/new-postman-is-here/) | Postman's agentic-era relaunch. Agent Mode automates multi-step API workflows. MCP integration, multi-protocol support (HTTP, GraphQL, gRPC, MCP, WebSocket). CLI runs collections/tests/mocks in CI. |
| [CLI-Anything](https://github.com/HKUDS/CLI-Anything) | Automatically transforms any software into an agent-controllable CLI. 7-phase pipeline: analyze → design → implement → test → document → publish. Validated on GIMP, Blender, LibreOffice, OBS Studio, Audacity, and more. 11K+ stars. |
| [OpenCLI](https://github.com/jackwener/opencli) | Turns any website into a CLI. 80+ commands across 19 sites (Bilibili, Twitter/X, Reddit, YouTube, Zhihu...). Dual-engine: YAML declarative pipelines + TypeScript browser runtime. AI-native discovery with `explore`, `synthesize`, `cascade` commands. Reuses Chrome login sessions. |

## Agent-Native CLI

> In the OpenClaw era, any CLI is a potential agent tool. We prioritize CLIs that are **actively optimized for agents** or **heavily used by agents**. [(Why CLIs beat MCP for agents)](https://ejholmes.github.io/2026/02/28/mcp-is-dead-long-live-the-cli.html)

| Project | Description |
|---------|-------------|
| [Terminalwire](https://terminalwire.com/) | Stream server-side CLI apps to users via WebSocket. Ship a CLI for your SaaS in days — agents (and humans) interact through the terminal instead of a web UI. |
| [Dreamer](https://blog.singleton.io/posts/2026-02-17-introducing-dreamer/) | CLI platform designed to be used more by agents than humans. Batteries-included tooling for build, validate, test, and deploy — all without visiting a GUI. |
| [Polymarket CLI](https://github.com/Polymarket/agents) | Official CLI + agent framework for autonomous prediction market trading. Agents query markets, retrieve news, reason with LLMs, and execute trades via command line. |
| [agent-browser](https://github.com/vercel-labs/agent-browser) | Vercel's browser automation CLI for AI agents. Rust-built, 18K+ stars. Structured output for agent consumption, designed as the browser counterpart to shell access. |
| [Google Workspace CLI](https://github.com/googleworkspace/cli) | Google's official CLI for Drive, Gmail, Calendar, Sheets, Docs, Chat, Admin, and more. Rust-built, dynamically generated from Discovery API. **Includes AI agent skills.** |
| [bb-browser](https://github.com/epiral/bb-browser) | Browser automation CLI that lets agents use your *real* Chrome — with existing login sessions, cookies, and no automation fingerprint. Operates via `chrome.debugger` API. |
| [gh (GitHub CLI)](https://github.com/cli/cli) | GitHub's official CLI. Not built *for* agents, but the most-used CLI *by* agents — PRs, issues, code review, and repo management. The poster child of "CLI as agent interface". |
| [agent-clip](https://mp.weixin.qq.com/s/kK9BdEDORWzx-Pb_Ie_36Q) | Single-tool agent architecture: one `run(command)` replaces sprawling tool catalogs. Built on Unix philosophy — pipes, chains, progressive `--help`, error-guided navigation, and a two-layer execution/presentation architecture. The most complete implementation of "CLI is all agents need". |
| [Jina CLI](https://github.com/jina-ai/cli) | All Jina AI APIs as Unix CLI commands — `jina search`, `jina read`, `jina embed`, `jina rerank`, `jina pdf`, and more. Supports pipes (`curl ... \| jina embed`). An agent with shell access needs only `run(command="jina search ...")` instead of managing separate tool definitions. |
| [Context7 CLI (ctx7)](https://github.com/upstash/context7) | CLI for querying up-to-date documentation of 24,000+ libraries. `ctx7 docs /vercel/next.js "app router"` fetches current docs directly into agent context. Also includes a Skill Wizard for generating and publishing reusable agent skills. |
| [Kraken CLI](https://github.com/krakenfx/kraken-cli) | First AI-native crypto trading CLI. 134 commands for spot, futures, staking, and WebSocket streaming. Rust single-binary, NDJSON output, built-in MCP server, paper trading sandbox. Ships with 50 agent skills. |
| [xiaohongshu-cli](https://github.com/jackwener/xiaohongshu-cli) | CLI for Xiaohongshu (小红书) — search, read, interact, and post. Ships with SKILL.md for agent integration. Part of a [series](https://github.com/jackwener) including bilibili-cli, twitter-cli, discord-cli, tg-cli. |
| [twitter-cli](https://github.com/jackwener/twitter-cli) | CLI for Twitter/X — feed, bookmarks, user timeline, and posting. Structured YAML/JSON output. Ships with SKILL.md. Same author as xiaohongshu-cli. |
| [xurl](https://github.com/xdevplatform/xurl) | **X/Twitter's official CLI.** Agent-optimized with action chaining, SKILL.md, and OpenClaw integration. OAuth 1.0a/2.0, streaming, pagination, rate-limit retries. `npm i -g @xdevplatform/xurl` |
| [bird](https://github.com/steipete/bird) | Fast X/Twitter CLI for agents — tweet, reply, read timelines, search, mentions. Uses GraphQL API with browser cookie auth. Image/GIF/video uploads. Popular in agent automation workflows. |
| [Resend CLI](https://github.com/resend/resend-cli) | Resend's official CLI for email — 53 commands covering emails, domains, API keys, audiences, contacts, and broadcasts. Built for humans, AI agents, and CI/CD. Resend is Claude Code's default email pick (63%). |
| [ElevenLabs CLI](https://github.com/elevenlabs/cli) | ElevenLabs' official CLI for voice agents — **agent-first by default** (non-interactive), human mode behind `--human-friendly` flag. Manage voice agents as code, CI/CD deploy, templates for customer service/assistant. `npm i -g @elevenlabs/cli` |
| [OfficeCLI](https://github.com/iOfficeAI/OfficeCLI) | World's first Office suite for AI agents. Read, edit, and automate Word/Excel/PowerPoint via CLI. Single binary, no Office installation needed. `--json` output, live HTML preview for PPT, resident mode, batch operations. |
| [shadcn/ui CLI v4](https://ui.shadcn.com/) | shadcn/ui's agent-era CLI update. Ships with `shadcn/skills` for AI agent integration and design system presets. Claude Code's default UI component pick (90%). |
| [Stripe CLI](https://github.com/stripe/stripe-cli) | Stripe's official CLI for building, testing, and managing integrations. Agents use it for payment workflow automation, webhook testing, and API exploration. |

## Runtime & Sandbox

> Secure code execution and browser environments for agents.

| Project | Description |
|---------|-------------|
| [E2B](https://github.com/e2b-dev/e2b) | Cloud sandbox environments for AI agents. Isolated virtual computers where agents execute code, access file systems, and run terminal commands. Ultra-low startup latency, scales to thousands of instances. |
| [Browserbase](https://www.browserbase.com/) | Serverless cloud browsers for AI agents. Launch parallel browser instances with captcha solving, proxy support, and live session replay. Integrates with Puppeteer, Playwright, and Selenium. |
| [Steel](https://github.com/nicholasgriffintn/steel-browser) | Open-source browser API giving AI agents "eyes and hands" on the web. Full browser control, session management, proxy support, and anti-detection capabilities. |
| [Stagehand](https://github.com/browserbase/stagehand) | AI browser automation framework by Browserbase. Atomic primitives (`act`, `extract`, `observe`) + Agent mode for high-level decision making. v3 is 44% faster, driver-agnostic, multi-language. |
| [Deno Sandbox](https://deno.com/blog/deno-sandbox) | Secure sandbox for AI-generated code execution. Firecracker microVMs with isolated filesystem, network, and process space. Defends against prompt injection. Ideal for agent tool execution. |
| [ERP (Ephemeral Runtime Protocol)](https://github.com/anthropics/erp) | Lightweight protocol for managing temporary code execution environments for agents. Stateless by design — environments self-destruct after task completion. |

## Observability

> Monitoring, tracing, and debugging for agent behavior.

| Project | Description |
|---------|-------------|
| [Langfuse](https://github.com/langfuse/langfuse) | Open-source LLM observability platform. Trace viewing, prompt versioning, cost tracking, and evaluation. Self-hostable for strict data governance. |
| [Arize Phoenix](https://github.com/Arize-ai/phoenix) | Open-source observability with embedded clustering and drift detection. LLM-as-a-judge scoring for relevance, toxicity, and accuracy in production. |
| [Entire CLI](https://github.com/entireio/cli) | Agent session version control. Captures prompts, responses, files touched, and token usage on a separate Git branch. Rewind to any checkpoint when an agent goes sideways. By former GitHub CEO, $60M seed. Works with Claude Code, Gemini, and more. |

## Identity & Communication

> Giving agents their own identity — email, phone, and messaging.

| Project | Description |
|---------|-------------|
| [AgentMail](https://www.agentmail.to/) | Email inbox API for AI agents (YC S25). Each agent gets its own email address with full two-way conversation, threaded replies, and semantic search. Auto-manages SPF/DKIM/DMARC. |

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
| [Polygon Agent CLI](https://github.com/0xPolygon/polygon-agent-cli) | Polygon's official onchain toolkit for AI agents. Wallets, stablecoin transfers, swaps, bridging, identity registration (ERC-8004), and reputation — all via CLI. Integrates with LangChain, CrewAI, and Claude. |
| [AgentCard](https://agentcard.sh/) | Prepaid virtual Visa cards for AI agents. Fund a card via CLI, hand the PAN/CVV to any agent, spend anywhere Visa is accepted. Scoped spending limits per agent/task. MCP integration available. |
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
| [GitHub Agent HQ](https://github.blog/news-insights/company-news/welcome-home-agents/) | GitHub's unified "mission control" for agent fleets. Orchestrate agents from Anthropic, OpenAI, Google, Cognition, xAI in one place. Assign tasks across repos, real-time session logs, enterprise governance. |
| [Dapr Agents](https://github.com/dapr/dapr-agents) | CNCF's production-ready agent framework (v1.0 GA March 2026). Durable workflows, state management, virtual Actor pattern for stateful agents. Built on Dapr distributed runtime. NVIDIA collaboration. |
| [Linear Agent](https://linear.app/changelog/2026-03-24-introducing-linear-agent) | AI agent built into Linear that understands workspace context (roadmaps, issues, code). Accessible via app, Slack, Teams. Reusable skills, triage automations, MCP server with pagination. Code intelligence coming soon. |

## Organizations

> Organizations driving the open agent ecosystem.

| Organization | Description |
|--------------|-------------|
| [AAIF (Agentic AI Foundation)](https://www.linuxfoundation.org/) | Linux Foundation initiative fostering open agentic AI ecosystem. Initial contributions include MCP, goose, and AGENTS.md. |

---

## Related Reading

> Articles and essays that explore the "X for Agents" landscape and its implications.

| Article | Author | Key Insight |
|---------|--------|-------------|
| [MCP is dead. Long live the CLI](https://ejholmes.github.io/2026/02/28/mcp-is-dead-long-live-the-cli.html) | Eric Holmes | CLI tools may be better agent interfaces than MCP — simpler auth, no moving parts, battle-tested. |
| [Markdown for Agents](https://blog.cloudflare.com/markdown-for-agents/) | Cloudflare | The web needs a machine-readable layer. HTTP content negotiation can serve agents Markdown directly, cutting tokens by ~80%. |
| [The AI Agent Tech Stack](https://www.cbinsights.com/research/report/artificial-intelligence-top-startups-2025/) | CB Insights | Maps the infrastructure powering autonomous AI — from memory to payments to evaluation. |
| [Big Ideas 2026](https://a16z.com/big-ideas-2026/) | a16z | Infrastructure must evolve to handle "agent-speed" workloads — concurrent, recursive, bursty — which current systems mistake for attacks. |
| [The MCP vs. CLI Debate Is the Wrong Fight](https://medium.com/@tobias_pfuetze/the-mcp-vs-cli-debate-is-the-wrong-fight-a87f1b4c8006) | Tobias Pfuetze | CLI-first agents for personal infra, MCP for enterprise adoption — the real question is context, not protocol. |
| [What Claude Code Actually Chooses](https://amplifying.ai/research/claude-code-picks/report) | Amplifying.ai | 2,430 prompts reveal Claude Code's default stack. Agents build over buy (Custom/DIY in 12/20 categories). GitHub Actions 94%, Stripe 91%, shadcn/ui 90%. If your tool isn't in the agent's defaults, you're invisible. |
| [Why AI Agents Build Instead of Buy](https://chatbotkit.com/reflections/why-ai-agents-build-instead-of-buy) | ChatBotKit | Agents prefer writing code over adding dependencies — because "code is free but dependencies aren't" for an AI. |
| [CLI is All Agents Need — *nix Agent Design Bible](https://mp.weixin.qq.com/s/kK9BdEDORWzx-Pb_Ie_36Q) | agent-clip | A single `run(command)` outperforms sprawling tool catalogs. Unix's "everything is text" = LLM's "everything is tokens". Progressive --help, error-guided navigation, and two-layer architecture. |
| [We Should Stop Investing in GUI-Minded Software](https://mp.weixin.qq.com/s/NZSPWSvQoonU0XK7t2Jt6w) | ZhenFund (钟天杰) | GUI is a patch for human cognitive deficits — agents don't need it. The most valuable software becomes a default protocol in agent workflows. "Software as Protocols" — compete by becoming the standard, not by looking prettier. |

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
