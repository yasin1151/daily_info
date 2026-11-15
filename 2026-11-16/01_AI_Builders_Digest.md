
内容已取到（feed 为 2026-11-15 生成，13 位 builder / 26 条推文 / 1 期播客，无博客更新）。下面是成稿。

---

# AI Builders Digest — 2026年11月16日

今天的主线很清楚：一位模型公司创始人对「coding agent 被 KV cache 绑架」做了一次系统性拆解，这也是近期对 Agent 工具链最有信息量的一段论述；X 上则是 Vercel 的 subagent 工作流、OpenAI 征集 Codex 插件反馈，以及 Aaron Levie 的「所有工作都在变成 coding-shaped」。

## PODCASTS

**Unsupervised Learning — Ep 97: Jev Creator on Decision Models, Benchmark Fatigue & Why the Labs Missed It**
嘉宾是 JEV 系列模型的创始人，主持人是 Redpoint 投资人 Jacob Efron。发布于 11 月 5 日，访谈在模型发布约一个月后进行。
https://www.youtube.com/@RedpointAI

*The Takeaway：决定一个模型能否上生产的不是 benchmark 分数，而是可靠性。整个行业把智能当成一根单轴来排名，恰恰搞错了 AI 真正卡住的地方。*

几个值得记住的点：

**1. 数学能解千禧年难题，却自动化不了会计。** 他把这个反差当成整个行业的诊断书：「为什么我们能解数学上的千禧年大奖难题，却自动化不了任何跟会计沾边的事？这应该让很多人觉得非常奇怪。」他的解释是模型被压缩成 system one 的形状，靠直觉、会犯错，而大部分真实工作需要的正是 system one 级的能力。诚实地公开模型弱点，本身就是产品价值。

**2. 开发者处在斯德哥尔摩综合征里。** 他说现实反馈「几乎为零」，行业默认模型厂商单方面推进路线图，开发者只是被动接收：「人们围绕 AI 会变来做计划，但对把这个领域带向哪里没有 agency。」他自己的内部玩笑是，最能让他在意的不是高管求见，而是有人抱怨 model jaggedness（模型能力的锯齿）。他期待开发者反过来逼厂商修锯齿，而不是研究每个模型的「心智理论」然后锁死架构。

**3. 对 KV cache 暴政的批判，这段最值得做 Agent 的人读。** 他的原话是：「几乎所有关于 coding agent UX 的设计决策，都是围绕 KV cache 做的。」由此推出一串具体后果：状态只能 append-only，像 iPython notebook 一样没法删；routing 基本失效；subagent 要传哪些上下文变成一道昂贵的猜谜；compaction 本质是有损压缩，换任务就会丢掉关键信息；多个 agent 共享同一份 context 在现有架构下做不到。他想要的是「摆脱 KV cache 暴政的 coding agent」，并给了几个具体设想：多个 agent 读写同一份上下文；按任务语义重算 KV cache，用代码算 cache 读写的 ROI；用一次廉价的 MapReduce 扫历史找相关信息，甚至能复用同事在同一代码库上的发现。他的判断是这些「都是可做的软件问题，只是跟 append-only 的智能不兼容」。

**4. 反对 benchmax，而且认为市场已经开始疲劳。** 「形状根本不重要，重要的是它真的有用。」他担心新模型发布已经进入过度承诺、交付不足的循环，烧掉的是开发者的信任。关于护城河他反而很松：「感觉是别人在替我们挖护城河」，并认为现在谈护城河像 GPT-3.5 时代担心护城河一样早。

**5. 编码 agent 到底提效多少：20% 到 40%。** 他自己的估计，并明确把技能退化、技术债这些长期副作用算了进去。有些场景接近无限提速，有些还不如手写。

**6. 对 Anthropic 1.5 万亿估值的冷水。** 「coding agent 极有价值」，但「净收益为正」和「值这么多钱」是两件事。他更尖锐的一句是：实验室最强的能力不是模型、产品或分发，而是 financial engineering，尤其在算力侧的合约结构上。以及那句关于叙事校准的比喻：有人说「让他们去治愈癌症」，这会变成玛丽·安托瓦内特的「让他们吃蛋糕」。

**7. 关于 AI 安全。** 他认为 ASI 讨论和 bio、cyber 风险是完全不同的威胁模型，离真正的 agency 大概还差两个量级巨大的突破。对 RSI 论者，他的批评是「既没怎么读过 AI 史，也没有对 Amdahl 定律的敬意」。

最后一句留给行业：「我们需要开始摆脱 LLM 教给我们的这种缺乏 agency 的状态，重新开始建造，回到玩的状态。」

---

## X / TWITTER

**Thibault Sottiaux（OpenAI，Codex & ChatGPT）**
公开为 Daybreak 征集反馈，范围包括模型、codex 插件、红队与蓝队的访问权限、文档，以及红队和防御工厂。这条拿到 737 赞、534 条回复，是今天互动最密集的一条，说明生态对 Codex 插件化这一层非常在意。
为什么重要：插件、权限分层、文档这三件事正是 Agent 工具链从 demo 走向生产的分界线，官方主动开收集口，通常意味着这一层要重做。
https://x.com/thsottiaux/status/2121845965997101118

