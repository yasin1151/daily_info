
# r/ClaudeCode 每日速览 · 2026-11-15

今日 8 条。Reddit 的所有端点仍然被封（`www.reddit.com`、`old.reddit.com`、redlib 公共实例全部返回 000），正文与评论改经归档通道（arctic-shift）取回；赞数是抓取时的归档快照，新帖普遍停在 1，不代表真实票数，也不作为排序依据。

---

## 1. Are people here actually using skills?

**摘要：** 楼主说自己从不用 skills，日常靠 connectors 与 MCP，其余事情直接 prompt，或者让 Claude 自己生成 prompt / handoff 再开新会话；他一直觉得 skills 只是“存好的 prompt”，想确认自己是不是漏了什么。评论区多数人认为 skills 的价值在于把多步骤流程固化成可重复调用的资产，最高赞的操作建议很直接：某个流程要走好几步、且你知道以后还会再做，就让 Claude 把它存成 skill。组织层面有人补充公司自建 marketplace 共享几十个 skill，甚至用 skill 生成 skill、再用 loop skill 串起来跑完整条流水线。反方则质疑每个 skill 的名称与描述都常驻上下文、攒多了会污染 context 预算，主张改用 bash/python 脚本或纯 md 文件。这场争论真实暴露了同一工具的两套心智模型：把 skills 当“流程封装”还是当“脚本替身”，直接决定上下文成本和组织复用方式。

**高赞评论：**
- u/OldNefariousness7899（赞数 63·归档快照）："If you work through a process that takes several steps, and you knew you'll want to do it again, ask it to save it as a skill." 立场说明：把判定条件说得很清楚——多步骤且会重复，才值得固化成 skill，而不是为每个小技巧都建一个。
- u/gaelfr38（赞数 19·归档快照）："At my company, we have our own marketplace and a few dozens of skills shared so that we don't keep reinventing the wheel." 立场说明：这是少见的企业侧落地样本，skill 当内部资产分发，配套 MR 审核与贡献回流的治理做法比工具本身更值得抄。
- u/OkLettuce338（赞数 10·归档快照）："I decompose my planning sessions into tickets with a skill so they all get the same process." 立场说明：展示了 skill 的组合玩法——用 skill 生成 driver skill、再塞进 loop skill，本质是把函数式思维搬到 prompt 层，但也提醒别把复杂度堆到失控。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xw4fby/

---

## 2. I spent 4,500+ hours coding with AI. This is the Claude Code setup I ended up with.

**摘要：** 作者两年多、每天约六小时、累计 4500 小时用 AI 写代码（他明确说明这是估算而非遥测），总结出失败模式从未改变：agent 自己评审自己的计划还觉得很好、过度工程、声称测试通过却没跑、改动不该动的文件。他的解法不是更聪明的 prompt 而是流程：~/.claude/ 下一份全局 CLAUDE.md 放工程原则与安全闸门，小修跳过仪式，架构改动走流水线，破坏性动作先确认。评论区最有共鸣的是“信 diff 不信 agent 摘要”，有人补上仓库级 gotchas 文件记录模型反复犯的错，有人要求 agent 在交付前明确列出“无法验证的部分”，也有人追问全局与项目级 CLAUDE.md 冲突怎么办，作者回答：全局放原则、项目放架构与命令、绝不重复，因为重复会漂移。整串把“agent 说它做完了”这种软声明，换成了可检验的证据链。

**高赞评论：**
- u/Impressive_Winter378（赞数 35·归档快照）："even when the agent says 'no changes needed', i now run git diff first." 立场说明：把这条规则讲到了极端场景——连“没有改动”这种结论都要自己验，因为摘要只是声明，diff 才是事实。
- u/jijialuoke（赞数 3·归档快照）："listing the specific patterns Claude tends to get wrong in that codebase" 立场说明：比通用 critique prompt 更实用的一层——把每个仓库特有的踩坑模式沉淀成 gotchas 文件，避免模型每次重新发现同一个 bug。
- u/biggromania（赞数 2·归档快照）："no proof, no delivery. It has to show the actual output or measured numbers" 立场说明：以及他补的“让它列出无法验证的部分”，把验收标准从“看起来对”变成可追溯的证据清单，落地成本极低。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xw7ylh/

