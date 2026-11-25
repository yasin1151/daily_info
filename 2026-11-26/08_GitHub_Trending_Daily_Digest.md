
**GitHub Trending 日报 · 2026-11-26**

今天榜单的明显主线是 **Agent Skills 生态**：在 12 个 AI 相关项目中，有 5 个是可直接安装给 Claude Code、Codex 或 Cursor 的技能包。新趋势是“用多年红队或研究方法论封装成技能包，直接作为付费服务出售”；模型训练类项目则明显退居次要位置，只剩 minimind 一个。

---

**1. Claude-BugHunter** `elementalsouls/Claude-BugHunter`
Python · 22,945 stars · **今日 +1,644**（今日榜首）
把 85 个 skill、16 个 slash command 打包成 Claude Code 的红队技能包，内含 681 条已公开的 HackerOne 报告模式（其中 433 条可逐条溯源），覆盖 24 类漏洞，并包含 M365、Entra、Okta、vCenter 等企业基础设施的攻击链，还配有 Burp MCP 集成。
**为什么值得关注**：这是目前把“人类专家方法论转译成 agent 可执行资产”最彻底的一个案例。它依据真实已披露报告构建技能，并非提示词堆砌；技能内容还自带 VRT 映射和 scope 卫生约束。在攻防侧，这种“技能包作为服务”的形态，可能会比模型本身更快形成商业壁垒。
https://github.com/elementalsouls/Claude-BugHunter

**2. CLI-Anything** `HKUDS/CLI-Anything`
Python · 65,645 stars · **今日 +1,094**
香港大学数据智能实验室的项目，核心主张是“今天的软件服务于人，明天的用户是 agent”。它能为任意软件自动生成 agent 可调用的 CLI 层，再通过 `cli-hub install <name>` 在 Pi、OpenClaw、Cursor、Claude Code 等宿主中安装注册表条目。
**为什么值得关注**：Agent 工具链的瓶颈一直在于“软件没有机器接口”。这个项目选择绕开 MCP，改走 CLI 路线，因为 CLI 天然支持管道、可复现、可审计，而且比 MCP server 更容易被老软件支持，还提供了 preview、live-preview 和 trajectory 循环，让 agent 在真实软件里生成 CAD、3D 场景、字幕等。
https://github.com/HKUDS/CLI-Anything

**3. diagram-design** `cathrynlavery/diagram-design`
HTML · 72,995 stars · **今日 +1,133**
包含 52 个编辑级图表设计技能，供 Claude Code、Codex、Copilot、Cursor、Factory Droid、Qoder、Pi 使用。
**为什么值得关注**：今天榜单的第二个信号是，**审美和版式能力正在被封装成技能资产**。如果说 BugHunter 卖的是领域知识，那么它卖的是“产出物的观感”。这类技能把模型生成的图从“工程师草稿”变成“可以直接放进文档、文章或演示文稿的层级”，落点非常具体，所以传播速度极快。
https://github.com/cathrynlavery/diagram-design

**4. Firecrawl** `firecrawl/firecrawl`
TypeScript · 210,000 stars · **今日 +1,131**
给 agent 提供“知识基础设施”：搜索、抓取、爬取、站点地图，接入 550+ 数据源（Alexandria）。今天的新变化值得单独说明：**Firecrawl Local** 现已可通过 `cargo install firecrawl-local` 安装，作为单二进制程序在本地运行，不需要数据库、队列或容器，同时可作为 MCP server 挂在本地使用。
**为什么值得关注**：这是从“云服务”向“本地单文件”的重要一步。对于成本和数据合规敏感的场景，例如内网知识库和个人 agent 工作站，本地抓取加云端搜索的混合模式，比纯 SaaS 方案更有吸引力。
https://github.com/firecrawl/firecrawl

**5. last30days** `mvanhorn/last30days-skill`
Python · 75,075 stars · **今日 +950**
一个由 agent 驱动的搜索器，跨 Reddit、X、YouTube、HN、Polymarket、arXiv、TikTok 并行抓取，然后**用真实互动数据（upvote、like、Polymarket 真金白银的概率）加权打分**，再由判官模型综合成结论。Reddit、HN、GitHub、专利数据无需配置即可使用，X 和 YouTube 等需要 30 秒向导解锁。
**为什么值得关注**：它直接解决了“搜索引擎按编辑权重排序，不按真实人群注意力排序”的老问题。对做事的人来说，“过去 30 天这个话题到底有多少人在意”是一个高频刚需；它把信号源换成了钱和票，思路很直接。
https://github.com/mvanhorn/last30days-skill

