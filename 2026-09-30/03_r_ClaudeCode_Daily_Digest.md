
r/ClaudeCode 每日推送 · 2026-09-30

本期 7 条，覆盖 r/ClaudeCode 过去约 83 小时的讨论，主线是 Opus 5.5 / Sonnet 5.5 的档位与编排、上下文与额度管理、以及 agent 记忆与验证方法。说明：本轮 Reddit 直连、old.reddit 与 redlib 公共实例全部不可达（http=000），数据取自 arctic-shift 归档 API；帖子与评论赞数均为入库快照，可能滞后，已逐条标注，未据此做高赞排序。引号内为社区原话（英文原句，未做改写）。

---

## 1. 长时自主任务该开哪档 effort：不是 max，而是 medium 加编排

**摘要：**
发帖人一直把所有 agent 挂在 max effort 上跑，直到每周额度被反复刷满，才回头问：在大型代码库上跑长时自主任务（重构、找漏洞、闭环验证），到底该用哪一档 effort。评论区的高赞答案相当一致：不是 max，而是 medium 加一个 orchestrator 带多个子代理。有人给出具体分工，orchestrator 自己不干活，负责并行调度三四个任务，用 Haiku 做侦察、Sonnet 做已经规划好的实现，并按前后端、Figma、测试、重构分设专门子代理。也有人把整套流程做成 specs 到 plans 到 work items 的依赖图，每个工作项挂一个实现 skill，例如 TDD，再用一个 orchestrate-wave skill 并行推进，关键是把模型固定在 skill 里而不是靠临场提示。对应的现实代价也摆得很明白：有人一次跑完一个 sprint，约两万五千行代码，要 8 小时再加 3 小时走 PR。对想把额度换成产出的人，这帖是一份现成的档位与编排参考。

**高赞评论：**
- u/haslo（赞数 49·归档快照）："Medium. One orchestrator, many sub agents, my own project specific agent framework guidelines." 他后续补充 orchestrator 只做协调，Haiku 负责侦察、Sonnet 负责已规划好的实现。立场说明：全场最高赞，直接把"长跑该用哪档"从 max 拉回 medium，代表社区主流做法。
- u/mrsmiley32（赞数 18·归档快照）："I do a whole sprint at a time ... takes about 8 hours and then 3 hours to PR." 立场说明：把额度换算成具体工作量，提醒这套玩法本质是"睡前挂机、第二天收 PR"。
- u/corben99（赞数 3·归档快照）："Build skills with defined sub agents that pin models. Then build flows of the skills." 他补充工作项之间带依赖图，每个挂一个实现 skill，再由 orchestrate-wave 并行调度。立场说明：给出把模型与角色固化进 skill、而不是临场指定的工程化路径。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1wrvhg1/

---

## 2. 怎么验证"省 token 插件"的宣传：社区集体泼冷水

**摘要：**
发帖人刚上手 Claude Code，被满屏"砍掉一半 token"的插件、CLAUDE.md 模板和缓存技巧刷屏，分不清哪些是实测、哪些是营销，于是问老手该怎么验证。评论区几乎是集体泼冷水：多数 token 优化器毫无价值，真正起作用的极少，而且高度依赖具体任务；除了真正的压缩器，任何声称省 token 的 skill 或文档最多省 2-3%，弄不好反而让消耗增加 5-10%；更有人直接说不会装这些陌生人推的插件，认为优化来自对上下文、缓存、提示词和模型选择的理解，而不是外挂。最有操作价值的一条给出验证方法：别盯某个时刻的上下文大小，而是同仓库、同任务、同模型，比较整个 run 的总 token、耗时、重试次数和最终质量——如果一个所谓"省 30% 上下文"的插件多跑了两轮，它其实让事情更糟。对天天被这类工具种草的人，这帖等于一份筛子。

**高赞评论：**
- u/Academic-Network-418（赞数 8·归档快照）："Vast majority of token optimizers are worthless. There's very few that actually work, and even then it entirely depends on what you're doing" 立场说明：定调式回答，把"要不要装优化插件"变成一个默认怀疑的问题。
- u/Bulky_Blood_7362（赞数 4·归档快照）："None of them actually works unless it's an actual compressor like headroom and stuff like that." 他补上量化判断：这类东西"will save 2-3% tokens or at worse will increase token consumption by 5-10%"。立场说明：给出可验证的量级，说明大多数"优化"落在噪声区间。
- u/tnh34（赞数 3·归档快照）："Token optimization comes from understanding context, caching, prompts, and choosing the right model for the job" 立场说明：把优化从外挂工具拉回基本功与模型选择，是本节最可执行的结论。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1wrqhc9/

---

## 3. Opus 5.5 用 high 还是 medium：讨论很快转向上下文纪律

