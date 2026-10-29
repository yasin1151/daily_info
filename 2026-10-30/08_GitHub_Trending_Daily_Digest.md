
**GitHub Trending 日报 · 2026-10-30**

扫到 11 个项目，其中 3 个是新增上榜。今天的榜单几乎是同一个主题：**「给 AI 一个自己的电脑 / 把 AI 组织成团队」**——个人 Agent 产品化、企业 Agent 治理、多 Agent 分工，三条路同时出现在 Trending 前列。

---

### 1. OpenMausBot — 开源的「Grok Bot」替代品，把 Agent 做成聊天软件

**简介**：Electron + React 19 的桌面应用，界面像 Telegram。侧边栏里每个「联系人」都是一个真实运行的 Agent——底层直接调用你本机已装的 `claude`、`codex`、`grok` CLI。每个 Bot 有自己的性格、自己的模型、自己的云端 Linux 桌面或隔离本地 VM，还能通过 Composio 接 500+ 应用。数据全部落在 `~/.openmausbot`，本地优先，不经过任何中间代理。

**为什么值得关注**：它抓住的洞察是——「一个助手装在对话框里」是错的形态。作者拆解了 2026 年七周内连发的四个闭源产品（Grok Bot、Meta Muse、OpenAI dots、Manus Cue），然后把这套「收件箱式 Agent 花名册」重建成开源版，模型和登录凭证都用你已有的。对一个天天和多个 CLI Agent 打交道的人来说，这是目前最接近「私人 Agent 团队」的开源形态。README 里还专门声明「没有代币，任何人发币都与我无关」，这个防御性声明本身就说明它火到什么程度。

**Stars**：7,439（今日 +1,190）｜TypeScript｜2026-08 创建
**链接**：https://github.com/milind-soni/OpenMausBot

---

### 2. OpenBot（CopilotKit）— 企业能真正「拥有」的 AI 同事

**简介**：Docker Compose 起一整套，数据进你自己的 PostgreSQL，模型不预置、由管理员填密钥（加密存储、不写日志）。每个 AI 同事分到独立容器，自带 Chromium、自己的登录态、自己的文件，只有你grant 的工具才能碰。关键设计是**所有工具调用都必须经过一个 gateway**：先按你的策略判定，写一条审计记录，然后才执行；被拒绝时会说明违反了哪条规则。

**为什么值得关注**：这是把「Agent 能不能信任」从提示词层面挪到了架构层面。CopilotKit 是 AG-UI 协议的推动方，所以这里 Agent 不被框架绑定——LangGraph、Mastra、CrewAI、Pydantic AI、Google ADK 写的都能接进来，治理逻辑跟着协议走而不是跟着框架走。定位也很克制：README 明说「这是模板不是产品，没有托管版可注册」，意思是让你 clone 下来改成自己的，CopilotKit 则卖「帮你部署进你的基础设施」的服务。企业 Agent 落地缺的正是这块审计与授权层。

**Stars**：8,109（今日 +240）｜TypeScript｜2026-08 创建｜MIT
**链接**：https://github.com/CopilotKit/OpenBot

---

### 3. Claude Code Game Studios — 把单个 Claude Code 会话变成一整间游戏工作室

**简介**：49 个 agent、74 个 skill、15 个 hook、14 条规则，全部以 `.claude/` 配置形式落地，按真实工作室层级编排：导演层守愿景，部门 lead 守各自领域，专员干具体活。配 74 个 slash 命令覆盖全流程（`/start`、`/design-system`、`/create-epics`、`/dev-story`、`/story-done`…），并支持 Godot、Unity、Unreal。

**为什么值得关注**：它解决的痛点是「一个人用 AI 做游戏没有结构」——没人阻止你硬编码魔法数字、跳过设计文档、写出意大利面代码，没有 QA、没有设计评审。这个项目本质上是把「组织流程」也做成了可检查的制品：hook 在 commit/push/资产变更时自动校验，规则按路径范围生效（改玩法代码和改 UI 代码适用不同标准）。对想知道「多 Agent 编排到底该怎么量化」的人，这是一个非常具体的参考实现——虽然它的旗帜鲜明，只服务于游戏开发这一件事。

**Stars**：29,129（今日 +538）｜Shell｜2026-02 创建｜MIT
**链接**：https://github.com/Donchitos/Claude-Code-Game-Studios

---

### 其他上榜（AI/ Agent 相关，简列）

| 项目 | 一句话 | 今日 |
|---|---|---|
| pbakaus/impeccable | 给 coding agent 用的「设计词汇表」，用 polish/bolder/critique 这类词指挥它改设计，专治 AI 味界面 | +2,881（Rust，95k★） |
| HKUDS/DeepTutor | 终身个性化教学辅导 Agent | +1,926（Python，50k★） |
| togg53192-cmd/jailbreaks | 作者把自己所有越狱提示词整理成列表 | +1,610（8.9k★） |
| elayadesign/ai-design-skills | AI 设计类 skill 合集（无描述，纯配置仓） | +1,178 |
| JetBrains/thinkrail | JetBrains 出的轻量 IDE，「会围绕你的工作方式自我定制」 | +1,116（TS，6k★） |
| obra/superpowers | Agentic skills 框架 + 一套软件开发方法论 | +1,037（308k★） |
| nightly-labs/openbot | 本地优先的桌面工作区，给常驻 AI 队友分配 Codex/Claude/Grok 的独立空间与任务队列 | +705 |
| thedotmack/claude-mem | 跨会话持久上下文：记录 Agent 全过程 → AI 压缩 → 下次注入 | +459（104k★） |

**值得注意的撞名**：`CopilotKit/OpenBot` 和 `nightly-labs/openbot` 同一天双双上榜，都是「每个 Agent 一台自己的电脑」，但一个走企业治理+审计路线，一个走个人桌面工作区路线。这种同题撞车通常意味着需求已经真实存在、而不是概念炒作。

已标记 3 条为已读。