---

## 3. Claude Code 2.1.323: experimental Code Mode (Claude writes JS to call tools), plugin version pinning, permission fixes

**摘要：** 11 月 12 日发布的 2.1.323 引入实验性 Code Mode：Claude 不再逐个调用工具，而是写一段 JavaScript 批量调用工具，由组织管理员开关；同时 plugin.json 支持 engines["claude-code"] 版本范围，插件超出范围就不安装、不更新、不加载；claude plugin validate 开始对 TypeScript hooks 做类型检查；未识别的模型 ID 默认给 1M 上下文（可用 CLAUDE_CODE_DISABLE_1M_CONTEXT=1 回退 200K）。评论里最有价值的是实测：有人在同一个仓库跑了一周，读密集任务收益明确，写任务反而更差，因为一行坏 JS 会让整批工具调用一起失败；另一位解释省 token 的机制是“不再每轮重发工具 schema 与结果”，JS 包装本身只值几百 token。还有人担心它绕开 hook 护栏、可观测性下降。对重度用户，这是一次上下文预算与可控性的重新权衡。

**高赞评论：**
- u/Far_Reindeer8428（赞数 49·归档快照）："we ran code mode on the same repo for a week and the win was real on read heavy tasks. write tasks were worse because one bad js line killed the whole batch of tool calls" 立场说明：目前看到最可信的一手对照，直接给出适用边界——读多写少的任务先上，写任务要谨慎。
- u/Far_Reindeer8428（赞数 13·归档快照，同一作者跟进）："the js wrapper costs a few hundred tokens, the savings come from not resending tool schemas and results every turn." 立场说明：把成本账算清楚了：省的不是包装，而是每轮重复的 schema 与工具输出，因此长任务收益才明显。
- u/joseph-edmondscomm（赞数 9·归档快照）："I assume this then totally defeats hooks based guard rails" 立场说明：提出了被官方文档忽略的治理问题，并建议只对只读工具开启、写操作仍走普通调用以便 hook 拦截，是安全侧最该追的点。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xvw576/

---

## 4. What belongs in CLAUDE.md versus skills or checks when you maintain several real apps?

**摘要：** 楼主自学出身，替几家小企业维护 web 与后台系统，三四个月重度使用 AI，想知道资深工程师怎么判断：一个反复出现的错误该写进 CLAUDE.md、做成 skill、加自动化检查，还是改任务拆法，以及什么内容要故意不放进主指令。回答给出了清晰分层——必须每次都生效、每次会话都要携带的放 CLAUDE.md 或 CLAUDE.local.md；只有关键词命中才值得载入的做成 skill；绝对不能出错的放 hook 或测试，因为 CLAUDE.md 只是建议而非强制。一条很实用的补充是：共享规则写 AGENTS.md，CLAUDE.md 用 @AGENTS.md 一行导入，避免两份文件漂移；并提醒 CLAUDE.md 每次会话全文载入、被当作上下文而非配置，官方建议控制在 200 行以内。对正在从“出错就加一段话”过渡到工程化约束的团队，这套判定标准可以直接落地。

**高赞评论：**
- u/Dorbank_Justt（赞数 3·归档快照）："Keep the shared rules in AGENTS.md and make CLAUDE.md a one line import, @AGENTS.md" 立场说明：多工具并存时最实际的去重方案，一份规则两个入口，避免 Claude 与 Codex 各维护一套说法。
- u/Api-Lord（赞数 1·归档快照）："Anything that must hold every time goes in a hook or test, since CLAUDE.md is only advice." 立场说明：点破 CLAUDE.md 的本质是建议，凡是“必须成立”的约束都得下沉到 hook/测试，这是很多人反复踩的坑。
- u/reach4thelaser5（赞数 1·归档快照）："The front matter of the skill is in every agents context but they only read it when they decide they need it" 立场说明：把 skill 的渐进加载机制说清楚了，也顺带解释了为什么 skill 数量多了仍有固定成本。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xvtoue/

---

