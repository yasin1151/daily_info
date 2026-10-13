
已完成扫描、抓取、API 交叉核验，并标记已读。以下是今日推送。

---

# GitHub Trending 日报 · 2026-10-14

来源：GitHub Trending Daily（今日 9 个项目，其中 **3 个为新上榜**：debpalash/VoiceStudio、vercel-labs/skills、xtool-org/xtool）。star 数据取自 Trending 页面，总量已用 GitHub API 交叉核验一致。已通过 blogwatcher 标记本次新条目标记为已读（该源当前无未读）。

## 今日焦点

**1. morluto/rea — 用 Agent 逆向一切的通用逆向工程台**
- 简介：把 LLM Agent 接进逆向工程链路，从 App 行为分析一路下探到原生二进制。内置 Ghidra / Hopper 反编译对接、MCP 协议、Claude Code 与 Codex 集成，覆盖二进制分析、CTF、静态分析。TypeScript。
- 为什么值得关注：单日 +54,706 star，连续第二天登顶且增速还在放大（昨日 +45,495）。「AI Agent 做逆向」已经从零散脚本变成完整工具链，安全 / CTF 社区的关注焦点。
- Stars：205,934（今日 +54,706）
- 链接：https://github.com/morluto/rea

**2. debpalash/VoiceStudio — 全本地、开源的 ElevenLabs 替代品【新上榜】**
- 简介：Python 写的本地优先语音工作台，支持声音克隆、声音设计、视频配音、听写、转写、有声书制作，号称覆盖 **646 种语言**。topics 里带 cuda / mlx / tauri，即 GPU 与 Apple 芯片双路线都做了适配，也提供简中 / 日文 README。
- 为什么值得关注：+2,277 star。「配音 / 克隆 SaaS 太贵 + 数据不能出厂」是当下最硬的本地化需求，这类项目一旦把多语言 + 本地推理做通，替代商业 API 的现实价值很高。
- Stars：63,158（今日 +2,277）
- 链接：https://github.com/debpalash/VoiceStudio

**3. storytold/artcraft — 面向艺术家/设计师/影视人的 AI 创作引擎**
- 简介：Rust 编写的「有意图的创作引擎」，主打 AI 图像与视频生成工作流，偏影视级内容生产。
- 为什么值得关注：+4,078 star，今日增速第三。Rust 实现 + 本地优先，在「AI 视频」赛道里属于少数性能导向的方案，适合关注生成式内容管线的人。
- Stars：25,559（今日 +4,078）
- 链接：https://github.com/storytold/artcraft

**4. mksglu/context-mode — AI 编码 Agent 的上下文窗口优化中间层**
- 简介：把工具输出丢进沙箱（体积约减少 98%）、持久化会话记忆，并通过 MCP + hooks 在 17 个平台（Claude Code、Codex、Copilot、Cursor、OpenCode、Zed、Kiro 等）做路由。
- 为什么值得关注：+978 star，连续上榜。上下文膨胀是编码 Agent 的头号工程痛点，做成跨平台 MCP 中间层是很务实的解法，插件生态越散它越有价值。
- Stars：28,197（今日 +978）
- 链接：https://github.com/mksglu/context-mode

**5. cathrynlavery/diagram-design — 给编码 Agent 用的「编辑级」图表生成技能**
- 简介：为 Claude Code、Codex、GitHub Copilot、Cursor、Factory Droid、Pi 提供 44 种图表类型，输出自包含 HTML + SVG。作者口号很直白：No shadows, no Mermaid slop。
- 为什么值得关注：+1,813 star。Agent Skill 生态正从「能写代码」扩到「能出可交付的设计稿」，这类审美向 skill 是清晰的风向标。
- Stars：54,044（今日 +1,813）
- 链接：https://github.com/cathrynlavery/diagram-design

**6. vercel-labs/skills — 开放 Agent Skills 生态的官方 CLI【新上榜】**
- 简介：**Vercel Labs 官方出品**的 skills 命令行工具（`npx skills add vercel-labs/agent-skills`），支持 OpenCode、Claude Code、Codex、Cursor 以及另外 **75 个 Agent**，可安装使用、也可不安装直接生成 prompt。
- 为什么值得关注：+187 star，量不大但信号强。大厂正式下场做「跨 Agent 的技能包管理器」，意味着 Agent Skills 正在被标准化成一个可分发、可复用的软件包生态——这是本轮 Agent 浪潮里最值得盯的基建方向之一。
- Stars：34,469（今日 +187）
- 链接：https://github.com/vercel-labs/skills

**7. lyogavin/airllm — 单张 4GB 显卡跑 2.8T 参数大模型**
- 简介：老牌分层加载推理项目回暖，主打单张 4GB GPU 完成 2.8T 级 LLM 推理。
- 为什么值得关注：+1,004 star。显存仍是硬约束，「小卡跑大模型」的低成本思路被反复重新发现，适合成本敏感的自部署场景。
- Stars：38,298（今日 +1,004）
- 链接：https://github.com/lyogavin/airllm

## 首次上榜

**8. xtool-org/xtool — 跨平台 Xcode 替代品**
- 简介：用开放标准在 Linux / Windows(WSL) / macOS 上复刻 Xcode 功能，把 SwiftPM package 构建成 iOS App、签名安装，并能以程序化方式对接 Apple Developer 服务。
- 为什么值得关注：+1,182 star。它把「开发 iOS 必须买 Mac」这道门槛拆掉，对 CI 成本和跨平台团队是实打实的解放；属于开发工具而非 AI，但今日新上榜里最实用。
- Stars：9,299（今日 +1,182）
- 链接：https://github.com/xtool-org/xtool

---

**附注（非 AI，仅作趋势参考）**：`bilawalsidhu/gods-eye-view`（★55,318，+1,961）——浏览器里的开源「间谍卫星模拟器」，用真实数据在 3D 地球上做开放空间情报（OSINT / 遥感）。

**榜单变动**：较昨日离榜 3 个 —— `Alishahryar1/free-claude-code`、`open-webui/open-webui`、`microsoft/BitNet`；新进 3 个 —— VoiceStudio、vercel-labs/skills、xtool。核心结构没变：**逆向 Agent（rea）+ Agent 周边基建（context-mode / diagram-design / vercel skills）已连续两日占据半壁江山**。
