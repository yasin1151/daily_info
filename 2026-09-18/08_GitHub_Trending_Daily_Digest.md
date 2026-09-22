
扫描与抓取已完成，4 条新条目已标记为已读。以下是本次产出：

---

# GitHub Trending 每日速递 · 2026-09-18

今日 trending 榜共 20 个项目，筛出 **AI / Agent / LLM / 开发工具 / MLOps / 数据工程** 相关 16 项，按今日新增 star 排序（stars 为抓取时快照，同时用 GitHub API 复核了仓库创建时间与 topics）。

## 一、Agent 技能与 AI 审查（今日最强主线，4/4 全部相关）

**1. cloudflare/security-audit-skill** ★10,532（+3,606）· JavaScript
简介：把 coding agent 变成安全审计员的技能。六阶段流水线：侦察（产出 architecture.md + coverage-ledger.json）→ 覆盖度驱动的分片猎取 → 候选漏洞交由全新 agent 尝试**证伪** → 输出机器可读的 findings.json（confirmed / needs_validation / rejected 三种裁定）→ 独立复核最终结论 → 生成报告。附带零依赖校验脚本 validate-findings.cjs / validate-coverage-ledger.cjs。
为什么值得关注：**+3,606 是今日全站第一增幅**。README 里写明它就是 Cloudflare 那套"漏洞挖掘 harness"（官方博客《Build your own vulnerability harness》）的种子版本——大厂把内部漏洞发现流水线的单仓库起点直接开源了。真正的关键设计是"每个结论必须由独立 agent 试图推翻"，这恰好是 AI 安全审计最缺的信任环节：不是让 agent 更像专家，而是让它无法自说自话。多种目标类型（内存安全/LLM 提示注入/供应链/云与 IaC/租户隔离）都有独立狩猎类目文档，落地性极强。
https://github.com/cloudflare/security-audit-skill

**2. alibaba/open-code-review** ★34,651（+3,290）· Go
简介：AI 代码审查 CLI。源自阿里内部官方的 AI 代码审查助手，两年间服务数万名开发者、识别数百万代码缺陷后开源。阅读 Git diff → 交给可配置的 LLM Agent（带工具体系，能读全文、检索代码库、横向看其他变更文件）→ 输出行级精确的结构化审查意见；`ocr scan` 还能整文件扫描无 diff 的陌生代码库。官方基准（50 个开源仓库 / 200 个真实 PR / 10 种语言 / 80+ 资深工程师标注的 1,505 条 ground truth，数据集已在 HuggingFace 发布）：同模型下 Precision 与 F1 显著高于通用 agent（Claude Code），**token 消耗仅约 1/9**，并承认 Recall 更低——是有意用精度换噪音。
为什么值得关注：**+3,290 排今日第二**，且这是榜单第二天的持续发酵（昨日 +3,215）。含金量在于它明确点名了通用 agent 做代码审查的三个老毛病：大变更集下"抄近道"漏文件、报错位置漂移、纯自然语言 skill 质量随 prompt 抖动；然后用"确定性流水线定位置 + LLM 写解释"来分工解决。如果你的团队正在自建审查链路，这是当下最该对标的开源实现，还带公开 benchmark 可复现。
https://github.com/alibaba/open-code-review

**3. addyosmani/agent-skills** ★95,827（+680）· JavaScript
简介：面向 AI coding agent 的"生产级工程技能"合集（Addy Osmani 出品），25 个技能 + 9 个斜杠命令，完整映射开发生命周期（/spec → /plan → /build → /test → /constraints → /review → /webperf → /code-simplify → /ship）。`npx skills add addyosmani/agent-skills` 一条命令可装进 70+ 种 agent（Claude Code、Cursor、Codex、Copilot、Cline…），技能还会按上下文自动激活（设计 API 触发 api-and-interface-design，写 UI 触发前端工程技能）。
为什么值得关注：它把资深工程师的"质量门"固化成了可执行的流程资产，而不是再教 agent 写代码。`/build auto` 的设计思路值得学：一次批准计划后自动跑完所有任务，但去掉的只是**任务之间的人工步进**，不是验证——每个任务仍然是测试驱动、逐个提交，遇到失败或风险步骤会暂停。
https://github.com/addyosmani/agent-skills

**4. affaan-m/ECC** ★261,141（+1,173）· JavaScript
简介：自称"agent harness 性能优化系统"——用 Skills、instincts、记忆、安全策略和 research-first 开发流程，增强 Claude Code、Codex、Opencode、Cursor 等各家 agent（topics 覆盖 ai-agents/llm/mcp/productivity，官网 ecc.tools）。
为什么值得关注：26.1 万 star 在整张榜上是异类量级，且今日 +1,173 比昨日（+1,046）还在加速。它代表一个现实判断：**跨 harness 的统一增强层**比再做一个 agent 更被需要。值得关注的是它怎么抽象"记忆 + 本能"这两层，以及这套抽象换 harness 时是否真的可迁移。
https://github.com/affaan-m/ECC

