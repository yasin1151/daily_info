
**AI Builders Digest — 2026年6月9日**

---

## X / TWITTER

**Anthropic Claude Code 团队成员 Boris Cherny**

Boris Cherny 分享了让 Opus 模型长时间自主运行的5个实用技巧：开启 auto mode 跳过权限确认、使用 dynamic workflows 协调成百上千个 agent 协同工作、通过 /goal 或 /loop 指令推动 Claude 持续执行直到任务完成、在云端运行 Claude Code 以便关闭笔记本电脑、以及确保 Claude 有端到端自我验证的手段（Chrome 浏览器扩展、iOS/Android 模拟器 MCP、启动完整后端服务等）。他指出多个 benchmark 显示 Opus 是长时间运行任务的最佳模型。

https://x.com/bcherny/status/2063792263067754658

---

**OpenAI Codex 与 ChatGPT 团队成员 Thibault Sottiaux**

Thibault Sottiaux 宣布了一项为期100天的 Codex 推广计划：每天选出1位用 Codex 做出了令人印象深刻或极具实用价值成果的用户，给其一个月的10倍用量上限，看他们能在此基础上做出什么。他形容这是他为 Codex 准备的一个"新的大按钮"，首批入选者明天公布。

https://x.com/thsottiaux/status/2063748242681307611

---

**Google 前产品负责人（Gemini、Veo、Nano Banana）Madhu Guru**

Madhu Guru 指出了一个普遍误解：很多人以为训练数据是低技能的苦力活，实际上推动模型前沿进步所需的数据恰恰相反。各大实验室急需的是高经济价值任务的训练数据，而这些任务在软件工程之外的领域几乎没有现成文档，涉及多年积累的复杂领域知识，横跨各种老旧工具。这也解释了为什么我们现在有 SWE agent 却没有知识工作 agent。像 Mercor 这样专门为这些高价值任务创建训练数据的公司，做的其实是极高杠杆的工作。

https://x.com/realmadhuguru/status/2063704354910347520

---

**Vercel CEO Guillermo Rauch**

Vercel AI Gateway 每月平均恢复超过 1 万亿 tokens，类似 Stripe 通过智能重试挽回失败的支付或过期的信用卡。该服务以零加价提供，在模型之上叠加了冗余机制、零数据保留强制策略、可观测性、用量 API 和额度上限控制，帮助开发者降低模型调用损耗。

https://x.com/rauchg/status/2063714700618334260

---

**Box CEO Aaron Levie**

Levie 连续输出三条深度洞察。第一，未来一两年 AI 用例必然会在模型家族之间分层：frontier 模型聚焦高端任务，更便宜的模型覆盖大批量工作负载。能够高效将 workload 路由到合适模型的 agent 编排层将变得极具价值——"能在保证任务成功的同时优化成本，这样的编排层将占据制高点"。第二，市场对 AI 吞噬企业软件存在误判。过去构建优秀软件本就很难，AI 虽略微降低了难度，但做出有品味、差异化、高质量且安全的产品依然不简单。更关键的是，企业软件公司绝大部分成本花在 GTM 上——规模化进入企业软件品类需要大量咨询式销售和实施支持，AI coding 工具对此几乎无能为力。第三，Box 已在 Web 端推出 Markdown 编辑器，支持完整 CLI 操作、评论和版本历史。Box Drive 可将云端文件挂载为本地驱动器，用户可在 Claude Cowork、Codex、Obsidian、Cursor 等任意应用中直接操作所有文件。

https://x.com/levie/status/2063835799096090749
https://x.com/levie/status/2063756386572681606
https://x.com/levie/status/2063649508681224367

---

**Y Combinator President & CEO Garry Tan**

Garry Tan 指出，教育人们如何使用 AI 工具已成为一个严重瓶颈，这也是 YC 创建 AI 教育平台的原因。此外，他的个人工具 GBrain v0.42.30 已支持生成关于用户思维方式如何随时间变化的详细总结，帮助追踪思维演变轨迹。

https://x.com/garrytan/status/2063786111588323780
https://x.com/garrytan/status/2063785286367392095

---

**Builder Zara Zhang（哈佛 2017）**

她的 Frontend Slides 技能之所以实现有机快速增长，核心原因是幻灯片天然具有社交属性——人们看到酷炫的 HTML 演示文稿后总会追问"你怎么做的"，使用 HTML 幻灯片的人往往被同行视为更 AI-native 和 AI-savvy，形成自然的口碑传播。

https://x.com/zarazhangrui/status/2063638307586662539

---

**FPV Ventures 合伙人 Nikunj Kothari**

从"tokenmaxxing"到"tokenoptimizing"的转变只用了短短几周。Nikunj 认为企业仍应给员工充足的 token 预算，让他们保持在技术前沿、探索各种边缘用例——否则人天然会退回"以前怎么做就一直怎么做"的惯性里。在控制成本和鼓励探索之间，过度收紧 token 反而会扼杀组织内部的 AI 实验精神。

https://x.com/nikunj/status/2063630238123483195

---

**OpenClaw + OpenAI 构建者 Peter Steinberger**

这条推文直接炸了——1.3 万赞、近 900 转推。Peter 说：不要再手动 prompt 你的 coding agent 了，你应该设计一个 loop 来自动 prompt 它们。从"人 → agent"的单次交互，升级为"人设计 loop → loop 驱动 agent"的自动化范式，这才是 agent 工具的正确打开方式。

https://x.com/steipete/status/2063697162748260627

---

