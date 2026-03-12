# Agent 工具接口概念指南

> 本文梳理 API、CLI、Skill、MCP 等概念在 AI Agent 语境下的关系与差异，帮助你理解为什么这个列表如此分类。

---

## 一句话总结

**API 是原材料，CLI 是半成品，Skill 是成品。** Agent 越聪明，越能直接用原材料；但用半成品效率更高。

```
底层                                                  高层
API (curl + HTTP)  →  CLI (封装好的命令)  →  Skill (完整的工作流)
     灵活但繁琐         开箱即用              一键完成任务
```

---

## API vs CLI：不只是封装

### 表面差异

| | curl + API | CLI |
|---|---|---|
| 认证 | 自己拼 Header、Token | `gh auth login` 一次搞定 |
| 分页 | 自己处理 `next_page` | 内部处理 |
| 错误 | 自己解析 HTTP 状态码和 JSON | 人/机可读的错误信息 |
| 输出 | 原始 JSON | 格式化 + `--json` 可选 |

### 深层差异：CLI 是 LLM 的母语

这才是关键。LLM 的训练数据里，CLI 是**最密集的工具使用范式**：

- GitHub 上数十亿行代码充满 `pip install && python main.py`
- CI/CD 脚本全是 `make build && make test && make deploy`
- Stack Overflow 的解决方案都是 `cat /var/log/syslog | grep "Out of memory" | tail -20`

LLM 不需要学 CLI——**它已经会了**。

对比完成同一个任务：

```
任务：找出日志里的错误行数

函数调用方式（3 次 tool call）：
  1. read_file(path="/var/log/app.log")
  2. search_text(text=<entire file>, pattern="ERROR")
  3. count_lines(text=<matched lines>)

CLI 方式（1 次 tool call）：
  run(command="cat /var/log/app.log | grep ERROR | wc -l")
  → "42"
```

一次调用替代三次。不是特殊优化——是 Unix 管道天然支持组合。

### 更深的哲学共鸣

Unix 在 50 年前的设计决策：**一切皆文本流**。程序之间通过文本管道沟通，小工具各司其职，`|` 组合成工作流。

LLM 在 50 年后的设计决策：**一切皆 token**。它只理解文本，只输出文本。

两个决策跨越半个世纪，从完全不同的出发点，**收敛到了同一个接口模型**。Unix 为人类终端操作者设计的文本系统，对 LLM 来说不是"也能用"，而是天然适配。

