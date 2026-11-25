
**AI Builders Digest — 2026年11月26日**

今日信息流新鲜度：1 天（feed 生成于 11-25）。16 位 builder、34 条推文、1 期播客。主线非常集中：**Agent 的"外壳"（harness）正在成为主战场**，同时英伟达 Jensen 回归引发的算力地缘震荡占满了播客与评论区。

---

## 一、Agent 工具链 / 自研引擎（今日最值得看）

**Anthropic Claude Code 负责人 Boris Cherny：MCP server 现在可以自带 skill**
原话："MCP servers can now ship with their own skills, so Claude Code knows how to use them out of the box."
这是本周对 Agent 工具链影响最大的单条改动（5100+ 赞）。过去 MCP 只解决"能连上什么"，模型还得自己摸索怎么用；现在 server 可以把使用说明和最佳实践一起打包发过来，等于把"接口协议"升级成"接口 + 说明书 + 用法"。对自研引擎的启示很直接：如果你在做工具接入层，MCP server 应该被当成一个可交付的产品单元来设计，而不是一串 endpoint。
👉 https://x.com/bcherny/status/2125292098165612585

**Vercel CEO Guillermo Rauch：CLI 只是 libfx 的薄壳，目标是"最小最聪明的 coding agent 内核"**
原话："The goal is to produce the smallest and most intelligent coding agent kernel, that's embeddable on any surface: browsers, servers, mobile, desktop, OS, ADEs…"
为什么重要：这是对"coding agent 到底该做成 IDE、CLI 还是平台"的一个明确回答——内核要小到可以嵌进任何表面（浏览器、服务器、手机、桌面、操作系统、各类 ADE）。这跟我们讨论自研引擎时的判断一致：竞争点不在外壳功能堆叠，而在内核的可嵌入性和可组合性。
👉 https://x.com/rauchg/status/2125320020666565096

**Peter Yang 实测 Gemini 4 Neon + Antigravity：一次跑到 42 个 agent**
他的三条心得：① Orchestrator 和 `/swarm` 在"多 agent 规划 + 并行构建"上很有用，他一度同时跑 42 个 agent；② `/grill-me` 是个内置 skill，先让模型反过来追问、把方案榨清楚再动手；③ 远程控制比 Claude Code 好，因为每个 thread 默认就是 active 的，可以直接把 Antigravity 加到手机主屏当常驻入口。
为什么重要：这是目前少见的、带具体数字的多 agent 实战反馈。"先让 agent 反问"（/grill-me）和多 agent 默认并行（thread 全 active）这两个设计选择，很可能被其他 harness 抄走。
👉 https://x.com/petergyang/status/2125246815884984398

**Swyx 整理的 agent 基础设施清单（转述 John 的观点）**
原话要点：local-cloud envs & sandboxes / session vs conversation store / user approval inbox / stream listeners / artifacts for everyone / 各种 dashboard 配置。
为什么重要：这六项基本就是"自研 agent 平台"最容易漏掉的六块地基。尤其是 "session vs conversation store"（会话状态和对话记录不是一回事）和 "user approval inbox"（审批队列要成为一等公民），很多人做到第三个月才发现架构里没地方放。
👉 https://x.com/swyx/status/2125431392226148670

**Replit CEO Amjad Masad：token 需求是阶跃函数，每一代 harness 解锁一个数量级的消耗**
原话："auto-complete -> chat -> agent -> long-running autonomous agents -> swarms. Each harness innovation unlocks an order of magnitude more potential token consumption. But then there's a lag between these new tools and users figuring out what to do with them."
为什么重要：这是对"算力需求会不会见顶"的一个结构性回答——不是用户变多，而是同一个用户被允许消耗的算力在阶跃上升。他同时指出存在"工具已就绪、用户还没学会怎么用"的滞后期，这正好解释了为什么很多团队买了 agent 却看不到产出。
👉 https://x.com/amasad/status/2125287538911072753

---

## 二、模型与产品动态

**OpenAI Codex 团队 Thibault Sottiaux：ChatGPT Business 送 banked reset + 免费 fast mode 到 12 月 31 日**
原话："We have two small things for you, a banked reset and fast mode at no extra charge through Dec 31."
纯商业动作，但对重度用 Codex 的团队是实实在在的额度利好。
👉 https://x.com/thsottiaux/status/2125299248782778588

