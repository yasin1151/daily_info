
**GitHub Trending 日报 · 2026-11-15**

今天的热榜几乎被同一个主题占据：给 coding agent 装上工具——浏览器权限、代码审查、计划评审台，以及把它们烧掉的 token 省回来。纯模型侧项目只剩一个 Zig 写的推理引擎。

---

## 一、今日涨幅榜

**1. alibaba/open-code-review —— 阿里开源的代码审查 Agent**
把审查拆成两层：确定性流水线负责可规则化的检查（NPE、线程安全、XSS、SQL 注入，内置多语言规则集），LLM Agent 只负责需要理解上下文的部分，输出精确到行的评论，兼容 OpenAI / Anthropic 接口。
*为什么值得关注*：今日涨幅第一（+897）。架构思路最值得借鉴——不让模型干它不擅长的活，规则引擎先筛掉确定性缺陷，模型只处理剩余部分，Token 成本和误报都可控。README 强调"在阿里内部规模上跑过"，是硬背书。
★ 51,404（+897）｜Go｜https://github.com/alibaba/open-code-review

**2. ChromeDevTools/chrome-devtools-mcp —— 让 coding agent 接管 Chrome 调试器**
把 Chrome DevTools 的能力包装成 MCP 服务，agent 可以直接读 DOM、抓网络请求、看 console 报错，而不是靠截图猜页面。
*为什么值得关注*：这是今天 star 总量最高的项目之一（5.6 万）。它解决了 agent 做前端调试时最根本的盲区——看不见运行时。配合 DevTools 团队官方维护，长期会变成前端 agent 的标准配件。
★ 56,272（+673）｜TypeScript｜https://github.com/ChromeDevTools/chrome-devtools-mcp

**3. GoogleChrome/modern-web-guidance-src —— 给 agent 喂最新的 Web 最佳实践**
Chrome 团队把 Web 平台的最新变更整理成 agent 可消费的知识源，让 coding agent 生成的代码不落后于规范。
*为什么值得关注*：今日涨幅第一（+1,225）。模型知识有截止日期，但 Web 平台每月都在变，这个项目承认了这个事实并用"持续投喂"解决它。对做 agent 上下文工程的人是个可复用的范式：与其微调，不如维护一份权威知识源。
★ 5,989（+1,225）｜TypeScript｜https://github.com/GoogleChrome/modern-web-guidance-src

**4. backnotprop/plannotator —— Agent 的计划评审台**
一个让你留在 agent 循环里的工作台：拆解任务、做决策、写计划、标注、审代码，全部在一个界面里完成并能分享出去。
*为什么值得关注*：它押注的是"人机协同的方式要变"——不是 agent 干完人验收，而是人在计划阶段就介入。今天 +412，说明"human-on-the-loop"这类工具正在从概念变成刚需。
★ 11,095（+412）｜TypeScript｜https://github.com/backnotprop/plannotator

**5. dream-num/univer —— 自建 AI Office 的 SDK**
一套 Office SDK，把表格编辑、计算、协作、文件处理能力打包，让你在自己的产品里嵌入"AI 版 Excel"。
*为什么值得关注*：+495。AI 应用层正在从"聊天框"往"文档/表格界面"回摆——因为用户真正的工作发生在表格和文档里。这类底层 SDK 是这波回摆的卖水人。
★ 24,463（+495）｜TypeScript｜https://github.com/dream-num/univer

**6. tradermonty/claude-trading-skills —— 炒股专用的 Claude Skills**
面向股票投资者的技能包：行情分析、技术图表、经济日历等，装进 Claude Code 就能用。
*为什么值得关注*：+556。它是"垂直领域 Skills 包"这一品类的典型样本——不写代码，只写提示词和工具约定，就能做出一个产品。同时也提醒一件事：这类包的可靠性完全取决于作者，金融场景尤其要自己复核数据源。
★ 4,779（+556）｜Python｜https://github.com/tradermonty/claude-trading-skills

**7. Alishahryar1/free-claude-code —— 11 个 harness 的免费额度聚合**
把 Claude Code、Codex、Antigravity、VSCode、Pi、OpenCode 等 11 个 agent 客户端串起来，宣称可白嫖 13 亿 token 额度。
*为什么值得关注*：+367，总星 7 万。这类项目的热度本身就是个信号：模型厂商的免费额度已经多到值得专门写工具去薅。但风险同样明显——违反服务条款、额度随时可能被收回，不适合生产使用。
★ 70,217（+367）｜Python｜https://github.com/Alishahryar1/free-claude-code

---

## 二、结构性信号：token 经济学与 Skills 生态

**8. JuliusBrussee/caveman —— 省 65% token 的代理**
一个"原始人语"技能 + 代理：让 agent 用最少的词说话，官方称可削减 65% 的 token 消耗。
*为什么值得关注*：总星 12 万，是今天榜上体量最大的项目之一。"为什么用很多 token，当很少 token 能做到"——这个粗暴的命题能火，说明省 token 已经从优化项变成主线需求。代价是可读性和潜在的理解损失，适合批处理不适合交互。
★ 120,050（+227）｜Go｜https://github.com/JuliusBrussee/caveman

