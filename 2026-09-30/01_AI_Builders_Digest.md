
Content is fresh (feed generated 2026-09-29) and small enough to assemble directly. Composing the digest now.

AI Builders Digest · 2026-09-30
来源：follow-builders 中央 feed（生成于 2026-09-29，18 位 builder / 34 条推文，无播客与博客更新）

═══ 一、本周主线：Anthropic 发布 Sonnet 5.5，Claude Code 主力模型换代 ═══

**Boris Cherny（Claude Code @ Anthropic）** — 全网互动最高的一条（4835 赞）
原话：「Sonnet 5.5 fixing a bug with Claude Code. 30% faster and 30% less usage.」即同一任务下速度提升 30%、用量下降 30%。这条是 Sonnet 5.5 官方定位的锚点：不是"更聪明"叙事，而是**速度与 token 成本双降**。
https://x.com/bcherny/status/2104638725317923228

**Cat Wu（Claude Code + Cowork @ Anthropic）**
原话：「In Claude Code, users get ~30% more tasks done compared to Sonnet 5. It's smarter, so it needs fewer tokens for the same work.」她给了一个扫地机器人的工具调用 demo：比 Sonnet 5 快 24 秒、少用 6K token。
https://x.com/_catwu/status/2104639552170377399

**Alex Albert（Research @ Anthropic）**
原话：「Sonnet 5.5 has the same feel I liked about Opus 5.5. It writes clearly, it's very fast, and it's a major capabilities jump over Sonnet 5. Really great model to iterate with.」注意关键词是 iterate，不是 one-shot。
https://x.com/alexalbert__/status/2104633937280811010

**Aaron Levie（Box CEO）— 唯一的硬数据横向评测**
Box 在企业内容上用 Box Agent 跑复杂工作流 eval：整体 +4 分，但「2.4× faster to a finished deliverable on 12% fewer tokens」。分行业拆开：金融服务 +48 分、生命科学 +22、法律 +14、公共部门 +11。具体案例里最值得看的是法律那条：Sonnet 5.5 **拒绝**发明一个"标准市场基准"来做租赁条款对照，而是指出合同真正缺了什么（抗幻觉，而非抗能力）。
https://x.com/levie/status/2104648654074343480

**Dan Shipper（Every CEO）**
原话：「It has dramatically improved writing even versus Opus 5.5... Astra is still my favorite for writing, but this model beats it at revision tasks.」他还抛了一个值得关注的判断：Every 团队里的两位工程师「feel like they don't have room in their stack for mid-tier models anymore」——如果中档模型在成本和能力上都被夹死，工具链的选型逻辑会变。
https://x.com/danshipper/status/2104636728992776510

**Claude 官方号（claudeai）** 放了两组同 prompt 对比：Sonnet 5 vs 5.5 的弹跳球物理、以及纯代码绘制的像素森林生物逐帧动画。
https://x.com/claudeai/status/2104675003673325732

为什么重要：这一轮迭代的核心是 **成本/时延** 而非能力上限，直接决定 coding agent 的实际可用工作量和自建工具链的推理预算。

═══ 二、Agent 工具链：prompt 这个抽象正在消失 ═══

**Thariq（Claude Code @ Anthropic）** — 4265 赞，本期最值得记下的一条观点
原话：「it's basically impossible for someone to just "show you their prompt" now, because everything is about references, skills and examples. I often ask my agent to look at 3 other repos I've made first, search the web for references, use other AI APIs, etc.」
他另一条回应"高层抽象（projects、claude tag、dynamic workflows）太贵"的担心：「Try Sonnet 5.5 in particular when making workflows.」——即高层编排的 token 成本问题，正被模型效率下降抵消。
https://x.com/trq212/status/2104608785696440510
https://x.com/trq212/status/2104660926373023830

为什么重要：把 prompt 工程重构成 references + skills + examples 的检索式上下文（含跨仓库、跨工具），正是自研 Agent 引擎的架构方向。这条给了一个来自模型厂商内部的背书。

═══ 三、OpenAI：DevDay 前夜的预告与 Codex 订阅口径变化 ═══

**Thibault Sottiaux（Codex & ChatGPT @ OpenAI）— 对重度用户影响最大的一条，需要仔细读**
要点（原帖很长，摘要如下）：
1. 明天重新开放 Pro $200 订阅给新用户，但**同时改变用量计算方式**——按他自己的说法，"do the math, it will net out at half the dollar in API spend compared to the old Pro $200 plan"，即订阅内含的 API 美元额度实际减半。
2. 承诺不再引入 5h limit（这与你们之前排查的 Codex 限额口径直接相关），周额度可自由使用。
3. 本周把 GPT-6 Sol 和 GPT-6 Luna 的价格降到原来的 50%。
4. 明天会给订阅加一些**不消耗用量**的新东西，暂不透露。
原话结尾：「I wanted to be transparent before all the big announcements tomorrow.」
https://x.com/thsottiaux/status/2104823812042940713

