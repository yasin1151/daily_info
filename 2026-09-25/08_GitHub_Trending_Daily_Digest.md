
**GitHub Trending 每日速报 | 2026-09-25**
本次扫描：Trending 榜单 14 个项目，其中 5 个为新增收录（3 个 AI 相关，2 个非 AI 已过滤）。AI/Agent 类项目今日继续霸榜，Top 3 全部为 Agent 基础设施方向。

---

**一、新增收录 · AI 相关（3 个）**

**1. Hindsight —— 会「学习」的 Agent 记忆系统**（今日 +1,607 ★，涨幅全场第一）
vectorize-io 出品，定位 "Agent Memory That Learns"，让 Agent 在长期运行中积累并复用经验，而不是每次从零开始。配套完整文档、集成库、独立 Benchmark 站和 arXiv 论文，工程化程度较高，已有 Hindsight Cloud 商业版本。
为什么值得关注：Agent 记忆是当前最热的工程痛点之一（长任务漂移、上下文遗忘），这个项目把「记忆」做成了可评估、可插拔的标准组件，且有论文+Benchmark 背书，属于会长期沉淀的基础设施，而非一次性 demo。
Stars：27,745 ｜ 语言：Python
https://github.com/vectorize-io/hindsight

**2. stable-diffusion.cpp —— 纯 C/C++ 跑扩散模型**（今日 +69 ★）
支持 SD、Flux、Wan、Qwen Image、Z-Image 等多种扩散模型的纯 C/C++ 推理，无 Python 依赖。
为什么值得关注：本地部署/边缘推理的关键拼图。想在 Mac、树莓派、嵌入式设备上不装 CUDA、不装 PyTorch 就跑图生图，这是目前最省事的路子；老项目今日重新上榜，通常意味着近期有重要模型适配更新。
Stars：7,236 ｜ 语言：C++
https://github.com/leejet/stable-diffusion.cpp

**3. NVIDIA Model-Optimizer —— 模型压缩统一工具箱**（今日 +22 ★）
NVIDIA 官方库，统一了量化（quantization）、蒸馏、剪枝、NAS、投机解码、稀疏化等 SOTA 优化技术，输入支持 HF / PyTorch / ONNX 模型。
为什么值得关注：MLOps 实用派工具。与其自己拼 bitsandbytes、torchao、TensorRT-LLM 的零散脚本，不如用官方一把抓的方案，跨框架兼容性好，适合做模型上线前的统一瘦身流水线。
Stars：4,060 ｜ 语言：Python
https://github.com/NVIDIA/Model-Optimizer

---

**二、榜单其他 AI / Agent / 开发工具项目**

**4. google/ax —— Google 的 Agent 编排运行时**（今日 +1,376 ★）
声明式 Agent 编排器，用 YAML 定义 Task/Workspace（Git 仓库、目标、网络围栏），由 AX 负责沙箱化执行、依赖注入和集群级调度，官方定位「类 Kubernetes 体验」，目标单集群跑数十亿 Agent 任务，底层基于 Agent Substrate 做沙箱隔离。
值得关注：Agent 从「单机脚本」走向「集群调度」的信号，Google 亲自下场定义 Agent 编排的标准姿势。不过 README 明确警告核心概念和 API 尚未稳定，会有破坏性变更，现在更适合观察而非生产使用。
Stars：10,370 ｜ 语言：Go
https://github.com/google/ax

**5. dream-num/univer —— 「Office Harness for AI Agents」**（今日 +1,060 ★）
高性能可嵌入式 Office SDK，把表格、文档、幻灯片、多维表格、画板、PDF 统一到一个插件化架构里，Canvas 渲染 + 公式引擎，浏览器和 Node.js 同一套 Facade API。
值得关注：Agent 要真正干活，绕不开「读写 Office 文件」这一关。这个项目把自己重新定位成 Agent 的办公套件底座，正好踩中 Agent 办公自动化这个大风口。
Stars：17,558 ｜ 语言：TypeScript
https://github.com/dream-num/univer

**6. obra/superpowers —— Agent 技能框架 + 开发方法论**（今日 +606 ★）
Shell 实现，主张「可用的 agentic skills framework」，强调方法论而不只是代码。
值得关注：在 Agent 生态里，"skills/技能包" 正在形成事实标准（Claude Skills、OpenClaw skills 等），这个项目是方法论侧的代表，适合借鉴它怎么组织技能、怎么约束 Agent 行为。
Stars：291,220 ｜ 语言：Shell
https://github.com/obra/superpowers

