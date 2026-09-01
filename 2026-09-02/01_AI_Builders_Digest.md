
All content reviewed. Dataset is small enough (10 builders / 19 tweets / 1 podcast) to assemble directly. Composing the digest:

---

# AI Builders Digest — 2026-09-02

## X / Twitter

**Nan Yu — 前 Linear 产品负责人，现加入 OpenAI 负责 Codex 和 ChatGPT**

在 Linear 工作 4 年后宣布加入 OpenAI，加入 Codex 和 ChatGPT 产品团队，称要把在 Linear 学到的软件工程工艺带到下一个阶段（3062 赞）。

值得关注：Linear 是开发者工具产品力的标杆，OpenAI 持续从顶级产品公司挖人，说明 Codex 在从"模型能力展示"转向"正经产品打磨"。

https://x.com/thenanyu/status/2094427243565269107

**Guillermo Rauch — Vercel CEO，两条**

1.「Coding tokens 就是基础设施」。他说企业发 coding token 的方式就像丢一把 AWS key 让人随便开机器——从不治理、优化、观测用量和成本。但核心基础设施从来不是这么管的。

值得关注：这是当前最实际的 Agent 成本治理论点：谁先做好 coding token 的 governance/observability，谁就掌握了企业 AI 预算的入口。

https://x.com/rauchg/status/2094523399280435630

2.「你的下一个设计系统是 Markdown」。Vercel 发布 DESIGN.md，宣称用它解决 AI 时代最难的问题之一：slop（AI 生成的平庸内容），让大型组织真正规模化"设计品味"（2443 赞）。

值得关注：AI 生成能力泛滥后，表达/品味的约束层成为新的产品竞争点——用可版本化的文本规范约束 AI 输出。

https://x.com/rauchg/status/2094541309579235680

**Aaron Levie — Box CEO，两条**

1. 开源权重模型越来越强 + post-training 基础设施成熟商业化后，手握大量数据的公司可以训练自己的专属模型了——以前唯一的出路是把数据授权给外部训练。

值得关注：数据资产的价值再分配信号——大企业自训模型的门槛正在从"能不能"变成"值不值"。

https://x.com/levie/status/2094650992818274514

2. 随着 AI 安全事件增多，我们需要最先进的 AI agent 来检测和防御安全问题；前沿模型在攻防上仍领先，但开源模型正在快速追赶。

值得关注：AI 攻防的 agent 化是确定方向，开源模型的 cyber 能力差距在快速缩小。

https://x.com/levie/status/2094545525102235844

**Garry Tan — YC 总裁兼 CEO**

开源了 GBrain 的新 eval：宣称其 retrieval-for-AI-agent 层在没有 LLM-in-loop 的情况下读回记忆达到 SOTA，并新增了"从 agent transcript 保存记忆"的 eval——从对话记录提炼记忆被认为是给大脑扩容的最佳方式（403 赞）。

值得关注：agent 记忆的读写 eval 正在成型，这是 Agent 工具链里最缺标准的一块。

https://x.com/garrytan/status/2094462971598754010

（另：他直言 Circleback 比 Granola 强得多，因为 Granola 连"多人发言消歧"都不支持——AI 会议纪要产品的真实槽点，603 赞。https://x.com/garrytan/status/2094465505142960443）

**Thibault Sottiaux — OpenAI Codex 负责人**

发帖征集：「如果你还没试过 Codex，但曾经考虑过——阻止你的是什么？」2344 赞、1816 条回复。

值得关注：回复量说明编码 agent 的采用障碍是社区最热的议题之一，OpenAI 在主动收集拒绝使用的理由（价格、信任、习惯、还是产品缺陷？）。

https://x.com/thsottiaux/status/2094588317245509959

**Madhu Guru — Meta AI 高级总监（前 Google Gemini/Veo 负责人）**

给 PM 的建议：理解模型前沿对你的产品有巨大 alpha——你应该比前沿实验室研究员更清楚：每个尺寸档位的模型今天能做好什么、在哪里失败、用什么 workaround 绕过失败。

值得关注：模型能力边界认知正在变成 PM 的核心竞争力，评估与选型是产品层最值钱的能力。

https://x.com/realmadhuguru/status/2094591503981281503

**Dan Shipper — Every CEO**

AI 拟人化：有助于我们理解、预测 AI 时是好事；用来制造恐慌、渲染意识、抬高道德地位时是坏事。反对拟人化的人，反对的其实是后者的滥用。

值得关注：给"AI 拟人化"之争提供了一个务实的中立框架，避免站队式争吵。

https://x.com/danshipper/status/2094406185109647580

## Podcast

**Training Data — Rich Sutton 与 Khurram Javed：为什么 AI 模型停止学习，以及如何重新开始**

The Takeaway：今天的 LLM 是"训完就死的化石"——部署后权重永远不再更新；真正的智能必须持续从真实世界经验中学习。

Rich Sutton（强化学习之父、《Bitter Lesson》作者，曾患癌仍坚持研究）与合伙人 Khurram Javed 创办 Oak Lab，核心观点极具反主流色彩：

- 他坚持「我不奇怪，是这个领域奇怪」——学习本来就是持续的，"continual learning"这个说法本身就意味着行业默认了模型不学习。
- 对合成数据直接开炮：「合成数据是个大错误」。世界远比任何模拟复杂（"Big World Hypothesis"），你无法为"别人脑子里在想什么"造出合成数据。经验数据永远比人造数据多。
- 对当前 LLM 的判词：「它们的权重从不变」。预训练、后训练做太多，一旦上线就停止学习——唯一的例外是 Cursor Tab、Composer 这类用海量用户数据持续更新权重的产品，但绝大多数场景做不到。
- Oak Lab 的药方是算法级修补（不是工程问题）：逐权重步长优化 + 发表在 Nature 的 continual backprop + 特征空间的 generate-and-test，让模型边用边学、同时学会"如何学习"。
- 野心：万亿参数模型 20 瓦功耗（5-10 年内靠摩尔定律两个数量级达成），同一套设计、无数个拥有不同经验的"mind"。他还补了一句：别怕人类会变得无关紧要，「世界会变得对人类更精彩」。

原话：「Their weights never change.」（它们[LLM]的权重从不变。）

值得关注：Sutton 是少数从第一性原理质疑 scaling 范式的重量级人物，这篇访谈把"LLM 停止学习"从抱怨变成了可执行的研究纲领，对自研引擎/Agent 长期架构有直接参考价值。

https://www.youtube.com/playlist?list=PLOhHNjZItNnMm5tdW61JpnyxeYH5NDDx8

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
