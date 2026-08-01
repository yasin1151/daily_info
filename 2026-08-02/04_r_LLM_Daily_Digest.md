
# r/LLM 今日热帖精选

## 1. I don't think Anthropic and OpenAI will survive

**摘要：** 这帖讨论“I don't think Anthropic and OpenAI will survive”。背景是 LLM 社区正在快速把注意力从单纯模型发布转向真实使用中的成本、可靠性、推理质量和工具链集成。主帖与评论区的核心信息显示，大家更关心它在日常开发、Agent 编排、API/本地部署或生产工作流里是否稳定可复现，而不是只看宣传指标。值得关注的是，评论里出现了具体限制、迁移顾虑和实践经验：At this point the harness and ease of use is much more important than the model itself. We keep hearing about Kimi, Deep；I have it from a US provider at 20 cents per mtok and 100 TPS now. I don’t know what you’re doing…。这些反馈能帮助判断相关产品或模型变化是否具备落地价值。

**高赞/高信号评论：**
1. u/FatefulDonkey（赞数：11）：At this point the harness and ease of use is much more important than the model itself. We keep hearing about Kimi, DeepSeek, and how cheap they are. But if I can't just download and use them directly in a terminal, what's the point。立场说明：这代表一线用户对成本、可靠性或工作流影响的直接反馈，比单纯参数宣传更有参考意义。
2. u/look（赞数：1）：I have it from a US provider at 20 cents per mtok and 100 TPS now. I don’t know what you’re doing…。立场说明：它补充了落地视角：真正决定是否采用的往往不是模型名，而是上下文、工具链和失败处理。
3. u/anykeyh（赞数：6）：Well, it's not that hard honestly; with OpenRouter it's a few clicks, adding Hermes or pi or whatever open agentic with it and you're ready to go. Max 10 minutes of setup. Now, if you mean run on your machine, DeepSeek v4 Flash is at the frontier of what is…。立场说明：这类经验有助于判断该变化是否能进入生产流程，而不只是停留在演示或营销层面。

原帖链接：https://www.reddit.com/r/LLM/comments/1vcp33f/i_dont_think_anthropic_and_openai_will_survive/

## 2. ChatGPT plus versus Claude Pro, (20 dollars/months) which is the bang for the buck?

**摘要：** 这帖讨论“ChatGPT plus versus Claude Pro, (20 dollars/months) which is the bang for the buck?”。背景是 LLM 社区正在快速把注意力从单纯模型发布转向真实使用中的成本、可靠性、推理质量和工具链集成。主帖与评论区的核心信息显示，大家更关心它在日常开发、Agent 编排、API/本地部署或生产工作流里是否稳定可复现，而不是只看宣传指标。值得关注的是，评论里出现了具体限制、迁移顾虑和实践经验：I too would recommend claude pro. I use Claude Opus as orchestrator and sub agents using open models via zap；ChatGPT plus is a better option, using GPT 5.6 Luna you will have a lot of ussage。这些反馈能帮助判断相关产品或模型变化是否具备落地价值。

**高赞/高信号评论：**
1. u/Normal-Cattle5915（赞数：1）：I too would recommend claude pro. I use Claude Opus as orchestrator and sub agents using open models via zap。立场说明：它补充了落地视角：真正决定是否采用的往往不是模型名，而是上下文、工具链和失败处理。
2. u/SkyImmediate5924（赞数：1）：ChatGPT plus is a better option, using GPT 5.6 Luna you will have a lot of ussage。立场说明：这类经验有助于判断该变化是否能进入生产流程，而不只是停留在演示或营销层面。
3. u/FailCharacter2933（赞数：1）：Claude is definetly the smarter one when it comes to coding but GPT is in total the faster, more generous and smarter in general tasks。立场说明：评论提供了反方或限制条件，可防止把单个案例过度外推成普遍结论。

原帖链接：https://www.reddit.com/r/LLM/comments/1vapzk2/chatgpt_plus_versus_claude_pro_20_dollarsmonths/

## 3. Bonsai 27B (3.9 GB) --- is it any good for coding or just useless toy... ?!

**摘要：** 这帖讨论“Bonsai 27B (3.9 GB) --- is it any good for coding or just useless toy... ?!”。背景是 LLM 社区正在快速把注意力从单纯模型发布转向真实使用中的成本、可靠性、推理质量和工具链集成。主帖与评论区的核心信息显示，大家更关心它在日常开发、Agent 编排、API/本地部署或生产工作流里是否稳定可复现，而不是只看宣传指标。值得关注的是，评论里出现了具体限制、迁移顾虑和实践经验：Its about 80% as good as Qwen 3.6 at 4bit. Really you want to run Qwen at 6bit on a 32gb GPU for actually decent local c；I've been running Qwen3.6 35b-a3b 5bit, which hasn't been that bad so far, simple coding tasks are one shot, others I te。这些反馈能帮助判断相关产品或模型变化是否具备落地价值。

**高赞/高信号评论：**
1. u/TheAussieWatchGuy（赞数：4）：Its about 80% as good as Qwen 3.6 at 4bit. Really you want to run Qwen at 6bit on a 32gb GPU for actually decent local coding that doesn't break the bank. Set expectations low. Single tasks at a time. It works well enough.。立场说明：这类经验有助于判断该变化是否能进入生产流程，而不只是停留在演示或营销层面。
2. u/shaumux（赞数：2）：I've been running Qwen3.6 35b-a3b 5bit, which hasn't been that bad so far, simple coding tasks are one shot, others I tell it to review it's work and consult the official docs and the results are pretty good, 6bit doesn't run on my 12gb card unfortunately。立场说明：评论提供了反方或限制条件，可防止把单个案例过度外推成普遍结论。
3. u/rrrrex（赞数：2）：Qwen 35B Q5, 40 layers on GPU, 28 on CPU, 60-100k context works fine If you really want 27B, choose Qwen 27B Thinkingcap mod, IQ3_K_XS works fine with KV Q8 32k context. It's much better that Bonsai and still fits in vram。立场说明：这条评论的价值在于把讨论从标题判断拉回到实际约束，提醒读者关注可验证的使用边界。

原帖链接：https://www.reddit.com/r/LLM/comments/1vbn58d/bonsai_27b_39_gb_is_it_any_good_for_coding_or/
