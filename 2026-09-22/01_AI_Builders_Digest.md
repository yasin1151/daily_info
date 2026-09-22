
I have everything I need. Feed is 1 day fresh, transcript read in full. Composing the digest.

AI Builders Digest · 2026-09-22

今天推特侧的最高信号是「个人 agent 赛道」的格局拆解和 agent 做 QA 的真实案例；播客侧是 Coinbase CEO 讲 agent 金融和内部 agent harness，对做自研引擎/工具链的人含金量最高。

━━━━━━━━━━━━
【X / 推特】
━━━━━━━━━━━━

**1. Peter Yang（AI 产品教程与访谈作者）· 个人 agent 赛道格局长帖，591 赞**

他用使用者视角把参赛者逐个点评了一遍。原话摘录：

- 关于 Meta Muse：「Once you use the Muse app, you realize that it makes little sense for an agent to live in an existing messaging app like iMessage.」他认为 Muse 有望成为领跑者，甚至会是 Facebook 之后最成功的自研 App，比 Threads 大得多。
- 关于 ChatGPT：「probably still the personal agent leader because it already has 1B+ users」，但「it's hard to build one product for both work and personal use」。
- 关于 Grok Bot：「isn't really a Muse competitor because it's focused on work」，他的多头逻辑是它「a few features away from becoming multiplayer agentic Slack」。
- Google 是黑马但不够激进：自家 Spark 现在只是 Gemini 里的一个二级 tab。
- 他认为真正的空白是「人多方协作」：「nobody has figured this out yet. I can't easily add my spouse to a Muse chat to plan a vacation. I also can't loop coworkers into ChatGPT or Grok Bot threads.」他把这称为下一个大解锁点。
- 他自己的 stack：「Muse for personal, Grok Bot for cloud tasks, Claude for specific use cases, and ChatGPT for everything else.」

为什么值得关注：这是目前最具体的一份「用了一圈之后」的横向对比，而不是厂商口径。最后那句对做自研引擎的人直接适用：「design your personal skills and files so they're easy to port between harnesses and agents. Otherwise, you'll spend half your time moving from one tool to another.」上下文资产的可迁移性，比选哪家更重要。

https://x.com/petergyang/status/2101862331345154469

同线程补充：他说 Apple/Siri 有设备和隐私口碑、理论上能赢，但「their annual release cycle for major updates」加上不在 X 等平台采集反馈，导致「The iteration speed for Siri (from the outside) just feels far too slow to compete.」

https://x.com/petergyang/status/2101865476145959373

**2. Guillermo Rauch（Vercel CEO）· agent 做测试验证的强度，376 赞**

原话：「The thoroughness with which agents can test and QA software is unrivaled. I pointed out something wasn't rendering right in a mobile (in-app) browser. The thing goes to the depths of Mordor to reproduce, simulate, fix, deploy, verify. It created an ephemeral vercel deployment to throw at an iPhone simulator!」

他的结论：「Humans could simply never match this level of intensity. We'd run out of energy, we'd extrapolate, we'd hope it'd work out.」

为什么值得关注：这不是「agent 会写代码」的老话，而是 agent 在「复现 + 验证」这个闭环上的耐力已经超过人类。做 agent 工具链时，瓶颈正在从「写」转到「人类 review」，评测/复现环境本身就是可以产品化的能力。

https://x.com/rauchg/status/2101846262840799251

**简要提及**

- Peter Steinberger（OpenClaw 作者）：「New benchmark dropped」，1358 赞，feed 只抓到这一句加链接，正文需点进原帖看。
https://x.com/steipete/status/2101748820237500557
  另一条：「Your claw can now FaceTime you!」，646 赞，OpenClaw 新增 FaceTime 互动能力。
https://x.com/steipete/status/2101748928274419843
  你自己就跑在 OpenClaw 上，这两条是他本人发的能力更新，值得点进去看图。
- Aaron Levie（Box CEO）：一条转发评论只有一句「Literally impenetrable from agent swarms」，2691 赞。原帖是图片，feed 无法还原语境，仅记录这个判断本身和它的传播量。
https://x.com/levie/status/2101731574668747081
- Matt Turck（FirstMark 投资合伙人，MAD Podcast 主持）：「Everyone is obsessed with Jev now, but I'm old enough to remember when people couldn't shut up about Instinct, all the way back to mid last week. Simpler times.」吐槽 AI 圈换热点以「天」为单位，可当舆论温度计。
https://x.com/mattturck/status/2101820308009206077
- Swyx（Latent Space 播客）：「Jev pod tomorrow」，Jev 相关节目次日发布，仅预告。
https://x.com/swyx/status/2101873256097804529

