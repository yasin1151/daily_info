
# r/LLM 今日热帖 · 2026-11-09

说明：Reddit 全端点（www / old / redlib / RSS）当前仍无法直连，本期内容取自 arctic-shift 归档快照。赞数为抓取时的快照值：评论多的大帖已形成真实梯度，新帖多为归档入库时的默认值，因此下文不做「高赞排序」结论，只按信息量挑选。

## 1. Opus 5.5 疑似「在毁我的代码库」：是体感变差，还是 effort 档位用错

**摘要：** 楼主称最近一小时里，在四个不同问题上都收到「改动多个类」的修复方案，追问「一行改动不行吗」之后模型又改口承认可以，认为模型给出了过度工程且不准确的建议，还贴了四张截图。帖子拿到 181 分、108 条评论，是本期最热的一条，评论区迅速分裂：一派认同「今天明显变笨、疯狂写冗余测试」，另一派认为问题出在把 effort 顶到 max，长上下文里 max 会把一行修复膨胀成多文件重构。这场争论的价值不在谁对，而在于它给出了一套可操作的归因顺序——先查 effort 档位、CLAUDE.md 与 handoff 是否膨胀、账号档位是否不同，再谈模型侧回归。

**高赞评论：**
- u/jbogez（赞数 212·归档快照）："Max effort might be your problem, try medium. It's overthinking." 立场说明：把「变差」归因到 effort 档位，建议先用 medium 跑，改完再单独让模型做一次代码审查查漏，而不是让 max 在同一轮里自我审查越改越多。
- u/adamslowe（赞数 33·归档快照）："I'm glad it's not just me. It's written 3000 lines of tests for 1000 lines of code. Batshit! And I'm on medium effort!" 立场说明：提供了反驳 effort 假说的关键反例——自己已经在 medium 档，仍然出现为 1000 行代码写 3000 行测试的膨胀，说明不只是档位问题。
- u/JonesJoneserson（赞数 25·归档快照）："Most of my day is spent on a company account -- seems like a lot of people agreeing with you here" 立场说明：提出账号档位假说，怀疑厂商对非企业账号降配；这是评论区唯一可验证的结构性解释，比单纯吵「变笨」更有追踪价值。

原帖：https://www.reddit.com/r/LLM/comments/1xphsj9/

## 2. 「说模型偷偷降级的人，请先给基准测试」——反向杰文斯悖论的辩论

**摘要：** 楼主受够了每天出现的「我用几个月了，我发誓它变差了」式帖子：零基准、零证据，只有「我发誓」。他并不否认降级可能真实存在，而是提出一个反向杰文斯悖论——模型越强，你越敢给开放式提示、越敢少做代码审查，于是错误自然更容易被看见；新模型刚发布时大家规矩地提示，摸清能力边界后就不断放权，反而制造了「越来越差」的错觉。评论区随即反击：秘密降级本来就不会体现在公开基准里；而「体感」在缺乏透明度的前提下已是唯一可得的信号。这是本期方法论密度最高的一条讨论。

**高赞评论：**
- u/Sea-Contribution6219（赞数 34·归档快照）："Bro is asking for benchmarks from the 'trust me bro' industry" 立场说明：一句话点破争议本质——要求体感派拿出基准，等于要求他们否定自己唯一的证据来源，所以这类要求通常不会得到回应。
- u/privatetudor（赞数 6·归档快照）："Why would the downgrade being secret prevent it showing up in a benchmark?" 立场说明：逻辑上最有力的一击：既然是模型能力变化，秘密与否都不妨碍它在自有测试集上体现；除非变化只发生在路由、限流或量化层。
- u/Direct-Detail-7031（赞数 4·归档快照）："trust the vibes, if you feel like the model is off its game, then what that means is, we need to pay closer attention to what it's doing" 立场说明：拥护体感派，主张在厂商不透明的现实下把「感觉不对」当成预警信号，用更密集的复核去验证，而不是等一份不会出现的官方基准。

原帖：https://www.reddit.com/r/LLM/comments/1xpqs9t/

## 3. 把自动压缩窗口从 967k 调到 280k，同一套餐多出约 25% Opus 用量

**摘要：** 作者做了一款在 Mac 上跑 Claude Code 的客户端，为了压住 Opus 消耗，用自己两周的对话做了回放实验：默认在约 967k token 触发压缩，若改成 280k，总花费只需原来的 79%，相当于同一订阅多出约 25% 的 Opus 额度。原因很直接——每个请求都带整段上下文，400k 以上的请求只占 21% 的调用量，却吃掉 45% 的输入 token。代价是压缩后的「记忆」变差：综合回忆率从 95% 掉到 70%，把最近的提问和回复在压缩后重新贴回去能回到 86%；低于 300k 再往下调收益就很小，因为压缩本身的开销会吃掉节省。

