
数据齐备（16 位 builder / 33 条推文 / 1 篇官方博客，feed 生成于 2026-09-17，新鲜）。以下是本次摘要。

---

# AI Builder 动态 — 2026-09-18

本期主线只有一件大事：Anthropic 把 Cowork 和 chat 合并成一个 Claude，并把 Docs / Slides / Design 塞进对话里。围绕它，几位 Claude Code 核心成员同时发了一轮"Agent 该怎么造"的反思，另有若干新模型代号在圈内被同时点名。

---

## 一、主线：Claude Cowork 与 chat 正式合并，文档/幻灯片/设计内置进对话

**来源：Anthropic 官方博客 + Boris Cherny / Cat Wu / Alex Albert / Claude 官方号**

官方博客《Claude Cowork and chat are now one Claude》宣布，从今天起 Cowork 和 chat 合并成一个 Claude，先向 Pro 和 Max 计划推出，未来几周铺开。核心变化是"不再让你选产品"：给 Claude 一个模糊任务，它自己判断该给快速回答还是做更深的 agentic 工作，以及输出成什么形式最合适。同时 Claude Docs 和 Claude Slides 当天上线、Claude Design 改为在任意对话中可用，三者都在付费计划 beta 中，可直接编辑、直接从 Claude 演示、或导出 PowerPoint/PDF。

Claude Code 团队的 Boris Cherny 把这件事讲得更清楚：Claude Code 证明了 AI 能做真实工作（"把 feature 交给 Claude，回来就是已交付的代码"），Cowork 证明了知识工作者也一样（"把 brief 交给 Claude，回来就是完成的文件"），今天的合并意味着"一个带着上下文到处跟着你的 Claude"。Cat Wu 补充了设计动机：用户反馈不想再纠结"这个任务该用哪个 Claude"，模型够强了就让它自己做路由，但"你全程有控制权，随时可以打断、改方向、调它的投入程度"。Alex Albert 的评价是"合并后的 UX 比单独的 chat 或 Cowork 都好"。官方号强调老用户无损迁移："chats、projects、artifacts、connectors 和 skills 都还在原地"。博客里还埋了一个真实用户案例，Senior Economist Andrew Keller 说他会让 Claude 去法研数据库里拉全部判例、读完、判断还缺哪些判例、下载并存进文件夹。企业侧留了缓冲：Enterprise 管理员会提前 30 天收到通知。

**为什么值得关注：** 这是 chat 产品和 agent 产品分界线的正式消失。对做 Agent 工具链的人来说，最值得抄的两点：一是"路由交给模型自己决定"（省掉了产品层面的模式选择），二是 Cowork 的 skills / connectors / artifacts 全部保留，说明 Anthropic 把"技能 + 连接器"当成了长期资产而非模式专属功能。

- https://claude.com/blog/cowork-is-now-claude
- https://x.com/bcherny/status/2100259951398789487
- https://x.com/_catwu/status/2100260655312089562
- https://x.com/alexalbert__/status/2100295757953917120

---

## 二、Agent 工具链：bash 不再是答案，"按你要的形状给工具"

**来源：Thariq（trq212，Anthropic Claude Code）**

三条连续的思考，是本期对自研 Agent 引擎最有参考价值的内容：

1. "如果你的目标只是可靠地做 tool calling，bash 已经不再是你需要的全部了。但 sandbox + bash 对于涉及代码生成与执行的活儿仍然好用。"（356 赞、50 回复，是这轮讨论里反响最大的一条）
2. "越来越多情况下，你可以直接给 Claude 按你想要形状做出来的工具，而不是用一层间接层去骗它。比如存数据，你真的想要一个文件系统，还是想要一个数据库的 API？" 他补充说这是他自己"相对去年的一次更新"。
3. 评价 Claude Managed Agents："沙箱是可选的，可以脱离 agent loop 的其余部分独立拉起，这个平衡点找得对。"他还说自己把一个老的 bash tool calling 项目移植到 CMA，跑得很好。

**为什么值得关注：** 这几乎是对"Agent 引擎 = 沙箱 + bash 万能论"的正面修正。趋势判断是：文件系统这种"通用但语义模糊"的接口会让位给结构化、领域化的工具 API；沙箱的价值收窄到"需要跑代码"的场景，而不是默认网关。

- https://x.com/trq212/status/2100315535758217422
- https://x.com/trq212/status/2100315537251463523
- https://x.com/trq212/status/2100315538472009897

---

## 三、模型与推理基础设施：同一天冒出"Jev""GPT Luna""Astra"几个代号

**来源：Vercel CEO Guillermo Rauch、Every CEO Dan Shipper、OpenAI 的 Thibault Sottiaux、Box CEO Aaron Levie、OpenAI 的 Sam Altman**

这条是本期的"信号噪声比"观察，几位互不相关的人在同一天点了同一批名字。

