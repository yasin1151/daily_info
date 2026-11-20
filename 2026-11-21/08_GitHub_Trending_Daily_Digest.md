
# GitHub Trending 今日热门 AI 项目（2026-11-21）

数据取自今日 GitHub Trending 榜单（daily），并按照 AI、Agent、LLM、开发工具方向筛选。Star 数为当前总量，`+N` 为今日新增。

---

## 1. Claude-BugHunter — 让 Claude Code 变成红队操作员
`elementalsouls/Claude-BugHunter` · Python · ★14,178 · **+1,660** · MIT

**简介**：一个可直接安装的 Claude Code 技能包，内含 83 个技能、15 个斜杠命令、681 条已披露漏洞报告的模式（其中 433 条逐条标注来源），覆盖 24 类核心漏洞，附带企业身份与基础设施攻击矩阵、Burp MCP 集成，已在授权红队项目和 DVWA、Juice Shop 等靶场上验证。

**为什么值得关注**：它把“挖洞经验”压缩成模型可直接加载的技能文件，这是 skills 生态目前最有商业价值的方向之一：垂直专业知识被封装成可供销售或流通的资产。同时也提供了一种信号：攻击性能力与 skill 分发结合在一起，安全团队很难再靠“模型不会”来防守。

https://github.com/elementalsouls/Claude-BugHunter

## 2. Firecrawl — Agent 的数据层问题重新受到关注
`firecrawl/firecrawl` · TypeScript · ★205,227 · **+1,226** · AGPL-3.0

**简介**：定位是“让 agent 更聪明的知识基础设施”，统一做搜索、抓取和解析，接入 550+ 数据源，把网页转成 LLM 可用的结构化内容。

**为什么值得关注**：这是 2024 年的老项目今天再次上榜，说明 2026 年 agent 的瓶颈已从“推理能力”转移到“喂什么进去”。当大家都在做 agent 框架时，真正提高 agent 能力的是抓取质量、反爬能力和结构化后的数据质量。

https://github.com/firecrawl/firecrawl

## 3. AutoClip — 一个链接一键出片
`zhouxiaoka/autoclip` · Python · ★12,149 · **+983** · MIT

**简介**：开源 AI 视频剪辑桌面工具（Tauri）。贴入播客、访谈或课程链接，自动剪成短视频，生成字幕、封面和发布文案，适配抖音、小红书、TikTok、Reels、YouTube Shorts、B站。软件免费，云端模型按量计费，需要时可手动回到编辑器调整。

**为什么值得关注**：这是今天榜单里最“能直接拿来用”的项目。它切中的是内容从业者的真实高频需求：长视频二次分发。它也属于典型的本地端加云端模型混合架构，避开了纯 SaaS 的订阅反感，同时保留了付费转化点。

https://github.com/zhouxiaoka/autoclip

## 4. Superpowers — 给编码 agent 装一套开发方法论
`obra/superpowers` · Shell · ★322,814 · **+888** · MIT

**简介**：由一组可组合 skills 加上初始指令构成的完整软件开发方法论。核心行为是让 agent 不直接开始写代码，而是先问清你到底要做什么、分块给你读设计，再产出实施计划。支持 Claude Code、Codex、Cursor、Gemini CLI、Copilot CLI、Kimi Code、OpenCode、Pi、Qwen Code、Hermes Agent 等近二十种客户端。

**为什么值得关注**：32 万 star 量级说明它已经超出普通工具范畴，变成了事实标准。它的主张是流程纪律比模型能力更决定产出质量。值得亲自试的原因，是它支持几乎所有主流 CLI，包括 Hermes Agent 本身，可以作为对比其他 agent 工作流的基准。

https://github.com/obra/superpowers

## 5. MiniMind — 3 块钱、2 小时从零训一个 LLM
`jingyaogong/minimind` · Python · ★67,670 · **+841** · Apache-2.0

**简介**：完全从零训练约 64M 参数的超小语言模型，最小版本体积约为 GPT-3 的 1/2700，覆盖 MoE、数据清洗、预训练、SFT、LoRA、DPO、PPO、GRPO、CISPO、Tool Use、Agentic RL 完整链路。

**为什么值得关注**：它是少数能把“大模型训练”从论文变成可动手实验的项目。对于想真正理解 RLHF 和 agentic RL 在代码层面如何实现的人，认真读一遍并完整跑通一遍，比读十篇综述更有价值。它对普通个人 GPU 友好，这是它长期留在榜单上的原因。

https://github.com/jingyaogong/minimind

## 6. CLI-Anything — 让所有软件变成 Agent 原生
`HKUDS/CLI-Anything` · Python · ★61,358 · **+774** · Apache-2.0

**简介**：口号是“Today's software serves humans, tomorrow's users will be agents”。它把现有软件封装成 agent 可直接调用的 CLI 接口，配套 CLI-Hub 注册表做统一发现。

**为什么值得关注**：这一判断认为，未来软件的使用者转向 agent，UI 的角色将发生变化，这是目前最激进的判断之一。它也确实指向一个现实问题：agent 操作软件目前主要靠 GUI 自动化（截图加点击），这条路又慢又容易出错；把 CLI 作为 agent 的原生接口，比让 agent 学人类点击界面稳健得多。

