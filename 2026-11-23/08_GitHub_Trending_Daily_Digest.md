
# GitHub Trending 日报 · 2026-11-23

今天 daily 榜 16 个项目，AI 与 Agent 相关占 12 个。榜单本身换血不多，**真正的变化是「技能包」开始往工程之外的领域扩**：昨天新上榜的是一个 App Store 合规 playbook，把商店审核规则、隐私清单和法域截止日期做成了 Claude Code / Codex 能直接调用的 skill。同时 classic 基础设施（nginx、OpenVINO）因发版重回榜单。

---

## 一、今日重点

### 1. App Store Compliance Playbook — 把「上架被拒」变成可扫描的 skill
`mjmirza/app-store-compliance` · Shell · ★3,955 · **今日 +617** · 昨天刚发 v2.5.1

**简介**：一份开源的 App Store / Google Play 审核避坑手册兼预提交检查器。124 条已归档的拒审原因及对应修法，隐私清单（Privacy Manifest）与 Data safety 声明校验，112 个按地区跟踪的合规截止日期（EU AI Act、DSA、COPPA、各州年龄法）。以 hook + skill 形式装进 Claude Code、Codex CLI、Gemini CLI、Cursor，装完多出 `/app-store-audit` 命令。

**为什么值得关注**：它的 v2.5.1 更新说明里专门写了 "China declarations" 和 "Play trader dates"——这正是国内开发者最容易漏、且一漏就卡首发的两项。作者也很坦白地划了边界：代码扫描看不出你的开发者账号是否激活、协议是否签完，这些仍要人工过一遍。合规是 skill 化最有说服力的场景：规则是公开文本、判定标准死板、人来读又极其枯燥，正好是 agent 的主场。

**Stars**：3,955（今日 +617）· Shell
https://github.com/mjmirza/app-store-compliance

### 2. Claude-BugHunter — 今日涨幅第一，红队经验被打包成 82 个技能
`elementalsouls/Claude-BugHunter` · Python · ★17,726 · **今日 +1,721**

**简介**：Claude Code 技能包，含 82 个技能、15 个 slash command、从 681 份公开漏洞报告中提炼的检测模式，覆盖 24 类核心漏洞，外加 M365/Entra、Okta、vCenter、SSL-VPN 的企业攻击链矩阵与 Burp MCP 集成。

**为什么值得关注**：三天前它还在 14k 星，今天 17.7k，是持续加速而不是一次性爆发。它的价值不在「提示词写得好」，而在于把资深渗透测试者的判断顺序固化下来——先看什么、什么信号算可疑、scope 怎么守。安全团队需要正视一个现实：攻击方的入门门槛正在被 skill 分发拉低，而防守方的检测规则还停留在人工维护。

**Stars**：17,726（今日 +1,721）· Python
https://github.com/elementalsouls/Claude-BugHunter

### 3. Firecrawl — 20 万星还在榜，agent 的瓶颈已经换了地方
`firecrawl/firecrawl` · TypeScript · ★207,004 · **今日 +910**

**简介**：一个 API 统一做搜索、抓取、解析，接 550+ 数据源，把网页转成 LLM 可直接吃的结构化内容。

**为什么值得关注**：它连续多日以近千星的速度增长，说明 2026 年 agent 的天花板确实已经从「模型推理」挪到了「喂进去什么」。做 RAG 或调研 agent 的人绕不开它，也绕不开它的成本结构——抓取质量差一点，后面所有环节都在放大误差。

**Stars**：207,004（今日 +910）· TypeScript
https://github.com/firecrawl/firecrawl

### 4. Superpowers — 32 万星的「agent 工程纪律」
`obra/superpowers` · Shell · ★324,138 · **今日 +785**

**简介**：一套可组合 skills 加初始指令构成的软件开发方法论：agent 不直接写代码，先和你提炼 spec，再产出实施计划，跑红绿 TDD，最后交给子 agent 并行开发与自查。已适配 Claude Code、Codex、Cursor、Gemini CLI、Copilot CLI、Kimi Code、OpenCode、Hermes Agent 等近二十种客户端。

