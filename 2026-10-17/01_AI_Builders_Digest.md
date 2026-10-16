
**AI Builders Digest — 2026年10月17日**

数据源：14 位 builder、30 条推文、1 集播客（feed 生成于 10 月 16 日，为新鲜内容）。

---

**X / TWITTER**

**Boris Cherny（Anthropic，Claude 团队）**
他说过去几年 Claude 在 prompt injection 防护上取得了显著进展，但 agent 能做的事情越多，这个问题就越需要在全行业范围内被解决。他期待与 Gray Swan 合作办竞赛，看看大家能挖出什么。
为什么值得关注：prompt injection 是 agent 落地的头号安全短板。Anthropic 把它从「自家模型的 bug」提升为「全行业共同问题」并出钱办攻防竞赛，等于承认这块还有硬骨头没啃下来。
https://x.com/bcherny/status/2110791698611855624

**Aaron Levie（Box CEO）**
两条观点最值得看。第一，他认为从「和 agent 来回聊天」转向「随手在后台拉起 agent 干活」，token 消耗将是今天的 100 倍到 1000 倍。因为知识工作今天基本卡在信息处理环节（搬数据、审文档、查代码安全、翻日志、查客户背景），再往后就是把任意数量的 agent 扔给一个问题，只说一句「搞定了再回来」。第二，他评价 Meta 放出 Muse 开放权重模型是「美国开源的一大步」，企业会混搭使用：编排和高难任务用前沿闭源模型，可重复流程用低成本的后训练定制模型。
为什么值得关注：第一条是「agent swarm 吃天量 token」最直白的产业判断，直接指向新一轮算力需求；第二条则否定了「开源 vs 闭源二选一」的叙事，混搭才是企业实际做法。
https://x.com/levie/status/2110622982762803449
https://x.com/levie/status/2110787013809222141

**Thibault Sottiaux（OpenAI，Codex 与 ChatGPT 团队）**
他发了一句含糊的「要么我们没想法了，要么我们正在做菜，时间会证明」，另外两条高赞帖是「我用法语写代码」和「Bonjour」，其中一条拿到 2774 赞。
为什么值得关注：Codex 负责人用这种方式预告在制品是常规操作，社区普遍在猜是否与新版本或多语言编程能力有关。这条本身信息量很低，但「有东西要发」的信号很明确。
https://x.com/thsottiaux/status/2110971985417441512

**Dan Shipper（Every CEO）**
他写了一段尖刻的嘲讽，讲可解释性研究的循环打脸：你今天读完 polysemanticity 就以为可解释性等于解缠绕叠加，下学期发现有个神经元对埃菲尔铁塔亮起来，就改口「我们知道它在想法国」便能对齐超级智能，再下一年才意识到，知道它认出埃菲尔铁塔，根本不告诉你它在策划什么。
为什么值得关注：这是对当前可解释性与对齐叙事的一记冷水，来自长期追踪一线研究、不算外行的人，在圈内传播度很高。
https://x.com/danshipper/status/2110831666587713810

**Aditya Agarwal（SPC 普通合伙人，Dropbox 前 CTO）**
他说坚信 Goodfire 可能是 SPC 投过最重要的公司之一，因为它证明可解释性和对齐可以当成工程问题来做。
为什么值得关注：和上一条正好是正反两方。投资人把「对齐工程化」当成主题来下注，说明这条路线开始有了资本叙事支撑。
https://x.com/adityaag/status/2110779602453066224

**Garry Tan（Y Combinator 总裁兼 CEO）**
转发 Muse 相关消息时只写了一句话：「开放权重模型正在崛起」。
为什么值得关注：YC 掌门人对开放权重的态度，会影响一批早期创业公司的技术选型。
https://x.com/garrytan/status/2110838867213668587

**Nan Yu（OpenAI Codex 产品负责人，前 Linear 产品负责人）**
他区分了「taste」：品味不是审美品味，那是最浅、最没意思的一种定义。
为什么值得关注：coding agent 的竞争正在从「能不能写对」转向「写得合不合口味」，产品负责人怎么定义品味，关系到 Codex 下一步优化什么。
https://x.com/thenanyu/status/2110730151222980849

**Zara Zhang（构建者）**
引用 Ezra Klein 的一句话：「永远不要低估你读者的智力，也不要高估他们的先验知识。」
为什么值得关注：做 AI 产品和写内容都适用的一条硬道理，值得抄下来。
https://x.com/zarazhangrui/status/2110815456458412179

---

**PODCASTS**

**The MAD Podcast with Matt Turck —《Jev: The AI That Makes Decisions, Not Text - and Why It Changes Everything（嘉宾：Diogo Almeida）》**
（feed 只提供频道地址，本期没有可用的单独视频链接）
https://www.youtube.com/@DataDrivenNYC/videos

**The Takeaway：** AI 最值钱的方向可能不是更会聊天，而是变成软件里那个可靠的「智能 if 语句」，用概率输出替你做决策。

Diogo Almeida 是 TypeSafe 的 CEO，也是 RLHF 的早期作者之一。他的模型 Jev 发布仅一个月就成了 AI 圈被复制最多的产品：发布会视频 4000 万播放，日活百万级用户、日处理万亿 token，三分之一财富 500 强在用，公司刚宣布 8.7 亿美元 A 轮、75 亿美元估值。他想解决的问题是：AI 很强，但对绝大多数真实场景毫无用处。

他的核心判断是「machine native AI」。今天所有 AI 都是侧边那个聊天框，因为它和软件配合得很差。Jev 的形态是分类器，输出概率而不是文本，让开发者用「智能 if 语句」把这些概率接进代码分支。他把这称为「系统一」：快速、直觉的决策，而不是脆弱的推理链。他的原话是那句最有名的比喻，「95% 是爱因斯坦，5% 是憨豆先生，如果它不告诉你哪一刻是憨豆先生，你怎么敢自动化任何东西？」

因此他把矛头对准 RLHF：那本质是让模型「会聊天、讨人喜欢」，代价是谄媚、过度拒答、风格高度同质，并且让模型在决策上更钝。更严重的是它抬高了人类对 AI 的预期，导致「巨大过度承诺、严重交付不足」。RLVR 也不解决问题，它只会把 benchmark 刷爆，对真实自动化没有改变。TypeSafe 自研了 RLCD，专门为机器原生智能优化，训练数据全部自建，且不使用用户数据。

他也回应了抄袭潮：三周内 Cloudflare、Databricks、微软都推出了 decision model 类别。他的看法是，拿掉文本生成、复制接口非常容易，他自己第一周就做出来了，但那个版本「蠢到令人尴尬」；可靠性上对手可能落后数年。他还批评 benchmark 误导人，倒是称赞 OpenAI 的 decision API 没放 benchmark，算「比别人厚道」。关于开源，他目前倾向只做 API，认为短期开放权重对用户是个「foot gun」。他甚至直言预训练是「一个巨大浪费资源的垃圾场」，所以只拿开放权重模型做底座。商业逻辑上，Jev 的名字来自杰文斯悖论：单位智能价格暴跌会让用量爆炸式增长，路径更像半导体而不是汽油。最后他明确说不认为我们正走在递归自我改进（RSI）的路上，拿 neural architecture search 的历史作类比，并且认为 AI 冬天会以另一种方式被避开，即 AI 对自动化真正开始有用。

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