**摘要：**
发帖人听到一种说法：Opus 5.5 用 medium 不只省 token，写代码还比 high 更好，high 只在知识型工作上更强，于是发帖求证。高赞回答没有纠缠档位，而是转向更根本的上下文管理：有人从不用 compact，直接清空或开新会话；有人建议先把工作拆成 GitHub issue，再每个 issue 开新会话或 /clear；更激烈的说法是 /compact 等于脑叶切除，应该写一份 handoff 文档再开新会话继续。也有人主张永远不要用 auto-compact，一旦它触发，说明早就越过了模型的"聪明区间"，模型大约在 200k token 后就开始缓慢退化，所以要主动管理上下文，并且 handoff 比 compact 好，因为你可以检查和修改它。还有一条很实用的判据：如果开新会话必须重新解释某件事，那件事大概就该被沉淀成一个 skill。对额度紧、又要长跑的人，这套上下文纪律比档位争论更值钱。

**高赞评论：**
- u/Additional-You9968（赞数 6·归档快照）："I never use compact, I clear the chat (or essentially make a new chat)" 立场说明：代表"能重开就不压缩"的一派，直接改变日常会话管理习惯。
- u/oprimido_opressor（赞数 3·归档快照）："/compact is a lobotomy. Create a handoff doc and continue from a fresh session" 立场说明：用一句狠话概括压缩的代价，给出 handoff 替代 compact 的具体动作。
- u/devlifedotnet（赞数 3·归档快照）："If you're building something plan it into gh issues first. Then new chat or /clear for each issue." 立场说明：把上下文管理前置到任务拆分阶段，是这套纪律里最容易落地的一条。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1wrmw8c/

---

## 4. agent 看不见自己的额度与上下文：长跑无人值守的两堵墙

**摘要：**
发帖团队已经让 Claude Code 半自主跑任务，任务自动记录、人工介入很少，但有两堵墙它看不见：任务跑到一半撞上额度上限而停下，或者在中途被 auto-compact 打断而丢失线索。根因是模型既看不到自己的额度，也看不到上下文有多满，更无法自己触发 compact，于是永远需要人插手。评论区给出不少落地方案：有人把"上下文与额度"一行注入每条消息之前，并配一条低额度时的处理规则；他们实测过规则措辞的影响——"剩 10% 转交新会话"这句原版在 10 次里只过 8 次，因为模型把规则里的免责说明当成了"下一轮再确认"的借口，把说明挪出判断句、并改成"立刻开始交接，哪怕任务做到一半"之后变成 10/10。也有人用 hook 在触限时暂停并提示用户，或者在任务切换时写文件再 /clear。对想让 agent 无人值守跑几周的人，这帖把"看不见的墙"和绕开它的具体写法都说清了。

**高赞评论：**
- u/kuroudo_ai（赞数 1·归档快照）："the rule's wording matters as much as the numbers." 他公开了实测细节：低额度交接规则的措辞从 8/10 改到 10/10，关键是别让免责说明变成模型拖延的理由。立场说明：把提示词工程落到可复现的通过率上，是本节最硬的一条。
- u/covati（赞数 1·归档快照）："Write a handoff linking to your ticket system and /clear." 立场说明：给出用票据系统承接交接、再 /clear 的简单流程，不依赖模型自觉。
- u/RomanKryvolapov（赞数 1·归档快照）："the model always detects when it is running out of subscription limits; it pauses and warns the user" 他还提到 Claude Code 2.1.277 起会在 5 小时额度触限时给一次"收尾额度"，属于软着陆而非油表。立场说明：既给出 hook 方案，也点明官方机制的边界：仍看不到早期预算。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1wt9ss3/

---

## 5. Sonnet 5.5 该放进 agent 栈的哪一层

**摘要：**
Sonnet 5.5 发布后，发帖人发现自己说不清新模型到底该放进 agent 栈的哪个位置——以前便宜模型、编码模型、贵模型分得很清楚，现在能力都够强，真问题变成哪类工作该路由给谁。评论区的分歧很有代表性。有人已经动手把实现代理从 Opus 5.5 high 换成 Sonnet 5.5 high，结论是速度明显更快、结果相当；他还给出三层审查的对照数据：同一个把 12 万行测试重构、拆成 17 个切片的任务，Opus 5.5 出了 12 个硬违规、7 个轻微问题，Sonnet 5.5 只有 2 个硬违规、0 个轻微。另一派用法是把 Sonnet 放在子代理里读代码库、汇总资料喂给 Opus 做规划，非编码的日常任务也交给它。反对意见则是根本不需要分层，用 Opus 5.5 xhigh 跑所有事也没超额度。对正在定模型分工的人，这是少见的带对照数据的讨论。