**South Park Commons 合伙人 Aditya Agarwal（前 Facebook 早期工程师 / Dropbox CTO）**

经历过 Meta 和 Dropbox 两次 IPO 之后，Aditya 的观察是：巨额财富不会凭空创造新欲望，而是放大内心已有的渴望。对很多人来说，这意味着可以做更疯狂、更出格的事——开新项目、投新公司、让硅谷的"疯狂循环"持续运转。未来几个月大量科技人将获得流动性，这对整个生态是巨大利好。

https://x.com/adityaag/status/2063731771284619521

---

**OpenAI CEO Sam Altman**

Sam 转发 Thibault Sottiaux 的 Codex 10X 使用量计划公告，只写了一句话："interesting recursive loop here maybe"（这可能是个有趣的递归循环）。前有 Peter 说 loop 驱动 agent，后有 Sam 把创业者用 AI 工具加速编程、再用编程成果扩大 AI 使用的飞轮也视为一种 recursive loop——"loop"成了本周 AI 圈最核心的隐喻。

https://x.com/sama/status/2063779477419901071

---

## OFFICIAL BLOGS

**Claude Blog: New in Claude Managed Agents — Dreaming, Outcomes, and Multiagent Orchestration**

Anthropic 为 Claude Managed Agents 发布了三项重大功能更新。首先是 **Dreaming**（梦境模式），这是一个定时后台进程，能回顾 agent 过往的会话记录和记忆存储，提取行为模式并优化记忆库，使 agent 随时间推移持续自我改进。它能发现单个 agent 无法察觉的模式：重复出现的错误、agent 自然收敛的工作流、团队共享的偏好等。官方称：「Dreaming 通过回顾过往会话来扩展记忆，发现模式并帮助 agent 自我改进。」

第二项是 **Outcomes**（结果评分），用户编写评分标准定义成功条件，独立评估 agent 在自己的 context window 中对输出进行打分，agent 会反复自我修正直到满足标准。在 benchmark 测试中，该功能将任务成功率提升了最高 10 个百分点，其中 docx 任务提升 8.4%，pptx 任务提升 10.1%。

第三项是 **Multiagent Orchestration**（多 agent 编排），一个主导 agent 将任务拆解并分派给拥有各自模型、prompt 和工具的专项 agent，子 agent 在共享文件系统上并行工作，所有过程可在 Claude Console 中完整追溯。

实际案例方面：Harvey 的法律文档任务完成率提升约 6 倍；Netflix 平台团队利用该功能并行分析数百个构建的日志；Spiral by Every 使用 Haiku 作为主导 agent 配合 Opus 子 agent 进行写作，以评分标准进行质量把关；Wisedocs 的文档审查速度提升 50%。

https://claude.com/blog/new-in-claude-managed-agents

---

## PODCASTS

**The MAD Podcast with Matt Turck: State of Enterprise AI 2026 — Aaron Levie on Tokenmaxxing, Rise of Headless, and AI-Proofing Your Job**

**核心观点：** 企业 AI 的真正瓶颈不在模型能力，而在于部署速度永远追不上突破速度——我们正处在一个巨大的"能力悬置"时代。

Box CEO Aaron Levie 在与 Firstmark 合伙人 Matt Turck 的对谈中，给出了一个迥异于主流叙事的判断：CIO 们其实相当乐观，远没有进入 Gartner 所谓的"幻灭谷"。编程和 IT 领域的生产力提升是肉眼可见的，市场、销售等业务部门正主动索要 AI 能力——真正卡脖子的是部署人才和组织变革管理，而不是技术本身。

但他真正火力全开的分析在另一个方向：**token 成本已经成为企业 AI 对话中占据三分之一比重的话题。** 企业被账单吓到了，因为 agent 消耗的 token 量远超传统 chat。"这就像我们把本该花十年逐步铺开的算力成本压缩到 12 个月内，然后企业一脸懵地问为什么账单这么高。"

Levie 由此引出关键判断：模型分层将成为定局。前沿模型处理高价值任务，便宜模型做高吞吐量的批量工作，一家公司最终可能同时使用五六种模型。而真正的价值洼地在于那个能把每个 workload 路由到最优模型的 orchestration 层——谁能做到"成本优化但不牺牲任务成功率"，谁就占据了制高点。

关于软件本身，他的观点同样锋利：市场曾经认为 AI 会吃掉企业软件，但事实相反。写代码容易了，卖软件依然难——GTM 成本才是企业软件公司的命门。但他也指出了一个真正的结构性变化：**agent 将比人类更频繁地消费企业软件。** 三年后，完成 AI 转型的企业软件公司都将同时拥有 seat 定价和 consumption 定价两种模式——这就是他所谓的"无头软件"时代。

最反直觉的洞察：**突破速度太快，反而拖慢了落地。** "突破持续以比客户建立标准架构更快的速度到来，而这些突破往往让你刚实施完的东西直接过时。"这就是他所说的"能力悬置"——模型能做的事远多于我们学会如何部署的。知识工作不像代码那样可以验证对错，权限、数据分散、非技术用户的工作流缺失……这些问题的解决可能需要五到十年。

在这场算力尚且被 VC 补贴的窗口期，Levie 的建议直白得惊人："趁现在有些产品还在补贴期，能写多少代码就写多少。"而企业真正该做的，是培养一种叫"内部 FDE"的新角色——他们同时理解 AI 工具和业务流程，负责把 agent 接入具体部门的工作流，并在模型迭代时持续维护。

https://www.youtube.com/watch?v=Gs2styCcwro

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
