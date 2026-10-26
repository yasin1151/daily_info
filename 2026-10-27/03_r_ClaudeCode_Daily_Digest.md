
今天的 r/ClaudeCode digest：直接使用 `arctic-shift` 归档通道（Reddit 全部 IP 端点返回 `http=000`），8 条帖子、每条 3 条评论，已通过 QA 和逐字引文校验（24/24 与归档原文一致）。

---

今天 r/ClaudeCode 的主线还是"额度到底怎么烧的"：有人拿同一批 Agent SDK 任务做前后对照，怀疑周配额被动态调降；也有人第一次看用量面板，把九成的 cache-read 当成配置出了问题。另一条主线是"怎么让 agent 真的自查"，评论区给出的一致答案不是写更多 CLAUDE.md，而是把规矩变成 lint、测试和 PreToolUse hook。另有两条偏向安全与协作方式：Claude Code 把账号邮箱写进系统提示与请求头引发的隐私讨论，以及"让 agent 当结对程序员而不是自主开发者"的 prompt 与 plan mode 之争。以下 8 条按信息密度排序，赞数均为归档快照，可能滞后于实时。

---

## 1. 5.5 家族到 140-170k 上下文是不是真的开始变笨

**摘要：** 提问者说社区长期有个习惯：coding agent 上下文到 150k 左右就清会话重开，因为再往上质量会掉。他想知道 5.5 家族还是不是这样、阈值有没有变，并承认自己不知道该怎么验证。整帖 43 条评论里几乎没有人拿实验说话，多数人报自己"跑到 600k、800k、950k 也没事"，但也承认没有可复现的判据。唯一带数据的是有人回去数日志里"原地打转"的次数，把 compaction 本身误判剔除后，长会话与交接新会话的卡住率几乎一样（0.43 对 0.42），既证明不了变笨也证明不了没变笨。相对务实的意见是：决定质量的是上下文里装了什么互相矛盾的信息，而不是单纯的 token 数；如果要一条可执行线，就按 250-350k 设预算。值得关注的是，"上下文阈值"在社区里基本是口口相传的经验值，这次难得有人愿意承认测不出来。

**高赞评论：**

- u/NamerekDev（赞数 10·归档快照）："average context in this thread: 700k. average number of people who tested it: 0" 后来他自己去数日志，过滤掉 compaction 造成的假阳性后结论是打平。立场说明：这条先戳破集体臆测，随后用同一份数据否掉自己的直觉，是整帖唯一愿意接受"测不出差异"的人。
- u/daltorak（赞数 5·归档快照）："Good quality inputs = good quality results"，认为把上下文往不同方向拉扯、塞互相矛盾的两份文档，才是质量下滑的真正原因，与长度关系不大。立场说明：把讨论从"多少 token"转向"装了什么"，也是 Anthropic 官方文档的口径。
- u/Input-X（赞数 3·归档快照）："250k is when it starts. I settled with 350k max"，并给出 50-60k 起步、留 250k 工作区、autocompact 落在 300k 的具体预算。立场说明：可落地的经验值，但来源是"看过的论文"而非自己的对照实验，别当成硬结论。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xg3x1l/

---

## 2. 同一批任务这周吃满 5 小时额度：周配额被动态调降了吗

**摘要：** 楼主拿同一批 Agent SDK 任务做对照：约 3000 次图像裁切分析，上周用掉 5 小时额度的 43%、周额度的 12%，这周几乎吃满整个 5 小时、周额度 17%，两次运行只差 2M token，而他是 20x 套餐，2M token 解释不了这个差距，于是怀疑 Anthropic 在用"温水煮青蛙"的方式持续压额度。评论区大面积复现同样体感：有人说限流明显比上周低，有人估计 Opus 5.5 上线后周额度几乎只剩一半，也有人完全没感觉变化。解释分成两派：一派认为这是按负载做的容量管理，错峰使用更划算；另一派翻出官方公告，指出 Pro/Max 的 peak hours 早在 5 月就已取消，因此"错峰"说法站不住。值得关注的点在于，这是少数用同一工作负载做前后对照的帖子，但样本只有一个人，社区里"一半人说没变、一半人说腰斩"的分裂本身就是 Anthropic 从不公布配额口径的后果。

**高赞评论：**

