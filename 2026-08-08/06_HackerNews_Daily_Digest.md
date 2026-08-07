
已完成：扫描到 20 篇新帖，已标记全部已读。以下是我筛出的 10 条高价值内容，按技术相关度优先整理：

1. **Oracle 禁止 OpenJDK 提交 AI 生成代码**
   - **摘要**：Oracle 明确禁止将 AI 生成代码提交到 OpenJDK 仓库、PR 或项目沟通中，但允许开发者私下用 LLM 做调试和审查。文章也对比了 Oracle 高管“AI 已在写代码”的内部叙事，凸显开源治理与合规边界的冲突。
   - **为什么值得关注**：这是大型开源项目对 AI 代码进入主干的明确政策信号，可能影响 Java/企业级开源协作规范。
   - **原文链接**：https://app.dealroom.co/news/feed/oracle-bans-ai-generated-code-from-openjdk-despite-ellison-s-claim-oracle-isn-t-writing-its-own-code

2. **Cloudflare 推出 Kitesurf：面向 Agent 的新浏览器**
   - **摘要**：Cloudflare 发布 Kitesurf，一个运行在 Workers / V8 isolates 上的 agent-first 浏览器，强调更低的内存和 CPU 开销，适合自动化、截图、HTML 抽取等任务。文章核心观点是：传统 Chromium 是为人设计的，而 Agent 需要的是结构化、可扩展、低成本的浏览器能力。
   - **为什么值得关注**：这是“Agent 浏览器”赛道的重要基础设施信号，直接关系到自动化代理、RPA、网页执行环境的下一代形态。
   - **原文链接**：https://blog.cloudflare.com/kitesurf/

3. **pgrust：把 Postgres 分析型性能提升到 300x**
   - **摘要**：作者介绍 pgrust 0.2 的性能重构，称其在 Clickbench 上可比 Postgres 快 300x，核心来自查询引擎重写、批处理、operator fusion 和 SIMD 优化。文中也解释了为什么现代数据库瓶颈已从磁盘 I/O 转向 CPU 与内存带宽。
   - **为什么值得关注**：这是数据库内核优化的高密度案例，适合关注分析型数据库、执行引擎、Rust 数据系统的人阅读。
   - **原文链接**：https://malisper.me/how-we-made-postgres-hundreds-of-times-faster-the-query-engine/

4. **DeepSeek V4 Flash 0731 的 ARC-AGI 结果**
   - **摘要**：该页展示 DeepSeek V4 Flash 0731 在 ARC-AGI-1/2/3 上的成绩与单位任务成本，强调“高分 + 低成本”组合。它把模型能力与推理成本放在同一张表里，便于比较不同路线的效率。
   - **为什么值得关注**：ARC 类基准仍是检验通用推理能力的重要窗口，这类结果能帮助判断模型能力进展是否“真提升”还是“堆成本”。
   - **原文链接**：https://arcprize.org/results/deepseek-v4-flash-0731

5. **美国水务控制器不该上网**
   - **摘要**：前 NSA 局长在 DEF CON 上警告，水系统 PLC 不应直接暴露在互联网，认为美国水务系统攻击面巨大且长期欠缺安全投入。文章引用了近期多州水系统遭入侵的背景，并提到需要更高标准和多方协作防御。
   - **为什么值得关注**：这是关键基础设施安全的典型案例，涉及 OT / ICS、国家级威胁建模和现实世界攻击面。
   - **原文链接**：https://www.theregister.com/security/2026/08/07/water-system-controllers-dont-belong-on-the-internet-says-ex-nsa-chief-after-suspected-iran-attacks/5285070

6. **REpsych：从控制流图生成图像的逆向“心理战”工具**
   - **摘要**：REpsych 是一个概念性工具集，展示如何把程序的控制流图（CFG）转成图像，用于逆向分析中的视觉干扰与“心理战”效果。项目本身偏实验性质，但技术上很有恶趣味，也体现了逆向工程和可视化的交叉玩法。
   - **为什么值得关注**：对安全研究、混淆分析、逆向可视化有启发，属于“看起来很怪，但脑洞很大”的项目。
   - **原文链接**：https://github.com/xoreaxeaxeax/repsych

7. **Assembly Hall of Shame：刻意把单条指令跑到最慢**
   - **摘要**：这个项目反其道而行之，专门寻找“单指令性能下限”，记录各种让 CPU、PCIe、GPU、SMM 等路径极慢的技巧。它不是优化指南，而是对现代硬件微架构极限的一次荒诞又严肃的探索。
   - **为什么值得关注**：适合系统性能、微架构、底层黑魔法爱好者；很多技巧本身就是对硬件行为的高分辨率观察。
   - **原文链接**：https://github.com/xoreaxeaxeax/asm-hall-of-shame

8. **Ancient Library：希腊/拉丁古典文献的原文阅读库**
   - **摘要**：Ancient Library 收录 1,060 余部希腊与拉丁文本，每个词都可解析词形并查看词典释义，目标是降低阅读原典门槛。它把传统人文学术资料做成了高度结构化、可检索的数字工具。
   - **为什么值得关注**：这是“知识基础设施”方向的好例子，展示了文本解析、词形学与数字人文产品化的结合。
   - **原文链接**：https://ancientlibrary.net/

9. **Wyzer Programming Language：资源导向 + 分布式安全的语言**
   - **摘要**：Wyzer 自称是静态类型、编译型、资源导向语言，强调 choreographic programming 和 perceus 内存模型，试图把分布式安全直接纳入语言层。项目文案很宏大，试图从语言机制上解决分布式系统中的协作与安全问题。
   - **为什么值得关注**：这是编程语言设计与分布式系统安全结合的激进尝试，适合关注 PL / 类型系统 / 编译器的人。
   - **原文链接**：https://github.com/Wyzer-Lang/wyzer

10. **textlog：无 JS、文本优先的轻量微博平台**
   - **摘要**：textlog 是一个开源文本社交平台，强调 280 字短帖、无 JS、无增长焦虑、无算法干扰，定位为更安静的公共表达空间。它突出“少即是多”的产品哲学，强调阅读和写作的低摩擦。
   - **为什么值得关注**：这是对主流社交产品的一种反向设计，适合关注产品理念、信息流节制和开源社交的人。
   - **原文链接**：https://textlog.cc/about

如需，我也可以把这 10 条进一步整理成“适合推送到飞书/Telegram 的短版格式”。
