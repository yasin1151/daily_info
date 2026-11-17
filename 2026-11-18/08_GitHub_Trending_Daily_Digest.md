
## GitHub Trending 日报 · 2026-11-18

今天榜单的 15 个仓库里，13 个直接与 coding agent 相关。变化明显出现在榜单更底下的两层，而不是出现新的技能包：**harness 层的性能、记忆与安全**（ECC 重新回到榜单顶部）、**把 agent 交付固化成可重复的 SOP**（腾讯 LoopForge），以及**厂商自己开始定插件规范**（cursor/plugins）。昨天在榜的 ffmpeg-skill、SkillEvaluator、chrome-devtools-mcp、claude-trading-skills 今天全部掉出榜单。

> 说明：blogwatcher 今天扫描 15 个仓库、新增 0 个（榜单为昨日延续），无未读需标记。以下按「今日重新进入榜单」和「延续在榜」两部分写。

---

## 一、今天重新回到榜单的四个

### 1. 把 agent harness 当操作系统来卖：ECC
**affaan-m/ECC** · JavaScript · ⭐ 305,471（+902 today）

自称「agent harness operating system」，核心是给 harness 增加运行时环境，而不是增加几个技能：**72 个 agent、327 个 skills、98 个旧命令 shim**，外加 hooks、规则目录、统一记忆库（`ecc memory`）、「instincts」持续学习（把会话里学到的偏好存成可复用条目，`/evolve` 再聚类成技能）、以及 AgentShield 安全扫描。MIT，一个 universal 安装脚本可挂到 Claude Code / Codex / Cursor / OpenCode / Qoder，也能接自托管 Kimi 端点。

**为什么值得关注**：市面上 90% 的「skills 合集」只是 prompt 包，ECC 补的是长期缺失的那一段工程实现——记忆如何跨会话存、偏好怎么沉淀、装进来的技能怎么防越权。327 个技能本身不一定都好用，但它把 skill 的组织和治理做成了产品，这一点比技能数量更值得看。反面是复杂度：README 两千多行、安装分五条路径，轻量用户容易被学习曲线拒之门外。

🔗 https://github.com/affaan-m/ECC

---

### 2. 腾讯把 agent 交付做成了 SOP 引擎：LoopForge
**Tencent/LoopForge** · Go · ⭐ 3,097（+590 today）

自托管（Docker，MIT）的 agent 交付工作台。两条路径：**跟 Main Bot 对话**——它现场开一个 Docker sandbox、把仓库检出、按项目角色派给子 agent、最后开 PR；或者**跑 SOP**——用节点编排「Agent / Script / Human-gate / 子 SOP」，固定阶段和审批点，同一个需求下次照同样流程走。内置后端、前端、bug 修复、产品四套 SOP。执行器支持十种 CLI：CodeBuddy、Codex、Claude Code、OpenCode、Cursor CLI、Antigravity、Kimi Code、Pi、DeepSeek Harness、ZCode。

**为什么值得关注**：它正面回应了「给 agent 说修个 bug，结果取决于这一次运行」这个痛点——规划、实现、审查、测试各自独立角色、独立模型、独立权限，节点可暂停、重试、从任意节点重跑。相比 8 月那批「agent 团队」demo，它的差异在于**审批门**和**可观测性**是产品设计里的关键环节，而不是事后补的日志。3k stars 说明还没出圈，但对需要让 agent 上线交付的团队，这是目前少见的完整形态。

🔗 https://github.com/Tencent/LoopForge

---

### 3. 先问清你要什么再写代码：Superpowers
**obra/superpowers** · Shell · ⭐ 319,304（+598 today）

一整套「软件开发方法论」以可组合 skills 的形式塞进 agent：开工先不写码，先把 spec 从对话里聊出来、分块给你签字，再出一份「照做的初级工程师也能执行」的实施计划（强调真红绿 TDD、YAGNI、DRY），然后进入 subagent-driven development——一个任务一个子 agent，带着审查往前推，能连续几小时不脱轨。安装覆盖 17 种 harness（Claude Code / Codex / Cursor / Antigravity / Gemini CLI / Copilot CLI / Devin / Kimi / Qwen / OpenCode / Hermes Agent……）。

