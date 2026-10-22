
# GitHub Trending 日报 · 2026-10-23

今天 Trending 前 9 名里，有 5 个是「agent skill / 编码 agent」类项目，它们都不是模型、也不是框架，而是给 Claude Code、Codex、Cursor 这类工具安装的「行为规则包」。这个方向已经成了 GitHub 上最容易冲榜的品类，而且开始按场景细分：安全审计、代码精简、代码库知识图谱、上手教程。

---

## 1. Cloudflare 开源安全审计 skill — 今日增速第一
**cloudflare/security-audit-skill** ｜ JavaScript ｜ 39,479 ★ ｜ **+2,979**（今日）
https://github.com/cloudflare/security-audit-skill

把编码 agent 变成安全审计员，六阶段流水线：侦察（产出 `architecture.md` + `coverage-ledger.json`）→ 覆盖驱动的漏洞猎人（按 ledger 单元派隔离 hunter，再由 coverage critic 找盲区）→ 候选验证（每个候选交给全新的 verifier 专门去**推翻**它）→ 结构化输出 `findings.json` 并按 `report-schema.json` 校验 → 独立复核来源声明 → 生成目标中立报告。多次运行是增量叠加的，会复用之前的 ledger 只补盲区。

**为什么值得关注**：这是 Cloudflare 官方博客《Build your own vulnerability harness》里那套全公司级漏洞挖掘系统的单仓库起点版本，现在直接开源。它解决的是 AI 找漏洞最要命的问题——幻觉。做法不是让模型更聪明，而是用「独立 agent 互相反证 + schema 强制 + 三态结论（confirmed / needs_validation / rejected）」把结论钉死。

---

## 2. Ponytail：让 AI 像最懒的资深工程师那样写代码
**DietrichGebert/ponytail** ｜ JavaScript ｜ 173,414 ★ ｜ **+1,949**
https://github.com/DietrichGebert/ponytail

核心就一条 SKILL.md 提示词：agent 先读懂改动涉及的代码和真实数据流，再走「懒惰阶梯」选最小方案。口号是「最好的代码是你从没写过的代码」。示例：要日期选择器，不带它时 agent 装了库或手写整套日历（335 行）；它发现仓库已有 `Input` 组件、浏览器自带日期选择器，拼起来（10 行）。官方基准 30 次运行全过，代码更少但校验/错误处理/安全/无障碍一项没砍。

5.3 版新增 Claude Code 输入框上方的常驻状态条：本次任务成本、token、agent 耗时、**复用旧代码比例**、改动后测试是否通过，数据全存本地 `~/.config/ponytail/band/`。支持 Claude Code / Codex / Cursor / Copilot 等 20 多个 agent。

**为什么值得关注**：正面刚「AI 写代码越写越多」这个社区最大抱怨，还把成本做成了可见指标——对成本敏感的团队，这个 band 比提示词本身更有说服力。注意：只从 GitHub 原仓库或 npm `@dietrichgebert/ponytail` 安装，作者明确说不会发 .exe/.dll。

---

## 3. Graphify：把整个仓库变成可查询的知识图谱
**Graphify-Labs/graphify** ｜ Python ｜ 132,909 ★ ｜ **+1,407**
https://github.com/Graphify-Labs/graphify

在 AI 编码助手里输入 `/graphify`，把代码、文档、SQL schema、配置、PDF、图片、视频全部映射成一张图，之后**查询而不是 grep**。代码部分走 tree-sitter AST，确定性解析、完全本地、不经过 LLM；文档媒体才用模型做语义补充。每条边都标 `EXTRACTED`（源码里明写的）或 `INFERRED`（graphify 推断的）。刻意不做向量库：没有 embedding，是真正可遍历的图。产出三个文件：`graph.html`（可点开过滤搜索）、`GRAPH_REPORT.md`、`graph.json`。

**为什么值得关注**：「agent 读大仓库」现在基本靠 grep + 向量 RAG，两者都有盲区；图遍历 + 边可解释性是对这个痛点的正面回答。但 1,602 个 open issue 说明规模上来后噪声不小，README 里也在推 14 天试用的 Graphify Cloud，开源版和商业版边界要自己判断。

---

## 4. Anthropic 官方开源 11 个「知识工作」插件
**anthropics/knowledge-work-plugins** ｜ Python ｜ 31,565 ★ ｜ **+303**
https://github.com/anthropics/knowledge-work-plugins

Claude Cowork 的官方插件集，同时兼容 Claude Code。11 个按岗位划分：productivity、sales、customer-support、product-management、marketing 等。每个插件打包了 skills、连接器、slash commands、sub-agents，预接 Slack / Notion / Linear / Jira / Asana / HubSpot / Microsoft 365 / Figma 等。

**为什么值得关注**：这是官方在定义「按岗位交付 agent」的标准形态——不是给工程师的，是给销售、客服、PM、市场的。插件市场的样板已经摆出来了，接下来拼的是企业自己改术语、改流程那层。

---

## 5. claude-howto：Claude Code 的体系化教程
**luongnv89/claude-howto** ｜ Python ｜ 43,161 ★ ｜ **+370**
https://github.com/luongnv89/claude-howto

「一个周末掌握 Claude Code」，从敲 `claude` 到编排 agents、hooks、skills、MCP servers，可视化教程 + 可复制模板 + 分级学习路径。多语言，含中文（`zh/README.md`）。强调的痛点很真实：官方文档讲功能，但不讲怎么把 slash command、hooks、memory、subagent 串成真能省时间的流程。

**为什么值得关注**：这类教程仓库能冲到 4.3 万星，本身就是信号——Claude Code 已经从早期采用者进入「需要教程」的大众阶段，围绕它的知识层开始规模化。

---

## 6. 其他上榜（简略）
- **supabase/supabase** ｜ TypeScript ｜ 113,469 ★ ｜ +683 — Postgres 开发平台，带 pgvector / embeddings，AI 应用后端的默认选项之一，属常规热度。https://github.com/supabase/supabase
- **fastapi/fastapi** ｜ Python ｜ 103,717 ★ ｜ +96 — 老牌框架，今日增量很小，无新话题。
- **php/php-src** ｜ C ｜ 41,133 ★ ｜ +423、**Meloong-Git/PCL** ｜ VB.NET ｜ 8,681 ★ ｜ +115 — 分别是 PHP 解释器和 Minecraft 启动器，与 AI 无关，未展开。

---

**一句话观察**：今天榜单真正的竞争点不在模型能力，而在「怎么让 agent 的行为可验证、可计量、可复用」——Cloudflare 用独立 agent 互证压制幻觉，Ponytail 用成本指标约束过度生成，Graphify 用带标签的图让上下文可信。这三件事指向同一个方向：agent 工程化正在从「写更长的 prompt」转向「建可审计的流程」。

已标记该源 4 条未读为已读。
