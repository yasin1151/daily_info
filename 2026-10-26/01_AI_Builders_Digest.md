
AI Builders Digest — 2026-10-26

数据截至 10 月 25 日（feed 生成于 2026-10-25）。今日 11 位 builder、23 条推文、1 期播客，无官方博客更新。

---

## 一、播客｜本期最值得完整听的一期

**The MAD Podcast（Matt Turck 主持）：Diogo Almeida 讲 JEV —— 做决策、不写字的那种 AI**
https://www.youtube.com/@DataDrivenNYC/videos
（注：feed 只给了频道页，没有单集 watch 链接）

**他是谁**：Diogo Almeida，TypeSafe CEO，JEV 模型作者，RLHF 的共同发明人之一。公司隐身两年，此前融资不到 4000 万美元；发布三周，宣布 8.7 亿美元 A 轮、估值 75 亿美元，发布视频 4000 万播放，日活约百万。

**核心观点（人话版）**
- **JEV 不是聊天模型的替代品，是另一类东西**。它不吐文字，吐概率：这封邮件算不算紧急、要不要升级、0.85 分还是 0.92 分。他把这叫做「machine-native AI」，System 1 只是实现细节。
- **为什么值得这么做**：他认为 RLHF 把模型调成了「讨人喜欢的聊天对象」，代价是谄媚、过度拒答、风格趋同（mode dropping），甚至让模型在判断上「略微变笨」。而 RLVR 能刷爆所有 benchmark，"95% 爱因斯坦，5% 憨豆先生"——**如果模型不告诉你哪次是憨豆先生，你就没法自动化任何东西**。原话："RLVR hasn't really changed automation."
- **最锋利的一段是「不可组合」**：软件之所以强大，是把一个可靠的小单元（bit 比较）做到足够可靠，然后复制、堆叠、让别人在上面再盖一层。而今天的 AI 是 "incredibly noncomposable. It plays nicely with nothing except other AI. And that's kind of tragic." 你想做邮件助理，只能在 system prompt 里用自然语言堆越来越长的 if 规则，复杂度一升错误率就升，"你只是在祈祷模型别犯那个错"。
- **他的替代方案**：把每个判断拆成独立的分类器——可测量的 smart if 语句。好处是**可读、可测、不会遗忘、可回填**（漏判了就把样本加进去）。"Code is kind of like the roller coaster tracks." 他明确说这不是「窄」，分类是 AI-complete 的。
- **对「只会抄个接口」的评价**：他自己第一周就做出了类似的东西，"so unbelievably dumb that it was embarrassing"。他说已经有公司在他们之前发过版本，"it was worse than nothing"；判断抄袭者「在可靠性上大概落后几年」，但他坚持先测再说。
- **点名表扬 OpenAI**：几天前发的 Decisions API「没带 benchmark，所以在我这里比别人强」。
- **两个非主流立场**：不认为我们在通往 RSI 的路上（举了编译器领域优化到极限最后整个方向被扔掉的例子，Amdahl 定律）；但认为 AI 的「冬天」已经被绕过去了——因为过去的问题是"AI 惊人地聪明，却对自动化惊人地没用"，"chatbots 感觉很魔法，但它们对世界的改变小得奇怪"。

**为什么和你相关**：这段几乎是给自研引擎/Agent 工具链写的设计评审。它主张的不是「换更强的模型」，而是**把自然语言 prompt 里的隐含判断，降级成显式、可度量、可回归测试的判定节点**。如果你正在纠结 harness 里该用 prompt 还是用代码卡逻辑，这期是正面回答。另一个可带走的指标口径：他说未来的核心不是 intelligence per second，而是**intelligence per dollar**。

---

## 二、X 上的信号

**Thibault Sottiaux（OpenAI，Codex & ChatGPT）——Codex 更新已全网推送**
"It is all propagated. Enjoy some mad codexing tomorrow. Fun week ahead too." 另有 "By midnight PST"。
https://x.com/thsottiaux/status/2114237083652882932
→ 三条连发（6524/1470/1398 赞）指向一次 Codex 相关更新完成分发、太平洋时间午夜前生效，且本周还有后续。他没说改了什么，只能确认节奏。如果你在跑 Codex 工作流，今天值得实测一遍。