**为什么值得关注**：它卖的不是工具而是流程，这也是它能在 32 万星上还保持日增近 800 的原因。真正的分歧点在下面：它假设 agent 的失败主要来自不守纪律，但另一派认为失败来自模型判断力本身——如果你的体感是后者，用它会觉得流程很重。

**Stars**：324,138（今日 +785）· Shell
https://github.com/obra/superpowers

### 5. CLI-Anything — 让软件以「命令行」而不是「界面」服务 agent
`HKUDS/CLI-Anything` · Python · ★62,751 · **今日 +687**

**简介**：港大数据智能实验室出品。`cli-hub install <name>` 给现有软件套一层 agent 可调用的 CLI，配套 CLI-Hub 注册表、18 个真实 app demo、arXiv 技术报告，Apache 2.0。

**为什么值得关注**：它和 MCP 是两条路线之争——一个是「统一工具协议」，一个是「把任何软件包装成命令行」。后者更土，但稳定性明显更好：agent 学点击 GUI 又慢又易碎，调用 CLI 则天然可复现、可脚本化。

**Stars**：62,751（今日 +687）· Python
https://github.com/HKUDS/CLI-Anything

---

## 二、其余上榜

| 项目 | 今日 | 一句话 |
|---|---|---|
| `XiaoYouChR/Ghost-Downloader-3` ★15,098 | +690 | 国产下载器集大成者，HTTP3/BT/FTP 全支持，v4.5.11 刚发（11-20），Fluent 设计；非 AI，但国内口碑极稳 |
| `mvanhorn/last30days-skill` ★72,686 | +673 | 跨 Reddit/X/YouTube/HN/Polymarket 的 30 天调研 skill，用赞和真金白银的下注额做相关性排序 |
| `zhouxiaoka/autoclip` ★13,407 | +640 | 一个链接一键出片，长视频自动切短视频 + 字幕封面文案，适配抖音/小红书/TikTok/Shorts |
| `toeverything/AFFiNE` ★76,801 | +537 | Notion + Miro 的开源替代，本地优先；连续在榜说明知识库这条赛道没凉 |
| `google-labs-code/stitch-skills` ★11,900 | +516 | Google Stitch MCP 的官方 Agent Skills 库，设计稿转代码的标准化尝试 |
| `cathrynlavery/diagram-design` ★70,278 | +513 | 45 种图表类型、自包含 HTML+SVG，README 明写 "No Mermaid slop"，走出版级排版 |
| `jingyaogong/minimind` ★68,626 | +473 | 2 小时、几块钱从零训一个 64M 模型，覆盖预训练到 GRPO/Agentic RL 全链路，最好的动手教材 |
| `Tracer-Cloud/opensre` ★14,394 | +395 | CI 挂了不只告诉你坏了，而是读失败的 run、追因、直接推 fix 给你 review；public alpha |
| `cursor/plugins` ★18,426 | +301 | Cursor 插件规范与官方插件，做编辑器集成的人必读的生态卡位文档 |
| `nginx/nginx` ★32,881 | +168 | 官方仓库，1.31.9 于 11-18 发布后回升；老基础设施因发版上榜，与 AI 无关 |
| `openvinotoolkit/openvino` ★12,087 | +155 | Intel 的 AI 推理优化部署工具链，支持 LLM 推理与扩散模型；端侧部署仍是刚需 |

---

**今日观察**：把三天的榜单连起来看，位置在变但结构没变——底层是数据与训练（Firecrawl、MiniMind），中间层是 agent 接口与技能（CLI-Anything、Superpowers、各类 skill 包），上层是垂直成品（AutoClip、OpenSRE）。今天新增的一个信号是 skill 的选题正在离开「写代码」，进入合规、上架、法务截止日期这类**规则明确但人懒得读**的领域：这类知识原本以咨询和 checklist 的形式卖钱，现在被压缩成几百 KB 的 markdown 免费分发，中间商的生存空间会先被挤压。

注：blogwatcher 的 GitHub Trending 源今日扫描为 0 条新记录（该源已缓存过这批项目），以上内容来自直接抓取 GitHub Trending daily 榜并逐项核对仓库元数据与最新 release。
