
AI Builders Digest — 2026-10-19

信息源抓取于 2026-10-18；X 上 8 位 builder 共 15 条推文，播客 1 期，官方博客 0 篇。今日主线很集中：**Agent 已经真的在读写生产数据库了，而基础设施侧的护栏还没跟上。**

---

## 一、播客：当几十亿个 Agent 打到你数据库上

**The MAD Podcast（Matt Turck）× Andy Pavlo** — CMU 数据库教授，两个月前加入 ClickHouse 创办 ClickHouse Labs。这期几乎是把"Agent 时代的数据层"讲透了。

https://www.youtube.com/@DataDrivenNYC/videos

**1）Agent 已经在自己建库、开分支。** Databricks 收购 Neon 时披露过一个数字：由 agent 创建的数据库分支占比从 30% 涨到 80%。Pavlo 的解释很朴素——coding agent 要改代码就得在数据库副本上验证，"你不想让它在生产库上试"。

**2）翻车是月度节目。** "每个月都有个故事，某人的生产数据库被 agent 删了。"他提到 Replit 那次著名事故，然后给了个很狠的类比：**"对不懂数据库历史的人来说，这就是狂野西部。像给猎豹喂了可卡因，再塞进法拉利。"**

**3）护栏不该靠人肉点 approve。** "把 agent 当幼儿看，你不会让幼儿在楼梯口乱跑。但你也不能一直坐在旁边点'批准'——那样你没法同时跑几百个 agent。"结论：约束要下沉到数据库权限层，而不是聊天框。

**4）查询量级是 10~100 倍。** 他把数据库史分成四代：主机 → 互联网 → 手机 → agent。前三次都是"更多人接进来"，这次是"每个人带几百个 agent，7×24 小时读写"，而且读写成混合型，比手机 App 那种纯读重得多。

**5）Agent 记忆：文件系统 vs 数据库之争，他觉得是伪命题。** **"什么是文件系统？它就是数据库。一切都是数据库。"** 差别只在保障：多 agent 共享状态、事务安全，SQLite 已经帮你做了，自己拿 JSON 文件硬搞就是重造轮子。

**6）最有意思的一段：模型时代的 SEO。** 为什么 agent 建应用总是推荐 Postgres？"因为预训练语料里全是它。" 他透露**已经有两家数据库公司来问他，怎么让自己的数据库被 agent 优先推荐**——他的回答是："去跟做模型的人谈，这不叫研究，这叫 SEO。"

**7）Text-to-SQL 的真实水位。** 他前一天刚跟某大行聊过：最初用现成方案准确率约 60%，后来靠多年打磨的语义层/上下文层 + 数百万美元投入做到 99.5%。"大行有无穷的钱才办得到；普通人现在下载个开源工具达不到这个水平。" 另外公开 benchmark（Spider 等）基本被训练数据污染了。

**8）对 MCP 的评价：不神，也不死。** "它本质上就是个 REST 接口，把人类可读文本在网络上传来传去，效率不高，但够用。" 安全上跟 JDBC/ODBC 客户端没区别——问题不在协议，在于你有没有搞清楚"谁在请求、要做什么、该不该允许"。

**9）一个惊人数据：** 他维护的 DBDB 项目每晚拉取所有开源数据库的最新 commit，检测 Claude/Codex 的 co-sign——**现在超过 60% 的开源数据库项目有 agent 提交的代码**。他自己在 CMU 的数据库课程项目，从 Opus 4 那一代开始 agent 基本能全做完。

**10）几个明确的判断：**
- 图数据库：**"图数据库是个糟糕的主意"**，SQL 2023 标准已加 property graph，服务端做遍历就够；他跟人在 HN 上打赌，2030 年前图库规模超不过关系库。
- 向量库：不会死，但会分化成"通用系统"或"像 Elasticsearch 那样的旁挂系统"，TurboPuffer 这类专精性价比的还活得不错。
- GPU 数据库：Nvidia 把 HeavyDB、Voltron 都收了，"它推这个是因为能多卖卡"，短期经济性存疑。
- DBA 岗位：调参、选索引这类活儿会被 agent 吃掉；数据建模和"看懂 agent 到底干了什么"的人还留着。
- OLTP+OLAP 融合：分析型起家再加事务型（Databricks/Neon、ClickHouse 上 Postgres）比反过来更顺；真正卡住的不是工程，是组织里两个团队都要"best of breed"。
- 极端可能：text-to-SQL 够好之后，**SQL 会变成汇编语言**——没人在写，但一切仍然编译到它。

---

## 二、X / Twitter

