
# r/LLM 今日热帖 · 2026-11-23

Reddit 仍未解封，本期经 arctic-shift 归档通道抓取。赞数为归档快照（多为入库默认值 1-3），不代表真实热度，因此不做"高赞排序"，评论按页面默认顺序取信号最高的几条。本期扫了 213 个候选、逐个探评论树，真实评论达到 3 条的只有 3 个帖子（其余多为零评论自推/展示帖），故只推 3 条。

---

## 1. 给 0.6B 模型一个天气工具，它不调用、直接编了"孟买正在下雨"

**摘要：** Cluaiz（开源推理引擎）的贡献者做了一组小型模型工具调用测试：5 个工具（天气、汇率、提醒、文件检索、邮件）、40 条 prompt、温度 0，其中 24 条明显该调工具、8 条是间接表达（"今天在伦敦需要带伞吗"）、8 条根本不需要工具。Qwen3 0.6B Q4_K_M 关闭思考只对 27/40，间接提问几乎全灭（1/8），而 32 条本该调工具的题里有 8 条直接编答案——"孟买目前正在下雨""开罗现在 35 度""今天晴天所以带伞"，参数也常写错（把 GBP 写成 british pounds）。打开思考后升到 34/40，间接提问从 1/8 到 7/8，代价是单次请求中位延迟从 2.0 秒涨到 3.6 秒，还多了一次不该有的调用。作者把全部原始回复放进了仓库，真正的问题是：本地小模型能不能放心交给工具，以及有没有不开思考也能压住"编天气"的提示写法。

**高赞评论：**
- u/xRebellion_（赞数 2·归档快照）：想要稳定的工具调用得上更大更新的模型，他点名 minicpm5（1-2B 那个记不清）和 lfm3 1.7B，两个都在 Q8、约 1-2GB 占用下跑过，"asked it to read and edit certain files and it seems good enough for tool calls"；并给了关键技巧——"steer it using system prompts to get the behavior you want"。立场说明：认为 0.6B 已触及能力地板，与其调参不如换 1-2B，再靠提示把间接提问补上。
- u/Character-Blood3482（赞数 2·归档快照）：qwen 3 0.6 是他 16GB 内存 i5 笔记本上唯一跑得动的思考模型，30 tok/s，"it was a beast (in term of speed / quality)"；他"i prefer think on"，需要快就换成原生不带思考的模型（如 gemma 3），而不是手动关开关。立场说明：从老机器端侧视角确认小模型仍有实用价值，并给出"换模型而非关开关"的操作路径。
- u/CommissionOdd3082（赞数 1·归档快照，楼主）：0.6B 是他特意挑的，"I picked 0.6B on purpose to see where the floor is"；他承认直接提问 18/24、间接提问 1/8 的落差说明崩在"自己判断该不该调"这一步，接下来要试在 system prompt 里按问题类型映射工具，再做对比。立场说明：作者本人把失败归因到工具选择而非参数生成，这个归因决定了后续优化方向。

原帖：https://www.reddit.com/r/LLM/comments/1y1zct6/

---

## 2. 家里的 AI 集群：挖矿时挖矿，来 LLM 任务就自动停矿让出全部算力

**摘要：** 作者晒出家里的多机 AI 集群：机器平时挖矿，一旦有 LLM 任务就自动停矿、把全部显存和算力让给推理，编排层按可用模型在 opencode 与 nginx 之间切换。仪表盘把多台机器上三个模型的遥测统一到一个界面，每 2 秒刷新，可自定义 API key 并推送到对应机器，还带导出快照用于分析优化。评论区里作者补充，这块面板本身就是让 qwen3.8-Flash-Next 与 glm5.3-F 一起出框架、配置和布局，最后用 opus 5.5 做视觉收尾；指标直接取自各引擎原生 /metrics，不额外搭一套可观测栈。对自建多机推理池的人来说，这条给出的是"闲置算力套利 + 便宜模型干主体活、贵模型只做收尾"的完整拼法，也顺带说明监控可以很轻。

