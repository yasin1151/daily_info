
GitHub Trending 每日热门 AI 项目 · 2026-10-09

数据源：GitHub Trending（daily）+ GitHub API 核对。今日上榜 9 个项目，其中 6 个属 AI / Agent / LLM / 开发工具方向。

一、AI / Agent / LLM 重点项目

1. morluto/rea — 用 Agent 逆向一切
简介：TypeScript 写的逆向工程 CLI，让 AI Agent 从应用行为一路分析到原生二进制：反编译、反汇编、静态分析，集成 Ghidra / Hopper，通过 MCP 协议接入 Claude Code、Codex 等。
为什么值得关注：把「逆向工程」这块传统硬核安全活直接内置成 Agent 能力，今日 +7,744 stars，是榜单涨幅第二、含金量最高的一条。安全 / CTF 人群开始真用，说明「Agent 干专业垂直活」已从演示进入实战。
Stars：25.6k（今日 +7,744） | https://github.com/morluto/rea

2. thedotmack/claude-mem — 给所有 Agent 装长期记忆
简介：捕获 Agent 会话全过程，用 AI 压缩成记忆，再在后续会话中注入相关上下文；兼容 Claude Code、OpenClaw、Codex、Gemini、Hermes、Copilot、OpenCode。
为什么值得关注：正面解决「每次新会话都失忆」的核心痛点，是本轮 agent memory 赛道（mem0 / supermemory / RAG）的集大成者，且明确点名支持 Hermes，可直接参考落地。
Stars：98.4k（今日 +662） | https://github.com/thedotmack/claude-mem

3. mattpocock/skills — 真实工程师的 Agent 技能库
简介：知名 TypeScript 教育者 Matt Pocock 公开自己 .agents 目录里的整套技能集合（Shell）。
为什么值得关注：28 万 stars、今日 +1,770，是榜单里体量最大的项目。它标志「Agent 技能（agent skills）」已成为新的分发单位——头部从业者的个人技能目录被大规模复用。值得拿去和自己的 skill 库对照查漏。
Stars：281k | https://github.com/mattpocock/skills

4. cathrynlavery/diagram-design — 给编码 Agent 的画图技能
简介：面向 Claude Code / Codex / Copilot / Factory Droid / Pi 的图表设计技能，42 种图类型，输出自包含 HTML+SVG，宣传语是 “No Mermaid slop”（不搞 Mermaid 那种糊成一团的图）。
为什么值得关注：切中「AI 生成的架构图又丑又不可编辑」这个真实痛点，用纯 SVG 绕开 Mermaid 的排版灾难，做技术文档 / 汇报很实用。
Stars：46.3k（今日 +1,163） | https://github.com/cathrynlavery/diagram-design

5. anthropics/knowledge-work-plugins — Anthropic 官方知识工作插件集
简介：Anthropic 开源的插件仓库，面向知识工作者在 Claude Cowork 中使用（Python）。
为什么值得关注：官方出品、2026-01 建库至今仍高频更新，是观察 Anthropic 如何定义「插件生态 / 知识工作场景」的一手材料，也是自家 plugin / skill 设计的对标样板。
Stars：27.5k（今日 +309） | https://github.com/anthropics/knowledge-work-plugins

6. storytold/artcraft — 面向创作者的 AI 影像 / 3D 引擎（今日 blogwatcher 新发现）
简介：Rust 写的 “intentional crafting engine”，面向艺术家、设计师、电影人，标签含 3D 图形、AI 视频、图像生成。
为什么值得关注：今日 +2,510 冲进榜单，是少数用 Rust 做 AI 生成 + 3D/影视创作的引擎型项目，代表「AI 原生内容生产工具」方向；2022 年建库、长期迭代，不是蹭热点的短期项目。
Stars：7.8k（今日 +2,510） | https://github.com/storytold/artcraft

二、其他上榜（非 AI，简记）
- boykopovar/AnyPS5 — 自动把 PS5 可执行文件移植到 Linux/Windows（C++，今日 +4,640，总榜涨幅第一），涉及 Vulkan / SPIR-V，游戏移植工具链。https://github.com/boykopovar/AnyPS5
- EpicGames/raddebugger — Epic 官方开源的原生用户态、多进程图形调试器（C，+283）。https://github.com/EpicGames/raddebugger
- liquidslr/system-design-notes — 《System Design Interview》读书笔记（+398）。https://github.com/liquidslr/system-design-notes

三、一句话观察
今日榜单由「Agent 技能 / Agent 专业能力」霸榜：rea（Agent 做逆向）、mattpocock/skills（技能分发）、claude-mem（Agent 记忆）、diagram-design（Agent 画图）四条同源，加上 Anthropic 官方插件集，指向同一个趋势——竞争焦点已从「模型多强」转向「给 Agent 配什么技能和记忆」。唯一非 Agent 的高增长是 PS5 移植工具和 Rust 创作引擎，属独立热点。

已标记 blogwatcher 中 GitHub Trending 条目为已读。
