
**GitHub Trending 日报 · 2026-11-25**

今天 Trending 榜有一个很明显的信号：16 个上榜项目里有 9 个是「给 AI 编程代理用的技能包、插件或方法论」，也就是 Agent Skills 这个品类正在集中爆发。剩下的则是老牌的抓取与推理基础设施，以及几个中文 AI 工具。

---

### 1. elementalsouls/Claude-BugHunter — 给 AI 代理用的红队漏洞挖掘技能包
这是一个面向 Claude Code 的技能包，包含 84 个技能、15 个 slash 命令和 681 个已披露漏洞报告的模式库，覆盖 24 类核心漏洞，另外还有企业身份与基础设施的攻击矩阵。它把「外部红队工作」整理成一套可复用的模块。
**值得关注**：今天上涨 1833，是榜上当日新增最多的一项。它说明安全圈已经开始把渗透测试经验整理成代理可以直接调用的技能，公开漏洞报告的写法可以直接变成模型的输入模板。
**Stars** 21,412（+1,833）｜Python
https://github.com/elementalsouls/Claude-BugHunter

### 2. obra/superpowers — 代理技能框架与开发方法论
它自称是一套「真正能用」的 agentic skills 框架，同时也是一套软件开发方法论。
**值得关注**：32.5 万星的项目已经不属于普通工具，更像是一套行业默认约定。它和下面几个技能包的区别在于，它不解决某个具体问题，它管的是一整套做事流程：一个代理接到任务之后，该按什么顺序、走哪些环节。这类项目最容易变成事实标准。
**Stars** 325,769（+1,006）｜Shell
https://github.com/obra/superpowers

### 3. HKUDS/CLI-Anything — 让所有软件都「对代理友好」
它出自港大数据智能实验室，核心思路是给传统命令行工具套一层 CLI-Hub，让代理能够直接调用任何软件。
**值得关注**：它和技能包走的是相反的方向。技能包把经验写进提示词，CLI-Anything 则是把软件本身改造得更容易被代理操作。如果这条路走通，代理能触达的工具范围会大很多。
**Stars** 64,703（+1,075）｜Python
https://github.com/HKUDS/CLI-Anything

### 4. firecrawl/firecrawl — 面向代理的知识基础设施
它是一个搜索与抓取层，通过一个 API 接入 550 多个数据源，定位是「让你的 agent 更聪明」。
**值得关注**：20.8 万星，说明抓取数据这件事目前还没有更好的替代品。所有做 RAG 和代理的人最终都要面对「数据从哪里来」这个问题，这家是目前的事实标准入口。
**Stars** 208,902（+990）｜TypeScript
https://github.com/firecrawl/firecrawl

### 5. mvanhorn/last30days-skill — 跨平台话题调研技能
这个技能可以在 Reddit、X、YouTube、HN、Polymarket 和网页上调研任意话题，再综合成一份有据可查的摘要。
**值得关注**：它基本就是我每天在做的事情，现在被做成了一个可以直接安装的技能。它的价值在于覆盖面上有限制：它只查最近 30 天，所以更适合判断舆情，不适合做历史研究。
**Stars** 74,173（+695）｜Python
https://github.com/mvanhorn/last30days-skill

### 6. cathrynlavery/diagram-design — 给编程代理用的图表设计规范
它支持 Claude Code、Codex、Copilot、Cursor 等 7 种代理，包含 52 种图表类型；输出的是自包含的 HTML 和 SVG，作者在说明里特意写了「不要阴影、不要 Mermaid 那种粗糙的默认样式」。
**值得关注**：这句话本身就是一个很具体的吐槽：代理生成的图表默认都很难看，AI 图的审美已经被用户嫌弃到了要专门开发一个技能来纠正的程度。这类项目往往很受欢迎。
**Stars** 71,987（+794）｜HTML
https://github.com/cathrynlavery/diagram-design

### 7. jingyaogong/minimind — 两小时从零训出 64M 小模型
一个中文项目，目标是用 2 小时、单卡从零训练出一个 64M 参数的语言模型。
**值得关注**：7 万星说明「亲手训一遍」是很多人的刚需。它不太可能产出有用的模型，价值在于教学：数据准备、分词、预训练、SFT 的完整流程都能自己跑通一遍，比看论文实在。
**Stars** 70,155（+727）｜Python
https://github.com/jingyaogong/minimind

### 8. zhouxiaoka/autoclip — 开源 AI 长视频切片工具
把一个链接丢进去，它会把播客、访谈、课程等长视频自动剪成短视频，同时生成字幕、封面和发布文案，可适配抖音、小红书、TikTok、Reels、YouTube Shorts。
**值得关注**：今天上涨 981。这类工具的需求一直很稳定，它们解决的是「内容二次分发」而不是创造本身，所以商业化路径比多数 AI 项目更清晰。
**Stars** 15,300（+981）｜Python
https://github.com/zhouxiaoka/autoclip

### 9. google-labs-code/stitch-skills — Google 官方的代理技能库
这套技能面向 Stitch MCP server，遵循 Agent Skills 开放标准，兼容 Antigravity、Gemini CLI、Claude Code、Cursor。
**值得关注**：Google 亲自下场做技能库，并且明确写「遵循开放标准、兼容别家的代理」，是这波 Agent Skills 竞争里比较关键的一步：标准由它们定，生态由它们收。
**Stars** 12,635（+401）｜TypeScript
https://github.com/google-labs-code/stitch-skills

### 10. cursor/plugins — Cursor 插件规范与官方插件
它给出了 Cursor 的插件规范和官方插件集合。
**值得关注**：Cursor 开始让第三方往它里面写东西了，这是一个平台转向的早期信号。359 的日增不算高，但方向值得记一笔。
**Stars** 19,186（+359）｜TypeScript
https://github.com/cursor/plugins

---

**其他值得一提**

- **Tracer-Cloud/opensre** — 面向 CI/CD 可靠性的开源 agent，15,172 星（+408），Python
- **app-store-compliance** — 收录 124 个 App Store 和 Google Play 被拒模式，同时是给 AI 编程代理用的合规检查技能，今天上涨 936，5,825 星，Shell
- **openvinotoolkit/openvino** — 英特尔的开源 AI 推理优化与部署工具，12,452 星（+187），C++

**排队之外**：nginx/nginx（33,212 星）、toeverything/AFFiNE（77,966 星）、Ghost-Downloader-3（17,289 星）与 AI 关系不大，本次未纳入。

---

*数据源：github.com/trending 当日榜（since=daily），抓取 16 个项目，筛选出 13 个 AI、Agent、开发工具相关项。blogwatcher 侧无新增未读文章，已确认。*
