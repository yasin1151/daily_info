
# AI Builders Digest — 2026-11-09

来源：10 位 builder、19 条推文、1 期播客。以下只保留有信息量的，纯周边和空话已剔除。

---

## X / Twitter

**OpenAI Codex 负责人 Thibault Sottiaux：Pro 套餐的真实用量倍数**

他先澄清一轮混乱："all Pro plans have no 5-hour limits"，只剩总量分档 — Pro 100 是 Plus 的 10 倍，Pro 200 是 20 倍，Pro 500 是 50 倍并解锁 ultrafast。随后又发一条公开征询："Would a Pro 50 make sense? Wdyt?"（1.3k 赞、855 条回复，讨论热度很高）。

为什么重要：Pro 档位已全部取消 5 小时窗口限制，只在总量上分层。对重度 Codex 用户，Pro 100 是当前成本拐点；官方主动问 Pro 50，说明还会补一档更低的入门档，值得等一等再续费。
https://x.com/thsottiaux/status/2119296267545419987

**Box CEO Aaron Levie：数量级提升来自 harness，不是模型本身**

"we're starting to see plenty of examples of productivity gains that are an order of magnitude or two above output levels pre-AI." 他列了五个前提：正确的 harness、对领域足够深的理解、相对较新的代码库、同时操作多个 agent 的熟练度、低摩擦的测试部署链路。更反直觉的是后半句——"What's crazy is this gap doesn't appear to be diminishing over time"，本以为 AI 会让差距收敛，结果是原有深度加上愿意换方法的人杠杆更大，而且还在复利。

为什么重要：这是对"Agent 工具链投入到底值不值"最直接的回答——决定产出的是脚手架和工程习惯，不是模型版本。
https://x.com/levie/status/2119111328099168409

同一天他还写了一条架构向的判断：推理不必靠近用户。长跑 agent 成为常态，任务价值远高于延迟敏感度（"getting back $500 in value from an automated task, but it takes an extra second"），而且推理过程不需要长期存数据，AI 工厂可以当 ephemeral 系统来用。结论是数据中心选址的政治经济格局会变。
https://x.com/levie/status/2118953909524050288

**Karpathy：47K 视频的个人 YouTube，Claude Code 三分钟一发成型**

他看到 Tristan 整理的优质 YouTube 频道清单后，直接把清单做成可浏览的站 "TristanTube"：47K 个 "super nerdy" 视频加 TV 模式。括号里那句才是重点 —"(One-shotted with Claude Code in 3 minutes)"。

为什么重要：顶级研究者现在把"做个内部工具"当成看清单的顺手动作，自建工具的成本已经被压到分钟级。
https://x.com/karpathy/status/2119114537442189652

**Peter Steinberger（OpenClaw / OpenAI）：反对在开放项目上追加限制**

谈 Asahi 项目："was all about taking something closed and restricted and opening it up. Adding new restrictions that make it harder for other projects to build on that is not the way." 末句 "that AI rejection is just silly"，语气很硬。

为什么重要：开源与 AI 的治理分歧正在具体项目上落地，条款怎么写直接决定下游能不能 build。
https://x.com/steipete/status/2119264334627090514

**Aditya Agarwal（SPC 合伙人，前 Dropbox CTO）：数据中心建不动，就做多已有产能**

"If building datacenters becomes harder, it is obvious that you should be super long anyone who has existing capacity (aka hyperscalers)." 需求只会上涨，"the spice holders will win big"，真正受损的是新模型训练速度 —"I guess we will pace the frontier after all. The body politic speaketh."

为什么重要：把"算力政治"翻译成可执行判断——瓶颈从 GPU 转到建站许可和地方政治，前沿模型的节奏会被动放慢。
https://x.com/adityaag/status/2119157297167372646

**Nikunj Kothari（FPV Ventures）：一篇把 AI 融资套路写尽的讽刺**

