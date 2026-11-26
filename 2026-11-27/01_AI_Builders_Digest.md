
# AI Builders 日报 · 2026-11-27

> 数据源：21 位 builder / 42 条推文 + 1 期播客（feed 生成于 11-26，内容为近 24 小时）。

---

## 一、Agent 工具链 / Coding Agent（今日主线）

**Thariq 从 Anthropic 跳去 OpenAI**（@trq212，原 Claude Code）
他本人宣布："I've joined OpenAI!"，措辞很克制但信息量足——"I felt that I could personally contribute the most to this effort at OpenAI"，并点名将与 @_catwu、@thsottiaux、@jxnlco 等人共事。这条 25,330 赞、2,000 条回复，是今天讨论量最大的单条。
为什么值得看：Claude Code 的核心产品人流向 Codex 阵营，是 coding agent 竞争从"模型能力"转向"产品手感"的一个明确信号。评论区基本在吵"是 Anthropic 留不住人还是 OpenAI 开价高"。
https://x.com/trq212/status/2125675533761671405

**Guillermo Rauch：workflows 又快 10 倍，直接冲着 harness 延迟去的**（@rauchg，Vercel CEO）
原话："For harness durability (@eve, libfx, pi, opencode…), this is a big deal, as it crushes latency in between turns. Upgrade to workflow@latest. No code changes." 另一条里他说得更狠：随着模型变强，"permissions, code diffs, commands, tool calls… The harness itself blurs away"，而整个 fx 仍然只有 6MB——subagents、MCP、skills、sessions、durability、ACP、TUI、网络传输全塞进去。
为什么值得看：这是"harness 会变薄、但中间层延迟变成核心指标"的直接表达。如果你在做自研引擎，turn 之间的空转才是用户感知的卡顿来源，不是模型首 token。
https://x.com/rauchg/status/2125685667833520237
https://x.com/rauchg/status/2125650675665432995

**Rauch 还顺手演示了一把多模型分工**：用 fx 让 Gemini Neon 规划、DeepSeek 干重活，一把做出 `lsx`（终端里的 Finder，走 Kitty graphics protocol，能内联渲染任何东西）。他的评价很实在："DS actually did all the heavy lifting. This was very cheap! I just told it to use DS 1017 fast subagents."
https://x.com/rauchg/status/2125482861033824410

**Karpathy 用 Claude Code 撸了一个"美国文明"地图**（@karpathy）
他让 Opus 5.5 抓了 31 个公开数据源（Census、BEA、BLS、EIA、NOAA、USGS、DoD、FEMA…），压到一张 25km 六边形网格上，转成《文明》的语言：GDP 是金币产出，圣何塞的城区是 Campus（1/4 劳动者是工程师/程序员/科学家，全国是 1/14），底特律是 Motor city，国家公园按游客数当奇观。代价是 **7 小时、45,000 行代码**，"Opus 5.5 on medium and turning on ultracode"，最后他只剩一半周额度。
为什么值得看：这是目前公开可见的、单次 agentic coding 时长和产出的一个上限样本——不是 demo，是 45K 行能跑的东西。他自己也说"我其实不太知道自己在干嘛，但很好玩"。
https://x.com/karpathy/status/2125779541952246039

**Madhu Guru：coding 速度上去了，出货没变，因为周边系统是旧的**（@realmadhuguru，Meta AI Sr Director）
原话："coding velocity is way up thanks to AI, while actual shipped products and business impact are unchanged in most companies. That's cos the surrounding system of experimentation tooling, evaluation, launch processes, and gtm are outdated." 他给的比喻很传神：**"It's like sticking a Ferrari engine in a sedan and racing it on Indian roads."** 建议是"map out your product lifecycle and rebuild it ground up"。
为什么值得看：这是对"Agent 提效"最常见的误判的纠正——瓶颈从写代码移到了 eval、发布流程和验证环节，这正好是工具链该补的位置。
https://x.com/realmadhuguru/status/2125630707640783322

