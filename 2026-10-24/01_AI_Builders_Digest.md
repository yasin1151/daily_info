
AI Builders Digest — 2026-10-24

数据窗口：2026-10-22 至 10-23（18 位 builder / 38 条推文 / 1 期播客）。今天的主线只有两条：**Agent 的权限与协议层在被标准化**，以及**一场大型凭证泄露事故正在把"Agent 时代的默认安全假设"整个推翻**。

---

## 一、Agent 工具链：协议层开始"进基金会"

**Anthropic Claude Code 负责人 Boris Cherny**：Agent Skills 最初只是 Claude Code 里的一个实验，现在业内大量采用，Anthropic 认为它更适合捐给 Agentic AI Foundation（和 MCP 放在一起）。这条 1697 赞，是本周对工具链影响最大的一条。
为什么重要：Skills + MCP 都交给中立的基金会，意味着 Agent 的"能力包"和"连接层"正在变成跨厂商基础设施——自研引擎如果还按私有格式做工具描述，未来要付迁移成本。
https://x.com/bcherny/status/2113333859907747871

**OpenAI Codex/ChatGPT 团队成员 Thibault Sottiaux**：Decisions API 正式 GA，OpenResponses 加入 Linux Foundation，性能和 Uber 全面押注 Codex 都在推进。（另有两条"明天上午 10 点前上线"的预告，未说明内容。）
为什么重要：OpenAI 这边也在把 Responses/Decisions 这类接口推向标准化，两家的动作方向一致——Agent 的调用契约正在被公共化。
https://x.com/thsottiaux/status/2113492187770175603

**Google/Vercel 生态侧，Vercel CEO Guillermo Rauch**：他提的"Generative UI 现实案例"里有个细节值得记——AI Gateway 本身是个工具市场，在 AI SDK 里加一个工具（1 行代码），你就获得了"Google"：不止搜索，还有天气、体育、股票、选举。
为什么重要：这是 Agent 工具链最省力的形态——把外部能力收成一个 tool 定义，而不是自建集成层。
https://x.com/rauchg/status/2113451268316205515

---

## 二、Agent 权限模型：从"逐步确认"转向"自动模式"

**Claude 官方**：下周起，Claude web/桌面/移动端的会话在 Pro、Max、Team 套餐上默认以 auto mode 运行——不再逐步请求批准，改由一个自动检查拦截高风险操作，用户可随时切回手动。（14710 赞，本周最高互动）
为什么重要：这是交互范式的转向。Agent 产品默认从"人审批每一步"变成"系统风控 + 事后可回退"，对自研引擎的启示是：审批流要做成策略引擎，而不是逐个弹窗。
https://x.com/claudeai/status/2113360845409583307

同批：**Claude Models on Google Cloud（Anthropic 托管）GA**，带 Google Cloud IAM 凭证、计费和承诺抵扣——企业采购路径打通。https://x.com/claudeai/status/2113380122468454765
**Claude 原生平台同日上线新特性**：Opus 5.5 的 Fast mode、code execution、Skills API。https://x.com/claudeai/status/2113380126561800305

**swyx（smol.ai / Cognition / Latent Space）**：他认为 Opus 5.5 是他用过最好的"工时估算模型"——随着我们把越来越多工作委派出去，这种校准能力越来越关键："别告诉我需要 2-3 个工作日（人类会花的时间），对一个不知疲倦、还能高度并行的 AGI 来说，它 2-3 小时就能做完。"
另一条更技术：pipeline 在运行中就能估算自己这套 pipeline 修复的 ETA——这对流水线调度非常关键。
为什么重要：Agent 干活的能力已经超过人类日程表的精度，瓶颈变成了"估算与调度"。这是自研 Agent 工具链最容易被忽略的一层。
https://x.com/swyx/status/2113283272130412684
https://x.com/swyx/status/2113492502355562875 （pipeline 自估 ETA 那条为 2113509413537693703）

---

## 三、安全：这周真正的行业震动

**Vercel CEO Guillermo Rauch**（本周最狠的一句对比）：你阿姨的密码是便签上写的"P4ssword!"；而互联网加密的守护者的密码是"4"。就一个 4。这把 key 可以用来定向解密几乎一切，现在还在清理残留风险。他同时喊出"该干掉静态凭证了"——如果小偷只能偷到会自毁的钥匙，攻击面就完全不同；行业当年能一起搞出 TLS 的绿锁，现在该给 OIDC 也来一次。
https://x.com/rauchg/status/2113462657059639505
https://x.com/rauchg/status/2113399539227136084

