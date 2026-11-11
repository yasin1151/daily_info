
**GitHub Trending 今日速览（11-12）**
抓取时间 07:40，未读数 4 → 已全部标记已读。AI/Agent 相关 7 个，其余 3 个附后。

---

### 1. meta/astryx — Meta 把「人和 agent 一起写前端」写进设计系统
开源设计系统，基于 React 19 + StyleX，主打可完全定制，且组件层直接对 agent 友好（不止给人看）。目前 Beta。
**为什么值得关注**：大厂第一次把 "agent ready" 放进设计系统的核心定位而不是营销词——走的是「组件自带语义/API 给 agent 消费」路线，跟截图/视觉理解那套是两条路。今日增速全场第二。
Stars：24,898（今日 +2,842）｜TypeScript
https://github.com/meta/astryx

### 2. addyosmani/agent-skills — 把资深工程师的工作流打包给 agent
Addy Osmani 出的"生产级工程技能"集合，按 `/spec → /plan → /build → /test → /review → /ship` 六个阶段固化流程、质量门和最佳实践，让 agent 在每一环行为一致。
**为什么值得关注**：Agent Skills 格式正在变成跨工具事实标准，这个库是"把工程规范做成可移植资产"规模最大的一次示范，也是给自建 agent 流水线的人现成的参考。
Stars：115,905（今日 +788）｜JavaScript
https://github.com/addyosmani/agent-skills

### 3. vercel-labs/agent-browser — 给 agent 一个纯文本浏览器（Rust CLI）
`snapshot` 把页面转成紧凑的可访问性树，每个元素带 `@e1` 这类 ref，然后一条命令一个动作。
**为什么值得关注**：绕开视觉模型截图 + 坐标点击那套又贵又不稳的方案，纯文本 + a11y 树对 token 和稳定性都更友好。做自动化 agent 的人，比套 Playwright 更省事。
Stars：49,839（今日 +712）｜Rust
https://github.com/vercel-labs/agent-browser

### 4. shadcn/improve — 贵模型写计划，便宜模型干活
一个 agent skill：用最强的模型审计代码库、判断什么值得做、写成自包含的实施计划（`plans/001-fix-n-plus-one.md`），自己不写一行实现代码。支持 `/improve quick|deep|security|branch|next`。
**为什么值得关注**："plan is the product" —— 直接针对现在 agent 成本结构做分工，输出纯 markdown，任何 agent 都能接手。省钱思路很具体。
Stars：10,832（今日 +333）
https://github.com/shadcn/improve

### 5. openai/codex-security — OpenAI 把安全扫描做成 CI 基础设施
Codex Security CLI + TypeScript SDK：扫描仓库/路径/Git 变更，验证漏洞、生成补丁、校验修复，起草 SECURITY.md、存威胁模型，导出 SARIF/JSON/CSV，并接 Linear、Jira、GitHub Actions。
**为什么值得关注**：这是 OpenAI 从"模型供应商"往"工程基础设施"再走一步，直接对着 Snyk、Semgrep 的地盘。今天新增项目里最值得盯的一个。
Stars：11,691（今日 +20，刚上榜）｜TypeScript
https://github.com/openai/codex-security

### 6. homeassistant-ai/ha-mcp — 87 个工具的 Home Assistant MCP 服务器
v7.3.0 起改为随 Home Assistant 2026.11+ 通过 HACS/Marketplace 内嵌安装，带 webhook 远程接入、侧边栏管理面板、可选账号鉴权。（注意：`ha_config_set_yaml` 已移入 beta）
**为什么值得关注**：MCP 从开发者玩具进入消费级硬件生态的标志。智能家居是最容易验证 agent 真实价值的场景，也是"AI 控制物理世界"最先落地的地方。
Stars：7,332（今日 +640）｜Python
https://github.com/homeassistant-ai/ha-mcp

### 7. ZhuLinsen/daily_stock_analysis — 多市场股票 LLM 分析，零成本定时跑
覆盖 A股/港股/美股/日股/韩股/台股自选股，多源行情 + 实时新闻 + 决策看板，每日自动推送到企微/飞书/Telegram/Discord/Slack/邮箱，跑在 GitHub Actions 上不花钱。附 arXiv 论文（2608.26990）。
**为什么值得关注**：stars 70,179、forks 56,828 —— fork/star ≈ 0.81，罕见的"人人 fork 自建"形态，说明它的用法就是让你自己部署一套。中文社区项目在 Trending 上继续高位，且拿了 Trendshift 当日 Python 第一。
Stars：70,179（今日 +429）｜Python
https://github.com/ZhuLinsen/daily_stock_analysis

---

### 非 AI 补充
- **we-promise/sure**（Ruby，12,918 stars，今日 +1,079）个人理财 app，今日全榜增速第一，社区驱动的开源替代（YNAB/Monarch 那类）。
- **GoogleChrome/modern-web-guidance-src**（TypeScript，1,717 stars，+133）仓库无简介，从命名看是 Chrome 团队现代 Web 开发指南的内容源仓库，偏内容型；今天新上榜。
- **TheAlgorithms/Java**（Java，67,001 stars，+108）老牌算法实现库，周期性回归榜单。

---

**今日趋势判断**：榜面几乎被"给 agent 用的基础设施"占满——技能包（agent-skills、improve）、执行工具（agent-browser）、安全扫描（codex-security）、设备控制（ha-mcp）、设计系统（astryx）。共同点是都不再追求"更聪明的模型"，而是在补 agent 落地缺的那一层工程件。真正的新品类是第 4 个：把"贵模型规划 / 便宜模型执行"模型分工做成了可复用技能。
