
今天 r/ClaudeCode 的主线仍然是「额度到底怎么烧掉的」，但难得出现了几个带测量方法论的帖子：有人把 Ultra 周额度按 token 类型拟合成换算表，有人对 /compact 与开新会话做了对照实验，也有人把 skills 和 memory 在每次启动时吃掉的 token 拆开算。另有三条偏工作流：50+ 并行 agent 的注意力成本、两万篇笔记的知识库为什么检索不起来、以及 Superpowers 这类框架是否已经过时。赞数为归档快照（多数帖子与评论分数仍停在入库默认值 1，少数已有真实梯度），可能滞后于线上。

---

## 1. 把 Ultra 周额度按 token 类型拆开算：冷缓存才是真正的漏斗

**摘要：** 有人用 Ultra（原 Max 20x）账号逐条记录 Claude Code 自己显示的额度百分比，拟合出一张换算表：1% 周额度大约等于 Opus 输出 66 万 token、输入 300 万、缓存读 1.7 亿、缓存写 460 万，按 API 价折算一整周约 1200 到 3700 美元。结论里最有用的两条是：输出 token 最贵，一个输出 token 抵得上 160 到 263 次缓存读；真正把额度烧掉的是冷缓存——主对话缓存保留一小时，子代理和后台任务默认只有五分钟，超时、压缩上下文或换模型都会让整段前缀按缓存写重新计费。作者给出 200k 与 800k 上下文的冷热对照：800k 冷缓存一轮就吃掉约 0.176% 周额度，是热缓存的 23 倍。对排期、子代理 TTL 和 fork 复用的决策有直接参考价值。

**高赞评论：**
- u/TotalOk8186（赞数 4·归档快照）：「how important it is to be running your subagents on 60m ttl rather than 5 when they're running scripts and tests that run over 5 mins」立场说明：直接把表格翻译成配置动作——跑脚本和测试的子代理应该挂一小时 TTL，因为父会话在等待期间最容易冷掉，重新写缓存的代价远大于多付的那点缓存写单价。
- u/Ok_Gur_9033（赞数 1·归档快照）：「Landing within 2 points of the thing you fitted to is a consistency check, not an accuracy one」立场说明：指出方法论软肋：模型是拟合到额度表、再拿额度表对账，只能证明自洽，不能证明额度表本身准确；作者也承认在订阅制下额度表就是唯一真值，只能接受这个前提。
- u/AncileBanish（赞数 2·归档快照）：「Compacting sends the whole conversation to the model to write the summary for the conversation moving forward」立场说明：解释压缩为什么会触发一次全量缓存写：写摘要要重读整段对话，随后新上下文的前缀是全新的，所以压缩本身也要付费，不是免费的瘦身。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xmwjcx/

---

## 2. 实测 /compact 与开新会话：同一条会话续跑反而便宜约 25%

**摘要：** 作者拿一个真实多步任务做对照：给 WeasyPrint 加 CSS box-shadow 支持，拆成解析、外阴影、扩散与多重阴影、内阴影四步，每步跑完都跑一遍上游测试，再用 Sonnet 5.5、effort high 各跑三次，比较单会话续跑、每次 /compact、每步开新会话三种做法。结果是保持一条会话总成本低约 25%，测试通过情况一致。评论区把这个结论的适用边界补了出来：上下文没长到 300k 以上时压缩本来就没有收益，而压缩动作本身要把整段对话重读一遍并产出摘要，之后新一轮前缀是全新的、必须全量写缓存，所以只有压缩后还要跑很多轮才划算。对想靠清上下文省额度的人，这是一份可复现的反例。

**高赞评论：**
- u/ReemX44（赞数 10·归档快照）：「You didn't let context grow big enough before each compact those are rookie numbers」立场说明：认为实验条件太温和，只有上下文堆到 300k-400k 再压缩才看得出差距；这质疑的是外部有效性，而不是否定结论本身。
- u/SirRobinBlibs（赞数 1·归档快照）：「compacting only pays off if enough turns follow on the smaller context to earn that back」立场说明：把压缩成本拆成两段——压缩那一次的全量重读，以及之后每轮省下的部分，给出「压缩后要跑够多轮才回本」的可操作判据。
- u/Additional_Video2992（赞数 1·归档快照）：「On a Claude subscription, within your plan's usage, the main conversation gets a one-hour cache」立场说明：补上缓存寿命差异：订阅用户主会话缓存一小时，API key 或额度计费只有五分钟，所以「挂着会话去吃午饭」对两类用户结论完全相反，/usage 里能直接看缓存还热不热。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xmy2j7/

---