**9. headroomlabs-ai/headroom —— 在到达 LLM 之前先压缩**
压缩工具输出、日志、文件和 RAG 片段，官方数据是 coding agent 少用 20% token。
*为什么值得关注*：和 caveman 同一赛道但方向相反——一个压输入的表达，一个压输入的体积。8 万星说明上下文压缩正在形成一个独立的基础设施层，未来大概率会被内置进各家 harness。
★ 79,671（+93）｜Python｜https://github.com/headroomlabs-ai/headroom

**10. NVIDIA/SkillEvaluator —— 给 agent skills 做评测和质量门禁**
多层级框架，评估 AI agent 技能的质量：语义重叠检测、合成数据生成、质量门禁。
*为什么值得关注*：+168，总星不高但方向关键。Skills 生态现在是一片无标准的野生市场，谁定义评测标准谁就掌握话语权。英伟达来做这件事，动机很清楚。
★ 1,252（+168）｜Python｜https://github.com/NVIDIA/SkillEvaluator

**11. anthropics/claude-plugins-official —— 官方插件目录**
Anthropic 自己维护的高质量 Claude Code 插件清单。
*为什么值得关注*：+137，总星 4.7 万。官方下场做目录，等于承认第三方 Skills 生态已经失控到需要人工筛选。对使用者来说，这是目前唯一相对可信的入口。
★ 47,299（+137）｜Python｜https://github.com/anthropics/claude-plugins-official

---

## 三、新上榜 / 值得盯

**12. Tencent/LoopForge —— 腾讯自托管的 coding-agent 交付流水线**
用脚本和人工审批关卡编排 CodeBuddy、Codex、Claude Code，覆盖从需求到 SDLC 的流程，标签里有 agent-orchestration、human-on-the-loop、self-hosted。
*为什么值得关注*：今天新上榜（+101），总星才 884，属于早期。但方向对：企业不缺单个 agent，缺的是把 agent 塞进已有研发流程的编排层，而且必须自托管——数据不出内网是硬约束。
★ 884（+101）｜Go｜https://github.com/Tencent/LoopForge

**13. andrewyng/openworker —— 吴恩达的桌面 Agent 应用 + Harness SDK**
两个东西打包：一个做调研、写作、审代码的桌面 App，和一套让你自己搭 agent 应用的 Harness SDK。可接云端或本地模型，权限和审批可控。
*为什么值得关注*：+94，总星 1.9 万。吴恩达团队的产品选择很有指向性——不做又一个聊天框，而是做"覆盖你已有工具的桌面层"。SDK 化则说明他们想当别人的底座。
★ 19,218（+94）｜Python｜https://github.com/andrewyng/openworker

**14. ag-ui-protocol/ag-ui —— Agent 与前端之间的交互协议**
把 Agent 接入前端应用的协议标准，定位类似"Agent 世界的 HTTP"。
*为什么值得关注*：今日新上榜但只 +9，相对冷清。协议类项目向来如此——先有共识才有价值，现在还在赌局早期。如果 agent 前端真的标准化，这类项目是绕不过的一层。
★ 17,346（+9）｜TypeScript｜https://github.com/ag-ui-protocol/ag-ui

**15. ashhart/TensorFold —— Zig 写的跨后端 LLM 推理引擎**
一套代码支持 Metal、CUDA、Vulkan，用 Zig 做统一后端。
*为什么值得关注*：+53。今天榜上唯一的推理侧项目。Zig 的价值在于能同时吃透编译期优化和底层内存布局，做推理引擎很对路。体量小（2.1k 星），属于赌未来的技术选型。
★ 2,154（+53）｜Zig｜https://github.com/ashhart/TensorFold

**其他**：microsoft/PyRIT（AI 红队扫描工具，★4.8k +22）持续在榜但今日无爆发；martin-olivier/airgorah（Rust WiFi 安全审计，★5.8k +269）与 AI 无关，未展开。

---

## 编辑观察

1. **Trending 已经被 Claude Code 生态"殖民"**。今天 32 个上榜项目里，标题或简介里带 Claude / agent skill 的超过一半，其中不小比例是"某领域 Skills 合集"——写提示词清单，几乎零技术门槛。热度真实，但同质化严重，多数会在一周内消失。
2. **token 压缩成了新战场**。caveman（12 万星）和 headroom（8 万星）同时在高位，说明"上下文成本"已经从工程师的私活变成有名字的产品品类。
3. **大厂开始补"编排层"而不是"模型层"**。阿里出审查流水线、腾讯出 LoopForge、Chrome 团队出 MCP 和知识源——都在抢占 agent 与现有工程体系之间的接缝，而不是再造一个模型。这个位置一旦占住，比模型本身更难替换。