**6. Superpowers** `obra/superpowers`
Shell · 326,588 stars · **今日 +902**
一套完整的软件开发方法论，可安装到 18 种宿主（Claude Code、Codex CLI/App、Cursor、Devin、Gemini CLI、Copilot CLI、Kimi Code、OpenCode、Hermes Agent…）。流程是：先追问你真正要做什么，然后把规格按可读的粒度分块给你确认，再生成一份“给没有品味和判断力的初级工程师也能执行”的实施计划，强制使用红绿 TDD、YAGNI、DRY，最后走 subagent 驱动的开发并逐个任务审查。
**为什么值得关注**：它其实是目前最成熟的“把工程纪律强加给 agent”方案，并非技能集合。README 里“假设执行者没有项目和测试直觉”这句设定，正好说中了 agent 编码失败的根本原因；它的跨宿主覆盖面也说明各大 CLI 都在抢同一套技能标准。
https://github.com/obra/superpowers

**7. minimind** `jingyaogong/minimind`
Python · 70,918 stars · **今日 +828**
用两小时从零训练一个 64M 参数的小语言模型，全套代码加教程。
**为什么值得关注**：大厂都在卷万亿参数的时候，它反向受到欢迎。对想搞清楚 transformer 内部机制、想在自己机器上用 CPU 跑通一次完整预训练的人，这是目前门槛最低的完整路径；它今天上榜也说明“可理解性”本身是稀缺品。
https://github.com/jingyaogong/minimind

**8. autoclip** `zhouxiaoka/autoclip`
Python · 16,126 stars · **今日 +868**
开源 AI 视频剪辑桌面工具：给一个链接，就能一键把播客、访谈或课程长视频剪成短视频，自动生成字幕、封面和发布文案，适配抖音、小红书、TikTok、Reels、YouTube Shorts。
**为什么值得关注**：这是榜单上离普通用户最近的一个 AI 项目，也是今天中文圈的关注重点之一。它把“切片 + 字幕 + 封面 + 文案”这一整条内容再加工流水线做成了本地工具，对做自媒体的人来说，省掉的是几个外包环节。
https://github.com/zhouxiaoka/autoclip

**9. Cursor Plugins** `cursor/plugins`
TypeScript · 19,522 stars · **今日 +408**
Cursor 官方插件规范的正式公开，并附官方插件集。
**为什么值得关注**：这属于基础设施信号，而非单纯的热度。Cursor 把插件规范公开，意味着编辑器侧的 agent 扩展生态开始走向标准化，和 Anthropic 的 Skills、OpenAI 的 MCP 形成三套并行标准；值得留意的是，这三套标准最终会不会收敛。
https://github.com/cursor/plugins

**10. Stitch Skills** `google-labs-code/stitch-skills`
TypeScript · 12,965 stars · **今日 +352**
Google Labs 出品的 Agent Skills 库，专门配套 Stitch MCP server，每个技能都遵循 Agent Skills 开放规范。
**为什么值得关注**：大厂开始用“官方技能库”的方式向 agent 生态推广自家产品，这是继模型 API 之后新的分发手段。它同时验证了 Agent Skills 规范正在被第三方和官方共同采用。
https://github.com/google-labs-code/stitch-skills

---

**此外还有两个值得关注的上榜项目**

- **opensre** `Tracer-Cloud/opensre`（Python, 15,504, +343）：CI/CD 可靠性领域的开源 agent，方向是把运维排障自动化，也是今天唯一一个属于 devops 的 AI 项目。
- **openvino** `openvinotoolkit/openvino`（C++, 12,648, +188）：Intel 的推理优化部署工具包，是端侧和 CPU 推理的老牌选择，今天属于常规热度。

**非 AI 项目**：`nginx`（官方源码仓，+174）、`AFFiNE`（Notion 与 Miro 的结合体，+578）、`Ghost-Downloader-3`（+950，下载器）、`app-store-compliance`（+853，规避 App Store 审核被拒的检查清单）。
