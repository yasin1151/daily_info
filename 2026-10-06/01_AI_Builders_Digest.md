
All content extracted. Feed is fresh (generated 2026-10-05). Composing the digest now.

**AI Builders Digest — 2026-10-06**

本期主线很清晰：一批做 agent 产品的人在同一天里，从不同角度谈同一件事，就是「模型变强之后，工具链和组织的瓶颈转移到了哪里」。OpenAI 的 Codex 负责人给出 28 天连续交付承诺，Vercel CEO 说 agent 已经改写了编程语言选型的经济学，播客里则有一位用自研 agent 平台改造传统保险公司和银行的人，给出了相当罕见的量化结果。

---

## 一、X / 推特

**OpenAI Codex 与 ChatGPT 负责人 Thibault Sottiaux（thsottiaux）**
高赞（2.07 万赞）的一条承诺：「接下来 28 天里，我们每天要么交付一个对大多数 codex/work 用户来说是明确改进的功能，要么就做一次彻底重置。让改进开始吧。」
为什么值得关注：这是 OpenAI 对 Codex 产品节奏的公开对赌。28 天日更或重置，等于承认前一段的迭代速度不及预期，接下来一个月是观察 Codex 产品方向（尤其是 work 与 code 两条线怎么收敛）最密集的窗口。
https://x.com/thsottiaux/status/2106845241357824205

**Vercel CEO Guillermo Rauch（rauchg）** 连发三条，合起来是一个判断：**agent 改写了工程决策的成本函数。**
- 关于 Rust：他明确站 DHH，说 Vercel 早就在「Rust 化」，但 Turborepo 从 Go 迁到 Rust 的 ROI「内部其实很有争议」，因为「写代码的是人，即使我们知道 Rust 是更好的选择」。现在不同了：「过去对『人最友好』的选择，不再必然是对『生意』最友好的选择。」他认为 Rust 也不是终点，因为「Rust 本身是在 agent 这股超音速海啸之前设计的」。
  为什么值得关注：这是一个一线基础设施公司在公开承认，AI 正在重排「哪种语言/工具值得投入」的算法。对任何自研引擎团队来说，这是选型逻辑层面的变化，而不只是效率提升。
  https://x.com/rauchg/status/2106863842450133114
- 模型越快，harness 的开销占比越高；下个版本会改进 session 存储与检索，并在 libfx 上解锁云端的 durability。
  https://x.com/rauchg/status/2106885457212825983
- 他自己的新项目：「README 完全手写，因为它是给人看的；文档内部用『AI English』，因为那是给 agent 看的。」他把这条称为「让世界变好一点的小规则」。
  为什么值得关注：这是 agent 工具链里一个正在成型的实践分层，人读的入口归人，agent 读的中间层交给 AI 写。
  https://x.com/rauchg/status/2106848085267902815

**Box CEO Aaron Levie（levie）** 谈 AI 创造的新岗位：「我们已经开始看到 AI 创造了什么样的新工作。把 AI 部署进经济里需要大量技术工作和周边服务，这带来了 AI 工程师、把 agent 落地到公司的 FDE、以及专门做 AI 部署的服务公司这些岗位。」他补充，官方统计还低估了大量「原本的数据、研究、软件岗位正在企业内部被重新定位到与 AI 相关的工作」上。
为什么值得关注：对「AI 到底消灭还是创造工作」这个问题，他给的是具体职位类别，而非立场表态，且点名 FDE（forward deployed engineer）是这轮最缺的角色之一。
https://x.com/levie/status/2106893015063421357

**Peter Yang（petergyang，AI 教程与访谈作者）** 两条值得看：
- 他认为 OpenAI 应该简化 ChatGPT：「我很高兴 OpenAI 开始专注把 ChatGPT 简化，因为它已经变成一团乱麻（抱歉）。」他列出要合并的东西：Work 与 Codex、Spaces 与 Pages 与 Sites、以及模型和 effort 选择器。他的 hot take 是：「整个 Work 的发布是个错误。就像 Claude 把 Cowork 收回了 Chat 一样，我不认为 Work 需要一个独立品牌。」
  为什么值得关注：这是产品线在快速试错后「回撤收敛」的一个外部证据，和上一条 Codex 的 28 天承诺可以互相印证。
  https://x.com/petergyang/status/2106926956554195018
- 他问 Granola 联合创始人 Sam：用户跳过你的 UI、直接用 MCP 完成任务，你什么感受？对方回答（原话）：「作为一个 UI 设计师，这确实会有一点伤感。我们一开始抗争过，觉得必须把所有人都留在 Granola UI 里。但一旦你做成了足够大的企业，你就不可避免地会有一堆内部工具。如果 Granola 不跟这些内部工具好好配合，那就根本进不了场。现在我们接受了一个事实：对很多工作流来说，用 Granola 最好的方式就是采集上下文，然后通过你们内部的 agent 去使用它。」
  为什么值得关注：这是「agent 时代 SaaS 的 UI 会不会被 MCP 吃掉」这个问题，来自当事产品创始人的诚实回答，比任何分析师的观点都更有价值。
  https://x.com/petergyang/status/2106897211766530299

