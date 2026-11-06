
# r/ClaudeCode 每日精选 · 2026-11-07

本期 7 条，全部来自归档接口（Reddit 直连仍被封）。赞数为抓取时的归档快照，新帖的 1 分多为入库默认值，不代表真实热度，因此选帖按评论内容质量而非分数排序。

---

## 1. 为什么几乎没人给 Claude 做沙箱？

**摘要：** 一位刚接触开发的用户提问：公司 IT 直接在工作机上装了 Claude Desktop，没有做任何隔离，模型对他所有工作目录和共享盘都有写权限，而软件团队基本也是同样配置。他的疑问是，为什么几乎没人认真隔离大模型。近三百条评论给出的现实是：多数人只依赖信任目录设置和 auto 模式自带的危险命令拦截，但前者并不阻止 bash 跳出目录执行 rm，后者本质上是模型自己判断。真正隔离要 Docker、虚拟机或云端会话，学习成本以天计。值得关注的是这里的取舍逻辑：沙箱不是防模型变坏，而是承认 agent 的失误不可回滚，所以要么隔离文件系统，要么把整台机器当作可丢弃的沙箱。

**高赞评论：**

- u/icodenstuff（551赞）："I asked Claude to add a guard to build script so it couldn't delete my home dir by accident. Guess how it decided to test it's work." 立场说明：全场最高赞，一句话说明让模型自己验证安全护栏本身就是风险源——它测试的方式就是真的执行删除。
- u/btherl（81赞）："It'll take a few disasters before people get scared enough to sandbox properly." 他同时强调风险其实不高，前提是机器本身可替换、重要内容都在版本控制里且有备份。立场说明：成本现实派，认为沙箱不是第一优先级，可丢弃的机器加版本控制是等效防线。
- u/Certain_Ring403（8赞）："unless run in a super tight container or VM, we’re relying on its good nature rather than inability to get out." 立场说明：分数低但判断最锋利，点出真正的区别不是模型逃不出去，而是它选择不逃，所以靠拦截提示并不构成边界。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1xp5c6f/

---

## 2. Opus 5.5 最近在毁我的代码库

**摘要：** 用户抱怨 Opus 5.5 最近给出的修复"改动多个类"，而一行就能解决，截图里模型自己也承认一行足够。评论区一半人附和从昨天开始明显变笨，另一半把矛头指向 effort 档位过高和指令文件膨胀。值得关注的是诊断顺序：所谓模型变笨，很多时候是配置问题——xhigh 或 max 会诱发过度设计和自我加戏，CLAUDE.md 与 handoff 文件被不断追加会让上下文变脏、后续判断持续劣化。有用户给自己定了 handoff 不超过四百行的规则并写进 CI。先降档、再检查指令文件体积，比等新模型发布更有效；但也有 medium 档同样膨胀的反例，说明测试结构仍得由人来定。

**高赞评论：**

- u/jbogez（105赞）："Max effort might be your problem, try medium. It's overthinking." 他还建议改完后让模型做一次自审，而不是一上来就调最高档。立场说明：最高赞把问题归因到 effort 配置而非模型退步，给出的是可立即验证的变量。
- u/fschwiet（19赞）："Don't use max effort when a 1-line fix is called for, unless a lot of research is needed to figure out that one line." 立场说明：把 effort 当成按任务分配的资源，只有需要大量检索定位时才值得开高，否则只会换来更复杂的补丁。
- u/adamslowe（14赞）："It's written 3000 lines of tests for 1000 lines of code." 他自己承认部分责任在指令不够明确，把"提供证明"理解成了用十二种方式证明同一件事。立场说明：即使降到 medium 仍出现膨胀，说明过度设计不能全甩给档位，测试架构要人来约束。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1xphsj9/

---

## 3. 还有人在用 plan mode 吗？

