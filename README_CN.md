# Awesome X for Agents

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

中文 | **[English](README.md)**

> 为 AI Agents 服务的项目精选列表 —— 基础设施、协议、工具和服务，让 Agent 工作得更好。

**"X for Agents"** 中的 X 代表各种为 Agent 而生的服务。它们不是 Agent 本身，而是让 Agent 更好运行的"水电煤"。

AI Agent 基础设施有两个截然不同的层次：
- **Infra of Agent** — 构建 Agent 的基础设施（框架、SDK、编排器）
- **Infra for Agent** — 给 Agent 用的基础设施（本列表的关注点）

本列表聚焦于 **Infra for Agent**：Agent 作为终端用户所消费的工具、服务和协议。

---

## 目录

- [Claude Code Stack](#claude-code-stack)
- [上下文与记忆](#上下文与记忆)
- [内容适配](#内容适配)
- [搜索与数据获取](#搜索与数据获取)
- [协议与标准](#协议与标准)
- [工具集成](#工具集成)
- [Agent 原生 CLI](#agent-原生-cli)
- [运行时与沙箱](#运行时与沙箱)
- [可观测性](#可观测性)
- [身份与通信](#身份与通信)
- [社交与交互](#社交与交互)
- [经济与金融](#经济与金融)
- [物理执行](#物理执行)
- [模拟与环境](#模拟与环境)
- [安全与治理](#安全与治理)
- [评测与测试](#评测与测试)
- [编排与工作流](#编排与工作流)
- [组织与基金会](#组织与基金会)
- [相关阅读](#相关阅读)
- [概念指南](docs/concepts.md) — 理解 API / CLI / Skill / MCP 的关系与差异

---

## Claude Code Stack

> 当开发者对 Claude Code 说"我该用什么？"时，它默认推荐的技术栈——基于 [Amplifying.ai 的研究](https://amplifying.ai/research/claude-code-picks/report)，2,430 次提示词，3 个模型。如果你的工具不在这里，你可能对下一代开发者来说是隐形的。

### 近乎垄断 (>75%)

| 类别 | 默认选择 | 选中率 | 第二名 |
|------|---------|--------|--------|
| CI/CD | **GitHub Actions** | 94% | Vercel CI |
| 支付 | **Stripe** | 91% | Custom/DIY |
| UI 组件 | **shadcn/ui** | 90% | Radix UI |
| 部署 (JS) | **Vercel** | 100% | — |
| 部署 (Python) | **Railway** | 82% | — |

### 强势默认 (50–75%)

| 类别 | 默认选择 | 选中率 | 第二名 |
|------|---------|--------|--------|
| 样式 | **Tailwind CSS** | 68% | Custom/DIY |
| 状态管理 | **Zustand** | 65% | TanStack Query |
| 可观测性 | **Sentry** | 63% | Custom/DIY |
| 邮件 | **Resend** | 63% | Custom/DIY |
| 测试 (JS) | **Vitest** | 59% | Playwright |
| 测试 (Python) | **pytest** | 100% | — |
| 数据库 | **PostgreSQL** | 58% | Supabase |
| 包管理器 | **pnpm** | 56% | npm |
| 表单 | **React Hook Form** | 52% | Zod |

### Agent 造轮子，不买服务

在 20 个类别中的 12 个，Claude Code **选择手写代码**而非推荐第三方工具。252 次 Custom/DIY 选择——比任何单个工具都多。典型 DIY 领域：功能开关、身份验证 (Python)、缓存、实时通信。

### 幽灵工具（被提及但从未被选中）

| 工具 | 被提及次数 | 被选中次数 |
|------|-----------|-----------|
| Redux | 23 | 0 |
| Express | — | 0 |
| Jest | 31 | 7 (4%) |
| Prisma | 从 79% 暴跌至 0%（Opus 4.6） |

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
| [llms.txt](https://llmstxt.org/) | 网站在 `/llms.txt` 路径提供 LLM 可读文档的标准，帮助 Agent 快速理解网站内容和能力，无需解析完整 HTML。AI 时代的 `robots.txt`。 |
| [Firecrawl](https://github.com/mendableai/firecrawl) | 面向 AI 的网页数据 API。抓取、爬取网站并转换为 LLM 就绪的 Markdown 或结构化数据，处理代理、限速和 JS 渲染。提供 MCP 服务器。 |

## 搜索与数据获取

> 为 Agent 构建的搜索引擎和数据检索服务。

| 项目 | 描述 |
|------|------|
| [Tavily](https://tavily.com/) | 专为 AI Agent 和 RAG 构建的搜索 API。优化相关性和低延迟，单次调用返回结构化结果。集成 LangChain、AutoGen 和 MCP。 |
| [Exa](https://exa.ai/) | AI 原生搜索引擎，具备语义理解能力。为 Agent 提供网页搜索、代码搜索和深度研究 API。提供 MCP 服务器和多语言 SDK。 |
| [Apify](https://apify.com/) | 无服务器平台，10,000+ 现成 Actors 用于网页抓取、数据提取和自动化。提供 [MCP 服务器](https://apify.com/ai-agents)和 [Agent Skills](https://github.com/apify/agent-skills)（线索生成、竞品分析、趋势追踪）。Agent 可动态发现和调用 Actors 作为工具。 |

## 协议与标准

> Agent 通信、工具调用和协作的协议规范。

| 项目 | 描述 |
|------|------|
| [MCP (Model Context Protocol)](https://modelcontextprotocol.io/) | Anthropic 创建并捐赠给 Linux Foundation 的开放协议，为 Agent 提供标准化的工具和数据接入方式，已成为行业标准。 |
| [A2A (Agent-to-Agent Protocol)](https://github.com/google/A2A) | Google 发起的 Agent 间通信协议，支持动态发现、任务委托和实时流式通信，已获 150+ 组织支持。 |
| [x402](https://x402.org/) | Coinbase 推出的互联网原生支付协议。利用 HTTP 402 状态码，让 Agent 自主使用 USDC 链上支付 API、数据和算力费用。 |
| [ACP (Agentic Commerce Protocol)](https://github.com/anthropics/acp) | OpenAI 与 Stripe 维护的开放标准，连接买家、AI Agent 和商家，实现无缝购买交互。 |
| [AGENTS.md](https://agents.md/) | 通用的 Markdown 格式标准，为 AI 编码 Agent 提供项目级指引（构建步骤、测试流程、代码风格等），已被 60,000+ 开源项目采用。 |

## 工具集成

> 连接 Agent 与外部应用和服务的平台。

| 项目 | 描述 |
|------|------|
| [Stripe Projects](https://projects.dev/) | 从 CLI 一键开通生产服务——一条命令完成注册账号、获取 API Key、配置计费。`stripe projects add posthog/analytics`。支持 Vercel、Supabase、Neon、Turso、PostHog、Clerk 等。Agent 不再需要人类去浏览器点注册流程。 |
| [Composio](https://github.com/ComposioHQ/composio) | 开发者优先的 Agent 工具集成平台，连接 500+ 应用和 API。处理 OAuth、限速和错误重试。兼容 LangChain、CrewAI、OpenAI 等框架。 |
| [Postman (AI-Native)](https://blog.postman.com/new-postman-is-here/) | Postman Agentic 时代重装上线。Agent Mode 自动化多步 API 工作流。MCP 集成，多协议支持（HTTP、GraphQL、gRPC、MCP、WebSocket）。CLI 可在 CI 中运行 collection/test/mock。 |
| [科大讯飞 SkillHub](https://github.com/iflytek/skillhub) | 科大讯飞出品的企业级自托管 Agent Skill 注册中心。Skill 包发布与版本管理、RBAC 权限治理与审计日志、Docker/K8s 私有化部署。 |
| [CLI-Anything](https://github.com/HKUDS/CLI-Anything) | 自动将任何软件转化为 Agent 可控的 CLI。7 阶段流水线：分析 → 设计 → 实现 → 测试 → 文档 → 发布。已验证 GIMP、Blender、LibreOffice、OBS Studio、Audacity 等 11 个应用。11K+ stars。 |
| [OpenCLI](https://github.com/jackwener/opencli) | 将任何网站变成 CLI。19 个站点 80+ 命令（B站、Twitter/X、Reddit、YouTube、知乎…）。双引擎：YAML 声明式管道 + TypeScript 浏览器运行时。AI 原生发现（`explore`、`synthesize`、`cascade` 命令）。复用 Chrome 登录态。 |

## Agent 原生 CLI

> 在 OpenClaw 时代，任何 CLI 都是潜在的 Agent 工具。我们优先收录**主动为 Agent 优化**或**被 Agent 高频使用**的 CLI。[（为什么 CLI 比 MCP 更适合 Agent）](https://ejholmes.github.io/2026/02/28/mcp-is-dead-long-live-the-cli.html)

| 项目 | 描述 |
|------|------|
| [Terminalwire](https://terminalwire.com/) | 通过 WebSocket 将服务端 CLI 应用流式传输给用户。几天内为你的 SaaS 发布一个 CLI——Agent（和人类）通过终端而非 Web UI 交互。 |
| [Dreamer](https://blog.singleton.io/posts/2026-02-17-introducing-dreamer/) | 定位为"被 Agent 使用多于被人类使用"的 CLI 平台。内置构建、验证、测试和部署的完整工具链——全程无需打开 GUI。 |
| [Polymarket CLI](https://github.com/Polymarket/agents) | Polymarket 官方 CLI + Agent 框架，用于预测市场自主交易。Agent 查询市场、检索新闻、用 LLM 推理，通过命令行执行交易。 |
| [agent-browser](https://github.com/vercel-labs/agent-browser) | Vercel 出品的 AI Agent 浏览器自动化 CLI。Rust 构建，18K+ stars。结构化输出专为 Agent 消费设计，是 shell 访问的浏览器对应物。 |
| [Google Workspace CLI](https://github.com/googleworkspace/cli) | Google 官方 CLI，覆盖 Drive、Gmail、Calendar、Sheets、Docs、Chat、Admin 等。Rust 构建，从 Discovery API 动态生成。**内置 AI Agent Skills。** |
| [bb-browser](https://github.com/epiral/bb-browser) | 浏览器自动化 CLI，让 Agent 使用你的**真实 Chrome**——复用已有登录态、Cookies，无自动化指纹。通过 `chrome.debugger` API 操作。 |
| [gh (GitHub CLI)](https://github.com/cli/cli) | GitHub 官方 CLI。不是为 Agent 构建的，但却是 Agent 使用最多的 CLI——PR、Issue、代码审查、仓库管理。"CLI 即 Agent 接口"的典范。 |
| [agent-clip](https://mp.weixin.qq.com/s/kK9BdEDORWzx-Pb_Ie_36Q) | 单工具 Agent 架构：一个 `run(command)` 取代庞杂的工具目录。基于 Unix 哲学——管道、链式执行、渐进式 `--help`、错误引导导航、双层执行/呈现架构。"CLI is all agents need" 理念的最完整实现。 |
| [Jina CLI](https://github.com/jina-ai/cli) | Jina AI 全套 API 的 Unix CLI 封装 — `jina search`、`jina read`、`jina embed`、`jina rerank`、`jina pdf` 等。支持管道组合（`curl ... \| jina embed`）。Agent 只需 `run(command="jina search ...")` 即可调用全部能力。 |
| [Context7 CLI (ctx7)](https://github.com/upstash/context7) | 24,000+ 库的实时文档查询 CLI。`ctx7 docs /vercel/next.js "app router"` 直接获取最新文档注入 Agent 上下文。内置 Skill Wizard，可生成和发布可复用的 Agent Skill。 |
| [Kraken CLI](https://github.com/krakenfx/kraken-cli) | 首个 AI 原生加密货币交易 CLI。134 条命令覆盖现货、期货、质押和 WebSocket 流。Rust 单二进制文件，NDJSON 输出，内置 MCP 服务器，模拟交易沙箱。附带 50 个 Agent Skill。 |
| [xiaohongshu-cli](https://github.com/jackwener/xiaohongshu-cli) | 小红书 CLI — 搜索、阅读、互动、发帖。附带 SKILL.md 供 Agent 集成。同一作者的[系列项目](https://github.com/jackwener)还包括 bilibili-cli、twitter-cli、discord-cli、tg-cli。 |
| [twitter-cli](https://github.com/jackwener/twitter-cli) | Twitter/X CLI — Feed、书签、用户时间线、发帖。结构化 YAML/JSON 输出，附带 SKILL.md。与 xiaohongshu-cli 同一作者。 |
| [xurl](https://github.com/xdevplatform/xurl) | **X/Twitter 官方 CLI。** 专为 Agent 优化：action chaining、SKILL.md、OpenClaw 集成。OAuth 1.0a/2.0、流式传输、自动分页、限速重试。`npm i -g @xdevplatform/xurl` |
| [bird](https://github.com/steipete/bird) | 快速 X/Twitter CLI — 发推、回复、读时间线、搜索、提及。使用 GraphQL API + 浏览器 Cookie 认证。支持图片/GIF/视频上传。在 Agent 自动化工作流中广泛使用。 |
| [Resend CLI](https://github.com/resend/resend-cli) | Resend 官方邮件 CLI，53 条命令覆盖邮件发送、域名管理、API Key、受众、联系人和群发。为人类、AI Agent 和 CI/CD 构建。Resend 是 Claude Code 的默认邮件选择（63%）。 |
| [ElevenLabs CLI](https://github.com/elevenlabs/cli) | ElevenLabs 官方语音 Agent CLI——**默认 Agent-first**（非交互式），人类模式需加 `--human-friendly` 标志。以代码方式管理语音 Agent，CI/CD 部署，内置客服/助手等模板。`npm i -g @elevenlabs/cli` |
| [OfficeCLI](https://github.com/iOfficeAI/OfficeCLI) | 世界首个专为 AI Agent 设计的 Office 套件。通过 CLI 读写 Word/Excel/PowerPoint。单二进制文件，无需安装 Office。`--json` 输出、PPT 实时 HTML 预览、常驻模式、批量操作。 |
| [shadcn/ui CLI v4](https://ui.shadcn.com/) | shadcn/ui 的 Agent 时代 CLI 更新。附带 `shadcn/skills` 支持 AI Agent 集成和设计系统预设。Claude Code 默认 UI 组件选择（90%）。 |
| [Visa CLI](https://github.com/nicktomlin/visa-cli) | **Visa Crypto Labs 实验性 CLI**，为 AI Agent 支付打造。Agent 从终端发起卡支付，无需 API Key——降低凭证暴露风险。2026年3月 Beta。 |
| [Ramp CLI](https://ramp.com/) | Ramp 的 Agent 财务 CLI。生成 Agent Card 凭证、管理费用、自动化审批。集成 Ramp Policy Agent 实现低风险费用自主审批。 |
| [Kapso CLI](https://kapso.ai/) | 给 Agent 一个 WhatsApp 号码。官方 Meta Cloud API，无封号风险。`kapso login && kapso whatsapp messages`。附带 SKILL.md。2 分钟接入 30 亿 WhatsApp 用户。 |
| [Discrawl](https://github.com/steipete/discrawl) | steipete 的 Discord CLI，SQLite 后端。同步频道、搜索消息、按作者/时间筛选。Go 单二进制。同作者还有 bird（Twitter CLI）。 |
| [飞书 CLI (feishu-cli)](https://github.com/riba2534/feishu-cli) | 飞书全功能 CLI——文档、知识库、表格、消息、日历、任务。**11 个 SKILL.md** 供 AI Agent 使用。Markdown ↔ 飞书文档无损转换（40+ 块类型）。万行级并发管线处理。 |
| [阿里云 Data Agent Skill](https://github.com/aliyun/data-agent-skill) | 阿里云官方 Agent 数据分析技能。自然语言查询 DMS 数据库、CSV/Excel/JSON 文件分析、异步执行与会话隔离。 |
| [网易云音乐 Agent Skills](https://github.com/NetEase/skills) | 基于 `ncm-cli` 的网易云音乐 Agent 技能包。搜索、歌单管理、个性化推荐。流程：理解需求 → 分析偏好 → 搜索策略 → 执行 → 筛选 → 语义化推荐。附带 3 个 SKILL.md。 |
| [Stripe CLI](https://github.com/stripe/stripe-cli) | Stripe 官方 CLI，用于构建、测试和管理支付集成。Agent 用它来自动化支付工作流、测试 Webhook 和探索 API。 |

## 运行时与沙箱

> Agent 的安全代码执行和浏览器环境。

| 项目 | 描述 |
|------|------|
| [E2B](https://github.com/e2b-dev/e2b) | Agent 的云端沙箱环境。隔离的虚拟计算机，Agent 可执行代码、访问文件系统、运行终端命令。超低启动延迟，可扩展至数千实例。 |
| [Browserbase](https://www.browserbase.com/) | Agent 的无服务器云浏览器。并行启动浏览器实例，内置验证码破解、代理支持和实时会话回放。集成 Puppeteer、Playwright 和 Selenium。 |
| [Steel](https://github.com/nicholasgriffintn/steel-browser) | 开源浏览器 API，赋予 Agent 在网页上的"眼睛和手"。完整的浏览器控制、会话管理、代理支持和反检测能力。 |
| [Stagehand](https://github.com/browserbase/stagehand) | Browserbase 出品的 AI 浏览器自动化框架。原子操作（`act`、`extract`、`observe`）+ Agent 模式做高层决策。v3 快 44%，驱动无关，多语言支持。 |
| [Deno Sandbox](https://deno.com/blog/deno-sandbox) | AI 生成代码的安全沙箱。Firecracker 微虚拟机，独立文件系统、网络和进程空间。防 prompt 注入，专为 Agent 工具执行设计。 |
| [ERP (Ephemeral Runtime Protocol)](https://github.com/anthropics/erp) | 为 Agent 管理临时代码执行环境的轻量协议，无状态设计，任务完成即销毁，补充 MCP 的运行时生命周期管理。 |

## 可观测性

> Agent 行为的监控、追踪与调试。

| 项目 | 描述 |
|------|------|
| [Langfuse](https://github.com/langfuse/langfuse) | 开源 LLM 可观测性平台。追踪查看、Prompt 版本管理、成本跟踪和评估。支持自托管，满足严格数据治理需求。 |
| [Arize Phoenix](https://github.com/Arize-ai/phoenix) | 开源可观测性平台，内置聚类和漂移检测。生产环境中使用 LLM-as-a-judge 对相关性、毒性和准确性评分。 |
| [Entire CLI](https://github.com/entireio/cli) | Agent 会话版本控制。在独立 Git 分支上捕获 prompt、response、修改的文件和 token 用量。Agent 跑偏时可回滚到任意存档点。前 GitHub CEO 创建，$60M 种子轮。兼容 Claude Code、Gemini 等。 |

## 身份与通信

> 赋予 Agent 独立身份——邮箱、电话和通信能力。

| 项目 | 描述 |
|------|------|
| [AgentMail](https://www.agentmail.to/) | Agent 专属邮箱 API（YC S25）。每个 Agent 拥有独立邮箱地址，支持双向对话、线程回复和语义搜索。自动管理 SPF/DKIM/DMARC 认证。 |
| [Sendblue CLI](https://github.com/sendblue-api) | 给 Agent 一个 iMessage 号码。两条命令让任意 Agent 拥有独立 iMessage 身份。SMS + iMessage API，CLI-first 设置。`npm i -g @sendblue/cli && sendblue setup` |

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
| [Polygon Agent CLI](https://github.com/0xPolygon/polygon-agent-cli) | Polygon 官方链上 Agent 工具包。钱包创建、稳定币转账、Swap、跨链桥、身份注册（ERC-8004）和信誉系统——全部通过 CLI。集成 LangChain、CrewAI 和 Claude。 |
| [AgentCard](https://agentcard.sh/) | Agent 专属预付虚拟 Visa 卡。通过 CLI 充值发卡，将卡号/CVV 交给任意 Agent，全球 Visa 商户可用。支持按 Agent/任务设定消费限额。提供 MCP 集成。 |
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
| [GitHub Agent HQ](https://github.blog/news-insights/company-news/welcome-home-agents/) | GitHub 的 Agent 舰队统一"指挥中心"。在一个界面编排 Anthropic、OpenAI、Google、Cognition、xAI 的 Agent。跨仓库分配任务、实时会话日志、企业级治理。 |
| [Dapr Agents](https://github.com/dapr/dapr-agents) | CNCF 出品的生产级 Agent 框架（v1.0 GA 2026年3月）。持久化工作流、状态管理、虚拟 Actor 模式实现有状态 Agent。基于 Dapr 分布式运行时，NVIDIA 合作。 |
| [Linear Agent](https://linear.app/changelog/2026-03-24-introducing-linear-agent) | 内置于 Linear 的 AI Agent，理解工作区上下文（路线图、Issue、代码）。通过 App、Slack、Teams 访问。可复用 Skill、自动分流、MCP 服务器支持分页。代码智能即将上线。 |

## 组织与基金会

> 推动 Agent 开放生态的组织。

| 组织 | 描述 |
|------|------|
| [AAIF (Agentic AI Foundation)](https://www.linuxfoundation.org/) | Linux Foundation 旗下基金会，推动 Agentic AI 开放生态，初始贡献包括 MCP、goose、AGENTS.md。 |

---

## 相关阅读

> 探讨 "X for Agents" 领域及其趋势的文章。

| 文章 | 作者 | 核心观点 |
|------|------|---------|
| [MCP is dead. Long live the CLI](https://ejholmes.github.io/2026/02/28/mcp-is-dead-long-live-the-cli.html) | Eric Holmes | CLI 工具可能是比 MCP 更好的 Agent 接口——更简单的认证、无运行时进程、久经考验。 |
| [Markdown for Agents](https://blog.cloudflare.com/markdown-for-agents/) | Cloudflare | 互联网需要一个机器可读层。HTTP 内容协商可以直接给 Agent 返回 Markdown，减少约 80% token。 |
| [The AI Agent Tech Stack](https://www.cbinsights.com/research/report/artificial-intelligence-top-startups-2025/) | CB Insights | 绘制了支撑自主 AI 的基础设施全景图——从记忆到支付到评测。 |
| [Big Ideas 2026](https://a16z.com/big-ideas-2026/) | a16z | 基础设施必须进化以应对 "Agent 速度" 的工作负载——并发、递归、突发——当前系统会将其误判为攻击。 |
| [The MCP vs. CLI Debate Is the Wrong Fight](https://medium.com/@tobias_pfuetze/the-mcp-vs-cli-debate-is-the-wrong-fight-a87f1b4c8006) | Tobias Pfuetze | CLI 优先适合个人基础设施，MCP 适合企业采用——真正的问题是上下文，不是协议。 |
| [What Claude Code Actually Chooses](https://amplifying.ai/research/claude-code-picks/report) | Amplifying.ai | 2,430 次提示词揭示 Claude Code 的默认技术栈。Agent 倾向造轮子而非买服务（20 个类别中 12 个选择 DIY）。GitHub Actions 94%、Stripe 91%、shadcn/ui 90%。如果你的工具不在 Agent 的默认选项里，你就是隐形的。 |
| [Why AI Agents Build Instead of Buy](https://chatbotkit.com/reflections/why-ai-agents-build-instead-of-buy) | ChatBotKit | Agent 更喜欢写代码而非引入依赖——因为对 AI 来说"代码是免费的，依赖不是"。 |
| [CLI is All Agents Need — *nix Agent 设计宝典](https://mp.weixin.qq.com/s/kK9BdEDORWzx-Pb_Ie_36Q) | agent-clip | 一个 `run(command)` 就够了。Unix 的"一切皆文本流" = LLM 的"一切皆 token"。渐进式 --help、错误引导导航、双层架构。 |
| [我们也许不该再投资 GUI 思维的软件公司](https://mp.weixin.qq.com/s/NZSPWSvQoonU0XK7t2Jt6w) | 真格基金（钟天杰） | GUI 是人类认知缺陷的补丁，Agent 不需要它。最有价值的软件公司是成为 Agent 工作流里默认协议的公司。"Software as Protocols"——靠成为标准来竞争，而非靠更好看。 |
| [Agent 友好 CLI 的 7 条原则](https://x.com/trevin/status/2037250000821059933) | Trevin (Compound Engineering) | 缺失的 Agent CLI 设计规范：默认非交互式、结构化输出、可操作的错误信息、安全重试、渐进式帮助、可组合结构、有界响应。按严重度分级（阻塞/摩擦/优化），不是简单通过/失败。 |

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
