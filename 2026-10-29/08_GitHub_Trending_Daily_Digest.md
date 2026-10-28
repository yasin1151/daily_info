
**GitHub Trending 日报 · 2026-10-29**

今日榜单最大的变化：前十里有一半是“给 AI 编码代理做技能包”的项目（superpowers、ai-design-skills、hallmark、impeccable、expo/skills）。社区竞争的重点，已从“哪个模型更强”转到“谁能把代理管得更准”。

**今日新上榜**

**1. macro-inc/macro** — 团队一体化工作台，邮件、聊天、文档、任务、CRM 和代理全部共享同一套团队记忆
简介：YC 系团队做的“公司操作系统”，所有内容用 @ 互相链接、可搜索，人和 AI agent 在同一条记忆上工作。Rust 写的，主打速度。Stars 5,404（今日 +106），Rust。
为什么值得关注：这是“Agent 有公司上下文”的第一次工程化尝试：读你的邮件和历史决策，直接干活，而不是只当一个聊天框。前 24 小时关注度不高，属早期项目，可以观望。
https://github.com/macro-inc/macro

**2. expo/skills** — Expo 官方给 AI 代理做的技能包
简介：官方维护的 agent skills，覆盖 Expo 项目的构建、EAS 部署、升级、调试，明确告诉代理“什么时候该用哪个 Expo API、iOS 和 Android 有哪些坑”。支持 Claude Code、Codex、Cursor、OpenCode。Stars 3,554（今日 +216），Shell。
为什么值得关注：这是“框架官方亲自写技能包”的信号。以前 agent 写 React Native 代码全靠猜文档；现在官方把领域知识固化成 skill，后面 Vue、Django 这类生态大概率跟进。
https://github.com/expo/skills

**3. ruvnet/RuView** — 用 WiFi 信号做人体姿态、呼吸和心率感知，全程不采集一个像素
简介：基于 WiFi CSI 信道状态，配合 ESP32 硬件和 HuggingFace 上的预训练模型，把普通 WiFi 变成空间传感器，可穿墙做存在检测和生命体征监测。Stars 101,009（今日 +596），Rust。
为什么值得关注：它又回到榜单前列，star 总量已过十万。隐私争议和“到底准不准”是评论区常年话题，但这是少数把无线感知做成可用仓库的项目，做智能家居或养老监护的值得看一眼。
https://github.com/ruvnet/RuView

**4. hmjz100/LinkSwift** — 八大网盘直链获取脚本（非 AI）
简介：百度、阿里、夸克、UC、天翼、移动、迅雷、123 网盘的下载直链解析，油猴脚本形式。Stars 34,513（今日 +1,380），JavaScript。
为什么值得关注：国内实用型项目，今天新增 star 数比多数 AI 项目还高。注意 GreasyFork 上有仿冒版本，README 明确要求从官方源安装。
https://github.com/hmjz100/LinkSwift

**持续在榜（AI 和 Agent，按今日热度排序）**

- **HKUDS/DeepTutor** 47,917（+2,376）— 终身个性化 AI 导师，港大数据智能实验室出品，今日全榜增量第一
- **Nutlope/hallmark** 40,659（+2,109）— “反 AI 味”设计技能，专治 Claude Code、Cursor、Codex 生成的模板化界面
- **elayadesign/ai-design-skills** 11,071（+1,938）— 设计类 agent 技能合集，昨天刚上榜还在快速上升
- **pbakaus/impeccable** 92,565（+1,471）— 给编码代理的“设计词汇表”，用 polish、bolder、critique 这类词调整代理的审美
- **obra/superpowers** 307,418（+1,096）— 代理技能框架与方法论，star 数已经是最高的那类
- **JetBrains/thinkrail** 5,006（+1,075）— JetBrains 的轻量 AI IDE，能按你的工作方式自我定制
- **nightly-labs/openbot** 3,224（+1,053）— 本地优先的桌面工作台，Codex、Claude、Grok 各占独立工作区，支持代理间协作
- **makecindy/cindy** 8,065（+740）— 开箱即用的开源 AI agent

一点观察：今天这批项目有个共同点——不修改模型本体，只改“喂给模型的那层”：技能包、设计规范、代理工作台和上下文记忆。真正的工程竞争正在从模型层转向上下文和工具层，这比 star 数字更值得关注。