## 5. Fable 5.2 as orchestrator, planner, reviewer and Opus 5.5 as implementation agent?

**摘要：** 提问者说 Fable 单独使用太烧额度，想知道能否让 Fable 5.2 负责编排、规划和评审，Opus 5.5 只做实现。高赞回答几乎一致地反着来：用 Opus 5.5 做编排、Fable 只在升级链上做顾问或深度研究，因为绝大多数任务用不到 Fable，真正决定输出质量的是提前搭好的流程与守卫。更激进的方案是把编排压到 Sonnet，规划时才叫 Fable 子代理，执行用 Opus 子代理，再让 Opus 子代理下挂 Haiku 处理工具输出噪音，并尽量关掉 MCP，因为所有 MCP 定义都会进系统提示词、被每个子代理继承。也有人实测 Fable 规划加 Opus 执行时，Opus 会忽略步骤化指导，换成 Sonnet 编排更顺、漂移更少。核心结论一致：编排层应该最便宜，贵模型只放在真正需要判断的位置。

**高赞评论：**
- u/TechgeekOne（赞数 15·归档快照）："I've been preferring Opus as the orchestrator with Fable as an advisor only. I get far more usage that way" 立场说明：给出的是可复制的降本结构，且强调 Fable 只在“说不清想要什么”的模糊设计任务上才值得上。
- u/Riverside3102（赞数 1·归档快照）："I'm at around 15B tokens a month at work on one Team Premium seat and don't hit the limit." 立场说明：少见的规模数据点——15B token/月不撞上限，靠的是小任务 one-shot、大任务才开子代理与 superpowers 流程，而不是靠更强的模型。
- u/ClickableName（赞数 1·归档快照）："Make sure to disable as much MCPs as possible, as all MCP definitons will be sent to the system prompt which all the subagents get." 立场说明：指出了多层子代理架构里最容易被忽略的隐性成本，MCP 清单会被每一层继承，删减比换模型更省钱。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xwckod/

---

## 6. Code review kept passing duplicate APIs my Claude Code agents built. Now a hook names the owner as they write

**摘要：** 作者发现代码评审抓不到 agent 造出的重复 API，因为另一份拷贝从来不在 diff 里：一次审计就找出两个只差大小写的成本查询 API、一个定义了两次的命令 API 和两份接口契约。他的做法是加一个 Write/Edit 之后触发的 hook，把新写的函数、类、路由、表拿到项目生成的 API 索引里、忽略大小写与词序地比对，命中就点名已有实现的所有者、要求 agent 去扩展它，但从不阻断。第一版全仓 grep 要 6.1 秒、超过 hook 两秒超时，等于什么都没说；改成读预计算索引后约 45 毫秒。评论区补了另一种思路：先约定 done list，再由没有参与实现的 agent 对着运行中的程序逐条证明。作者随后真做了重命名实验，六次评审里两组坏实现全被抓到，但也误拦了 12 次正确改动中的 4 次，原因都是项目缺 API 索引。

**高赞评论：**
- u/oyren-ai（赞数 1·归档快照）："precomputing a normalized symbol and route index so the post-edit hook finishes in 45ms instead of grepping the whole repo is super clean." 立场说明：抓住了这个方案真正的工程点——hook 的有效性首先取决于它能否在超时内跑完，慢一秒就等于没有护栏。
- u/m-ritter（赞数 1·归档快照）："What fixed it for me was agreeing a done list before any code, then having a separate agent that did not write the change prove each point against the running program." 立场说明：把检查前移到派活阶段，并要求评审者与实现者不共享假设，是对“自评自审”结构性缺陷的正面回应。
- u/PutBrief9403（赞数 1·归档快照）："It helps, but it's a request, not a check, so nothing catches it when the agent skips it." 立场说明：一句话点明全局指令与写入时检查的区别，也追问了索引新鲜度这个真实缺口，作者承认目前只信任磁盘上的索引。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xq52lp/

---

## 7. Technical Debt (Black Box Apps) solved by future Claude?

