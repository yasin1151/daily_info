
抓取完成。今日 Trending 16 个项目中，12 个属于 AI/Agent 相关，其余 4 个（nginx、AFFiNE、Ghost-Downloader-3、App Store 合规手册）已跳过。

---

# 📡 GitHub Trending AI 项目日报 — 2026-11-27

## 1. Claude-BugHunter — 给 Claude Code 装的「渗透测试军火库」
🔗 https://github.com/elementalsouls/Claude-BugHunter
⭐ 24,511 | 今日 +1,600 | Python

一个自包含的 Claude 技能包，面向漏洞挖掘和外部红队作业：85 个技能、16 个 slash 命令、681 条已公开漏洞报告模式（其中 433 条逐条标注出处、可审计），覆盖 24 类核心漏洞，另附企业身份与基础设施攻击矩阵、Burp MCP 集成、项目目录脚手架。作者称在授权红队项目和 DVWA / OWASP Juice Shop / Hacker101 等公开靶场上实测过。

**为什么值得关注：** 这是「Agent 技能包 + 垂直安全知识库」这条路线目前做得最细的一次——不是给模型加提示词，而是把几百份真实披露报告的攻防模式结构化，做成可引用、可追责的资产。它也说明 Claude Code 的技能生态开始从「通用开发流程」下沉到「高门槛专业领域」，安全是目前最赚钱也最敏感的那块。

---

## 2. Firecrawl — 让 Agent 变聪明的知识基础设施
🔗 https://github.com/firecrawl/firecrawl
⭐ 210,906 | 今日 +1,042 | TypeScript

面向 Agent 的搜索与抓取层：一个 API 接入 550+ 数据源，负责搜索、爬取、把网页转成 LLM 友好的 Markdown，是目前生产环境里用得最多的「网页→上下文」管道之一。

**为什么值得关注：** 榜单常客但今天仍在放量，说明 Agent 落地时真正的瓶颈不在模型而在于「喂什么给它吃」。抓取质量、反爬对抗、上下文清洗，目前基本是 Firecrawl、Exa 这一层在分食，自建成本高、维护更贵，中小团队几乎只能买。

---

## 3. diagram-design — 拒绝「Mermaid 味儿」的图表设计技能包
🔗 https://github.com/cathrynlavery/diagram-design
⭐ 73,824 | 今日 +951 | HTML

给 Claude Code、Codex、GitHub Copilot、Cursor、Factory Droid、Qoder、Pi 等编码 Agent 用的图表设计技能：52 种图表类型，输出自包含的 HTML + SVG，自带编辑级排版规范，作者明确标榜「没有阴影、没有 Mermaid 那种潦草感」。

**为什么值得关注：** 大量 AI 生成图表的通病是结构对、排版丑。这个项目把「设计品味」写成了硬约束（字体、间距、配色全部固化），是 Agent 技能从「能不能画」转向「画得好不好看」的典型样本。做技术文档和汇报材料的人可以直接拿来用。

---

## 4. AutoClip — 开源的 OpusClip 替代，本地剪片不订阅
🔗 https://github.com/zhouxiaoka/autoclip
⭐ 16,906 | 今日 +770 | Python

本地优先的 AI 视频剪辑桌面工具 + MCP server：给一个链接，自动把播客、访谈、课程等长视频切成短视频，生成字幕、封面和发布文案，适配抖音、小红书、TikTok、Reels 和 YouTube Shorts。内置 Whisper。

**为什么值得关注：** 中文作者作品，直接对标 OpusClip 的订阅收费模式，把「长转短」这条内容再分发流水线整条本地化——素材不出机器，没有按分钟计费。同时它自带 MCP server，意味着剪辑能力可以被 Agent 直接调用，而不是人在 GUI 里点。

---

## 5. Superpowers — 给编码 Agent 的完整软件开发方法论
🔗 https://github.com/obra/superpowers
⭐ 327,460 | 今日 +853 | Shell

不是工具而是一套方法论：一组可组合的技能加上让 Agent 真正会用这些技能的初始指令，覆盖从头脑风暴、计划、子 Agent 驱动开发到验收的完整 SDLC。支持面极广——Claude Code、Codex CLI、Cursor、Gemini CLI、Copilot CLI、OpenCode、Qwen Code、Kimi Code、Antigravity、Devin CLI、Factory Droid，甚至包括 Hermes Agent。

**为什么值得关注：** Agent 写代码的能力在涨，但「怎么组织一次复杂开发」仍然靠人拍脑袋。这个项目把流程本身产品化，且刻意做成跨 CLI 通用——等于在赌「技能标准比模型厂商的护城河更长命」。它的安装列表长到离谱，本身就是当下编码 Agent 混战格局的一张地图。

---

## 6. last30days-skill — 一句话调研任意话题近 30 天全网舆论
🔗 https://github.com/mvanhorn/last30days-skill
⭐ 75,722 | 今日 +755 | Python

一个 Agent 技能：输入任意话题，自动去 Reddit、X、YouTube、Hacker News、Polymarket 和普通网页上收集最近 30 天的相关内容，再合成一份有出处的综述。

**为什么值得关注：** 说穿了就是「把人工情报调研流程写成技能」，按平台分别取信号、再用预言机市场做量化校验。Polymarket 的接入是个有意思的细节——用赔率当事实性交叉验证。对做舆情监控、竞品调研的人，这条路径比单纯让模型联网搜索可靠得多。

---