**高赞评论：**
- u/d-motions（赞数 1·归档快照）：解释面板是 qwen 3.8 FN 与 glm 5.3 F 协作出框架、配置和主布局，opus 5.5 只负责最后一 pass 的观感（磨砂玻璃、背景），并因为"most of the time there are just some monochromatic dashboards"才特意做了三套配色；方法论一句总结——"Do all the difficult work with your local llm and only use the expensive tokens on your final touches"。立场说明：这条把"分层用模型"从口号落成了具体分工，是整帖最可复用的部分。
- u/mikewagnercmp（赞数 1·归档快照）：追问面板是自研还是 grafana 搭的，"I have a fancy grafana dashboard for my unraid machine"，还在从 kilo 和 Claude 的会话数据库里抓会话数据，考虑把推理指标存进 prometheus。立场说明：代表已有可观测栈的一方，关心的不是面板好看，而是能不能与现成的 prometheus/grafana 体系对接。
- u/motionride_nr1（赞数 1·归档快照，楼主）：面板把各机器上三个模型的指标统一成一套视图，"It updates once every two seconds"，配置侧可以改 API key 和每个模型的若干参数并下发到对应机器。立场说明：补齐了实现细节——统一指标口径加 2 秒轮询，比接一整套重型监控便宜得多，适合个人集群。

原帖：https://www.reddit.com/r/LLM/comments/1y2q923/

---

## 3. "LLM 给的建议到底有几个靠谱"：评论区没吵架，反而拆出了三个失效机制

**摘要：** 楼主问了一个很朴素的问题：让 Claude、Gemini、ChatGPT 处理"怎么跟伴侣开口""怎么道歉"这类日常人际问题，到底有多少次真的有用、多少次帮倒忙。九条回复没有滑向玄学，而是集中到三点：一是恐惧故事存在幸存者偏差，机器劝你分手的段子传播力远高于一千次"用我感受句式"的平庸建议；二是真正的风险不是内容烂，而是行文太自信、结构太完整，让人误以为在读一个有推理支撑的结论——模型会顺着你的立场写五段论证，问"怎么证明我老婆在煤气灯我"，它就给你搭一套严密案卷；三是用户自己漏关键事实、把自己写成受害者，模型只能照着错的输入算。也有人认为能力在快速变化，半年前很少给好建议、现在经常可以，但对争议性、社交类决策仍然很弱。

**高赞评论：**
- u/AENocturneOfficial（赞数 3·归档快照）：用"你只听到输钱的人讲硬币"的比喻说幸存者偏差，指出危险不在建议糟糕，而在"the text sounds so confident and well structured that it tricks your brain into thinking you're reading a reasoned argument instead of a probabilistic guess at the next word"；模型是确认偏误的镜子——问"怎么冷静地跟我老婆谈"，它给你脚本，问"怎么证明她在煤气灯我"，它给你一套无懈可击的法律论证。立场说明：把问题从模型能力转到提问者意图，是这条讨论里最有产品含义的判断。
- u/Bed-After（赞数 1·归档快照）：认为模型没有生活经验可依，"It took literal decades of mistakes, and trial and error, to reach the conclusions I did"，AI 没犯过错，能做的最多是抓取一堆听起来悦耳的鼓励话。立场说明：代表"经验不可替代"一派，是对能力乐观论最直接的反驳，也解释了为什么这类建议总显得正确但无用。
- u/MainBeneficial3742（赞数 1·归档快照）：觉得变化极快，自己在用 gemini 4 neon，"it gives good advices surprisingly often"，一年前很少、现在经常；但他补了一句限定——"llms are still bad at controversial decisions, social decisions"，而且你必须把问题讲清楚，不能一句话就指望好结果。立场说明：既给了能力在涨的实测体感，也没有否认边界，属于对前两条的折中修正。

原帖：https://www.reddit.com/r/LLM/comments/1y2ogot/
