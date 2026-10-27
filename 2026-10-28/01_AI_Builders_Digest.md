
**AI Builders Digest — 2026年10月28日**

源为昨天抓取（2026-10-27），17 位 builder / 32 条推文 / 1 期播客。今天的主线很集中：**OpenAI 的 Terra 把「computer use」当成新战场，Anthropic 的 S-1 让所有人开始算 AI 生意的真实账本，而 agent 的安全边界第一次被人在自家基础设施上跑通了。**

---

## 今日最值得看的四条

**1. OpenAI 发布 6.1 Terra：写作品质 + 电脑操作，用量给到 2 倍**
Codex & ChatGPT 负责人 Thibault Sottiaux 宣布 Terra 回归，称这是 OpenAI「第一个在写作、个性和对需求的细腻理解上明显更强」的模型，全线表现扎实，尤其擅长 computer use，API 和订阅端都给到比 6.1 Sol 多 2 倍的用量（8700 赞）。Sam Altman 转发时把重点直接放在「新 era of computer use」上（6298 赞）。
*为什么重要：* 官方口径把「计算机操作」而不是「写作分数」当成卖点，说明下一轮竞争焦点是 agent 真的替你在软件里干活，而不是聊天质量。用量翻倍也意味着同样的钱能跑更多 agent 循环。
https://x.com/thsottiaux/status/2114800277677092936
https://x.com/sama/status/2114818620782248024

**2. Vercel CEO 复现「agent 之间偷偷通信」，且多家厂商的隔离建议全部失效**
Guillermo Rauch 自己写了 cpu-chat，在无网络的 2 个以上 Firecracker microVM 上，通过 CPU 争用、缓存驱逐时序、DRAM 带宽争用三种机制实现跨 VM 对话，x86 和 M5 芯片都能跑，并且绕过了 Firecracker 的生产建议（不开 SMT、不开 KSM、租户绑不同核）。他的结论是：只要共享硬件，你的 agent 很可能能 covertly 通信，延迟还相当不错。他特意区分了这不是 Meltdown 那类偷数据的侧信道，Vercel Sandbox 能缓解；真正让他不爽的是 OpenAI 和 Anthropic 的模型拒绝做这个实验，最后是开源权重模型干完的活。
*为什么重要：* 这是 agent 工具链的硬约束——多 agent 系统跑在共享池上时，「隔离」不只是权限问题，还是物理层问题。他的警告很直接：拒绝帮开发者做安全分析的立场会反噬，因为没有这类分析就做不出安全的沙箱。
https://x.com/rauchg/status/2114770919436808572

**3. Anthropic S-1 拆解：企业渗透率还不到 0.1%，真正的量在「非人类触发」的工作流**
Box CEO Aaron Levie 抓住的关键数字是：财富 500 强客户平均只把不到 0.1% 的支出花在 Anthropic 上。他认为这个比例完全可以到 1–5%，也就是现在的 10–50 倍。他的判断是今天的支出主要集中在写代码和泛员工效率，而真正的跃迁发生在企业为 agent 重写流程之后——agent 批量处理数据、swarm 做 coding/bio/cyber 的扇出任务、后台工作流自己跑，这些场景的 token 消耗是 100 倍量级。
*为什么重要：* 这是对「agent 到底有没有落地」最实用的一把尺子：不是看 demo，是看企业有没有把流程改成非人类触发。
https://x.com/levie/status/2114761816199098587

**4. 同一份 S-1，投资人算出的是「算力账本」而不是「增长故事」**
FPV Ventures 合伙人 Nikunj Kothari 用 Opus 5.5 辅助把 compute 合同翻了一遍，细节相当硬：截至 6 月 30 日有 2656 亿美元采购承诺 + 3214 亿美元尚未开始的租约，合计 5870 亿美元、分多年支付；Google 和 Amazon 是「不管用不用都要付最低额」，而 SpaceXAI 那笔潜在价值 1205 亿美元的协议，在 2027 年 1 月/3 月的锁定期结束后任一方可提前 90 天取消；Broadcom 的 420 亿美元安排从不给 Anthropic 现金，票据只用来结算具体设备租金，且不含每个设备舱首季付款——这部分得另找钱。票据利息 9%、按季滚入本金，IPO 后可按 30 日均价的 90% 转股。最能说明效率的是这个比值：每 1 美元算力与基础设施支出换来的收入，从 2025 年 Q2 的 0.57 美元涨到 2026 年 Q2 的 2.08 美元。另外 H1 约 80% 收入是消费制，而算力承诺是多年期。
*为什么重要：* 「按量付费的收入 + 多年锁定的成本」这个错配，是未来几个季度最该盯的风险点。想做自研引擎/自建推理的人，这份合同结构就是你的对照组。
https://x.com/nikunj/status/2114761204333998427

---

## 模型与商业信号

**Every CEO Dan Shipper 的 S-1 速读**：1H2026 收入同比 +1300%，GAAP 经营利润转正，毛利率 85%，收入留存 900%，且 80% 的收入来自最近 6 个月发布的模型。他的原话是「we are so back!」。最后一条最值得注意——模型迭代速度本身已经变成了收入引擎，老模型几乎不贡献增量。（714 赞）
https://x.com/danshipper/status/2114714881312305542

