
All source content is in hand (14 builders / 29 tweets, 1 fresh podcast, no blog posts). Composing the digest.

AI Builders Digest — 2026-11-18

今天的主线其实不是"让 agent 写更多代码",而是"给 agent 造一个能干活的工作台"。Latent Space 那期 Stanford 课程复盘是全天最有料的一块,几乎每条都能直接拿来对着自己的工具链自检一遍。

**一、播客深读:Stanford 到底怎么教 AI-native 工程**

Latent Space · [One Million AI Engineer Special] How Stanford Teaches AI-Native Engineering — Mihail Eric, Monaco
https://www.youtube.com/@LatentSpacePod

一句话takeaway:教 agent 工程,最有效的路径不是讲原理,是让学生先手写一个两百行的 harness,再去把真实产品的 prompt 拆开看。

- 第一周就让学生用两百行写一个能跑的编码 agent,门槛只要求 CS106B 水平。第二节课直接拿 MITMProxy 拦真实 Claude Code 的请求,把 system prompt、plan prompt、compaction prompt 全摊在屏幕上——玩具版、真货、以及两者之间的差距,一次看清。这种"先造再拆"的顺序,比先讲 architecture 有效得多。

- Claude Code 的 system prompt 一度接近两万 token,砍掉八成之后又慢慢涨回来,来回跷跷板。原因不是没人管,而是"怎么用 Git"这类知识被搬进了模型权重。它早期真正赢的地方是简洁:fewer tools do more,而且是 built for where the model will go。

- 上下文处理他给的是三段式:先 research 把陌生大库摸清,再给几个备选方案让人选,然后落成 plan/spec,最后实现加测试。结论很硬——vanilla prompt 到不了百万行级别的仓库,这是规模问题,不是风格问题。

- 他更推崇 dynamic workflows:sub-agent 不要复制一个父 agent,按需写个 harness 再跑它。多 agent 最难的是上下文,fan-out 之后要来回"扩张—收缩";给多了,agent 会把你随口一句话当成法律去执行,然后犯很低级的错。

- 关于 skills,他说多数人只会消费不会写,naive 写出来通常很差——"写 skill 本身是需要一点 skill 的"。最烦的是 trigger 写太宽,在无关项目里误触发。更值钱的用法是拿 skill 承载组织级最佳实践,而不是单纯为了省一次 prompt。

- Agent-ready 仓库是后面一切的地基,但企业真正的卡点常常不是缺 agent,是 merge queue 堵住、起一个 app 太慢,"再加一个 SRE bot 不会是答案"。瓶颈随后会移到评审:一天三十多个 PR,人一插手就成了速度上限;而该守的不是 PR 描述,是整个代码库的 spec。

- 建与买的原则是 buy to learn, build to keep。Monaco 自建了基于 Coder.com 的后台 agent 平台 Monocoder,和一个一半 AI SRE、一半客服的 Slack bot Hal;但 code review 留给 Devin——而且第二次没人推,是工程师自己要加的。