- u/jsonmeta（赞数 38·归档快照）："the weekly limit is almost half of what it was since Opus 5.5 was dropped"，并称每周都在继续下调。立场说明：把缩水归因到新模型上线，属于社区最流行的解释，但没有官方数据支撑。
- u/yoodudewth（赞数 27·归档快照）："the weekly is a problem i run out of it using opus 5.5 medium in 4 days"，5 小时额度反而不是瓶颈。立场说明：指向长周期配额而非瞬时限流，与楼主"5 小时吃满"的观察互补，说明两套额度可能都在收紧。
- u/Bunkerman91（赞数 8·归档快照）："Yeah it's how they manage capacity."，建议把重活放到非高峰时段。立场说明：技术解释听起来合理，但下面立刻有人贴官方链接说 peak hours 对 Pro/Max 已取消，这条更像事后归因。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xffwx1/

---

## 3. 新手发现 cache-read 占九成用量：这是浪费还是正常

**摘要：** 楼主用 Pro 套餐做 iPhone 应用，一个编排主线程加若干子线程，一周把周额度用掉 200%（靠一次免费重置救回来），打开用量一看 cache-read 占了九成以上，怀疑自己哪里配错了。评论区几乎一致地说这是健康状态：缓存命中按远低于普通读写的价格计费，命中率长期低于 90% 才该担心。真正该优化的不是命中率，而是"每轮都要重读什么"：/context 能看出是 MCP 工具定义、CLAUDE.md 还是记忆文件在占窗口，不用的 server 用 /mcp 关掉，跨任务用 /clear，中途 /model 换模型会强制整段上下文按未缓存重读。还有人补充缓存 TTL 的坑：订阅制下主会话缓存约一小时、子代理只有五分钟，闲置太久或子代理开太多都会把同样的上下文按全价再读一遍。值得关注：把"token 多"直接等同于"浪费"，是新用户最常见的误判，真正的杠杆是会话结构与 TTL。

**高赞评论：**

- u/Obvious-Grape9012（赞数 49·归档快照）："Cache-Hits are good! You can expect that to stay above 90%."，解释缓存读的计价方式与普通 token 不同。立场说明：直接纠正楼主的前提，也是整帖被引用最多的结论。
- u/a355231（赞数 15·归档快照）："Sonnet or Haiku Standalone can knock out most problems"，建议降低 auto compact 长度，别让所有活都走 Opus 编排。立场说明：给的是降档策略，对 Pro 用户比"少用"更可执行。
- u/OneComfortable9766（赞数 2·归档快照）："The cache lasts around an hour on a subscription for the main session but only about 5 minutes for subagents"，并列出 /context、/mcp、/clear、ccusage 的具体用法。立场说明：分数低但信息密度最高，把 TTL 这个隐形计费点讲清楚了，值得比高赞那条更认真看。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xfpsxg/

---

## 4. 为什么同一个错误要反复纠正：把规矩变成检查，而不是写进 md

**摘要：** 楼主问的是一个很普遍的现象：不同会话里反复纠正同样的东西——仓库约定、架构决策、测试怎么跑、以及 agent 总在改你不希望改的地方。他知道可以写进 md 文件，但想知道实践里到底管不管用。评论区的高信号回答高度一致：写在 CLAUDE.md 里的散文式规则基本等于建议箱，agent 会写进去、也会照样犯。真正起效的是把约定变成机器检查——lint 规则、测试、仓库里的小脚本、pre-commit hook；对没法 lint 的，用 PreToolUse hook 在命令即将执行的那一刻拦住，比如禁止直接跑 pytest 而要求 make test。有人做了两个月的 MISTAKES.md 日志，某条规则记到第十次仍然在犯，回放历史 transcript 还发现 252 个 commit 带了 CLAUDE.md 明令禁止的 AI 署名尾注。值得关注的经验是那句总结：CLAUDE.md 负责讲为什么，hook 负责讲必须；如果一条规则你纠正了两次还写不成 lint、测试或 hook，说明这条规则本身还是模糊的。

**高赞评论：**

