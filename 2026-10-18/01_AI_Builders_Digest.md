
# AI Builders 日报 — 2026-10-18

## 本期主线：Brockman 说安全投入该超过软件投入，以及"常驻 Agent"已经落地

**No Priors｜The Changing Physics of Cybersecurity and Drug Development（嘉宾：OpenAI 联合创始人兼总裁 Greg Brockman）**
https://www.youtube.com/@NoPriorsPodcast

一句话结论：Brockman 认为 AI 已经从"能答题"跨到"能产出新知识"，而这两件事同时把网络安全和药物研发的底层成本结构掀翻了。

三个值得记的点：

**1）数学已经不是演示，是产出了。** 他提到 OpenAI 公布了近 400 个被解决的重量级开放问题，数学界现在在做的事是"从里面找洞见"，而不是验证对错。他的判断标准很有意思——不是"机器给出了一个没人看得懂的证明"，而是"人类拿着这些工具能做到以前不可想象的事"。他还提到用 debate / iterative amplification 这类 2017 年就讨论过的技术，让 AI 的输出对人类可核查（举的例子是图书摘要：你不需要读完书，只需要另一个 AI 指出"这一段关键情节没被覆盖"，你就能判断）。

**2）"防守者窗口"是有期限的。** 原话："我认为网络安全投入应该远远超过软件投入。" 逻辑是——软件正在变成廉价的入场券，真正稀缺的是"可靠、安全、你信得过的软件"。他描述的 OpenAI 内部操作很具体：每次新模型发布，抽 25 名生产工程师停掉手上项目，专职用当前最强的模型去攻击自家基础设施，修完之后再迭代，直到"把这个模型能找到的问题打饱和"，然后等下一个模型再来一遍。另外他们有 10 亿美元承诺给防守方，和 CrowdStrike 这类厂商合作。附带一个被低估的方向：既然模型擅长证明，为什么不用它做软件安全属性的形式化验证。

**3）DOTS 是形态变化，不是能力变化。** 他描述自己的那个常驻 agent："你停止工作，它继续工作。" 它有自己的云电脑，知道他日历冲突、收件箱和 Slack 内容，早上给他一份"你答应过要做但没做的事"清单，而且经常主动发现他没让它看的东西。他的原话是"最好的 UI 是没有 UI"，但也承认企业侧的真正难点在于 admin 控制——功能开关本身就是一种"需要被展示的缺失功能"，没有 UI 时你连怎么告知用户都成问题。

药物研发那段也值得听：他的论证是"生物学对人类是陌生的，但对神经网络没理由比自然语言更难"，所以第一性原理上该能破解"生物学的语言"；现实瓶颈一半是数据，另一半居然是很土的监管文书（写一份临床试验申请要一年）。

---

## Agent / 编码工具链

**Anthropic 的 Boris Cherny：Code Review 是他敢快的原因**
https://x.com/bcherny/status/2111158313463525518
"我无法想象没有 Claude Code Review 怎么保持生产力。它跑在我所有 PR 上，几乎每个 bug 都在上线前被抓住。" 他把这称为团队能一边加速一边提高质量门槛的"秘密配方"（近 3400 赞）。同一天他还推了 Claude Slides，说自己现在做 deck 不再靠 Google 搜 "iphone frame svg"。这条对自研工具链的启示很直接：**review 环节自动化比生成环节自动化更能释放吞吐**。

**Box CEO Aaron Levie：该给 RSI 定价了**
https://x.com/levie/status/2111312141609586862
他列了一个飞轮的四个前提：模型能力已超过多数人类工程师、长跑 agent 的 harness 与 infra 有实质进步、可用数据在变多、以及能把 agent 并行到远超任何个人的任务/测试/方案数量上。结论是"这个飞轮几乎必然让模型进展比我们见过的都快"——"如果你没把 RSI 会带来什么算进价格里，那大概是个错误"。这是本期除播客外最值得读的一条，且直接指向 agent harness 是当前瓶颈所在。

**Every CEO Dan Shipper：瓶颈从生成转移到编辑**
https://x.com/danshipper/status/2111174407637139668
"生成现在既便宜质量又高。我们真正需要的那次能力跃升，是编辑和监督（editing and oversight）。" 一句话点出所有 agent 产品的当前痛点：产出不缺，缺的是让人敢签字的那层把关。

**YC 总裁 Garry Tan：一个 agent 写代码，另一个搭 DevOps**
https://x.com/garrytan/status/2111235500568969451
他开新项目时的组合是 capydotai + AsideAI，"agent 既能写第一版代码，又能顺手把整套 DevOps 搭好"。这是"agent 组队"而非"单个 agent 全能"的一个真实用法样本。

**OpenAI 的 Thibault Sottiaux：ChatGPT Space 上线**
https://x.com/thsottiaux/status/2111249534072529256
他自嘲 Space 的发布"有时尴尬得可爱，因为是真正在做它的团队出镜"。同时 Codex/ChatGPT 前一天加了 slides 支持（Pro / Business / Enterprise 先行）。产品线在往"工作产出物"而不是"对话"收敛。

---

## 模型与产品动向

**Replit CEO Amjad Masad：部署进你自己的云，数据不出门**
https://x.com/amasad/status/2111267314012496121
"你的数据属于你。我们把 Replit 部署到你的云上，数据永不离开。" 明确瞄准政府、金融、医疗这类高压监管场景。对做企业 agent 的人来说，这是"数据主权"作为产品卖点的一个清晰信号。

**Vercel CEO Guillermo Rauch：scriptc 编译的 TypeScript 比 tsgo 快 2-4 倍**
https://x.com/rauchg/status/2111274408706965898
"TypeScript is the new TypeScript"——一个用 scriptc 编译的 TS 跑分超过 tsgo 2-4 倍。工具链层面的性能竞赛还在继续。

**Claude 官方：Haiku 5.5 写二十首俳句，然后用 JavaScript 画出每一帧**
https://x.com/claudeai/status/2111177845846495646
小模型做完整多步创作流水线的一个展示，比跑分更能说明"低成本模型已经够用"这件事到了哪一步。

**Sam Altman：Navier-Stokes 里程碑 T 恤的背面**
https://x.com/sama/status/2111139227761266699
他晒的那件 T 恤背面印的是"解法 chain-of-thought 的最后一行"（9000+ 赞）。信息量不大，但这本身是个态度：把模型的推理轨迹当成可展示的成果物。

---

## 一句话总结

今天所有信号指向同一件事：**模型能力已经不是瓶颈，harness、review、权限、数据边界这些"外围工程"才是。** Brockman 的 25 人专职扫漏洞、Cherny 的 PR 自动审查、Shipper 的"编辑与监督"、Masad 的数据不出门，说的是同一个问题的四个面。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
