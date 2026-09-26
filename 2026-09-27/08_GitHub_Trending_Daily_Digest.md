
# GitHub Trending 日报 · 2026-09-27

## AI / Agent / LLM 重点

**1. Paperclip — 给"AI 员工"当公司管**
The open-source app everyone uses to manage agents at work。README 的比喻很直白：*"如果 OpenClaw 是一个员工，Paperclip 就是那家公司"*。Node.js 服务端 + React UI，Orchestrate 一队 AI agent 去跑业务：自带 agent、派目标、在同一面板看任务进度和成本。表层像任务管理器，底层是组织架构图、预算、治理、目标对齐和 agent 协同。
为什么值得关注：agent 编排正从"单机跑一个"转向"管一队人"，它把预算/权限/审计这些企业级问题做进了开源壳子里，是当前赛道最热的形态。
Stars 87,228（今日 +2,589）｜ https://github.com/paperclipai/paperclip

**2. Hindsight — 会"学"而不只是"记"的 agent 记忆**
vectorize-io 的 agent memory 系统，路线和主流截然不同：多数方案只做对话历史召回，Hindsight 主张让 agent 随时间真正学到东西，README 明确表示要绕开 RAG 和知识图谱的短板，在长期记忆任务上给出 SOTA 表现。可做 LLM wrapper、嵌入、MCP 接入，也直接支持 coding agent。
为什么值得关注：记忆是 agent 落地的最大瓶颈之一，"learn not just remember" 这个定位如果 benchmark 站得住，会直接冲击现有 RAG 栈。
Stars 32,121（今日 +2,152）｜ https://github.com/vectorize-io/hindsight

**3. Univer — 给 AI agent 用的 Office 底座**
"The Office Harness for AI Agents"：表格、文档、幻灯片、Bases、看板，PDF 在路上。高性能可定制的 Office SDK，插件架构 + Canvas 渲染 + 公式引擎，一套 Facade API 在浏览器和 Node.js 通用，允许嵌进自己的产品而不用跳进托管 App。
为什么值得关注：agent 要产出"人类可直接编辑的工作文件"，表格/文档是最硬的落地场景，这相当于把 Office 能力开放成 agent 的 API。
Stars 19,191（今日 +845）｜ https://github.com/dream-num/univer

**4. NVIDIA Model-Optimizer — 模型压缩的统一工具箱**
把量化、蒸馏、剪枝、神经架构搜索、投机解码等 SOTA 优化技术收进一个库，官方维护。
为什么值得关注：推理成本是所有人当下的痛点，NVIDIA 亲自统一这个工具面，等于给"怎么把模型塞进更小显存、跑更快"给出官方答案。
Stars 4,736（今日 +354）｜ https://github.com/NVIDIA/Model-Optimizer

**5. Buzz — 人和 agent 共处的自托管工作间**
Rust 写的自托管 workspace：*"人类和 AI agent 共享同一批房间"*，构建在你自己拥有的 relay 上，Apache 2.0。
为什么值得关注：主打"主权"（数据与中继都在自己手里）的多智能体协作空间，是对 Slack/Discord+bot 范式的一次重构尝试。
Stars 34,822（今日 +367）｜ https://github.com/block/buzz

**6. ai-engineering-from-scratch — 523 节课的 AI 工程课程**
作者正是 Agent Memory 的作者。README 原话：*"84% 的学生已在用 AI 工具，但只有 18% 觉得自己具备职业化使用它们的准备——这门课就是来补这个缺口的。"* 523 lessons / 20 phases / 约 342 小时，覆盖 Python、TypeScript、Rust、Julia，每节课都产出可复用件：一个 prompt、一个 skill、一个 agent 或一个 MCP server。免费、开源、MIT。
为什么值得关注：目前最系统的一份"从零做 AI 工程"教材，且强调产物落地而非理论。
Stars 58,343（今日 +828）｜ https://github.com/rohitg00/ai-engineering-from-scratch

**7. mobile-mcp — 让 LLM 直接操作手机**
MCP Server，打通 iOS/Android 真机、模拟器、仿真器：通过结构化 accessibility 快照或基于截图的坐标点击来操控原生 App，接口与平台无关，不需要分别懂 iOS 和 Android。兼容 Claude Code、Codex、Gemini、GitHub Copilot 等任意 MCP 客户端。
为什么值得关注：mobile agent 一直缺稳定的操作层，它把这条腿补齐了（新上榜）。
Stars 7,325（今日 +143）｜ https://github.com/mobile-next/mobile-mcp

**8. claude-code-action — 官方 Claude Code CI 动作（新上榜）**
Anthropic 官方通用 action，跑在 PR 和 issue 上：会回答提问、也能直接改代码。根据 workflow 上下文智能判断何时启用——响应 @claude 提及、被指派 issue，或用显式 prompt 执行自动化。支持 Anthropic 直连 API（API key 或 workload identity federation）等多种鉴权。
为什么值得关注：官方把 coding agent 塞进 CI 链路，code review / 自动修 issue 的默认姿势正在被标准化。
Stars 9,084（今日 +15）｜ https://github.com/anthropics/claude-code-action

**9. reverse-skill — AI 驱动的安全技能路由包**
逆向技能路由包 / Cybersecurity Skills Router：逆向工程、授权渗透测试、安全研究的技能路由 + 按需引导工具链，AI 驱动调度。全 PowerShell 实现。
为什么值得关注：安全圈在把"技能包 + AI 路由"当成新的 agent 分发格式，热度和题材都少见。
Stars 37,992（今日 +409）｜ https://github.com/zhaoxuya520/reverse-skill

## 开发工具 / 基础设施

- **microsoft/vscode** 193,066（+78，新上榜）— 编辑器本体，AI 侧的所有 IDE 集成都以它为主战场。
- **vercel/next.js** 142,619（+31，新上榜）— React 框架，前端默认选项，AI 应用 Web 层的常见底座。
- **tensorflow/tensorflow** 200,442（+31，新上榜）— 老牌 ML 框架，今日重回榜尾，热度来自存量而非新闻。
- **openbao/openbao** 7,999（+360）— 开源方案，管理、存储、分发敏感数据：密钥、证书、凭证。Vault 改协议后的社区继任者，AI 基础设施的密钥管理绕不开这类组件。
- **llvm/llvm-project** 40,746（+29）、**actions/runner-images** 13,296（+13，新上榜）— 编译器工具链与 CI 镜像，纯基础设施，与今日 AI 主线无关。

---
**今日主线判断**：榜单前二（Paperclip +2,589、Hindsight +2,152）合计新增近 4,700 stars，全部落在"多 agent 管理与 agent 记忆"这一层——社区注意力已从"造 agent"明确移到"管 agent、让 agent 记住"。Univer 代表的"agent 产出人类可编辑文档"是第二条清晰暗线。NVIDIA 下场统一模型优化工具面，则是推理成本压力在工具层的直接映射。

已标记本批 6 条未读为已读（tensorflow、vscode、claude-code-action、runner-images、mobile-mcp、next.js）。
