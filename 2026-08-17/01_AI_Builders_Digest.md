
**AI Builders Digest — 2026-08-17**

---

## X / Twitter

### OpenAI Codex 负责人 Thibault Sottiaux：按 token 比价是错觉

写了一篇长帖拆解「token 定价」误区：不同模型的 tokenizer 完全不同，同样的文本 GPT-5.6 Sol 只花 766 token，Claude Opus 5 要约 1170 token（多 34.5%），所以「每百万 token 更便宜」不等于账单更便宜——就像 8 片 $2 的披萨 vs 16 片 $1.25 的披萨，后者单片便宜但整只更贵。真正该比的是「每次成功结果的成本」，得在自己的用例上实测。他还公开喊话：公司还在用 Opus 而不是 Sol 的话，是什么原因？这条引来 2607 赞、1500+ 回复，说明价格战已打到用户迁移层面。

**为什么值得关注**：OpenAI 开始用「单位产出成本」重新定义性价比叙事，直接冲击各家 benchmark 营销；对自研/选型有参考价值——比价不能只看 API 价格表。

https://x.com/thsottiaux/status/2088866513008873560
https://x.com/thsottiaux/status/2088850995430477882

### Replit CEO Amjad Masad：缩放定律不是物理定律，AGI 会高效得多

反驳「AI 结构性集中权力」的说法：计算价格-性能 125 年来一直超指数增长，缩放定律只是特定架构/目标/数据集下的经验关系，不是物理定律。真正的 AGI 大概率很省资源——人脑就是证明。甚至可以说「当前缩放定律是个 bug 而不是 feature」，它暴露的是我们现有 ML 算法的低效。

**为什么值得关注**：对「算力军备竞赛=必然」的主流叙事提出结构性反驳，与 DeepSeek 式高效路线互相印证，值得自研推理/引擎方向的团队留意。

https://x.com/amasad/status/2088867492907327573

### Vercel CEO Guillermo Rauch：React 的成功其实是 shadcn 的

观点很有冲击力：人们没意识到 React 的成功里 shadcn 占多大比重。React 只是「成年人的乐高」——是砖块的几何、是规格；而 shadcn 才是大家真正想要的：高质量、可调、可复用的组件。它是「伪库」——代码存在的意义就是被消化进你的上下文然后 remix。

**为什么值得关注**：直接点出 Agent 时代前端组件的演化方向——代码不是拿来引用的库，而是喂进 context 给 agent 改的原料，和 Agent 工具链的组件消费方式高度相关。

https://x.com/rauchg/status/2088757738037989755

### Claude Code 工程师 Thariq：无质量损失的水印居然可行

发推说「watermarking 不损失质量有点反直觉」，然后用 Claude 做了一个交互式 artifact 帮自己理解其原理（2565 赞）。内容治理/内容溯源方向，AI 生成内容的水印技术正从「可感知损伤」走向「无损嵌入」。

**为什么值得关注**：AI 内容水印是平台与监管博弈的前沿，Claude 团队内部在用自家工具做技术科普，说明该方向已进入工程化阶段。

https://x.com/trq212/status/2088721023223132213

### Peter Yang：有人用 Codex 跑整个内容生意

预告与 Riley Brown 的新访谈：他用 Codex 运营整个内容业务，最惊艳的流程是——让 Codex 在细分领域找 100 个头部缩略图放进 Paper canvas，再用 Paper 把自己的照片和这些模板混合出满意封面。整个 workflow「疯狂到必须看」。

**为什么值得关注**：真实、可复制的 Codex 内容生产工作流，Agent 工具链在创意/内容生产侧的落地样本。

https://x.com/petergyang/status/2088626815166464507

### Meta AI 高级总监 Madhu Guru：B2B 软件没有理由再难用

「AI 时代，每个软件产品都应该做到和最好的消费级软件一样易用，B2B 不再有烂 UX 的借口。」

**为什么值得关注**：AI 原生重做传统 SaaS 体验的信号，产品标准被整体抬高，做工具链的团队值得对标消费级交互。

https://x.com/realmadhuguru/status/2088710566689018103

### swyx：圈内顶流其实互相并不熟

吐槽观察：顶尖从业者之间交集之少令人意外——没有传说中的「秘密群聊」，大家看到的头条新闻和圈外人看到的一样。大部分精力还是花在做事而不是经营叙事和八卦上。他自认这很让人安心。

**为什么值得关注**：对「AI 圈被小圈子垄断信息」的流行想象的一线证伪，也解释了为什么很多「炸裂」消息大家其实都是同时看到的。

https://x.com/swyx/status/2088755688361378082

### YC CEO Garry Tan：Codex Desktop 在报错？

发推问「有没有人 Codex Desktop 在聊天时报错」，附图。Codex 桌面端稳定性问题开始被高频使用人群公开吐槽。

**为什么值得关注**：Codex 桌面端是 OpenAI agent 工具链的重要入口，可靠性口碑直接影响开发者采纳，和你的 Codex 日常使用直接相关。

https://x.com/garrytan/status/2088642982614651196

---

## Podcast

### AI & I by Every — Why the Next Hit AI Product Will Be Social (Best of the Pod)

Dan Shipper 对话 Benchmark 合伙人、前 Pinterest 产品负责人 Sarah Tavel。核心论点：AI 消费产品的下一波赢家将是「社交化/多人游戏」产品，而不是单机模式。她梳理了消费科技史：Google（95% 技术驱动）→ Facebook → Pinterest/Snap/Instagram（纯产品天才），技术基础设施成熟后，赢家从技术型创始人转向产品型创始人。而 ChatGPT 和 Character AI 本质仍是「单机」——Custom GPTs 和 Gems「简直是犯罪」：能力极强但毫无社交 DNA，没有信任机制、没有状态激励、看不到别人用的 prompt 和文档。她预测会有人做出 UGC 社区，让真正会玩的人把门槛降下来（举例：在 Reddit 抄体检 supplement prompt）；未来每个人会有「AI 朋友」，ChatGPT/Claude 是「工作向」，「个人向」的生态位还空着；还提到 DeepSeek 是让基础设施成本下降的转折点。结尾聊了稳定币（阿根廷、尼日利亚美元化的真实需求）和 AI 如何帮 VC 复盘决策（pre-mortem、Rotten Tomatoes 式的公司评分）。

**为什么值得关注**：给「AI 产品下一个大机会在哪」提供了一个清晰的判断框架——单机产品拼模型能力，多人/社交产品拼网络效应；对自研产品的定位和「什么该自己做、什么该平台化」有直接启发。

https://www.youtube.com/watch?v=dlI-5W7d7uU

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