**高赞评论：**
- u/holyknight00（赞数 6·归档快照）："going beyond 300k tokens is stupid and, a waste of time and money." 立场说明：直接跳过测量细节给出结论式立场，代表评论区里「1M 上下文属于营销参数、实际只有成本没有收益」这一派。
- u/Demien19（赞数 4·归档快照）："1M context is overkill and waste of context tokens. Make yourself updatable .md files and keep context to 200k compact and disable 1M." 立场说明：给出可落地的替代方案——用可维护的 Markdown 交接文件承载状态，配两个环境变量把窗口压到 200k 并关掉 1M，比调压缩阈值更彻底。
- u/bipolarNarwhale（赞数 2·归档快照）："I just took a chat that had 600k context window used and ran /compact and the result was.... 8% - 84.7k/1m." 立场说明：拿自己一次 600k 会话压缩后只剩 8% 的结果质疑原文的 70% 回忆率口径，提醒这类「压缩后记得多少」的结论高度依赖测量方式。

原帖：https://www.reddit.com/r/LLM/comments/1xph5fl/

## 4. 用 Markdown 加知识图谱替掉向量检索：ERP 场景里 RAG 的瓶颈也许不在向量

**摘要：** 作者为一个复杂的 ERP 系统搭 AI 助手，最初走标准 RAG：切块、embedding、向量召回再喂给模型，但效果不满意，问题常常不在模型而在召回的知识本身——模型能看懂单张表，却看不懂表、模块与业务规则之间怎么连。于是他改成给 Claude 一套手工编写、严格组织的 Markdown 知识库：每个模块做什么、业务逻辑、工作流、模块间关系、例外条件，数据库部分则写清每张表代表什么、为什么存在、字段在业务上怎么用，再配一份显式的关系图。他自称准确率提升到 95%，但强调不是新架构，只是想找人验证。

**高赞评论：**
- u/Coindef（赞数 8·归档快照）："pick a fixed set of questions you already know the right answer to, run both systems blind, and score them the same way." 立场说明：认同「跨表约束正是向量检索的死角」，但要求先做盲测再信 95% 这个数字；同时提醒多租户场景要把过滤放在数据库侧而不是提示词里，模型很擅长忘记自己是谁。
- u/frepont（赞数 3·归档快照）："At some point if your graph gets sufficiently large you end up with two problems - links that SHOULD exist don't get created and links that DID exist start getting orphaned." 立场说明：指出这套方案真正的天花板：图一大就有该连没连上、连过的又悬空两类腐化，靠修复脚本或会话钩子只能拖延，最后仍要上重型维护机制。
- u/SawToothKernel（赞数 2·归档快照）："What I don't understand is why you would describe the module structure/table usage/etc. When that knowledge already exists as code." 立场说明：最强的反面意见：结构信息在代码里已有单一事实源，手工文档等于制造第二份会漂移的真相；真正值得写下来的只有代码表达不了的「为什么」。

原帖：https://www.reddit.com/r/LLM/comments/1xpj88x/

## 5. 30GB 开发机被闲置会话吃爆：OOM 杀掉的都是 19–24GB 的 Claude Code 进程

**摘要：** 作者在一台开发机上并行跑多个 Claude Code 会话，还会让会话派生子会话做杂活，且从不关。七月里内核 OOM killer 四天触发五次，被杀进程每次都是常驻 19–24GB 的 Claude Code，而不是任何容器；十月机器（30GB 内存）三天内又冻死三次，查下来是闲置数天、什么也没在做的会话合计占了约 14GB。他一次性归档了 185 个闲置超过三天的会话、停掉 12 个旧服务，可用内存从 2.0GB 回到 10.5GB。结论很朴素：跑大量 agent 时，会话进程本身才是机器最大的租户，而没有人会去关它。

**高赞评论：**
- u/ScrumptiousChildren（赞数 4·归档快照）："With the CC harness the only way to reduce process cost is subagents which don’t spawn standalone, expensive claude processes." 立场说明：把内存问题和 harness 设计连起来——只有子代理不另起独立进程，才能真正压低常驻成本；他自己给会话设了 24 小时闲置自动回收，只杀进程、不动缓存与记录。
- u/athershu（赞数 1·归档快照）："Our fix was to stop treating the session as the unit and treat the task as the unit." 立场说明：团队级解法：一个任务一个会话加一个 worktree，任务验收后连 worktree 一起丢弃，并让子会话也登记成任务，避免「子会话没有主人所以没人关」。
- u/bostonaholic（赞数 1·归档快照）："A session with no transcript writes for a day is a candidate to close, keeping the transcript on disk." 立场说明：最简可执行规则——一条分支只留一个活跃会话，一天没写记录就关掉但保留记录；并提醒 OOM 前先量闲置会话，别错怪那个看起来很忙的会话。