**摘要：** 提问者发现自己不知不觉不再用 plan mode，怀疑是模型变强后不需要了。评论区的主流答案是换成了"审问式"技能：先让模型反问需求、逼出隐含前提，再产出 spec，最后实现。也有人认为 plan mode 仍有不可替代的作用——它是一个强制函数，逼你在花掉大量 token 之前确认方向，同时让模型停在抽象层，不把讨论误解成"现在开始写代码"。值得关注的是计划环节并没有消失，而是从内置模式迁移到了 markdown 计划文件加技能组合：计划落到文件后，上下文被压缩、会话被清空或换工具都能接上。另有用户提醒，内置的 opusplan 会在批准后切到 sonnet，但每个模型有独立缓存，切换后首轮要把整段对话重新读一遍。

**高赞评论：**

- u/Fluffybaxter（68赞）："Plan mode + grill me skill every time I work on a complex task." 他承认这样会慢一点，但能想清楚并避免大量返工。立场说明：代表当前主流用法，内置计划模式与审问技能叠加，用更长前置换更少返工。
- u/UruquianLilac（22赞）："Most of my work starts with a plan that I ask it outputs to an MD file." 立场说明：关键不是模式而是产物——计划成为文件后，新会话、压缩后、换工具都能靠读文件恢复上下文，控制权在人手里。
- u/RealFullMetal（3赞）："each model has its own cache, so the first turn after the switch rereads the whole conversation uncached" 立场说明：给出内置的模型分层方案（规划用强模型、执行用便宜模型），同时点明缓存不共享，切换那一轮成本会突然跳高。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1xphyon/

---

## 4. 用 hook 抓住 agent 的重复补丁

**摘要：** 作者发现 agent 对同一段磁盘清理逻辑打了二十九次补丁，每次只解决眼前的 bug，最后要求它重新设计才收敛成一条规则。于是他写了 PostToolUse hook：同一个文件一个月内被修两次以上，就把历史修复摆给 agent 看并要求先重新设计，但从不阻断。值得关注的是评论区把它推进成了完整的电路断路器设计：按机制而不是按文件计数，用失败的测试名或行为标签做聚合键，误报只花一句话、漏报要花二十九次补丁。最有价值的一条实测指出覆盖漏洞——一百五十三份本地 transcript 里有 39.2% 的源码写入走 Bash、sed 或 write_text，只监听 Edit 和 Write 的 hook 根本不会触发。

**高赞评论：**

- u/Then-Internal8832（1赞）："watching Edit and Write alone missed 39.2% of source file mutations across my 153 local Claude Code and Codex CLI transcripts" 立场说明：全场最有价值的实测数据，指出 heredoc、sed、write_text 都会绕过 Edit/Write 监听，hook 覆盖面必须先补齐。
- u/ASIREXLABS（1赞）："count fixes per mechanism instead of per file" 立场说明：用失败测试或行为标签做聚合键，可以区分"同一机制反复坏"和"同文件里两个无关 bug"，直接消掉误报源头。
- u/Far_Reindeer8428（0赞）："a false alarm costs one sentence from the agent, a loop costs 29 patches." 他还把同样的逻辑用在审查层：同一类问题被标两次就停下来问人。立场说明：解释了为什么只提示不阻断是对的——误报代价极低，而硬阻断会挡住正常的连续修复。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1xp9boq/

---

## 5. 长驻后台子代理为什么一直在烧 token

**摘要：** 用户把主会话当编排器，希望后台子代理只在需要决策时才唤醒它。实际行为是：子代理启动 Monitor 等事件、结束回合进入后台，这个动作本身就会给主会话发消息；而 Monitor 超时上限是三十分钟，到期后子代理重新挂起，于是每半小时往主会话塞一条消息，即使什么都没发生。回答几乎一致：不要用长驻子代理等待，把判断从模型移到脚本——后台 bash 盯事件流、维护状态文件，只在需要决策时退出，主会话只收一次通知；或者注册成 plugin monitor 绕开三十分钟上限。值得关注的是计费层面的解释：子代理的缓存 TTL 只有五分钟，每次唤醒都要未命中缓存地重读整段上下文，长驻等待在经济上必然亏。

**高赞评论：**