**Amjad Masad：3B 参数的本地版 Muse**
只有一句 "3B local Muse 🤯"，没有更多细节。但方向明确——把能跑在本地的小模型塞进产品链路，这跟他前面说的"harness 创新带动算力消耗"是一套逻辑的两面：边缘侧用小模型，云端侧调大模型。
👉 https://x.com/amasad/status/2125414100692041797

**OpenClaw 作者 Peter Steinberger：一年复盘**
原话要点：OC 在 prosumer 和企业侧找到了位置，多人协作（multiplayer team）功能是同级别里最好的；"shipping reliable and free open source is also really really hard"，每天醒来面对一堆用户抱怨是情绪上的挑战；这一年主要在做无聊的部分——快、稳、安全，功能上除了新的记忆系统和即将到来的 OpenClaw ID 之外没什么大动作。
为什么值得看：这是一份少见的、承认"免费开源 agent 产品有多难"的自述。记忆系统和身份（OpenClaw ID）被点名为下一阶段重点，值得关注。
👉 https://x.com/steipete/status/2125422797304549672

---

## 三、行业判断与讨论

**Box CEO Aaron Levie：同一家公司内部会出现 10 倍产出差**
原话核心："AI is starting to look quite different. Even within the same company you can have a 10X delta between the lowest and highest adopters."
他的论证很扎实：以往技术采纳是"公司级"的（这家公司上云了 / 数字化了），所以内部各团队提升大致均等；AI 不一样，差距出现在团队之间，取决于有没有真的重新设计流程去塞 agent。目前集中在编码，但更多工作会变成"编码相邻"，所以这个效应会外溢。
为什么重要：这解释了为什么"全公司统一采购 AI 工具"往往没效果——采购不等于流程重构。
👉 https://x.com/levie/status/2125442246543814686

**YC 总裁 Garry Tan：AI 放缓的两个原因**
① 模型能力已经超出部分客户的实际需求，但他认为"agency 和 taste 上还有阶跃空间"；② 社会吸收技术的能力到了极限——"people don't like their cheese moved"。
这是对"为什么模型越来越强、企业落地却没加速"的一个偏保守的解释，和 Levie 的"团队间 10 倍差"可以对照着看。
👉 https://x.com/garrytan/status/2125247943540142577
👉 https://x.com/garrytan/status/2125247972158193792

**Meta AI 高级总监 Madhu Guru：信心和正确率几乎不相关**
他借 Jensen 事件的各方预测开火："some flip-flopped on their predictions within days - each time with the same confidence!"，并指出信息生态"asymmetrically rewards certainty, speed and brashness"，而"我不知道，看看会怎么发展"根本拿不到流量。结论是"take everything with a sack of salt"，并借机给那些"一贯大声且一贯错"的人做了次校准。
为什么值得看：这是对 AI 圈评论质量的一次直接批评，也是对读 digest 这件事本身的提醒。
👉 https://x.com/realmadhuguru/status/2125355549202194801

**FPV Ventures 合伙人 Nikunj Kothari：2026 年 pitch 的八种宇宙观**
"App companies: He who owns the workflow controls the universe. / Harness companies: He who puts the intelligence to work controls the universe. / Inference: He who serves... / Model: He who builds... / Data: He who feeds... / Infra: He who keeps it running... / Chip: He who controls the sand... / Energy: He who controls the electrons..."
一条高密度吐槽，但"harness companies"被单独列为一类，说明在一线 VC 的分类体系里，harness 已经和模型、推理平级了。
👉 https://x.com/nikunj/status/2125376105024758112

**Matt Turck（FirstMark VC）转发的一句讽刺**
"'Look at Anthropic below IPO price, they've been at it for almost SIX years now and they are BARELY a trillion dollar company'"
值得记一笔的是语气：泡沫叙事已经开始用"六年才勉强万亿"这种句式来调侃了。这不是分析，但是情绪指标。
👉 https://x.com/mattturck/status/2125275072802029631

**Zara Zhang：定位清晰度和解释字数成反比**
"The clarity of a product's positioning is inversely proportional to the number of words it takes to explain what it is in plain language." 一句话的产品原则，对写 agent 产品官网和 README 都适用。
👉 https://x.com/zarazhangrui/status/2125256097925865639

