
GitHub Trending 每日速览 · 2026-09-29（周二）

本期日榜共 8 个项目，其中 AI/Agent 相关 5 个。今天榜单的公共主题很集中：全是"给 agent 配套的基础设施"，模型本身的新项目一个没上。

---

**1. Paperclip —— AI 智能体的"公司操作系统"**
- 简介：Node.js 服务端 + React 前端的开源智能体编排平台。自述"如果 OpenClaw 是一名员工，Paperclip 就是整家公司"。你带入自己的 agent，指派目标，在一个看板里跟踪工作和成本；底层是组织架构图、预算、治理和目标对齐。
- 为什么值得关注：92.7k stars、15.9k forks，但 open issues 高达 5,987 —— 热度极高、维护压力也极大。它代表一个明确转向：从"跑单个 agent"到"管一支 agent 团队 + 预算 + 治理"，把 LLM 编排包装成企业管理系统卖。
- Stars：92.7k（+3,185 今日）｜TypeScript｜MIT
- https://github.com/paperclipai/paperclip

**2. Hindsight —— 让 Agent"会学习"的记忆系统**
- 简介：Agent 记忆层，主打"学习"而不只是"记住对话历史"。官方直接说要绕开 RAG 和知识图谱的短板，自称在长程记忆基准上达到 SOTA；提供 Python/Node 客户端、集成库、cookbook、论文（arXiv 2512.12818），另有托管云版。
- 为什么值得关注：今日 +4,413 stars，本期涨幅第一。记忆是 agent 落地公认的瓶颈（上下文贵、RAG 召回不准），这个项目把"从历史里检索"升级成"从经验里学习"，且有论文和公开 benchmark 兜底——但这类自评 SOTA 需要用它的 benchmarks.hindsight.vectorize.io 自己复现，别只信 README。
- Stars：40.9k（+4,413 今日）｜Python｜MIT
- https://github.com/vectorize-io/hindsight

**3. OpenRig —— 把 Claude Code 和 Codex 编成一支团队**
- 简介：用 YAML 定义 agent 团队，一条命令启动。核心表述是"harness 包裹模型，rig 包裹你的 harness"：Claude Code 和 Codex 跑在同一个 rig 里当一套系统管；你跟一个 lead agent 谈目标，它去协调跨团队专家，把需要你拍板的决策汇总回来。依赖 Node 22/24 + tmux，macOS/Linux。
- 为什么值得关注：本期唯一专注"多编码 agent 协同"的工具，正撞上当下双持 Claude Code + Codex 的开发者痛点。注意它会在你机器上写入 provider hooks 和 workspace trust 配置，README 自己提醒先备份、先跑 `rig setup --dry-run`；1,693 stars、仅 10 个 watcher，属于早期尝鲜项目。
- Stars：1.7k（+781 今日，日增占总量 46%）｜TypeScript｜Apache-2.0
- https://github.com/mvschwarz/openrig

**4. Univer —— 给 AI Agent 准备的 Office 运行时**
- 简介：高性能可定制的 Office SDK，把表格、文档、幻灯片、Base、看板、PDF 收进同一个运行时；插件架构 + Canvas 渲染 + 公式引擎，一套 Facade API 同时跑浏览器和 Node.js。本期定位语已改成 "The Office Harness for AI Agents"。
- 为什么值得关注：2022 年的老项目，重新包装成 agent 基础设施后再次上榜（+1,105 stars）。它解决的是 agent 交付真实职场文件（xlsx/docx/pptx）这条路——现在大多数 agent 只会吐 Markdown，而企业要的是能直接发的 Office 文件。想做 agent 办公产出，这是底层件。
- Stars：21.2k（+1,105 今日）｜TypeScript｜Apache-2.0
- https://github.com/dream-num/univer

**5. VoiceStudio —— 全本地的 ElevenLabs 替代品**
- 简介：开源、完全本地跑的语音工作台：声音克隆、音色设计、视频配音、听写、转录、有声书制作，覆盖 646 种语言。默认引擎 k2-fsa/OmniVoice，可换引擎；Electron 桌面端 + 浮窗听写，提供本地 API 和 MCP 接口供 agent 调用，可选远程 worker。
- 为什么值得关注：今日 +3,274 stars。在语料隐私敏感 + 成本敏感的场景下，"本地 TTS/克隆 + 给 agent 开 MCP 口"是很明确的组合拳，支持 MLX/CUDA，Mac 上能跑。但协议是 AGPL-3.0，闭源商业集成前要评估合规成本。
- Stars：43.9k（+3,274 今日）｜Python｜AGPL-3.0
- https://github.com/debpalash/VoiceStudio

---

**其余上榜（非 AI 向，简记）**
- cs341-illinois/coursebook（TeX，2.5k，+316）：伊利诺伊大学 CS341 系统编程开源教材
- byoungd/up（JavaScript，64.6k，+310）：中文"人生进阶指南"，含 AI 学习/英语学习路线
- NawfalMotii79/PLFM_RADAR（25.7k，+145）：开源低成本 10.5 GHz 相控阵雷达系统

数据已核对：stars/forks 通过 GitHub API 二次校验，与 trending 页面一致；blogwatcher 的 2 条未读（coursebook、up）已标记为已读。
