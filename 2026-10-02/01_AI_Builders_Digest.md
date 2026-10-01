
以下是今日摘要。

---

# AI Builders Digest — 2026-10-02

数据源新鲜（feed 生成于 2026-10-01），17 位 builder / 34 条推文 / 1 期播客。本日主线：**OpenAI DevDay 后的产品外溢**（持久化 Agent、Codex 工具链、MCP 一键部署）与 **Agent 协作/连接层**的集中讨论。

---

## 一、播客重点：Sam Altman 谈 Dots 与"持久化智能"

**AI & I（现更名 The Every Podcast）—《How Sam Altman Uses Dots to Take Back His Time》**
主持：Dan Shipper（Every CEO）｜录制于 OpenAI Dev Day 现场
链接：https://www.youtube.com/playlist?list=PLuMcoKK9mKgHtW_o9h5sGO2vXrffKHwJL

**核心内容（为什么值得关注：这是 OpenAI 一号人物对"Agent 下一步形态"最直白的一次公开表述）**

- **Dots = 常驻型个人 Agent。** Sam 说自己现在早上不再第一时间刷手机，而是把"判断哪些事现在必须看"交给 dot，把自己的深度工作时间抢回来。他举了两个具体例子：Dev Day 当天 keynote 上一个 demo 崩了，同事（转录作 Tebow）的 dot 在演示前 5 分钟主动发消息说"我看了演示内容，这台设备大概率会让 demo 失败，要不要我修"；以及 dot 在他忙碌一天后提醒他"你只有这一小段空档，这件事必须处理"，而他自己根本没发现。dot 还会**跨源拼上下文**——例如发现要改签的航班与 Slack 里（而非日历里）的会议冲突。
- **"我没见过有人能雇一个人做到这件事"。** Sam 描述：他把零散想法/散步时的语音随手丢给 dot，dot 主动做出 5-6 个版本的某个新功能，他再连续迭代；还有一次他用 Codex 搜不到一段 Slack 内容（因为那其实是张截图），第二天 dot 说"我一直在想这件事，我帮你找到了"，因为它 overnight 逐张看了截图。
- **Space：三件套办公工具一次发布。** 理由是大模型原生不适合"人机协同"，"多人 + 多人的 AI 一起工作时，现有抽象会崩掉"。他特别看好**"活文档"（live documents）**：文档随人交互自动更新，且"七个人的 dot 可以协同产出一个原本只存在于大家脑子里、半成型的东西"。
- **Decisions API 与速度层。** 提到 competitor 的"新模型类型"（转录作 Jev）让他们更想优先做"更快、更便宜"的路线；提到 Astra 是把 Dots 推过"智能门槛"的关键模型；提到 Ultrafast 速度档——"近期先给 8 倍，之后会有 100 倍"，并承认"我们历史上一直在压降 IQ 的价格，现在必须像投入智能一样投入速度的民主化"。
- **平台观。** 明确反对"最终只剩一家模型公司"，强调"给开发者和我们一样的工具"（Codex native apps、plugin extensions、**把 ChatGPT 订阅带到第三方 app**、marketplace）。他自评 App Store 那件事"还没做出来"，但平台已让很多人建起真公司。
- **文艺复兴 vs 工业革命。** 他用这个框架回应"AI 会不会把人变成家猫"：希望是"人重新拿回对自己时间的控制"，而非把人变成机器里的齿轮。也透露他现在最关心的是 **safety/alignment/security**，半年前更关心营收增长。

---

## 二、Agent / 工具链（与自研引擎最相关）

**Thibault Sottiaux（OpenAI，Codex & ChatGPT）**
- 现在**可以直接在 ChatGPT 里构建并部署 MCP server**，并设置访问权限（限定若干人，或公开分享给所有人）。
  https://x.com/thsottiaux/status/2105519215092584786
- 另一条：**GPT-6.1 Sol 是他们史上需求最大的模型**，ChatGPT 与 Codex 一度过载，已紧急扩容，"未来几小时速度应接近昨天的两倍"。
  https://x.com/thsottiaux/status/2105464274747527543
- 为什么重要：MCP 的创建/分发门槛被拉到了对话界面级别，直接冲击现有 Agent 工具链中间层。

**Peter Steinberger（steipete，OpenClaw + OpenAI）**
- "聊天流里的 agent 间通信越来越烦人"，他在 OpenClaw 里把 agent 间消息默认收成**一行可展开**，并判断"别人会跟进"。
  https://x.com/steipete/status/2105362785534361996
- "CI 和 GitHub 在比谁更拖慢我，是时候重新想想怎么工作了。"
  https://x.com/steipete/status/2105341288958869952
- 为什么重要：多 Agent 协作的**可观测性/降噪**正在成为一线实操痛点。

**Garry Tan（YC 总裁兼 CEO）**
- 指出多数代码编辑器只能"自上而下编排子 agent"，而他第一次看到 **agent swarm 像同侪一样互相通信、自发协调**（点名 Capy），"可以有机地探索空间，而不是预先编排"。
  https://x.com/garrytan/status/2105449821645480046