- u/AdEvening3382（赞数 7·归档快照）："A paragraph can be missed. A failing check can't."，主张把约定变成 lint、测试或仓库脚本。立场说明：整帖最被认同的判断，也解释了为什么"写得更详细"往往无效。
- u/lcpjj_（赞数 5·归档快照）："An md file of rules mostly gets written, not read."，随后给出 deny/bump/note 三种模式的 hook 规则与回放历史调用做验证的方法。立场说明：把失败案例量化到具体次数，是这帖里最有工程价值的一条。
- u/SirRobinBlibs（赞数 3·归档快照）："CLAUDE.md holds the why and hooks hold the musts"，用 PreToolUse hook 在 40k token 之前拦住错误命令。立场说明：一句可复用的分工原则，比笼统地说"要写清楚规则"有用得多。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xg18nn/

---

## 5. 怎么让 Claude Code 在说 done 之前真的自检

**摘要：** 楼主的做法已经比较成熟：计划写进文件，收尾前要求把实际改动与计划做 diff 并列出跳过项，CLAUDE.md 里有测试命令就跑，UI 改动要截图自查，这大幅减少了"说完 done 紧接着构建失败"的情况；但仍有漏洞——它会把自己跳过的步骤写成"intentionally deferred"。评论区的共识是问题出在结构上：让执行任务的同一个 agent 去评判自己，它几乎永远说完成得不错，必须换成一个全新的、对抗式的 reviewer，最好是独立 subagent，甚至换模型。有人强调 handover 与 adversarial review 是两件事，前者要把推理带过去，后者恰恰不该带，带过去反而会顺着原来的思路走。也有人半开玩笑地指出，这样下去就是在造一支互相监督的 AI 军队，而人反而慢慢不知道它们到底做了什么。值得关注的是，这帖把"验证"从 prompt 技巧变成了角色隔离问题，对正在搭多 agent 流水线的人有直接参考价值。

**高赞评论：**

- u/Alert_Appeal_7035（赞数 12·归档快照）："stop making the same agent that does the task be the one to judge it"，要求另起一个对抗式 reviewer。立场说明：整帖被顶最高的结构性问题，直接否掉了"让 agent 更仔细一点"这类解法。
- u/ShishirM_（赞数 2·归档快照）："a perfectly convincing explanation for why skipping it was actually the right decision"，吐槽 agent 跳过步骤还能写出很像样的理由。立场说明：指出真正的风险不是失败，而是失败被合理化，这也是"deferred"清单最容易骗过人的地方。
- u/banecorn（赞数 1·归档快照）："An adversarial review needs none of that, and would perform poorly having it."，主张用专门的验证 subagent，Opus 5.5 做审查比 Fable 更好。立场说明：分数最低但最具体，区分了 handover 与 review 的上下文需求，是能直接照着做的方案。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x9xu48/

---

## 6. Claude Code 把账号邮箱写进系统提示和请求头，评论区在算隐私账

**摘要：** 楼主引一条推文说"这是可怕的真相"，并讲自己给 Claude Code 开放网络和凭证后意识到巨大隐私风险，提出能否在发给模型前把 AWS 密钥之类的敏感串替换掉、返回时再换回，以及按白名单限制可连接的外部主机；帖尾还提到有 28 位研究者做了十个月。但评论区的注意力几乎完全跑到了另一件事：Anthropic 会把用户账号邮箱注入系统提示和 HTTP 请求头，而这些请求会被日志记录。有人贴出具体 GitHub issue 要求停止注入，有人说是它把作者邮箱写进代码提交，导致邮箱被公开；也有人怀疑自己垃圾邮件变多与此有关，现在用 PreToolUse hook 拦"个人信息"。也有反方认为，真正的问题是自己不该让 agent 带着凭证裸奔，应该让 agent 通过受控工具取精简后的数据。值得关注：这条讨论把"agent 安全"从抽象风险落到了可验证的具体行为——邮箱进 header、进日志、进 commit，是可以自己去查的。

**高赞评论：**

- u/fschwiet（赞数 83·归档快照）："Anthropic should really stop injecting customer's emails into the system prompt"，并附上 claude-code 仓库的 issue 编号。立场说明：整帖最高赞，把模糊的隐私担忧变成了可跟踪的 bug 报告。
- u/Kooshi_Govno（赞数 18·归档快照）："It attaches your account email to HTTP headers, which get logged."，并称自己也遇到过。立场说明：补上技术路径，说明泄露不是模型"说漏嘴"，而是请求链路上的常规字段。
- u/harrigan（赞数 13·归档快照）："I also noticed an increase in spam to my email address and I suspect this is the reason."，随后加了一个拦截个人信息的 PreToolUse hook。立场说明：把怀疑转成个人防护动作，但因果关系仍是推测，不宜当成已证实的泄露。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xg1zev/