**OpenAI Codex & ChatGPT 团队的 Thibault Sottiaux** — 一条只有 "Done" 两个字母，6188 赞，配上前一条 "Landing sometime today by EOD PST"，明显是在宣布当天有东西上线（feed 里没说明是什么，不做猜测）。真正有价值的是另一条：

> "My work dot 'Burger' coordinated with my personal dot 'Dorito' over email at my personal dots request to get documents, which then coordinated with my CPA in order to file some tax stuff. Took 20 minutes. We're still so early."

中文：他让工作侧的 agent 和自己个人侧的 agent 通过邮件互相协调取材料，再去和自己的会计师对接，把报税的东西办了，全程 20 分钟。**这是"agent 之间用人类既有协议（邮件）互相办事"的早期样本**——没有 API 集成、没有统一编排层，直接复用现成通道。

https://x.com/thsottiaux/status/2111495392559067199
（"Done" 那条：https://x.com/thsottiaux/status/2111566005684289735 ）

---

**Replit CEO Amjad Masad** — 专门发帖澄清模型策略，回应 TC Disrupt 上的发言被误读：

> "Replit remains model agnostic... What I meant at TC Disrupt is that OpenAI is now our preferred partner powering Agent based on performance, cost, and strength of our partnership."

中文：Replit 仍是模型中立，用户可选 Anthropic 及其他模型；但**默认体验（也就是 Agent 的主链路）现在押在 OpenAI 上**，理由是性能、成本、合作深度。这句话对做 agent 产品的人有参考价值：多模型可选已经是标配话术，真正决定体验的是"默认路由给谁"。

https://x.com/amasad/status/2111494912562888939

---

**Box CEO Aaron Levie** — 今天传播最广的一条，直接反驳"AI 让软件工程失业"：

> "The biggest misread of anyone predicting the end of software engineering was imagining that the world only needed a certain amount of software... Exactly the opposite is happening where essentially most things are actually turning into software."

中文：唱衰软件工程的人犯的最大错误，是假设"世界需要的软件总量是固定的"，自动化只会减少人力。实际相反——因为 agent 会用工具、会操作电脑、能现场写代码、能像人一样处理数据（但快得多），**过去根本没法数字化的场景现在可以硬塞进"软件"里**。银行做新交易品类、生命科学的研究与实验、制造业的供应链自动化，第一顺位都是工程师。"未来我们不会手写代码了，但几乎所有东西都会是代码——懂代码的人位置极好。"

https://x.com/levie/status/2111525362446520466

---

**Peter Yang（AI 教程作者）** — 两条对 agent 工具链有直接用处：

(1) Claude Code 客户端体验变化：

> "the Claude Code app is much faster now and arguably simpler to use than ChatGPT. The only things missing still are better browser/computer use, remote control for all threads, and live voice."

中文：Claude Code 现在明显更快、用起来甚至比 ChatGPT 更简单；仍缺三块——更好的浏览器/电脑操作、所有会话的远程控制、实时语音。**这是一份很具体的竞品功能 gap 清单**，做 coding agent 产品可以直接对照。

https://x.com/petergyang/status/2111496600522805624

(2) 他自己有 45 个 app/agent 授权在 Google 账号上，写了个审计 prompt（全文可复制）：

> "Help me audit my Google app connections... 1. Review EVERY app across all connection categories. Ask me which ones I still use rather than guessing. 2. Open each app's details. Distinguish basic Google sign-in from permissions to access Gmail, Drive, Calendar... 4. Show me your recommendations before changing anything. Only disconnect apps I explicitly approve..."

中文：让 agent 逐个走查所有第三方授权，区分"仅登录"和"能读 Gmail/Drive/日历"，先给建议再动手，只断你明确批准的。**"45 个 agent 挂在一个 Google 账号上"正在变成常态，权限审计本身就该交给 agent 做**——这条 prompt 的关键设计是"先报告、后执行"，值得抄。

https://x.com/petergyang/status/2111508293818671449

---

## 三、一句话小结

今天所有信号指向同一件事：**agent 的能力已经跑在权限模型前面了**。Pavlo 在数据库层说"护栏"，Masad 在说"默认路由"，Peter Yang 在说"45 个授权没人管"，Sottiaux 在演示"agent 用邮件互相办事"——**缺口不在模型智商，在于谁有权做什么、出事了怎么回滚。**

其他几条（swyx 讲 AI Engineer 频道观众数据、Nan Yu 的"AI 之前我们在关注前端框架"、Nikunj 调侃 VC 融资轮次命名）属闲聊，未收录。

---
Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