- 另发长文记录与美国交通部长 Sean Duffy 的对谈：用 Air Space Intelligence 的 SMART 工具做航路/延误预测，"2.5 小时的 ground stop 可能只需 45 分钟"，强调"不需要突破性技术，需要的是愿意用软件并接受 AI 增强的意志"。
  https://x.com/garrytan/status/2105395957357588561

**Guillermo Rauch（Vercel CEO）**
- 宣布 **Connect**：让服务方出现在 2000 万+ 开发者及其将发布的数十亿 agent 面前。核心论点——"**代码变免费后，构建的最终 boss 是连接**"；"今天构建 agent 的世界被静态凭证拖累，给每个 agent/app 发一堆 key 是 DX 地狱，也是巨大负债。"
  https://x.com/rauchg/status/2105390544096841942
- 另一条批评 token 聚合数据源噪声大（供应商促销、自称 ZDR），称 **Vercel AI Gateway** 因真实客户用量 + 零加价，是可信的全球 token 流向数据源，并透露每周都拒绝"来源可疑的免费 token 促销"。
  https://x.com/rauchg/status/2105476587756138942

**Aaron Levie（Box CEO）**
- 长文：当下最大机会是**成为 AI 进入经济的"部署层"**。改造企业工作流的工程量远超预期：遗留系统上云、数据治理、把软件接到 agent、重设计工作流、HITL、构建并维护 evals、随新模型持续更新。他强调"AI 不等于部署软件"——你交付的是**流程中的工作产出**，而非工具；因此会催生大量新的 FDE（Forward Deployed Engineer）与新型服务公司。
  https://x.com/levie/status/2105354449795621179

**Nan Yu（OpenAI 产品，Codex；前 Linear 产品负责人）**
- 入职约一周的观察：OpenAI 最突出的是**"荒谬地偏向行动"**的文化——随口聊一句功能，回到工位 PR 已经在面前；Slack 上说"下周吃个饭"，5 分钟内日历邀请就到了。副作用是"一切都像上了膛"，但"这种能量教不会，一旦失去极难找回"。
  https://x.com/thenanyu/status/2105316751802348005

---

## 三、模型 / 产品动态

**Josh Woodward（Google，VP of Google Labs / Gemini App）** 只发了一句 **"Gemini 4 Argon!"**（1319 赞）
https://x.com/joshwoodward/status/2105396307250782446

**Peter Yang（AI 教程作者）** 评论：**"Google 在 Gemini 4 上做成了！"**，但补一句"接下来需要在编码 harness（Antigravity）和个人 agent（Spark）上更有竞争力"。
https://x.com/petergyang/status/2105393240392585359

**Google Labs**：宣布 **Opal 将于 2026-11-17 关停**，其经验沉淀为 Gemini App 的 **Skills**（全球上线）——"把常用自定义指令存进对话、更快自动化重复任务"。
https://x.com/GoogleLabs/status/2105352889665564838

**Matt Turck（FirstMark Capital 合伙人，MAD Podcast 主持人）** 一句调侃配图：**"SaaS 公司们看着 Anthropic 的 ARR 增长走平"**（549 赞）。值得注意：这是当下 SaaS 估值叙事里最敏感的那根弦。
https://x.com/mattturck/status/2105261211906384132

**Amjad Masad（Replit CEO）**：Make + 一键发布 Meta VR 应用。
https://x.com/amasad/status/2105321112389443805

**Claude（Anthropic）**：Claude Founder House 将到 SF Tech Week（10/6–8）与斯德哥尔摩（10/14），含 talks / workshops / office hours。
https://x.com/claudeai/status/2105370680485417401

---

## 四、其他值得一读

**Swyx（smol.ai / AI Engineer / Latent Space）**：称 Flow 正在做"硬件工程领域的 Git+GitHub"——把汽车到火箭这类复杂、不可逆、高价值管线的上千方对齐起来获得加速，"一旦用过 Flow，就回不去 spreadsheet_final_FINAL_v23 了"。
https://x.com/swyx/status/2105348724331606411

**Nikunj Kothari（fpv ventures 合伙人）**：已把工作大部分自动化，只剩三件事没有：找项目/写 cold email（"坚信技术救不了这块"）、见创始人（线下，Zoom 很烂）、写 pass note（仍全部手写，"老实说这是这行最难的部分"）。
https://x.com/nikunj/status/2105532229866942772

**Aditya Agarwal（SPC GP）**：他常问创业者的问题是"这家公司的极致版本（maximalist version）是什么"。判断：AI 让创业更容易，却把"什么是伟大的创业公司"的门槛大幅抬高了——从小处起步会很难拿到钱、招到人、最后真的撬动未来。
https://x.com/adityaag/status/2105339569139056776

---

**一句话总结**：今天最值得咀嚼的是两个信号——① OpenAI 正在把 Agent 从"对话"推进到"常驻 + 跨源 + 主动交付工作产出"（Dots / Decisions API / Ultrafast），并顺手把 **MCP 的创建分发**压到对话框里；② 社区这边，**Multi-Agent 之间的通信降噪（steipete）、同侪自协调 swarm（Garry Tan）、以及 Agent 的连接/凭证层（Rauch 的 Connect）** 正在被当作下一批硬骨头。对做自研引擎/Agent 工具链来说，后三条比模型参数更值得抄作业。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
