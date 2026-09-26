
All content extracted. This is a small dataset (14 builders / 29 tweets / 1 podcast / 1 blog) — composing directly.

---

**AI Builders Digest — 2026-09-27**

## X / 构建者动态

**Boris Cherny（Anthropic，Claude Code）——把 agent 塞进沟通层，而不是 IDE**
他晒了自己日常在 Slack 里用的 agent（Tag）的实际战绩：每天写掉他 50% 以上的 PR，做掉近 100% 的数据分析，还修掉大部分产品反馈和 bug。他强调这不是普通 Slack bot——它是主动的、可编程的、有记忆、能访问你的 connectors。他给的提示词很能说明形态，比如："从现在起，把本频道每个 bug 都端到端复现一遍并跑通整个应用；复现后直接提 PR 并 @ 对应团队 review"，以及"围绕这个诡异数据头脑风暴约 100 个假设，用 workflow 逐一验证，大概烧 10M tokens 深挖，最后画张图"。
*为什么值得关注：这是 Agent 工具链最前沿的形态样本——agent 的主场从编辑器迁移到团队沟通层，而"花千万级 token 做一次性深挖"已经被当成常规操作。*
https://x.com/bcherny/status/2103538666597691552

**Thariq（Anthropic，Claude Code）——effort 档位到底该怎么调**
他专门深挖了 reasoning effort 这个问题：什么时候该改档、为什么不该无脑拉满 max。他的个人用法是反直觉的："我在想保持在链路里的时候更多用 effort low；effort max 基本只在我完全不打算介入，或者想去找安全漏洞时用。"配套还放了一个新的 dev site，用可交互的 benchmark 解释器和 demo 讲这件事。
*为什么值得关注：对自研引擎和 agent 工具链来说，推理预算分档策略直接决定成本/质量的取舍，而一线开发者给出的经验是"不要默认拉满"。*
https://x.com/trq212/status/2103577115010687067 （主贴：https://x.com/trq212/status/2103576349499855160）

**Peter Steinberger（OpenClaw 作者）——多并发 agent 的架构坑，以及 agent 重构的规模**
他很坦诚地复盘了自己最大的设计失误：OpenClaw 迁到 SQLite 时用了同步 DB 访问。"当时它只是 Slack 或 iMessage 上向你汇报的单个 agent，这没问题；但现在一个 agent 可能并行跑 50 个 session，整个团队都在用它，这就是瓶颈了。"他给自己的 agent 下了一个 /goal，目前已经落地 575 个 PR 把整套东西迁到异步 worker，"即便巨大的重构也不再可怕了"。
*为什么值得关注：这是"单 agent 玩具"到"多人共用的多 agent 系统"之间真实会撞上的墙，也是 agent 承担大规模重构的实操数据点。*
https://x.com/steipete/status/2103648679169257737

**Guillermo Rauch（Vercel CEO）——采购门槛正在从"对人好用"变成"对 agent 好用"**
在讲他们帮 Klaviyo 这类组织搭 agentic 部署平台（接入 claude/codex/cursor、走 IDP 做 SSO、然后全员安全使用）时，他给了一个很硬的判断："新的 procurement bar 会是你的产品对 agent 有多顺手，而不是对人类有多顺手——agent 能不能轻松读懂你的 ontology、操作你的数据。"他还指出这解释了为什么大型企业 SaaS 突然开始优先发 CLI 和 MCP，或者翻出被冷落多年的 API。往下推的结论更狠：一旦这套就位，"有一大堆长尾 SaaS 应用我怀疑再也不会被采购了，它们会被直接生成出来，更安全、更快、更现代，还针对每家公司定制"。另一条他感叹 npx skills 的增长："我们过去写代码，现在写英文。"
*为什么值得关注：CLI / MCP / ontology 从"加分项"变成"准入项"的判断，对 Agent 工具链的路线选择是直接可用的输入。*
https://x.com/rauchg/status/2103564484602384855 、 https://x.com/rauchg/status/2103543983557517340

