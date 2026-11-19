
**r/ClaudeCode 每日摘要 · 2026-11-20**

Reddit 三个入口（www、old.reddit、redlib）仍被网络层封锁，返回均为 000；本期内容通过归档通道（arctic-shift）取回，共扫描 745 个候选，去重后剩余 712 个新帖，逐个拉取评论树后筛出 8 条可操作话题。赞数为归档快照，可能滞后于线上实时值；标 1 的多为入库默认值，不代表真实热度，因此不做“高赞排序”结论，评论按平台默认的 best（最佳优先）顺序并结合内容质量挑选。

---

## 1. 初级工程师把生产库密码贴进 Claude 排查迁移，团队该怎么定规矩

**摘要：**

一位初级工程师在失败的数据库迁移上卡住，直接把生产环境连接串连同密码贴进 Claude Code，让它排查，四分钟后问题解决。他反问：这是公司的 Claude 账号，数据能去哪儿？发帖人仍然轮换了密码，并演示了用 1Password、Infisical 注入密钥、让 agent 在不接触明文密码的前提下操作数据库的做法。这个帖子把“该给 agent 什么权限”从抽象原则变成了具体事故：凭据会留在会话 transcript 里，留在下一次粘贴里，也会留在下一个初级工程师模仿的工作路径里。评论区几乎一致认为轮换密码是唯一正确动作，分歧在于是追责个人，还是追责“让初级工程师持有生产库密码”的流程，以及是否该允许 agent 直连生产。值得团队关注的是三条可落地规范：密钥托管注入、只读副本、SQL 由人执行。

**高赞评论：**

- u/EC36339（赞数 1434·归档快照）："You gave the prod db password to a junior?" 立场说明：最高赞没有骂 AI，而是质疑权限管理——真正的事故点是初级工程师手里握着生产库密码，agent 只是把既有问题暴露出来。
- u/srggrch（赞数 298·归档快照）："Sending secrets to AI agent is bad, giving it direct access to production DB is worse" 立场说明：把风险拆成两层：明文凭据流向第三方模型是一层，让 agent 具备直连生产的执行权限是更危险的一层，后者才是要优先控制的。
- u/rubenknol（赞数 38·归档快照）："it will sit inside the transcript and the transcript is accessible to org admins when doing a data dump" 立场说明：给出运营侧做法：团队用 skill 加上下文层规则，一旦有人把生产凭据贴进 transcript 就告警，同时保留一条“确实需要用生产凭据”的合法通道，而不是一刀切禁止。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y071r3/

---

## 2. 除了多开 agent，还有什么在无声烧 token

**摘要：**

发帖人问：除了并行跑 agent，还有哪些日常动作在浪费 token。回帖把账算得很具体。排在前面的主要来源是截图：每次 UI 校验产生的模拟器截图都会留在上下文里，并随着后续每一轮对话重新发送，一张图要付很多次钱。其次是上下文体积乘以轮次：一个大窗口撑到接近上限才自动压缩，成本远高于在三十万 token 左右带着交接笔记重开新会话。第三类是配置层面的持续损耗：拿 Opus 或 Fable 去干 Haiku 级别的活、让 prompt cache 过期后继续长会话、臃肿的 CLAUDE.md，以及一堆每次请求都要加载却用不上的 skill 和 MCP。最实用的一条建议是先看 /usage 的分解，确认自己这套配置里到底哪一项占大头，再动手削减。值得关注：token 成本主要由上下文管理习惯决定，而不是模型单价。

**高赞评论：**