**Swyx：别信"每任务成本"的帕累托前沿图**（@swyx）
原话引用："Cost per task is a misleading metric; the scarce resource is human attention, not token cost." 他自己补刀："beware the pareto frontier charts that make you believe you can reduce every model to 2 numbers; it can hide some AWFUL reliability issues"。159 条回复，说明戳到痛处了。
为什么值得看：选模型/选 harness 时用两个数字做决策，代价通常落在长尾的可靠性事故上。
https://x.com/swyx/status/2125627281230205435

**Aaron Levie：coding 是知识工作的预览片**（@levie，Box CEO）
三段论讲得很清楚：先是从"自己动手做研究、打字、创造价值"变成"协调 agent 干活"；再往后，"we will be giving agents goals to optimize against and they'll go off on and increasingly solve larger problems"。他同时指出最大障碍："much of this work remains non-verifiable, so humans will be even more in the loop than they are in coding." 结论是"pay attention to coding and you'll get a sense for where work is going"。
https://x.com/levie/status/2125837181398950233

**Nan Yu 一句话怼"chat 不是 AI 的正确界面"**（@thenanyu，Codex @ OpenAI）
原话："Whenever someone says 'chat isn't the right interface for AI' I know they're gonna follow it up with a bunch of hand-waving." 191 赞。
为什么值得看：这句话在 agent/产品圈被反复引用，本质是在要求批评者拿出可验证的替代方案，而不是姿态。
https://x.com/thenanyu/status/2125718932741120476

**Peter Steinberger：Google 做了 MCP，然后开始收费卡 CLI**（@steipete，OpenClaw + OpenAI）
原话："huh, so Google finally built an MCP and is now forbidding clis like gog unless you pay them more? classy" 1,023 赞。
https://x.com/steipete/status/2125654555262431248

**Zara Zhang：32k star 的 skill 还在涨，但她自己都意外**（@zarazhangrui）
"my Frontend Slides skill has kept growing (now at 32k stars) organically even though I haven't talked about it for months. I thought the growing capabilities of the coding agents would make the skill obsolete. Why are people still using it??" 另一条自省更值得记："I made many tools for myself but I ended up using most of them for just a couple weeks and then stopped... Making high-retention software is a difficult craft."
为什么值得看：模型变强并没有消灭 skill 层，反而暴露了"生成质量稳定"和"人的留存习惯"是两件事。
https://x.com/zarazhangrui/status/2125649866902868355

---

## 二、模型与基础设施

**OpenAI 承认 GPT-6.2 上线计费算错了，额度会消耗得更快**（@thsottiaux，Codex & ChatGPT @ OpenAI）
原话要点：上线时错误地给大多数用户打了折，现已修正，"you will reach your limits 40% faster on GPT-6.2 Astra and 25% faster on Sol"，历史差额不追缴，作为补偿"we'll be adding one banked reset for everyone on Go, Plus, Pro, and Business"。3,652 条回复，情绪可想而知。
为什么值得看：直接影响每天用 Codex/Astra 的人的实际可用时长，且是官方口径的"变贵"。
https://x.com/thsottiaux/status/2125784147889393806

**Sam Altman：OpenAI 在测 Private Inference**（@sama）
"testing Private Inference, our latest offering as part of OpenAI Private Intelligence, with a small group of customers"，并说明 ZDR + Private Safety Processing 能让自动安全审查在不让人接触原始内容的前提下跑完。7,997 赞。
为什么值得看：企业侧 agent 落地的真实卡点是合规审查与数据边界，这是官方给出的架构答案。
https://x.com/sama/status/2125638790593274259

**Amjad Masad：大规模软件迁移终于可行，前提是能验证**（@amasad，Replit CEO）
"Large scale software migration is now viable provided you can verify the results. This is exceptionally important given the aging software systems running critical infrastructure."
https://x.com/amasad/status/2125664998454366305

**Claude 官方账号提到 Fable 5.2**（@claudeai），只有一句"What are you exploring with Fable 5.2?"，信息量极低，但值得记一笔版本号。
https://x.com/claudeai/status/2125616074242552180

