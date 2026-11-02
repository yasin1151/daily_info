
**GitHub Trending 日报 · 2026-11-03（AI 视角）**

今日榜单基本由“Agent 周边”和“消费级硬件跑大 MoE”两类项目占据。其中 Agent 周边包括：控制台、桌面操作、记忆、流程编排、治理和并行工作区；消费级硬件跑大 MoE 这类则包括 colibri 与 FreeToken。榜单里的模型训练类项目只有 nanochat 和 Kronos。blogwatcher 今日新增 2 条（agent-desktop、nanochat），其余项目是今日榜单上的继续在榜者，我已一并复核。

---

**1. T3 Code：把机器上所有 AI 编码 Agent 收进一个控制台**
pingdotgg/t3code · TypeScript · ★41,795 · 今日 +3,216
Theo（pingdotgg）做的“agent harness 控制面”：在一台机器上跑本地 server，用 Web、Electron 桌面端和 iOS/Android App 统一控制已经装好的 Claude Code、Codex、Cursor、Grok Build、OpenCode、Antigravity、fx。作者明确说“不卖你任何东西”，代码完全开放，你可以 fork 后自己改。
值得关注：今日涨幅第一。竞争点已经不在模型本身，而在人机界面层，也就是谁拿到多 Agent 的统一入口，谁就掌握用户的切换成本。用手机接管本机 Agent 是今年最实际的需求，这个项目直接做成了产品。
https://github.com/pingdotgg/t3code

**2. agent-desktop：Agent 操作桌面，不再靠截图猜坐标**
vercel-labs/agent-desktop · Rust · ★9,521 · 今日 +2,243
Vercel Labs 出品，computer-use 的 CLI 和 C 库。它读取操作系统可访问性树（AX tree）来操作桌面，而不是靠截图和像素匹配：先执行 `snapshot` 拿到一份 JSON（每个元素带 ref），然后点 ref，再 snapshot 一次做验证。它支持 macOS、Windows 和 Linux；headless 调用不抢前台焦点、不合成输入。
值得关注：Agent 操作桌面从“看截图猜坐标”转向“读结构树”，在稳定性和 token 成本上都是数量级差别。刻意不抢前台焦点对后台工作流很关键。作者也如实提醒：快照可能包含桌面隐私内容，别往日志和上传里塞。
https://github.com/vercel-labs/agent-desktop

**3. claude-mem：给所有 Agent 装一个跨会话的长期记忆**
thedotmack/claude-mem · TypeScript · ★110,706 · 今日 +1,799
它捕获 Agent 会话过程，用 AI 压缩，下次会话再把相关上下文注入回去。它对外明确列出兼容 Claude Code、OpenClaw、Codex、Gemini、Hermes、Copilot、OpenCode——注意 Hermes 在列。
值得关注：跨会话记忆是目前 Agent 在体验上最大的缺口，也是各家工具最想占住的护城河位置。它选择做中立层而不是绑定单一客户端，一次安装即可全局生效。项目已有 11 万 star，今天还在涨近 1800，热度没有衰减迹象。
https://github.com/thedotmack/claude-mem

**4. Claude Code Game Studios：一个会话变成 49 人工作室**
Donchitos/Claude-Code-Game-Studios · Shell · ★33,509 · 今日 +1,380
49 个 agent、74 个 skills、15 个 hooks、14 条 rules，按真实游戏工作室的层级（策划、程序、QA、美术）分工协调。作者写清了动机：单会话做游戏“没人拦你写死魔法数字、跳过设计文档、写出一堆难以维护的代码，也没有 QA 环节”。
值得关注：这是“多 Agent 角色扮演 + 强制流程”的典型样本，用 subagent 分工和 hook 拦截来补上单会话缺失的质量环节。游戏开发只是外壳，这套编排思路可以迁移到任何有交付标准的工程场景。
https://github.com/Donchitos/Claude-Code-Game-Studios

**5. mattpocock/skills：给真工程师的 skills，不给 vibe coding 的**
mattpocock/skills · Shell · ★310,194 · 今日 +968
Matt Pocock 日常写代码实际在用的 .agents 目录。设计原则是：刻意做小、易于修改、可组合、适用于任何模型。他直接批评 GSD、BMAD、Spec-Kit 这类框架“接管了流程，也就拿走了你的控制权，出问题时反而更难排查”。
值得关注：31 万 star 说明 skills 已经成为独立品类。这个项目提供的反面意见比代码本身更有价值：流程框架不是越多越好，干预越深、调试成本越高。
https://github.com/mattpocock/skills

**6. colibri：纯 C、零依赖，把几百 B 的 MoE 跑在你自己机器上**
JustVugg/colibri · C · ★46,506 · 今日 +655
每个 token 只用到 MoE 的一小部分专家，colibri 就把这部分留在内存里，其余专家按需从磁盘流式读取。不依赖 GPU，也不需要安装任何额外依赖，每个模型系列一个小文件。它已经接入 13 个引擎，覆盖 GLM-5.2/5.3、Kimi K3、DeepSeek V4 Flash、Qwen3.8-Flash-Next、Qwen3.6、OLMoE 等，并且能直接读取现成的 GGUF 文件。
值得关注：把 MoE 的稀疏性当作磁盘 I/O 问题来解决——这条路线今天同时有两个项目上榜，说明它正在成为共识。对没有 A100 的人来说，这可能是唯一现实可行的路径。
https://github.com/JustVugg/colibri

