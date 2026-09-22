
AI Builders Digest — 2026-09-20

（数据来源：Follow Builders 中央 feed，抓取于 2026-09-19，内容新鲜；今日官方博客无更新）

---

## 一、X / Twitter

### Claude Code 开始支持 AGENTS.md，并预告 "mods" 机制 —— Anthropic 的 Thariq（Claude Code 团队）

今天讨论度最高的一条：Claude Code 从 2.1.277 版本起，如果目录里没有 CLAUDE.md，会主动去找并用 AGENTS.md，行为可在 /config 里开关。Thariq 同时透露，AGENTS.md 支持本身就是基于他们即将推出的 "Claude Code mods"（自定义 Claude Code harness 的方式）做的，AGENTS.md 是内置的第一个 mod，用户之后可以自己构建自定义的项目指令版本，mod 的源码也已公开。

这条的点赞量 25,553、转发 2,174，是本次 feed 里绝对的头部。为什么值得关注：AGENTS.md 是社区自发形成、被多个 agent 工具（Codex、Cursor、Amp 等）采纳的跨工具约定，Anthropic 主动兼容等于承认"单一厂商私有配置文件"的时代在退场；而 "mods" 这个概念暗示 harness 本身正在被产品化成可插拔层，这对自研引擎/Agent 工具链的人来说，是一条明确的架构信号——上下文管理、指令加载、工具装配，未来都会变成可替换组件。

- 主帖：https://x.com/trq212/status/2101009392611278961
- mods 说明：https://x.com/trq212/status/2101009393731223817
- mod 源码：https://x.com/trq212/status/2101009395052343462

### 开源模型在 Vercel AI Gateway 上的 token 占比冲到 78.4% —— Vercel CEO Guillermo Rauch

Rauch 发帖贴出当天 Vercel AI Gateway 的数据：按 token 量计，open models 占 78.4%，closed 占 21.6%，可能是历史新高。更值得注意的是按花费（spend）算的排名——当天第 3、第 4 名是 Moonshot AI 和 DeepSeek，把 Z.ai 加进来之后，三家合计的花费已经超过第 2 名的 OpenAI。他特意加了一句限定：这是"跨供应商的推理花费（大多发生在美国）"，不是直接流向开源权重实验室的收入。

为什么值得关注：token 占比高说明开源模型吃掉了绝大多数调用量，但真正有说服力的是 spend 排名——它意味着这些调用不是"便宜货补位"，而是在真实付费工作负载里占住了位置。同一天 Rauch 还在推 Jev 的采用率，说"数据和轶事都令人震惊，所有人都在用"，并把它归因于 "AI 太贵/太慢" 的时代情绪，认为人们现在急于把 AI 塞进更多地方。

- token 占比数据：https://x.com/rauchg/status/2101186741042663579
- Jev 采用率的判断：https://x.com/rauchg/status/2101079472732848510
- Vercel 上免费开放 Jev：https://x.com/rauchg/status/2101116978677285241

### "Jev 会成为 agent 做瞬间决策的新一类用例" —— Box CEO Aaron Levie

Levie 认为 Jev（Typeface 出的极速小模型）在企业的价值在于让 agent 能做"秒级判断"：工作流里的分叉、数据分类、judgment call 以及其他几百种场景。他给了一个 Box × Jev 的 demo：从 Box 里取出事故报告，判断是否面向客户、严重程度如何，然后把文件移动到 escalate / monitor / review 三个文件夹之一，并写入 metadata template 实例——整个过程"几乎瞬间完成，且几乎零成本"。他列举的延伸场景包括保险理赔、合同管理、贷款审批、安全审查、客户日志分析。

为什么值得关注：这是目前对"快而便宜的小模型"最具体的一份企业落地清单。关键不在模型能力上限，而在于把一次 LLM 调用压缩到可以在每个工作流节点上都跑一遍的成本量级——这改变了 agent 的系统设计假设（不必再为了省 token 而做厚重的规则裁剪和缓存层）。

https://x.com/levie/status/2101007708044574906

### Jev 的实测数据：28 秒、0.11 美元给 3000 份零食打分 —— FPV Ventures 合伙人 Nikunj Kothari

