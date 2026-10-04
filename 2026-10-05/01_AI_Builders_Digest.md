
AI Builders Digest — 2026-10-05

【X / TWITTER】

**OpenAI Codex 负责人 Thibault Sottiaux（thsottiaux）— OpenAI 收敛产品线**
他宣布 Codex/ChatGPT 的策略"锁定"：接下来只做四件事——做减法、提升效率以给更多人更多用量、突破性功能、新模型。原话："Only things being worked on are simplifications, more efficiency for more usage, groundbreaking features or new models... feedback is clear that you all want things to get simpler."（6762 赞）
为什么值得关注：这是 OpenAI 对"功能堆叠招致用户疲惫"的正式回应，意味着 Codex 下一阶段主打简化与配额，而非继续加功能。
https://x.com/thsottiaux/status/2106610099720720811

同一位还实测了自己的 agent：让它批量删除/分类邮箱、给邮件打标签、梳理需要回复的邮件并在后台检索上下文，他称之为第一次达成 inbox zero。这是一个很具体的"agent 替人干脏活"样本。
https://x.com/thsottiaux/status/2106603980386394123

**Box CEO Aaron Levie — agent 采用仍是"双峰分布"，还有 100 倍空间**
他指出：编程及相邻任务已起飞，其余知识工作几乎还没开始。原因是多数工作流需要被重新设计（数据重新接线、问责与合规范式、安全升级），不是简单加个聊天框。"We're still so unbelievably early... you can basically expect 100X more agent adoption from what we've seen so far."（187 赞）
为什么值得关注：给"agent 落地"泼的一盆清醒水——瓶颈在流程重构，不在模型能力。
https://x.com/levie/status/2106583814709633413

**Meta AI 高级总监 Madhu Guru — AI 采用是"产品问题"**
他认为即便在付费用户中，使用深度也很浅，主因是 AI 产品像"有 100 个拉杆的飞机驾驶舱"（连接器、权限、模型选择、token 用量等）。他预判未来 12 个月会显著改观。
为什么值得关注：这正是 自研引擎 / Agent 工具链 的核心命题——把复杂度收进产品内部，别丢给用户。
https://x.com/realmadhuguru/status/2106450089938157720

**Vercel CEO Guillermo Rauch — 安全 = 验证工程 + 算力预算分配**
他的判断：安全会变成软件公司越来越大的职能，"Security is verification engineering（我的代码大概率内存安全），as well as capital allocation（我该把最多 token 投向哪个攻击面）"。同时他给出一个高传播度的观点——"AI will make everything free, including itself"（3229 赞）。
为什么值得关注：用 token 预算来理解安全投入，是把 agent 时代工程经济学说清楚的一个框架。
https://x.com/rauchg/status/2106516538836856945

**OpenAI 的 Sam Altman — 反对把 AI 当宗教**
"我对于人们试图赋予 AI 模型宗教性的力量、或交出自己的判断力，感到非常不安，我认为这是一个真实的安全问题。"（24293 赞）
为什么值得关注：这是当前关于"AI 崇拜 / 过度信任模型"争议里最高声量的表态，也映射了舆论对 AI 依赖的警惕。
https://x.com/sama/status/2106388373221118198

**OpenClaw / OpenAI 的 Peter Steinberger — 自家 Android app 卡在 Google 审核一周多**
"We're now over a week in review limbo for OpenClaw's Android app."（6315 赞），并半开玩笑地说"我们都在造同一个东西"。
为什么值得关注：Agent 工具链的瓶颈经常是应用商店这类非技术环节，不只是模型。
https://x.com/steipete/status/2106446147791597774

**Replit CEO Amjad Masad** — 发布 "Replit Drift"，并预告与 OpenRouter 的 Alex Atallah 做了一期"很深入、偏技术"的对谈。
https://x.com/amasad/status/2106406812316827874

**Cursor 设计师 Ryo Lu（ryolu_）— 一篇关于"趋同到均值"的长文**
他认为当所有人看别人做什么来决定自己做什么时，产物会变得"精致但没有生命"；AI 让这个循环变得无摩擦，"a tidal wave of mid"（一片平庸的浪潮）。他的呼吁是把做软件当艺术做——带有个人视角。1776 赞，属于本期最有讨论度的观点文。
https://x.com/ryolu_/status/2106337039201505453

**SPC 合伙人、Dropbox 前 CTO Aditya Agarwal — "智能便宜到不用计量"**
他认为 AI 真正颠覆之处是：既民主化了顶级医生/律师这类资源的"访问权"，又把每个人的可用时间变成无限。
https://x.com/adityaag/status/2106503075209044336

（另有 Zara Zhang 抛出开放式问题"How will the world change if coding agents get 10x better?"：https://x.com/zarazhangrui/status/2106405482852434359）

【OFFICIAL BLOGS】

**Claude Blog：Claude Cowork 与 chat 合并为一个 Claude**
核心公告：Cowork（大任务）与聊天、Design 不再分区，Claude 自动判断任务需要什么；同时上线 Claude Docs 和 Claude Slides（beta），可在对话里直接写文档、生成幻灯片并导出 PPT/PDF。原话："People used both, and told us the frustrating part was deciding where a task belonged... So we stopped making you choose."
为什么值得关注：这是"agent 平台不再让用户选入口"的产品信号——入口收敛、由模型自己路由，正是 Agent 工具链的一个方向。付费版未来数周在 Pro/Max 先灰度。
https://claude.com/blog/cowork-is-now-claude

【PODCASTS】

**The MAD Podcast — "Who Feeds the GPUs? Inside AI's Hidden $30B Layer"，嘉宾 Renen Hallak（VAST Data 创始人兼 CEO）**

一句话结论：喂饱 GPU 的存储/数据基础设施层，正在成为 AI 里最赚钱、最少人注意的一层，而它的下一步是"模型管理"和"机密计算"。

VAST 估值 300 亿美元，客户包括 xAI 及多家大型 AI 云，但名字并不出圈——因为它站在"NVIDIA 五层蛋糕"的最中间（软件基础设施）。Hallak 说旧架构是"shared nothing"分片，节点超过约 100 个就因通信平方级增长而崩溃；AI 需要的是百万级节点、单集群数 EB、数十 TB/s 吞吐，于是他们把 SSD 放到网络另一侧，做"shared everything"。

两个最值得记的点：
1) 需求侧离谱到让他害怕。有客户原本说三年要 500PB，一周后回来说再追加 2EB："I think in the next ten years, we'll see more difference than we did in the last thousand years."他认为这个增速至少还能持续 5–10 年，瓶颈是物理的——土地、电力、芯片。
2) 新发布聚焦"模型管理 + 机密计算（data enclave）"：让企业模型推理跑在企业自己的机房，模型权重全程加密端到端（借助 NVIDIA 加密内存），两边都不暴露——企业数据不出门，模型厂权重不被偷。他判断 AI 云之所以能压制超级云厂商，是典型的"创新者窘境"：新栈的人天天在实战中学，守着老现金牛的人学不到。

他还有一个值得琢磨的判断：软件基础设施层会像过去云/PC/移动时代一样沉淀大量价值，而"模型层"是历史上第一次出现，地位最难预测，未来很可能与应用层重新合并。
https://www.youtube.com/watch?v=awoR908Yu5Y

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
