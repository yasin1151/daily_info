
**AI Builders Digest — 2026-11-04**

今天的内容 12 位 builder、29 条推文、1 期播客。主线很集中：**Agent 的运行时（工作区 + 权限）、模型路由被平台内置、以及"harness 比模型更影响体感"**。播客是 Latent Space 对 Legora CTO 的深访，讲的是"完全看不到用户数据时怎么把法律 Agent 做对"，对自研引擎和 Agent 工具链参考价值最高。

---

## X / Twitter

**Vercel CEO Guillermo Rauch：无状态沙箱是错误的基准线**
他的判断是 Agent 只有"带着自己的工作区"才有用，身份、skills、repo、记忆都得跟着走，把冷启动毫秒数当核心指标是量错了对象。同时他对 WebMCP 非常看好，认为让网页向 Agent 暴露结构化能力这个方向值得押注。顺带提到 Vercel Sandbox 已铺到 19 个区域、需求周环比双位数增长。
值得看：这是一条会直接决定架构的假设，不是细节。状态连续性和冷启动是两套不同的设计。
https://x.com/rauchg/status/2117338179535810957
https://x.com/rauchg/status/2117419661654720671

**Replit CEO Amjad Masad：Agent 应该跑在组织可控的专用环境里**
原话是 AI agents 应该在专用的、组织可控的环境中运行，每个任务只拿到它所需的有限资源。这是"Agent 权限模型"的标准答案，和 Rauch 的工作区论是同一枚硬币的两面：一个是状态连续性，一个是权限边界。
https://x.com/amasad/status/2117499074496872882

**OpenAI（Codex 与 ChatGPT）Thibault Sottiaux：模型路由做成默认能力**
"你那个点会替你在任务里挑最合适的模型，不同环节调用不同的模型。"产品层把路由内置，不再让用户手选。同一天他还提到团队在 Git 相关能力上有新东西、终于可以公开讲。
值得看：路由从"框架里自己写"变成"平台免费内置"，会压缩中间层的空间。
https://x.com/thsottiaux/status/2117283355427495983
https://x.com/thsottiaux/status/2117412956950638872

**前 Anthropic Claude Code 团队成员 Thariq：200 美元档就够用**
一周体验后的结论是"你不需要无限 token 也能做出好东西"，并补了一句更关键的判断：这是智能有史以来最贵的时候。做成本模型时如果把"token 无限"当前提，通常会系统性高估未来支出。
https://x.com/trq212/status/2117305792923889731

**AI 教程作者 Peter Yang：最好的写作模型被 harness 拖累**
他让 ChatGPT 和 Gemini 同时改稿，Gemini 的建议明显更好；但 Antigravity 的 browser use 基本不能用，他只能把 Gemini 的修改一条条粘回 ChatGPT 在浏览器里落地。"模型能力"和"产品可用性"是两件事，harness 的一票否决权经常被低估。
https://x.com/petergyang/status/2117333424403042330

**Every CEO Dan Shipper：同一件事的另一半证据**
他认为 Argon 好用，一半是它本身好，一半是 Antigravity"还卡在 2025 年"，没堆那么多复杂功能与复杂度。
https://x.com/danshipper/status/2117363007340609556
https://x.com/danshipper/status/2117428596688171450

**YC 总裁 Garry Tan：多 captain + 子线程，吞吐量 5 倍**
用 Capy Captains 把 issue 修复吞吐量一夜之间提高约 5 倍，他的说法是"能在 captain 和子线程之间协调是一个疯狂的解锁"。
值得看：这不是模型变强，是编排结构变强。多 Agent 分工 + 任务树是目前少数敢给出实测倍数的说法。
https://x.com/garrytan/status/2117410016730964358

**OpenAI Codex 产品 Nan Yu：多人 AI 的冷水**
"除了极少数场景，群聊是一种糟糕的多人 AI 体验，几乎必然产出 slop。"多人 + Agent 的产品形态远没定，别默认"拉个群"就是协作。
https://x.com/thenanyu/status/2117432599559716940

**SPC 合伙人 Aditya Agarwal：语音输入跑到 20 亿美元**
Wispr Flow 完成 2.8 亿美元 B 轮、20 亿美元估值，创始人 Tankots 是四届创业者兼 IOI 奖牌得主。
https://x.com/adityaag/status/2117314981355761

---

## 播客

**Latent Space｜Building Legal Agents When You Can't See the Data — Legora CTO Jacob Lauritzen**
https://www.youtube.com/@LatentSpacePod
（该源只提供频道链接，没有单集 URL）

**一句话总结：** 这类垂直 Agent 最难的地方不是模型，而是在完全看不到用户数据的前提下，还得把 Agent 做对、把 evals 建起来。

Legora 是 YC24 的斯德哥尔摩公司，起点就是"ChatGPT + 瑞典法条 + 搜索"。现在 100 名工程师，Tabular Review 一天能跑上百万单元格（前端用 ag-Grid），产品被他形容成"给律师用的 CoWork"。

**数据盲区是他们最真实的产品约束。** 客户数据本身属于律所的客户，Legora 看不到任何 trace："这里有个 agent，能做很多惊人的事，而我完全不知道人们到底在拿它干什么。" 对策有三层：合成/改写数据、按失败模式分类（"我们知道失败模式大概就是这十到二十种"），以及一个 3 名工程师 + 3 名律师 + 百人级 legal engineer 池的 evals 团队，按 practice area × task 维护一张性能热力图。

**反直觉的一条：新模型经常在某些任务上退步。** "很多次发布是改进了大部分、回退了某一部分，比你想的更常见。" 所以"等下一个模型解决"有保质期。他举了个确实白捡的例子：引用准确率从 70% 到 99%，他们一行代码没改。

**模型策略是 arbitrage，不是选边。** 按子任务路由，不指望律师理解"这是 Sonnet high 还是 Opus mid 的任务"——"律师一小时收 1000 美元，你只要让它能跑"。他们现在开始 post-train，但不训主 Agent（"我们赢不了 Anthropic"），只针对法律检索这种 fan-out retrieval 任务后训练小模型，换延迟和成本。

**架构上最值得抄的是 Lists 作为 primitive。** 它"像一个 Notion database"，可以配触发器、自动化；Agent 能建 list，list 能触发 Agent，互相读——"Agent swarm 就活了"。按他的说法，这相当于用 Linear 协调一堆 coding agent 的那套玩法。两次收购（瑞典 Kira、英国 Wexler 的 litigation fact intelligence）都建在这个 primitive 上。

**关于 harness 的两个具体细节：** 一是他们的 Word 插件在 MapReduce 和"全塞进 context"之间来回改了好几次——"我们一直在换模型外面那层脚手架"；长文档跨块推理（两页讲一件事，单块都不相关、合起来才相关）依然是硬问题。二是模型性格：Opus 和 Fable "extremely chatty"，Astra 简洁得多，而且很难用 prompt 压下去。

**最后一句最扎人的：没人验证引用。** 他们做了多层可点击引用（能点回 PDF 的 bounding box、能点回 Tabular 的单元格），"但律师根本不验证。这和写代码一样，有工程师完全不管、直接把 agent 输出发出去，也有人每个逗号都读。"

他对形态的判断：律所会直接在 Legora 里干活，大企业会用 Claude/Copilot 去调 Legora——"就像我用 Claude 操作 Linear，但我还是会打开 Linear。" 另外他在琢磨一个更大胆的问题：**"Agent 能不能就是 API"**，卡点是执行成本和延迟不受控，以及一百次里有两次会干出格的事。

---

今日无官方博客更新。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
