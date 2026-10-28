
**AI Builders 日报 · 2026-10-29**
数据面：13 位 builder / 29 条推文，播客与博客本轮无更新（feed 生成于 10-28）。

---

## 1. Box CEO Aaron Levie：企业 Agent 部署率不到 1%，瓶颈在能力不在意愿

Levie 转发并强化了一个判断：绝大多数企业工作流至今没有被 agent 真正改造过，"整个经济体的实际部署大概不到 1%"。他区分了两种现状——很多公司所谓"用了 AI"，只是让 LLM 跑一遍、出个判断或反馈，几乎没有真正的自动化。他强调这不只是企业技术采纳慢的问题，"很大一部分原因就是 AI 本身的能力还没到"。

转折点在于：computer use、长任务 agent、harness 改进以及周边基础设施成熟后，agent 才第一次能上更复杂的工作流。他预测会出现可自我改进的系统——给定一个工作流目标，能在大量实例上逐步提升执行成功率；加上 agent swarm 这种形态，"你可以直接对一个问题投入任意算力，agent 自己去做"。最终形态不是用户逐个 prompt agent 干活，而是组织重新设计底层流程去适配 agent，冲击最大的会是金融、生命科学、医疗等信息密集行业。

**为什么重要**：这是对"Agent 元年已过"叙事最直接的反对。对做 Agent 工具链的人来说，他点出的三个杠杆——harness、长任务可靠性、swarm 调度——正好是当前工程投入最密集的地方；而"执行成功率随实例量自我提升"这句话，几乎就是在描述 eval + 反馈闭环的产品化。
https://x.com/levie/status/2115305369799110905

---

## 2. 前 Claude Code 工程师 Thariq：给 Agent 做操作系统级入口，8262 赞

Thariq（bio 自述 "formerly Claude Code @anthropicai"）晒了一个个人实验：一个 AI-native 的 macOS dock，带自定义模式（写作、building 等）帮助自己保持专注。关键设计是 **agent 自己能够改 mode 的行为、新增 mode**，并通过一个叫 `jev` 的东西实时对我的活动和通知做分类，然后据此采取动作。他在另一条推文里补充，这是他很久以来想做的 HCI 工作，但"动 OS 内部一直太耗时"，并明确说还不打算公开、边缘情况很多、不建议使用。这条拿到 8262 赞 / 432 回复，是他本轮互动最高的一条。

**为什么重要**：这是"Agent 的入口该长什么样"的一次实操回答——不是聊天框，而是一个能感知你当前活动上下文、并且**允许 agent 自己改写自身交互形态**的常驻层。对自研引擎的启示在于 `jev` 这类实时活动分类器：把 OS 事件流变成 agent 可消费的状态，而不是等用户打成一句话。
https://x.com/trq212/status/2115135857669881939

---

## 3. 同一位：开源软件的"agent 可改 + 上游自动合并"分发方式还不存在

Thariq 另一条 2465 赞的观察：感觉需要一种新的开源软件分发方式，使得"人们可以通过 agent 修改代码，同时又能自动把上游变更合并进来"。他明确指出，coding agent 有能力做这件事，但**它们不会自动去做**。

**为什么重要**：这戳中了 agent-native 开发流程里最空的一块。现在的 fork + patch 模型对人类维护者友好，对 agent 极不友好——agent 改完就漂移，上游一更新就冲突。谁先把"agent 维护的 patch 集 + 自动 rebase 上游"做成基础设施（而不是让每个 agent 每次重新理解 diff），谁就拿到 agent 时代的包管理入口。
https://x.com/trq212/status/2115188992861970693

---

## 4. OpenAI Codex 侧发布节点：官方连发三条预告，"明天还有好消息"

Thibault Sottiaux（bio：Codex & ChatGPT @OpenAI）本轮发了三条递进式推文：先是 "Lands by midnight PST."，然后是 "（链接）has landed"——这条拿到 5209 赞 / 1127 回复，是本轮全站互动最高的一条；随后又补了一句 "And it's done. See you tomorrow for some good news."，暗示次日还有后续。