**Zara Zhang（zarazhangrui）** 观察模型的长时任务能力：「Opus 5.5 就那样安静地跑出去二十分钟以上，然后带回一个完整的杰作。」
为什么值得关注：长时自主执行正是 coding agent 与自研引擎最关心的能力指标，这是一条来自日常使用的体感记录。
https://x.com/zarazhangrui/status/2106876921082712250

**Dan Shipper（Every CEO）** 谈持久化 agent：「这几周 dot 已经成了我接触 AI 的主要界面。我的 dot 叫 boo……我打赌一年后我还会以这种方式和 ChatGPT 交互，也就是当作一个常驻的持久 agent，但 boo 会消失。这很像早年 OpenClaw 的日子，我们很喜欢那些 Claw 的个性小怪癖，但一旦有功能上更强的东西出现，我们立刻就丢掉了它们。」
为什么值得关注：他给出的判断是「持久 agent 的交互形态会留下，个性化外壳会被替换」，这正是 agent 工具链该押注的部分。
https://x.com/danshipper/status/2106892868564431255

**Matt Turck（FirstMark 投资人）** 引用 Goodfire 的 Eric Ho：「AI 里最被圈外误解的一点是『模型是长出来的，不是造出来的』，我们并不真正知道它们如何工作，所以对可解释性的需求非常紧迫。」
为什么值得关注：LLM 基础设施层面，可解释性仍是未解的核心问题。
https://x.com/mattturck/status/2106821381765956044

**Peter Steinberger（steipete，OpenClaw 与 OpenAI）** 简短发布：「bug 修复与性能改进。」（OpenClaw 本体更新）
https://x.com/steipete/status/2106796559400882209

**Garry Tan（YC CEO）**：「当所有人都在造同样的 primitives 时，这恰恰说明这些需求只会从此刻开始变得更强烈。而我们最终会收敛到那个正确的 OS 上。」
https://x.com/garrytan/status/2106901111106097210

---

## 二、播客

**No Priors：重塑老牌公司，与 Sequence Holdings 联合创始人兼 CEO Michael Lee**
链接（本期为具体视频）：https://www.youtube.com/watch?v=TCpRwJBQvW0

**核心要点**：真正的 AI 转型不是「给流水线上每个人发一台小机器」，而是重新设计组织本身；而能做这件事的既不是企业自己（招不到也留不住人），也不是咨询公司（激励结构决定它只能做增量），所以需要一种新型的所有权结构。

**背景**：Michael Lee 出自高盛、Apollo、Lone Pine（在 Lone Pine 管理私募业务时很早就覆盖 AI），二十个月前创立 Sequence Holdings，一个永久控股公司，专门收购传统企业、再配一支前沿工程团队把它们重造成行业领导者。刚宣布了迄今最大的一笔 AI take-private：与 Dell 家族办公室一起，以 77 亿美元私有化保险经纪公司 Baldwin。

**值得关注的内容**：
- **用人话解释他的框架**：他认为服务业公司优化的是「进你的钱包、留在你的钱包、扩大你钱包里的份额」，天生指向增量改良，改不了组织的激励和人员结构；而软件产品的基因决定了它只能卖「今天这个工作流」，卖不了「还不存在的新工作流」。所以只有所有权能对齐长期利益。
- **一个很反直觉的判断**：「每个公司都有一个被歌颂的人格类型。」他举例 Blackstone 被歌颂的是投资人，所以在「alpha 来自工程和 AI」的世界里，你需要把被歌颂的对象改成工程师。他说 Palantir 本质上就是「聚合了世界级工程师、并歌颂工程师，然后包装起来卖给拿不到这种人才的组织」。
- **自研引擎细节（对做工具链的人最有价值）**：他们的平台叫 **Atlas**，四层结构：数据本体（data ontology，把业务用代码定义清楚，让模型「读得懂」这家公司）、agent builder（构建基于 ground truth 的高性能 agent）、**Lattice**（orchestration 引擎，用 agent 把工作流编排起来）、顶层 **Artifacts**（应用构建器）。他们的观察是：把业务拆到原子层级，80% 是同质的，20% 才是垂直行业特有的，所以核心基础设施可以在不同被投公司间复用。
- **量化结果**：在 BankSouth 投入六个月后，消费贷核保的耗时**下降 94%**，平均贷款全流程从 **30 天缩短到 11 天**；今年 Q2 相对 Q1 贷款量翻倍，且**没有改变核保标准**，反而用更小的核保团队接住了全部量（少掉的一人是一个退休、一个调去了前台）。他特别说明贷款量翻倍「纯粹是运气」，不敢归功于 Sequence。
- **最硬的一句原话**：「我们内部有个玩笑：在 Sequence 我们有两个问题，一个是工程问题，一个是人类工程问题，而人类工程问题比工程问题难得多。」

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