- u/locbuilds（赞数 30·归档快照）："screenshots are a big one, every simulator image stays in context and gets resent each turn" 立场说明：纠正了“图片只看一次”的直觉，多模态输入会按轮重复计费，所以做完 UI 校验应当 /clear 而不是继续同一个会话。
- u/norviking（赞数 9·归档快照）："Tokens = context size x turns" 立场说明：给出可用的成本模型，主张在三十万 token 带交接笔记重开，并把主会话降级成编排器，让子 agent 各自压缩上下文、各自设上限。
- u/Poquito-Cabeza（赞数 7·归档快照）："Letting your prompt cache go cold." 立场说明：指出超过一小时不回复，就会因为缓存重建产生额外成本，正确做法是让 Claude 生成 handoff 或先压缩，再去开新会话续接。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xzsy2b/

---

## 3. medium / high / max 推理档位到底差多少

**摘要：**

Opus 5.5 刚发布时，很多人直接把推理档位调到 medium，觉得和 high 没区别，但最近感觉变差了，于是发帖征集各档位的长期使用体感。回帖没有统一答案，却有清晰共识：多数任务 medium 足够，max 的单位收益最低，耗时与 token 却最高；max 的价值集中在特定场景，比如长脚本里跨几十行的返回值漂移、竞态条件和边界用例排查，以及开工前写规格与收尾时做复审。有人给出按阶段分配的流程：用高档次做调研和设计，medium 负责实际实现，max 做代码审查；也有人建议不要只听取别人的说法，拿自己的日常任务搭建一个小 eval，逐档对比后再判断。值得关注：把推理档位当成成本架构来分配，而不是“越高越聪明”的直觉。

**高赞评论：**

- u/Prior_Opportunity935（赞数 76·归档快照）："I use basically only use extra, Max will drone on for something that doesnt matter." 立场说明：最高赞走实用路线：max 容易在无关细节上长篇输出，extra 才是日常的最佳选择，high 反而会漏掉 extra 能看到的东西。
- u/hulkklogan（赞数 34·归档快照）："max is extremely expensive and nets basically no new ability to finish tasks" 立场说明：按公开指标算账，max 主要买到的是时间和花费而不是完成率，因此默认 medium、需要多想一步时上 high。
- u/Even_Meet8223（赞数 20·归档快照）："max reasoning catches subtle logic drift in long scripts" 立场说明：提供反例：函数返回值在三十行之后发生偏移这种漂移，medium 抓不到、high 多数能抓、max 才能覆盖边界，所以调试期值得开满。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xyxtjh/

---

## 4. 还有人在用 plan mode 吗

**摘要：**

有人观察到 plan mode 的使用频率明显下降，发帖问：还在用的人是真觉得更高效，还是新模型自己就会规划了。回帖分成三派。实用派只对涉及两个以上文件的改动启用，理由是读一份二十行的计划是最便宜的纠错方式，等到方向错了再去看 diff 就太贵了；流程派已经不切换模式，而是直接在 prompt 里要求先出计划，并把计划写进项目里的 plan 目录长期保存，这样即使会话被压缩或遇到额度上限，新会话也能从文件续接，不必依赖记忆；反对派认为 Anthropic 从 Opus 4.8 到 5 之后就建议用 skill 编排规划，自己全程 auto。折中共识是：一句话能说清的改动就跳过，要写一段话才能说清的就必须先看计划，并列出会改到的文件。值得关注：plan mode 的核心价值是编辑前的停止点，让在动手前说不成为可操作的环节。

**高赞评论：**

- u/dakuzen（赞数 28·归档快照）："I typically instruct the prompt to plan rather than switching to plan mode explicitly" 立场说明：把计划当成一份产出物而非一种模式，所有计划保存到项目里的 plan 文件夹，和进度文档一起做版本管理，跨会话都能追溯。
- u/tariqosmani（赞数 7·归档快照）："What plan mode gives you is a stop point where you can say no before anything is edited." 立场说明：指出 plan mode 的作用本质是人可以否决，并给出判定规则：一句话能描述的改动就跳过，需要一段话的先看计划并要它列出所有会改的文件。
- u/pceimpulsive（赞数 5·归档快照）："even anthropic advises against it since like opus 4.8-5 area. In favour of skills that orchestrate planning more." 立场说明：反方观点，认为规划该交给 skill 编排，自己全程 auto，代表一部分老用户已经完成的迁移方向。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y089ng/

