
r/LLM 今日热帖

1. If you could fix one thing in today's LLM ecosystem, what would it be?

摘要：这篇热帖在征集社区对当前 LLM 生态最想修复的问题，讨论重点集中在幻觉、输出一致性、后训练基础设施复杂度等实际痛点。它值得关注，因为评论不是单纯抱怨模型“不够聪明”，而是把问题落到可验证性、稳定输出、训练/部署门槛这些会直接影响开发者采用成本和产品可靠性的环节。

高赞评论：
- u/themoroccanship（2 赞）：I successfully made a model say "I don't know" when it does not know instead of bluffing, available in GitHub and Hugging Face. https://tilelli.tech Hopefully by the end of this year, I solve it or at least I will reduce...  
  立场说明：这条评论把“少幻觉”具体化为让模型承认不知道，关注点是可信度和可验证输出，而不是单纯追求回答更长。
- u/thinking_byte（2 赞）：Better consistency and predictability in outputs so the same prompt does not randomly give different quality results.  
  立场说明：这条评论指出 LLM 产品化的核心障碍之一：同一提示下质量随机波动，会直接影响自动化流程和评测稳定性。
- u/EitherPreference5326（2 赞）：The issue I’d fix: post-training is too dependent on heavyweight infra. Serious LLM post-training often means stitching together vLLM, Megatron, DeepSpeed, Ray, custom CUDA kernels, distributed launchers, reward-model se...  
  立场说明：这条评论从后训练基础设施复杂度切入，说明当前生态对普通团队并不友好，真正瓶颈可能在工程栈而不只是模型本身。

原帖：https://www.reddit.com/r/llm/comments/1uou67s/

2. DeepSeek might be the best value-for-money LLM right now

摘要：这篇帖子讨论 DeepSeek 是否是当前性价比最高的 LLM，核心关注点是价格、效果和可靠性之间的取舍。它值得关注，因为社区没有只停留在“便宜”这个单一指标上，而是进一步比较了 Mimo、Claude 等替代模型，并把 honesty benchmark、幻觉率和实际任务效果纳入判断，适合用来观察模型选型中的成本/质量平衡。

高赞评论：
- u/look（2 赞）：Eh, Mimo is the same price, and I find its Pro model more effective for most tasks.  
  立场说明：这条评论提醒性价比不能只看价格，还要看同价位模型在具体任务里的有效性。
- u/themoroccanship（1 赞）：I agree, not only this, it won our own honesty benchmark, we come up with, to see if the model knows what it does not know. Deepseek is the winner, Claude is second.  
  立场说明：这条评论把讨论转向“诚实度”评测，强调模型能否知道自己不知道，这比单纯 benchmark 分数更接近真实使用风险。
- u/themoroccanship（1 赞）：Our benchmark is honesty specialized. What benchmark shows he hallucinate more or less than others ? Every AI hallucinates, that's the truth, we just focused on who does it less and why.  
  立场说明：这条评论补充了评测边界：所有模型都会幻觉，关键是比较谁更少、为什么更少，适合用于模型采购或 API 替换时的风险判断。

原帖：https://www.reddit.com/r/llm/comments/1uonzrp/