**Guillermo Rauch（Vercel CEO）——「过度指导 vs 指导不足」才是第一技能**
"There'll be times where you over-guide the AI... There'll be times where you under-guide the AI. How well you manage this superpower is the #0 skill I look for."（2087 赞）
https://x.com/rauchg/status/2114085432749347086
→ 这是当下 agent 工具体验的真实痛点：给少了跑偏、给多了锁死。他把这个张力直接定义为招聘第一标准，说明「控制粒度」已经被当成工程能力而非 prompt 技巧。
另一条也值得看：他注意到模型爱用 gate / evidence / culprit / durable / provenance / contract 这类词，认为这源于「大部分工程其实是调试和审计」；还顺势提出是否存在一种「最小可用英语」（参照 ASD-STE100 只用约 900 词）。
https://x.com/rauchg/status/2114164830403989880

**Aaron Levie（Box CEO）——安全 agent 的量级会爆**
"我们很快会有比今天多 1000 倍的 token 流过安全 agent"。他描述了 agent swarm：扇出、调用任意安全工具、试各种攻击变体、读日志、批量判断企业数据风险等级。
https://x.com/levie/status/2114187326406766604
→ 他强调这能力「过去几个月才出现」，前提是长时运行 agent 和 computer use 够用了、模型在安全领域训得够深。对 Agent 工具链的含义：多 agent 扇出 + 工具编排不再是 demo，而是安全预算的新科目。

**Ryo Lu（前 Cursor / Notion / Stripe 设计师）——一篇反对「无摩擦」的长文**
"struggle together"：他回顾自己靠反复失败学会编程和设计，而现在"we ask. something appears. it works well enough. we move on."——结果是**我们学会了拿结果，却不理解它为什么work，而且因为结果看起来完整，很容易错过那些我们从未学会提出的问题**。他也写到协作的不适感，以及 agent 永远耐心、永远在场，"talking to it can feel easier than reaching toward someone who might misunderstand you"。最后一句是"or a comfortable kind of confinement, where everything responds to us but fewer things reach us?"（511 赞）
https://x.com/ryolu_/status/2114187405251219954
→ 今天 feed 里传播最广的反调，而且出自做 AI 编程工具的人自己。适合配着上一节播客一起读：一个说 AI 不可组合所以要把判断拆细，一个说 AI 太顺滑所以人会丢掉拆解的能力。

**Peter Yang——对一条影响 Claude 用户的消息表示惋惜**
"I had trouble believing this is true but shouldn't have doubted @ArfurGrok. Huge bummer for claude users. Anthony and Thariq are two of the best at listening to users."
https://x.com/petergyang/status/2114001125636768121
→ 他在转发别人的爆料，原文（被引推文）不在 feed 里，所以具体是什么变动无法确认，只能确认他点了两个以「听用户说话」出名的人。Claude Code 用户近期值得留意官方渠道，别只信转述。

---

## 三、简讯

- **Alex Albert（Anthropic Research）**在几条转发里点到同事的名字，其中出现 "Claude Managed Agents" 和 "Duet" 两个项目名——只是致谢列表，无细节，但 "Managed Agents" 这个命名方向可以留意。
https://x.com/alexalbert__/status/2114145588686233612
- **Nikunj Kothari（FPV Ventures）**：他把自己对 agent 演进的框架概括成 context → harnesses → judgement，说某篇帖子把这事讲得比他说得清楚。
https://x.com/nikunj/status/2113994081345126486
- **Aditya Agarwal（South Park Commons）**："being max AI pilled" 的副作用是自己开始格外珍惜和家人朋友的线下时间。"Let the agents cook (or not). But dear god, celebrate humans."
https://x.com/adityaag/status/2114135237806760097

已跳过：Swyx 的招聘贴、Garry Tan 的产品链接、Zara Zhang 的个人感慨、Peter Yang 的儿童阅读 App 推荐（自述非赞助但属产品推荐）、若干纯 @ 回复。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