## 3. 每次启动被 skills 和 memory 吃掉多少 token：15k 的构成与削法

**摘要：** 提问者在 Pro 套餐上发现每个新会话固定花掉约 8k memory 加 7k skills，想压缩，但让 Claude 自己「精简记忆」并没有效果。回复把这两笔账拆开了：会话启动时只有 skill 的名字和描述进上下文，完整正文要等 skill 真正被调用才加载，所以那 7k 基本是描述文本堆出来的，正确削法是删掉不用的 skill、把描述压到一两句，而不是去改正文；memory 的 8k 则是每次会话全额付费，把只在特定任务用到的细节挪到按需读取的文件里收益更大。还给出两个可操作检查点：新会话先跑 /context 看分项，以及用子目录 CLAUDE.md 与 .claude/rules 做路径级按需加载。对 Pro 用户判断该删 skill 还是该删记忆很有用。

**高赞评论：**
- u/AdEvening3382（赞数 1·归档快照）：「the way to shrink it is removing skills you never use or tightening their descriptions, not editing the bodies」立场说明：纠正最常见的优化方向错误——改 skill 正文对启动开销无效，因为启动时只加载名字和描述，真正该动的是清单和描述长度。
- u/Yedapo（赞数 1·归档快照）：「Asking Claude to trim it often just rewrites it shorter without actually deleting stuff」立场说明：解释「让 Claude 精简记忆」为什么常常白费：它倾向于改写措辞而不删条目，得人工过一遍、真正砍掉内容才有效。
- u/awesomebirder（赞数 1·归档快照）：「clearing around 80-100k with a short handoff note will stretch pro way more than trimming memory」立场说明：认为优化重点排错了：启动那 15k 首轮就进缓存、之后重读很便宜，真正贵的是每轮重读整段上下文，所以清空时机比省 memory 更值钱。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xke5ja/

---

## 4. 每天 50+ 并行 agent 线程四个月：瓶颈从 token 变成注意力

**摘要：** 作者四个月里几乎把所有工作都丢给 agent，某些天同时跑 50 多个线程，产出确实比以往多，但每周结束时像「开了一整周会」——每个线程迟早回来找人：测这个、批那个、纠正这个、把那个转走，每一次都是一次上下文切换。他引用 BCG 三月对 1488 名美国员工的调查，称 14% 的 AI 使用者经历过所谓「AI brain fry」，重度监督 AI 的人报告精神疲劳高 12%、信息过载高 19%，并声明这是自陈数据、只有一轮，仅供参考。他正在做的改动是停止把线程数当目标，改做一个只显示「有多少决策在等我、每个项目朝哪走」的小面板。对正在扩并行度的团队，这是一份关于评审端成本的现场记录。

**高赞评论：**
- u/CriM_91（赞数 16·归档快照）：「stop building! Stop building 10 projects at once. Aim for 2 at maximum」立场说明：来自 LLM 研发团队工程师的反向建议：同时推进超过两个项目、或在同一项目上开 20 个会话，一个月内必然脑力透支，他认为任何 dashboard 都救不了这个结构问题。
- u/BoltSLAMMER（赞数 7·归档快照）：「My question is four months of nonstop work, have you shipped anything ?」立场说明：最尖锐的质疑：持续加功能可能是多巴胺循环，用「一直在推进」替代「做完并交付」这件更难的事，四个月后要看的是交付物而不是线程数。
- u/Dorbank_Justt（赞数 3·归档快照）：「it writes one line on what it wants to do, one on why, the exact text or change, and what happens if I say no」立场说明：给出可落地的降本手法：把所有请求压成同一形状（做什么、为什么、具体改动、拒绝的后果），批量审批才能读得快；「拒绝会怎样」还能筛掉根本不需要人介入的请求。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xh5cum/

---

## 5. 两万篇笔记的第二大脑，Claude 就是不去查：问题不在模型

**摘要：** 作者在 Obsidian 里按 PARA 结构堆了约两万篇 markdown，嵌了多层 CLAUDE.md 和 agent.md，但 Claude 极少主动去查，答问题时宁可凭上下文猜。他要的不是无限上下文，而是「意识到缺某条信息时先去取」。高赞回复几乎一致地把矛头指向结构而不是模型：给内容建搜索索引、把「先查索引」做成硬约束，而不是在记忆文件里写一句祈使句；多层嵌套的 agent 文件不但没帮忙，还在每次会话里占掉预算。也有人给出现成组合：索引或 BM25 检索加一个 user prompt hook，让排序后的候选笔记在每轮开头被推进上下文，检索就不再由模型自由裁量。适合正在自建知识库或「公司大脑」的人对照排查。

