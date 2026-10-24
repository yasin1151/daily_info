
**GitHub Trending 日报 · 2026-10-25（近 24 小时）**

今日榜单共 10 个仓库，其中 8 个与 AI、Agent 相关，主线很清楚：一是 **Agent 的安全与运行时**（OpenShell、security-audit-skill），二是 **“去 AI 味”的设计层 skill**（impeccable、hallmark），三是 **Agent 客户端与官方工具箱**（cindy、AWS Toolkit）。另外，榜单第一名单日新增 2,271 stars 的“skill”，已经不是模型，而是给 Agent 用的技能包。

---

**1. Cloudflare 安全审计 Skill：把一个内部漏洞挖掘平台拆成仓库放出**
`cloudflare/security-audit-skill`｜JavaScript｜44,479 stars（+2,271）｜今日第一

把编码 Agent 变成安全审计员：侦察、按覆盖率分配猎人、候选漏洞验证、结构化输出、独立复核，最后生成报告，全部自动完成。这是 Cloudflare 那套“漏洞发现平台”的单仓库起点，来自他们博客里的多阶段平台雏形。亮点是判定分级很严格：`confirmed`、`needs_validation`、`rejected` 必须带完整来源追溯，还要用独立 Agent 复核结论。

为什么值得关注：这是“skill 即产品”最极端的一个样本，并且出自有真实攻防产出的团队；它的六阶段流程和 coverage ledger，比大多数所谓“AI 安全扫描”具体得多。想给内部代码库做自动化审计的，可以直接拿来改。

https://github.com/cloudflare/security-audit-skill

---

**2. NVIDIA OpenShell：给 Agent 群体用的安全运行时**
`NVIDIA/OpenShell`｜Rust｜19,461 stars（+893）｜Apache-2.0

让自主 Agent 能读文件、装包、调 API、用凭证，同时不把数据、密钥、网络全部交出去。做法是双管齐下：**内核级强制执行**（每一次文件访问、系统调用、网络连接都按策略拦截），加上**形式化验证**（策略变更在应用之前，先算出会放开什么）。支持声明式策略和隔离原语，0.1.x 已发布稳定版本，并提供 pip 包。

为什么值得关注：Agent 落地目前最大的阻碍是“不敢让它碰真环境”，而这件事需要在内核层面解决，靠 prompt 层解决不了。NVIDIA 直接拿 Rust 在内核层面做权限沙箱，也是今天最“系统工程”的项目。

https://github.com/NVIDIA/OpenShell

---

**3. AWS 官方 Agent Toolkit 正式 GA：大厂把 MCP/skill 当作发行渠道**
`aws/agent-toolkit-for-aws`｜Python｜3,119 stars（+11）｜Apache-2.0

官方提供、AWS 背书的 MCP servers、skills、plugins，目标是让 Claude Code、Codex、Cursor、Devin、Kiro 这些编码 Agent 能正确构建和部署 AWS 应用。安装路径非常“产品化”：Claude Code 里直接 `/plugin install aws-core@claude-plugins-official`（已默认挂到 Anthropic 官方市场），CLI 侧是 `aws configure agent-toolkit`。插件按域拆分，包括 `aws-core`、`aws-agents`（Bedrock + AgentCore）、`aws-data-analytics`。

为什么值得关注：你不再需要手写一套 AWS 提示词，官方直接以插件形式发行“云平台知识”。这也标志着 AWS 把“Agent 上下文”当成了新的 SDK 分发面。今日 +11 stars 说明它才刚起步，但战略意义大于热度。

https://github.com/aws/agent-toolkit-for-aws

---

**4. Impeccable：让 AI 生成的前端别那么“AI 味”**
`pbakaus/impeccable`｜Rust｜86,372 stars（+733）｜今日第三

面向 AI 编码 Agent 的设计指导：1 个 skill、24 条命令、实时浏览器迭代，外加 **62 条确定性检测规则**，专门抓 AI 生成前端的通病（全是 Inter 字体、紫蓝渐变、卡片套卡片、每个标题上方一个圆角方块图标、正文灰色压在彩色底上）。`npx impeccable install` 装完后，在工具里运行 `/impeccable init`，它会把产品事实写进 `PRODUCT.md`，后续所有命令都基于这份“真相”工作。检测规则跑 CLI 或浏览器扩展，**无需 LLM、无需 API Key**。

为什么值得关注：起点是 Anthropic 官方 frontend-design skill，但补上了“可验证”这一环——62 条规则能零成本确定性地拦截，不用再靠模型自觉。设计层正在成为 skill 竞争最激烈的战场。

https://github.com/pbakaus/impeccable

---

**5. Hallmark：另一个“反 AI slop”设计 skill，出自 Together AI**
`Nutlope/hallmark`｜CSS｜32,106 stars（+570）

