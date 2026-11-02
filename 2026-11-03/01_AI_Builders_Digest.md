
AI Builders Digest — 2026年11月3日

## X / 推特

**Andrej Karpathy — 用 Claude 两小时做了个"HackerTube"，过滤掉推荐算法**
他对 YouTube 的推荐很烦，于是让 Claude 把 HN 二十年积累的 4300 万条评论筛了一遍，找出被反复推荐的 6,454 个视频，做成一个无需登录、缩略图取视频中间帧的观看站。全程用 Opus 5.5 + Claude Code 桌面版，他本人只做了三件"手工活"：申请 YouTube API key、开一台 VPS、买域名；之后"把 IP 给 Claude，让它更新、加固、部署、优化，它全做完了"。
为什么重要：这是当前 agent 能力上限的实证样本——人的工作被压缩到"提供凭证 + 做审美判断"，其余是几句话说清需求就能交付。
https://x.com/karpathy/status/2116957135661945283

**Guillermo Rauch（Vercel CEO）— "Own your intelligence"**
他主张本地模型必须继续扩散：绝对体量的超大模型短期内本地跑不动，那就把选择权留在自己手上——自己拥有 harness、数据、连接、运行时，也就是拥有自己的 agent，并拥抱开源。他还补一句：反对这件事的人，"多半是想把你的智能再卖回给你"。
为什么重要：这是对"自研引擎 + 自有 agent harness"路线最直接的公开背书，出自做平台的人而不是做模型的人。
https://x.com/rauchg/status/2117000819623243925

**Box CEO Aaron Levie — 岗位描述正在从"用 AI"变成"管 agent"**
他的判断是：我们正从"agent 帮我们把活干得更好更快"，转向"我们帮 agent 把它们的活干好"；这让很多人从"带 AI 杠杆的个人贡献者"变成"一支 agent 团队的经理"。影响最大的是信息密集型工作——编程、安全、法务、生物、工程。关键变化是杠杆与工时脱钩：过去知识工作只能调"投入小时数"，现在 agent 可以并行，产出理论上按目标而非按小时计。
为什么重要：如果这条成立，绩效衡量、团队编制、汇报结构都得重写，而不是给现有流程加个 AI 按钮。
https://x.com/levie/status/2117134917847093491

**Replit CEO Amjad Masad — 两条：补贴要收回，反馈即 prompt**
一条是警告："如果你正在享受被补贴的 AI 订阅，准备好被收回吧。" 另一条是产品机制：在 Replit 上打开一个开关，站内用户反馈会直接变成 agent 的 prompt 去改产品。
为什么重要：前者是成本结构的真话，后者是产品迭代闭环的形态变化——从"人读反馈再排期"变成"反馈直接进 agent 执行队列"。
https://x.com/amasad/status/2117010858845089805
https://x.com/amasad/status/2116998155925360965

**Peter Yang 访谈摘录 — "你的产品为什么一定要有个人？"**
他引 Google Labs 一位产品总监（X 账号 jacalulu）的话："这真的会让你反思，为什么你想要产品里有个人？你的产品是不是必须有个 UI？" 她的划分是：创作类、学习类还需要人亲自交互；纯消费娱乐之外的大量产品，用户会乐意不再自己操作界面。
为什么重要：agent-first 产品的设计边界问题，比"加个聊天框"要深。
https://x.com/petergyang/status/2116987415319740756

**Peter Yang — 现阶段仍是"一类活一个赢家"**
他想只用一个 AI 工具但做不到：浏览器/电脑操作 = ChatGPT + Codex；设计/视频剪辑/"品味" = Claude；7×24 agent 与定时任务 = Grok Bot；Gemini 写作被低估。
为什么重要：工具栈按能力分工仍是现实，选型逻辑是"任务类型 → 最佳 harness"，不是"找一个全能模型"。
https://x.com/petergyang/status/2116946320674152810

**Garry Tan（YC 总裁兼 CEO）— Particle-1：agentic retrieval 上接近大模型，价格 1/23**
为什么重要：检索这类 agent 基础设施的成本曲线正在陡降，直接影响长上下文/多轮检索型 agent 的单位经济。
https://x.com/garrytan/status/2117137390016073977

## 播客

**Unsupervised Learning — Ep 95: Modal CEO on the Future of Inference, the Chaos of the GPU Market & Origins of the Sandbox Bet**

**一句话结论**：Agent 沙箱是过去三年 AI infra 里最漂亮的一次非对称下注——原型几天做完，如今单拎出来就是 3 亿美元年化收入；而 GPU 云本身，长期是门苦生意。

Modal 创始人兼 CEO Erik Bernhardsson 讲了三件事：

**一、算力市场还是野市。** 他形容 GTC 现场"像个露天的 GPU 黑市"——在酒店大堂换号码，最后靠销售副总裁的亲戚打高尔夫才牵上线。Modal 现在同时对接 25 家云，每周签两三笔算力合同。算力不是可互换合约：位置、可靠性、网络和磁盘差异太大，很难做成真正的交易所；公开的 GPU 价格指数和他们实际成交价对不上。

**二、沙箱是"低 downside、高 upside"的下注。** 2023 年做原型只花了几天，2025 年爆发后系统重写了五次，现在沙箱约占收入三分之一，12 个月涨了近千倍。他说真正的 alpha 来源是"不怕做难事"——自研文件系统、容器运行时、CPU/GPU 快照，换来极快的冷启动，而这些恰好是 agent 最在意的东西："agent 想要的和工程师想要的很像——快反馈、好报错、好文档。"

**三、写代码这件事已经变了。** Modal 合并的代码里约 95% 有 agent 参与，但人还得盯着。一个新麻烦：agent 训练数据里全是旧代码，导致下架功能格外难，弃用窗口被迫大幅拉长。他还点出一个新工种——agent 优化，本质是 AEO：让 Claude 这类模型在回答时推荐 Modal，因为"进了训练数据就有在位优势"。

对 NeoCloud 的判断很冷：模式不算差，但同质化、资本成本高；买卡只付约 30% 首付等于隐性加杠杆，依赖后续融资。至于 GPU 租金，他 48 小时内改了主意，现在押 12 个月后更贵——理由是看了 Anthropic 的 S-1，被其盈利水平惊到，认为两大买家不会减速。

（该期在 Redpoint 的 YouTube 频道，feed 只提供频道链接）
https://www.youtube.com/@RedpointAI

---
今日略过：Thibault Sottiaux（内容为梗图式互动）、Thariq（游戏美术进展）、Dan Shipper / Zara Zhang / Swyx（无实质内容或纯回复）。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