Guillermo Rauch 说 Vercel 的 fx 默认模式现在是 auto，每条命令都由一个安全审查器分析，"这个审查器今天跑在 GPT Luna 上"；同时提到 Jev"p95 延迟最多快 18 倍，而且更准"，将进 Vercel AI Gateway 并很可能成为新默认。Dan Shipper 用一张两栏对照图吐槽：左边"LLM 只是自动补全"，右边"jev 只是 JSON 分类器"，底下握手加一面红旗，等于说"这俩其实是一回事，别拿'只是分类器'当贬低"。

OpenAI 侧，Codex & ChatGPT 的 Thibault Sottiaux 发了一条极简预热：Astra，"快、前沿、高效、人人可用"，四条对勾（4485 赞）；同一天稍晚还发了句"有时候物理规律是骗不过的"（5415 赞）。Sam Altman 则说本周最想发的东西要推到下周，"但我觉得值得等"（8692 赞）。Box CEO Aaron Levie 从企业视角补了一句：还有"成片的 AI 创新版图根本不在我们雷达上"，能极快、极便宜、且保持高能力地处理信息，对大量企业任务意义巨大，他点名数据分类、工作流内的路由决策、特定领域问题上的决策、安全相关的快速判断，都正是很多流程里的闸门，"这种模型和路线在企业 agentic workflow 里可能相当有意思"。

**为什么值得关注：** 三个代号同天出现、且都围绕"快 + 便宜 + 足够强"这条轴，加上 Altman 的推迟表态，说明下一波竞争点不在"更强"，而在"同能力下把延迟和成本打下来"。Levie 那段等于告诉你这类模型的第一批真实需求场景是分类、路由、审批这类"流程闸门"，而不是写代码。

- https://x.com/rauchg/status/2100307962262872105
- https://x.com/danshipper/status/2100251499443998766
- https://x.com/thsottiaux/status/2100297380968997327
- https://x.com/sama/status/2100351958167220547
- https://x.com/levie/status/2100448648672993540

---

## 四、值得单独记一笔的四条

**Zara Zhang（zarazhangrui）对 Claude 说话方式的吐槽成了小热点：** "我最近用 Claude 越来越少了，因为它的说话方式已经变得让人受不了。它总是在展示自己多聪明多高级，而不是真的把一个观点传达清楚。"（1830 赞、306 回复）括号里是整条帖子的措辞，值得原样保留，因为它代表的情绪在合并公告的评论区里相当普遍：功能上做加法，语气上做减法，是两件事。

- https://x.com/zarazhangrui/status/2100278750776824115

**Peter Yang 用 8 个 skill 做完整个播客：** /podcast-prep 做嘉宾调研并生成访谈提纲、/podcast-edit 读原始转录并共同挑选片头和要剪的片段、/podcast-production 编排 5 个 skill 把整集变成 6 份资产。他特意反驳了"模型变强了 skill 就多余"："对我没用，skill 是让 AI 遵守我特定的剪辑和 browser-use 指令的唯一办法。"

- https://x.com/petergyang/status/2100328939034128856

**Nikunj Kothari 的 NousResearch "Home" agent 已进家庭日常：** "断断续续折腾了几个月，现在真的很好用了。这也是我们第一个'群组'bot，我和我太太每天都用它，失败的时候尤其长见识。我试过用 Grok Bot 之类复刻，拿不到这种粒度的控制，比如只读指定邮件、把行内附件转成结构化数据、或者带登录态的浏览器会话。"

- https://x.com/nikunj/status/2100212813625196917

**Garry Tan 提到 harness 可替换、记忆与人格连续：** "我可以用任何我想用的 harness，而它还是同一个性格、完整记忆的我的个人 AGI。"（512 赞）一句话点出 agent 记忆层与执行层解耦的方向。

- https://x.com/garrytan/status/2100339347669279149

**Madhu Guru（Meta AI 高级总监，前 Google 主导 Gemini/Veo/Nano Banana）：** "安全和保障是你的 AI 产品和模型的*特性*，不是需要从外部强加给你的护栏。"措辞上的"特性 vs 护栏"之分，对做 Agent 产品的人有实际设计含义。

- https://x.com/realmadhuguru/status/2100312717739667963

---

## 五、官方博客

**Claude Blog：Claude Cowork and chat are now one Claude**（2026-09-16）
已在第一节展开。补充三个数字/条款层面的要点：Pro 与 Max 先行，Team 与 Free"很快跟上"，Enterprise 管理员至少提前 30 天收到变更通知；Cowork 单独使用不受影响；默认行为是"执行前先问"，可以改成"只在需要细看时才找你"。博客结尾一句挺有画面感："如果你一直攒着某个又大又乱的项目，现在正是时候。"

- https://claude.com/blog/cowork-is-now-claude

*本期无播客更新。*

---

**一句话总结：** 产品和工具层面最大的动作是 Anthropic 抹掉 chat / agent 的产品分界，把路由交给模型；技术讨论层面最有价值的是 Claude Code 团队明确否定"bash 万能论"，主张按领域形状给工具；市场信号层面则是"快、便宜、够强"这类模型（Jev、GPT Luna、Astra）开始被企业场景明确点名。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