---

## 5. 怎么让 Claude 别再长篇大论

**摘要：**

一个用了五个月 Claude Code 的用户抱怨：工作质量满意，唯一的问题是过度解释，试过各种提示、规则、插件，模型要么直接无视，要么遵守几条之后又漂回长篇大论。回帖给出的方案分三层。最省事的是改配置：output style 直接设成 concise，多数人反而绕过了这个自带开关。最稳的是在系统提示层加约束，例如用 append-system-prompt 限定“除非我要细节，否则回复不超过四句”，再 alias 成默认启动参数，因为系统提示不像 CLAUDE.md 那样会在长会话里漂移。工程化一点的是做成 skill，或在 PreToolUse、SessionEnd 这类 hook 上于关键节点重申约束。还有人用 ASD-STE100 简化技术英语标准来约束句式。值得关注：反复在对话里喊“简洁点”是最不可靠的一层，能改配置就不要靠提醒。

**高赞评论：**

- u/daltorak（赞数 17·归档快照）："everybody is giving answers except for the one thing that's the obviously correct one: change the settings. It's configurable." 立场说明：最高赞提醒大家先看产品自带开关，输出长度是配置项，不是只能靠 prompt 技巧解决的玄学。
- u/locbuilds（赞数 8·归档快照）："claude --append-system-prompt "keep replies under 4 sentences unless i ask for detail"" 立场说明：这招比写进 CLAUDE.md 更稳，因为它位于系统提示里，长会话中不会漂移，alias 之后等于永久生效。
- u/hihcadore（赞数 6·归档快照）："I tell it to apply ASD-STE100 Simplified Technical English standards to all replies." 立场说明：用受限语言标准约束句式和用词，比笼统要求“简洁”更可执行，也更适合技术文档场景。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xzsfuu/

---

## 6. 同时跑多个 agent，怎么不被报告淹没

**摘要：**

发帖人用 tmux 同时跑多个 agent，一晚派了九个任务，早上收获一堆自己都不想读的报告；他甚至试过让 agent 生成可批注的 HTML，仍然太长，最后意识到真正的瓶颈是自己的注意力。回帖的共识是把过滤前移，而不是加强阅读。输入侧把工作拆成小票据，只让 agent 执行明确编号的需求，最终回复只写“已完成 + 改了什么”。输出侧让每个 agent 把完整报告写进文件、只返回一行摘要，再派一个负责筛选（triage）的子 agent 去读文件，挑出需要人看的，并把汇报格式固定进 CLAUDE.md 保证每次一致。调度侧用汇总 agent 定时轮询，只在失败或需要人工决策时告警。也有人提醒信任是逐步建立出来的，需要持续把标准写进工作流。值得关注：报告洪水是规格与汇报协议的问题，不是 agent 开得太多。

**高赞评论：**

- u/cleverhoods（赞数 1·归档快照）："you actually manage this on the input side, at the spec." 立场说明：问题要在规格侧解决：任务拆成可引用的编号需求之后，agent 的最终回复自然只剩“评审完成、改了什么”，不需要再靠人去读长文。
- u/se7en1011x（赞数 1·归档快照）："Have each agent write its report to a file and only return a short summary line, then point a subagent at the files to triage what needs your eyes." 立场说明：把筛选工作也交给子 agent，并把汇报格式写进 CLAUDE.md，让每次运行的输出结构一致，人只看被挑出来的部分。
- u/Whole-Loss5173（赞数 1·归档快照）："i use a summary agent that batches reports every 2 hours and only sends alerts if there's a failure or a manual review needed." 立场说明：用时间窗口聚合把通知改成异常驱动，从“人盯九份报告”变成“只在真的需要决策时被打断”。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y0fuig/

---

