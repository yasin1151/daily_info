
**AI Builders 日报｜2026-06-11**

- **Thariq / Claude Code @ Anthropic**：他展示了用 Fable 编辑自己发布视频的流程：模型写了大量代码，并通过工具调用完成转录、`ffmpeg`、调色、Figma MCP、Remotion UI 和渲染，几乎不碰传统视频编辑器。  
  **为什么重要**：这是“agent 做创意生产流水线”的好例子：不是单点生成，而是把 MCP、CLI、多媒体工具、代码生成串成可复用工作流。对自研 Agent 工具链来说，关键能力是工具编排、文件/媒体上下文、长任务状态与可审计步骤。  
  https://x.com/trq212/status/2064826394589442448

- **Mike Krieger / Anthropic Labs（AI & I 播客）**：他认为 Fable 这类模型会迫使用户重新学习任务拆解方式：从短 prompt/即时问答，转向长时程、多会话、后台子 agent、动态 workflow。他举例把一个 Python 内部项目通过 workflow 迁移到 TypeScript/Bun：先理解代码、生成规格说明、逐模块翻译、增量测试、对抗检查，最后产出可运行迁移版本。  
  **为什么重要**：Agent 产品的核心界面可能不再只是 chat，而是“用 chat 生成、用代码表达、用 UI 监控”的 workflow。自研引擎要支持 plan 可视化、子任务恢复、分阶段验证，以及不同子任务路由到不同强度/成本模型。  
  https://www.youtube.com/watch?v=XWpTgCvgYaE

- **Mike Krieger / Anthropic Labs（AI & I 播客）**：他还提到 agent-native architecture：软件里的每个动作都应该能被 agent 访问和调用，进一步让 agent 能从软件内部修改软件本身；例如移动端里通过 managed agent 接收编辑请求、展示 live preview 和 diff。  
  **为什么重要**：这指向下一代 SaaS/工具软件架构：不是“给现有 UI 加聊天框”，而是把产品能力暴露成稳定 tool surface，让 agent 能读状态、改状态、验证结果。对 Hermes/OpenClaw 类系统，MCP/tool schema、权限边界、preview/diff、回滚会成为基础设施。  
  https://www.youtube.com/watch?v=XWpTgCvgYaE

- **Thibault Sottiaux / Codex & ChatGPT @ OpenAI**：他说过去 48 小时 Codex 的 token 消耗出现强劲增长，而且不是由明确发布驱动。  
  **为什么重要**：coding agent 的使用开始从“尝鲜”进入高频生产环境，token 消耗增长本身说明长任务、多轮修复、并发 agent session 正成为常态。工具链需要更重视成本观测、任务预算、模型路由和失败重试策略。  
  https://x.com/thsottiaux/status/2064911328087810308

- **Aaron Levie / Box CEO**：Box 用自己的 Complex Work Eval 测 Fable 驱动的 Box AI Agent，称其相对 Opus 4.8 在复杂企业文档任务上更稳定，尤其是多步计算、复杂推理和跨行业一致性；示例包括法律尽调、医疗、金融服务等。  
  **为什么重要**：企业 agent 的评测正在从通用 benchmark 转向真实业务文档与流程任务。对自研引擎来说，eval 不应只测答题正确率，而要测“多步任务完成率、跨运行一致性、领域规则遵守、可解释证据链”。  
  https://x.com/levie/status/2064922814688481678

- **Zara Zhang / Builder**：她提出团队应该为彼此构建 agents/skills，例如设计团队为市场团队构建设计 agent，让市场能在品牌规范内自助产出素材；组织也会从按 function 划分，逐渐转向按 loop 划分。  
  **为什么重要**：高价值 agent/skill 往往不是通用助手，而是由领域专家把隐性知识、规范、判断标准封装成跨团队能力。对 Hermes 技能系统来说，这强化了“技能即组织知识接口”的方向：专家沉淀上下文，其他团队通过 agent 消费。  
  https://x.com/zarazhangrui/status/2064835289559023958

- **Garry Tan / YC CEO**：他提到 Nessie 可以把 ChatGPT、Perplexity、Gemini 的上下文、记忆和历史迁移到其他记忆系统，并特别提到 OpenClaw/Hermes Agent 与 MCP servers。  
  **为什么重要**：agent 的长期竞争点会落到“可迁移记忆”和“跨工具上下文连续性”。如果用户的历史、偏好、项目状态不能带走，agent 会变成孤岛；MCP + memory bridge 可能成为个人 AI 工作台的底层粘合层。  
  https://x.com/garrytan/status/2064947145652994510

- **Claude / Anthropic**：Claude Platform 新增 scheduled deployments 和 vault 环境变量。  
  **为什么重要**：平台正在补齐生产化 agent/app 运行能力：定时部署、密钥管理、环境隔离。这些看似普通 DevOps 功能，但对 agent 工作流上线非常关键，因为 agent 生成/修改的应用也需要安全、可重复、可调度的发布路径。  
  https://x.com/claudeai/status/2064741184547795408
