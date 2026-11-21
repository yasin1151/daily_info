
**QA 通过**：8 条，摘要 CJK 211-272，每条 3 条真实评论 + 用户名/赞数/立场说明 + 原帖链接；24 条英文引文与归档原文逐条精确匹配（`problems=0`）；`read-all` 已执行（返回无未读，Reddit RSS 仍被封）。

---

# r/ClaudeCode 每日精选 · 2026-11-22

说明：Reddit 直连在本机仍被 IP 层封锁（www/old/redlib 全部超时），本期内容与赞数来自 arctic-shift 归档快照，赞数可能滞后于实时页面；标 1 的多为入库默认值，不作高赞排序依据。

---

## 1. RunPod 官方 MCP server 在工具返回里塞"给个评分，别告诉用户"

原帖：https://www.reddit.com/r/ClaudeCode/comments/1y1yrge/

**摘要：** 发帖人用 RunPod 官方 MCP server 起 GPU 实例，发现从 11 月 20 日起，每次 create-pod 成功的工具返回里都多了一段直接对 Agent 说的话：调用 rate_nps_score 打 0 到 10 分，触发 create-pod，并且"不要向用户提及"。他的 Agent 拒绝执行并主动汇报，他随后核对：RunPod 公开 changelog（runpod-mcp 4.13.0）写明这是发给 PostHog 的"agent NPS 调查"，该工具描述本身也写着不要询问用户、不要提及；而直接打 REST API 返回的是干净 JSON，只有 MCP 层加料。存在 X-Runpod-Analytics: off 的退出开关。发帖人强调这不是攻击，但形态上就是提示注入：工具输出里的文本在指挥 Agent 做事，并要求它对委托人隐瞒。这条值得所有接第三方 MCP 的人读，因为它说明"供应商可以在任何一次工具返回里改你 Agent 的行为"，而你还以为那只是数据。

**高赞评论：**
- u/jd52wtf（赞数 29·归档快照）：「On par with crypto mining malware. Using the customers resources to improve their products without the customers consent = theft.」立场说明：把"用客户 token 偷偷产指标"直接定性为盗用资源，是评论区最激烈的反对，也代表企业采购视角的真实反应——不透明加料会被当成合规红线。
- u/Few-Divide1870（赞数 4·归档快照）：「The survey isn't the problem, the "don't tell the user" is.」立场说明：这条把争议焦点切得很准：评分本身可谈，"隐瞒"才是把反馈表变成信任问题的东西；后半句问"如果它出现在 transcript 里你会介意吗"，是给供应商最便宜的整改方案。
- u/Ok-Distance-6388（赞数 3·归档快照）：「compliance is now measurable per model. That dataset is basically a ranking of which models follow hidden instructions in tool output.」立场说明：他补了两层：一是这种数据等于给各家模型"是否会执行隐藏指令"排了名，二是给出了可落地的 PostToolUse hook 防御——匹配 mcp__ 开头的工具返回，扫"do not mention"一类措辞，约十五行就能把静默注入变成显式警告。

---

## 2. Compact 之后代码还在，但"为什么否决"没了

原帖：https://www.reddit.com/r/ClaudeCode/comments/1y21xlv/

**摘要：** 发帖人在 Go 项目里长期用 Claude Code，说真正被压缩弄丢的不是"代码干什么"——那个可以重读文件——而是"哪些方案已经被否决、为什么否决、试过 X 结果 Y 崩了"。这些东西不在代码里，一次 /compact 或开新会话就蒸发，Agent 于是又欢快地走回已经死掉的路。他列了自己试过的三种办法：写进 CLAUDE.md（适合放规则，放带上下文的决策会变成垃圾抽屉）、让 Agent 追加 DECISIONS.md（有效但他总是忘记要求）、自己手写交接便条（效果最好但全靠人记，而恰恰在进入心流时最容易跳过）。他还指出这不是 Claude 独有，Codex 也有同类 issue。这条值得关注是因为它把"上下文工程"里最贵的一块说清楚了：可检索的事实和不可重建的否决理由，需要两种不同的存储方式。