Nikunj 贴了一个带多维度标准的评测：用 Jev 给 3000 份"儿童零食"打分，耗时 28 秒，花费 0.11 美元。他还顺手做了个叫 Jevable 的站点，把 X 上所有 Jev demo 收集起来、按类别筛选，允许任何人用 + 按钮提交自己的项目。

为什么值得关注：28 秒 / 0.11 美元 这种量级的数字，是判断"哪些批处理任务终于值得用 LLM 做"的标尺。很多过去因为成本和延迟被排除在外的任务（全量数据打标、per-record 判断），在这个价位上会重新变成可选项。

- 实测数据：https://x.com/nikunj/status/2101006585481073093
- Jevable 展示站：https://x.com/nikunj/status/2101077053567332618

### 让 agent 管 agent：roboclaw 接管团队服务器 —— OpenClaw 的 Peter Steinberger

Steinberger 分享了一个挺有意思的部署形态：roboclaw 在跑他们的团队服务器，挂在 Discord 上，和 gpt-live 通话，并且知道自己在同时处理的所有 session；开会时可以直接问它当前和过往 session 的上下文。另一条里他提到，让 agent 帮忙整理自己的 session 列表已经成了习惯（"打开 home sidebar，让你的 claw 重排 session"），并且强调 CUA（computer use agent）在这些界面里都可用，所以 agent 可以比单纯截图更高效。他还提到会让人在 PR 落地前"劫持 session 去 slop 清理"。

为什么值得关注：这是 agent 反过来治理 agent 工作流的真实案例——session 本身变成可被查询和整理的一等对象，而不是散落的日志。"CUA 比截图更高效" 也点出了 computer-use 路线的效率分水岭：结构化操作 > 视觉模仿。

- roboclaw 团队服务器：https://x.com/steipete/status/2101141707375227372
- session 整理与 CUA：https://x.com/steipete/status/2101115690719809873
- session 重排技巧：https://x.com/steipete/status/2101139037801283997

### 个人 agent 替用户打电话砍账单 —— Peter Yang（AI 教程与访谈作者）

Peter Yang 说 Meta 的 Muse 是他试过最好的个人 agent，帮他一年省下 800 美元以上的宽带和话费，并称"能想象 Muse 成为 Meta 的下一个十亿用户应用"。他放出了 Muse 与 Comcast 谈判、拿到 288 美元年费的电话文字记录，评论是："说实话，大部分公司的客服线路都没准备好迎接 agent。"

为什么值得关注：这是消费级 agent 少见的、有可验证数字的落地场景。同时它也预告了一个很快会出现的现实问题——当客服系统面对大量 agent 来电，验证、身份和博弈规则都会被重写。

- Muse 用例与省下的钱：https://x.com/petergyang/status/2101033599319613533
- Comcast 通话文字记录：https://x.com/petergyang/status/2101083891507593576

### 为被质疑的 demo 辩护 —— Every CEO Dan Shipper

Dan Shipper 公开为 Jack Cheng 的一个 demo 辩护：虽然 X 上确实有大量夸张的 AI demo，但把 Jack Cheng 的作品说成 "fake" 让他很难过，评价对方是"我合作过最聪明、最知性诚实、最专注工艺的人之一"，并说这个 demo "既是真实的，也是对未来的有趣一瞥"，直言 "not a good look"。

为什么值得关注：这是本周社区里最有代表性的一场争论——"demo 造假"指控与"demo 本来就是前瞻性展示"之间的边界。在产品宣传与真实能力差距被反复放大的当下，这类争议会持续影响公众对 AI 进展的信任。

https://x.com/danshipper/status/2101155521818476693

### 其他短讯

- **OpenAI 的 Thibault Sottiaux（Codex & ChatGPT）** 预热即将到来的 keynote，说和 Romain Huet、Sam Altman 一起准备时最麻烦的是"好东西多到有点荒谬、要挤在很短时间里讲完"，并承诺"下周就会有一些东西"，不必久等。这条点赞 3,650，是本次 feed 里除 Claude Code 外的第二高点——说明外界对 OpenAI 开发者侧更新的预期很高。https://x.com/thsottiaux/status/2101157729037586694
- **Zara Zhang（独立开发者）** 一句被广泛转发的观察："当你消费的大多是垃圾时，你很难不生产垃圾。要修输出，先修输入。"对做内容/数据管线的人来说，这是对数据质量决定产出质量的直白提醒。https://x.com/zarazhangrui/status/2101123389528457596

