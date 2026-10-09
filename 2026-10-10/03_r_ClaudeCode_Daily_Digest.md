
扫描与质检完成。blogwatcher 扫描因 Reddit IP 层封锁失败（`dial tcp 69.171.235.22:443: i/o timeout`），已按 skill 改走可用通道；`read-all --yes` 返回 `No unread articles to mark as read`（可接受）。本次通过服务端代理 feed2json 读取 Reddit RSS 拿到真实正文与评论，QA `QA_OK sections=6 links=6`，20 条英文引文全部与归档正文精确匹配（VERIFY_OK）。

---

r/ClaudeCode 每日摘要（2026-10-10）

抓取说明：本机对 Reddit 全端点（www.reddit.com / old.reddit.com / api.reddit.com）及所有 redlib 公共实例仍是网络层封锁（http=000、TCP 超时），本次改走服务端代理 feed2json 读取 Reddit RSS，拿到帖子正文与真实评论（作者、正文、时间）。RSS 不提供评论赞数，故每条评论统一标注「赞数：RSS 未提供」，不做高赞排序；帖分来自 arctic-shift 归档快照，近期帖多为快照 1，无参考价值，因此本文不含分数排序结论。以下 6 条均满足「3 条真实非 bot 评论」门槛，且与近 14 天已推送内容无重复。

---

## 1. 冷缓存续跑：回一句「Continue」这一轮要多付 5 倍 token

**摘要：** 一位自称做 meta-harness 的开发者给出实测：会话缓存冷掉（cold cache）后仅回一句「Continue」续跑，这一轮会多付约 5 倍 token。他把 150k 上下文当作分水岭——低于 150k 直接 Continue 无妨，超过后就要谨慎。建议先用确定性裁剪（把旧工具结果换成一行 stub、删掉 thinking 块，不额外调用模型），再用带通知的 UI 提示会话即将冷掉并自动预热缓存；他因为 Haiku 5.5 变便宜而重做了这套方案。对每天开多个会话、跑长任务的用户，这是把「缓存存活时长」当成成本变量来管理的实用视角，也解释了长会话账单为何会突然跳高。

**高赞评论：**
- u/Wrong-Expression-669（赞数：RSS 未提供）："typing \"Continue\" isnt what costs you 5x, the cold cache is. you pay the same re-read of 400k tokens if you type \"refactor the auth module\" or a single period ... at 400-700k you're basicly paying a dollar per 50k of your own history back, thats not a harness problem thats a \"why is there 700k of stuff in here\" problem." 立场说明：他直接把 OP 的「措辞玄学」拉回机制本身——花钱的是冷缓存重读，不是那句咒语，追问的应该是「上下文里为什么堆了 700k」，方向与 OP 不同但更接近账单根因。
- u/Downtown-Pear-6509（赞数：RSS 未提供）："i do a local compact by grabbing the jsonl and rhen removing thinking and tool output, doing a /clear and pasting it back in ... and i can do this while hopping to another llm like clsude to openai and back" 立场说明：给出一个人人可复现的手工替代方案（取 JSONL → 删 thinking 与工具输出 → /clear 后贴回），还顺带说明可在不同厂商模型间来回搬，属于「不依赖工具也能省钱」的一手经验。
- u/Scared-Letterhead949（赞数：RSS 未提供）："Opus 5.5 is so cheap I don't think it matters anymore." 立场说明：代表另一种声音——模型单价已经降到让缓存优化不再值得投入，提醒读者先算清自己实际的每轮成本再决定是否为此写工具。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x1ybwb/

---

## 2. 多个 agent 共用一个仓库，上下文怎么共享？

**摘要：** 提问者所在团队多人多 agent 共用同一代码库：有人用 Claude Code、有人用 Codex，各自维护上下文，导致 GitHub 上出现冲突；他问社区有没有让不同 agent 共享记忆的做法，并担心上下文不该进 git 时如何做门禁。回复的主流答案是「靠流程而不是记忆系统」：每条工作流配一个 plan.md，新 agent 从上次进度接手，撞到上下文上限时由 stop hook 触发交接 skill、更新 plan 再开新线程；也有人让每个会话在 main 之外独立 checkout、分支存活不超过一天，合并前先读 main 上的新增内容。最有价值的提醒是：真正的坑往往不是 git 冲突而是规则冲突——一条分支先动手，另一条在途分支照旧手写，文件不同 git 不报错，却缺了构建所需的二进制。