## 二、Agent 运行环境与工具链（今日 3 个新入榜）

**5. Tencent/BrowserSkill** ★4,084（+1,350）· TypeScript
简介：让 AI agent 使用你**已登录的真实浏览器**，且不打断你自己的工作。由 `bsk` CLI/daemon + 浏览器扩展两部分组成；agent 需要碰你已打开的标签页时必须显式"借用"，任务结束归还，其他标签页一律不碰；浏览器任务跑在独立的可见 Agent Window 里。支持 Cursor、Claude Code、Codex、OpenClaw、CodeBuddy、Pi、Hermes Agent、DeepSeek Harness 等——只要 agent 能调 shell 就能用，不绑定模型或框架。遇到验证码、登录、确认弹窗等人类步骤时，会交还给你接管、完成后再继续。
为什么值得关注：+1,350 是今日第三增幅，且它是**今天新入榜**的项目（创建于 2026-06-22）。它切的是一个非常真实的痛点：agent 自动化卡在登录态和被封之上，业界通行做法是另开测试账号或无头浏览器，而它反过来复用你的真实会话，并用"显式借用 + 归还 + 人工接管"来对冲风险。这个交互契约（而非技术本身）才是最值得抄的部分。
https://github.com/Tencent/BrowserSkill

**6. TencentCloud/Octop** ★3,417（+386）· Python · MIT
简介：可自托管的多用户、多 agent AI 助手。单进程启动，同时提供 Web 控制台、CLI 和 IM 集成；可经飞书、钉钉、QQ、Discord、企业微信或 HTTP/SSE/WebSocket 对话；用"专家库"、Connectors（OAuth + MCP）和 ACP（IDE 工作流）扩展能力，topics 里有 local-first、long-term-memory。
为什么值得关注：今天新入榜（创建 2026-07-08），MIT 协议 + 完全自托管 + 多用户是它的差异点——大多数开源 agent 助手是"单人本地玩具"，它明确按团队/家庭共享场景设计。腾讯云出品，IM 侧集成（尤其国内几家用得上的）是现成优势。刚过 3.4k star，属于早期。
https://github.com/TencentCloud/Octop

**7. cline/cline** ★68,547（+381）· TypeScript
简介：自主编程 agent，同时提供 SDK、IDE 扩展、CLI 三种形态。
为什么值得关注：榜单常客，"同一内核、多形态分发"仍是 agent 产品化的成熟样本，热度稳定。
https://github.com/cline/cline

**8. coder/coder** ★14,816（+204）· Go · AGPL-3.0
简介：为开发者和**他们的 agent** 提供安全环境（远程开发环境平台，topics 含 agents、dev-tools、terraform、remote-development）。今天新入榜。
为什么值得关注：简介从"开发者"改成"开发者和他们的 agent"，这一字之差是行业信号——当写代码的主体变成 agent，环境供给层的需求就变了：需要一次性开出可销毁、可审计、带凭据边界的沙箱。值得关注它怎么用 Terraform 做 agent 运行环境模板。
https://github.com/coder/coder

## 三、知识 / RAG / 研究 Agent

**9. Tencent/WeKnora** ★26,164（+1,123）· Go（+1,123 排今日第五，昨日 +1,201，连续高位）
简介：开源 LLM 知识平台，三块能力：文档 → 可查询 RAG；带 MCP 工具、租户技能目录、会话级沙箱（Docker/E2B/Cube）的 ReAct Agent；以及 **Wiki Mode** —— agent 把原始文档蒸馏成互相链接、可自我维护的 Markdown 知识库，带知识图谱、修订历史与一键回滚。最新 v0.8.0 加了技能沙箱运行时、跨会话长期记忆、anydoc 进程内 Office 解析、GitLab/腾讯 IMA 数据源、LiteLLM；数据源覆盖飞书 / Notion / 语雀 / 钉钉文档 / RSS，IM 侧接企业微信、飞书、Slack、Telegram，20+ 模型 provider，多工作区 RBAC + 审计日志。
为什么值得关注：昨天说的"知识库自己维护自己"这条线今天仍在加速。它的定位已经明显转向**企业级知识基础设施**：多工作区 RBAC、四层角色矩阵、按 KB 的所有权、审计日志、按租户网络策略的沙箱——这些不是 demo 会做的东西。如果你在评估自建知识库，它的 CHANGELOG 本身就是一份"企业知识库该有哪些能力"的清单。
https://github.com/Tencent/WeKnora

**10. alphaXiv/OpenResearch** ★4,928（+940）· Rust
简介：research agent 的本地优先工作台。把 Claude Code、Codex、OpenCode、Cursor 变成能做文献综述、提假设、跑实验、产出研究成果的 research agent；`orx up` 起本地 dashboard（127.0.0.1:4791），支持接 LM Studio / oMLX / Ollama 本地模型；提供 macOS/Windows/Linux 客户端。README 里挂着 Trendshift"当日全站第一仓库"徽章。
为什么值得关注：+940 排今日第六。它的取巧之处在于**不自己造 agent**，只做本地工作台与流程编排，直接吃现有 coding agent 的能力——成本低、落地快。配合本地模型选项，对在意数据不出本机的科研/调研场景很合适。
https://github.com/alphaXiv/OpenResearch