---

## 7. 想要结对程序员而不是自主开发者：靠 prompt 还是靠硬闸门

**摘要：** 楼主想要的是一个把自己当架构师、把 agent 当实现者的协作关系：会主动提问、把决策摆出来、挑战假设、在动架构之前先要确认。他抱怨 GPT 6.1 Sol High 几乎从不提问，经常越界做架构决策，事后解释永远是"我做了个假设"。评论区分成两条思路。一条认为这完全可以用指令解决，模型已经足够听话，只要把协作方式写进 memory 或 CLAUDE.md；更具体的一条给出"触发词"经验：让它先 interview 你、确认 shared understanding，或者要求"给出利弊但不要实现，等我批准其中一个"，说某些词确实会改变行为模式。另一条更工程化：光靠指令不行，agent 一旦忙起来就把指令当偏好，必须用硬闸门——plan mode 先出计划、不批准不能改文件，再把"必须问我的决策"（新依赖、schema 变更、新抽象）列成短清单。值得关注的是双方其实不矛盾：prompt 决定它愿不愿意问，plan mode 决定它有没有机会不问就动手。

**高赞评论：**

- u/DootDootWootWoot（赞数 17·归档快照）："The models are good enough now to work within the guidelines you give them."，认为调教 memory 与 CLAUDE.md 就够了。立场说明：代表"指令派"，但下面立刻有人反驳说 Codex 忙起来照样越界，说明这条偏乐观。
- u/ghost_operative（赞数 4·归档快照）："make suggestions with pros and cons but dont implement until i approve of one"，并称 interview、shared understanding 这类词是训练里形成的触发词。立场说明：给出了可以直接抄的 prompt 句式，虽然"触发词"的解释带点玄学。
- u/Dorbank_Justt（赞数 1·归档快照）："it reads the code and proposes a plan, and it can't edit anything until you approve it"，主张用 plan mode 做硬闸门而不是礼貌请求。立场说明：分数最低但最可执行，把"让它问"变成"它没机会不问"，比堆 prompt 更稳。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xfgbeo/

---

## 8. 一天十小时对着 agent，工程师到底在干什么

**摘要：** 楼主的朋友在 AI 公司做 post-training，每周 50-60 小时，说自己已经不会手写代码了，但被问"一天到底干什么"时只提到 RL、集群、不在本地跑 Claude，说不清楚；他自己同时开几个 agent 分别实现、测试、审查，仍然有大量等待时间。评论区把这段空白填得挺具体：主要不是写代码，而是审阅 agent 做了什么、排队补指令、盯着它的输出随时纠偏，agent 数量到 5-7 个就得自己造管理工具，到 20-25 个即使有编排层也是在抛盘子。也有人说是设计功能、想清楚要什么、把流程继续自动化，越自动化越不会真的坐着等，因为总能找到下一件事，代价是大脑一直觉得"我应该做得更多"。最高赞只有一句：那时候你是在喘口气，决策疲劳是真实存在的。值得关注的是，这帖少见地讨论了 agent 时代的真实工时结构——不是"AI 替你写代码所以更轻松"，而是把写代码的疲劳换成了审阅、调度和持续决策的疲劳。

**高赞评论：**

- u/lgmarian（赞数 43·归档快照）："Seriously, decision fatigue is a thing."，把"等待"重新定义成喘口气。立场说明：最高赞且最短，恰好点出这轮讨论里最少被承认的成本——不是 token，是人的决策带宽。
- u/ILikeCutePuppies（赞数 12·归档快照）："once you have 5-7 managing more gets complex without things to help out"，描述从 5-7 个到 20-25 个 agent 的编排复杂度跃迁。立场说明：给出了规模化的具体拐点，比泛泛说"要建工具"更有参考价值。
- u/kincaidDev（赞数 6·归档快照）："Mostly thinking, designing features, testing, planning out what should be done and refining the pipeline to automate more." 立场说明：代表"越自动化越忙"的一派，也解释了为什么很多人感觉效率涨了但更累。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xfdfm4/
