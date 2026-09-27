
**GitHub Trending 日报｜2026-09-28（07:35 CST）**

本轮扫描 GitHub Trending（daily），9 个项目上热榜，其中 3 个为本轮新增（blogwatcher 已标记已读并核验）。

---

## 一、本轮新增项目（3 条）

**1. scriptc — 把 TypeScript 直接编译成原生代码**
- 简介：Vercel Labs 的实验项目，用 TypeScript 编译器做解析与类型检查，再输出带类型的 IR、可读 C 代码、文本 LLVM IR、原生汇编/目标文件和可执行程序、WASM。macOS 15+ arm64 上普通 LLVM 层可执行文件用自带 helper + 预编译 runtime pack，clang 只当链接器，不参与编译。
- 为什么值得关注：TS 生态长期靠 Node/V8 跑，性能天花板明显。Vercel 亲自下场做 AOT 编译（不只是打包或 JIT 提示），意味着 TS 有条件进入系统层/边缘运行时。目前是 Labs 实验阶段，先观察它能否稳定产出可读 C 和干净 WASM，再考虑试水。
- Stars：5,382（今日 +186）｜语言 TypeScript｜Apache-2.0
- 链接：https://github.com/vercel-labs/scriptc

**2. OpenRig — 把 Claude Code 和 Codex 当成同一支团队来编排**
- 简介：一句话概括作者的设计：「harness 包住一个模型，rig 包住一堆 harness」。用 YAML 定义 agent 团队（含 lead agent、跨团队 specialist），一条命令启动；Claude Code 与 Codex 可同时跑在同一个 rig 里，共享工作区与上下文地址，靠 tmux 承载会话。Node 20/22/24 + tmux，`npm install -g @openrig/cli`，建议先 `rig setup --dry-run`。
- 为什么值得关注：当前多 agent 编排的痛点不是「能不能并行」，而是并行会话散落、上下文丢失、结果无人汇总。OpenRig 直接把这个当产品问题解决，并且敢于把两个互相竞争的 CLI（Claude Code / Codex）放在同一层管理，是对「agent 团队」这一形态的正面实验。注意它会写 provider hooks 和工作区信任设置，先在非关键仓库试用。
- Stars：937（今日 +114）｜语言 TypeScript｜topics 含 agent-orchestration、multi-agent、codex-cli
- 链接：https://github.com/mvschwarz/openrig

**3. Madeira — 未越狱 iPhone 上跑 Windows PC 游戏（非 AI，附记）**
- 简介：Wine（ARM64EC）+ FEX-Emu（x86-64→ARM64 翻译）+ DXMT（D3D11→Metal）合成单个 Mach 进程，wineserver 作为线程而非独立进程。Thumper、ULTRAKILL 已可玩，Marvel Cosmic Invasion 能进游戏但控制不稳、出现过无解释退出。需要 JIT，因而必须挂调试器（用 StikDebug），无法上架 App Store，只能侧载；免费 Apple ID 的 profile 7 天过期需每周重装（容器保留存档）。
- 为什么值得关注：把 x86 Windows 游戏栈整体搬到 iOS 这件事，工程上比多数 AI demo 更硬核；但它明确是研究项目而非产品，且依赖每周重签，实用价值有限，当作技术路标看即可。
- Stars：798（今日 +117）｜语言 C
- 链接：https://github.com/willfaust/Madeira

---

## 二、热榜上的 AI/Agent 项目（本轮已知，未变更）

**4. paperclipai/paperclip — 团队里管 agent 的开源应用**
- 简介：TypeScript 写的开源应用，定位是「大家用来在办公场景里管理 agent」的统一入口。
- 为什么值得关注：Stars 已近 9 万、今日仍 +2,527，说明「agent 治理/编排控制台」是当前最拥挤也最有真实需求的方向——从个人玩 CLI 转向组织内统一管理，已是明确趋势。topics 为空、README 极简，实际能力需要自测。
- Stars：89,755（今日 +2,527）
- 链接：https://github.com/paperclipai/paperclip

**5. vectorize-io/hindsight — 会学习的 Agent 记忆层**
- 简介：Python 项目，主题直指 agent memory：让记忆系统能从交互中自我学习，而不是简单的向量检索堆叠。
- 为什么值得关注：今日 +4,463 为全榜最高。agent 记忆是目前落地最痛的一环（上下文窗口、跨会话一致性、遗忘策略），有真实 RAG/记忆公司背景的团队来做，值得跟进它的检索与更新机制。
- Stars：37,212（今日 +4,463）｜topics: agentic-ai、agents、ai-memory、memory
- 链接：https://github.com/vectorize-io/hindsight

**6. debpalash/VoiceStudio — 完全本地的 ElevenLabs 替代**
- 简介：本地运行的声音工作台：声音克隆、音色设计、视频配音、听写、转写、有声书制作，覆盖 646 种语言。Tauri 界面，支持 CUDA / MLX 双加速，本地优先。
- 为什么值得关注：今日 +3,060。「本地 + 多语言 + 全语音链路」正好对应成本敏感用户对云 TTS 的替代诉求，且 MLX 后端意味着 Apple 芯片可用，Mac 用户可直接受益。
- Stars：40,017（今日 +3,060）｜topics 含 tts、voice-cloning、local-first、mlx
- 链接：https://github.com/debpalash/VoiceStudio

**7. dream-num/univer — 给 AI Agent 用的 Office 运行时**
- 简介：把电子表格、文档、幻灯片、画布、关系表、PDF 统一进一个运行时，定位为「AI Agent 的 Office harness」，提供 sheet/doc/slides/pdf 的 SDK。
- 为什么值得关注：agent 要真正干活，绕不过文档与表格这类结构化产物。Univer 提供的是让 agent 直接读写 Excel/Word/PPT/PDF 的底座，比让模型生成文本再靠人粘贴更接近可用。老项目（2022 年建）持续更新，近期被 AI agent 场景重新带热，今日 +920。
- Stars：20,140（今日 +920）
- 链接：https://github.com/dream-num/univer

**8. rohitg00/ai-engineering-from-scratch — AI 工程从零到落地教程**
- 简介：Python 为主的教学型仓库，「Learn it. Build it. Ship it for others.」，覆盖 transformer、NLP、计算机视觉、强化学习、MCP、agent 与 swarm。
- 为什么值得关注：Stars 5.9 万、今日 +848，说明系统化学习 AI 工程的诉求仍然强烈，适合作为团队内部培训或自查知识盲点的索引。
- Stars：59,235（今日 +848）
- 链接：https://github.com/rohitg00/ai-engineering-from-scratch

---

## 三、一句话跟进建议
- 值得动手试：**OpenRig**（多 agent 编排，先 dry-run）；**VoiceStudio**（Mac 上用 MLX 跑本地语音克隆）。
- 值得读代码：**scriptc**（看 TS→C 的实现路线）；**hindsight**（看记忆更新策略）。
- 只是观察：Madeira（研究项目，依赖每周重签）、PipePipe（Android 第三方 YouTube 客户端，★6,554，今日 +274，与 AI 无关）。

数据来源：blogwatcher-cli（GitHub Trending，HTML 源，本轮 New: 3）+ GitHub REST API 元数据 + Trending 页 HTML 解析；本轮 9 个热榜项目已全部标记已读，核验返回 "No unread articles!"。
