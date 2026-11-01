
# r/ClaudeCode 每日推送 · 2026-11-02

本机 Reddit 三个端点在 IP 层被封（www / old / redlib 全部 000），正文与评论取自 arctic-shift 归档 API。赞数为归档快照，可能滞后，标 1 的多是入库默认值，本文不做"高赞排序"，只按内容信号选评论。今天 7 条，全部是硬信息：上下文卫生、双模型分工、effort 档位、skill 路由、会话续读、反 slop 检查、新游戏条款实测。

---

## 1. 每个任务都开新会话，还是养一个超长会话？

**摘要：** 楼主问了一个老问题：该为每个任务开新会话，还是保持一个长会话跑到底？社区两派说法互相矛盾，一派称长会话会变糊涂，一派从不清理。评论区的回答比楼主具体：票数最高的一条直接说，不清理就是在大量浪费 token；接着有人给出阈值，让 Claude 在上下文到 150k 时提醒收尾交接，理由是审计过自己的用量，那个点之后清理并交接更省钱，而且成本随上下文长度近似对数放大，因为每条消息都要把前面全部重读一遍。反方也不是抬杠：有人说自己仓库一开始就 100k，硬压到 150k 以下不现实，但没感觉性能变差，只是定期清理归档。真正值得抄走的是第三层信息——有人发现自己试装的各种 skill 和 MCP 全在往上下文里塞东西，一大半根本没用，光打招呼就可能占掉不少预算。也就是说，上下文卫生不是玄学，而是可以定阈值、审计、先关掉无用加载项来修的工程问题。

**高赞评论：**
- u/kimvais（赞数 34·归档快照）："You are wasting a fuckton of tokens if you never clear" —— 立场说明：措辞很冲但指向明确，把"会话该不该清"从习惯之争拉回到 token 账本上，是本节最直白的成本判断。
- u/ShockTheCasbah（赞数 6·归档快照）："I have Claude programmed to tell me to start wrapping at 150k context" —— 立场说明：给了可复制的阈值做法，还补了一句审计结论，说清空交接比继续跑更划算，且开销随上下文放大，属于有测量支撑的经验而非感觉。
- u/ilion（赞数 1·归档快照）："too much is loading into my context currently even though a bunch of it is useless" —— 立场说明：指出浪费的大头可能不是对话本身，而是装了一堆用不上的 skill 和 MCP，提示先做减法再谈清理频率；分数低但提供了别人没提的排查方向。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xkyeg4/

---

## 2. 想让便宜模型做实现、Claude 只做监督，这套分工怎么才安全？

**摘要：** 楼主算了一笔经济账：Claude Pro 升 5 倍档太贵，于是想把实现工作交给 DeepSeek 4.1 Flash 这类便宜模型，Claude 只负责定义任务、给上下文、评审结果。他卡在两处：把另一个模型带到可开工状态很费功夫，且不愿给自主 agent 开放仓库、凭证和本机文件。评论里最有价值的一条反过来泼冷水：这样并不会更省，最便宜的永远是单 agent，降成本的关键是减少往返轮次，他自己做了个能批量改文件并顺带跑检查的 MCP 工具，把轮次砍掉一半。那为什么还要拆？因为实现者自己验收自己存在利益冲突，模型会为了"完成任务"牺牲质量，拆开之后可以把成功重新定义成每一步决策正确。隔离方案也写得很实在：一次性 worktree、容器里不放真凭证、真 key 放在前置代理上只转发白名单域名、产物一律当不可信 diff、测试自己重跑再合并。也有人实测后承认，自动化委派比手动更费 token，最终还是升了套餐。

**高赞评论：**
- u/Isogash（赞数 4·归档快照）："It won't save cost, the absolute cheapest way to get something done with AI is a single agent" —— 立场说明：直接否掉楼主的成本假设，并给出真正有效的方向是压缩轮次，同时解释了多 agent 的正当理由是不让实现者自己打分，论证最完整。
- u/LynxInformal5305（赞数 2·归档快照）："The worker saying 'all tests pass' is a claim" —— 立场说明：一句话点出委派里最容易被忽略的漏洞——子 agent 的通过结论只是声明，监督方必须在干净检出上自己重跑；并给出最朴素的隔离起点：一次性 worktree、不给凭证、只交 patch。
- u/ShipSafeScan（赞数 2·归档快照）："put a proxy in front that holds the real key and only forwards to an allowlist of hosts" —— 立场说明：把"不给钥匙"落成工程做法，密钥留在容器外、出口网络也锁白名单，并提醒能读文件又能任意联网的 worker 正是数据外泄的入口。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xk8imc/

---

## 3. effort 从 xhigh 降到 high、再到 medium，实际差在哪？