**为什么重要**：1127 条回复的发布量级，说明这是 Codex 的一次正式版本动作。需要说明的是，推文正文只留了一个外链、没有写出发布内容，我无法在不点开链接的情况下确认具体是什么功能，因此不在这里替它下定义——但结合 Levie 那条所述的"harness 改进"，coding agent 侧的基础设施迭代节奏明显在加速。建议直接点原推看链接。
https://x.com/thsottiaux/status/2115297093879472332

---

## 5. Replit CEO Amjad Masad：coding 正在被次前沿模型吃掉，前沿的钱应该押在"新发现"上

Masad 的投资判断相当尖锐：如果他要投前沿 AI，会主要押注在**新发现及其应用（比如医药）**上，理由是"coding 和大部分知识工作正在被 sub-frontier 模型快速饱和"。

**为什么重要**：这是对"前沿模型护城河"最不客气的质疑之一，而且出自一个靠 coding agent 做生意的人。含义是：应用层的价值不在"谁有最强模型"，而在"谁能用便宜一档的模型把 coding 做到够用"。对成本敏感的团队来说，这条基本是在说——别为前沿溢价买单，把工程力气花在 harness 和 evals 上。
https://x.com/amasad/status/2115207856496480261

---

## 6. YC 总裁 Garry Tan：20 个 subagent 常驻跑，现在反过来要"瘦身降 token"

Garry Tan 晒了 Capy（@capydotai）"软件工厂"带来的 GitHub 贡献图变化，说自己同时有 **10 到 20 个 subagent 常驻在 GStack 和 GBrain 上跑**，PR 产出很密。但另一条推文的口风完全相反：他正在"尝试精简 GStack，降低 token 消耗和任务延迟"。

**为什么重要**：前半段是 multi-agent 编排的样板，后半段才是真话——subagent 铺开之后，成本和延迟立刻成为主要矛盾。这和记忆里"多 agent 不等于更快的吞吐，常常等于更贵的等待"是一致的。值得关注的是他有没有公开 GStack 瘦身的具体手段（上下文裁剪？模型降级？任务路由？）。
https://x.com/garrytan/status/2115193524152860771
（瘦身那条）https://x.com/garrytan/status/2115215790756794496

---

## 7. 一条术语提醒：FPV Ventures 的 Nikunj 列出 8 个"人人都在用、定义全不一样"的词

Nikunj Kothari 说自己对这 8 个概念有大致判断，但仍必须逐个深挖，因为"会拿到 10 个截然不同的定义"：long horizon、out of distribution（尤其数据侧）、intelligence per watt、RL environments、"forward deployed"、revenue、"frontier"、self improving。他说有些确实主观，但"回答的方差会让你吃惊"。

**为什么重要**：做技术选型和对外沟通时，这 8 个词现在被当成共识在用，实际含义却各说各话。特别是 `long horizon` 和 `self improving`——Levie 和 Masad 在上面两条里用的就不是同一个意思。评估第三方 agent 产品时，这几个词基本都需要追问一句"你的定义是什么"。
https://x.com/nikunj/status/2115111451614744845

---

## 其他一句话（信息量偏低，不展开）

- **Vercel CEO Guillermo Rauch** 用一段 shell 梗（`alias now=vercel`、一个 bun 的 Dockerfile、"we are so back"）宣告 Vercel 部署链路回归，196 赞。工程梗大于信息量。 https://x.com/rauchg/status/2115218670389756243
- **Every CEO Dan Shipper**：视频创作和游戏制作会像今天的文档、PPT 一样，成为知识工作的普遍基础设施（227 赞）。 https://x.com/danshipper/status/2115093098816745910

---

## 本轮对自研引擎 / Agent 工具链的三点可动作信号

1. **入口层**：Thariq 的 dock 实验说明"实时活动分类 → agent 自主改交互形态"这条路已经能被个人在几周内做出来，且极受欢迎。自研引擎如果只有 CLI/chat 入口，等于把上下文采集的主动权留给了用户手打。
2. **代码层**：agent 修改 + 上游自动合并，目前是空白地带。这比再做一个 agent 更容易形成结构性位置。
3. **成本层**：Garry Tan 从"堆 20 个 subagent"转向"降 token、降延迟"，加上 Masad 的"sub-frontier 够用论"，两条独立信号指向同一个结论——2026 下半年的竞争点不是模型上限，是单位任务成本。