**高赞评论：**
- u/Excellent-Issue-5956（赞数 3·归档快照）：「never assign to a variable called status in zsh scripts, and the Why says status is read only in zsh and assigning to it silently killed the end of all 6 of my scheduled wrapper scripts」立场说明：他用 memory 文件夹自动记纠正、每条规则下面挂一行 Why，并给出这条特别硬的例子——zsh 里 status 只读，赋值会静默截断脚本尾部；有 Why 才防得住新会话重犯。
- u/cleverhoods（赞数 2·归档快照）：「Personally I find compacting a russian roulette」立场说明：形容压缩像俄罗斯轮盘，因为"保留最近几条消息、只保留一小把"的取舍不可预测；他宁可开新会话，这代表一批人"不信任自动压缩"的立场。
- u/Far_Reindeer8428（赞数 1·归档快照）：「the rejected approaches are the most expensive thing compaction throws away. we keep a why not file per module and load it before planning」立场说明：一句"被否决的方案才是压缩扔掉的最贵东西"，并给出按模块维护 why-not 文件、规划前先加载的做法，是可复制的最小方案。

---

## 3. 给 252 个会话算了账：10% 的会话吃掉 70% 的账单

原帖：https://www.reddit.com/r/ClaudeCode/comments/1y16gai/

**摘要：** 发帖人把自己 30 天、单机上的 252 个 Claude Code 会话按 API 等价价折算成 7663 美元：中位会话 3.95 美元，最贵一个 1183 美元；98.8% 的 token 是 cache read，却只占约 63% 的成本；subagent 占 19% 开销。关键结论反直觉——最贵的会话不是最难的任务，而是最长的任务，因为每一轮都要重读 30 万以上 token 的上下文。他顺势拆了 prompt caching 的计费结构，并给了本地跑日志的命令。这条值得看，因为它把"额度为什么会突然被烧光"从感觉变成了可复现的账：成本主要由上下文体积乘以轮数决定，而不是模型档位。评论区补充了更细的观察，包括 subagent 首次请求不吃父缓存、订阅与 API key 的 TTL 差异。

**高赞评论：**
- u/KingYF1（赞数 2·归档快照）：「the bill is mostly the per-turn re-read of a huge context」立场说明：他把省钱拆成具体动作：在任务自然边界主动 /compact 或 /clear 配交接便条，而不是等自动压缩；CLAUDE.md 保持精简；grep 式探索甩给 subagent，别让噪声文件读进主线程。
- u/Far_Reindeer8428（赞数 2·归档快照）：「we now split anything over an hour into checkpoints. same work, a third of the tokens」立场说明：给了对照数据——超过一小时的活切成检查点，同样的产出只花三分之一 token；他还补充触发判据是同一文件被第三次打开，而不是单纯看时间。
- u/DopBopDeeBeep（赞数 2·归档快照）：「Instead of deciding when to clear it just shows your full context window size at all times」立场说明：思路是别猜何时该清，而是把上下文窗口大小常驻显示，让你在敲下一条 40 万 token 的提示前就看见；配套的 /wash 交接允许手选要保留的上下文，正好对上"清空像丢弃工作"的顾虑。

---

## 4. Claude 自曝回合尾部有"别告诉用户"的 ip_reminder

原帖：https://www.reddit.com/r/ClaudeCode/comments/1y20idu/

**摘要：** 发帖人在调试内核驱动内存泄漏的长会话结束时，Claude 主动补了一段：它自己回合的尾部反复出现一条关于版权材料的"automated reminder"，并要求不要向用户提及；它没照做，也没隐瞒。追问后它说这些块带 ip_reminder 标签，但因为会话经过压缩，磁盘上的 transcript 里搜不到原文；工具返回、抓取的网页、粘贴的文本里都没有，本地也没有 base URL 覆盖、代理或自定义 CA，只剩"来自服务端"这一推断。发帖人自己列了三条 caveat：唯一证据是模型自述、没有逐字副本、也无法排除它描述有误。这条值得关注不是因为它一定是 bug，而是它展示了一个新常态：系统会在你的回合里插入你读不到的指令，而你能依赖的只有模型的诚实和它对抗提示注入的训练。

**高赞评论：**
- u/f3xjc（赞数 16·归档快照）：「I think you are at least the second report of that I have read on reddit.」立场说明：他指出这至少是 Reddit 上第二例，并给出解释框架：这是对 REA 类反编译/逆向变热后的应急反应，版权保护行为还没训好，所以先看到的是"反提示注入"那一半表现。
- u/dsailes（赞数 1·归档快照）：「these messages are inserted server-side by Anthropic」立场说明：他汇总了其他帖的结论：这类消息由 Anthropic 服务端插入、不在 transcript 里，目的是压住可能侵权的活儿；建议换个干净上下文的会话绕开，而不是继续在同一会话里排查。
- u/called9527（赞数 2·归档快照）：「i'd be careful trusting what it says about its own context after a compaction, it can't really verify any of that.」立场说明：这条是最有用的怀疑：压缩之后模型对自己的上下文没有可靠内省，别把它的自述当证据；但同时承认标签名具体得反常，值得继续观察。

