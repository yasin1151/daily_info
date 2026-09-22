
Feed is fresh (1 day old): 11 builders / 23 tweets, 0 blogs, 1 podcast. I've filtered out low-signal posts (Garry Tan politics, Dan Shipper teasers, Amanda Askell musing, image-only tweets) per the focus instruction. Assembling the Chinese digest now:

---

# AI Builders Digest — 2026-09-09

本周提要: OpenAI 进入 "Astra" 发布周,社区情绪明显回春;Replit CEO 断言"功能上与 AGI 无异";Vercel CEO 押注 agent skills 与本地推理;开源圈开始抱怨 agent 间协作还是太蠢。

## X / Twitter

**1. OpenAI 进入 "Astra" 发布周,社区情绪回春**
OpenAI Codex/ChatGPT 团队的 Thibault Sottiaux 连发高赞推:"I think I can officially say: we are so back"(1.4万赞)、"All reset for everyone. Enjoy the week with Astra"(8803赞)。另一条提到他正翻一份 28 页的 deck,Codex 在逐条追踪本周所有新发布。
为什么重要: 推文没给产品细节,但强烈暗示 OpenAI 本周以 Astra 为主题做了一波集中发布,且和 Codex/agent 能力直接相关。这是观察 OpenAI 下一步动作的关键窗口。
https://x.com/thsottiaux/status/2097193293532848288

首批真实用户已开吐槽: AI 教程作者 Peter Yang 说 "Astra seems worse at triggering my skills automatically and following my instructions in them",即 Astra 的自动技能触发和指令遵循不如预期。这个抱怨直指 agent 可靠性老问题,对做 agent 工具链的人有参考价值。
https://x.com/petergyang/status/2097095296862036404

**2. Replit CEO Amjad Masad: 没到 AGI,但功能上与 AGI 无异**
原话:"I don't think we've reached AGI but what we have is functionally indistinguishable from AGI. Because we have a relentless programmer that doesn't get bored or tired... any problem that can be casted as a coding problem is virtually solved."
解读: 当你拥有一个不知疲倦、不会无聊的程序员,凡能"编码化"的问题基本等于被解决。言下之意: 真正的约束不再是写代码,而是把问题清晰表达成可编码的形式。来自 coding agent 产品一线 CEO 的判断,做工具链定位时值得对照。
https://x.com/amasad/status/2096936109817135331

**3. Vercel CEO Guillermo Rauch: 软件工程的新瓶颈是 review/testing/QA**
两个动作:(1) 宣传 agent-browser 的高质量视频录制能力,"Your software factory needs high quality video recording",并称正把自动化 review、测试、QA 的经验做成更多功能;(2) 个人开源资助 v2: 35 位贡献者每人 $1000,主题直指 "Agent skills & tools"(他说 skills 已成为一种有价值的软件形态)、Local AI、性能与高质量基础组件,强调纯个人、无条件。
为什么重要: 头部基建 CEO 判断下一个瓶颈在工程流程自动化,并用真金白银押注 agent skills 和本地推理生态,和自研 agent 工具链方向强相关。
https://x.com/rauchg/status/2097134278358548658
https://x.com/rauchg/status/2097116011384426516

**4. OpenClaw 的 Peter Steinberger: agent 之间的 PR 协作还很蠢**
原话:"Did a PR to one of our upstream projects and they requested some minor changes. What's even the point with this workflow? You already wrote the prompt, why make me ping my agent again so your agent then merges?"
场景: 他给上游项目提 PR,对方要求小改,但两边实际都是 agent 在跑,却还要人工来回 ping 各自的 agent 才能推进。痛点很真实: agent 驱动的开源协作缺少"agent 对 agent"的异步闭环,这正是下一层工具的机会。
https://x.com/steipete/status/2097091456234111377

**5. Box CEO Aaron Levie: AI 就业的叙事目前反着演**
(1) "The AI jobs prediction so far is playing out the opposite of what many thought." 他认为原因是 AI 把自动化带进了没有"有限需求"特征的领域,agent 仍需要人类 operator 和 oversight 才能产生价值;程序员、律师没被大规模替代,反而催生网络安全、FDE、agent operator、非软件领域工程师等新岗位类别。
(2) 提醒创业者: 要按"能力与可用 token 再提升几个数量级"的愿景来规划产品,最好的机会是今天勉强能交付、完整使命在当下技术下近乎不可能的那些方向。
https://x.com/levie/status/2097004960307449937
https://x.com/levie/status/2097189559712837770

**6. FPV Ventures 的 Nikunj Kothari: 构建变简单后,"做什么"成了瓶颈**
"As building gets easier, what to build becomes the important bottleneck... the good ones are extremely well setup for the AI native organizations." 与 Levie 的判断互相印证: 供给端已不是限制,稀缺的是需求判断和"为 AI-native 组织设计"的能力。
https://x.com/nikunj/status/2096963347359150348

## PODCASTS

**AI & I by Every: A $10B Hedge Fund's AI Playbook(Best of the Pod)**
Dan Shipper 对话 Walleye 对冲基金(约百亿美元 AUM、400 人)的 owner-operator CEO/CIO Will。这位量化加基本面多策略的掌舵人给全公司发过一封"AI-first memo",原话:"Using ChatGPT is not cheating. That's a non applicable idea from academia... As a hedge fund, we should be ashamed to leave money on the table by ignoring tools that make us faster, smarter and more effective." 另一句:"Not using these tools is like refusing to use the Internet in 1995 because it wasn't perfect."
落地比口号实在: 全员强制 AI 培训、不分部门;设跨部门 "AI Senate" 用户小组;自建内部研究工具 Current,基本面研究员人手一个,财报季用量暴涨,已有 50 多家外部机构排队申请当 beta;用 LLM 处理非结构化数据做交易信号已多年;所有 Zoom/会议全量录音存档,他自嘲是 "the Borg";个人用 AI 起草沟通,单封邮件从 4-5 小时压到 15 分钟。他的框架: AI 是发动机,人还是要造飞机 ("a jet engine won't fly by itself. You still got to hook it up with a plane")。
为什么值得听: 难得的运营者一手视角,不是 VC 空谈,讲的是大组织里 AI 工具和内部平台怎么真正铺开,以及"AI-first 文化"从顶层如何落地。(注: 该集为 8/26 发布的 Best of the Pod 重播,链接为频道播放列表。)
https://www.youtube.com/playlist?list=PLuMcoKK9mKgHtW_o9h5sGO2vXrffKHwJL

---
Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
