
## r/LLM 今日热帖精选

### 1. Gemini seems useless for coding? It hallucinates non stop.
**摘要：** 这条讨论围绕 Gemini 在编程任务中的幻觉和上下文保持问题展开。主帖认为 Gemini 在代码文件理解、上下文连续性和错误自我纠正上表现不稳定，评论区则给出更细的分歧：有人认为它更适合 Google 生态里的通用助手和多媒体场景，也有人把 Gemini Flash 当作 IDE 内快速问答模型使用，但不适合复杂 agentic workflow。值得关注的是，这类反馈把“模型能不能写代码”拆成了交互速度、文件上下文、长期任务可靠性和产品定位几个维度，比单一榜单更接近真实开发体验。

**高赞/高信号评论：**
- u/pmmaoel（2赞）：Gemini was never meant to be good at coding. Google picked it's battles and is winning in other areas like mass consumer adoption of AI helpers like the ones in Google suite, on chrome, on android, AI search mode or the image/video gen models. They k…
  - 立场说明：这条评论提醒读者区分模型产品定位，不应只用 coding 能力评价 Gemini 的整体价值。
- u/TokenRingAI（1赞）：Gemini 3.5 Flash is my main model for interactive coding chat in my IDE. It works great for that. Super fast. Reasonably intelligent. It does have a high hallucination rate, and is terrible at agentic work. I tested it extensively in our agent workfl…
  - 立场说明：这条评论给出具体使用边界：适合快速交互式问答，但不适合作为自主执行型 coding agent。
- u/GlompSpark（1赞）：Well, first it claimed it could only see the beginning and end of the file, then it claimed it could actually see the entire file, then it claimed it could not find the file in the context window. Later, it said it was only able to read up to line 3k…
  - 立场说明：这条评论提供了可复现的上下文管理失败案例，说明问题不只是主观偏好。

**原帖：** https://www.reddit.com/r/llm/comments/1uy7ho5/

### 2. Training an LLM from scratch — which architecture to start with?
**摘要：** 这条讨论来自想从零训练 LLM 的学习者，核心问题是该从哪种架构入手。评论区的主流建议不是追最新架构，而是从 GPT-2、NanoGPT 或小型 Qwen 这类资料充分、实现简单、资源需求可控的路线开始；也有人补充了 12GB 显存、RTX 4070 Super、30B tokens 级数据下载等实际成本信息。值得关注的是，讨论把“训练一个 LLM”从抽象愿望落到了工程约束：显存、训练时长、数据来源、代码可读性和学习反馈周期才是入门阶段真正决定成败的因素。

**高赞/高信号评论：**
- u/BidWestern1056（3赞）：you should do qwen but also check out a new type of small model to train https://github.com/gowrav-vishwakarma/qllm2
  - 立场说明：这条评论提供了可直接探索的替代路线，适合想比较 GPT 系和 Qwen 系实现的人。
- u/benawheeler（3赞）：NanoGPT or GPT-2, can be trained with like 12GB of VRAM but it takes a while, like 7-14 days of constant training depending on your GPU. I’ve done this with an RTX 4070 Super lol. Like 30B tokens can be downloaded from huggingface Nemotron-CC-v2 or f…
  - 立场说明：这条评论价值较高，因为它把硬件、时间和数据规模讲清楚，能帮助判断训练计划是否现实。
- u/thinking_byte（2赞）：Just start with GPT-2. It's simple, well documented, and makes the whole learning process a lot less overwhelming.
  - 立场说明：这条评论强调降低复杂度，对入门训练项目比追新架构更实用。

**原帖：** https://www.reddit.com/r/llm/comments/1ux69t8/

### 3. Introducing Uyu-2-28B: Better Than Gemma 4 31B at Role-Playing
**摘要：** 这条讨论围绕 Uyu-2-28B 这个偏角色扮演/创作写作的新模型展开，主帖声称其效果优于更大的 Gemma 系模型。评论区没有只停留在“好不好玩”，而是提出了上下文中途截断、MacBook 16GB 内存无法运行、希望有 MLX 或更小版本、是否应剪枝/微调等实际问题。值得关注的是，它反映了开源模型发布后的典型落地门槛：榜单或主观体验之外，用户真正关心的是长上下文稳定性、本地硬件适配、模型尺寸和是否能迁移到 coding 等非角色扮演场景。

**高赞/高信号评论：**
- u/tomByrer（5赞）：I'd love to see a version that was pruned of role playing & creative writing to be stronger at coding....
  - 立场说明：这条评论指出模型能力取舍问题，说明用户希望把创作模型的部分能力迁移到 coding 场景。
- u/pokefake（2赞）：As a Korean user, I’m really interested in the Uyu-2-28B model you’ve released. However, I’m unable to run it at all on my M1 MacBook with 16GB of RAM. It might be asking too much, but I’d love to see an MLX version of a 12B model based on Gemma, lik…
  - 立场说明：这条评论把问题落到本地部署门槛，尤其是 Apple Silicon 和小内存设备的可用性。
- u/smflx（2赞）：I have the same interest of reducing model for creative writing but possibly losing coding. But, pruning 8% seems small for taking risk, I would rather skip it & fine tune the full model. Just curious why you did. Also, any chance of reducing more?
  - 立场说明：这条评论关注剪枝与微调的工程取舍，能帮助判断模型改造是否值得承担能力损失风险。

**原帖：** https://www.reddit.com/r/llm/comments/1uvxteg/