**摘要：** 楼主是 2025 年中就开始用 Claude Code 的老用户，最近把实现者从 xhigh 换成 high，发现又快又好，但 Claude 自己声称 medium 在编程任务上常常优于 high，他不太信，想收集社区经验。评论区迅速分成两派。高票一派主张 medium 就够了，理由是绝大多数人的项目复杂度根本用不到高强度思考，high 和 xhigh 只在超大系统、多层调用、大量消费者那种规模上才值回票价。另一派则质疑这套结论的样本质量：先问一句"你到底有没有真的看代码"，指出这类讨论九成来自看不出好坏实现的 vibe coder，低 effort 更容易破坏架构基本功，而高强度档位反而会堆出一层层没必要的间接层。最有解释力的一条来自第三视角：effort 并不是"聪明程度旋钮"，它的作用是促使模型在动手前多翻项目文件，所以该不该开取决于任务性质和你自己把需求写清楚的程度——你越放手，才越需要高 effort 去补你留下的空白。

**高赞评论：**
- u/fredastere（赞数 20·归档快照）："I think 95% of us works on projects that medium simply is a beast at" —— 立场说明：代表"默认 medium"派最完整的表述，划出了 high/xhigh 的适用边界是真正的超大规模系统，并称自己切回 medium 后体感明显更顺。
- u/BingpotStudio（赞数 13·归档快照）："Are you actually reviewing the code though?" —— 立场说明：给整场讨论做了质量校验，指出很多'低档位也够用'的结论来自无法判断代码好坏的人，并称低 effort 更容易破坏架构基础，是反方最有分量的质疑。
- u/ghost_operative（赞数 1·归档快照）："it's used to encourage the ai to explore project files more before doing work" —— 立场说明：把 effort 重新定义成"动手前探索多少文件"的开关而非智力档位，解释了两派为何都能自证，是本节最有解释力的模型；分数低但信息密度最高。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xkdg81/

---

## 4. 辛苦建好的 skill，为什么模型说不用就不用？

**摘要：** 楼主花了一个多小时让 Claude 建 skill，下个会话让它按 skill 执行却被完全无视，即使明确点名也一样。他的疑问很朴素：如果模型可以随意忽略，创建 skill 到底有什么意义？评论给出的机制解释比抱怨有用得多：模型平时只看得到 skill 的名字和 description，也就是 frontmatter，正文要等命中才会被读进来，所以 description 写得含糊或不贴合真实使用场景，就不会被选中；而且 instructions 只能改变概率，唯一能保证触发的是 hook，比如把代码格式化交给 hook 跑，远比在 Markdown 里写一大段格式规范可靠。有人进一步建议把流程写成带 hook 的 plugin，让相关任务必然调用对应 skill，而不是指望模型记得。还有一条很实用的诊断法：先让模型在新会话里复述 skill 的步骤，如果复述不出来，说明根本没加载，是名字或路径问题，再怎么改提问方式都没用；能复述却不执行，才是路由概率问题。

**高赞评论：**
- u/lgmarian（赞数 2·归档快照）："The description is crucial, as they only read the frontmatter, until it uses the skill" —— 立场说明：一句话说清 skill 的可见性机制，并指出 hook 是唯一有保证的触发方式，把问题从"模型不听话"纠正为"检索键没写好"。
- u/___nil___（赞数 2·归档快照）："you can't rely on instructions alone" —— 立场说明：主张把"做 A 必须用 skill A"写成协议并用 plugin 加 hook 强制执行，代表了从提示工程转向机制约束的思路，可直接照做。
- u/Anreall2000（赞数 1·归档快照）："Model only see skill name and skill description, to save tokens" —— 立场说明：补充了为什么要这样设计——省 token，因此 description 质量直接决定命中率；这条解释了机制缘由，帮助用户判断该改描述还是改触发方式。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xivdvi/

---

## 5. 新会话能不能只读地参考旧会话？

**摘要：** 楼主听说可以让新会话读取旧会话，但在 CLI 和桌面 App 里都找不到明确命令，问是已有功能还是得自己造。评论区的答案分三层，而且都比官方文档具体。第一层是路径：每个会话本来就以 jsonl 存在 ~/.claude/projects 下，目录名由项目路径的斜杠换成横线得到，文件名就是 session id，把路径交给新会话、让它先 grep 关键词再读命中行附近即可，session id 可以在 /status 里看到。第二层是保留原会话：直接 resume 会继续往同一份 transcript 追加内容，想要真正的只读分支就用 resume 加 fork-session。第三层是成本提醒，也是最容易被忽略的：jsonl 里记录了每一次工具输出，所以一个长会话的文件体积远大于聊天时的体感，让新会话整份读进来可能比直接 fork 还贵，正确姿势是先定位相关片段再局部读。这套做法等于不装插件就实现了"选择性只读续读"。

