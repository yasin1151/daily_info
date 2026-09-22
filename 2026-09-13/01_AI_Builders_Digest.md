
已取得全部内容（15 位 builder / 30 条推文 / 1 期播客，feed 生成于 2026-09-12，无博客更新）。以下是今日摘要。

---

# AI Builders Digest — 2026-09-13

**数据**：15 位 builder、30 条推文、1 期播客（No Priors）｜无官方博客更新

---

## X / 推特

### 模型与平台发布

**OpenAI Codex & ChatGPT 负责人 Thibault Sottiaux（thsottiaux）**
Astra 本周一口气发了好几样：Images 2.5、GPT-Live-1、**Agents API**、**Data Agent**，以及面向金融服务的 ChatGPT。他补了一句「这还没到 DevDay，下周也有安排」，等于预告还有一轮。
同一天他罕见地公开回应质量投诉：已定位并修复三类问题——为旧模型写的 skills 在新模型上触发过频、一个 opt-in 的上下文管理实验会导致提前停止或回复旧消息、若干配置错误的引擎拉低了长尾流量质量。官方估计约 4000–5000 名用户受影响，实验已关闭，并会再补一次 reset。
另外宣布 Git AI 团队（Aidan 与 Sasha）加入 OpenAI。Git AI 是他们做的开源工具，用来分析 coding agent 对代码库究竟贡献了什么；OpenAI 承诺继续开源并加大投入。
**为什么值得关注**：Agents API 与 Data Agent 是自研 agent 工具链需要直接对接的接口层；而「度量 coding agent 实际贡献」这件事被大厂收编，说明 agent 效果评估正在从内部工具变成正式产品。
https://x.com/thsottiaux/status/2098639827084480864 ｜ https://x.com/thsottiaux/status/2098612714704891959 ｜ https://x.com/thsottiaux/status/2098569976143806918

### Agent 工具链与评估

**Anthropic Claude Code 团队成员 Thariq（trq212）**
发布 plugin evals：「很多人反馈模型换代后不知道自己的 skills 还灵不灵」，现在在插件目录里跑 `claude plugin eval init` 就能给 skill 建评估。
他同时吐槽当前的 eval 文化：「**只看 pass/fail 分数已经没法解读 evals 了**」——他见到的很多 benchmark 失败其实源于隐藏测试过严，有些情况下模型的答案比「标准答案」更合理。
**为什么值得关注**：这是把「skills 会随模型换代失效」当成工程问题来解，对做自研引擎/agent 工具链的人是很直接的参考（skill + eval 配套）。
https://x.com/trq212/status/2098531560643539440 ｜ https://x.com/trq212/status/2098490139798655427

**Every CEO Dan Shipper（danshipper）**
「更好的 benchmark 分数并不能说明模型在你的真实工作里表现如何」。所以 Every 三年来的新模型评测一直是「vibe check」——基于真实工作场景写长文评测。现在他们把这件事定量化：内部搭了一个平台，让每个同事基于自己的日常工作建**个人 benchmark**。
**为什么值得关注**：评估重心从公共榜单转向「自己工作流的私有 eval」，这是目前多家团队共同的方向。
https://x.com/danshipper/status/2098481799047647715

### Coding agent 的正反两派

**Peter Yang（petergyang）**
公开质疑「软件工厂（software factory）」：「**除了验证和测试，我不认为 AI 已经到了能端到端自建新功能或自我改进产品的地步**。」他的实测经验是：把任务挂一整夜去构建新东西，只要它做错一个假设，整件事就变成 token 浪费。他直接发问：有哪个产品/功能是真正由软件工厂端到端做出来、没有人类定义需求或验收的？
另外他分享了自己的分工：**本地定时任务全放 Codex，云端任务全部迁到 Grok Bot**。
https://x.com/petergyang/status/2098565668241334366 ｜ https://x.com/petergyang/status/2098614492066435228

**Cursor 设计师 Ryo Lu（ryolu_）**
Cursor 上线了「long-lived agents for your big ideas」——面向长期、大颗粒想法的常驻 agent。
https://x.com/ryolu_/status/2098324260867772806

**Peter Steinberger（OpenClaw + OpenAI）**
在云会话里用 Astra + CUA 玩 Doom，自嘲「「还不到 AGI，但大概打得过苍蝇的脑子」」。同时他给 trycua 提交了一个 patch，让按键在 Linux 下可靠工作。
https://x.com/steipete/status/2098527519213604889 ｜ https://x.com/steipete/status/2098527982709256637

### 基础设施与产品

**Vercel CEO Guillermo Rauch（rauchg）**
Tailscale 的 model router 底层用的是 Vercel AI Gateway。他的判断是：「**AI Gateway 就是新的 CDN**」——你可以「直连源站」，但那很脆；也可以自建，但既痛苦又贵。
**为什么值得关注**：模型路由/网关正在被当作基础设施层来定位，多模型调度与降级会逐渐成为标配。
https://x.com/rauchg/status/2098531157230969062

