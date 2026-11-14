
AI Builders 情报快报 — 2026-11-15

数据源：9 位 builder / 21 条推文 + 1 期播客（Training Data，2026-11-05）。今日无官方博客更新。

---

一、头条：Trajectory 想把「持续学习」做成一个一键按钮

Training Data 播客专访 Trajectory 联创 Ronak（前 Windsurf / 更早在 DeepMind，联创分别来自 Gemini Robotics 与 Apple Vision Pro）。这一期技术密度很高，几乎每段都对自研引擎和 Agent 工具链有直接参考价值。

他的核心比喻是地图：现在的 Agent 像"去 AAA 门店拿纸质地图"——模型很强，但你想改路线，只能等下一次全量批量训练；他要做到"Google Maps"，每一次真实 rollout 都在更新。他给出三个不可省的原语：一是把生产里所有主 Agent 和子 Agent 的轨迹 trace 下来（他自己点名 Braintrust、Raindrop 这类工具先解决这一步）；二是让 trace 可回放（环境用 Dockerfile 定义）；三是训练栈 / loss / reward 那一段——这才是他真正要抽象掉的部分。

最硬的两块研究：1）把 GRPO 从"同一题必须跑 8~16 次组成 group"改成 group size one，直接吃 1 万条来自不同任务的轨迹，一条 rollout 就学——这样就**不再需要构造仿真环境**。2）reward 不用全标：从 1 万条里挑 100 条有代表性的，人只对这 100 条写 rubric，训一个 meta grader 把奖励扩散到剩下 9900 条。他的终极目标是"观测面板上圈出 Agent 做得好的 5 件事和差的 5 件事，点 train"。

落地数据：法律 AI 公司 Harvey 用他们平台训出的模型**便宜 6 倍**，开源基底从约 4% 准确率提到约 18%。Rogo 追求的是"智能密度"——同样任务用少得多的 token 完成。他明确说 NVIDIA 也在用。

最值得抄的一句话是模型 vs harness 的分工："模型给你效率——同一件事它见过 100 次、1000 次，更快更便宜更可靠；harness 给你新能力——以前根本做不到的事。"他预判的终局是**10% 任务走前沿模型（他称 Fable），90% 路由到自训的便宜模型**，差额就是毛利。另外他说团队现在大部分时间在画白板、吵系统设计，实现交给"Agent 软件工厂"，训练代码也按微服务 + K8s 自动扩缩生产化了。

为什么重要：这是目前对"自研引擎"最完整的一条产品化路径说明——不是自己从零训基座，而是 trace → replay → reward 压缩 → 小步 RL 微调 → 路由。而且它把 harness 和 model 的收益边界讲清楚了，做工具链的人应该据此决定力气往哪投。
链接：https://www.youtube.com/playlist?list=PLOhHNjZItNnMm5tdW61JpnyxeYH5NDDx8

---

二、Agent 工具链与编码 Agent

Vercel CEO Guillermo Rauch 发布 Workflow SDK 5 与 Vercel Workflows，称其为"Agent 的里程碑式一步"，四个改善点：time-to-first-step 与 step 间隔大幅缩短；加密与安全加码；规模化下的可靠性经过大量容灾演练；最关键的是持久化日志层被抽出来做成可复用的 durable-harness，"任何 Agent harness 都能用"。配合他前一条"Vercel Sandbox is inevitable"，Vercel 明显在往上吃 Agent 执行层。
为什么重要：durable-harness 一旦成为可复用底座，自研引擎不必自己造持久化执行/回放层，这正好和播客里"trace 可回放"那一环咬合。
https://x.com/rauchg/status/2121277727940776114

YC 总裁 Garry Tan 放出一条很反直觉的实测结论：在 Claude Code 2.1.322 上跑 52 个编码任务，模型 Fable 5.2 的解出率 82.7%、Opus 5.5 是 84.6%——几乎打平，但 Fable 5.2 **每个解出任务的成本是 2.80 倍**。所以他的建议是"编码默认继续用 Opus 5.5"。他自己也承认问题在于题目太简单：Opus 已经能解大部分，"要区分两者得上更难的题"。他同时开源了这个 harness eval 仓库。
为什么重要：这是少见的有具体样本量、有成对成本口径的对照，而不是榜单分数。评测方法本身比结论更值得借——固定 harness 版本、按"每解出任务的成本"而不是每 token 计价。
https://x.com/garrytan/status/2121464508225053153
eval 仓库：https://x.com/garrytan/status/2121463161069228382