---

## 四、播客｜Unsupervised Learning Ep 98：中国专家谈 Jensen 回归

嘉宾是 ChinaTalk 的 Jordan Schneider，主持人 Jacob Efron（Redpoint 投资人）。整期是一次"急诊式"录制，48K 字转录，核心不是八卦而是**算力管制的实际后果**。

**事件链条**：Jensen 先被赶下台，又在几天内回归。Jordan 的判断是：董事会敢这么做，唯一前提是 Trump 承诺了"和解 + 赦免"的组合，罚款 2500 万美元了事。真正的罪名不是那桩私生活丑闻，而是**对芯片走私的长期睁眼瞎**——Super Micro 的高管用吹风机把服务器机架的标签吹掉以便运进中国；Mega Speed 与阿里旗下某个专做军事研究的部门有合作。Jordan 的类比是银行业对朝鲜、伊朗资金流的态度转变：先是"这生意不错，无所谓"，直到财政部开出几十亿罚单才认真起来。而英伟达做的是反过来的事——"如果规则说不能卖 100，那就造一个卖 99 的芯片"。

**刚刚落地的新规**（上周五）：132 页，两块内容。一是先进芯片在台积电流片需商务部批准（堵走私）；二是"远程访问"条款，要求马来西亚等地服务中国客户的 neocloud 在 90 天后停止。Jordan 给的关键数字：**中国生态约五分之二的算力来自马来西亚数据中心和远程访问**。

**中方的反应**：主要是梗图（宫廷剧风格，因为"后宫"在中国历史里是常规叙事）。有一篇 VC 文章短暂刷屏后被删，称之为"中国 AI 生态最黑暗的时刻"——芯片少、钱少、股价较高点跌了不少，最好的拿芯片路径就是这条马来西亚通道，而这正是 Jensen 在帮忙维持的。

**他对"这是普通技术"论的反驳**：Mythos 之后，前沿模型已经是可以"hack the planet"的工具，过去九个月里 AI 驱动的网络攻击已经反复出现。所以"这是普通技术、不必在意相对进度"的论证已经失效。至于"反正他们迟早能拿到芯片"——他认为方向搞错了：**华为的瓶颈不是需求而是供给**，卡在 HBM 和半导体设备（EUV、刻蚀、沉积）上，这属于另一套管制。"只要西方保持 10-15 倍算力优势，联合设计那点收益就是四舍五入的误差。"

**两个前瞻判断**（我认为这是全期最有价值的部分）：
1. **中国对机器人数据出口管制，他给 75% 概率**。逻辑是：中国政府对具备强网络能力的模型已经从开放权重转向闭源权重，并且已经出台第一版 AI 出口管制、建立了模型出海许可制度。如果你的业务依赖从中国采集机器人/生物数据，这个风险要提前定价。
2. **下一次"急诊播客"可能是什么**：一是"中国版 Hugging Face 时刻"——中国出现类似事件后政府收紧，进而冲击全球开源；二是美国的网络大灾难。

**关于机器人，他现场吐槽得很直接**：在奥斯汀 CORAL 会议上，DeepMind 花了数百亿美元的机器人"勉强能拿起一个松饼"，而所有人还在惊叹"它拿起松饼了"。他的判断是：解模型只占 20%，剩下全是制造和材料，而"我没法面不改色地告诉你美国造机器人会比中国强"——问一圈展台，磁铁"只有一个地方能买到"，占全球 99.5%。

**更长的那条线**：AI 的政治 backlash。他引的那个数字值得记住——**只有 2% 的美国人希望 AI 发展得更快**。他的推演是：未来两年还行，但到 2029 年两党候选人都会开始说"我们得慢一点"，而"钱解决不了这个问题"（德州砸了 5 亿美元仍然输掉）。

👉 https://www.youtube.com/watch?v=gkd5eOQGASU

---

**一句话收束**：今天最该带走的不是 Jensen 的官司，而是两个数字——**harness 每次创新带来一个数量级的 token 消耗**，以及**中国生态五分之二的算力走的是远程访问通道**。前者决定你自研引擎的天花板在哪，后者决定这条通道关掉之后行业的算力账要怎么重算。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