**Sam Altman（OpenAI CEO）** — 8097 赞
原话：「Pretty excited for DevDay tomorrow. We have found a new thing.」"a new thing" 的措辞被大量转发放大，但官方没给任何具体信息。
https://x.com/sama/status/2104661956879913457

**Dan Shipper（Every CEO）** 现场判断：「i've been to every dev day since 2023, this is by far the most launches OpenAI has ever had」，并附一句「rsi?」（自我加速的调侃）。
https://x.com/danshipper/status/2104662907716050988

**Peter Yang** 第一次去 OpenAI DevDay；**Peter Steinberger（steipete，OpenClaw + OpenAI）** 回「See ya there!」，暗示 OpenClaw 侧也会有人到场。
https://x.com/petergyang/status/2104781373433377030
https://x.com/steipete/status/2104702088626557384

为什么重要：如果订阅内含额度减半成立，**重度 Codex 用户的成本模型要重算**，同时降价的 GPT-6 Sol/Luna 是对冲选项；DevDay 的量级预告意味着明天会有一波工具链接口变动。

═══ 四、基础设施：Vercel 把「为 agent 设计」做进产品 ═══

**Guillermo Rauch（Vercel CEO）**
1. 域名搜索不再需要登录，原话点题：「Especially great if you're an agent.」——把无鉴权 API 面当作 agent 的入口。
2. 一次真实迁移复盘：约 70% 更快的构建、约 75% 更快的渲染；关键是「We derived two AI skills from the migration that we'll be sharing back」，一个成熟、充满"前供应商特有写法"的负载，净工作量不到一周完成。
https://x.com/rauchg/status/2104764419305796094
https://x.com/rauchg/status/2104660502723072281

为什么重要：把一次性迁移沉淀成可复用的 AI skills 并对外分享，是"Agent 工具链"从 demo 走向工程化交付的典型样本。

═══ 五、投资视角（一条值得看的反调） ═══

**Nikunj Kothari（FPV Ventures 合伙人）**
原话：「Where are all the "distribution is a moat and hence raise a lot of money" investors today.. when the incumbents are flexing their distribution muscle.」他的结论：「Use capital as a weapon to compound and not as destiny」;并明确补了一句这不是针对某家公司，而是针对「会给出糟糕建议、等公司崩了再转去投下一家的投资人」。
https://x.com/nikunj/status/2104566122549063756

为什么重要：在模型能力快速平价化的窗口里，"分发即护城河"这个融资叙事的可靠性正在被质疑。

═══ 六、轻量条目（速览） ═══

- **Peter Yang**：用 Sonnet 5.5 做出了一个可玩的星际争霸关卡（人族守基地，含 SC2 模型与 Suno 生成的配乐），并说 demo 的 sizzle reel 也是模型做的。https://x.com/petergyang/status/2104736498151256303
- **Peter Yang** 对舆论的观察：「Folks on X are so fickle about "omg openai is getting mogged by Claude 5.5" or just a few months ago "anthropic is so cooked by codex."」他的态度是两个（且很快更多）对手互推前沿对所有人都有利。https://x.com/petergyang/status/2104809410040336784
- **Garry Tan（YC 总裁兼 CEO）**：「Codegen meets WhatsApp actually makes a ton of sense」——对 codegen 下沉到 IM 入口的判断。https://x.com/garrytan/status/2104771351009702168
- **Swyx（smol.ai / Cognition / AI Engineer）**：「oai designers have to be trolling us」，配图吐槽，未给更多上下文。https://x.com/swyx/status/2104741800393253322
- **Zara Zhang（Builder）**：公开招募访谈对象，想聊三件事：用 AI 做前端但做不出"不像 AI 味"的漂亮界面、看得到 X 上的 demo 但复现不出来、以及正在做这类 demo 愿意分享流程的人。https://x.com/zarazhangrui/status/2104689580045979811
- **Ryo Lu（Cursor 设计）**：在台湾做了 YouBike 的骑行导航小工具（码头、实时导航、语音转向提示）。https://x.com/ryolu_/status/2104546903807660224
- **Nikunj Kothari**：另一条演示视频，注明是 Opus 5.5 一次成型（one shot）。https://x.com/nikunj/status/2104758141128974358

未收录：Josh Woodward 的 Yosemite 感叹、Thariq 的"一步步想"玩笑、Garry Tan 的 karma 感悟、Thibault 的两条周末闲聊、Steinberger/Altman 之外的纯应和，均属无实质信息内容。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