**Box CEO Aaron Levie（levie）**
Box 现在可以挂载到 agent sandbox 上，让 agent 更方便地读写「自己电脑」上的文件。他的说法是：「当 agent 在企业里执行关键工作流，它们会需要人早就有的那些原语。」
**为什么值得关注**：agent 的文件系统/权限原语（挂载、沙箱、读写）正在被当成企业 agent 的基础设施来补齐。
https://x.com/levie/status/2098478938003841123

**Replit CEO Amjad Masad（amasad）**
宣布 Replit 收购了一家完全建立在 Replit 之上的业务，他预计「这只是第一批中的第一个」。另发布「带预算的 Routines」。
**为什么值得关注**：用平台造出来的公司在被平台自己收购，是 AI 原生开发平台开始形成生态闭环的信号。
https://x.com/amasad/status/2098548464452055437 ｜ https://x.com/amasad/status/2098317466682179643

### 组织与行业观察

**Meta AI 资深总监 Madhu Guru（realmadhuguru）**
总结「多数企业 AI 项目为什么失败」：1）用旧剧本做 AI——CEO 指派亲信牵头建中央 AI 团队，但团队结构、产品范式、上线学习方式全不适用（过去 15 年产品开发多是渐进改进，AI 要求的是实验与发明）；2）对 evals 投入不足；3）在业务「外面」给公司造 AI——中央团队自称平台团队，做的工具跟一线工作流、上下文和判断脱节，结果只有勉强采用，没有真正的生产力提升。他的建议：招真正做过 AI 产品的负责人；把 evals 当一等公民；把最懂 AI 的 builder 嵌进财务/销售/支持等要改造的职能里。
https://x.com/realmadhuguru/status/2098448235048378456

**Builder Zara Zhang（zarazhangrui）**
「**一人公司这个概念被高估了**」。她承认 AI 让一个人能做更多，但「从零造新东西是极度孤独的体验」，需要有人一起头脑风暴、一起受苦、一起庆祝；不找人绑在一起，极容易失去动力。
https://x.com/zarazhangrui/status/2098483800456179923

---

## 播客

### No Priors — Coinbase CEO Brian Armstrong：Agentic Finance、稳定币与代币化

**核心一句话**：Armstrong 认为 AI agent 会拥有自己的银行账户，而加密轨道（crypto rails）是让这件事跑起来的关键——「在不久的将来，agent 的数量会超过人类；顺理成章地，agent 经济在某个时点也会超过人类经济。」

**为什么值得关注（对做 agent 工具链的人）**：这期最有价值的不是加密叙事，而是他把「agent 支付」当成**技术约束问题**来拆解——现在 76% 的 agent 电商交易金额低于 30 美分，而信用卡最低费率就是 30 美分固定费，物理上不可行。Coinbase 孵化的 X402 协议（已捐给 Linux Foundation，Google、Cloudflare、AWS 参与）就是为绕过这个约束而生。他认为未来会出现大量**专精 agent**：小开源模型用公司私有数据（例如 10 万条合规案例）做微调或 RL，能在特定任务上**跑赢前沿大模型**。

**内部工程上最有参考价值的一段**：Coinbase 在建一个「brain」系统来逼近递归自我改进。每个服务/仓库/团队都有一个 brain，内容是该服务的全部事故历史、必须执行的财务控制、每次 AB test、以及 PR 被接受或拒绝的完整 Git 历史。agent 改动服务前先读 brain；人类 review 时如果手动修了 agent 的错，「这个上下文必须回写进 brain，这样修的不只是这一次，而是所有未来的情况」，于是 one-shot PR 的接受率会持续上台阶。他们把这套挂在内部 agent harness（代号 Toshi）上，并接入 X402 让 agent 自己付钱调用外部服务。

**一句原话**：他让一个高价模型为一个复杂 feature 做三阶段计划、每个阶段拆 10 项、然后「叫它开 10 个 agent 并行执行每一项，顺便推荐该用哪个 agent，因为有些可以用更便宜的模型」——播客开始前两分钟，agent 回来告诉他 phase one 的 10 项全部做完、待 review。「这在过去我会一整天在 Slack 里 ping 团队；现在我把评论 @ 给一个 agent，直接给团队发一个已经做好的 PR。这个瞬间非常有魔力，甚至有点上瘾。」

其他要点：Coinbase 88% 收入已来自非比特币交易；tokenized stocks 已在美国以外上线、正与 SEC 谈美国路径；预测市场数月内做到约 1 亿美元年化收入、环比增长超 100%；他认为预测市场长期空间远不止体育，可用于评估政策的宏观后果。个人层面他谈了新公司 New Limit（抗衰老，已建成表观遗传重编程的前沿模型，首个 phase 1 临床针对酒精性肝病，明年启动），以及特殊经济区/「自由城市」对创新的意义。

https://www.youtube.com/watch?v=uLDK4l_-gUE

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders

---

补充说明（不进正文）：本轮 feed 为 1 天前生成（2026-09-12），非缓存内容；`blogPosts` 为 0，故无官方博客章节。已按你的偏好过滤掉纯个人/纪念日/招募类推文（Garry Tan 的 SAT、Matt Turck 与 Aditya Agarwal 的 9/11 纪念、Nikunj 的 VC 署名之争等）。
