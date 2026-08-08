
r/LLM 今日热帖（已按实抓到的 old.reddit 候选筛选）

## 1. I don't think Anthropic and OpenAI will survive
**摘要：** 这帖不是单纯唱衰某家公司，而是在讨论一个更现实的分水岭：当模型能力差距逐渐缩小时，真正决定产品成败的可能是 harness、默认工作流、接入门槛和单位任务成本。楼主用 DeepSeek-v4-flash 的低成本实测，质疑闭源大厂还能否仅靠“最强模型”维持溢价。值得关注的是，它把讨论从榜单拉回到 agent 生产环境里最关键的指标：能不能便宜、稳定、可接入地跑完整任务链。

**高赞评论：**
1. **u/FatefulDonkey（32赞）**：他认为决定性因素是 harness 和易用性，而不是单纯模型本体；**立场说明：** 这条把争论从“谁最聪明”拉回“谁更好用”，很贴近真实落地。
2. **u/anykeyh（16赞）**：他指出用 OpenRouter 再配 Hermes 这类 agent 工具，十分钟就能接上便宜模型；**立场说明：** 这是典型的工程视角，强调接入成本而不是情绪化站队。
3. **u/TonyPace（4赞）**：他分享自己从 Windows 换到 CachyOS，并说很多兼容问题可以靠 AI 修掉；**立场说明：** 虽然偏个人经验，但它侧面说明“可用性”正在吞掉过去被视为门槛的迁移成本。

原帖链接：https://www.reddit.com/r/LLM/comments/1vcp33f/i_dont_think_anthropic_and_openai_will_survive/

---

## 2. DeepSeek V4 Flash makes agent workflows look much more realistic
**摘要：** 这帖核心不是“哪家模型更强”，而是“哪家模型能让 agent 工作流真正算得过来”。楼主强调 DeepSeek V4 Flash 的成本/性能比，让多轮重试、工具调用、验证和长链路执行不再显得奢侈，这对自动化 agent 尤其关键。帖子值得看在它把注意力从单次 benchmark 转向任务级成本：如果每一轮都更便宜，系统就能容忍更多校验、更多回退和更长上下文，从而更接近可部署的生产方案。

**高赞评论：**
1. **u/Eden1506（5赞）**：他怀疑图表里 Qwen 3.6 35b 的成本和智能指数都有异常；**立场说明：** 这条抓住了数据表可信度问题，提醒大家别被漂亮图误导。
2. **u/crusaderky（3赞）**：他指出这些是 datacenter 成本，很多模型的标价未必适用于所有场景；**立场说明：** 很实用，说明“价格”本身就有上下文依赖。
3. **u/0x7Lee（1赞）**：他提到图表可能混了 reasoning / non-reasoning 配置，导致某些行被选错；**立场说明：** 虽然赞数不高，但它直接指向数据来源和评估方法，属于高信号工程提醒。

原帖链接：https://www.reddit.com/r/LLM/comments/1vcqrjo/deepseek_v4_flash_makes_agent_workflows_look_much_more_realistic/

---

## 3. The 3 biggest problems with closed source LLM-as-a-service
**摘要：** 这帖聚焦闭源 LLM 服务最让工程团队头疼的三个问题：每个任务到底会吃多少 token 很难预测、模型内部策略会悄悄变化、以及用户难以获得稳定可验证的行为保证。楼主把问题描述得很像生产环境的真实痛点：同一个任务，有时很快结束，有时会反复和 shell 转义、工具调用、规划分支纠缠很久，成本和结果都不透明。这个讨论值得关注，因为它直接关系到企业是否能把 LLM 真正当成基础设施，而不是一次性实验品。

**高赞评论：**
1. **u/omeriko9（1赞）**：他认可 token 成本预测和内部变化是大问题，但对“保证”这一点提出异议；**立场说明：** 这是典型的边界讨论，能帮助分清“技术不确定性”和“产品承诺”。
2. **u/Bureaucromancer（1赞）**：他指出这些问题和雇人做事的难题很像；**立场说明：** 这条把 LLM 服务和现实协作成本类比，强调不可控性本来就是服务的一部分。
3. **u/Bureaucromancer（1赞）**：他进一步强调不确定性是 LLM 的本性，不一定只是厂商作恶；**立场说明：** 这是一种更成熟的工程判断：问题不只在供应商，也在任务本身的随机性。

原帖链接：https://www.reddit.com/r/LLM/comments/1vdwjqz/the_3_biggest_problems_with_closed_source/

---