---

## 三、播客深读：Noam Brown 讲"游戏理论为什么没通向通用智能"

**Training Data · "OpenAI's Noam Brown: Why Game Theory Didn't Lead to General Intelligence"（Live at No Limit Finals）**
https://www.youtube.com/watch?v=tRaFbDFBl_A

这期是今天最有信息密度的一块，几个点值得单独记：

**1. 博弈论的死穴是"假设理性"**
他从 2012 年打扑克起步，一路做到外交（Diplomacy）。结论是反直觉的："the game theory approach doesn't actually work that well in diplomacy"，因为博弈论的前提是"all the other players are rational, that it is common knowledge that all players are rational, and people are not actually rational"。他用最后通牒博弈举例：GTO 解是给对手 1 分钱，但真人一定拒绝。真正做出超人外交 AI 的路是"train on human data... Do not assume rationality, but to just assume that people are gonna behave like people"——**训练一个"人类非理性模型"**。

**2. 他自己承认这是一次信仰崩塌**
"my entire career up until that point had been about game theory... I had to wrestle with the fact that actually that was not the path to general intelligence." 2022 年他带着"reasoning 才是关键"去谈，被回复"再预训练大一点就都解决了"。他反驳的依据很硬：GPT-4 要打好像样的围棋，"it would be about six orders of magnitude"——不现实。

**3. 真正的解锁是 CoT + RL，不是 CoT 本身**
"the key ingredient was... if you do reinforcement learning to train for this behavior, then you actually get much better chain of thought behavior"，随后观察到"the longer the model takes to think before responding, the better it does"。这一步把 test-time compute 变成通用可扩展的东西。

**4. 模型"锯齿化"的具体案例，比抽象说法有用得多**
他每次出新模型都让它写扑克 bot 当评测。5.5/5.6 是第一次感觉"10x、20x 地放大我的能力，但还不能独立完成"。缺的东西很微妙："long term planning and organization. They're not really good at noticing when they're going down the wrong direction and stepping back." 例子：让它实现 CFR，它会花几小时死磕数值精度，而"numerics don't really matter that much"——**典型的局部最优陷阱，不是能力不足**。

**5. 关于 RSI 和"退学"的暴论**
他认为 RSI 不是新概念，"all of human technological progress, it really is just one giant RSI loop"，今天不同的只是"generality"和"speed"。瓶颈仍在算力和模型的长尾短板。他给学生的建议是："if somebody is promising student, the best thing to do is actually to drop out and join the labs now"，并说自己招过几个跳过大学最后一年的人，"do exceptionally well"。

**6. 两个轻松但有信息量的判断**
Astra 已经"able to make money playing online poker"；五年内让单个 AI agent 去打 WSOP 赢过所有人类，他给"20% 概率"，理由是方差和"全下弃牌"式策略可以抹平技术水平。

---

## 四、一条值得单独想的观察

**Peter Yang：AI 产品最难的不是能力，是让人跟上**（@petergyang）
"one of the biggest challenges of AI products is just letting humans keep up with whatever the AI is doing. That ending of Her where the AIs found humans too slow and collectively left us doesn't seem too far from reality."
为什么值得看：和 Rauch 的"harness 变薄、延迟变成核心指标"、Madhu 的"周边流程是瓶颈"是同一个问题的三个面——**人的带宽成了系统里唯一不能扩容的部分**。
https://x.com/petergyang/status/2125750286539272695

---

**今日主线一句话**：coding agent 的竞争焦点正从"模型多强"转向"turn 之间多快、验证多可靠、额度多耐用"——Thariq 的人才流动、Rauch 的 10x workflow、Sottoiaux 的额度缩水、Swyx 的可靠性警告，说的是同一件事。

**已跳过**：Blade Runner 影评、WoW 段位、猫、咖啡店评分、Jensen 八卦、以及若干纯 t.co 无正文推文。