**高赞评论：**
- u/hbthegreat（赞数 30·归档快照）：「nearly all of them are larping and just slopping shit into documents that are linked together」立场说明：泼冷水但有用：多数「第二大脑」只是把文档互链就宣称建成，真正能用的是贴合自己思考方式的结构，照搬别人的模板只会得到一堆漂移的笔记。
- u/DaRKoN_（赞数 21·归档快照）：「get a search index over your content, give it a way to search the index, be explicit to search it first」立场说明：给出最小可行方案：检索能力加明确的前置指令，同时劝他砍掉层层嵌套的 agent 文件——让 AI 爬两万篇文档本身就是在烧 token。
- u/Downtown-Pear-6509（赞数 12·归档快照）：「ranking existing knowledge base articles and suggesting them as part of the user prompt hook」立场说明：把「模型自己想起来去查」换成确定性注入：在 user prompt hook 里先做相关性排序并附上候选，检索就从模型的自由裁量变成流程的一部分。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xixsh5/

---

## 6. Pro 用户怎么配模型和 effort 才不烧额度

**摘要：** 一个刚上 Pro 的用户问：日常该用哪个模型、哪个 effort 档才撑得住。回复基本收敛到「别默认用最高档」：日常编码用 Sonnet 5.5 medium，复杂推理或卡住时才升 Opus；有人长期用 Opus 5.5 low 思考，理由是这一档直接给方案而不是先反复自我打磨，能更快判断值不值得继续。另一条被反复强调的是会话长度比模型选择更影响消耗——每条消息都会重读整段对话，一条会话连做五个任务的成本远高于五条短会话，任务之间 /clear、别让测试输出整段回灌，省下来的比换模型更多。也有人给出编排式方案：Opus 只做规划和评审，Haiku 执行，贵模型不写代码。对刚订阅、还在摸额度边界的人是一份实用配置清单。

**高赞评论：**
- u/Dense-Ad6315（赞数 2·归档快照）：「sonnet 5.5 basically all the time at med thinking. any higher absolutely kills limits」立场说明：从 Max 降回 Pro 的用户给出最保守配置：全程 Sonnet medium，再往上调档额度立刻见底，对 Pro 档来说 effort 档位比模型代际更敏感。
- u/awesomebirder（赞数 1·归档快照）：「session length matters more than the model on pro」立场说明：把优化优先级摆正：Pro 上会话长度的影响大于模型档位，任务之间清空、避免大段测试输出回灌，比换便宜模型更有效。
- u/TheDragonBallGuy75（赞数 1·归档快照）：「Opus never writes any code itself, it just acts as the reviewer」立场说明：给出编排思路：Opus high 只做拆解与评审，具体实现交给 Haiku 高 effort 的小代理，让贵模型不写代码是省额度的关键。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xkbp7a/

---

## 7. Superpowers 让 Claude Code 变慢：这些框架是不是已经过时了

**摘要：** 作者抱怨最近用 Superpowers 时 Claude Code 明显变慢，本该简单的项目拖到八天，Fast Mode 取消后更糟，怀疑框架里规划、测试、验证这些环节的开销已经超过实际编码，开始考虑改用多 agent 和 git worktree 并行。评论区主流判断是「框架过时」：这类 skill 诞生于模型还需要大量引导的时期，而 Opus 5.5 默认就会自己定成功标准、跑验证门禁，再叠一层强制流程等于把同样的检查做两遍，多出来的轮次既慢又烧 token。也有人指出真正的分界不是用不用框架，而是有没有在动手前写清「做完是什么样」；另有几位提醒并行只在任务真正独立时有用，worktree 隔离了代码却不会帮你审查。

**高赞评论：**
- u/bilbo_was_right（赞数 6·归档快照）：「Boris said plan mode is generally no longer necessary, but I also feel like I get much better results pretty consistently when I use plan first」立场说明：点出官方说法与体感的矛盾：规划阶段的价值不在功能，而在给模型划一条清晰的「规划/实现」界线，这也是他坚持先写计划的原因。
- u/scott2449（赞数 4·归档快照）：「I use like 1/10th the tokens」立场说明：给出对照样本：不用任何框架、plain Opus 5.5 medium 配 400-600k 窗口，结果比同事更快而且 token 只有十分之一，说明流程层的收益已经为负。
- u/Diouze12（赞数 2·归档快照）：「There is no need for any framework since opus 5.5 and even more it's counter productive」立场说明：从模型行为解释变慢的成因：Opus 会重复确认每一步，再叠框架就是双重验证；他自己反而要在 CLAUDE.md 里限制 checkpoint 频率，避免每次改动都跑一遍构建和测试。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xl8klo/