**Aaron Levie（Box CEO）——evals 是企业 AI 扩散的闸门**
"你无法自动化你无法度量的东西"——他把 evals 直接定性为企业在非确定性流程上的唯一抓手。确定性流程还能用软件测，但今天几乎没多少企业有办法搞清楚 agent 在自家环境里到底干得怎么样。所以所有变更、升级、部署都下游于好的 evals；未来既会有大量领域专用的 evals，每家企业的环境也需要自己的那套。
*为什么值得关注：如果你在做 agent 落地，"先做 eval 再做功能"这个顺序被一线 CEO 说成了前提条件，而不是最佳实践。*
https://x.com/levie/status/2103629073595728372

**Thibault Sottiaux（OpenAI，Codex & ChatGPT）——Codex 宕机与用量限额重置**
Codex 出现故障，他先发"我们已知晓 Codex 挂了，正在恢复"（近 1.06 万赞、2255 条回复），恢复后宣布"我们回来了，并且会给所有付费用户重置 Codex 和 ChatGPT work 的用量限额"，为短暂中断致歉。
*为什么值得关注：除了时效性，这条也侧面反映 Codex 用量限额对重度用户是真实痛点（高赞高回复说明情绪）。*
https://x.com/thsottiaux/status/2103637477760311522

**Amjad Masad（Replit CEO）——收购 Atta 团队，押注"自动驾驶的公司"**
Replit 正在构建"self-driving company"，核心是"把理解业务的能力交到每个人手里"。他欢迎 Atta 的 Omar、Amine 及团队加入，看重的是 Atta 在业务分析和数据可视化上的做法，和自己"有用的智能应该人人可用"的信念一致。
*为什么值得关注：编码工具公司正在往"自动运营公司"外延，这是产品边界迁移的信号。*
https://x.com/amasad/status/2103632415185133992

**Sam Altman（OpenAI）——agent 联网行为的持续审查**
他说围绕"agent 在训练和评估期间使用互联网访问"有一项仍在进行的大范围审查，会持续发布摘要；坦承"没有我们希望的那么快"，但要在透明度和"从 PB 级 agent 活动日志里搞清楚究竟发生了什么"之间平衡，也要和受影响组织协调。按严重程度排序处理并加人，Hugging Face 那件事仍是他们见过最严重的事件。
*为什么值得关注：agent 自主联网的行为边界与披露机制，是接下来所有 agent 产品都要面对的合规前置。*
https://x.com/sama/status/2103567198690349362

**Matt Turck（FirstMark Capital）——超级幂律**
"创业公司如此之多。但所有投资人都想投同样那 10 到 30 家。这事一直都成立，但大概从未到这个程度。Hyper power law。"
*为什么值得关注：一句话概括当前一级市场的资金结构，是判断"做工具链还是做应用"时的背景板。*
https://x.com/mattturck/status/2103550183506337835

**Peter Yang（AI 教程作者）——对 Muse 的实际吐槽**
他让 Grok Bot 和 Muse 追踪同一份日本行程，Muse 报的价格比 Grok Bot 贵 1000 美元以上；追问后 Muse 说它查的是 Duffel 而不是 Google Flights，他直接问"Duffel 是个什么鬼"。他同时认为 Muse 的 UI 和吉祥物做得很棒，但底层模型智能程度存疑，"如果它没那么聪明也说得通，毕竟这是要做给十亿人用的"。
*为什么值得关注：真实用户的横向实测，比发布会更能说明消费级 agent 在工具选择上的可靠性问题。*
https://x.com/petergyang/status/2103693608729932025

## 官方博客

