
# AI Builders Digest — 2026-11-28

今日主线：AIE Code Summit 上 Thariq Shihipar 的演讲把 2026 定性为「软件工厂」之年，并给出 2027 的关键词——**文艺复兴**。同一批人同时在讨论另一件更硬的事：**决策模型（decision model）正在被 agent harness 严重低估**。推特侧信号偏弱，多为感恩节闲聊，只挑有信息量的。

---

## 播客（今日重点）

### Latent Space — The Revolution vs The Renaissance（嘉宾：Thariq Shihipar，刚从 Anthropic 加入 OpenAI）

https://www.youtube.com/watch?v=Qe9d9dWyED0

**一句话结论：把「人」从 loop 里彻底拿掉是错的；2027 的竞争力不在于让 agent 更自主，而在于给 agent 造一个人类能看懂、能上手玩的中间层。**

Thariq 在 AIE Code 的闭幕 keynote 提出一个双轨框架：AI 同时是**工业革命**（效率、可靠性、标准化质量、规模）和**文艺复兴**（每一个边际质量提升都有价值、可以做极度个人化的东西）。他的判断是 2026 是软件工厂/工业化之年，接下来该轮到文艺复兴那一侧。两者不冲突，同一个项目里可以并存——比如游戏引擎用 WebAssembly 写死，上层脚本层留给人调。

**最具体的一条工程实践：`/human` 文件夹。** 他做游戏时最痛苦的体验不是模型写不出来，而是「我根本不知道发生了什么」——描述一个机制，模型做了一堆合理假设，等到玩的时候才发现某个角色在这个情形下会这样行动，非常迷失。解法是给模型划一个专门目录，里面是**真代码而不是文档**，但 lint 规则完全不同：高密度注释、禁止单字母变量、限制行长，目标是**每个文件读起来像 spec，但可以直接跑、可以直接改**。模型造底层原语，人在上面玩组合——「这个角色能不能同时放三道火墙」。

**他公开承认自己押错过的一个技术判断**：他一度是「Bash is all you need」的信徒（也信过「React is all you need」，因为模型只会写 React）。结论是错的：

> "The models as they get more general will just be able to work in whatever format you want."

模型在能力边缘时只会一种做法，能力变宽之后什么格式都行——包括**用 computer use 直接在 Figma 里画前端**。下游效果是人终于能看懂模型在干什么，而不必接受「模型自己在 loop 里造一坨不可维护的东西」。

**关于「完美平衡」的反直觉观点**：他做了个桌游 Frontier Lab（扮演前沿实验室，有经济/科学/文化胜利条件），让 Claude 跑了几千局模拟——结果永远是经济胜利通吃。他让 Claude 修平衡，**Claude 修得很差**，他把这当成一个 eval：模型是否理解「跨数千回合的系统」并能让通常必输的策略有时获胜。他想要的不是平衡而是**高方差**：

> "A perfectly balanced game is boring." 石头剪刀布是完美平衡的，所以无聊。你要的是弱但高方差——让人能靠 main 一个弱角色把 meta 玩出来。

**关于模型能力瓶颈，他讲得很干脆**：两个 $200 套餐都没打满，不缺 token，「我甚至不觉得自己被智能卡住了，可能被野心卡住了」——真正卡住的是**与模型协作的方式**。所以他会用模型去做自己并没有深厚专业的事（比如拿 Qwen 改权重让它以为埃菲尔铁塔在罗马，看下游怎么变），理由是「让更多天真的、但有一定水准的人去试，对大家都是好事」。他也提到自己在试一个「大概没人这么做」的 RL 想法。

**决策模型（他叫 system one model）是全场最被低估的东西。** 他的论据来自可解释性：一次前向传播之后模型其实已经知道答案了。Ilya 的经典例子——推理小说最后一句「凶手是 X」，那几个 token 零信息量，模型早就知道凶手是谁，后面纯粹是在白白解码。所以如果是「从一个数组里选哪个」这种问题，直接问分类头就行。**关键区分**：如果 token 在中间确实做了计算（需要 tool call 去查是哪一趟航班），那推理是必要的；否则就是浪费。