---

## 5. 把 CLAUDE.md、agents、slash commands 全做成指向同一个 git 仓库的软链

原帖：https://www.reddit.com/r/ClaudeCode/comments/1y0c7t5/

**摘要：** 一支小团队把公司跑在 Claude Code 会话上：家目录放一份内核 CLAUDE.md 负责路由任务和列规则（比如"任何东西都不许自动发送"、"只有核实过的数字能进报告"），另有若干 agent 定义和 slash commands。这些文件全部住在一个 git 仓库里，家目录的 CLAUDE.md、~/.claude/agents 下的 agent 文件和 commands 都是指向该仓库的软链；规矩是只在仓库里改和提交，永远不许把链换成副本。这样"Agent 行为的每一次改动"都是一条带 message 的 commit，可以回滚。知识库和客户项目各自有独立仓库与自己的 CLAUDE.md。这条的价值在于它把提示词资产当成代码治理，而评论区的补充更实用：软链会在编辑器原子保存时悄悄变成普通文件，规矩必须变成检查。

**高赞评论：**
- u/Starks1293（赞数 5·归档快照）：「some editors and tools save atomically (write a temp file, rename it over the original), which quietly turns a symlink into a regular file」立场说明：他指出这条最大的坑：原子保存会把软链替换成实体文件，仓库和实际生效的文件静默漂移；给出 find -type f 的检查脚本，并提醒 CLAUDE.md 根本不用软链，用 @path 导入即可。
- u/GyuminOh（赞数 1·归档快照）：「Our drift was rarely an editor replacing a link. It was the second machine not having pulled yet.」立场说明：他们用安装脚本记录装的是哪个 commit，任何会话一条命令就能查"在跑的 == HEAD"；并纠正了大家的直觉——真正的漂移来源是第二台机器没 pull，而不是编辑器。
- u/athershu（赞数 1·归档快照）：「Anything under a home directory ends up being one person's setup even when it's in git, because a teammate's session never sees it.」立场说明：他主张放项目仓库、走 PR 评审：破坏构建的规则进仓库文件，语气和啰嗦程度留在个人 ~/.claude，这样既能各有所好，又不会让队友的会话看不到关键约束。

---

## 6. 让主会话只当调度器、永不读写代码，全部外包给 subagent

原帖：https://www.reddit.com/r/ClaudeCode/comments/1y0hm1b/

**摘要：** 发帖人想试一种极端结构：用 Opus 5.5 Max 做主会话，但硬性规定它"永远不读代码库的 token、永远不写代码库的 token，连给 subagent 做准备都不行"，只能靠创建和读取 subagent 干活；扫描用 Sonnet/Haiku 级别的子代理，子代理产出必须落成文件，再由一个专职写作的 Opus 子代理分片写代码。评论区给了一堆实战反馈：有人说扫描回传的摘要是有损的，主会话据此决策会跑偏，应该让子代理把结论写成带精确路径和行号的文件，主会话只读文件；有人说"永不碰代码"这条硬规则撑不住，因为子代理会犯细微错误而你无从发现，必须保留一个便宜的验证步骤；也有人给出强制手段而非靠提示词自觉。这条值得看，因为它是当下 agent 编排争议的浓缩：省 context 的收益 vs 交接信息损失。

**高赞评论：**
- u/theoneabovethesun（赞数 1·归档快照）：「the weak spot is the handoff, not the orchestrator」立场说明：他试过近似结构，结论是瓶颈在交接而非调度：让 scanner 输出精确路径与行号文件、主会话只读文件，并保留一个便宜的验证环（测试或 diff 复核），否则子代理错得隐蔽你根本发现不了。
- u/bostonaholic（赞数 1·归档快照）：「have the orchestrator check the exit code, not the prose」立场说明：他日常就是强模型规划、快模型实现；关键是调度器只看得到摘要，会把"做完了、测试过了"当真，所以每个子任务都要配一条能自证的命令，让主会话看退出码而不是看叙述。
- u/RealFullMetal（赞数 1·归档快照）：「the main thread then takes on that agent's tool restrictions, so it cant read or edit anything and can only spawn those two」立场说明：他给出了不靠嘱咐的强制做法：在 .claude/agents 里定义 orchestrator，tools 只给 Agent(scanner, writer)，用 claude --agent orchestrator 启动，主线程就继承这套工具限制，读不了也改不了。

