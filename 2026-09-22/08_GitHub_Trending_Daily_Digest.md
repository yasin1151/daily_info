
## GitHub Trending 每日推送 · 2026-09-22

榜单共 12 个项目；blogwatcher 本轮仅新增 2 条（均已标记已读）。其余 10 个前几天已推送过，下面只列**有新变化 / 值得再看的数字**，不重复介绍。

---

### 一、本轮新增（首次上榜）

**1. zhouxiaoka / autoclip｜今日 +266 ★｜总计 8,204 ★｜Python / MIT（今日新增）**
一句话：AI 自动剪高光——把长视频（访谈、播客、课程、直播回放）变成能发出去的短视频切片与合集。
简介：输入本地视频、YouTube 或 B 站链接，可附 SRT 字幕；AI 读字幕生成大纲、话题时间线、精彩度评分和片段标题，自动出切片 + 推荐合集，并提供抖音、小红书、YouTube Shorts、B 站导出预设（可烧字幕、加标题卡）。三种用法：macOS/Windows 桌面包（内置 Python + FFmpeg）、Docker Web 界面、CLI + MCP server（`autoclip run video.mp4 --provider ollama`，支持 Ollama / LM Studio 本地模型，也支持通义千问、OpenAI 兼容接口、Gemini、硅基流动）。
为什么今天上榜：作者 9/20 发 v1.3.0（新增 CLI 与 MCP server）、9/21 发 v1.3.1（界面/官网/README 一次性支持中英日韩西葡俄法八语），属于「连续发版 + 国内自媒体二创刚需」双重推力，一天涨 266 ★、总计 8.2k ★。对你们这条线的意义：它是最典型的「本地可跑、可被 Agent 调用」的视频处理工具——把 FFmpeg/Whisper/LLM 串成一条 CLI + MCP 流水线，而不是又一个网页套壳，这类「媒体处理 + MCP」正快速变成内容型 Agent 的标配组件。
https://github.com/zhouxiaoka/autoclip

**2. mvt-project / mvt｜今日 +177 ★｜总计 13,567 ★｜Python**
一句话：手机（Android / iOS）取证工具包，检查设备是否被入侵——Amnesty International 安全实验室为「Pegasus 项目」做的工具。
简介：从 2021 年 7 月 Pegasus 事件时开源，可提取 iOS 备份、Android 备份与系统日志（sysdiagnose、dumpsys）中的入侵痕迹，配套官方取证方法论与 IOC 规则比对。社区维护活跃，最近合并了 **v3 分支（含破坏性变更，输出格式变了，依赖脚本的会踩坑）**，9/21 又发了 v2026.9.21，把 iOS 备份解密库换成了 `iphone_backup_decrypt`。
为什么值得关注：它不是 AI 项目，但今天是趋势榜上少见的「数字安全」条目，且和 Agent 生态有交集——本周云厂商在推安全审计 skill、AI 自动找漏洞，而 MVT 是「真实攻击发生后如何验证」的那一环。做安全/合规、或者要给自动取证 Agent 找现成能力的人值得收藏。
https://github.com/mvt-project/mvt

---

### 二、榜单其它值得注意的变化（都已推送过，仅记数字与拐点）

| 项目 | 今日 | 总计 | 变化要点 |
|---|---|---|---|
| Open-Dev-Society/OpenStock | +843 | 17,688 | 今日榜首，开源行情平台（非 AI），比昨日 +752 再加速 |
| trycua/cua | +609 | 25,679 | computer-use 基础设施，稳居 AI 系第一梯队 |
| BuilderIO/agent-native | **+607** | 5,867 | **昨日仅 +89，今天跳 6.8 倍**——Agent 与 UI 共享同一 action 层的框架被集中发现 |
| coder/coder | +461 | 16,403 | 「给 Agent 的隔离开发环境」需求持续 |
| anthropics/financial-services | +425 | 35,803 | 官方垂直行业 Agent 模板回榜 |
| Crosstalk-Solutions/project-nomad | +360 | 37,838 | 离线优先知识服务器 + 可选本地 AI（9/15 推过，回榜） |
| ruanyf/weekly | +221 | 103,908 | 中文技术圈信息源常客 |
| akitaonrails/ai-memory | +217 | 7,652 | Rust 写的「编码 Agent 长期记忆 + 跨厂商交接」（8 月推过，回榜） |
| yynxxxxx/Codex-X | +79 | 3,665 | Codex CLI 可视化配置工具（提示词/Provider/Skills/MCP） |
| cloudflare/quiche | +69 | 12,334 | QUIC/HTTP3 实现，协议侧长期热度 |

**今日观察**
1. 榜单「新鲜度」继续偏低：12 个里只有 2 个是全新面孔，其余全是已推过的熟脸，说明今天没有新的 AI 大项目发布窗口。
2. AI 侧最值得看的单一信号是 **agent-native 单日从 +89 跳到 +607**——「Agent 不该是聊天框，而应与界面共用同一层 action 抽象」这个产品范式正在被快速接受。
3. 新增的两个项目都不在「模型/Agent 框架」主赛道，而在**应用工具层**：视频二创（autoclip）和数字取证（mvt）。共同点是都提供 CLI + 可编排接口，方便被 Agent 当作工具调用——这也印证了近期趋势：纯框架热度下降，能被直接接入工作流的「完成一件事」的工具在上升。

数据来源：blogwatcher「GitHub Trending」（12 条，新增 2 条，已读）+ GitHub Trending 日榜 HTML + GitHub 仓库 API（语言/star/topics/发版时间）。
