
## GitHub Trending 每日精选 · 2026-11-14

扫描 12 个上榜项目，4 个为新增。以下为重点。

---

### 新增项目

**1. Plannotator —— 给 AI 编码智能体装上"人肉审阅层"**
- 项目：backnotprop/plannotator ｜ TypeScript ｜ ★10,437（今日 +100）
- 简介：本地浏览器里的审阅面板。智能体提出方案、写计划、生成 HTML 或跑完任务时自动弹开，你可以直接在页面上批注、圈改、评论，一键把反馈回灌给智能体执行。已适配 Claude Code、Codex、Copilot CLI、Gemini CLI、OpenCode、Kiro、Droid、Amp、Pi。新推出的 Plannotator Inbox 面向多智能体并行工作，汇总各类决策与产物待你拍板。
- 为什么值得关注：现在瓶颈不在"生成"而在"审"。Agent 一次输出几十个文件、几个方案，纯靠聊天窗口里读 diff 基本不可行。这类把 review 从终端搬到可视化界面的工具，是 agent 工作流真正落地到日常开发的关键缺口，比再造一个 agent 框架更实用。
- 链接：https://github.com/backnotprop/plannotator

**2. Claude Trading Skills —— 用 Skills 把投资流程"结构化"，而不是让 AI 下单**
- 项目：tradermonty/claude-trading-skills ｜ Python ｜ ★4,146（今日 +60）
- 简介：一套基于 Claude Skills 的个人投资工作流工具箱。作者定位很克制：不外包买卖决策，只把"复盘—风控—交易计划—交易日志—持续改进"这套流程固化成可执行的技能与清单。内置五条主流程：15 分钟每日市场体检、每周长线组合复盘、风险允许时才筛波段标的、每笔平仓强制写复盘、月度绩效回顾调整规则。依赖 Alpaca / FMP 等数据源，也支持手动 CSV 降级。
- 为什么值得关注：这是"Skills 化"思路在垂直领域的一个样本——把行业方法论包装成带决策闸门（discipline gate）的 Skill，而不是又一个"AI 荐股"套壳。README 开头就写明不构成投资建议、不保证盈利，态度罕见地诚实。
- 链接：https://github.com/tradermonty/claude-trading-skills

**3. Veyra —— Windows 上的实时 GPU 视频增强管线**
- 项目：Likely7/Veyra-NRVideo ｜ C++ ｜ ★1,608（今日 +245）
- 简介：把本地视频、采集卡、主机串流统一进一条实时 GPU 增强链路：超分辨率、降噪、HDR、帧生成，并支持 PS5 / Xbox / PC 串流采集。宣传语很标题党——"用 DLSS 5 让 PS5 上的 GTA6 跑到 120FPS"，实际是采集端做超分 + 插帧。
- 为什么值得关注：今日增速最快的项目之一（+245，几乎翻倍于体量更大的老项目）。说明消费级"AI 画质增强"仍是流量富矿，也侧面反映主机玩家对新作帧率的强需求。注意：这类项目常踩版权与 ToS 灰区，且效果高度依赖显卡型号，别只看宣传图。
- 链接：https://github.com/Likely7/Veyra-NRVideo

**4. Uptime Kuma —— 自托管监控老将回榜**
- 项目：louislam/uptime-kuma ｜ JavaScript ｜ ★93,845（今日 +61）
- 简介：界面漂亮的自托管服务监控工具，HTTP/TCP/Ping/DNS/推送心跳等探针齐全，自带状态页与多渠道告警。
- 为什么值得关注：不是 AI 项目，但对你这类"跑一堆定时任务和本地服务"的场景是刚需——cron 挂掉、网关失联能第一时间告警，而不是等推送没来才发现。放在这里作为运维工具推荐。
- 链接：https://github.com/louislam/uptime-kuma

---

### 榜上其他 AI 相关（此前已推过，今日热度）

| 项目 | 语言 | Stars | 今日 | 一句话 |
|---|---|---|---|---|
| GoogleChrome/modern-web-guidance-src | TypeScript | 4,793 | +1,875 | 给编码智能体实时喂最新 Web 最佳实践，今日全榜增速第一 |
| openai/codex-security | TypeScript | 13,112 | +754 | OpenAI 官方安全 CLI + SDK，自动发现、验证并修复漏洞 |
| ChromeDevTools/chrome-devtools-mcp | TypeScript | 55,438 | +145 | 把 Chrome DevTools 变成 agent 可调用的 MCP 工具 |
| alibaba/open-code-review | Go | 50,578 | +206 | 阿里规模化实战的代码审查：确定性流水线 + LLM Agent 混合架构 |
| ZhuLinsen/daily_stock_analysis | Python | 71,563 | +272 | LLM 多市场股票分析，多源行情+决策看板+定时推送，零成本运行 |
| block/buzz | Rust | 37,291 | +95 | Block 出品的"蜂群思维"通信平台 |

---

### 今日观察

三条主线很明显：**一是 agent 的"外围工程"正在成为主战场**（Plannotator 管审阅、chrome-devtools-mcp 管调试、modern-web-guidance-src 管知识注入、codex-security 管安全），单纯比拼模型能力的项目已经很难冲榜；**二是 Skills 化开始向垂直行业渗透**，claude-trading-skills 这种"方法论 + 决策闸门"的封装，比通用 agent 框架更容易验证价值；**三是消费级 AI 增强仍是流量洼地**，Veyra 靠一句 DLSS5 就跑出 +245。

已标记 4 条为已读，当前无未读积压。