**高赞评论：**
- u/RealFullMetal（赞数 2·归档快照）："every session is already saved as a jsonl" —— 立场说明：给出最完整的路径公式和 grep 找 id 的命令，等于直接回答了楼主的问题——不需要额外功能，文件一直都在，只是没人告诉你位置。
- u/zzunkie（赞数 1·归档快照）："claude --resume <session-id> --fork-session" —— 立场说明：提供了唯一真正满足"只读"语义的原生命令组合，新会话继承历史而原会话保持不变；这条是本帖最直接的解法。
- u/awesomebirder（赞数 1·归档快照）："the jsonl has every tool output in it too" —— 立场说明：提醒文件里含全部工具输出、体积被低估，整份读进来可能比 fork 更贵，主张 grep 后再局部读，是防踩坑的成本提醒。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xkficd/

---

## 6. 想靠提示词文件治住 AI slop，为什么基本没用？

**摘要：** 楼主的困境很多人熟悉：边想边做确实快，但每个需求都长出一个新文件，文件之间互相影响，耦合失控；他试过把 GRASP、GoF 这类设计原则写进 planner 和 reviewer 的提示词，结果像对空气说话。第一条高票回答直接把方向拨正：不存在能替你解决这事的提示词文件，问题在于人有没有贴着代码一起走，模型只会给出你描述范围内的平均解，没有明确愿景就没有好结构。真正可落地的答案是把设计原则变成会失败的检查：用 dependency-cruiser、import-linter、ArchUnit 声明分层规则，比如 ui 不许 import db，再加文件行数和复杂度上限，挂在 hook 或 CI 上，违反时把报错原文回喂给模型，让它自己修耦合。更狠的一招是给新建文件加成本：用 PreToolUse hook 拦 Write，文件不存在就以退出码 2 阻断，强制它先说明为什么现有模块放不下。结论很清楚——规则要活在构建里，活在被忽略的段落里等于没有。

**高赞评论：**
- u/onFilm（赞数 13·归档快照）："this is where your creativity and problem solving skills come in handy" —— 立场说明：本节最高票，直接否定楼主的解法方向，指出 slop 的根源是缺少人工贴身协作与明确愿景，而不是缺一段更强的指令，是整场讨论的定调。
- u/verstands（赞数 2·归档快照）："I'd turn the principles into checks it can fail" —— 立场说明：把抽象原则翻译成可执行门禁，列了三种语言的依赖检查工具和分层示例，并强调失败信息回喂给模型后它自己会修，是全帖最可复制的方案。
- u/Significant_Door_433（赞数 1·归档快照）："make new files cost something" —— 立场说明：针对"每个需求一个新文件"给出精确机制——PreToolUse 拦 Write，路径不存在就 exit 2 并在 stderr 要求论证，把习惯问题变成一道必须通过的关卡。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xji1dk/

---

## 7. 新版那条"别复刻现有游戏"的规则，实测到底拦什么？

**摘要：** Claude Code 2.1.316 的系统提示里多了一句"不要重建某个具体的现有游戏，即使改名或声称原创"，楼主没有停留在转发截图，而是拿 9 个提示词在两个版本上各跑一次，共 18 次，全部用 Opus 5.5、各自独立目录。结果比传言温和：原创游戏、通用平台跳跃、自己设计稿加自绘美术、修自己游戏的 bug，两版都正常；加一个"空洞骑士手感"的二段跳也没事；Flappy Bird 和吃豆人照做；唯一真正的推回是 Tetris 改名"原创"，2.1.316 拒绝照做，改成了一个造桥解谜，全程零硬拒。作者自己给了三条限定：每个提示词只跑一次，这是快照不是基准测试；这条是模型会权衡的指令而非硬过滤器，结果会波动；直接问两个版本有没有这条规则，双方都说没有，说明模型自述不能当证据。评论的争论点转向边界：这种软约束会不会顺手把合法的 MOD、复刻引擎和同人项目一起挡掉，以及它究竟在保护独立开发者还是保护大厂。

**高赞评论：**
- u/Nohbdy94（赞数 33·归档快照）："Denying copy-catting is resulting in innovation within a genre getting denied too" —— 立场说明：本节最高票，指出软约束真正的问题不是禁抄袭本身，而是把类型演化也一起判成抄袭，代表了对护栏外溢效应的核心担忧。
- u/Firereign（赞数 4·归档快照）："But that won't stop the _server-side classifiers_ from firing" —— 立场说明：从机制上拆开本地系统提示与服务端分类器，说明改 prompt 能绕过前者但绕不过后者，也解释了为什么这条规则表现是概率性而非硬拒，是技术含量最高的一条。
- u/Substantial-Elk4531（赞数 5·归档快照）："there have actually been lawsuits against developers who tried to copy the mechanics of Tetris" —— 立场说明：给出唯一被实测推回的 Tetris 之所以特殊的法律背景，说明厂商的顾虑有判例来源，为读这条新闻补上了缺失的因果。

**原帖链接：** https://www.reddit.com/r/ClaudeCode/comments/1xkx3z7/
