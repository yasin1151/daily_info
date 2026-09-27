
Feed is fresh (generated 2026-09-27, 1 day old), so no staleness caveat needed. I have all content extracted. Composing the digest directly (small dataset: 8 builders / 14 tweets / 1 podcast).

**AI Builders Digest｜2026年09月28日**

数据源更新于 2026-09-27。本期覆盖 8 位 builder、14 条推文、1 期播客（无官方博客更新）。

---

## 一、编码 Agent 的额度与供给

**OpenAI，Codex 与 ChatGPT 负责人 Thibault Sottiaux（thsottiaux on X）**
> "Resets all propagated. That will be all. Have a fantastic weekend."

中文：所有（用量）重置已经全部生效，就这些，周末愉快。

为什么值得关注：1.39 万赞、1872 条回复，是本期热度最高的一条。一句话能上这样的话量级，说明 Codex 的额度/限流是当下开发者最敏感的话题，官方用轻描淡写的方式做了"重置完成"公告。
https://x.com/thsottiaux/status/2103911959544610829

**Peter Yang（AI 教程作者，petergyang on X）**
> "Not sure what happened to Claude limits they went from barely usable to basically unlimited 😂"

中文：不知道 Claude 的额度到底发生了什么，从勉强能用直接变成几乎无限了。

为什么值得关注：和上一条同一天出现，指向同一个信号，主流编码 agent 的额度瓶颈正在集体松动。422 赞、80 条回复，评论区基本都是"我也发现了"。
https://x.com/petergyang/status/2104066667361992892

---

## 二、Agent 工具链与新入口

**Peter Yang** 另外两条都在试 Google 的新东西：

- 第一次用 Antigravity（Google 新的 agent 开发工具）去接 Google 新音频 API，吐槽"我该找谁反馈问题"（139 赞、46 条回复）。说明这个工具已经开放到普通开发者，但反馈渠道还很乱。
  https://x.com/petergyang/status/2104003094615052443
- 自己用 Gemini 音频 API 搭了一个日语对话练习 app，10 节课、每节 10 句。是"低成本自造学习工具"的典型用法。
  https://x.com/petergyang/status/2104059554204188833

**Garry Tan（Y Combinator 总裁兼 CEO，garrytan on X）**
> "This is my favorite way to fix bugs now, @capydotai with GStack /autoplan on a production issue, GPT-6 medium reasoning"

中文：我现在最喜欢的修 bug 方式，是用 Capy 的 GStack /autoplan 跑生产环境事故，推理档位用 GPT-6 medium。

为什么值得关注：YC 一号人物公开演示用 agent 自动化排障生产事故，"agentic debugging" 从 demo 走到真实工作流的样本。另外这是本期唯一出现 GPT-6 型号的表述，留意模型换代节奏。
https://x.com/garrytan/status/2103989902476259702

**Thariq（Claude Code，Anthropic，trq212 on X）**
> "Just about 1 year ago I posted one of the first posts about using Claude Code to make videos. Each of these actually took a long time to iterate with Claude and get right..."

中文：大约一年前他发了最早一批"用 Claude Code 做视频"的帖子，当时每一个都得反复跟 Claude 来回磨、纠正细节才能做对，感慨一年间变化之大。

为什么值得关注：这是从内部人视角给出的"编码 agent 这一年到底进步了多少"的对照，1101 赞。对判断工具链演进速度有参考价值。
https://x.com/trq212/status/2103897226154328502

---

## 三、观点与争议

**Vercel CEO Guillermo Rauch（rauchg on X）**
> "Reject non-understanding. Slop grenades are not just code and PRs. We run a real risk that *reading* gets entirely discounted, because of the exhaustion of getting low-quality and unverified AI prose being thrown at you all the time."

中文：他提出要"拒绝不理解"。AI 垃圾不只是代码和 PR，还有文字。我们面临一个真实风险，阅读本身会被彻底贬值，因为你不断被低质量、未经验证的 AI 文本轰炸，直到精疲力尽。他举了一个正在疯传的例子：某个"性能提升"被归功于编译器改动，但那份 PR 描述里 AI 自己就明说这跟编译器无关，是算法和数据结构的改变，并且暗示同样的收益本来可以用别的方式拿到。他说自己想要的，是用 AI 服务于理解世界、增强人的认知和创造力。

为什么值得关注：1715 赞、124 转发。这是 builder 圈对"AI 生成内容泛滥"最凝练的一次立场表达，直接关系到所有用 agent 写代码、写文档的团队的评审文化。
https://x.com/rauchg/status/2103939888513274147

**Dan Shipper（Every CEO，danshipper on X）**
把柏拉图《普罗泰戈拉篇》写成小说，再让 Opus 5.5 把它拍成电影短片（scene 1、scene 2）。属于创作向实验，但顺手确认了 Opus 5.5 已经在被内容创作者日常使用。
https://x.com/danshipper/status/2103850415930708437
https://x.com/danshipper/status/2103894152316645620

---

## 四、播客

**No Priors：Why Diffusion Will Win AI Inference**（嘉宾 Inception 联合创始人兼 CEO、斯坦福教授 Stefano Ermon，2026-09-18）

中文摘要：这期是"扩散模型能不能取代自回归模型做 LLM 推理"的技术路线之争。Ermon 是扩散模型的奠基人之一（2019 年与学生 Yang Song 的 score-based 工作，后来演化成 Stable Diffusion、Midjourney 那一脉）。他的核心论证是：

- 自回归模型的根本问题是推理阶段的串行性。第 10 个 token 必须等前 9 个生成完，这种负载极度 memory bound，GPU 大部分时间在搬权重而不是算数。训练时代 RNN 被 transformer 取代的原因是并行化，推理时代对应的解法就是扩散。
- 扩散模型推理时的负载形态"几乎等同于训练"，天然并行、天然贴合 GPU。他称之为 bitter lesson：更并行的方案最终一定赢。
- 他们 2024 年发的论文首次证明在 GPT-2 规模上，扩散 LLM 能用同样参数、同样数据达到自回归模型同等 perplexity，而生成速度约快 10 倍。
- 商业进展：Inception 约 50 人、成立两年，Mercury 系列模型在基准上与各家"速度优化版"小模型（Flash、mini/nano 一类）质量相当但明显更快，已在生产环境服务真实客户。语音 agent 公司 Open Call 原本用 Cerebras 定制芯片跑 LLM 换取低延迟，后来换到 Mercury，因为软件层的并行加速能在 NVIDIA GPU 上拿到同等速度，可获得性更高、成本更低。
- 他判断目前大约 20% 到 30% 的 workload 对延迟极其敏感，属于这类模型的可用地盘。
- 另一个被低估的优势是可控性：扩散是粗到细生成，从最开始就能用外部奖励函数或约束去 steer，而自回归必须等整个对象生成完才能打分。这在图像、分子等领域已经有大量证据，用在文本上是新空间。
- 挑战也很直白：生态不成熟，serving engine、kernel、SFT/RLHF 训练栈基本都得自研，所以他们选择不开源，把 IP 留在手里，代价是社区贡献少、on-prem 部署难。他明确说这本身就是护城河的一部分。

为什么值得关注：对做自研推理引擎和 agent 工具链的团队，这期把"推理经济学 = 每瓦智能、每美元智能"讲得最清楚，而且给出了一个非主流架构已经在生产环境跑通的实证，不是 PPT 路线图。

链接（该期播客，JSON 中只提供频道页地址）：
https://www.youtube.com/@NoPriorsPodcast

---

生成自 Follow Builders skill：https://github.com/zarazhangrui/follow-builders