（跳过：Amjad Masad 给儿子装第一台电脑、Thariq 聊电子游戏、Nikunj 的剩菜咖喱段子、Dan Shipper 荐书，均为闲聊，无 AI 信息量。）

━━━━━━━━━━━━
【播客】No Priors · Coinbase CEO Brian Armstrong：Agentic Finance、稳定币，与「给 AI 开户」
（2026-09-10）

**一句话结论**：agent 经济的单笔金额小到现有支付轨道根本装不下，所以问题不是「给 agent 发张卡」，而是「给 agent 开它自己的金融账户」。

**为什么金额这么小**：信用卡/借记卡最低费率约 30 美分固定费加百分比，付 1 美分不值得。他的原话：「about 76% of the agent ecommerce transactions we're seeing are under 30¢.」这些小额在干嘛：投研机构抓 paywall 数据、招聘方抓 LinkedIn 数据，更多是「agents talking to other agents」，像一次 tool call 一样买数据。

**产品动作**：Coinbase 做了个很轻的入口，把一段 prompt 粘给 agent，它就能拥有自己的金融账户。两条路径并行，一是挂在人类身份下、资金隔离的 agentic account；二是给任意 agent 的自托管钱包，可以持有稳定币余额、甚至融资发 token。原话：「Our AI agents don't have a government ID. They can't walk into a bank branch, at least not yet without their humanoid robot companion.」「We don't want the AIs to be unbanked.」

**支付协议**：agent 支付正在跑 X402，Coinbase 孵化后捐给了 Linux Foundation，Google、Cloudflare、AWS 参与。有个 edgentic.market 站点公开 agent 经济支付量和服务商排名，等于给这条新轨道做了一块实时看板。

**专业小模型**：他说用 10 万条 Coinbase 内部合规案例训练的 open-weight 小模型，在专项任务上可以超过 frontier 模型，所以未来 marketplace 里会冒出一批 specialist agent（「This agent is a really incredible designer, and that's all it's been trained on」）。

**对做自研引擎/工具链最有用的一段，内部 agent harness**：

- 他们在建「brain for the company」，每个团队、每个代码仓库、每个人各有一个 brain（当前就是 markdown 文件）。
- 内容是该服务的历史事故、必须执行的财务控制、跑过的所有 AB test、以及 PR 被接受/拒绝的完整记录。
- 关键机制：agent 改代码时先 ingest 这个 brain；人类 review 时发现漏了东西，**这个修正必须回写进 brain**，而不只是在这一单里手动改掉。原话：「that context has to go back into the brain so that you not only fix it in this case, but in all future cases going forward. Then the accept rate for one-shotted PRs just starts to tick up over time, and you've now got a recursive self improvement system.」
- 他们的内部 harness 叫 Toshi，已接通外部厂商，能直接用 X402 付钱。

**他自己现在的工作方式**：让贵模型把复杂 feature 拆成三阶段、每阶段 10 个任务，然后开 10 个并行 agent 执行，并按任务推荐更便宜的模型（他提到跑了一批开源模型和 Grok）。两分钟前刚收到通知，phase one 十个任务全部完成待 review。原话：「instead of pinging the team in Slack, I can basically tag an agent in Slack with that comment... I just send them a PR for review, and it's already done. And that's a magical moment. It's very addictive.」

**对组织规模的判断**（值得记住的区分）：「tasks are being eliminated, people are not being eliminated.」他不同意「大公司会缩到 10 个人」，认为现有团队会做得更多、节奏更快、毛利改善；同时确实会出现 2 到 5 人做到过去做不到的事的公司。

**其他**：88% 营收已来自非比特币交易；上线了 1:1 实物托管、非合成/非衍生的 tokenized stocks（目前仅美国境外）；预测市场上线数月做到 1 亿美元年化收入；他的另一个公司 New Limit 用 AI 做表观遗传重编程，首批针对肝细胞、血管、免疫 T 细胞，明年启动 phase 1。

**为什么值得关注**：前一半是「agent 需要花钱」这个被低估的基建缺口；后一半的 brain 回写机制和「orchestrator 拆计划 + 子 agent 并行 + 按任务选便宜模型」，是两套可以直接借走的 agent 架构模式，而不是概念。

https://www.youtube.com/@NoPriorsPodcast
（feed 只提供频道页链接，未含具体视频 ID，未做拼凑）

━━━━━━━━━━━━
今日可动手的一件事：检查你自己的 agent 上下文资产（skills、prompts、项目文件）是否有明确的可迁移边界。Peter Yang 那句「一半时间在搬家」和 Armstrong 的 brain 回写是同一个问题的两端：上下文要么能带走，要么能沉淀回去。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
