
**GitHub Trending 日报 · 2026-10-19（按今日新增 star 排序）**

今天榜单几乎是「Agent 工具链」专场：13 个上榜项目中有 11 个跟 AI 编码智能体直接相关，包括求职、插件市场、多智能体编排、跨工具记忆等环节，说明竞争已经从「谁家 agent 更强」转向「围绕 agent 的工具生态」。

**1. AI Job Search：把求职流程做成 Claude Code 框架**
简介：基于 Claude Code 的求职自动化框架，fork 后填入个人资料，即可用 `/scrape`、`/apply`、`/interview` 三个工作流完成职位抓取评估、简历改写、求职信生成和面试准备。
值得关注：作者是地球物理学家，2025 年底被裁后自己写下这套工具跑完整轮求职，全部本地运行、数据不外传。它展示了「个人垂直 agent 工作流」最容易被复制的形态。
Stars：53,044（今日 +2,213） · https://github.com/MadsLorentzen/ai-job-search

**2. VoiceStudio：完全本地化的 ElevenLabs 替代**
简介：开源本地语音工具，涵盖声音克隆、音色设计、视频配音、听写、转写和有声书制作，宣称支持 646 种语言。
值得关注：语音合成是少数还依赖云端订阅的模态，本地化意味着零按量计费和内容不外流；今日 +2,098 说明成本敏感型用户正在大规模迁移。
Stars：75,258（今日 +2,098） · https://github.com/debpalash/VoiceStudio

**3. opencode：开源编码 agent 的头部项目**
简介：TypeScript 写的开源 coding agent，终端内运行，支持多家模型供应商。
值得关注：21.6 万 star 已进入头部梯队，是目前闭源商业 agent 之外事实上的社区标准，值得作为 Claude Code 的替代或备份方案评估。
Stars：216,537（今日 +1,417） · https://github.com/anomalyco/opencode

**4. claude-plugins-official：Anthropic 官方插件市场**
简介：Anthropic 亲自维护的 Claude Code 插件目录，分内部插件和第三方合作方插件两部分，可用 `/plugin install` 直接装。
值得关注：官方亲自下场做分发渠道，意味着插件生态开始规范化；但 README 明确声明「Anthropic 不审核插件内含的 MCP server 和文件」，安全责任仍在用户，装前要看清权限。
Stars：42,654（今日 +1,187） · https://github.com/anthropics/claude-plugins-official

**5. Orca：多 agent 并行工作台**
简介：桌面、移动及远程运行时三端的 agent 编排器，可让 Codex、Claude Code、OpenCode、Pi 各占一个独立 worktree 并排跑，用你自己的订阅额度。
值得关注：解决的是「同时跑多个 agent 会互相踩文件」这个高频问题，用 worktree 做隔离是当前最务实的解法，适合已经在并行开发的团队。
Stars：96,589（今日 +1,146） · https://github.com/stablyai/orca

**6. CLI-Anything：把所有软件变成 agent 原生**
简介：港大数据智能实验室出品，为各类软件自动生成 CLI 封装，并通过 `cli-hub install` 统一分发，让 agent 能直接操作 CAD、3D、字幕、图表等工具。
值得关注：主张「明天的用户是 agent 而不是人」，思路与 MCP 互补——用 CLI 作为通用接口层，绕开每个软件单独写集成的成本。
Stars：54,570（今日 +582） · https://github.com/HKUDS/CLI-Anything

**7. ai-memory：跨 agent 的长期记忆层**
简介：Rust 实现的共享记忆服务，支持 20 多个 harness（Claude Code、Codex、Cursor、Gemini CLI、OpenCode、Devin 等）。在 Claude Code 中途退出后，换 Codex 在同一目录接着做，无需重述架构和失败过的方案。
值得关注：直击「每个 agent 的记忆都锁在自己家」这个痛点，且 handoff 是带 owner 的强类型协议、记忆存在自建服务器上，团队共享时还有审计日志，工程完整度明显高于同类玩具项目。
Stars：10,455（今日 +513） · https://github.com/akitaonrails/ai-memory

**8. ruflo：agent 元框架（原 claude-flow）**
简介：面向 Claude Code 和 Codex 的 agent meta-harness，主打多智能体 swarm 编排、自适应记忆、联邦式协作，可 `npx ruflo` 直接跑。
值得关注：老牌 claude-flow 改名重生，这类「套在 agent 外面的编排层」正在成为独立品类，但功能堆得极多，实际稳定性需要自己压测。
Stars：76,495（今日 +502） · https://github.com/ruvnet/ruflo

**9. android/skills：Google 官方的 Android agent 技能库**
简介：Google 官方的 AI 优化模块化指令集，遵循开放 agent skills 标准（SKILL.md），用 `android skills add` 装进任意 agent 目录。
值得关注：官方明确说只写「评测显示 LLM 表现不佳」的场景，不重复覆盖 Jetpack Compose 这类模型已经擅长的部分——这种按评测数据选题的做法，比无脑堆文档更值得其他厂商学。
Stars：8,752（今日 +381） · https://github.com/android/skills

**10. cursor/plugins：Cursor 的插件规范**
简介：Cursor 官方插件规范与官方插件集，TypeScript 实现。
值得关注：与 Anthropic 的插件市场同一天上榜，说明「编辑器/agent 插件标准」之战正式开打，插件作者接下来要面对多套规范并存的适配成本。
Stars：12,722（今日 +351） · https://github.com/cursor/plugins

**其他上榜**
- **ComfyUI**：本地扩散模型推理引擎，13.8 万 star，今日 +155，仍是图像生成工作流的默认底座。https://github.com/Comfy-Org/ComfyUI
- **Jasna**：本地 GPU 视频/图像修复工具，带 GUI 和 CLI，部分模型需购买授权码，今日 +115（新上榜）。https://github.com/Kruk2/jasna
- **llm-course**：mlabonne 的 LLM 入门路线图加 Colab  notebooks，8.4 万 star，今日 +81（新上榜），属于长期慢热型学习资源。https://github.com/mlabonne/llm-course

已标记 2 条新条目为已读，当前无未读积压。
