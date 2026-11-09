
**GitHub Trending 日报 · 2026-11-10**

今日榜单共 11 个新上榜或持续在榜项目，其中 blogwatcher 新增抓取到 2 个，即下方标为 NEW 的条目。AI、Agent 相关项目占了绝大多数。

---

**1. GBrain — 给你手上的 agent 一套自己掌控的记忆（NEW）**
项目简介：把显式事实连同来源一起存下来，支持纠错和撤回，同一份记忆可在 ChatGPT、Claude、Cursor 等多个 agent 之间共享。默认是无需 key 的记忆加关键词检索，语义搜索、综合、后台增强按需加上。MIT 协议，可自托管；官方托管服务 gbrain.io 收费。
为什么值得关注：agent 记忆是目前最痛的一环，但主流方案基本是黑盒向量库。GBrain 走的是“可审计、可撤回、带出处”的路子，更接近工程上能放心用的形态。作者是 YC 的 Garry Tan，项目刚上榜就积累了 3.2 万 stars，有一定声量加成。
Stars：32,119（+215）｜TypeScript｜https://github.com/garrytan/gbrain

**2. HA-MCP — 让 Claude、ChatGPT 直接管 Home Assistant（NEW）**
项目简介：Home Assistant 的 MCP server，对外暴露 87 个工具，覆盖设备查询、状态控制、自动化配置。基于 FastMCP 构建。
为什么值得关注：智能家居是 MCP 最自然的落地场景之一，工具堆到 87 个说明作者在做细粒度接口，而没有用一个“万能工具”敷衍过去。值得注意的细节：v7.3.0 把 `ha_config_set_yaml` 挪进了 beta，说明直接让模型写 YAML 配置这类高风险工具，作者自己也在收紧权限。这个克制比功能数量更值得参考。
Stars：5,929（+31）｜Python｜https://github.com/homeassistant-ai/ha-mcp

**3. Astryx — Meta 开源的设计系统，明确把 agent 当成使用方**
项目简介：完全可定制的 React 19 + StyleX 设计系统，目前 Beta，已在 npm 发布 `@astryxdesign/core`，配套 Storybook 和在线沙箱。
为什么值得关注：宣传语写的是“by people and the agents working alongside them”，意思是组件库第一次把 AI 当作一等消费方来设计——这通常意味着组件元数据、token 语义、机器可读文档需要重做。如果这条路走通，前端组件库的写法会被改写。今日 +3,324，是榜上单日涨幅第二。
Stars：19,911（+3,324）｜TypeScript｜https://github.com/meta/astryx

**4. Anthropic Skills — Agent 技能库的官方标准仓库**
项目简介：Agent Skills 的公开仓库，收录官方和社区的可复用技能定义。
为什么值得关注：19 万 stars 的量级说明 Skills 已经从 Anthropic 的内部约定变成了事实标准，是观察 agent 生态“能力分发”怎么做的最佳样本。
Stars：190,907（+1,052）｜Python｜https://github.com/anthropics/skills

**5. agent-browser — Vercel 给 AI agent 做的浏览器操作 CLI**
项目简介：用 Rust 写的浏览器自动化命令行，专供 AI agent 调用。
为什么值得关注：绕开了 Playwright 的 Node 重包装，拿 Rust 直接操作 CDP，体积和启动开销都小一个量级。Vercel 在做 agent 的“手”，配合他们已有的部署链路，能拼出完整的 agent 工作流。
Stars：48,432（+914）｜Rust｜https://github.com/vercel-labs/agent-browser

**6. OpenMausBot — 开源版 Grok Bot，把 agent 当聊天联系人**
项目简介：Electron + React 19 桌面应用，侧边栏每个 bot 都是本地跑的 Claude 或 Codex 实例，各自有性格、模型、云电脑和接入的应用。可以与它们对话，观察它们工作，并审批关键动作。基于你自己的模型，本地优先。
为什么值得关注：代表“agent 编排”正在从开发者 IDE 溢出到普通人的聊天界面，并且保留了人对关键动作的审批——“approve what matters” 这层设计，比单纯堆自主性更实际。今日 +1,589，涨得很快。
Stars：19,628（+1,589）｜TypeScript｜https://github.com/milind-soni/OpenMausBot

**7. claude-quickstarts — Claude API 可部署应用的最小样例集**
项目简介：官方维护的一组起步项目，帮你快速搭出能用 Claude API 的可部署应用。
为什么值得关注：想验证“这个功能用 Claude 做要几行代码”，这里是成本最低的答案，适合当技术选型时的基线。
Stars：19,991（+560）｜Python｜https://github.com/anthropics/claude-quickstarts

**8. MuJoCo — DeepMind 的物理仿真引擎**
项目简介：多关节刚体动力学加接触仿真，通用的物理模拟器。
为什么值得关注：具身智能和机器人强化学习的事实底座。它持续在榜，说明机器人方向的开源投入没有降温。
Stars：16,888（+579）｜C++｜https://github.com/google-deepmind/mujoco

**9. RuView — 用 WiFi 信号做空间感知，不碰摄像头**
项目简介：把普通 WiFi 信号转成实时空间感知、生命体征监测和存在检测，完全不需要一帧视频。
为什么值得关注：这是“隐私友好感知”这个方向少见的成熟实现。养老监护、独居安全、HVAC 节能这些场景，卡点一直是摄像头带来的隐私问题，WiFi 感知绕开了这一点。10.3 万 stars 说明这个需求不是小众。
Stars：103,414（+245）｜Rust｜https://github.com/ruvnet/RuView

**10. daily_stock_analysis — LLM 驱动的多市场行情分析系统**
项目简介：多源行情加实时新闻加决策看板加自动推送，支持零成本定时运行，中英双语文档。
为什么值得关注：技术本身不复杂，但 fork 数（56,379）和 stars 数几乎持平，fork 与 star 的比值达到 0.82，是典型的“拿来即用、直接部署”型项目。这个比值本身比项目内容更有意思——它说明市场对“能自己跑起来的金融 agent”的需求非常大。
Stars：68,803（+505）｜Python｜https://github.com/ZhuLinsen/daily_stock_analysis

**另外提一个非 AI 的：** sherlock（106,947，+4,294）今日涨幅第一，跨平台按用户名追查社交账号的 OSINT 工具。这波爆发通常跟某个平台改版或某起事件有关，跟 AI 无关，但它是今天唯一压过所有 AI 项目的条目。

---

**一句话观察**：今天榜单的重心不在“更大的模型”，而在 agent 的配套设施——记忆层（GBrain）、操作能力（agent-browser）、界面（OpenMausBot）、能力分发（Skills）、外部世界接口（HA-MCP）。另外，Meta 的 Astryx 透露出一个新信号：组件库开始把 AI 当成正式用户来设计。