**摘要：** 楼主观察到越来越多公司已经看不懂自己的代码库，每次迭代更贵、slop 继续堆积，于是提出一个赌注：干脆继续制造技术债务、构建黑盒应用，等“Opus 8”出现再让它读完整仓库、合并所有冗余 helper 与不必要的抽象。评论区吵成两派。一派认为 slop 与否正在变得不重要：维护问题在 AI 独占代码库后消失，性能问题可以局部修，写给人看的可读性不再是优先级。另一派给出更强反驳：AI 在好代码库里表现明显更好，越乱的库越容易让它继续犯错并更乱，这和人类面对遗留系统没有本质差别，只是成本临界点来得更晚；在真实遗留系统里让 agent 乱改，后果是钱和合规风险。折中方案是每次提交后自动生成文档当缓冲，或先写测试再让模型放手重构。

**高赞评论：**
- u/baseball-44（赞数 35·归档快照）："It is quickly becoming unimportant whether or not code is slop." 立场说明：把“可读性服务的是人类”这个前提摆到台面上，逻辑自洽但默认了 AI 会无限变强、且没人需要为当前代码负责，这个前提值得警惕。
- u/faiface（赞数 23·归档快照）："AI performs much better in good codebases than bad codebases... The more sloppy a codebase is, the more likely the AI is to both make mistakes and make it even more sloppy." 立场说明：全场最硬的反驳，用模型行为本身否掉了“债留给未来的模型”的幻想，也指出差别只是临界点更晚。
- u/muffchucker（赞数 8·归档快照）："That line moves every couple months, and it's moving quickly. I maintain ancient systems (20-55 years old) that predate SQL dbs and last year AI couldn't remotely help." 立场说明：来自遗留系统维护一线的经验修正——能力边界确实在快速移动，但“已经能帮上忙”和“可以不管代码质量”是两件事。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xqe2tm/

---

## 8. i'm not using big models and it's eating so much!! i started fresh and in few minutes i'm 83%

**摘要：** 一位每月 20 美元的 Pro 用户抱怨自己“没用大模型”却几分钟就吃掉 83% 的 5 小时额度，正文只有一句让 Claude 修。评论区最不客气的回答指出他其实在用 Opus 4.8——既贵又是老版本，方向完全错了；另一位 Pro 用户说自己平均能连续干两小时才撞到 5 小时上限，差异可能来自同时开十几个子会话。真正有信息量的是成本口径：Opus 5.5 输入 4 美元、输出 20 美元每百万 token，比 Opus 4.8 的 5/25 降了约 20%，但更该看单任务成本；想省额度应该降到 Sonnet 5.5，而不是降回更老的 Opus。这条串的价值在于把“额度变少了”的情绪抱怨，拉回到模型档位、并行会话数量、单任务成本这三个可调旋钮上。

**高赞评论：**
- u/Just_Run2412（赞数 3·归档快照）："Opus 5.5 is priced at $4 input and $20 output per million tokens, a 20% cut from the $5/$25 of Opus 4.8" 立场说明：把争论从情绪拉回定价表，并强调真正该看的是 cost per task 而非每百万 token 单价，这个换算方法比结论更有用。
- u/Brapchu（赞数 4·归档快照）："I'm using Pro as well and I can work like ~2 hours minimum on average on my projects before I run out of the 5 hour limit on Opus 5.5" 立场说明：同档位用户的对照样本，说明额度崩塌通常不是模型问题而是用法问题，先排查并行子会话和上下文膨胀。
- u/Wilbis（赞数 1·归档快照）："They might be running 10 chats at the same time that were spawned by the main chat." 立场说明：指出了最常见的额度黑洞——fan-out 出来的子会话，每个都在独立计费且往往无人监控。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xvzgsu/

---

抓取说明：blogwatcher 扫描因 Reddit RSS 仍不可达而失败（`dial tcp 69.171.235.22:443: i/o timeout`），`read-all --yes` 返回无未读；正文与评论经 arctic-shift 归档通道获取，441 个候选、去重后 420 个新帖、逐个探测 40 个候选的评论树（0 失败）。最终稿已通过 QA（8 节、8 链接、摘要 150–300 中文字）与 24 条英文引文的逐字校验（0 处不符）。
