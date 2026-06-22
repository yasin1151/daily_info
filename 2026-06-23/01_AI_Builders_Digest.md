
# AI Builders Digest｜2026-06-22

今日有高信号更新，重点集中在 agent harness、模型路由、企业 headless agent、上下文工程与 coding agent 产品形态。

## 1. Aaron Levie：多模型路由正在变成 agent harness 的核心层
- **摘要**：Box CEO Aaron Levie 转述 Sakana 的 Fugu：对外是单一 API，对内自动完成模型选择、任务委派、验证与综合，把复杂的 multi-agent 系统隐藏在开发者代码之外。
- **为什么重要**：这和自研 Agent 引擎高度相关。未来差异化不只是“接哪个模型”，而是调度层能否按任务动态路由、验证输出、组合专家模型，并把复杂性封装成稳定 API。
- **链接**：https://x.com/levie/status/2068917230570795178

## 2. Aaron Levie：Agent 会比人类多 100 倍使用企业软件
- **摘要**：Levie 认为 agent 对 CRM、文档、知识库、分析系统的访问量会远超人类，因此企业软件需要权限护栏、数据防泄漏、审计日志、权威数据源、人机协作机制。
- **为什么重要**：这说明 Agent 工具链的基础设施需求正在从“能调用工具”升级到“可治理的 headless 操作系统”：权限、审计、上下文边界、数据最小化会成为平台级能力。
- **链接**：https://x.com/levie/status/2068851573175021864

## 3. Google DeepMind Logan Kilpatrick：coding harness 正在泛化成通用 agent harness
- **摘要**：Logan Kilpatrick 在 Training Data 播客中说，Google 的 Antigravity 不只是 IDE/CLI/SDK，而是一个可通过 Gemini API 使用的 managed agent 系统；同一套 harness 也在支撑 Search、Gemini App、Cloud、AI Studio 等产品。更关键的是，他认为 coding agent harness 已经证明自己可以成为通用 agent harness。
- **为什么重要**：这是大厂架构信号：agent 能力不再只是应用层功能，而是横跨产品线的统一执行层。自研引擎应关注“基础 harness + 场景特化适配”的分层，而不是为每个场景重写 agent。
- **链接**：https://www.youtube.com/watch?v=cMAs8z2dehs

## 4. Logan Kilpatrick：“模型正在吃掉 harness”，但外部 scaffolding 仍有窗口期
- **摘要**：Logan 认为“模型”已经不只是权重，而是包含工具调用、托管工具、搜索、代码执行、容器化运行环境和 agent harness 的大系统。外部 scaffolding 通常领先模型几步，但会逐渐被模型原生能力吸收。
- **为什么重要**：对自研 Agent 工具链的启发是：不要把护城河押在容易被模型内化的薄封装上；更有价值的是领域工作流、可靠性、权限治理、可观测性、数据连接、垂直场景经验。
- **链接**：https://www.youtube.com/watch?v=cMAs8z2dehs

## 5. Peter Yang：HTML/CSS/JS 可能是视频 agent 的中间表示
- **摘要**：Peter Yang 转述 Liu 的观点：视频 agent 难点在于模型缺少可靠视觉智能，因此他们转向代码；HTML 是 LLM 的“母语”，可以同时表达信息、视觉审美、素材、SVG、CSS 与 JS。
- **为什么重要**：这给多模态 agent 一个实用方向：不要直接让模型“看图/剪视频”，而是设计可编辑、可验证、可渲染的中间表示。对自研引擎来说，IR/DSL 可能比端到端生成更可控。
- **链接**：https://x.com/petergyang/status/2068755908319236338

## 6. Zara Zhang：高质量 AI 输出依赖更长、更扎实的上下文
- **摘要**：Zara Zhang 提出一个判断 AI slop 的经验法则：输入上下文是否长于输出？她发现高质量产出通常需要输入上下文达到输出的 3–5 倍。
- **为什么重要**：这不是 prompt 技巧，而是 context engineering 原则。Agent 工具链要重视上下文采集、压缩、排序、引用和任务状态管理；否则模型越强，越容易在贫弱上下文下生成“看似正确”的低质输出。
- **链接**：https://x.com/zarazhangrui/status/2068923768500793603

## 7. Garry Tan：个人脑 / 公司脑会成为 AGI 早期的关键杠杆
- **摘要**：Garry Tan 认为，在可用 AGI 早期，拥有个人脑和公司脑被低估了；AGI 给你智能，但真正的解锁来自你积累的个人与组织上下文。
- **为什么重要**：这和长期记忆、知识库、项目上下文、团队操作历史高度相关。Agent 平台的价值不只是执行任务，而是持续沉淀可调用的组织上下文。
- **链接**：https://x.com/garrytan/status/2068701356358308112