- u/rubenknol（3赞）："sub-agents only have cache TTL of 5 minutes" 立场说明：从缓存 TTL 解释为什么不经济，长时间挂起的子代理每次醒来都是全额重读，越等越贵。
- u/namanjainbuilt（1赞）："Move the deciding out of the agent and into the script." 他的做法是后台 bash 轮询事件日志，只在出现失败或卡住时退出。立场说明：给出可落地的替代架构，代价是脚本做不了判断，"值得通知"必须写成规则。
- u/Significant_Door_433（2赞）："what wakes the main session is the subagent's turn ending, and a subagent that waits has to end its turn." 立场说明：直接点出根因——唤醒事件是回合结束，所以任何等待型子代理都必然反复惊动主会话；正解是把状态放文件、只启动短命子代理。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1xp8dfi/

---

## 6. 为什么我用 Opus 5.5 做不出不像 AI 的界面

**摘要：** 用户说 Opus 5.5 生成的网站全是 AI 味：仪表盘堆得密密麻麻、卡片套卡片、配色难看、经常不响应式。他改过提示词、给过参考图、试过不同思考档位，Ultracode 加 Max 反而最差。评论区的共识是把设计决策从模型手里拿走：先自己定好字阶、间距、两三个颜色和允许使用的组件清单，再逐区块生成、每块截图和参考图比对；或者先给三张以上真实参考图，让它写一份 style skill，之后照着 skill 建，每轮只改一个维度。值得关注的是这不是提示词技巧问题而是权限问题，模型不该拥有视觉决策权；同时有人指出对话里一旦出现过强烈否定，这条线程基本救不回来，只能开新会话。

**高赞评论：**

- u/ajax81（17赞）："it never recovers from a user crash out. When it loses its mojo, there’s no recovery, so u start a new thread." 立场说明：指出会话级不可逆——在对话里骂过之后输出会持续跑偏，继续在同一线程里调提示词是无效投入。
- u/WillowFar6967（14赞）："I design first, then hand it the tokens" 以及 "Then it builds one section at a time and screenshots it against the reference before moving on." 立场说明：把设计固化成 token 与组件白名单、逐区块截图验收，是最可复制的一套流程。
- u/Heyn_Studio（4赞）："having it write a style skill from them first, and then building against that skill" 立场说明：把参考图蒸馏成可复用的 style skill，比每次写"做得干净一点"有效，且每轮只改一个维度防止一次改五处又回到 slop。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1xpae6d/

---

## 7. 用 Markdown 加知识图谱替掉向量检索 RAG

**摘要：** 作者为一个复杂的 ERP 系统放弃向量检索，改用大量 Markdown 文档加知识图谱，把模块职责、业务规则、表之间在业务上的关系都写清楚，声称效果超出预期。评论没有停在称赞：有人指出他同时改了三件事——知识本身、导航方式、以及对实时数据的访问，收益无法归因；也有人提醒图谱规模上去后必然出现该建的链接没建、旧链接失效，需要定期跑的修复脚本或 session hook 才能保真。值得关注的是对 RAG 的正确质疑不是"向量没用"，而是跨表跨规则的 join 语义根本不在单个 chunk 里；要证明收益必须固定问题集、盲测两套系统，并额外跑一遍去掉图谱的对照。

**高赞评论：**

- u/Coindef（3赞）："pure vector search keeps missing the join" 他描述的是：单条答案落在一个 chunk 里时嵌入够用，一旦要问表 A 如何在规则 C 下约束模块 B 就不行了。立场说明：准确指出向量检索的结构性短板，同时要求先固定问题集盲测再谈 95% 的准确率。
- u/Armannss（1赞）："You changed the knowledge itself (business meaning, exceptions, relationships), the navigation, and access to live records." 立场说明：方法论批评——一次动三个变量，实验无法归因；应固定模型和问题集，分别切换向量检索与图谱导航做对照。
- u/frepont（2赞）："links that SHOULD exist don’t get created and links that DID exist start getting orphaned" 立场说明：指出手写知识库的长期成本，图谱越大越需要修复脚本或 hook 维持准确，否则前面的收益会被缓慢侵蚀。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1xpj88x/