> 参考阅读：[CLI is All Agents Need](https://mp.weixin.qq.com/s/kK9BdEDORWzx-Pb_Ie_36Q)

---

## CLI vs MCP：不是非此即彼

MCP（Model Context Protocol）和 CLI 解决的是不同层面的问题：

| | CLI | MCP |
|---|---|---|
| 本质 | 执行命令，返回文本 | 标准化的工具发现和调用协议 |
| 优势 | 零学习成本、管道组合、训练数据丰富 | 结构化 schema、类型安全、企业级 |
| 适合 | 个人开发、Agent 自主执行 | 企业集成、多 Agent 协作 |
| 认证 | 系统级（SSH key、token 文件） | 协议级（OAuth、API key） |

实际使用中，两者是互补的：

- **CLI 优先**：Agent 日常操作（文件、Git、部署）用 CLI
- **MCP 桥接**：需要结构化数据交换或跨组织协作时用 MCP
- **CLI over MCP**：一些项目把 CLI 能力通过 MCP 暴露出去，两全其美

> "真正的问题是上下文，不是协议。" — Tobias Pfuetze

---

## Skill：对 CLI 的再一层封装

Skill 是一组预定义的指令、工作流和知识，打包成一个可复用的能力模块。

```
CLI 命令:  git commit -m "fix: ..."
Skill:     "帮我提交代码" → 自动 diff → 生成 commit message → 提交
```

### Skill 的三种消费者

| 消费者 | 使用方式 | 例子 |
|--------|---------|------|
| **开发者** | 本地安装 SKILL.md，Agent 自动加载 | Claude Code 的 `/skill` |
| **Agent** | 通过 API/CLI 调用 Skill 服务 | agent-clip 的 `run(command)` |
| **普通用户** | 通过网页界面使用（不知道 Skill 存在） | SkillHub、未来的 Skill 网页服务 |

### Skill 生态的现状

- **供给端**：GitHub 上已有大量 SKILL.md（Claude Code 社区、awesome-claude-skills）
- **分发端**：[SkillHub](https://skillhub.tencent.com/) 等平台做策展和分发
- **消费端**：目前主要是开发者通过 CLI 使用，普通用户的入口还在建设中

### Skill as a Service：一个可能的方向

当前 Skill 的痛点：**只有会用 CLI 的人才能用**。99% 的人不知道 SKILL.md 是什么。

一个自然的演进方向：

```
SKILL.md（GitHub 上的文件）
    ↓ 包装
网页服务（用户填表单，点"生成"）
    ↓ 执行
云端调用 Claude API + SKILL.md → 返回结果
```

用户看到的不是 Skill，而是"PPT 生成器"、"周报助手"这样的工具。

这跟 Coze/Dify 的区别：
- Coze/Dify 让你**自己搭工作流**（需要理解节点、变量、API）
- Skill as a Service 让你**直接用别人调好的 Skill**（零门槛）

---

## 单工具假说：run(command) 就够了

主流 Agent 框架给 LLM 一堆独立工具：

```
tools: [search_web, read_file, write_file, run_code, send_email, ...]
```

LLM 每次要从 15 个不同 schema 的工具中选一个——认知负荷花在了"选工具"上，而不是"解决问题"上。

[agent-clip](https://github.com/anthropics/agent-clip) 的做法：**一个 `run(command="...")`，所有能力通过 CLI 命令暴露。**

```bash
run(command="cat notes.md")                              # 读文件
run(command="cat log.txt | grep ERROR | wc -l")          # 管道组合
run(command="see screenshot.png")                        # 看图
run(command="memory search 'deployment issue'")          # 搜索记忆
run(command="clip sandbox bash 'python3 analyze.py'")    # 沙箱执行
```

命令选择是在统一 namespace 里做字符串组合——而函数选择是在多个不相关的 API 间做模式切换。前者对 LLM 来说简单得多。

### 让 CLI 自己教 Agent

好的 CLI 设计让 Agent 不需要提前学习所有文档，而是**按需发现**：

```
第零层：tool description 列出所有命令摘要
         → Agent 知道有哪些能力

第一层：command（无参数）→ 返回用法
         → run("memory") → "usage: memory search|recent|store|facts|forget"

第二层：command subcommand（缺参数）→ 返回参数格式
         → run("memory search") → "usage: memory search <query> [-t topic_id]"
```

渐进式披露：**给 Agent 一张地图，而不是一本 1000 页的说明书。**

### 错误信息即导航

传统 CLI 错误：
```
$ cat photo.png
cat: binary file (standard output)
```
人会 Google。Agent 不能 Google。

为 Agent 设计的错误：
```
[error] cat: binary image file (182KB). Use: see photo.png
```
Agent 直接调用 `see`，一步修正。

### 双层架构

```
┌─────────────────────────────────┐
│  Layer 2: LLM 呈现层             │  ← 截断、二进制拦截、元数据
├─────────────────────────────────┤
│  Layer 1: Unix 执行层             │  ← 纯 Unix 语义，管道不能截断
└─────────────────────────────────┘
```

为什么要分层？因为管道中间不能截断（否则 `grep` 只搜到前 200 行），但最终结果必须为 LLM 做裁剪（否则 5000 行日志淹没上下文）。

---

## Agent 的工具接口演进

把以上概念串起来，Agent 与外部世界交互的方式正在这样演进：

```
2023: Function Calling（结构化 JSON schema）
  → 精确但僵硬，每个工具都要定义 schema

2024: MCP（标准化协议）
  → 统一了工具发现和调用，但运行时复杂

2025: CLI-first（命令行优先）
  → 回归 Unix 哲学，LLM 天然适配

2026: Single-tool Agent（单工具 Agent）
  → 一个 run()，所有能力通过 CLI 组合
  → Skill 层为普通用户提供零门槛入口
```

这不是线性替代，而是**层层叠加**：底层 API 永远在，CLI 封装了 API，Skill 封装了 CLI，MCP 在需要标准化的地方桥接一切。

---

## 延伸阅读

- [CLI is All Agents Need — *nix Agent 设计宝典](https://mp.weixin.qq.com/s/kK9BdEDORWzx-Pb_Ie_36Q) — 为什么 `run(command)` 就够了
- [MCP is dead. Long live the CLI](https://ejholmes.github.io/2026/02/28/mcp-is-dead-long-live-the-cli.html) — CLI 作为 Agent 接口的优势
- [What Claude Code Actually Chooses](https://amplifying.ai/research/claude-code-picks/report) — Agent 的默认技术栈偏好
- [Why AI Agents Build Instead of Buy](https://chatbotkit.com/reflections/why-ai-agents-build-instead-of-buy) — Agent 为什么喜欢造轮子
