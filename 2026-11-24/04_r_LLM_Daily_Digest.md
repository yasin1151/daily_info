
**r/LLM 今日速递 · 2026-11-24**

Reddit 三个入口（www / old / redlib）本轮全部不可达，以下内容取自 arctic-shift 归档快照。r/LLM 今天帖子不少但评论极薄：0-720 小时内 345 个候选帖里，真正攒到 3 条以上真人评论的只有个位数，所以这期只推 3 条有实际讨论的。赞数是归档抓取时的快照，可能滞后，标 1 的基本都是入库默认值，不代表热度。发帖时间分别是 11-13、11-19、11-23，前两条是本轮补读。

---

## 1. Skills + Code Mode MCP：上百个工具塞进 agent 而不炸上下文

**摘要：** 作者在给公司写 MCP server、同时做个人 agent Nanabot 时撞上同一个问题：工具一多，光是把每个方法的详细描述塞给模型就要吃掉大量上下文。他引的极端案例是 Cloudflare——2500 多个 API 方法如果全按 MCP 工具描述展开，估算要 117 万 token。Code Mode MCP 的做法是只给 agent 两个入口：search() 按需查方法签名，execute() 直接跑 JS，一次调用里串起多个方法再返回结果，中间不必回模型。但作者提醒省下来的并不白省：反复搜索、按需加载签名同样消耗 token，实际收益取决于目录规模、搜索频次和调用次数，必须拿具体任务实测。他补上的关键一环是 Skills——先告诉 agent 有哪些工具族、什么时候该去搜，否则模型根本意识不到自己需要找工具。对正在把 MCP 扩到几十上百个方法的团队，这是目前少见的落地拆解。

**高赞评论：**

- u/everyjourney（赞数 2·归档快照）："Great write-up, thanks for this!" 立场说明：纯正面反馈，说明这篇拆解在版内被当成可转发的资料，但没补充任何实现细节。
- u/ApprehensiveAd1946（赞数 1·归档快照）："a thorough breakdown on code mode and what it is just as larger platforms like OpenCode and Claude are adapting them" 立场说明：把 Code Mode 看成正在被大平台吸收的通用方向，等于给作者的方案投了信任票。
- u/random_user-1234（赞数 1·归档快照）："Are you describing something new or just an introduction to code mode and skills for people that might not know?" 立场说明：全场唯一的质疑——他认为这更像科普而非新方法，提醒读者别把综述当成原创贡献。

原帖：https://www.reddit.com/r/LLM/comments/1xv57a6/

---

## 2. 两块 3060 微调私有语言模型，卡在"效果中等"

**摘要：** 发帖人想在自己机器上跑一个专写某种私有语言的模型：Linux、64GB 内存、Ryzen 9 5900X、两块 GTX 3060 12GB。他已经在 Qwen2.5-Coder-14B-Instruct 上用 QLoRA 微调私有语言的训练数据，再量化成 Q5_K_M GGUF 交给 Ollama，结果只能算中等；也试过 Claude Code CLI，但抱怨它吃的 token 太多。他想问还有没有别的路子。这条帖的价值不在答案而在边界：评论区没给出可行方案，第一条回复是"不如从零训一个中等规模的 transformer"，被楼主反问"那我该从哪开始"，对方只回了句"TensorFlow 能做 transformer"。对同样想用消费级显卡微调私有语言的团队，这是很现实的提醒——14B 级 QLoRA 加两块 12GB 卡跑得通，真正决定成败的是数据质量和评测集，社区不会替你把这块补上。

**高赞评论：**

- u/ProbablyDoesntLikeU（赞数 1·归档快照）："Maybe you're better off making a medium/large transformer from scratch?" 立场说明：全帖排在最前的建议，但方向跳得太远——从微调直接跳到自研预训练，没有回应 12GB 显存和私有语言数据量的现实约束。
- u/nelgin（赞数 1·归档快照，楼主）："Maybe if I knew where to start :)" 立场说明：楼主一句反问点出了这类建议的空洞：对没有预训练经验的人，"从零开始"等于没有方案。
- u/ProbablyDoesntLikeU（赞数 1·归档快照）："Tensor flow does transformers" 立场说明：被追问后只丢了一个框架名，没有训练流程、数据配比或评测方法，属于典型的"点到为止"式回答。

原帖：https://www.reddit.com/r/LLM/comments/1y04etw/

---

## 3. 问 AI 家教到底有没有用，回帖只在谈态度

**摘要：** 一位数学吃力的学生发帖问：能不能让 Claude、Gemini、ChatGPT 根据他的兴趣（心理学和恐怖题材）造一套类似 IEP 的方案，把概念讲透再反复出题直到掌握，他想知道怎么才能从 AI 家教里拿到最大收益。三条回复分成两派：一派认为效果很好，甚至比人类老师更合自己的节奏；另一派担心把思考整个外包出去之后，人就不会自己想了。整条帖子没有具体方法，但它照出了当下 AI 家教讨论的真实水位——大家在谈态度和感受，很少有人给出可验证的做法，比如怎么设计间隔重复、怎么防止模型顺着学生的错误思路一路确认。想认真用 AI 补课的人，评测这一环还得自己补。

**高赞评论：**

- u/ChillingChasuble（赞数 2·归档快照）："Very effective at tutoring. I like using an LLM to learn a subject better than a human teacher." 立场说明：正面体验派，理由是可自定节奏、不怕问蠢问题，但没有说明用什么方法验证自己真的学会了。
- u/PsychoticRuminator（赞数 2·归档快照）："if we offload all of our thinking onto technology, how can we think for ourselves?" 立场说明：这条是把问题从"效果"拉到"代价"——他认为风险不在答案对不对，而在长期依赖会削掉自主思考能力。
- u/joeyda3rd（赞数 1·归档快照）："Who needs to learn math anymore? /s" 立场说明：带 /s 的调侃，代表版内对"AI 代劳学习"的一类疲惫情绪，信息量低，但能看出这个话题已经被玩成梗。

原帖：https://www.reddit.com/r/LLM/comments/1y3h21i/