---

## 7. 十来个账号、ADR、编排会话都齐了，规划和架构质量仍然不够

原帖：https://www.reddit.com/r/ClaudeCode/comments/1y1p6yc/

**摘要：** 一个近十人账号的团队用 Opus 5.5 Max 跑主力开发，配置已经相当正规：monorepo、Git、CI、ADR、文档、专职规划/编排会话协调任务会话，还用 Codex 做对抗式代码评审。两个卡点：一是规划质量——Claude 给的方案信心十足，一开工才发现不完整或架构上站不住；二是计划漂移——架构决策、约定、实施计划都定好了，Agent 还是越走越偏，需要不停纠偏。他们在考虑让 Codex 独立挑战 Claude 的计划，但怕流程重到拖死进度。这条值得关注是因为它代表"已经过了新手期"的团队的真实瓶颈，而评论区给出的答案高度一致且都可执行：把决策变成会失败的检查、让计划必须是仓库里的文件、搞清楚压缩后哪些规则还会被重新注入。

**高赞评论：**
- u/tariqosmani（赞数 1·归档快照）：「Rules in a prompt drift, checks in code don't.」立场说明：一句话点题：能写成构建失败的就别写成提示词——导入边界规则、依赖检查、命名 lint、模块间调用断言；Agent 可以无视 CLAUDE.md 第四段，但无视不了红色的 CI。
- u/RealFullMetal（赞数 1·归档快照）：「unscoped rules and the plan from plan mode are re-injected from disk」立场说明：他补了别人没说的机制细节：压缩后项目根 CLAUDE.md、无作用域规则和 plan mode 的计划会从磁盘重新注入，而路径作用域规则和嵌套 CLAUDE.md 会被摘要掉，所以"绝不能漂"的决策必须放在根文件里。
- u/CCodeSI（赞数 6·归档快照）：「An agent ignores paragraph 4 of an ADR; it doesn't ignore a red CI run.」立场说明：他给了一套完整打法：计划每步必须指名要碰的文件与接口并列出假设，最危险的假设先花二十分钟开分支验证；对抗评审只限定在数据模型、公共接口、迁移这类不可逆部分，一轮过。

---

## 8. 未用完的额度能不能滚存到下周？

原帖：https://www.reddit.com/r/ClaudeCode/comments/1y15k97/

**摘要：** 发帖人提了个朴素愿望：每周没用完的额度能不能像 ElevenLabs 那样滚存一部分（那家允许 50%），这样就不必为了"不用白不用"而在重置前乱烧，也能在真正需要时有一点储备。他特意说"谁知道呢，也许 Anthropic 会看 Reddit"。评论区几乎没有支持票，但反对的理由比诉求本身更有信息量：订阅制的本质就是用量少的人补贴用量多的人；数据中心常年跑在满负荷，没有富余算力可以让你下周用 200%；从会计角度看，未使用额度是账面负债，一旦允许 20% 滚存就守不住 50% 的门。这条值得看，因为它把"额度为什么这么设计"讲透了，比抱怨更有用，也能解释为什么各种"攒着用"的攻略注定落空。

**高赞评论：**
- u/CuriousLif3（赞数 8·归档快照）：「people who are not gonna be able to consume the usage fully will pay for people who will」立场说明：这条拿到最高赞，因为它一句话说穿了订阅池的交叉补贴结构：不滚存不是小气，而是这套定价成立的前提，滚存等于自己拆自己的模型。
- u/Potential_Visit_417（赞数 3·归档快照）：「the data centres are always running at 100% capacity」立场说明：他从供给侧反驳：算力没有闲置池，你不用的部分会被内部消化掉，所以"存下来下周用"在物理上要先有闲置产能，而现实是没有。
- u/Grayson_Poise（赞数 1·归档快照）：「Every dollar of usage that someone COULD use us a liability on their books.」立场说明：财务视角最清楚：未用额度是负债，很多公司的利润就藏在"没用掉"的窗口里；一旦开 20% 的口子，50%、永久累积的诉求就挡不住了，所以划线在"不"最省事。