他自己标注 "the whole thing is satire, but individually each line is true"：模糊地晒营收（"no y axis, just keep showing numbers and to the right"）、让投资人 quote tweet 替你邀功、买 "premier" 媒体的文章再对投资人投广告、最后堆咒语 "long horizon agent swarms... world models physical ai"。

为什么重要：这份咒语清单就是当下 AI 融资的估值关键词表，也说明 agent swarm / world model / physical AI 已经进入叙事通胀阶段。
https://x.com/nikunj/status/2119162212044742938

**Garry Tan（YC 总裁）：把"能否拥有丰裕"当成下个十年的政治主轴**

"We could have abundance... This is going to be the defining political issue of the next decade: can we have human progress in science, medicine and engineering through superintelligence? Or will we choose the darkness?"

为什么重要：YC 一方已把 AI 叙事从产品层拉到政治动员层，这会影响创业公司的公共表达和监管环境。同日他另有一条直接说 "WIRED is a shell of its former self"。
https://x.com/garrytan/status/2119146939514278238

其余几位本期没有可用的技术内容：Swyx 只在晒周边和贴纸，Amjad Masad 讲哈萨克斯坦见闻与 "The Better Lesson"（无正文），Zara Zhang 讲创业命运非注定（通用励志），故不展开。

---

## PODCASTS

**No Priors — Tokenization, Agentic Trading, Harmonic: Robinhood's Mission to Expand Ownership with CEO Vlad Tenev**

**一句话结论：所有权是唯一主线，agent 只是把所有权民主化的新工具。**

Vlad Tenev 用 "ownership" 一个词概括 Robinhood，覆盖 120 多国。他的判断是"没有广泛所有权的社会本质上非常脆弱"，产品线由此串起：Trump accounts、Robinhood Ventures（上市前私企）、tokenization，共同指向"所有权全球化"。

代币化的机制照抄稳定币：资产仍托管在银行，代币在 DeFi 里流转、拆分、抵押。去年在欧洲上线股票代币但没真正 DeFi 化，今年配合自建 Robinhood Chain 重启，完全上链。开发者把它当乐高用：股票代币与 meme coin 组交易对、NFT、池化资产。野心在长尾国家——用户用一个手机加非托管钱包买美股，"就像稳定币成了他们获取美元的默认方式"。

最值得做 Agent 工具链的人看的是 agentic trading 部分：Robinhood MCP 上线几个月 15 万客户开户，工具调用量指数增长，最近约每天 3000 万次。随后发布 Robinhood Agents，harness 和 UI 都在账户内，他原话是"可以理解成为交易优化的 Claude Code 或 Codex"，带 skills 和 agent app store。北极星是"把对冲基金的能力放进普通人的口袋"。风控是账户隔离、默认每笔人工批准、可关闭，"sandboxed，也许不算 air gap，但差不多"——这个默认策略值得抄。

Harmonic 部分他明确反对数学被垄断："AI 公司带着巨大的数据中心，员工用秘密模型做完全部工作。" Aristotle 模型是去年 IMO 金牌三个模型之一，公开后被用来攻 Erdos 问题。他的立场是工具该交到用户手里，"一个普通人用它证明出纳维-斯托克斯，会比实验室证明更被接受"。

最后是 AI 繁荣的所有权缺口：巨头多为私有，万亿估值上市后散户已无 1000 倍空间，收益集中到少数 VC。"如果我是个普通人，我没从这些活动中获得任何经济利益"——那就别奇怪人们反对数据中心。他甚至拿 crypto 做对照：2022、2023 年很多人亏钱，2024 年仍全力投票，因为"crypto 从一开始就是个人广泛持有"。解法是 Fund I（持有 OpenAI、Crusoe）与携手 YC 的 Fund II；Trump accounts 由财政部为 2025 年后出生的孩子存入 1000 美元，Dell 基金会追加 60 亿美元以上，目标把家庭持股率从 65% 推到 95%。

链接（该期仅有频道页，feed 未提供单集地址）：https://www.youtube.com/@NoPriorsPodcast

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
