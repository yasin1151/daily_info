
内容全部到手（feed 生成于 2026-09-25，11 位 builder / 23 条推文 / 1 篇官方博客 / 1 期播客）。以下是最终摘要。

---

# AI Builders Digest — 2026-09-26

来源：Follow Builders 中央 feed（数据生成于 2026-09-25）

## X / Twitter

**Vercel CEO Guillermo Rauch：AI Gateway 模型支出份额出现剧烈换血**

Rauch 公布了 Vercel AI Gateway 过去两个月的模型支出分布：Anthropic 仍是第一，但份额从 69% 掉到 40%；OpenAI 从 10% 涨到 24%，token 消耗量已登顶；Kimi K3 和 DeepSeek 吃掉了 Anthropic 流失份额的约一半；Opus 5.5 上线两天就拿下 10% 支出；图像生成 62% 由 OpenAI 完成。为什么值得关注：这是少见的、来自真实网关流量的模型竞争快照，说明多头格局已经形成，单一模型绑定正在快速贬值。

https://x.com/rauchg/status/2103216656747262419

**Anthropic Claude Code 团队 Thariq：Plan Mode 要改造成可扩展的「mods」体系**

Thariq 回应开发者的集中反馈，承认很多用户不需要 plan mode（因为自己在做规划），另一部分人则喜欢进入「Claude 只思考、只和你脑暴」的模式。他的方案是把 plan mode 变成一个内置 mod，让 mod 可以新增模式、覆写 shift+tab 快捷键，并且允许用户自定义 plan mode 的 prompt、创建并分享自己的模式。为什么值得关注：这是 coding agent 从「固定交互流程」走向「可插拔交互框架」的信号，直接决定工具链的可定制性上限。

https://x.com/trq212/status/2103212051065921632
https://x.com/trq212/status/2103212052391354794

**Replit CEO Amjad Masad：Muse 现在可以直接在 Replit 上造应用**

Masad 宣布 Replit 的 Muse 具备在 Replit 内部生成完整应用的能力。为什么值得关注：这是「agent 直接交付可运行产品」的又一次产品化落地，把从想法到部署的链路继续压扁。

https://x.com/amasad/status/2103129037011120525

**OpenClaw 作者 Peter Steinberger：给 agent 下「干净」指令是无效的，要给野心目标**

Steinberger 给出了一个非常具体的 agent 提示技巧：如果你只是让 agent「清理一下代码」，它会远远过早停手；应该给它一个有难度的量化目标，比如「删掉 20% 最没用的测试，同时把覆盖率变化控制在 2% 以内」。他还提到用 Daybreak 在一个项目上又找出 8 个长期存在的漏洞，提醒大家认真对待 OSS 依赖。为什么值得关注：这是可直接复制到自研引擎 system prompt 里的经验，也是 agent 评估标准设计的实操素材。

https://x.com/steipete/status/2103148444701610233
https://x.com/steipete/status/2103200311641076100

**Latent Space / AINews 主理人 Swyx：内容策略「Scaling without Slop」开始见效**

Swyx 回顾自己年初定下的内容策略，称前 10 万 YouTube 订阅花了 3 年，接下来 10 万只用了 1.2 个月，AEO/SEO/订阅指标同步上扬，并预告 Latent Space、AINews 进入下一阶段。为什么值得关注：AI 内容生态的分发规律正在被 AEO（答案引擎优化）重写，值得做信息产品的人参考。

https://x.com/swyx/status/2103361254433993165

**Peter Yang（AI 教程与访谈作者）：模型能力迭代快到「不知道下一个被爆的是什么」**

Peter Yang 调侃：Astra 把 3D 模型爆掉了，Opus 又把视频爆掉了，已经不知道下一个是什么。另一条他总结了一个实用技巧，称之为「给 AI 顺毛」（stroking the AI's ego），实测有效。为什么值得关注：前者是模型能力边界的社区体感，后者是 prompt 层面的软技巧，都反映一线用户的真实用法。

https://x.com/petergyang/status/2103318850641260959
https://x.com/petergyang/status/2103310612864569388

**fpv ventures 合伙人 Nikunj Kothari：垂直行业会走向「人人一套定制软件」**

Kothari 引用并认同一个观点：每个小企业主、尤其是蓝领工种，最终都会拥有为自己定制的软件，而「最后一公里」正是差异化与独特体验发生的地方。为什么值得关注：与本期 Claude for Small Business 的方向互相印证，垂直 agent 的落点正在从「通用助手」转向「行业专属工具」。

https://x.com/nikunj/status/2103360292973633770

**Google 副总裁 Josh Woodward：Google Labs 的 Dreambeans 试验在长「邪教式」小社区**

