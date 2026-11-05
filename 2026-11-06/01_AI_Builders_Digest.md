
内容已全部取到（15 位 builder、30 条推、1 期播客，feed 生成于 2026-11-05）。以下是成品摘要。

---

# AI Builders Digest — 2026年11月6日

今天信号集中在两处：coding agent 正从「帮你写代码」变成「重写整个软件工程流程」；而做过 Claude Code 的那批产品人，正在流向 OpenAI。

## X / 推特

**Guillermo Rauch（Vercel CEO）：人类写的软件「又慢又漏」，AI 会把它全部重写**

原话：「most human-made software: Was really slow / Had many security vulnerabilities / Was under-specified and incorrect. AI will rewrite it all. Many times.」他的判断不只是提速，而是 AI 会形式化验证、压测、加固、补文档，「we are witnessing the true birth of software engineering」。
值得看的原因：这是 Vercel 自家 Security Reviews 上线后的表态，不是空谈 —— 他给的数字是 24 小时内识别 6,817 个漏洞、其中 580 个 critical/high、已有 1,411 个由 Agent 自动修好（免费到 11 月 10 日）。
https://x.com/rauchg/status/2118166970273292299
https://x.com/rauchg/status/2118152230260092940

**Cat Wu：Claude Code 的产品负责人跳去 OpenAI，带队 Core Products**

原话要点：「we'll build agents that have your back and your team's, and keep you in control」。她此前在 Anthropic 做 Claude Code，也待过 Dagster、Scale。
为什么重要：本周 coding agent 竞争格局最直接的人事信号，一条推 1.2 万赞。加上 Dan Shipper 吐槽「这些 OpenAI 新员工显然都读了我的 Codex 文章」，OpenAI 在 Codex 侧明显在加码产品。
https://x.com/_catwu/status/2118137612577968402

**Peter Steinberger（OpenClaw）：单个 agent 的用量限额还有意义吗**

原话：「As capabilities increase you want to work with and support an agent that represents your project, that runs loops and evolves your codebase. The humans merely curate the automations.」
为什么重要：直接指向自研 agent 工具链的下一形态 —— 不再是「人和一个 session 对话」，而是一个长期代表项目跑循环、演化代码库的 agent，人退到调度/编排层。限额、会话、上下文窗口这些以「单次交互」为前提的设计，都可能要重做。
https://x.com/steipete/status/2118116514700386439

**Swyx（smol.ai / Cognition / Latent Space）：thinkymachines 的 inkling 是「没有代价的蒸馏」**

原话：「3x faster 5x cheaper but evals SAME ON FRONTIERCODE 2 — this is distillation without tradeoffs. i think thinkymachines inkling is one of the most underrated base models in the world. expect to see a TON more of these esp on US pretrained models.」
为什么重要：3 倍快、5 倍便宜、前沿代码评测不掉分。如果这个结论站得住，coding agent 的成本结构会立刻改变 —— 不用再拿最贵的旗舰模型跑主力任务，蒸馏小模型可以顶上来，而且这类模型会大量出现在美国预训练模型之上。
https://x.com/swyx/status/2118208851506036989

**Amjad Masad（Replit CEO）：日本金融巨头 SMFL 的落地数字**

原话：「in just one week, with one person, completed a project that previously required six people working for six months.」
为什么重要：企业侧 agent 落地的量化样本。注意这是合作方宣传口径，实际效率提升要打折，但方向（一个人一周 ≈ 六人半年）和之前 Replit 自己讲的故事一致。
https://x.com/amasad/status/2118180254300688857

**Thibault Sottiaux（OpenAI，Codex & ChatGPT）：OpenAI 在组建网络安全团队**

原话：「We've assembled a world class cyber team and I'm excited for us to share more about our work over the weeks and months.」并公开招人（@clintgibler）。2,188 赞。
为什么重要：前沿实验室把「防自家模型被用于攻击」当成独立建制来投人，和安全评测、红队、agent 权限边界这条线直接相关。
https://x.com/thsottiaux/status/2118146794362405231

**Ryo Lu（前 Cursor 设计负责人）：当什么都能做出来，我们还知道自己要什么吗**