原帖：https://www.reddit.com/r/LLM/comments/1xpksr1/

## 6. 自建 CI runner 跑测试快约 3 倍，还省下每月数百美元

**摘要：** 楼主正文只有标题，评论区却把这笔账算得很清楚：当构建速度成为瓶颈，GitHub 托管 runner、Blacksmith 这类云 CI 的费用很快会超过一台本地服务器的成本。多位实践者给出具体配置——本地服务器加 Mac mini，各挂几个 runner，32GB 内存的 Ryzen 5800H 上性能约为 GH 托管 runner 的 3 倍、任务耗时减半；有人把仓库整体迁到自建 Forgejo，顺手退掉 Copilot 订阅。也有人提醒风险随公开度上升：公开仓库挂自建 runner，等于让任意 PR 的 workflow 在你的机器上执行，可被用来探测漏洞。另有反馈称 PR 太重时自建仍慢，最终改用租用服务器托管 runner。

**高赞评论：**
- u/TheOwlHypothesis（赞数 14·归档快照）："Be careful if your repo is public or you're basically letting anyone poke your machine for vulnerabilities running GitHub actions." 立场说明：把话题从省钱拉到安全边界：自建 runner 的收益成立，但公开仓库场景等于对外开放一台能跑任意 action 的机器，必须先做隔离。
- u/Background-Ad9540（赞数 3·归档快照）："Set up a local server and mac mini and added a couple of runners each and I am saving 100s of $s now and keeping the speed up." 立场说明：同一路径的规模化版本：构建节奏一快，云 CI 成本立刻失控，本地加 Mac mini 混合挂 runner 后每月省下数百美元，且认为这类运维过去门槛太高、现在靠 agent 才做得动。
- u/asiancouple3648（赞数 1·归档快照）："Going from GH to my own runners on a 32gb ryzen 5800h is 3x the performance of GH runner. The jobs run twice as fast." 立场说明：提供了唯一可对标的硬件数字：32GB Ryzen 5800H 约 3 倍性能、任务时间减半，代价是风扇噪音，属于典型的用闲置硬件换云账单。

原帖：https://www.reddit.com/r/LLM/comments/1xpk5wu/

## 7. 有状态还是无状态 agent：主流答案是把状态放进仓库，让会话随时可杀

**摘要：** 楼主转行重新学编程，想以系统设计为主线，于是问社区编码 agent 应该走无状态还是带状态（A2A）路线。他自述的核心规则是：仓库是唯一事实源，任何 agent 任何时候接手项目，都能只靠 repo 拿到全部所需。评论区给出的主流答案是「agent 无状态、仓库即状态」——会话随时可以杀掉且不丢东西，重要信息必须活过进程，进 spec、失败测试和 CI；有状态只在单个长任务内部有价值，跨任务保留会话恰恰是漂移和过期假设的来源。

**高赞评论：**
- u/Dorbank_Justt（赞数 2·归档快照）："Mostly stateless, with the state kept in files the agent reads when it starts." 立场说明：落到具体工程形态：每个周期性任务是一个带步骤和参考文件的 SKILL.md，新会话只靠仓库就能接手；他唯一被状态咬到的地方是 Playwright MCP 的登录态，浏览器配置只能被一个会话持有。
- u/thegreatdeployer（赞数 2·归档快照）："running more lanes at once mostly bought me merge fights, and those ate more usage than the actual work." 立场说明：从额度角度反推并发策略：一次开太多并行车道只会换来合并冲突，而冲突消耗的用量比真正干活还多；2 到 3 条车道、各自分支、当天可合的小票才是可持续节奏。
- u/torvalds75（赞数 1·归档快照）："Without them a fresh session proposes X again, and because X looks reasonable it can get through tests and CI." 立场说明：补上无状态方案最容易被忽略的缺口：实现型 agent 最需要的恰恰是被否决的决定，缺了记录，新会话会重新提出旧方案并通过测试，因此决定要挂在对应 issue 上而不是全量重读。

原帖：https://www.reddit.com/r/LLM/comments/1xpkxtb/