**7. anthropics/financial-services —— Claude 金融服务参考 Agent**（今日 +510 ★）
Anthropic 官方的金融服务 Agent 参考实现，覆盖投行、股票研究、私募、财富管理四大场景，含 Pitch Agent、Market Researcher、GL Reconciler 等命名 Agent，同一套 system prompt 和 skills 既可作为 Claude Cowork 插件安装，也可通过 Claude Managed Agents API 部署。
值得关注：官方给出的「垂直行业 Agent 怎么落地」范本，含合规免责声明和人工签核设计，对做行业 Agent 的人有直接参考价值；也说明 Anthropic 正把 Agent 推向受监管行业。
Stars：37,342 ｜ 语言：Python
https://github.com/anthropics/financial-services

**8. superdesigndev/treg —— 「Agent 工具的 OpenRouter」**（今日 +470 ★）
一个 base URL + 一个 token，即可调用 3,000+ 端点、60+ 供应商的 Agent 工具（SEO/外链、社交趋势、企业信息富化、广告、爬虫、图视频生成），按次计费、最低一分钱起，无需向各供应商注册。核心卖点：把 Semrush $139/月、Moz $99/月、Crunchbase $99/月这类订阅墙后面的能力，转成按调用付费，并支持团队密钥托管在服务端不落地到 Agent。
值得关注：Agent 工具变现的新模式，直接解决「为一个任务订一整月 SaaS」的成本痛点；也回答了「Agent 该按任务而不是按工具来思考」的产品思路。
Stars：3,145 ｜ 语言：Python
https://github.com/superdesigndev/treg

**9. strands-agents/harness-sdk —— 生产级 Agent Harness SDK**（今日 +463 ★）
Strands Agents 出品，主打「模型驱动、几行代码构建 Agent」，提供 Python 与 TypeScript 双语言的生产级 Agent Harness SDK，可端到端控制 Agent 执行。
值得关注：与 google/ax 上下呼应，说明「Harness（执行外壳/编排层）」正在成为 Agent 工程的关键抽象层。适合需要自建 Agent 运行时、又不想从零造轮子的团队。
Stars：8,238 ｜ 语言：Python
https://github.com/strands-agents/harness-sdk

**10. HKUDS/CLI-Anything —— 让所有软件都成为 Agent 原生**（今日 +415 ★）
港大数据智能实验室（HKUDS）项目，口号 "Making ALL Software Agent-Native"，配套 CLI-Hub 站点（clianything.cc），趋势徽章显示曾获当日 Trending 第一。
值得关注：思路是补齐 Agent 与存量软件之间的适配层——不必等每个软件原生支持 MCP，先把 CLI 能力标准化暴露给 Agent。与 OpenAI、Anthropic 推动的 CLI/工具化方向一致，实用性强。
Stars：50,319 ｜ 语言：Python
https://github.com/HKUDS/CLI-Anything

**11. rohitg00/ai-engineering-from-scratch —— 从零学 AI 工程**（今日 +310 ★）
口号 "Learn it. Build it. Ship it for others."，从零开始构建 AI 工程能力的教程/课程式仓库。
值得关注：AI 工程（而非算法研究）方向的学习资源持续被追捧，说明市场对「会搭系统、会调 prompt、会做 RAG 和 Agent」的工程能力需求旺盛，适合作为团队新人入门材料。
Stars：56,516 ｜ 语言：Python
https://github.com/rohitg00/ai-engineering-from-scratch

---

**三、已过滤（非 AI 方向，仅备注）**
- FxEmbed/FxEmbed（新增）：修复 X/Twitter 与 Bluesky 在 Discord 等平台的嵌入显示，5,358 ★，今日 +165
- julyx10/lap（新增）：离线优先的本地照片管理器，2,859 ★，今日 +151，Vue
- mvt-project/mvt：手机取证工具包（Mobile Verification Toolkit），14,719 ★，今日 +275

---

**一句话趋势判断**：今日榜单几乎是「Agent 基础设施专场」——记忆层（Hindsight）、编排层（google/ax、harness-sdk）、工具层（treg、CLI-Anything）、办公底座（Univer）、行业垂直 Agent（Anthropic 金融）齐备，一条从底层到应用的 Agent 技术栈正在快速成型；腾讯、字节之外，Google 与 Anthropic 也开始用开源仓库抢标准定义权。

已标记 5 篇新文章为已读。
