
All content extracted. Feed is fresh (generated 2026-09-10), 14 builders / 28 tweets, no podcast or blog items. Assembling the Chinese digest directly.

---

**AI Builders Digest 2026-09-11**

今日聚焦:coding agent 的经济学、OpenClaw 云端会话、Claude Marketplace 的企业分发,以及一轮关于「AI 替代率」的方法论争论。

**1. Thibault Sottiaux(OpenAI,负责 Codex 与 ChatGPT)**
今早出事故:一部分 banked resets(额度重置券)在 ChatGPT Work 和 Codex 里使用时没有完全生效。官方处理是,凡在受影响时间窗口内用掉的用户全部再补一张,并发邮件道歉。他另一条说,和研究团队争论新模型该叫什么名字是「人生一大乐事」,他们想出来的东西相当好笑。
为什么值得关注:重置券 bug 直接影响 Codex 重度付费用户,补发说明 Codex 是被当作核心产品在维护;而「讨论新模型命名」是典型的发布前信号。
https://x.com/thsottiaux/status/2097752790177370535
https://x.com/thsottiaux/status/2097912273264095536

**2. Aaron Levie(Box CEO)**
他连发两条产业判断。第一条:世界对 coding agent 的使用会远超所有人想象,会用来做全新品类的工具、给以前负担不起软件的公司做软件、用 agent 防网络风险、自动化生命科学和复杂数据工作流、升级遗留系统。核心逻辑是代码成本下降后软件用途变多,工程师杠杆大幅上升,结果是需要更多工程师而不是更少。第二条:AI 能力与 GDP 影响之间的鸿沟,答案在于「扩散」会比人们想的慢得多。他称之为公司物理定律,数据准备、流程再造、变革管理、对齐新工作流,一个都绕不过去,再加上等客户回方案、等许可证、药物研发要数年这类现实世界的速度。
为什么值得关注:两条合起来是对「AI 取代程序员」和「模型很强但宏观数据不动」的产业界正面回应,也点明了 to B agent 真正的落地瓶颈不在模型侧。
https://x.com/levie/status/2097920810543468551
https://x.com/levie/status/2097738533297689012

**3. Peter Steinberger(OpenClaw 创始人,现与 OpenAI 合作)**
OpenClaw 的云端会话终于跑得很快了,远程终端、WebVNC 以及用于 computer use 的 CUA 一起上了。另一条说,他两个月前推动的 Dashboards/Mini-Apps 已经取代了团队围绕 OpenClaw 自建的一大批自定义工具,现在一切都是一条侧边栏、一个 dashboard 或一个插件。
为什么值得关注:这是 Agent 工具链最前沿的一手实践。把浏览器操作、远程终端和可扩展 UI 插件体系合到同一个 runtime,基本就是「agent 操作系统」该有的形态,对自研引擎有直接参考价值。
https://x.com/steipete/status/2097935551735423464
https://x.com/steipete/status/2097880507753382201

**4. Claude 官方账号(Anthropic)**
Claude Marketplace 上线,首批入驻 CrowdStrike、Cursor、Factory、Gamma 和 Vercel。企业客户可以用原本的 Anthropic 采购承诺额度,直接购买更多 Claude 驱动的产品和 agent。
为什么值得关注:模型厂商把「采购承诺额度」变成了应用商店的支付通道。企业买生态产品的决策链路被大幅缩短,对做 agent 产品的团队来说是多了一条现成分发渠道。
https://x.com/claudeai/status/2097718980437831935

**5. Guillermo Rauch(Vercel CEO)**
Vercel 与 Benchmark 合办一场叫 AI Benchmarks 的活动,自称是 SF 史上最名副其实的活动名,主题是评估模型、引导世界走向能力、真相与效率的公司。他另一条提到,过去六个月光是价格下调、费用取消和结构优化就有 8 次,外加 16 个模型折扣。
为什么值得关注:benchmark 正在长成一个独立软件品类;同时推理成本仍在快速下降,这是 agent 大规模铺开的先决条件。
https://x.com/rauchg/status/2097837950612717804
https://x.com/rauchg/status/2097828203658383674

**6. Dan Shipper(Every CEO)**
他对一份 AI 就业影响报告提出方法论质疑:报告假设工作可以拆成任务,并且自动化创造的人类任务永远只是被自动化任务的一个比例,也就是预设自动化只会减少人类劳动。他反驳说自动化经常创造出成倍的人类工作。他还借维特根斯坦和海德格尔的角度讲,一份工作是「看世界和在意世界的一种特定方式」,编辑会注意到护士不会注意的事,你关心什么决定了你注意到什么、什么值得做。这些没法被完整拆成任务清单,而它恰恰是工作的一部分。
为什么值得关注:这是对「AI 替代率」类测算最锋利的一击,也解释了为什么自动化落地后工作量常常反而变多。
https://x.com/danshipper/status/2097758891270697101

**7. Peter Yang(AI 教程与访谈作者)**
他在追问 Codex 的移动端:ChatGPT Work 和 Remote Codex 线程什么时候能上手机,目前似乎只有 Chat 线程支持。他另一条分享了一个测模型思考能力的小技巧:把一整张图直接贴进 ChatGPT,让它用极其直白的措辞指出正在拖累你的盲区。
为什么值得关注:一句话点出 Codex 移动端缺口,说明 Codex 已经进入被当日常主力工具用的阶段。
https://x.com/petergyang/status/2097763574886375832
https://x.com/petergyang/status/2097729250505966046

**8. Sam Altman(OpenAI CEO)**
他发文欢迎 Paul 加入,感谢他长期以来在 AI 安全上的贡献,表示很高兴再次共事。另一条是回应某条消息:「这确实会很糟,但我们会先保证给客户提供优质服务,直到重新把局面控制住。」
为什么值得关注:后半句「先保客户」通常出现在算力紧张或服务降级的语境中,是 OpenAI 资源压力的一次侧写。该条的上下文未收录在数据里,这里只呈现原话。
https://x.com/sama/status/2097776310940569783
https://x.com/sama/status/2097695001341829212

**9. Zara Zhang(独立开发者)**
一句短评:想法很容易,信念很难。
为什么值得关注:在 agent 这条拥挤的赛道上,能把一个方向长期做下去,往往比想到点子更稀缺。
https://x.com/zarazhangrui/status/2097599758391255259

本期无官方博客更新,无播客新一期。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
