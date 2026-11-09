
**AI Builders Digest — 2026-11-10**

今日共 10 位 builder 更新（21 条）、1 期播客。最值得花时间的是 Latent Space 这期斯坦福 AI 原生工程课，几乎就是一份 agent harness 的自研路线图。

---

## X / Twitter

**Box CEO Aaron Levie —— agent swarms：生产力上限消失**
他把当前变化概括成一句话：从"你打字、AI 回一句"的对话式产出，转向"你设定一个问题、一群 agent 分头做完任意大的工作量"。收益从 20-50% 变成"没有明显上限"。已经发生在 coding，接下来是安全（更多 agent 审更多东西）、生命科学，以及任何"电脑上的工作能被并行化"的领域。他的判断是人的直觉还没跟上：我们习惯"投入时间 ≈ 产出质量"，而这个相关性正在被打破。
https://x.com/levie/status/2119592025440092192

**同一位，另一条更实操：每 3-6 个月回头重试一次当年失败的事**
过去半年模型在 computer use / tool use、context rot 减轻、推理、多模态、领域专精上的进步，让"只要有 API 的东西，agent 就能接管"成为默认假设。这意味着不必让模型"凭空生成一切"，而是让它去调用现有系统——安全 agent 用现成的数据源和 cyber 工具、IT agent 跨软件栈执行流程、架构 agent 用 CAD。反过来：今天不 agent-friendly 的工具，会被 agent-friendly 或 OSS 的同类替换掉。
https://x.com/levie/status/2119502716770902234

**OpenAI Codex 产品负责人 Nan Yu（前 Linear 产品负责人）——选"最笨"的架构，而不是"最简单"的**
"Simple is something you iterate to. Dumb is the correct starting point." 他的论点：架构、设计都该选能跑通的最笨方案；聪明方案的代价是用户也得跟你一样聪明才看得懂。另一条同样锋利：软件在"你知道要做什么"时变得很容易，在"你不知道"时变得很难——没有清晰度，你会烧很多钱产出一堆垃圾；而在 AI 之前你至少什么都发不出来，那算进步。
https://x.com/thenanyu/status/2119493015190249556
https://x.com/thenanyu/status/2119462224721002560

**YC 总裁 Garry Tan —— 你想要一个自己的软件工厂**
他提到 gstack-evals 复现了一篇关于 Jevons 悖论（AI 让写码变便宜，需求反而暴涨）的文章，结论可复现，且 particle-1 表现更好。另一条：一旦意识到软件在前沿模型下如此易改，现有产品的那些 bug 就变得难以忍受，同时"个人即时软件"（just-in-time software）会变成必然。
https://x.com/garrytan/status/2119624260675350605
https://x.com/garrytan/status/2119615647592395037

**Zara Zhang —— "vibe coding" 这个词该退休了**
她说自己几乎不用这个词了，因为它暗示你没投入心力、产出是 AI slop；但很多人用 AI 写码时是掏心掏肺的，两者并不矛盾，需要一个更好的词。这条 182 条回复，说明这是社区真实的语义争夺点。
https://x.com/zarazhangrui/status/2119592080318341128

**设计师 Ryo Lu（做过 Cursor、Notion、Stripe）——当什么都能做时，我们还知道自己想要什么吗**
在 aiDotEngineer 上海站的完整演讲，所有 slide 手工做在 Keynote 里，中英双语字幕。704 赞，讲的是能力过剩之后"意图"变成稀缺资源，和 Levie 那条正好互补。
https://x.com/ryolu_/status/2119586846657454152

**Vercel CEO Guillermo Rauch —— 用 WebGL2 + Web Audio 做了一台物理级黑胶唱机**
不是 AI，但今天技术圈传播最广的一条（2200+ 赞）：把歌曲转成纹路的物理形状，模拟唱针每秒 38.4 万次划过沟槽，直接输出"这段运动在唱头里会感应出的电压"，所以爆豆声、抖晃、内圈变闷都是仿真副产品而不是音效贴图。代码开源可 remix。
https://x.com/rauchg/status/2119536313712230802

---

## Podcasts

**Latent Space：[One Million AI Engineer Special] How Stanford Teaches AI-Native Engineering — Mihail Eric, Monaco**
https://www.youtube.com/watch?v=dpY7YzZo4kE

**Takeaway：** 斯坦福这门爆火的课（CS 146 "Modern Software Developer"）第一周就让学生自己写一个约 200 行的 agent harness，然后用 MITMProxy 拦截真实 Claude Code 的请求，把自己的循环和生产级的 system / plan / compaction prompt 逐条对照。学的不是"怎么用 AI 写码"，而是"读懂一个 agent 框架的设计取舍"。

**十周结构**：① harness 内部，从零写 coding agent；② context engineering + tool design + MCP；③ skills；④ agent 配置、hooks、subagents；⑤ agent-ready 代码库；⑥ agentic code review；⑦ 安全；⑧ background agents；⑨⑩ 客座 + 团队基建（LLM gateway、MCP portal、软件工厂）。作业形态今年变了：不再是 9 个教学型小作业，而是向 Warp、Vercel 的 Eve 等 OSS 伙伴的真实仓库提 PR，由 maintainer review 给反馈；capstone 拿 YC 的 request for startups 当选题种子。

**几个可直接迁移的判断：**
- Claude Code 的 system prompt 是所有 coding agent 里最长的，约 2 万 token。他强烈建议做一次 MITMProxy 抓包："You'll be shocked."
- harness 里的硬编码规则是"模型能力不足的补丁"，模型升级后要主动删。Git 该怎么用这类内容已经沉进权重，"It's actually expected to be more kinda captured in the models, like the model weights itself." 示例留太多就是过度约束。
- 多 agent 的真问题不是编排，是 context 反复 expand/contract；给太多上下文，subagent 会把一句随口评论当铁律——"they're gonna overtune to some random one-off comment"。
- skill 最难的是触发边界："the worst part is when a skill triggers when you're not expecting it to." 更耐久的定位是承载组织级最佳实践，而不是随手 prompt 的替代品。
- 自建 vs 采购的判据是 "you buy to learn and you build to keep"：code review 继续用 Devin，background agent 平台自研 Monocoder（跑在 coder.com 上）。

**金句**：*"You write prompts that write prompts."* / *"if you're not holding yourself accountable to delivering real products, you're just screwing around with LLMs."*

---

关于本次推送：Matt Turck 的两条是马斯克相关的玩笑、Peter Yang 的一条是照护家人的访谈片段和一条与行业无关的观察、Nikunj 的是旧金山社交礼仪、Swyx 的三条都是转推指路——按你的偏好都滤掉了，没有硬凑。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
