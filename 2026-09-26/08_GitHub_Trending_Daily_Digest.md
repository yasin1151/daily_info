
# GitHub Trending 日报 · AI 项目
**2026-09-26（周六）** ｜ 今日热榜 16 个项目，其中 AI/Agent/LLM/MLOps 相关 13 个

---

## 一、今日新上榜（首次进入热榜）

**1. paperclipai/paperclip**
- 简介：开源 AI 员工管理平台。Node.js 服务 + React 前端，把一组 AI agent 当作"公司"来编排：自带模型、指派目标、在同一看板追踪任务与成本。原话定位是"如果 OpenClaw 是员工，Paperclip 就是公司"。
- 为什么值得关注：agent 编排的竞争点正从"单个助手好不好用"转向"团队/组织级调度 + 成本核算"，这是企业真正落地时要回答的问题。今日 +1,853 星登顶全场。
- Stars：84.8k（今日 +1,853）｜ 语言：TypeScript
- https://github.com/paperclipai/paperclip

**2. androoAGI/starnet**
- 简介：local-first 桌面 agent harness。把 agent 组成一个像素风太空站，每个"房间 = 一个能力边界明确的团队"，界面不是装饰而是运行时状态的实时投影；自备 API key，跑真实模型和工具。
- 为什么值得关注：把 agent 运行时状态可视化、游戏化，是"可观测性 + 陪伴感"的一次有趣尝试，local-first + BYOK 路线也贴合隐私敏感场景。
- Stars：462（今日 +118）｜ 语言：JavaScript
- https://github.com/androoAGI/starnet

**3. shy3130/tick-stock-panel（TSP）**
- 简介：自托管的 A 股「选股 + 监控 + 回测」量化工作台，卖点是多数据源"能力路由"、分钟级策略执行、全时段异动监控，并内置 AI 对话助手（经 RunningHub 直连 400+ 大模型）。作者明确声明不内置"AI 荐股/涨停预测"，仅供学习研究。
- 为什么值得关注：中文圈少见的 LLM + 量化自托管方案，数据源插件化设计解决了"换一家数据源就要重写拉数代码"的老问题。
- Stars：5.1k（今日 +31）｜ 语言：Python
- https://github.com/shy3130/tick-stock-panel

---

## 二、持续在榜 · 今日涨幅榜（AI 相关）

**4. vectorize-io/hindsight** — Agent 记忆系统，强调"让 agent 学会"而不只是记住对话历史，宣称规避 RAG 与知识图谱的不足，配套 benchmark 和论文。信号：记忆赛道正从"召回历史"升级为"持续学习"。｜Stars 29.8k（今日 +1,652）
https://github.com/vectorize-io/hindsight

**5. google/ax** — Google 的声明式 agent 编排运行时：声明任务与 workspace，AX 负责沙箱化、接好环境、在集群上跑十亿级自主 agent 负载。官方已挂警告：核心概念与协议仍在剧烈变动，stable 前会有 breaking change。信号：大厂下场的"agent 基础设施"，走 k8s 式高吞吐调度路线。｜Stars 11.5k（今日 +1,386）
https://github.com/google/ax

**6. rohitg00/ai-engineering-from-scratch** — "Learn it. Build it. Ship it." 的 AI 工程教程仓库，已内置 12 种语言翻译页（含简体中文），作者同时是 Agent Memory 项目的作者。信号：系统化 AI 工程学习资料持续霸榜。｜Stars 57.5k（今日 +1,181）
https://github.com/rohitg00/ai-engineering-from-scratch

**7. dream-num/univer** — 自称"AI Agent 的 Office Harness"：表格/文档/幻灯片/Base/看板/PDF 收在同一个运行时，Canvas 渲染 + 公式引擎 + 统一 Facade API，浏览器与 Node.js 通用。信号：agent 要干活就得操作办公文档，这块正在被"给 agent 用的 Office SDK"重新定义。｜Stars 18.4k（今日 +1,048）
https://github.com/dream-num/univer

**8. NVIDIA/Model-Optimizer** — NVIDIA 官方模型优化库：量化、剪枝、NAS、蒸馏、投机解码、稀疏化，输入支持 HF/PyTorch/ONNX，输出直通 TensorRT-LLM、TensorRT、vLLM 做推理加速。信号：部署侧压缩的标准入口，MLOps 工具箱必备。｜Stars 4.5k（今日 +360）
https://github.com/NVIDIA/Model-Optimizer

**9. pbakaus/impeccable** — 给 AI 编码 agent 的"设计语言"：1 个 skill + 24 条命令 + 浏览器实时迭代 + 61 条确定性检测规则，专治 AI 生成前端的"塑料感"。信号：从"能生成"到"生成得好看"，开始出现约束 AI 审美的工程化工具。｜Stars 71.2k（今日 +326）
https://github.com/pbakaus/impeccable

---

## 三、Skills / 插件生态（今日 4 席，值得单列）

一个明显趋势：**"给 agent 装技能"已经成了最主流的项目分发形式**，今日热榜里有四席都是 skills 仓库。

- **obra/superpowers** — agentic skills 框架 + 软件开发方法论，被认为是这条路的开创者之一。｜Stars 291.6k（今日 +465）｜ https://github.com/obra/superpowers
- **mattpocock/skills** — "Skills for Real Engineers"，直接来自作者自己的 `.agents` 目录。｜Stars 269.7k（今日 +588）｜ https://github.com/mattpocock/skills
- **anthropics/skills** — Anthropic 官方 Agent Skills 公开仓库。｜Stars 178.3k（今日 +231）｜ https://github.com/anthropics/skills
- **anthropics/claude-plugins-official** — Anthropic 官方维护的 Claude Code 插件目录，做质量筛选。｜Stars 36.9k（今日 +62）｜ https://github.com/anthropics/claude-plugins-official

---

## 四、其他新上榜（非 AI 向，一笔带过）

- **derv82/wifit3** — Wifite 的 USB-only 跨平台重写（无线安全审计），901 星，今日 +168。
- **kelseyhightower/kubernetes-the-hard-way** — 经典 K8s 手工搭建教程，"不写脚本"路线仍在榜，50.1k 星，今日 +105。
- **openbao/openbao** — 密钥/证书管理方案（Vault 的开源分支），7.7k 星，今日 +16。

---

**一句话总结**：今日热榜主线是 **agent 的"组织化"与"技能化"**——上游有 paperclip（把 agent 当公司管）和 google/ax（集群级调度），下游有四个 skills/插件仓库负责能力分发；同时 agent 记忆（hindsight）、办公文档运行时（univer）、前端审美约束（impeccable）在补齐 agent 落地的短板。

（已标记 6 条未读为已读。）