Every CEO Dan Shipper 提了个他认为"软件公司还在被付费"的真问题：既然 Fable 5.2 已经能 vibe code 出任何东西，为什么团队仍然为软件付钱？他给的答案方向是采购的是可靠性、责任和协作，而不是代码本身。他另一条把某个公式称作"AI 里最重要的公式"，配图未展开。
为什么重要：这是做 Agent 产品定价时绕不开的追问——当生成成本趋零，你卖的到底是什么。
https://x.com/danshipper/status/2121248233510818003
https://x.com/danshipper/status/2121243400293007866

---

三、模型与评测之争

FPV Ventures 合伙人 Nikunj Kothari 直接开火："我以为 Llama 4 之后大家已经不做 benchmark-maxxing 这种炫技了，结果卡特尔又回来了。"他的判断是除了极少数真正有意义的 benchmark，其余都是姿态，或者只挑一个榜爬到极致当营销——"对少数公司有用，但长期撑不住"。他给的建议很朴素：把模型放进自己的真实工作流里用，才知道哪个真的适合你。
为什么重要：和上面 Garry Tan 的结论互为注脚——榜单分数与"每解出任务成本"经常背离，选型时应以自有 harness 上的 A/B 为准。
https://x.com/nikunj/status/2121320899161010360

Peter Yang（做实用 AI 教程与访谈）给出一个 Agent skill 的真实用例：把病人的全部病历放进一个 Drive 文件夹，让 ChatGPT 或 Claude 装上他免费开源的 /fuck-cancer skill，指向该文件夹，就能生成一页纸病情简报、检索临床试验等。这条 434 赞，他还鼓励别人 fork 改成其他长期病种。同一天他还在质疑 WSJ 关于 Alice Huang 是间谍的报道，引用新加坡政府材料称证据不足，并转述了一位 NVIDIA 员工的讲述，提醒读者自行核查。
为什么重要：这是"skill 作为分发形态"的典型——一个 markdown 技能包 + 用户自己的数据，就能做出垂直工具，不需要模型也不需要应用。
https://x.com/petergyang/status/2121430386685395022

---

四、行业舆情：Stand with Jensen 刷屏

今天的时间线基本被这件事占满。Replit CEO Amjad Masad 转发号召"读这封 Stand with Jensen 的公开信并签名"，2557 赞 / 367 转；他随后又说明已和 StandWithJensen 页面的所有者（站点用 Replit 搭建托管）一起把限流调高，"现在应该能扛住流量了"——这条 1270 赞，等于顺手演示了一次 Replit 的扩容能力。YC 总裁 Garry Tan 也签名，措辞是"Jensen 应该得到正当程序，而不是现在正在发生的事"，2017 赞。少数派声音来自 Peter Yang，他认为目前还不清楚 Alice Huang 是否真是间谍，指 WSJ 跳到了结论。
为什么重要：AI 圈核心人物第一次如此集中地在同一份公开信上表态，且诉求是"程序正义"而非技术路线；同时它暴露了"一条推文带来的流量足以打挂一个静态站点"这个工程现实。
https://x.com/amasad/status/2121377395244749097
https://x.com/amasad/status/2121389001546567837
https://x.com/garrytan/status/2121462697787342932
https://x.com/petergyang/status/2121430819667579031

---

五、一句话速览

- Amjad Masad：Replit 与 Visa 在 agentic commerce 上合作，"更多功能在路上"。https://x.com/amasad/status/2121428406764204199
- Aditya Agarwal（SPC 合伙人，前 Dropbox CTO）：为 AI 100 里的自家公司站台，点了 Baseten、Render、Profound、Replit、Gamma、Cog、Density；另有一句"我们正处在一个非常诡异的时间线"。https://x.com/adityaag/status/2121281677238604148
- 今日跳过：Swyx 的活动预告、Matt Turck 关于 FAA 停飞的玩笑、以及若干无上下文的短句。

---

今日对自研引擎最该带走的三点：一是"group size one"的思路——不必为每个任务造仿真环境，真实 rollout 本身就够训；二是 reward 用 100 条代表样本 + meta grader 扩散，省掉全量标注；三是 harness 与 model 收益边界分明，10/90 路由是明确的产品形态。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