- 安全他排在第七周,理由是"安全不是第一周"。真问题不是模型 bug 变多,而是你根本不知道自己在发什么(less awareness of what's being written)。边界给得很具体:数据、计费、鉴权这三块别让 agent 写,其余随便。第 11 周是白送的 make benchmarks and evals,他说这是"敲开每家前沿实验室大门的门票",SWE-bench 本身就是普林斯顿的本科项目。

**二、X 上的讨论**

**Thariq(前 Claude Code,Anthropic)· 4.8k 赞**
"software factories feel like a temporary problem. the models will learn to build them for you. the more interesting question to me is how to build a workspace where agents can collaborate with you"
翻译过来:软件工厂是个临时问题,模型早晚会自己会造;真正有意思的是怎么搭一个 agent 能和你协作的工作空间。这条是今天点赞最高的观点,和播客里"造 harness 而不是造流程"是同一个方向。
https://x.com/trq212/status/2122438326431154210

**Guillermo Rauch(Vercel CEO)· 3.9k 赞 + 两条工具链观点**
"用户是 agent 了,所以你要跑的是 evals,evals 反过来驱动软件工程循环"——他直接把旧的"用户访谈→画用户旅程"换成了"用户是 agent,你跑 eval"。另一条给出自研智能的四个动作:用开放的 SDK 和 harness、用 Gateway 保住模型选择权、自己掌握 trace 和数据并强制 ZDR、用私有推理自己握模型。对新一轮"要不要自己造引擎"的争论,这是一个相当明确的站队:基础设施层自己拿,模型层留退路。
https://x.com/rauchg/status/2122415506451841215
https://x.com/rauchg/status/2122458782294847807

**Aaron Levie(Box CEO)**
"每位员工的 token 支出曲线还看不到天花板"。他的推演是:过去 12 个月的编码能力基本是"垃圾",现在才刚刚开始能用;编码通了之后 tool use 和 computer use 才打开知识工作的门;再往后是 agent swarm 和后台 agent,它们消耗的 token 会远超现在能想象的量级。对做基础设施的人是好消息,对做成本控制的人不是。
https://x.com/levie/status/2122508098351038532

**Garry Tan(YC 总裁)· 自研引擎进行时**
GBrain 接下来几周要上一个用 Rust 写的后端引擎,直接把 postgres+pgvector / pglite 换掉,自己承接 vector search、graph search、embeddings、RAG 和 HNSW。他说这是用 Vorflux 当 software factory 做的"好玩项目"。另一条提到 GBrain 的 Hosted 版本原生支持"个人 brain 汇总成团队 brain、再汇总成公司 brain"。这条值得留意:YC 自己下场把记忆/检索层从 Postgres 生态里拔出来。
https://x.com/garrytan/status/2122576951080792543
https://x.com/garrytan/status/2122517681740124271

**Nikunj Kothari(fpv ventures 合伙人)· 2026 基础设施战争**
"Vibe coding 在 Q1,harnesses 在 Q2,sandboxes 在 Q3,agentic CI 在 Q4",然后补一句 provider 多到记不住,问大家猜下一个是什么。这个季度划分有点粗糙,但"harness → sandbox → agentic CI"这条演进顺序,基本就是过去一年 agent 工具链的真实叠层方式。
https://x.com/nikunj/status/2122543500814336281

**Peter Steinberger(OpenClaw)· 1k 赞**
"人们:求求减少权限弹窗,让 agent 能在 macOS 上干活不用一直盯着 / Apple:收到,给你加一批更吓人的弹窗"。桌面端 agent 的权限模型现在是真瓶颈——不是能力不够,是每一步都要人点确认。
https://x.com/steipete/status/2122463466304971068

**Josh Woodward(Google 副总裁,Google Labs / Gemini)与 Google Labs**
Gemini Notebook 现在能把你的资料源直接变成可交互站点,他给的例子是用元素周期表做的,"好做、好分享"。Google Labs 同时宣布欢迎 Howie 团队加入,对方多年在做日程和日历管理,目标指向给中小企业做下一代 AI 工具。产品侧的动作比模型侧更值得看。
https://x.com/joshwoodward/status/2122453269842886788
https://x.com/GoogleLabs/status/2122461899178820069

**Peter Yang(AI 教程作者)· 让 Claude 不做 AI slop 的五条**
来自 nateparrott 的实践:一是 upfront 给足上下文(截图、喜欢的页面、过去的作品,已有产品就让 Claude 从代码重建真实界面);二是让它先研究熟悉的 UX pattern;三是明确告诉它自己的设计偏见——"模型根本不知道自己的 bias 是什么",在 design.md 里禁掉 serif、米白背景、卡片边条这些 tell;四是先出 wireframe 再谈字体颜色;五是让它一次给 5 个方案再 remix。这套东西本质上是把"风格约束"写进 context,和写 skill 是一个道理。
https://x.com/petergyang/status/2122347721298510021

---

今天值得带走的两个判断:一是 harness 层的价值正在被反复确认——Stanford 用两百行让学生亲手造一遍,Monaco 自建 Monocoder,Vercel 强调 open harness,YC 干脆把检索层用 Rust 重写;二是瓶颈已经从"agent 会不会写代码"挪到了评审、merge queue 和权限模型这些组织与系统边界上。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