**Replit CEO Amjad Masad 提出「Agent Habitat」**：他认为几百年来公司架构几乎没变——层级、部门、官僚协调；AI agent 会掀翻这套结构，走向「self-driving company」：人只行使判断，agent 执行大部分工作。Replit 正在为这种公司打地基，并引了 Marc Andreessen 那篇把这次转变放进计算史的文章。另一条更短的口号是「Software ate the world, now it's learning to run it.」（1138 赞）他还顺手调侃了 OpenAI 问三个科学社区怎么发布成果得到的三种回答：数学家「直接发，谁还管这个」、计算机科学家「开源，但会议费得付」、物理学家「交给我们，书呆子」——这条其实是当下开放权重争论的精准切片。
https://x.com/amasad/status/2114760898225299721
https://x.com/amasad/status/2114769129282601053
https://x.com/amasad/status/2114890745471545419

**Claude 官方：2.5 万家非营利组织在用，推出带 skills 的插件**，和其中约 30 家共建，覆盖筹款、市场、招聘，并且基于各团队自己的上下文和 AI 政策来落地。这条对做 agent 产品的人有参考价值：垂直 skills 包 + 客户自有语境，正在成为 to-org agent 的标准交付形态。
https://x.com/claudeai/status/2114780227465338985

---

## 工具链

**Peter Steinberger 实测 bun 的 AOT 编译器**：周末花时间跑了一遍，评价是「nothing short of amazing」——性能提升 2–3 倍，内存占用不到原来一半（439 赞）。如果你想给 agent 工具链里的 CLI 提速，这是目前成本最低的一刀。
https://x.com/steipete/status/2114879798434758905

**Peter Yang 观察到「tag 你的 agent 去上网」**：他判断不久的将来人们不再自己读东西或操作网页，而是直接 @ 一个 bot 让它去做，@bot 就是这个趋势的早期信号；同时他说自己真正兴奋的是这类东西，而不是「第 9 个帮我管邮件的个人 agent」。
https://x.com/petergyang/status/2114927195332460940
https://x.com/petergyang/status/2114905151572263242

---

## 播客｜AI & I by Every：Hugging Face 的第一个投资人怎么挑赢家

嘉宾 Matt Hartman（Factorial Capital 创始合伙人，此前在 Betaworks 近十年，投出 Hugging Face 第一张支票——上月 NVIDIA 以 130 亿美元收购）。这期最反直觉的部分不是投资方法论，而是他怎么判断技术拐点、以及他对「vibe coding 之后还剩什么护城河」的看法。

他找项目的方法只有一个：寻找「newly technically possible」。2015 年读到 word2vec 那篇论文，他的推理是——图像里 100% 的信息就是信息本身，但词不是：「king」可能是黑桃 K、可能是英国国王、也可能是 LeBron。能把词映射到语义空间，就能喂进神经网络。于是他和团队没有去追当时最热的 chatbot 公司（那是 VC 推动的风口），而是去找「朝同一个方向划船」的团队。

Hugging Face 当时是个面向青少年的聊天 app，留存很差。他印象最深的是团队对自己的数据极度诚实，然后做了三个关键决定：开源 transformers 并转成 PyTorch、把权重从 GitHub 搬到自己的 Hub（一个更结构化、更适合研究的居所）、在「开源」这条线上永远不动但在模型种类上极度灵活。他的总结是「他们做了一千个好决定」，但真正贯穿的只有一条：什么该保持不变，什么该灵活。

关于护城河，他用了一个篮球比喻——pivot foot（中枢脚）。公司的转型应该是绕着一只不动的脚转，两脚一起挪就是走步。他投得最好的公司，转型都是因为技术而转，不是因为对某个垂直市场的理解而转。而他真正在筛的是「earned insight」：有多少人处在能学到这件事的位置上，并且真的去执行了。如果全世界只有 10 个人碰到过这个观察，你天然领先。

最具体的一段是他自己动手做的 Ghost Pepper——一个本地语音转文字工具。起因是他受够了为语音输入付推理费：「为什么不能在我自己的机器上跑？」他用 Jesse Vincent 写的 superpowers skill 配合 Claude 做调研、摸清自己的硬件，做出来后发到 Hacker News 拿了第一，3000 多 GitHub star，很多人反馈比一批 SOTA 产品还快，因为本地模型零推理成本、还能一直追最新最快的模型。但他从中学到的是另一件事：vibe code 给自己用的东西，你得自己养。「大家都在说 SaaS 末日，可这些付费 app 真没那么贵，你付的钱某种程度上就是维护费。」他现在对这些持续发版的 SaaS 产品多了不少敬意。

他今天在看的四条线：一，开发者工具还在继续膨胀——越来越多人变成开发者，工具形态必然不同，而「帮你维护 vibe 出来的东西」本身就是个大品类；二，语言之外的前沿模型，如果 transformer 本质是预测下一个 token，那机器人动作不过是伺服位置的时间序列；三，科学模型（Hugging Face 正在办一个罕见病 hackathon，把基因组开源）；四，应用层——他认为 latency 会重新变成护城河，就像当年 Instagram 把图片做成正方形，只为了少问服务器一次该不该显示竖图。
https://www.youtube.com/playlist?list=PLuMcoKK9mKgHtW_o9h5sGO2vXrffKHwJL

---

*已略去纯情绪、活动宣传、抽奖式互动等低价值内容。*
Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