他给的具体场景是**客服机器人**——本质就是一棵决策树，需要时再 opt out 到推理。这正好卡在「全硬编码」和「每回合都 tool-calling loop」之间。他还吐槽这个品类的厂商不肯公布模型尺寸：「如果我告诉你它是 1B 模型，你对拿它做决策的感受会完全不同。」（对话里提到 OpenAI 的 Luna/Terra、JEV、TypeSafe 的命名，都是这个新品类在摸索叫法。）他顺手列了几个可能的变体：记忆模型、优先队列模型、以及「do what I meant, not what I said」——按精神而非字面执行。

**为什么值得关注**：如果你在做 agent 工具链，这里有两个可直接抄的东西——(1) 用 lint 规则差异把「人类可读层」做成真代码而不是产物文档；(2) 把高频、低推理需求的判断下沉到决策模型，只在需要计算时才升级到大模型。这两条都是成本结构上的动作，不是品味问题。

**其他值得一提的碎片**：他厌恶「人人抄人人」的多 agent 产品，想要自己的各个 bot 能互相说话——现在只是把它们都接到一个 txt 文件上，「Introduce yourselves」，让它们共享上下文。RSI 那段的观点也很克制：RSI 会把 AI 研究变成**知识工作**（做决策、分配资源、争取 buy-in），而不是模型全自动跑；他给的反例是 speculative decoding——「如果世界上没有那篇论文，你只跟模型说把推理做快，它大概只会去写暴力 kernel，不会想到训一个 draft model」，所以模型还不够有创造力。对 2026 的总结：

> "It's the year that AI sort of worked... simultaneously everything is very different and nothing is that different."

---

## X / 推特

**Box CEO Aaron Levie** — 现在是从零重造服务型公司、或把现有服务公司转型的窗口期，核心是「以 agent 为中心」。他的论证不是「agent 替代人」，而是**领域知识反而更值钱了**——想从 agent 里榨出价值仍然需要深度的行业理解，但交付能力有了 10X 乘数。结果是三件事同时发生：客户更满意、能抢到更多客户、以及能去做原来不在 TAM 里的更小客户。他点名广告、IT 转型、管理咨询、金融这些「历史上完全被人力速度约束」的行业。
为什么重要：这是目前对「agent 的商业价值落在哪」最清晰的表述——落在交付侧，不在软件侧。
https://x.com/levie/status/2125983542475894821

**OpenAI（Codex & ChatGPT）Thibault Sottiaux** — Codex 的 **banked reset** 上线（额度重置可结转保存），近 8000 赞。文字只有一句，但这是重度用户最关心的限额机制改动。
https://x.com/thsottiaux/status/2125853628250599730

**Replit CEO Amjad Masad** — 「Google 这次在 Gemini 4 上真的做出来了」，并在推 Replit 里试。
https://x.com/amasad/status/2126018746884243652

**OpenAI（Codex）Nan Yu** — 一个关于交互形态的判断：语音是 chat、往对话里发图是 chat、给一句指令拿回一个网站也是 chat。「这些事你现在在 ChatGPT 里全都能做。」潜台词是模型产品的界面正在重新收敛回单一 chat 入口。
https://x.com/thenanyu/status/2126036677642928363

**swyx（smol.ai / Cognition / Latent Space）** — 押注 agentic payments：「2028 之前最分裂也最重要的主题之一，没有中间态——要么早点下场，要么断言它永远不会发生。」
https://x.com/swyx/status/2126106139582677088

**fpv ventures 合伙人 Nikunj Kothari** — 去年感恩节怕忘了给重要的人发消息，结果 Claude 发现 iMessage 和 WhatsApp 在电脑上就是**本地数据库**，一路做成了个挺有用的小项目，脚本已开源（纯本地、不调 AI）。
为什么重要：又一个「模型 + 本地数据 = 个人工具」的低成本样本。
https://x.com/nikunj/status/2126133563292803100

**OpenAI CEO Sam Altman** — 提到 Ven 是最早相信「用当时的模型就能解千禧年数学难题」的人之一，并说「聪明 + 正确放置的自信和勇气」这个组合非常稀有。
https://x.com/sama/status/2125990371897557278

---

## 未收录

Peter Yang、Guillermo Rauch、Matt Turck、Zara Zhang（X 涨粉方法论，非 AI 主题）、Aditya Agarwal、Sam Altman 的家庭向推文——感恩节闲聊与个人内容，无工程信息量。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
