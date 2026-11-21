
已获取全部内容（feed 为 11-21 新鲜数据，15 位 builder / 31 条推文 / 1 期播客）。开始整理摘要。

**AI Builders Digest — 2026-11-22**

今天最硬的一条数据来自 Latent Space 那期 Linear COO 的访谈：**Linear 上超过 50% 的 issue 已经不是人创建的，而是 agent 创建的**。这是个很少被公开的具体数字，比任何"agent 元年"的宏大叙事都有说服力。

---

## X / 推特

### Box CEO Aaron Levie — Agent 的用法变了：给目标，别给步骤
他说今年模型能力有一次明显的跳跃：过去你必须非常精确地告诉 agent「怎么做」，否则几乎不可能成功；现在反过来，**你给 agent 一个自己都定义不清楚的问题，它给出的实现方案往往比你想的更好**，因为它能在远大于你的解空间里连线。他认为这会扩展到金融、法律、生命科学、网络安全等"没有人能装下全部行业知识"的领域，最终改变的是我们部署 agent 的方式——不是明确指令，而是给目标 + 足够的自由度。

> 为什么值得关注：这是对"prompt engineering 正在退化为 goal engineering"最清晰的表述之一，而且出自一个把 agent 卖给大企业的人，不是实验室里的人。如果你在做 agent 产品，产品形态（该给用户暴露多少控制权）会直接受这个判断影响。

https://x.com/levie/status/2123686350410912145

### Vercel CEO Guillermo Rauch — 给 AI 基础设施上一个"AI 版 SOC2"
他宣布 Vercel 的 AI 基础设施现在通过了 ISO 42001:2023 的年度第三方审计，把它比作"AI 领域的 SOC2"——第一个全球性的、独立审计的、关于公司如何构建/评估/监控/治理 AI 系统的标准。另一条推文里他提到用内部 pre-release 的 eve 做个人购物 agent，说当年做 hello world 时基础设施全缺，现在 agentcard、iMessage/WhatsApp 通道、性能都到位了，"可以在我们的 open intelligence stack 上交付一个你完全控制的 Muse/Instinct 级别的平台"。

> 为什么值得关注：agent 落地到企业，卡点正从"模型不够强"转向"合规审计过不了"。谁先把 AI 治理标准做成基础设施的默认项，谁就吃下受监管行业。这条对做 2B agent 的人比模型发布更重要。

https://x.com/rauchg/status/2123869175085191298
https://x.com/rauchg/status/2123879031049449791

### Zara Zhang — 别把 Claude Artifacts 交付给客户
"不要把 Claude Artifacts / ChatGPT 生成的网站发给你的客户。这会让客户觉得『这东西我自己 prompt 一下 Claude/Codex 就有了』。"

> 为什么值得关注：一句话点破了 AI 时代交付物的定价困境。当生成成本趋近于零，交付"能生成出来的东西"就没有溢价，溢价必须来自客户自己搞不定的部分（数据、集成、责任、运维）。做外包/咨询/工具的都该看一下这句。

https://x.com/zarazhangrui/status/2123813583339532321

### Swyx — 公开质疑 Cursor 的 agent 产品成熟度
他直接问："Cursor 的 origin 后来怎么样了？有人真的在实战里用过吗？有 actions / CI/CD 了吗？"另一条在预告 LangChain 的访谈：前 dbt 的 Josh Schottenstein 加入 LangChain 要做成一家 30 亿美元的公司，"而他们现在不得不从头重建内容、上下文（知识）和软件工厂"。

> 为什么值得关注：Cursor 从 IDE 转向后台 agent（origin）是今年 coding agent 赛道最大的赌注之一，但社区里"发布很久、没见人真用"的质疑是真实存在的。Swyx 是少数会公开问这种问题的人。

https://x.com/swyx/status/2123690305736396925
https://x.com/swyx/status/2123843282082132335

### OpenAI Codex 团队（Thibault Sottiaux / Nan Yu）— 桌面端大更新
Sottiaux："团队全员死磕，去升级桌面 app。更快、更简单、用起来舒服很多。"产品负责人 Nan Yu 补充这是"对那些一天要做几十到几百次的操作，做了大幅性能和 QoL 提升"。

> 为什么值得关注：coding agent 的竞争已经从"模型能力"打到"每天高频操作的摩擦"。这类更新不性感，但决定用户是否真的把 agent 留在工作流里。

