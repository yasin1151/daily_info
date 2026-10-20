
**GitHub Trending 日报 · 2026-10-21**

今日有 13 个项目进入趋势榜，其中至少 9 个属于 AI/Agent 方向。值得注意的变化是：竞争重点已从“比拼哪个 coding agent 更强”，转向“给 agent 添加技能和降低成本”，而且技能开始按具体职能细分：求职、安全审计、SEO、Android 测试。

---

**1. ai-job-search：把整条求职流程写成 Claude Code 工作流**
简介：一个在本地运行的 AI 求职框架，用基于 Claude Code 的 `/scrape`、`/apply`、`/interview` 三个命令，完成职位评估、简历定制、求职信撰写和面试准备；fork 后填入自己的资料即可使用。
看点：作者本人是地球物理转行，被裁员后靠这套流程投了 69 份简历、获得 20 个一面、在 6 月入职 AI 工程师岗位；README 里把完整转化漏斗都公开了。这并非 demo，而是经过验证的方法。以 fork 方式分发，也说明个人求职工具正在变成可复用的 agent 资产。
`60,470★ | 今日 +3,890（今日第一）| Python` → https://github.com/MadsLorentzen/ai-job-search

**2. security-audit-skill：Cloudflare 把漏洞挖掘流程开源成 agent 技能**
简介：它把 coding agent 变成一个安全审计员，分为六个阶段运行：侦察并建立 coverage ledger、按覆盖度派多个隔离 hunter、由独立 verifier 反驳候选漏洞，最后写入结构化 `findings.json` 并做二次溯源验证。
看点：这是 Cloudflare 内部大规模漏洞挖掘 harness 的起源版本，正式 harness 由它演化而来。关键设计是“候选必须被独立 agent 试着推翻”，比让单个 agent 报告漏洞更可信。安全团队可以直接把它当作起点。
`34,101★ | 今日 +1,680 | JavaScript` → https://github.com/cloudflare/security-audit-skill

**3. orca：把多个 coding agent 当作一个团队来管理的 IDE**
简介：可以并排运行 Codex、Claude Code、OpenCode、Pi，每个 agent 在独立 git worktree 中工作，并统一追踪；同一句提示可以分发到五个 agent 并比较结果，胜出的分支再合并。
看点：它试图解决“agent 并行后如何管理”的问题：用 worktree 做隔离，由终端支持 WebGL 渲染和无限分屏，Design Mode 可以直接在真实 Chromium 中点击 UI 元素，把 HTML/CSS 和截图放入提示词，同时提供手机端接收通知和跟进。它还有 SSH worktree，可把重活放到远程机器上执行。
`99,683★ | 今日 +1,559 | TypeScript` → https://github.com/stablyai/orca

**4. ponytail：让 AI agent 像组里最懒的资深工程师那样写代码**
简介：一个给 agent 使用的技能包，核心规则是“只写任务真正需要的东西”，但明确禁止因此削减校验、错误处理、安全和可访问性。
看点：它给出了在同仓库、同模型（Opus 5.5）下开启和关闭该技能的对比基准，39 个任务各运行 5 次：代码量减少 53%、耗时减少 41%、成本减少 26%、token 减少 45%，同时 98% 的风险逻辑带有测试（未使用技能时为 68%），6 个安全任务在 30 次运行中全部通过。它反驳了“省 token 就等于降低质量”这一常见质疑，这是目前最扎实的一份证据。
`169,587★ | 今日 +1,396 | JavaScript` → https://github.com/DietrichGebert/ponytail

**5. graphify：不再用 grep 搜索代码，而是把仓库变成可查询的知识图谱**
简介：在 AI 编程助手里输入 `/graphify`，它会把整个项目（代码、文档、PDF、图片、视频）映射成一张知识图谱，你可以沿路径查询，而不必用 grep 逐文件搜索。
看点：代码部分使用 tree-sitter AST 在本地解析，不调用 LLM，数据不离开本机；每条边都标记为 EXTRACTED（源码中明确存在）或 INFERRED（由工具推断），这个区分非常重要：它不把它当作向量索引，没有 embedding，也不使用向量库。作者称这能把 agent 的 token 开销降低 80%。今天 blogwatcher 抓到的两个新条目之一。
`130,194★ | 今日 +906 | Python` → https://github.com/Graphify-Labs/graphify

**6. headroom：在内容进入 LLM 之前先对其压缩**
简介：压缩 agent 读取的一切内容，包括工具输出、日志、RAG 片段、文件和对话历史；提供 Python/TS 库、本地代理，也支持用 `headroom wrap claude|codex|cursor|...` 一条命令接入，并提供 MCP server 和跨 agent 共享记忆。
看点：README 给出例子，一段 FATAL 日志从 10,144 token 压缩到 1,260 token 后，仍然能定位同一个错误。压缩在本地进行，原文缓存在本地（CCR），并且可逆、可按需取回。还有 `headroom learn`，它会分析失败的会话，并把修正写入 `CLAUDE.local.md`。对于按 token 计费的团队，这是能直接降低成本的工具。
`76,737★ | 今日 +555 | Python` → https://github.com/headroomlabs-ai/headroom