他在 aiDotEngineer 上海场讲的原话：「when we can make anything, do we still know what we want? i want tools that help us find our own answers, not skip the process of forming them. not just more output, but more room to think, care, and make together.」
为什么重要：做 agent 产品的人里出现了反向信号 —— 从「无限提升产出」转向「保留用户自己形成判断的过程」。这是对「一键生成一切」叙事的怀疑。
https://x.com/ryolu_/status/2118207967728451760

**Matt Turck（FirstMark 合伙人）：用户要的是「一个大脑」，不是一堆 app**

原话：「one central brain (AI) that can interact with me whether I text it or speak to it, whether I want to buy something or need support, and can actually do something helpful for me (agentic action) - 24/7, always in a good mood.」
为什么重要：Dialpad 收购 Ada 的投资人视角，企业 agent 的整合方向是收口到单一入口，而不是再造一个垂直 SaaS。
https://x.com/mattturck/status/2118010883754299884

**短讯**
- Garry Tan（YC 总裁）：「GStack's /review skill is actually useful for preventing bugs still」—— 自己造的 code review skill，自己还在日常用。
  https://x.com/garrytan/status/2118221083233206736

## PODCASTS

**AI & I by Every — The Inside Story of the 50 Who Built Modern AI（嘉宾：Kevin Roose）**

**Takeaway：这一代 AI 的关键决策大多发生在几封内部备忘和几次桌面谈话里，而不是发布会上 —— 而写这些历史的人，现在反过来用 agent 团队审自己的稿子。**

Kevin Roose 是前纽约时报科技记者、Hard Fork 前联合主持，现在和 Casey Newton 做 Machine Gods。他为写这本书访谈了约 150 人，其中 50 位是真正把现代 AI 建起来的人。他的结论不是「我们要完了」，也不是「全是泡沫」：「I don't think we're doomed. But we have a lot to do.」他认为没有什么被注定，当下几年的选择权重很大。

最反直觉的一段史料是 Dario Amodei 2017 年在 OpenAI 写的内部备忘「the big blob of compute hypothesis」。当时整个领域都在做窄模型 —— 想赢围棋就专门搭一套系统训到极致。Dario 的判断是全都做错了：应该堆「大块无结构的算力」，指向「预测下一个词」这种通用问题，然后相信智能会自己长出来。这份备忘在 OpenAI 内部重塑了路线图，LLM 那时甚至还不存在。

监管上他的判断很直接：短期内不会联邦立法，除非出大事 —— 而「等出大事再仓促立法」是美国一贯的响应模式。他主张的第一道门槛很朴素：像药企上市前必须做临床一样，模型对公众开放前必须通过标准安全测试（自主网络攻击、生物武器滥用）；第二步是需要某种「减缓前沿」的协调机制。他特别说自己几个月前还不相信能减速，是看到 Dario、Demis、Sam 这些人真的想给安全团队买时间才改观。

最有实操价值的是他自己的工作流：写这本书 450 页、一年完成，正文一个字没用 AI，但其余部分全上了。他把每章草稿丢进 Claude Code，跑一个 agent swarm，每个 agent 领一个身份 —— 一个 AI 怀疑论者（根本不信 LLM 有智能）、一个 AI 史学家（能纠正技术前史的错）、一个 Walter Isaacson 式的文体匠人（只关心叙事弧线和读起来是否愉悦），再由一个「主编 agent」汇总成一份改稿意见。这套「Council of Claudes」抓到过人和人类编辑都没抓到的事实错误。他的原话很值得记：「a couple years ago, we had to fact check the AIs, and now the AIs fact check me.」研究管理则靠 NotebookLM 把全部材料倒进去做检索和连线。

他还给了一个很好用的二分法：日常任务分「举重」和「开叉车」。举重的意义就在费力本身，把叉车开进健身房是纯浪费 —— 所以他不让 AI 读睡前故事给孩子，那是他自己必须做的事；而开公司那些法律、保险、文书流程，他乐意全交给机器。他自己现在的状态是「agents correcting my other agents，一团乱」，工具太多跟不上。

https://www.youtube.com/playlist?list=PLuMcoKK9mKgHtW_o9h5sGO2vXrffKHwJL
（注：feed 只提供该节目的播放列表链接，没有单集 URL，未做替换。）

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
