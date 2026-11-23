
AI Builders Digest — 2026-11-24

今日主线很集中：OpenAI 想把「perplexity」做成全行业统一的监管刻度，Vercel 和 Box 各自从安全和编排两个方向拆 agent 的底层问题，而 Every 的 Dan Shipper 给了一个我认为今天最值得读的答案：模型能力会变成所有人的地板价，剩下的价值在你怎么用它。

═══════════════════
X / TWITTER
═══════════════════

▍Sam Altman（OpenAI CEO）：提出用 perplexity 当行业「开发红线」的度量

他在 White House Accords 的框架下公开表态，认为 frontier lab 应该联合建立共享的评测规范和 red-team 标准，并且更进一步：设立一条基于 perplexity 等指标的共同上限，各家承诺在「我们理解和监控 AI 行为的能力达到某个具体里程碑」（比如 CoT monitor 的继任者出现）之前，不去越过这条线。他自己也承认这是在提议一个「可量化的暂停条件」。

为什么值得看：过去两年监管讨论一直在 FLOPS 算力门槛上打转，绕不开「训练完之后还能不能用」这个漏洞。用 perplexity（模型压缩度）当刻度，是把监管对象从「投入了多少算力」改成「模型内在有多聪明」，这在方法论上是很不一样的一步。当然，由被监管方自己提指标这件事本身就值得警惕。

https://x.com/sama/status/2124551883130114403
https://x.com/sama/status/2124558713646428663

▍Swyx（smol.ai / Cognition / Latent Space）：这张图讲清了过去四年，但也可能骗了我们

他先是被 OpenAI 那张 perplexity 曲线打动，说这是「讲过去四年故事最漂亮的方式之一」，并顺手给了个判断：大家天天吵的后训练问题，其实只是 B plot，真正的 A plot 一直是大规模预训练的进展。

但隔了几个小时他自己开始怀疑：按这个 metric 算，今年一年的 AI 进步比 2022 到 2025 加起来还多，「感觉上不太像」。他的猜测是要么被算法和指标骗了，要么这个指标只在前沿数学层面才翻译成真实能力。这种当众自我反驳挺少见，也正好说明现在缺一个能对齐体感的进度度量。

https://x.com/swyx/status/2124583459356373052
https://x.com/swyx/status/2124590240539259381

▍Guillermo Rauch（Vercel CEO）：那些「免费 stealth model」是工业级数据外流

这条是今天火药味最重的。他直接指控某家提供「免费、ZDR、stealth model」推理的服务是「工业化规模的数据外流，流向国家项目」，并说 Dragos 的研究佐证了他的怀疑。后半段是他惯常的自我推销：Vercel AI Gateway 是靠真实 token 量堆起来的，没走过这些捷径。他还模拟了一段跟老板汇报的场景：抱歉老板，我就是想试试那个很酷的免费模型，现在我们的密钥、客户数据和代码都在另一个大洲了。

同一天他还有一条更偏理念的：AI 应该被指向「人类可理解性」，而不只是艺术性的成果。黎曼猜想的证明应该附带论文、walkthrough 和新概念，就像即使 LLM 能直接输出 CPU 指令，高级语言的中间表示依然有价值。

为什么值得看：第一条是安全采购层面的实务风险，凡是在做多模型路由的团队都该看一眼；第二条是少见的、来自基础设施厂商对「可解释性不是可选项」的明确表态。

https://x.com/rauchg/status/2124595496849445079
https://x.com/rauchg/status/2124654108124848350

▍Aaron Levie（Box CEO）：agent 编排的真正难点是「共享知识的暴露度」

他这条是对「agent 会怎么协作」最具体的一段描述。核心判断：当 agent 承担越来越长的项目型工作，并且出现一堆 agent 朝同一个目标并行推进时，harness 和编排架构必须演进。最大的变化不在算力，而在 agent 之间怎么共享知识、怎么跟踪任务状态、怎么和人类协调。

他的原话是这事「理论上技术上是直接的」，但要保证 agent 既能拿到相关资源、又不至于过度或过少暴露，复杂度极高。可以大量借鉴人类已有的协作方式（共享文件、每人一台电脑、聊天和收件箱），但 primitives 必须支持远超人类的吞吐，而且是在 agent 本身很容易变成安全风险向量的前提下。

为什么值得看：这是目前少有的、把「多 agent 协作」从 demo 层面拉到权限模型和状态管理层面的公开表述。做 agent 工具链的话，这段话基本就是需求文档。

https://x.com/levie/status/2124658150771188157

▍Peter Yang 转述 Microsoft Copilot EVP：Agents are very harsh customers

他引了 Microsoft Copilot 的 EVP 的一段话，讲 agent 成为软件主要用户之后会发生什么：agent 会按性能、价格、可靠性挑最优解，而 agent 的偏好不等于人的偏好。人做搜索你给十条链接加摘要就够了，agent 根本不在乎，你可以返回一千条结果。所以 API 和 UX 都会开始长出专门服务 agent 的模式。