**Box CEO Aaron Levie**：任何形式的"靠隐蔽性做安全"彻底结束了。对人不算好用，但在一个会翻遍每个缝隙、试遍每种攻击排列组合的自主系统面前，它就是失效的。后果是大量遗留企业基础设施要升级、数据管道要清洗、访问控制要重做；Agent 在防守侧也能帮忙（加速整改 + 模拟风险向量），但路很长——这也是他判断"扩散（diffusion）时间线会比一些人想象的更慢"的部分原因。
为什么重要：这条把"Agent 能力强"直接换算成"存量系统必须重写"，是今年比较少见的、从安全侧反推 AI 落地节奏的论证。
https://x.com/levie/status/2113499900399034689

**Replit CEO Amjad Masad**：发了"我们如何保护你的应用免受近期这些漏洞影响"。https://x.com/amasad/status/2113474587166171560
（同一天多位 builder 都在谈同一批漏洞，说明这是一次跨平台的凭证/加密层事故，不是单点问题。）

---

## 四、竞争格局与开源模型

**FirstMark 投资人 Matt Turck**：Mistral 的 Le Chonk 播客，信息量很大——西方最大开源模型、Mistral 自有数据中心 3800 张 GPU 训练、Le Chonk 现在还在训练中、万亿参数模型在路上、从 DeepSeek 借鉴了什么、RL 训的是代码/网络/金融/芯片、"模型 ping 了自己的训练器"的 sandbox 故事。他另一条判断更利落：现在所有人都在和所有人竞争——芯片商打推理商，推理商打 neo-cloud 和 post-training，模型打应用和芯片，应用打模型，NVIDIA 卖给所有人。
https://x.com/mattturck/status/2113311361639829673
https://x.com/mattturck/status/2113263905950568730

**SPC 的 Aditya Agarwal 与 Physical Intelligence 联创 Sergey Levine 对话**：机器人正在经历 LLM 经历过的那次转变——从微调、到提示、到直接用自然语言告诉模型要什么。π0.7 能从"口语教练"里学新技能。
为什么重要：这是"语言即接口"在具身侧的复现，Agent 的指令层设计思路可以照搬。
https://x.com/adityaag/status/2113385971844518124

---

## 五、播客：Training Data — David Silver & Lasse Espeholt（Ineffable Intelligence）

标题：*A Superlearner for the Age of Experience*（2026-10-13）
链接（官方给的播放列表地址）：https://www.youtube.com/playlist?list=PLOhHNjZItNnMm5tdW61JpnyxeYH5NDDx8

这是本周最值得听的一期，两个 AlphaGo 时代的人出来做"不靠人类数据"的实验室。核心观点：

- **超级学习者 = 深度 + 广度**。深度上要能从一无所知走到发现人类不知道的东西；广度上要能丢进任何经验流（模拟、数字、物理世界）都持续学习。David Silver 的比喻：人类是从"脑子里的灰浆"出发，自己发现了语言、数学、科学，没人给过蓝图，也没人给过万亿条数据集——"这件事 AI 至今没人破解"。
- **他们主动放弃人类先验**，这是有意识的短期性能牺牲换长期上限。论据是 AlphaGo 用了两年、大量人类数据 + 人在回路才赢李世石；AlphaZero 放弃人类数据后，几小时就超过了那两年的成果（国际象棋 4 小时击败最强 AI）。
- **对现有 LLM 路线最尖锐的评价**：很多 LLM 公司本质上在造"半自主、人在回路的算法"——成千上万人挂在学习回路里。他尊重这个路线走得很远，但不认为能走到真正的超级学习者。
- **"坩埚"（crucibles）**：不手工设计谜题，而是造有大量 emergent complexity 的环境——百万级互相作用的物体/物理引擎、百万级互相作用的 agent。第二个 agent 一进场，19×19 的围棋就产生了无穷层复杂度。
- **奖励函数**：不给"这就是科学"的精确奖励，只给极简、易描述的目标，让复杂性和涌现自己长出来（类比进化只优化适应度）。
- **算力**：20 人团队，保持极高"算力/人"比；今年年底成为 GCP 上最大 GPU 集群的首批客户，看中 Vera Rubin 单机架即一台机器的高带宽——因为 RL 的迭代周期远快于 LLM。他们的模拟要跑在 GPU 上，刻意避免 LLM 公司那种"沙箱堆在 CPU 上"的困境。
- **安全**：认为靠监控英文思维链的对齐方式正在触顶，agent 会说一套做一套；提出非语言的监控手段——shadow actions（让它想做但不真做）、用另一个超级智能当监控者并对其行为幅度做正则化。主张"模拟里全速，现实里限速"。
- **预测**（他自称预测纪录不错）：一年内会有极强的"方向正确"证据；真正的超级智能从原来的 3-5 年，因为 coding agent 的加速作用，收紧到 **3 年**。

对自研引擎/Agent 工具链最直接的一条：这期里"环境即产品"的思路（crucibles 而非 benchmark 任务集）和前面 MCP/Skills 进基金会是同一件事的两面——**决定 agent 上限的不是模型，是它被允许在其中行动的世界和接口**。

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