**高赞评论：**
- u/Cultural-Ad3996（赞数：RSS 未提供）："I run many sessions on one repo. Each works in its own checkout off main and its branch lives less than a day ... What still bites is a rule, not a conflict. One branch moved hand-written browser launches into a shared helper. Another branch already in flight added a launch written by hand. Different files, so git flagged nothing, and the new one lacked a binary the build needs." 立场说明：最贴近实战的一条，指出现有 diff 工具看不见「语义/规则级冲突」，这是多 agent 并行最容易被漏掉的失效模式。
- u/Specific_Yam_4666（赞数：RSS 未提供）："I run each workstream from a plan.md file, each fresh agents just picks up where the last left off. Handover is automated, so when an agent hits its context cap a stop hook runs and they call a handover skill, update the plan, and start the new thread with a fresh agent ... I'd recommend thinking of context sharing as something that driven by good processes, rather than a memory system." 立场说明：把「共享上下文」重新定义为流程问题并给出 hook + skill 的具体实现，同时明确反对把它做成 memory.md 那种记忆系统。
- u/VegetableSir7788（赞数：RSS 未提供）："are they disagreeing about what to build or just editing the same bits at the same time? id figure that out before adding shared memory ... otherwise its easy to end up building a management system for the agents instead of the thing you wanted them to build" 立场说明：先诊断冲突类型（是目标分歧还是同一处并发编辑）再决定要不要上共享记忆，避免把精力花在给 agent 造管理系统上。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x1vju8/

---

## 3. 实测：Haiku / Sonnet / Opus 5.5 当子代理，6 个真实任务的成本与准确率

**摘要：** 作者拿自己项目里 Opus 5.5 已经做过的 6 个真实任务，让 Sonnet 5.5、Haiku 5.5 在 high effort 下重跑，再逐条对照标准答案。代码检索（应改的 48 个文件）三家命中数接近：Opus 45、Sonnet 44、Haiku 44，但成本是 6.17 / 1.38 / 0.44 美元，Haiku 性价比明显胜出；网页调研与事实核查则 Opus 更稳，Haiku 会把大量正确句子误标为错误（30 条对 Opus 0 条），「照它改会删掉半篇正确文章」。他补测 Haiku xhigh：调研质量接近 Opus，但慢一倍且仍不可靠于核查。最终分工是 Haiku 做代码检索、Opus 做调研与核查、Sonnet 用于允许小错的场景——非常具体的一条子代理模型路由经验。

**高赞评论：**
- u/vladgladi（赞数：RSS 未提供）："Useful test, thanks for checking against real answers instead of vibes. I route about 40 agents by task type, and the split that held up for me is not by difficulty but by what happens after. If the output is read by a person or only reported, the cheap model is fine. If the output triggers an action (a file changes, a post goes out, another agent builds on it), it either goes to a bigger model or a bigger model checks it." 立场说明：给出比「按难度分模型」更可操作的判据——按输出后果分流（被阅读 vs 触发动作），并点出代码检索是「漏文件看起来像干净结果」的陷阱。
- u/shravanrevanna（赞数：RSS 未提供）："on the fact-checking run, were those 28 false \"wrong\" flags from Haiku actually reading sources, or judging from memory without fetching?" 立场说明：追问 Haiku 的误报是「读了源但判断错」还是「根本没抓源只凭记忆」，直接决定这套结论能否迁移到自己的核查流水线，属方法论层面的关键提问。
- u/benchmaster-xtreme（赞数：RSS 未提供）："I'd be interested in seeing the same test being run with Haiku at xhigh. AA shows a pretty large performance jump from high to xhigh." 立场说明：要求把 xhigh 档纳入对照（OP 随后补了 xhigh 数据：价半、慢一倍、核查仍不可靠），推动结论从 high 单点扩展成完整的档位曲线。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x1e7ts/

---

## 4. 让模型「按提示词自动选 effort」的小工具，以及 effort 与缓存的关系

**摘要：** 作者做了 Claude Code 小工具 effortless：在输入框上方加一条 bar，由 Haiku 5.5（有 TypeSafe key 则用 Jev）读每条提示词判定难度并自动设定 effort，必要时把简单提示切到更便宜的模型，本体会话与缓存保持不变；bar 还会在缓存即将冷掉时提醒、在话题切换时建议交接。他给出约 8 万次自己请求的统计：缓存读取约占成本 76%，输出只占 8%；effort 主要影响工具调用次数而非回答长度；在 Opus/Sonnet 5.5 上切 effort 不破坏缓存，但在 Fable 5.1 与更早 Opus 上会重写 56%-100% 的缓存，所以自动模式在这些模型上暂停。评论区把话题推进到官方文档细节与 effort 的本质。

**高赞评论：**
- u/ghost_operative（赞数：RSS 未提供）："you dont want to change the effort mid session ... the necessary effort isnt about how long your prompt is ... effort is about how much you need to agent to explore the codebase vs how much your giving it information upfront in the prompt." 立场说明：对「按提示词长度猜 effort」这条基本假设提出反驳，指出真正的变量是「需要 agent 自己探索多少代码库」，对工具的核心判据是实质性质疑。
- u/ChocolateGoggles（赞数：RSS 未提供）：引用官方文档原文 "On Opus 5.5, Sonnet 5.5, Haiku 5.5, and Fable 5.1 with an API key or a Claude subscription, changing effort keeps the cache, and Claude Code applies the new level without asking. This doesn't apply on Amazon Bedrock, Google Cloud's Agent Platform, or a Claude apps gateway, or when you set CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS or your organization has a HIPAA configuration." 立场说明：贴出权威依据并感叹「这么重要的行为竟然没什么人知道」，同时点明 Bedrock / GCP / 网关 / HIPAA 等不生效的例外，是整串里信息密度最高的一条。
- u/Yogesh991（赞数：RSS 未提供）："Effort change is now supported and doesn't recache everything from start" 立场说明：一句话确认切 effort 已不再全量重算缓存，把 OP 关于「在 Fable/旧 Opus 上会重写缓存」的警告限定为版本/模型相关，属于纠正适用范围的补充。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x19b2c/