## 7. 在 Claude、Codex、Gemini 之间换手，交接该放什么

**摘要：**

有人转述一条开源 Agent Skills 帖子（Repo Memory 存放项目的决策与进度，Repo Relay 在 Claude、Codex、Gemini、Grok、Cursor 之间传递任务与交接），顺势问大家在换助手时究竟怎么带上上下文。回帖的经验高度一致：上下文要放进仓库，不能住在聊天记录里；用一页纸的文件记录决策、原因和未完成事项，聊天历史不要搬。更细的观察是“进度笔记”一两天就过期，真正有价值的是决策记录：试过什么、为什么放弃、下一步是什么。因为单个 markdown 会被不断重写，被否决的方案那段内容会悄悄消失，新的 agent 于是又把旧方案提一遍。有团队改成每条未决事项一个 tracker 条目，关闭时把理由写在条目上，维护成本几乎为零。值得关注：跨 agent 记忆的难点是保留“为什么”，而不是复制“是什么”。

**高赞评论：**

- u/icaruza（赞数 3·归档快照）："My entire project repo on GitHub is sufficient context." 立场说明：只要愿景、设计系统、每个功能的规格、构建计划、UAT 指南和代码都在仓库里，换工具就是无痛的，上下文不该被锁在某个助手的会话中。
- u/torvalds75（赞数 1·归档快照）："is what a fresh assistant actually needs, and it's exactly the part a single running markdown file loses." 立场说明：把交接拆成进度与决策两类：进度一两天就过期，决策记录才是新助手需要的，仓库放代码与规格、tracker 放决策与未决项，关闭时写理由是任务的一部分。
- u/ChrisShips（赞数 1·归档快照）："every fancy memory setup I've tried dies by day 4" 立场说明：反工具化立场：复杂记忆系统的维护成本会被低估，最后活下来的往往只是一份 AGENTS.md 加 git log。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y07e70/

---

## 8. Claude 自己的截图脚本把 Mac 磁盘塞满了

**摘要：**

发帖人发现 Mac 只剩 25GB，让 Claude 排查，结果发现一部分主要原因就是 Claude 自己：每次做 UI 校验，脚本都会启动一个使用全新临时 profile 的 Chrome，而且从不清理，攒下 157 个 profile、约 8.7GB，还有一个无界面（headless）Chrome 孤儿进程跑了 27 小时；一周后磁盘又满，这次是 439 份 Chrome 应用副本（共享块，实际约 2GB）。他定的规则是：截图脚本把 profile 固定在一个目录并在 finally 里删除，agent 结束必须杀掉自己启动的 Chrome，不要硬删。回帖补充了更工程化的做法：把清理写成脚本而不是写成文字规则，因为长规则会在每个会话反复占用 token，只留一行 CLAUDE.md 指向脚本；用 SessionEnd hook 在会话结束时执行清理，不依赖模型记得。值得关注：agent 产生的临时文件必须有生命周期归属。

**高赞评论：**

- u/anotheruserguy（赞数 4·归档快照）："Having a rule like this will eat up a lot of tokens since each one will be loaded into every single session, vs only the one line in the Claude.md." 立场说明：把规范写成可执行脚本、只在 CLAUDE.md 留一行指针，既控制每轮 token 成本，也让清理逻辑可以被 Claude 自己读懂和维护。
- u/RealFullMetal（赞数 1·归档快照）："hook runs a command when the claude code session ends, so the cleanup" 立场说明：用 SessionEnd hook 把清理从“写进指令然后指望它生效”变成确定性执行，还能按会话结束原因区分 /clear 和退出。
- u/Dorbank_Justt（赞数 1·归档快照）："SessionEnd hooks share a 1.5 second budget by default." 立场说明：补上关键坑：默认预算只有 1.5 秒，清理几 GB 会超时，需要显式调大超时，并且只删已知的那个目录而不是按通配匹配。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xufdct/