https://github.com/HKUDS/CLI-Anything

## 7. last30days — 用真实投票而不是编辑推荐做搜索
`mvanhorn/last30days-skill` · Python · ★71,419 · **+685** · MIT

**简介**：一个由 agent 主导的搜索引擎，跨 Reddit、X、YouTube、Hacker News、Polymarket 和全网检索，排序依据是 upvote、like 和真实下注资金，而不是编辑挑选。

**为什么值得关注**：它和你的信息流需求高度重合。用“钱和赞”作为相关性信号，是对 SEO 化搜索的一种直接反驳，尤其适合查“某件事社区到底怎么看”。Polymarket 的赔率作为信号维度，是目前少见的设计。

https://github.com/mvanhorn/last30days-skill

## 8. diagram-design — 让 agent 输出编辑级图表
`cathrynlavery/diagram-design` · HTML · ★69,262 · **+634** · MIT

**简介**：一套“编辑级”图表设计规范与 skill，适配 Claude Code、Codex、GitHub Copilot、Cursor、Factory Droid、Qoder 等，输出的是真正可用于出版的设计，而不是 matplotlib 默认样式。

**为什么值得关注**：生成图表的能力早就有，但“好看且信息层次正确”一直是缺失的一环。它瞄准的是 agent 产出物的最后一公里质量问题：技术内容创作者几乎都需要这项能力，但很少有人把它做成 skill。

https://github.com/cathrynlavery/diagram-design

## 9. PaperOrchestra — Google 的多 agent 论文写作流水线
`google-research/paper-orchestra` · Python · ★5,427 · **+492** · Apache-2.0

**简介**：Google Cloud AI Research 出品。把零散的“想法 + 实验日志”转换成可投稿的 LaTeX 稿件：大纲生成、文献综述、分节写作、内容精修、图表生成，按目标会议模板输出。

**为什么值得关注**：这是今天争议潜力最大的项目。工业实验室公开做“自动写论文”，必然会在学术圈引发讨论：它可能被视为科研效率工具，也可能被视为论文工厂的基础设施。技术上值得看的是它的多 agent 分工与文献筛选策略；立场上，它值得关注，但不建议不加判断地接受。

https://github.com/google-research/paper-orchestra

## 10. OpenSRE — 会自己修 CI 的运维 agent
`Tracer-Cloud/opensre` · Python · ★13,587 · **+465** · Apache-2.0

**简介**：开源 CI/CD 可靠性 agent。CI 只告诉你它坏了，不告诉你为什么以及怎么修；OpenSRE 读取失败的 run、追因、直接推一个 fix 给你 review。自托管，自带模型，目前 public alpha。

**为什么值得关注**：CI 排障是 agent 最容易被验证价值的场景：输入输出明确，失败可复现，而且工程师真的不想做。它支持 Datadog、GitLab CI 等接入，说明作者想把它放进真实流水线，而不是停留于 demo。

https://github.com/Tracer-Cloud/opensre

---

## 其他值得留意

| 项目 | 今日 | 一句话 |
|---|---|---|
| `google-labs-code/stitch-skills` ★11,015 | +315 | Google Stitch MCP 的官方 Agent Skills 库，设计稿转代码的标准化尝试 |
| `FlashML-org/FreeVideo` ★3,786 | +304 | MiniMax H3 在 8GB 显存本地跑，桌面 App 三平台；759 个 open issue 说明它足够热门，但同时也还不够成熟 |
| `cursor/plugins` ★17,835 | +292 | Cursor 插件规范与官方插件，生态卡位文档，做编辑器集成的人必读 |
| `anomalyco/opencode` ★228,250 | +244 | 开源编码 agent，今天依然在高位，作为 Claude Code 的替代方案持续增长 |
| `colbymchenry/codegraph` ★78,247 | +127 | 预索引代码知识图谱，随代码变更自动同步，供 Claude Code、Codex、Gemini 使用 |
| `earendil-works/pi` ★123,069 | +160 | AI agent 工具包：统一 LLM API + agent loop + TUI + 编码 CLI |
| `p-e-w/heretic` ★42,358 | +181 | 免训练去审查、降谄媚，属于模型改造类，伦理争议持续 |
| `SWE-agent/mini-swe-agent` ★9,898 | +62 | 100 行代码解决 GitHub issue 的极简 agent，适合作为教学材料 |

---

**今日观察**：榜单结构很清晰地分成三层：底层是数据与训练（Firecrawl、MiniMind），中间层是 agent 接口与技能（CLI-Anything、Superpowers、各类 skills 包），上层是垂直成品（AutoClip、FreeVideo、OpenSRE）。其中增长最猛的是“技能包”这一类，今天前十里有五个是 skill bundle；这说明在 2026 年末，agent 的竞争重点正在转向如何包装和分发专业能力，而不再主要围绕模型本身。

注：blogwatcher 的 “GitHub Trending” 源今日扫描结果为 0 新条目（该源此前已扫描过），本次内容来自直接抓取 GitHub Trending 页面的 daily 榜（含 Python、TypeScript 分榜）。