---

## 5. Opus 5.5 之后还需要 Fable 吗：额度账、/advisor 与「顺手纠偏」

**摘要：** 帖子问：Opus 5.5 出来后还有人在用 Fable 吗？多数回复表示已把 Opus 5.5 当日常主力，Fable 只在需要大局思考或独立评审时上场。有人算了笔账：Fable 要值得用，不只是效果更好，而是「每单位额度更值」——若它消耗 2 倍额度、周上限却只有一半，就补不回自己的成本。更主流的用法是把 Fable 当 /advisor 的第二视角，或让 Fable 出计划、Opus 5.5 再指挥一批 Opus/Sonnet 代理去执行。评论还集中吐槽 Opus 的「顺手纠偏」：明明只问 A，它却跑去谈 B、清理无关的陈旧注释，需要额外指令拉回，这正是部分人仍留恋 Fable 的地方。

**高赞评论：**
- u/Pleasant_Curve_9024（赞数：RSS 未提供）："My problem is that fable doesn't just have to be better in order for me to want to use it, it has to be better per usage. If it drains 2x the usage and has a limit of only 50% of the weekly, and it takes me 1.5x the time/prompting/energy to get a similar level of result out of opus, fable doesn't make up for its own cost." 立场说明：把选型判据从「谁更强」换成「每额度产出」，是额度敏感用户最容易忽略的成本视角，也解释了为什么「更好的模型」未必值得开。
- u/Individual_Solid_944（赞数：RSS 未提供）："I was using it regularly and was hitting limits constantly. Then I started using opus for most of the tasks that I would otherwise hand to fable. And the results are so good and much cheaper - and indistinguishable from fable in almost all cases. Oh, and they get done faster as well." 立场说明：给出从 Fable 迁回 Opus 的完整动机链（常撞额度 → 更便宜 → 结果几乎无差别 → 还更快），是可复现的个人切换经验而非情绪表态。
- u/MaqeSweden（赞数：RSS 未提供）："Using it briefly to create important plans, then letting Opus 5.5 coordinate a bunch of opus and sonnet agents to execute on Fable's plan." 立场说明：给出具体的分工流水线——Fable 只出计划，Opus 5.5 指挥 Opus/Sonnet 代理落地，把贵模型用在最上游的规划上，是用量控制的可落地做法。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x1poui/

---

## 6. 对照测试：Haiku 5.5 够不够当主力 coding agent

**摘要：** 作者在一个真实的中型混合语言代码库（Rust 核心 + 遗留脚本层）上设计了对照测试：让 Haiku 5.5 在低/中/高 effort 下，对上 Sonnet 5.5、GPT-6 Luna、GPT-6.1 Sol，任务包括两个含糊 bug 修复、一份埋了 9 个 bug 与 2 个诱饵的 code review、两个棘手规格实现，以及一个「报错指错方向、照做会更糟」的判断题；答案与隐藏测试都在跑之前写好。意外发现是：规格明确的任务几乎人人满分，说明自包含编码任务已无法区分当代模型；真正拉开差距的是 agentic 任务（跨语言边界迁移逻辑并遵循仓库的隐式约定），Haiku 中档已可追平 Sonnet。评论区把口径补到「有没有反馈回路」这一层。

**高赞评论：**
- u/Poretga99（赞数：RSS 未提供）："That simply means you do not have a feedback loop ready for your agent. Just instruct it to build the project and it will find the compilation errors itself." 立场说明：把「经常撞编译错误」直接归因到缺少反馈回路，给出「让它自己构建、自己发现错误」的具体做法，对评测与日常使用都适用。
- u/1-800-methdyke（赞数：RSS 未提供）："Two years ago, models could write code mostly one file at a time, and tool use was very iffy. Agent loops were just beginning to show up for short horizon tasks. Haiku 4.5 would have fit right in near the top. Haiku 5.5 is where we were a year ago." 立场说明：用一年/两年前的 agent loop 能力作为标尺来解释「便宜档已够用」的原因，帮助读者判断这个结论有多少来自模型进步、多少来自 harness 成熟。
- u/c0reM（赞数：RSS 未提供）："In practice it doesn't, because nobody would choose to use a worse model when Opus or other smarter models exist for complex tasks. But it's easy to remember the \"past\" of 6 to 12 months ago with how the previous models made us feel when they came out. But that's often a rose tinted glasses view." 立场说明：提醒「便宜模型够用」在真实生产中不一定成立——复杂任务上没人会主动选更弱的模型，并指出对旧模型的怀旧往往是玫瑰色滤镜，给整串热潮降温。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x132yy/
