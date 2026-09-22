
已完成扫描与抓取，4 条新条目已标记已读。以下是今日报告。

---

# GitHub Trending 今日 AI / Agent 热门项目
**2026-09-19 · 共 17 个趋势项目，其中 AI 相关 15 个**

## 🔔 本轮新增（blogwatcher 首次发现，4 条）

**1. Fission-AI / OpenSpec** ⭐ 69.3k · TypeScript · 今日 +298
一句话：给 AI 编码助手用的「规格驱动开发（SDD）」框架。
简介：主张在写代码前先把需求固化成结构化 spec（PRD/规格文件），让 Claude Code、Codex 等 agent 按规格实现，而不是直接凭一句话瞎改代码。提供 spec 生成、校验、变更追踪的完整流程。
为什么值得关注：它切中的是 AI 编程最痛的「上下文工程」问题——agent 跑偏往往不是模型不行，而是需求没写清。已形成 PRD/spec/SDLC 整套话题标签，是当前 SDD 流派的代表性项目，团队要落地 agent 编码绕不开它。
https://github.com/Fission-AI/OpenSpec

**2. rustfs / rustfs** ⭐ 33.1k · Rust · 今日 +298
一句话：Rust 写的开源 S3 兼容高性能对象存储，主打替代 MinIO / Ceph。
简介：完全兼容 S3 API，支持与 MinIO、Ceph 共存和平滑迁移，标签里直接标注 `ai-native`、`ai-storage`，定位是给 AI/大数据负载做存储底座。
为什么值得关注：MinIO 收紧许可后社区一直在找替代品，Rust 重写带来更高性能与更低内存占用。对自建模型权重、数据集仓库的团队是直接可选项。
https://github.com/rustfs/rustfs

**3. ahmedkhaleel2004 / gitdiagram** ⭐ 16.5k · TypeScript · 今日 +145
一句话：把任意 GitHub 仓库一键变成可交互架构图。
简介：输入仓库地址，自动分析代码结构并生成可视化系统设计图，免费、免登录、速度快，也可本地部署。
为什么值得关注：读陌生代码库最耗时的就是建立心智模型，它把「理解一个仓库」从几小时压缩到几十秒。对接手遗留项目、评估第三方依赖特别实用，是 AI 辅助代码理解的典型产品化。
https://github.com/ahmedkhaleel2004/gitdiagram

**4. tradesdontlie / tradingview-mcp** ⭐ 6.5k · JavaScript · 今日 +64
一句话：把 TradingView 桌面端接到 Claude Code 的 MCP 服务器，做 AI 辅助看盘。
简介：通过 MCP 协议让 AI agent 读取你的 TradingView 图表，自动做技术形态分析和个人工作流自动化。
为什么值得关注：这是 MCP 生态「垂直场景化」的样本——不再是大而全的工具市场，而是把 AI agent 焊进具体专业软件（金融终端）。同类思路可复制到任何桌面专业软件。
https://github.com/tradesdontlie/tradingview-mcp

## 🔥 今日其他 AI 热门（按今日新增 stars 排序）

**cloudflare / security-audit-skill** ⭐ 13.6k · JavaScript · 今日 **+3,019**（今日涨幅第一）
Cloudflare 出的编码 agent 技能：多阶段自动安全审计，产出可独立复核、机器可读的漏洞发现。大厂亲自下场做 agent 技能（skill）是个明确信号——agent skill 正在成为新的分发格式。
https://github.com/cloudflare/security-audit-skill

**alibaba / open-code-review** ⭐ 36.6k · Go · 今日 +2,724
阿里巴巴开源的代码评审工具，混合架构：确定性流水线 + LLM Agent，能给出精确到行的评论，内置 NPE、线程安全、XSS、SQL 注入等多语言规则集，兼容 OpenAI/Anthropic。号称经阿里内部海量代码验证——「确定性规则 + LLM」是比纯 LLM 评审更靠谱的工程化路线。
https://github.com/alibaba/open-code-review

**Tencent / BrowserSkill** ⭐ 5.3k · TypeScript · 今日 +1,319
让 AI agent 直接操作你「已登录的真实浏览器」而不打断你的工作，提供 CLI + 浏览器扩展，适配任何有 shell 能力的 agent。解决了 agent 自动化的最大痛点之一：登录态和验证码。
https://github.com/Tencent/BrowserSkill

**affaan-m / ECC** ⭐ 262k · JavaScript · 今日 +965
「agent harness 性能优化系统」：技能、本能反应、记忆、安全、research-first 开发流程，通吃 Claude Code / Codex / Opencode / Cursor。26 万 star 体量说明 agent「外挂增强」需求巨大。
https://github.com/affaan-m/ECC

**asciimoo / hister** ⭐ 5.0k · Go · 今日 +842
自建个人搜索引擎，索引你的浏览器历史，支持 MCP server，主打隐私本地化。为 agent 提供「个人记忆检索」的候选方案。
https://github.com/asciimoo/hister

**addyosmani / agent-skills** ⭐ 96.4k · JavaScript · 今日 +677
Google 的 Addy Osmani 出的「生产级 AI 编码 agent 技能库」，覆盖 Claude Code / Codex / Cursor / Antigravity。工程老兵沉淀的 skill 集合，质量口碑好。
https://github.com/addyosmani/agent-skills

**TencentCloud / Octop** ⭐ 3.9k · Python · 今日 +571
自托管 AI 助手，多用户 + 多 agent，强调 local-first 与长期记忆。适合想自己掌控数据、又要有团队协作能力的场景。
https://github.com/TencentCloud/Octop

**coder / coder** ⭐ 15.3k · Go · 今日 +478
给开发者和他们的 agent 提供安全、可管控的远程开发环境（Terraform 驱动）。当 agent 开始自己写代码跑命令，「人类和 agent 共用的沙箱环境」成了刚需。
https://github.com/coder/coder

**anthropics / claude-code** ⭐ 146k · TypeScript · 今日 +442
终端里的 agentic 编码工具，理解代码库、执行常规任务、处理 git 工作流。仍是该品类基准线。
https://github.com/anthropics/claude-code

**anthropics / knowledge-work-plugins** ⭐ 24.9k · Python · 今日 +300
Anthropic 开源的知识工作者插件库（面向 Claude Cowork）。官方插件生态的起点，值得关注其插件规范。
https://github.com/anthropics/knowledge-work-plugins

**supermemoryai / supermemory** ⭐ 30.3k · TypeScript · 今日 +140
「AI 时代的记忆 API」：极快、可扩展、可完全本地运行的内存与上下文引擎。agent 长期记忆赛道的主要玩家之一。
https://github.com/supermemoryai/supermemory

---

**今日观察**：上榜项目高度集中在三个方向——① **agent 技能/外挂层**（security-audit-skill、agent-skills、ECC、OpenSpec），Cloudflare、阿里、Google、Anthropic 同时下注，skill 正在成为新的分发格式；② **agent 的「手和眼」**（BrowserSkill 真实浏览器、gitdiagram 代码理解、tradingview-mcp 垂直接入），解决 agent 与真实世界交互的最后一公里；③ **agent 时代的基础设施**（coder 沙箱环境、rustfs AI 存储、supermemory 记忆）。纯模型层的项目基本消失，趋势明确转向「把 agent 用好」的工程化配套。

（已标记 4 条新条目为已读）