**11. anthropics/knowledge-work-plugins** ★24,548（+287）· Python
简介：Anthropic 官方插件仓库，主要面向知识工作者在 Claude Cowork 中使用。
为什么值得关注：增幅平缓但方向重要——官方定义的"办公类插件"清单，等于 Anthropic 对"agent 该接管哪些非编程知识工作"的表态。想看 agent 从程序员工具向通用办公铺开的路径，这条线比单个热门项目更有指示意义。
https://github.com/anthropics/knowledge-work-plugins

## 四、本地推理与模型/视觉

**12. JustVugg/colibri** ★35,731（+872）· C · Apache-2.0
简介：纯 C、零引擎依赖的推理引擎，"把存储、RAM、VRAM 当作单一推理层级"（AI memory multitiering），从而在消费级与异构硬件上跑前沿 MoE 模型——744B 到 2.8T 参数。目前已支持九个模型家族，每个一个 C 文件、共用 `coli chat` / `coli serve` / `coli web` 前端：GLM-5.2/5.3（744B）、GLM-5.3-Flash（321B，带视觉）、Inkling（975B）、Kimi K3（2.8T）、DeepSeek V4 Flash（284B）、DeepSeek V4.1 Flash（552B，带视觉）、Qwen3.8-Flash-Next、Qwen3.6（35B-A3B）、OLMoE（7B）。实测 demo：GLM-5.2 744B int4 流式 CPU 32 秒就绪、常驻 9.9 GB。
为什么值得关注：昨天 +1,532，今天 +872，热度略退但仍在榜上，说明不是一日爆红后即沉。设计原则写得很有工程师味：**"速度没有 SLA，但语义有硬保证"**——实验必须靠可复现的端到端测量立足，默认策略绝不悄悄改模型精度或路由语义；快内存不够可以变慢，但不许悄悄改变模型。本地跑大 MoE 这条路上，这是当前最硬核的可运行实现。
https://github.com/JustVugg/colibri

**13. jamiepine/voicebox** ★54,827（+665）· TypeScript · MIT
简介：开源 AI 语音工作室——克隆、听写、创作三合一（topics 含 qwen3-tts、whisper、voice-clone、CUDA、MLX）。
为什么值得关注：语音方向少见的"工作室级完整产品"而非单点模型，且同时支持 CUDA 与 Apple MLX 两套后端，macOS 用户体验应该不错。注意仓库最近一次 push 是 2026-08-09，更新节奏不算活跃，更多是产品形态参考。
https://github.com/jamiepine/voicebox

**14. roboflow/supervision** ★50,796（+327）· Python
简介：Roboflow 出品的可复用计算机视觉工具库。
为什么值得关注：稳定增长的老项目，CV 流水线的默认选择之一，无新变化。
https://github.com/roboflow/supervision

## 五、其他入榜（非 AI 主线，一笔带过）

- **NationalSecurityAgency/ghidra** ★78,456（+912）· Java —— NSA 的逆向工程框架，增幅不低，通常说明安全话题在带动关注；今天恰好和 security-audit-skill 同榜。
- **n8n-io/n8n** ★204,958（+319）· TypeScript —— 工作流自动化平台，简介已强调"native AI capabilities"。
- **abue-ammar/tinycast** ★6,132（+738）· Swift —— 纯原生 macOS 启动器/快捷键/剪贴板历史，与 AI 无关。
- **ever-co/ever-gauzy** ★7,516（+469）· TypeScript（ERP/CRM/HRM 开源商业管理平台，非 AI 主线）；**cilium/cilium** ★25,257（+153）· Go（eBPF 网络/安全/可观测，今天新入榜但增幅平淡）。

---

**一句话总结**：今日主线依旧是 **"给 agent 装技能与流程，并解决 agent 结论可信度问题"**——cloudflare/security-audit-skill（独立证伪）+ alibaba/open-code-review（基准可复现、token 仅 1/9）+ addyosmani/agent-skills（工程门固化）+ ECC 四席同榜；第二条支线是 **agent 的运行环境开始被专门供给**（Tencent/BrowserSkill 复用真实登录态、coder/coder 给"开发者和他们的 agent"发环境、Octop 自托管多用户多 agent），三个新面孔都在这一侧。今天最值得先读的是 cloudflare/security-audit-skill（看它怎么让 agent 自我证伪）和 alibaba/open-code-review（带公开 benchmark，可直接对标自建审查链）。

（已标记 blogwatcher 4 条为已读，当前该源无未读；本次产出将按 job 83667c76356d 归入 08:30 的 GitHub 每日入库流程。）