为什么值得看：一句话，「为人类注意力做优化」这个前提正在失效。如果 agent 是主要调用方，产品设计的第一性原理要换。

https://x.com/petergyang/status/2124669298191090033

▍Amjad Masad（Replit CEO）：桌面 AI app 基本都是安全隐私灾难

他的说法很直接：桌面 AI 应用普遍是安全和隐私噩梦，所以 Replit 跟 Windows 合作给 Replit Desktop 做了一套安全模型，并拿 Christie's（做稀有艺术品托管的那家）作为客户背书，说他们选择 Replit 来做 secure agentic work。

为什么值得看：agent 拿到本地文件系统权限这件事，正在从「先跑起来再说」进入「要能过企业采购」的阶段。

https://x.com/amasad/status/2124604574606795002

▍Nan Yu（OpenAI Codex 产品）：让 vibecoded 项目能 scale 的「秘密 prompt」

他说自己发现了一个让所有 vibe code 出来的项目性能更好、可靠性更高的秘密 prompt，内容是：「Use Postgres」。33 个赞不多，但对做过这类项目的人来说这是个会心一笑的准确吐槽。

https://x.com/thenanyu/status/2124592238974156861

═══════════════════
PODCASTS
═══════════════════

▍AI & I by Every：A New Vision for Human Work After Automation

一句话结论：当模型能力变成所有人都拿得到的地板价，唯一还稀缺的东西是你带着「责任范围 + 视角」去推模型的那一下。

这是 Dan Shipper（Every 联合创始人兼 CEO）在 Every 首届线下大会的闭幕演讲。他会前做了一件很聪明的事：拿公司季度的客户调研数据，一个人干完了原本要五个岗位的活。分析数据、给全公司做一个实时对战小游戏、vibe code 一个自己的 CRM 然后群发冷邮件。按他的记账，这在 2020 年相当于一个数据科学家、一个游戏开发、一个产品营销、一个工程师、一个 BDR，外加二十万美元。他只用一份 Claude 订阅，塞在一周日历的空隙里做完。

他先放了 OpenAI 的 GDPval 数据，专业任务上 AI 盲评胜率从 2024 年 GPT-4o 的 12.4%，到 2025 年 47.6%，到 2026 年约 83%。他说「这个 benchmark 已经饱和了」，然后给出了整场演讲最诚实的一句：「我们完蛋了。」

但真正有意思的是他紧接着的反问：如果这些活 agent 都能干，我为什么还要一个三十人的团队？答案藏在同一份调研里。同一个数据集，同一个 Claude，每个人捞出来的东西完全不同。GTM 工程师 Yash 看到的是首月流失，因为邮件发太多，他直接提了 PR 去改那个数；市场负责人 Douglas 看到的是读者普遍「孤独」，那种「我很爱 AI，但身边人都觉得我疯了」的心理画像；高级编辑 Jack 做了个黏土动画的 Family Feud 问答秀来讲结果。而如果直接问 Claude「你在这份数据里看到了什么」，它给的答案（写作是业务核心、bundle 是留存原因、风险是聚焦和量太大）全都对，但人人都拿得到，所以便宜。

最硬的证据来自他们的 eval 负责人 Mike Taylor 做的一个实验：他试图预测 Dan 在 Slack 里会说什么。能预测，93% 的命中率，但前提是让 Claude 对每个问题同时给 400 个答案，正确答案就在里面。可一旦让 Claude 排序，正确答案只在 top 10% 里的 60% 的时间，基本是抛硬币。也就是说：生成已经很便宜，排序依然几乎做不到。

所以他的推论是，责任划分缩小了搜索空间，个人视角决定了排序，这两件事合起来才是那个「默认 prompt 拿不到」的输出。他还顺手拆了那个常见的反驳，「等 2027 年的 Claude 会排序了，Yash 还有什么用」：2027 年的 Yash 会带着新经验、并且用着 2027 年的 Claude；而 2027 年那侧的 Claude 也得有人 setup、有人写 prompt。真正在比较的其实是「有视角的人在推模型」对「默认 prompt」，两边模型一样，可以约掉。他的原话：

「What's valuable, the alpha, is where you push the model using your perspective and your responsibility for a particular area of the world.」

翻过来就是：值钱的是你用视角和责任去推模型的那一段，而不是模型本身给的默认答案。他把这个叫 allocation economy，你在分配智能这种资源，而不是自己生产知识。

为什么值得看：这是今天唯一一个不靠「能力曲线」讲故事、而是从具体工作流反推人类价值的说法，而且给的证据是可信的具体实验（400 个答案、93%、top 10% 里 60%）。做 agent 产品的话，这段话最实用的一点是：别再把「模型能生成」当卖点，排序和归因才是真正难做、也真正能收到钱的地方。

https://www.youtube.com/watch?v=WstNofgQF5Q

─────────────────
今日其余 builder（Matt Turck、Nikunj Kothari、Ryo Lu、Dan Shipper 的单条推文）没有达到收录门槛，主要是调侃、demo 和未证实的猜测，未纳入。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