**Guillermo Rauch（Vercel CEO）**
两条高信号。一是他的个人工作流已经全部改为「用最强模型做规划，再委派给快模型的 subagent 执行」，并说这只需要在 AGENTS.md 里写一行指令。二是他演示了 fx + Gemini Argon 两个 prompt 生成的纯 Web Components 界面，没有用任何框架，而 agent 直接复用了 UI SDK 里 14 项现成行为：窗口缩放、拖拽、菜单栏 hover 切换、typeahead、工具栏 roving focus、10 段 EQ 滑块、作用域热键、ARIA，以及 WebMCP 的 agent 控制。
为什么重要：前者是当下最省钱也最稳的 Agent 架构范式；后者说明「给 agent 可识别的界面语义」正在被产品化成 SDK，而不是每个团队自己糊一层。
https://x.com/rauchg/status/2121739228698886454
https://x.com/rauchg/status/2121804295381377342

**Aaron Levie（Box CEO）**
一段完整的判断：模型在 coding、tool use、computer use 上进步最快，所以「用软件干活、或从零生成代码」的 agent 会比其他知识工作领域跑得更快。推论是反直觉的：不是只有一小部分工作能被自动化，而是「越来越多的工作会变成 coding-shaped，去适配 agent 擅长的事」。他同时纠正了行业心智模型：模型不需要无所不知，它需要会使用或生成软件，再加上深度领域专长做判断，这个组合一通，其他都跟着通。
为什么重要：如果你在做垂直 Agent，这是在说护城河在领域判断和软件接口，不在模型知识面。
https://x.com/levie/status/2121686564078297461

**Amjad Masad（Replit CEO）**
今天最高赞的一条（1115 赞）是关于可靠性的：「我们进入了墨菲的世界。任何可能出错的事都会出错。当数十亿件事同时发生、递归地互相依赖、并且加速时，曾经被视为罕见的故障，现在是每天的日常。」另两条分别是「Autonomous Businesses are here」，以及他对递归自我改进的历史定位：技术本身就在递归地自我改进，AI 是加速剂但不是这个循环的起点，Douglas Engelbart 早就懂这件事。
为什么重要：agent 规模化之后，长尾故障率会从异常变成基线，可靠性设计得按「每天都会坏」来做预算。
https://x.com/amasad/status/2121519931741127144
https://x.com/amasad/status/2121765647168483589

**Swyx（smol.ai / Cognition / Latent Space）**
转发赞同并补刀：「显然是对的，我们现在在 AI UX 上有多不合格简直离谱，尤其考虑到已经存在便宜到不用计量的模型。」225 赞、83 条回复，讨论相当热。
为什么重要：模型便宜到边际成本可忽略之后，瓶颈整体转移到交互设计层，这也是自研引擎最容易做出差异化的地方。
https://x.com/swyx/status/2121757606801023085

**Peter Yang（AI 教程与访谈作者）**
分享了两个很实用的 prompt：`/doctor prompt-audit` 审计你的 Claude Code 配置（CLAUDE.md、skills、commands）并给出修复建议；`/claude-api prompt-audit [skill 名]` 对单个 skill 做深度体检。他的抱怨很到位：希望 Claude Code 在每次新模型发布时（比如 Fable 5.2）自动提示跑一遍这两个。
为什么重要：模型换代时最容易腐坏的不是代码而是提示词和 skill 配置，这类「配置体检」应该变成 CI 一样的常规动作。
https://x.com/petergyang/status/2121649295950762363

**Garry Tan（YC 总裁兼 CEO）**
两条与 agent 相关的表态：「Aside Browser 对每个 AI agent 都是巨大的解锁」，以及「把这些都做了，然后配上 gbrain 用」。
为什么重要：浏览器层正在被重新定义为 agent 的执行环境，而不是人的阅读器；YC 一侧的表态通常预示接下来一批创业方向。
https://x.com/garrytan/status/2121824006819258485

**Matt Turck（FirstMark 资本，MAD Podcast）**
转评一个关于 open weights 的观点并追问：NVIDIA 是唯一一个既有深口袋、又有明确商业利益去做 open weights AI，并且愿意下创始人式大注的玩家。「接下来会发生什么？」
为什么重要：开放权重这条线的资金结构高度依赖单一玩家，一旦它的动机变化，整个开源生态的节奏都会变。
https://x.com/mattturck/status/2121608999053492408

**Dan Shipper（Every CEO）**
宣布他们把 frontier 团队所有 AI 实验都公开了，包括原始代码和短篇记录，并直接给出使用方式：「想让你的 agent 拿到我们全部的原始 alpha，就让它去读我们的 frontier feed。」
为什么重要：内容正在从「给人读」变成「给 agent 读」，把实验记录做成 agent 可消费的 feed 是个有意思的先行样本。
https://x.com/danshipper/status/2121620539655819305

**Josh Woodward（Google，Gemini App）**
Gemini 接入 Google Wallet 做个人财务洞察：即时生成支出图表、揪出偷偷涨价的订阅、按去年真实支出做假期预算。先对美国用户开放。462 赞。
为什么重要：这是把 agent 的「读数据 + 出结论」能力塞进一个高频日常场景，比通用聊天更能验证可靠性。
https://x.com/joshwoodward/status/2121755282326102417

---

今天跳过：Peter Steinberger、Zara Zhang 等几条无实质内容的转发式发言，以及 Garry Tan 关于 FAA 现代化的评论（与 AI 无关）。

我的建议：如果只读一段，读播客里的 KV cache 那节（约 27 到 34 分钟），它把 subagent 上下文传递、compaction 丢失信息、多 agent 共享状态这几个你日常会撞上的问题，用一套统一的原因解释清楚了。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