## 7. CLI-Anything — 把所有软件变成 Agent 原生
🔗 https://github.com/HKUDS/CLI-Anything
⭐ 66,337 | 今日 +744 | Python

港大数据智能实验室（HKUDS）出品，口号是「Making ALL Software Agent-Native」，配了一个 CLI-Hub 分发入口（clianything.cc）。思路是把原本只有 GUI 的软件包装成命令行接口，让 Agent 能直接调用。

**为什么值得关注：** Agent 落地的最大摩擦是绝大多数软件没有 API，只有按钮。把 GUI 软件 CLI 化、再统一到一个 hub 里分发，相当于给 Agent 补上「手」。HKUDS 近期在 Agent 基础设施上连续出活，这个方向如果跑通，MCP 之外会多出一条更粗暴但更通用的集成路径。

---

## 8. MiniMind — 两小时从零训出你自己的 64M 大模型
🔗 https://github.com/jingyaogong/minimind
⭐ 71,606 | 今日 +701 | Python

中文圈老牌教学项目：从零手写并训练一个 64M 参数的小语言模型，全流程两小时可跑完，涵盖数据、分词、预训练、SFT 到推理。

**为什么值得关注：** 榜单天天有 Agent 框架，但真正理解 Transformer 内部怎么运作的人反而变少了。这类「把大模型拆小到能在单卡跑通」的项目，是当前最实用的入门教材——尤其适合在被 API 抽象层包裹太久之后，回头补一次底层直觉。

---

## 9. OpenSRE — 面向 CI/CD 可靠性的开源运维 Agent
🔗 https://github.com/Tracer-Cloud/opensre
⭐ 15,806 | 今日 +325 | Python

一句话戳中痛点：「CI 告诉你挂了，但不告诉你为什么、怎么修。」OpenSRE 是个 CLI Agent，读取失败的流水线，追踪根因，然后推一个修复补丁给你审核。可自托管、用你自己的模型（支持 Ollama），接 Datadog、Grafana、GitLab CI、Slack。当前状态 public alpha。

**为什么值得关注：** SRE/运维是 LLM Agent 少数几个 ROI 清楚、又能容忍「先给建议再人工确认」的场景。自托管 + 自带模型的选择对中大型公司很关键——CI 日志里有最敏感的代码和密钥信息，不太可能直接送去 SaaS。alpha 阶段，适合试不适合上生产。

---

## 10. Stitch Skills — Google 官方设计 Agent 技能库
🔗 https://github.com/google-labs-code/stitch-skills
⭐ 13,275 | 今日 +308 | TypeScript

Google Stitch（AI 生成 UI 设计）官方的技能与插件集合，遵循 Agent Skills 开放标准，兼容 Codex、Antigravity、Gemini CLI、Claude Code、Cursor、OpenCode。分 stitch-design / stitch-build / stitch-utilities 三组插件，可通过 Codex 插件市场稀疏安装。

**为什么值得关注：** 这是 Google 在「Agent 技能标准」上的正式押注——注意它没有自建封闭格式，而是直接兼容 agentskills.io 开放标准，并主动适配竞争对手的 Agent。设计→代码这条链路一旦打通，Figma 到前端的中间环节会被吃得更狠。

---

## 11. Cursor Plugins — Cursor 官方的插件规范与首批插件
🔗 https://github.com/cursor/plugins
⭐ 19,777 | 今日 +268 | TypeScript

Cursor 的插件规范（.cursor-plugin/plugin.json 清单）加官方插件仓库：每个插件是独立目录，已有 Teaching（技能映射、练习计划、学习复盘）、Continual Learning（增量式更新 AGENTS.md 记忆）、Cursor Team Kit（团队 CI / 代码评审 / 发布内部工作流）等。

**为什么值得关注：** Cursor 从编辑器转向「插件平台」，这是在重新划自己的边界——把 IDE 变成 Agent 运行时的宿主。值得盯的是 Continual Learning 那个思路：用高信号的条目增量维护 AGENTS.md，而不是每次重写整份记忆。这套东西正在成为跨工具的共识做法。

---

## 12. OpenVINO — Intel 的 AI 推理优化与部署工具包
🔗 https://github.com/openvinotoolkit/openvino
⭐ 12,810 | 今日 +176 | C++

Intel 的开源推理优化工具包，把训练好的模型优化并部署到 Intel 的 CPU、GPU、NPU 上，支持 LLM 推理、扩散模型、计算机视觉、语音识别、推荐系统等场景。

**为什么值得关注：** 在所有目光都盯着英伟达的时候，端侧和 x86 推理的性价比战场一直在悄悄推进。今天模型小型化（见上面那个 64M 项目）和本地 Agent 的需求同时在涨，OpenVINO 这类能把消费级硬件榨出推理吞吐的工具，实际价值被低估了。

---

**趋势观察：** 今天榜单几乎是「Agent 技能包」包场——Claude-BugHunter、superpowers、diagram-design、last30days、stitch-skills、cursor/plugins 六个都是技能/插件形态，加上 CLI-Anything 这类「给 Agent 补手」的集成层。竞争焦点已经从「模型多聪明」整体迁移到「怎么把专业知识和流程固化给 Agent 用」，而且各方都在往开放标准（agentskills.io）上靠，而不是圈自己的格式。
今日增量榜前二（红队技能包 +1600、抓取基建 +1042）也印证了这一点：市场在为「垂直知识结构化」和「上下文供给」付钱，而不是再要一个通用聊天壳。

*数据来源：GitHub Trending（daily），非 AI 项目已跳过*
