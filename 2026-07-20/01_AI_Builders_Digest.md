
AI Builders Digest — 2026-07-20

**X / Twitter**

**OpenAI Codex & ChatGPT 的 Thibault Sottiaux：ChatGPT Work 正在从“聊天”变成“任务委派界面”**  
短摘要：Thibault 展示了一个典型 ChatGPT Work 用法：直接口述任务，让 ChatGPT 扫描大量 Twitter DM，筛出提到 ChatGPT Work 的申请者，抽取姓名、DM 链接、内容、工作类型分类、workflow 成熟度评分，并生成 spreadsheet。他还说自己的工作已经基本变成“delegating to ChatGPT Work”，并强调它覆盖建站、邮件管理、文档总结、docs/sheets/slides 创建等工作流。  
为什么重要：这很贴近 Agent 工具链的真实产品形态变化：不是单点 prompt，而是“自然语言任务描述 + 跨应用数据读取 + 分类判断 + 表格产物”的工作流执行。对自研引擎来说，关键不是 UI 聊天，而是权限、上下文接入、任务分解、产物格式化和可回溯链接。  
链接：  
https://x.com/thsottiaux/status/2078702412085498087  
https://x.com/thsottiaux/status/2078697741455356367  
https://x.com/thsottiaux/status/2078697631019303273

**Vercel CEO Guillermo Rauch：前沿开源模型的网络安全能力已经到来**  
短摘要：Rauch 基于 Vercel 内部 eval 表示，Kimi K3 在 cybersecurity 上是 top-tier，Moonshot benchmark-overfit 的质疑没有被他们的 stealth eval 支持；Sol 的 cyber 能力更强但成本也显著更高；Fable 在测试中几乎拒答，无法完成 run。他的结论是：frontier open-weight cybersecurity capability 已经出现。  
为什么重要：这对 LLM infra 和 coding/security agent 都是信号：模型能力差异不能只看公开 benchmark，需要贴近真实任务的内部 eval；同时，安全策略本身会影响 agent 能否完成防御性任务。做自研 agent engine 时，模型路由、任务类型 eval、拒答率、成本和防御性 cyber 能力要一起评估。  
链接：https://x.com/rauchg/status/2078647648307880209

**Box CEO Aaron Levie：企业 AI 生态不会只被少数模型公司吃掉**  
短摘要：Levie 认为过去几个月已经说明，AI 价值不会只集中在少数 frontier labs。未来会同时出现多层生态：企业和 applied AI 公司调优并托管自有模型；面向法律、IT、安全、HR、客服、coding 等业务流程的应用层公司；垂直领域 lab；用于运行、治理、保护、编排模型和 agent 的新基础设施；以及帮助企业完成 AI change management 的服务公司。他还认为模型 gatekeeping 在全球竞争中不可持续，美国更应该安全地推动扩散、基础设施和 OSS。  
为什么重要：这几乎是 Agent 工具链的市场地图。自研引擎的机会不一定在训练 frontier model，而在企业数据接入、agent orchestration、治理、权限、审计、模型路由、workflow adoption 这些“扩散层”。  
链接：  
https://x.com/levie/status/2078567715544121815  
https://x.com/levie/status/2078481578779685245

**Zara Zhang：每个人都应该有自己的 AI 模型 eval set**  
短摘要：Zara 建议每个人建立“personal eval set”：一组真正和自己日常工作/生活相关的任务。行业 benchmark 有用，但未必反映模型对你是否真正有用；能力边界需要通过反复试探、撞到边界来发现。她还指出，企业 AI adoption 的最大障碍是：懂 AI 的人不懂业务，懂业务的人不懂 AI。  
为什么重要：这对自研 agent 和内部工具落地非常直接。通用 benchmark 只能做初筛，真正决定产品质量的是业务相关 eval、用户 workflow 采样、失败案例沉淀，以及让业务专家参与评估闭环。  
链接：  
https://x.com/zarazhangrui/status/2078666187026911488  
https://x.com/zarazhangrui/status/2078492577788268549

**Matt Turck：模型层还没有商品化**  
短摘要：Matt 用一句反讽总结行业叙事：“2024/2025/2026 都在说 model layer is commoditizing，但模型层仍然没有商品化。”  
为什么重要：对产品和 infra 决策来说，这意味着不能过早假设“模型都一样”。Agent engine 仍需要面向模型差异设计：能力矩阵、成本曲线、延迟、工具调用可靠性、长上下文表现、拒答策略和任务特化 eval。  
链接：https://x.com/mattturck/status/2078520552680046920

**Podcasts**

**Unsupervised Learning — Ep 90: AI Pioneer Jürgen Schmidhuber on the State of AI Today**  
The Takeaway：Schmidhuber 的核心观点是，真正下一阶段的 AI scientist 不只是更会读网页和写代码的 LLM，而是能通过自己的行动生成数据、训练 world model、规划下一步实验的系统。

短摘要：Schmidhuber 回顾了 recursive self-improvement、meta-learning、自修改机器等路线，并承认当下让预训练模型“写代码、改自己的代码”是合理路径，但它仍受限于人类生成数据。他更看重“人工科学家”：系统在未知环境中预测自身行动后果，通过实验创造训练数据，再用 world model 做规划。他的关键表述是：“Babies don't learn by downloading the web... They learn by predicting the consequences of the actions.” 他还认为，网页数据只是所有可通过实验收集数据的极小一部分，未来更重要的是 artificial curiosity 驱动的自生成数据闭环。

为什么重要：这给 Agent 工具链提供了一个更底层的判断框架：当前 coding agent 多数仍是“读上下文、调用工具、改代码”的静态循环；下一步更强的 agent 需要能主动设计实验、收集反馈、更新环境模型，并围绕任务目标规划探索。对自研引擎而言，eval harness、sandbox、可观测性、行动日志、反馈学习和安全护栏会比单纯 prompt engineering 更关键。  
链接：https://www.youtube.com/watch?v=RKjR8DQ40po

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