**为什么值得关注**：31 万 stars 这个量级说明它已经是「方法论层」的事实标准之一，而不是某个工具的小插件。它和 ECC、LoopForge 恰好构成三层：**流程规范（superpowers）→ 运行时与记忆（ECC）→ 组织级交付流水线（LoopForge）**。三者今天同榜，是这批项目从「玩票」走向「工程化」的清晰信号。

🔗 https://github.com/obra/superpowers

---

### 4. Cursor 亲自下场定插件规范：cursor/plugins
**cursor/plugins** · TypeScript · ⭐ 16,886（+196 today）

官方插件规范 + 官方与第三方插件仓库：每个插件是独立目录、自带 `.cursor-plugin/plugin.json`。里面有 `orchestrate`（大任务拆给并行云端 agent，规划/执行/验证/交接分角色）、`thermos`（分支深度安全与正确性审查，多个子 agent 并行）、`ralph-loop`（自指迭代循环）、`advisor`（拿不准时先问更强的模型）、`pr-review-canvas`（按重要性重排 PR diff），还有一大批企业集成（Gmail、Drive、Sheets、Salesforce、Zoom、X、Playwright）。

**为什么值得关注**：这是「插件规范之争」正式开打的标志——Anthropic 有 plugin marketplace，Google 有 Agent Skills，Cursor 现在给出自己的 manifest 格式和官方插件集。对用户的现实影响是：同一个工作流以后可能要在三套规范里各写一遍。

🔗 https://github.com/cursor/plugins

---

## 二、延续在榜（今日涨幅）

| 项目 | 一句话 | Stars（今日） |
|---|---|---|
| **dream-num/univer** | AI 办公 SDK：把表格/文档/幻灯片的编辑、公式、协同、xlsx 读写做成可嵌入零件 | 28,882（+1,776，今日第一）|
| **ag-ui-protocol/ag-ui** | Agent-User Interaction Protocol，把 agent 的事件流接进前端应用 | 19,976（+1,444）|
| **google-research/paper-orchestra** | 多 agent 论文写作：大纲→文献→分节→精修→配图，一天从 1,457 涨到 2,938 | 2,938（+1,175）|
| **elementalsouls/Claude-BugHunter** | Claude Code 红队技能包：82 技能 / 15 命令 / 681 条漏洞模式 | 9,196（+1,007）|
| **mvanhorn/last30days-skill** | 不搜网页搜「人的反应」：Reddit 赞、X likes、Polymarket 赔率加权后合成简报 | 69,008（+772）|
| **alibaba/open-code-review** | 确定性规则流水线 + LLM Agent 的分层代码审查，行级评论 | 53,705（+764）|
| **backnotprop/plannotator** | Agent 协作工作台：改计划、标注、审代码，一键回推反馈 | 13,053（+691）|
| **getarcaneapp/arcane** | Go 写的自托管 Docker 管理面板，v3 | 9,305（+654）|
| **google-labs-code/stitch-skills** | Google Labs 的 Agent Skills 库，配 Stitch MCP，兼容主流 harness | 10,083（+350）|
| **jingyaogong/minimind** | 2 小时从零训一个 64M 参数 LLM 的教学项目 | 65,925（+188）|
| **sveltejs/svelte** | 非 AI：前端框架（今日唯一与 agent 无关的榜单项目）| 89,578（+533）|

---

## 三、今天的三个观察

1. **榜单进入「同一批项目持续发酵」阶段。** 15 个里 10 个昨天就在榜，剩下 5 个是回流。这不是 GitHub Trending 卡住了，而是 agent 工具的口味已经收敛到很窄的一类：harness、技能、编排、审查台。
2. **涨幅结构在下移。** 昨天第一名的叙事是「技能往行业里扎根」（办公、视频、论文、炒股、挖洞），今天前四名里三个是**底层设施**——harness 运行时（ECC）、SOP 引擎（LoopForge）、方法论（superpowers）。行业垂直技能包则集体掉榜。说明从业者当前缺的更多是「怎么稳定跑起来」，而不是「再买一门手艺」。
3. **三套插件规范并存已是既成事实。** Anthropic plugin marketplace、Google Agent Skills、Cursor plugin spec 各有各的 manifest。跨 harness 的兼容层因此成了真实的商业需求——superpowers 装 17 种 harness、ECC 一个脚本通吃，本质上都在做这件事。

*今日无全新仓库入榜，以上为榜单延续与回流的完整梳理。*