**Claude Blog：Claude Cowork 和 chat 合并成一个 Claude**
从今天起 Cowork 和 chat 不再分开——提个简单问题，或者把一份中午要交的报告丢过去，Claude 会接着做，哪怕你已经合上笔记本。正在 Pro 和 Max 计划上陆续推送。同时新增 Claude Docs 和 Claude Slides，Claude Design 也进入对话内。官方解释合并的原因很直接：他们本来把 Cowork 当成"大活儿专用地"、Design 当"视觉活儿专用地"，但用户两边都用，反馈最烦的就是"要判断一个任务该放哪边"，而且两边的内容还不互通，于是干脆不再让人做选择。用户原话（Andrew Keller，Senior Economist）："我可以让 Claude 打开我的法律研究数据库，它会把所有案例找出来、读完、判断我还需要哪些其他案例、下载下来，存进一个文件夹供我自己审阅。"
*为什么值得关注：agent 产品形态正在从"多个垂直入口"收敛回"一个统一对话面"，长任务（关掉电脑还在跑）成为默认能力。Beta 在付费计划，企业管理员决定何时开启。*
https://claude.com/blog/cowork-is-now-claude

## 播客

**No Priors：Re-Founding Incumbents for the AI Era（嘉宾 Michael Lee，Sequence Holdings 联合创始人兼 CEO）**
**一句话结论：** 与其给现有装配线上的每个人发一台小机器提速，不如直接买下行业里的老牌公司，然后按 AI 的原生形态把组织重新设计一遍。
Sequence Holdings 是一家永久控股公司，专门和传统行业的管理团队合作"refound"他们的业务。他们刚宣布了迄今最大的 AI take private：与 Dell 家族办公室一起，以 77 亿美元收购保险经纪公司 Baldwin。更早的试点则是一家社区银行 BankSouth——从服务方变成股东之后，Michael Lee 说感受是"天壤之别"，因为可以按十年尺度去搭技术底座，而且银行受监管反而是优势：流程定义清楚、数据卫生极好，"如果从这个角度看，它其实非常适合 agent 落地"。六个月的成绩单很具体：消费贷平均承保时间下降 94%，全行平均一笔贷款端到端从 30 天缩到 11 天，而且是在不改变任何授信标准的前提下完成的；承保团队人数反而更少，原因只是一人退休、一人转去前台。他反复强调最难的不是工程问题是人的问题：要给员工的感觉不是"你被替代了"，而是"我们把你从重复劳动里拿出来，让你做你更擅长、更享受的事"。
他关于组织文化的判断可能是这期最值得抄走的一句：**"地球上每家公司都有一个被推崇的人格样板……在一个你相信 alpha 来自工程和 AI 的世界里，你需要创造一种文化，让被推崇的人格样板是工程师。"** 他拿 Blackstone 做对比——Blackstone 被推崇的是投资人，所以它能聚起全世界最好的投资人。技术层面他提到自建的 Atlas 平台分四层：数据本体（把业务用代码定义清楚，让模型理解"这个系统的客户和那个系统的客户是同一个人"）、agent builder（构建扎根于 ground truth 的 agent）、Lattice 编排引擎（用造好的 agent 给流程装仪表）、最上层是 artifacts。底层观察是："把业务拆到原子级，80% 是高度同质的，20% 才是垂直行业特有的。"至于为什么服务商和买软件都不行——服务商优化的是"进你的钱包、留在你钱包、扩大份额"，本质是渐进主义；买软件则是对所有人开放就等于没有优势，而且软件永远只能卖"今天设计成这样的工作流"。他把自己的模式总结为"一年只做一笔，如果没有合适的，这一年一笔不做也很好"。
*为什么值得关注：这是把"AI 转型"从 PPT 变成可量化前后对比的少数真实案例（94%、30→11 天），而且 Atlas 的"数据本体 + agent builder + 编排引擎"三层结构和 Rauch 说的 ontology 是同一件事的两个侧面——如果你在做自研引擎，这两条可以互相印证。*
https://www.youtube.com/@NoPriorsPodcast

---
*Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders*