---

## 二、PODCASTS

### No Priors：为什么 diffusion 会赢下 AI 推理 —— Inception 联合创始人兼 CEO Stefano Ermon

**一句话结论：Ermon 押注 diffusion 语言模型，不是因为它更聪明，而是因为"推理时的并行度"才是决定智能/每瓦、智能/每美元的关键，而自回归模型在推理时本质上仍是串行的。**

Ermon 是斯坦福教授，也是 diffusion 的奠基者之一（2019 年和博士生 Yang Song 提出 score-based 生成模型，后来演化成现代 diffusion，进而催生 Stable Diffusion、Midjourney）。他两年前创立 Inception，目前约 50 人，做的产品是 Mercury——基于 diffusion 的语言模型。

他的核心论证是一条漂亮的历史类比：2017 年人们从 RNN 换到 transformer，是因为 RNN 必须逐个 token 串行处理，训练太慢；而 transformer 能并行处理多个 token。但**推理阶段的自回归模型仍然串行**——不生成前 9 个 token 就没法生成第 10 个。这类负载极度 memory bound，时间几乎全花在内存层级之间搬运权重上，算术密度很低，根本吃不满 GPU。"那么和 RNN→transformer 对应的那一步是什么？就是 diffusion。"因为 diffusion 在推理时的工作负载和训练时几乎一样——同时处理大量 token 并行计算。他甚至把它上升为 bitter lesson 的推论："更并行的方案最终一定会赢。"

对抗性证据也有：2024 年他的组首次证明，在 GPT-2 规模（不到 10 亿参数）上，把 transformer 当 diffusion 模型训练，可以达到与自回归模型相同的困惑度，同时生成速度约快 10 倍。如今的 Mercury 在 benchmark 上与各家的 speed-optimized 小模型（Haiku、Flash、mini/nano 类）相当但明显更快，已经生产上线。有意思的客户案例是语音 agent 公司 Open Call：他们原来把 LLM 跑在 Cerebras 定制芯片上来换取速度，切到 Mercury 后，用普通 NVIDIA GPU 就拿到了同等速度——更高的可用性、更低的成本、更好的质量。

几个值得记住的细节：
- **必须自建推理引擎。** diffusion LLM 跑不了 vLLM 或 SGLang，他们自研了 serving engine、kernel、SFT/RLHF/RL 全套栈，选择不开源以保留 IP。代价是生态薄、难被采用、难做本地部署。这也是他对抗大厂的核心论点：护城河不只是模型权重，而是 serving engine 这类"没有它模型根本跑不起来"的组件。
- **控制性可能是被低估的差异化。** 自回归模型必须等整个输出生成完才能用 reward 打分；diffusion 是"粗到细"的迭代去噪，一开始就能判断方向，因而可以用外部 reward 或约束去 steer 生成过程——这在学术文献里有相当证据，而且是很可能只在 diffusion 上存在的交互形态。
- **先赢速度，其他是未知数。** 他坦言速度是当初"最容易测试"的切入点；但 diffusers 可能更数据高效（加噪再学习去噪本身就相当于数据增强），如果这点在规模上成立，当数据成为瓶颈时意义会大幅上升。
- **市场量级判断：** 他用 OpenRouter 的任务分类做估算，认为约 20%~30% 的工作负载对延迟高度敏感，至少是这个下限是可被"在给定延迟预算内质量最高"的模型吃掉的。
- **关于递归自我改进：** "我们现在还没到那一步。"他用前沿模型加速了自己的迭代，但认为"人的独创性目前仍然极其重要"——想出对的点子、剪枝搜索空间、识别有希望的方向，是当前不可替代的部分。他也给学术研究打了气：flash attention、DPO 都源自他的实验室，"gem 是存在的"。

为什么值得关注：如果推理经济性是接下来的主战场，那么"更并行 = 更省钱"这条链会直接冲击现有自研引擎的假设——尤其是当你的瓶颈在 memory bandwidth 而不在 FLOPS 时，架构选择会比模型规模更早决定单位成本。同时"必须自建 serving 栈"这一点，对任何做自研推理栈的人都是既提示机会、也提示工作量。

https://www.youtube.com/@NoPriorsPodcast
（注：feed 中仅有频道链接，未提供单集直链）

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