Woodward 介绍了 Google Labs 的较新实验 Dreambeans：每天早上固定数量（few beans）的可做事项被「酿」出来，指向现实世界里真实的人、一起做你关心的事，目前有一批忠实拥趸。为什么值得关注：这是大厂在「反纯对话式 AI」方向上的一次小规模试探，把 AI 当调度器而不是聊天对象。

https://x.com/joshwoodward/status/2103182635992514569

## 官方博客

**Claude Blog：Claude for Small Business 大版本更新，43 个 workflow + 27 个新集成**

本次更新把 Claude 从「后台事务助手」推到「业务增长助手」：新增 43 个开箱即用 workflow 和 27 个集成，覆盖 Shopify、Salesforce、TikTok、Atlassian、Zoom、Xero、Gusto、Square、Stripe、Zapier 等小企业已经在用的工具，并配套秋季线下免费 workshop 与合作伙伴 webinar。自今年 5 月上线以来安装量已超过 90 万次。官方转述的用户反馈里，TruckingMBA 的 Bill Hood 说：「我们告诉它最终目标，它自己去测，90% 的情况下它能做对。我们是一家五个人的公司。」为什么值得关注：这是「工作流即产品」的典型打法——不是卖通用 agent，而是把行业 know-how 固化成可复用的 workflow + 集成矩阵，和国内做垂直 Agent 工具链的思路高度重合。

https://claude.com/blog/claude-for-small-business-launches-new-workflows-integrations-and-training-programs

## 播客

**The MAD Podcast with Matt Turck：Who Feeds the GPUs？Inside AI's Hidden $30B Layer — Renen Hallak，VAST Data**

**The Takeaway：真正卡住 AI 的不是 GPU，是夹在 GPU 和模型之间那层没人愿意做的软件基础设施，而且它的需求正在按季度被自己人反复上调。**

Renen Hallak 是 VAST Data 的创始人兼 CEO，公司估值 300 亿美元，客户包括 xAI、CoreWeave、Nebius、Mistral、Nscale，但几乎没人听过，因为它坐在 Jensen 那个「五层蛋糕」（能源、芯片、基础设施、模型、应用）的正中间。他描述需求的方式最值得记：一个 AI cloud 客户原说三年要 500 PB，上周回来说「再加 2 个 exabyte」；小客户和大客户都在普遍往上修，「有时候这确实让我害怕」。他给企业的路线图是一句很好记的话——"We infer during the day, we fine-tune at night"，白天推理、夜里微调，组织的 IP 最终沉淀为权重，而不是把数据交给别人。

他本周发布的方向是「模型管理」：当模型变成和 GPU、SSD 一样的资源，就需要一个操作系统来判断哪个模型擅长什么、prompt 该路由到哪张卡、哪张卡上还缓存着你的 context。其中一块是 Data Enclave，靠 NVIDIA 的加密内存做端到端机密计算，让企业在自己机房推理却不暴露模型权重、模型厂商也看不到企业数据。配套的还有 agent 治理：给 agent 分配类似人类用户的 user ID，用 ACL/RBAC/ABAC 控制它能读哪些数据、能调哪些工具、能和谁对话，并通过持久化流式服务做可观测。他举的证据是本周 Navier–Stokes 被「放出去 1 万个 agent、几天内给出结果」，认为 agent 协作带来的阶跃确实在发生。

对生态的判断也很直接：硬件会快速商品化，价值会留在软件基础设施层（他把亚马逊、微软、苹果、谷歌当作云、PC、移动、互联网时代的同类先例），而模型层从未出现过，可能最终和应用层合并。谈到 hyperscaler 时他说「他们的午餐正在被别人吃掉」，并用创新者窘境解释为什么 AI cloud 没被打败——因为在战壕里干活的人每天在学习，握着便宜资金的没在学。关于 NVIDIA：「除了作为投资人，我们之间没有任何法律文件」，但双方各有一百多位工程师在十几个项目上协作。他借 Elon 的管理哲学收尾：找出限制因素、干掉它、再找下一个；「坏消息要大声且反复说，好消息说一次且轻声」。

https://www.youtube.com/@DataDrivenNYC/videos
（本期音频页由 feed 提供，为节目频道页；JSON 中未包含具体视频地址）

Matt Turck 另发了一条带完整时间轴的章节列表，涵盖「AI factory 到底是什么」「Walmart 和 Goldman 该不该自建 AI」「KV cache / model routing / RAG 与 agent memory」「500 PB 到 2 EB」「圆形 AI 融资是否有系统性风险」等：

https://x.com/mattturck/status/2103167531917721866

---

本期跳过：Dan Shipper（仅互动性短推）、Aditya Agarwal（与 AI 无关的加州话题对谈）、Swyx 关于会议形式的一般性吐槽。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