https://x.com/thsottiaux/status/2123861214644347122
https://x.com/thenanyu/status/2123983081577267264

### Peter Yang — 把 Antigravity 变成手机上的远程控制
技巧帖：用 Antigravity 做 Gemini Neon 的人，可以在手机浏览器打开后「添加到主屏幕」，就能远程操控所有 Antigravity 线程。他的评价是：Antigravity 还没有移动 app，但这个远程控制比 Claude 的更好用，因为所有线程默认都在。

> 为什么值得关注：这是"agent 需要随身遥控器"这个需求的一个低成本解法。值得注意的隐含信号是——agent 产品的移动端体验现在是明显的空档。

https://x.com/petergyang/status/2123879309463228445

### 一个数学圈的集体时刻（Amjad Masad / Aditya Agarwal）
Replit CEO Amjad Masad：两个独立的黎曼猜想证明同时出现，一个 AI 一个人类，"如果都正确，最有趣的会是优雅程度上的差别"。SPC 的 Aditya Agarwal 则更冲："我们一边在解黎曼，一边在用一粒药丸干掉胰腺癌。但当然，咱们还是来争论一下『AI trade』好不好吧 lol。"

> 为什么值得关注：这是当下 AI 舆论里少见的、把"能力进展"和"市场情绪"直接对立起来的表达。当模型同时给出数学证明和药物发现的结果时，讨论"AI 是不是泡沫"的坐标系其实已经错位了。

https://x.com/amasad/status/2123874539218010491
https://x.com/adityaag/status/2124019178843894078

### Matt Turck（FirstMark Capital）— 一个关于"agentic 邮件"的冷笑话
有人为了在 Slush 大会见他，先发两封邮件，他回一次，对方紧接着又连发三封。他心想"这人是真的想见"。当天碰面，他说"看来是注定要见"，对方看了两眼他的胸牌，面无表情，说"哦你好"，然后走开。

> 为什么值得关注：这是对这种"用 agent 批量自动化外联"风气的精准吐槽。自动化把触达成本打到零之后，接收方的默认反应已经变成"这不是真人"——外联的信任成本反而变高了。

https://x.com/mattturck/status/2123777488786538982

---

## 播客

### Latent Space — Scaling Linear's GTM to $100M ARR（Cristina Cordova, COO）
这一期名义上是 GTM，但前半段全是 AI 产品形态的一手判断，信息密度很高。

**最硬的数据**：Linear 2025 年上线 MCP server（自称是所在品类第一家），**一年半之后，Linear 上超过 50% 的 issue 是由 agent 创建的**。她说"一半的工作是以完全不同的方式产生的"。

**她最反直觉的观点**：现在很多公司觉得"我只要当个数据库，开个 MCP server，把数据都交给 agent 就行"——她明确说这不是一个好商业模式。原话："你必须把 agentic 工作流带进你自己的工具里，而且要比别人在外面接你系统的工具更好。否则人就没有理由再进你的工具。"她的证据是：MCP 用量和 app 用量在同步上升，而不是此消彼长——因为 chat 界面不适合可视化团队工作，而且基本是单人游戏，不利于协作。

**产品怎么落**：Linear 推出 Loops（自动把 agent 指派给某个 issue 并开始写代码）、Triage Intelligence（进来的 bug/需求自动打标、分派、排队，"不是所有东西都需要是个 agent，它可以只是产品的一部分"）。coding session 里用户可以在 OpenAI 或 Anthropic 的模型和 harness 之间选，按官方 API 价格上浮一点收费；Linear Agent 的对话是免费的，目前全用 frontier 模型而非开源。

**最值得琢磨的一句**：她说 MCP server、agents 平台、和 Codex / Cursor / GitHub Copilot 的合作，"**这些没有一件是计划内的**"。于是他们的产品路线图现在最长只做六个月，"因为谁知道会变成什么样"。

> 为什么值得关注：这是一个 SaaS 公司被 agent 从底层改写产品形态的完整样本——从"人点界面"到"agent 创建一半的工作"，从 seat-based 到 usage-based 定价，从年度路线图到六个月路线图。如果你在做 自研引擎 / Agent 工具链，这里有三个可以直接拿走的判断：MCP 只是入口不是护城河、agent 工作流要内建、路线图要缩短。

https://www.youtube.com/watch?v=x0VSm6IjcDQ

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