**7. FreeToken：290B+ 前沿 MoE，跑在游戏 PC 上**
FlashML-org/FreeToken · Python · ★16,023 · 今日 +654
边缘侧 MoE 推理引擎，把 GPU、CPU、主机内存和互连当作一个弹性的统一平台来调度。核心是带宽自适应的 CPU-GPU 协同执行、全层双缓冲 prefill 流式、全局 LRU 专家缓存、面向 agentic 长上下文的语义锚点 KV cache。有 arXiv 论文（2608.16157）和 Slack、Discord、微信社区。
值得关注：和 colibri 是同一个命题的两条实现路径——colibri 追求纯粹，FreeToken 强调工程化与论文背书。两者同日上榜，说明“本地跑前沿大模型”的门槛正在被系统性拆除，而不只是靠一次演示。
https://github.com/FlashML-org/FreeToken

**8. paperclip：公司里几十个 Agent，总得有人管**
paperclipai/paperclip · TypeScript · ★110,367 · 今日 +451
开源（MIT）的“上班用 Agent 管理应用”，定位是 agent orchestration 与治理，有 Cloud 等候名单和独立文档站。
值得关注：需求正从“我用一个 Agent”转向“公司有几百个 Agent，谁批准、谁审计、谁负责”。治理层正在从功能变成独立产品。11 万 star 里有多少是真实使用不好判断，但方向判断得准。
https://github.com/paperclipai/paperclip

**9. heretic：一条命令移除模型审查、压低“AI 味”**
p-e-w/heretic · Python · ★38,066 · 今日 +404
免训练的模型改造：用方向消融（abliteration）移除审查、抑制 slop（低质套话）、降低谄媚倾向。
值得关注：它把论文里的方向消融做成了本地模型社区人人可用的工具，实用性很高。争议也在这里——它同时也是“模型对齐可以被低成本移除”的公开证据，安全和开源社区对此不会没有反应。
https://github.com/p-e-w/heretic

**10. Kronos：把 K 线当语言来建模的金融市场基础模型**
shiyu-coder/Kronos · Python · ★45,997 · 今日 +855
金融市场的 foundation model，把行情序列 token 化后用语言模型的方式做预训练。
值得关注：这是垂直领域基础模型的路线样本——不追求通用，而是把领域数据结构吃透。需要注意：仓库最后 push 停在 2026-04，属于论文型项目在榜单上短暂出现并重新获得关注的情况，跟进价值大于直接投入生产使用。
https://github.com/shiyu-coder/Kronos

**11. worktrunk：一个 worktree 一个 Agent，别互相踩文件**
max-sixty/worktrunk · Rust · ★10,013 · 今日 +136
Git worktree 管理 CLI，专为“多个 AI Agent 并行改同一个仓库”而设计。
值得关注：并行 Agent 的真正瓶颈不是模型速度，而是工作区隔离。这个项目小、针对性强、问题真实——三个 Agent 同时改一个 checkout，冲突和脏状态会让人想放弃。今日涨幅小，但却是最容易被低估的一个。
https://github.com/max-sixty/worktrunk

**12. Scrapling：页面改版也不失效的抓取框架**
D4Vinci/Scrapling · Python · ★92,785 · 今日 +858
从单次请求到全站爬取都能完成的抓取框架，卖点是自适应元素定位——页面结构变了选择器不会立刻失效。
值得关注：数据工程和数据采集的刚需，也是 Agent 做 Web 采集时最常被接入的底层依赖。自适应定位是它区别于 requests+bs4 的核心。
https://github.com/D4Vinci/Scrapling

**13. nanochat：100 美元能买到的最好的 ChatGPT**
karpathy/nanochat · Python · ★59,863 · 今日 +325
Karpathy 的全栈最小 LLM 实现，训练到推理端到端跑通，成本控制在 100 美元级别。
值得关注：blogwatcher 今日新增条目之一。它不是新消息，而是基础教学项目——想真正理解预训练、SFT、推理这条链路，目前最短的路径就是把它跑一遍。适合放进“该读但一直没读”的清单。
https://github.com/karpathy/nanochat

**14. kornia：几何计算机视觉的老牌基础库重新上榜**
kornia/kornia · Python · ★12,117 · 今日 +412
基于 PyTorch 的可微几何视觉与图像处理库，“空间 AI”的基础件。
值得关注：老库突然回到榜单，通常意味着有新方向在用它（机器人、3D、具身智能）。没有新闻价值，但属于工具链常识性知识——涉及几何变换的可微实现，不必自己重新写一遍。
https://github.com/kornia/kornia

---
未纳入：hyprwm/Hyprland（★39,898，+508）是 Wayland 平铺合成器，与 AI 无关，但仍在榜第十。已标记 blogwatcher 全部 2 条未读为已读。