一键给 Claude Code、Cursor、Codex、OpenCode 换上一套“不像机器生成”的设计体系。v2 有 48 套主题（每套是一种材质：纸张、字体、配色、组件、纹理），按“访客来干什么”来排页面（预约页就预约、商店页就卖货），再用真实浏览器 lint 掉那些一眼就能看出是机器生成的痕迹：每个标题上方的 eyebrow、字距拉开的全大写标签、标题里一个彩色词、满是空框或只有照片的页面、首屏不满一屏、每页末尾都塞邮件订阅、表单点了“谢谢”却没真发送。最后还有一个“新上下文 reviewer”做终审。

为什么值得关注：和 Impeccable 同一赛道但气质不同——它更偏“成品感”和分档 gate（Floor 永不发布、Reflex 可申辩、Finish 只影响打磨）。两个项目同时上榜，说明“AI 生成界面同质化”已经是被市场承认的痛点。

https://github.com/Nutlope/hallmark

---

**6. claude-howto：把 Claude Code 从入门到编排 agent 讲完**
`luongnv89/claude-howto`｜Python｜44,530 stars（+442）｜MIT

面向 Claude Code 2.1+ 的视觉化教程，从敲 `claude` 到编排 agent、hooks、skills、MCP servers，自带可复制模板和分级学习路径（“15 分钟上手”）。文档提供英、越、**中**、乌克兰、日五种语言，版本跟到 2.1.302。

为什么值得关注：涨到 4.4 万 stars 的“教程类”仓库能持续上榜，说明 Claude Code 的用户增长还在靠自学文档承接。要带团队上手的话，中文版可以直接发出去。

https://github.com/luongnv89/claude-howto

---

**7. Cindy：开箱即用的开源桌面/手机 Agent，把 Claude Code 和 Codex 当引擎**
`makecindy/cindy`｜TypeScript｜4,074 stars（+471）｜Apache-2.0

一个开源 AI Agent 客户端（Electron 桌面 + Expo 移动端，pnpm monorepo）。核心卖点：**不用自己配 harness**——首批支持 Claude Code 和 Codex，模型与 harness 可以自由混搭，并且能在任务中途切换；能同时驱动浏览器、电脑和手机，还能从 IM 和定时任务接收工作。付费方式很克制：可以用官方托管服务、直接授权你已有的 **Claude Code / Codex Coding Plan**（不必重复付费）、接自己的 API Key，或者跑本地模型。记忆、Skills、定时自动化、MCP 都在，甚至可以“跳过登录”只用本地 Agent。

为什么值得关注：+471 stars 且仓库是新的——它切的是“我有订阅但想要一个统一入口”的人群。把已付费订阅复用进第三方客户端，这个模式接下来可能会被大量复制，也大概率会引起厂商条款层面的摩擦。

https://github.com/makecindy/cindy

---

**8. Gemini CLI：榜单里的“前朝遗老”，README 自己宣告被取代**
`google-gemini/gemini-cli`｜TypeScript｜108,027 stars（+38）

开源终端 AI Agent，把 Gemini 接进命令行。但今天把它列出来，是因为 README 顶部现在挂着两条重要声明：**免费层和 Google One 用户注意——Gemini CLI 已于 2026 年 6 月 18 日被 Antigravity CLI 取代**；并且 **Gemini CLI 没有为 Gemini 4 Argon 做优化**，要用新模型请走 Antigravity。

为什么值得关注：10.8 万 stars 的项目被官方迁移，CLI Agent 这条赛道一年内就换代了。如果你脚本里还 hardcode 着 `gemini`，是时候检查迁移路径了。

https://github.com/google-gemini/gemini-cli

---

**9. Microduck：一只会走路的强化学习小鸭子（唯一非软件项目）**
`pollen-robotics/microduck`｜Rust｜10,967 stars（+381）

Pollen Robotics 的开源双足小机器人，这个仓库是“鸭子的大脑”——大约 2 万行左右的固件/控制代码，步态由强化学习策略驱动，策略训练代码单独放在 `microduck_rl` 仓库。

为什么值得关注：硬件 + RL 策略全开源的项目很少见，而且它是今天榜单里唯一“能跑出门”的东西。做具身智能的可以拿它当低成本实验平台。

https://github.com/pollen-robotics/microduck

---

**筛掉的**：`jbiaojerry/ebook-treasure-chest`（+220，2.2 万 stars）——电子书下载链接聚合，覆盖帆书、微信读书、京东读书等平台，与 AI/开发工具无关，属于版权灰色地带，不建议入库。

**一句话观察**：今天的榜单没有新模型，全是围绕 Agent 的“周边基建”——安全运行时、官方工具箱、设计品味、教程、统一客户端。市场正在从“哪个模型强”转向“怎么让 Agent 可靠地干真活”。

*已标记 6 条未读为已读（blogwatcher: GitHub Trending 已清空）。*