**7. artemis：让 AI 像人一样使用真机进行 Android 测试**
简介：Google 开源的 Android 自动化 agent，把自然语言指令转换成可靠的端到端操作，并抓取日志和截图；它通过 MCP 接入 Antigravity、Claude Code、Windsurf，让 IDE 直接驱动测试机。
看点：在 Google Research 的 AndroidWorld 基准（包含 100+ 多步任务）上达到 99%+ 完成率，走一步通常需要 3–5 秒；元素定位优先使用索引，坐标和视觉定位作为兜底，因此也能处理自定义界面。这是“agent 进行真机测试”从演示走向工程化的信号。
`13,259★ | 今日 +348 | Python` → https://github.com/google/artemis

**8. CLI-Anything：把所有软件都变成 agent 原生**
简介：港大数据智能实验室的项目，为各类软件自动生成 CLI harness，让 agent 可以通过命令行操作 CAD、3D 场景、图表、游戏、字幕等工具；配套 CLI-Hub 支持用 `pip install cli-anything-hub` 安装。
看点：立项逻辑很明确：“今天的软件服务于人类，明天的用户是 agent”。它的做法是应用没有 API 时，就生成一层 CLI，而不是训练专用模型。从 55k 星和社区 contributor 招募速度来看，这套思路的接受度很高。
`55,661★ | 今日 +628 | Python` → https://github.com/HKUDS/CLI-Anything

**9. Kronos：第一个面向金融 K 线序列的开源基础模型**
简介：这是一个 decoder-only 基础模型系列，专门针对 K 线（OHLCV）预训练：先用专用 tokenizer 把多维连续行情量化成层级离散 token，再用自回归 Transformer 建模，可用于预测和多种量化任务。
看点：训练数据覆盖 45 个以上全球交易所，论文已被 AAAI 2026 接收，也提供微调脚本。它是“垂直领域基础模型”路线的一个样本，与通用时序模型的差别在于显式处理了金融数据高噪声、非平稳的特性。
`42,335★ | 今日 +719 | Python` → https://github.com/shiyu-coder/Kronos

**10. opencode：开源 coding agent 的长期选手**
简介：一个完整的开源 coding agent，提供终端与 IDE 两种形态。
看点：它今天没有新功能发布，仍然上涨 1,256 星，说明“开源替代闭源 coding agent”这条赛道仍有需求。已有 218k 星，属于基础设施级别的关注度。
`218,882★ | 今日 +1,256 | TypeScript` → https://github.com/anomalyco/opencode

---

**其余上榜项目快速浏览**

- **ComfyUI** — 扩散模型 GUI/后端，节点式工作流，本地推理中最快的一档。`140,728★ | +1,201` → https://github.com/Comfy-Org/ComfyUI
- **ruflo** — Claude Code/Codex 的 agent meta-harness，通过插件市场安装 core/console/mods，mods 会在会话内做路由和策略约束。`77,818★ | +683` → https://github.com/ruvnet/ruflo
- **agency-agents** — 一批带性格、流程和交付物的 AI 专家角色，已推出跨平台安装 App，可一键装进 Claude Code、Cursor、Codex。`162,313★ | +590` → https://github.com/msitarzewski/agency-agents
- **knowledge-work-plugins** — Anthropic 开源 11 个按职能打包的 Claude Cowork 插件（产品、销售、财务等），内置 Slack/Notion/Jira 等连接器。`30,780★ | +262` → https://github.com/anthropics/knowledge-work-plugins
- **vllm** — 高吞吐 LLM 推理与 serving 引擎，今天 star 数量（+98）表明没有重大版本变化，属于常规热度。`94,423★ | +98` → https://github.com/vllm-project/vllm
- **claude-seo** — 面向 Claude Code 的 SEO 技能包，包含 26 个子技能和 19 个子 agent，覆盖技术 SEO、E-E-A-T、结构化数据以及面向 AI 搜索（GEO/AEO）的优化。`19,474★ | +185` → https://github.com/AgriciDaniel/claude-seo

---

**一句话观察**：榜单前四名中有三个属于“给 agent 添加职能技能”（求职、安全审计、写码习惯），并非 agent 本体。这说明竞争重点已经从“模型能力”转向“工作流封装”，而且愿意公开真实数据（如 ponytail 的 A/B 基准、ai-job-search 的求职漏斗）的项目，涨星速度明显快于只有宣传语的项目。

已标记 2 条新条目（graphify、vllm）为已读。