**高赞评论：**
- u/Outrageous-Issue9722（赞数 1·归档快照）："I switched my implementation agent to sonnet 5.5 high, was opus 5.5 high. Seems a lot faster for the same result." 他给出对照："Opus 5.5 12 hard violations, 7 minor" 对 "Sonnet 5.5 2 hard violations, 0 minor"。立场说明：用三层审查的违规计数做 A/B，是本节唯一带数据的证据。
- u/itsvivianferreira（赞数 1·归档快照）："I mostly use Sonnet in subagents to go through codebases and summarize data for Opus in planning mode" 立场说明：给出"小模型读、大模型规划"的经典分层，顺手把非编码任务也归到小模型。
- u/unconceivables（赞数 1·归档快照）："It doesn't, because I can run Opus 5.5 xhigh for everything without running out of usage." 立场说明：反方代表，说明分层的前提是额度真的会成为瓶颈。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1wtdgwy/

---

## 6. 子代理为什么不能动态选 effort：现有工具的边界

**摘要：**
发帖人想要的是一种动态编排：让 xhigh 的 orchestrator 自己决定把研究员放 medium、把写代码的代理放 high、把摘要代理放 low，而不是提前把每个子代理写死在 Markdown 文件里。评论区先给了变通方案：既然子代理工具不收 effort 参数，就把 effort 作为唯一差异做几个通用代理文件，比如 worker-low、worker-medium、worker-high，描述写成"什么时候用这一档"，由 orchestrator 按名字挑；注意如果 spawn 时又传了 model，会覆盖代理文件里的 model。更关键的一条指出工具其实已经存在：ultracode 底层的 Workflow 工具里，每个 agent 调用都能单独指定 model 与 effort，orchestrator 写脚本时就选好了，不需要任何代理文件，但前提是别漏传，否则会继承会话的 xhigh。发帖人随后指出 Workflow 的短板：代理之间不能互相通信，只适合交任务、拿交接的模式。对正在设计多代理编排的人，这帖把现有工具的边界划得很清楚。

**高赞评论：**
- u/Excellent-Issue-5956（赞数 1·归档快照）："The Workflow tool (what ultracode runs on) already does this. Each agent() call in the script takes its own model and effort" 他补充常规 Agent 工具只支持 model 覆盖，所以那一条路才需要 worker-low/medium/high 文件。立场说明：指出需求已有原生实现，避免大家继续手搓代理文件。
- u/kuroudo_ai（赞数 1·归档快照）："make the effort level the only thing that differs between a few generic agents, and let the orchestrator pick by name." 立场说明：给出零成本变通方案，并提醒 spawn 时传 model 会覆盖代理文件设置。
- u/Xterm1na10r（赞数 1·归档快照）："the workflow tool doesn't let agents message each other and communicate afaik" 立场说明：点出 Workflow 的能力缺口，说明为什么发帖人仍想要 Agent 工具原生的 effort 参数。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1wtdxcx/

---

## 7. 凭什么让用户当 AI 的记忆管理员

**摘要：**
发帖人做的是基于 Claude API 的 agent 产品，用户抱怨都指向同一件事：要靠自己反复粘贴上下文，AI 才能记住之前几十轮里建立的东西，不粘贴就全忘；即便粘了，检索也常把已经被推翻的旧决定翻出来。他质疑凭什么让用户当记忆管理员。评论区没人同情他，但技术回答很实在：有人指出扁平对话日志本来就不适合当作跨 50 轮演进的项目事实源——检索能精确找到一条旧决定，却给不出正确答案，因为它已经被取代，正确做法是维护显式的项目状态，记下当前决定、来源消息与被谁取代，日志只当支持性历史。也有人列出成熟方案：Mem0、开源的 Hindsight，或自建并接受配置成本。还有人给出工程化答案：用几十张 SQL 表把人物、地点、事件抽取出来，AI 通过工具查表，三天自动压缩但重要信息落表。对做 agent 记忆的人，这帖是一份反面清单。

**高赞评论：**
- u/Ok-Category2729（赞数 7·归档快照）："flat conversation logs are the wrong source of truth for a project that evolves over 50 sessions" 他给出的修法是"keep explicit project state with current decisions, their source messages, and which decisions they supersede"。立场说明：一句点破"检索正确但答案错误"的根因，是本节最有价值的设计判断。
- u/Maasu（赞数 5·归档快照）："Mem0 is a popular one. Hindsight I heard good things on, it's free and open source." 他自己维护 forgetful，但坦言配置成本较高、不太适合发帖人的场景。立场说明：给出可选的现成记忆层，并诚实标注自建方案的代价。
- u/verstands（赞数 -1·归档快照）："I'd keep a canonical, versioned memory store behind the agent: facts with timestamps, source sessions, confidence, and project scope." 他主张冲突时显式暴露或询问一次，而不是静默覆盖旧事实。立场说明：分数为负但内容契合 OP 的直觉，给出可测试的版本化记忆设计。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1wqrf16/
