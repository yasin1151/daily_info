
# GitHub Trending 今日热门（2026-11-13）

## 今日主线
今天榜单上最明显的变化：**为 coding agent 准备的技能包正在成为独立品类**。Chrome 团队、Meta、Addy Osmani 在同一天上榜，做的都是同一件事：把人类工程师的经验打包成 agent 能直接读取的 skills。第二条线是基础设施层面的消息：OpenAI 把安全扫描做成了正式 CLI 产品，本地推理引擎则继续在语言层面展开竞争。

---

## AI / Agent

**1. astryx：Meta 开源的设计系统，为“人机协作”而设计**
Meta 内部用了八年的设计系统，支撑过 13,000+ 个应用，今天首次开源。包含 150+ 个无障碍组件、品牌主题和 CLI，基于 React 19 + StyleX，但不绑定样式方案，Tailwind 和 CSS Modules 都能覆盖。它最特别的是“agent ready”：API、文档、CLI 三者统一设计，人和 AI 助手依照同一套参考构建，不需要再让模型猜测你的组件用法。
26,471 stars（今日 +1,789，今日涨幅第一） · https://github.com/meta/astryx

**2. codex-security：OpenAI 官方出品的代码安全扫描 CLI**
`@openai/codex-security` 是能在 Codex 里直接调用的安全 workflow：扫描仓库或 Git diff、验证可疑漏洞是否真实、生成补丁、校验已有修复，还能起草 SECURITY.md 和威胁模型。同时提供 TypeScript SDK 和 GitHub Action，支持导出 SARIF/JSON/CSV，也能把结果同步到 Linear、Jira。它的意义在于：在 AI 写代码越来越快的背景下，安全审查也被做成 agent 可以自动串联执行的环节，而不是等到最后人工一顿扫描。
12,382 stars（今日 +663） · https://github.com/openai/codex-security

**3. agent-skills：把资深工程师的工作流拆成 9 条 slash command**
Addy Osmani 的新项目，按 DEFINE→PLAN→BUILD→VERIFY→REVIEW→SHIP 生命周期拆成 `/spec` `/plan` `/build` `/test` `/constraints` `/review` 等命令，每条命令会自动调用对应技能。核心主张很明确：先写规格再写代码、把任务切成小步、用测试证明结果有效。它不绑定特定模型或客户端，属于“给所有 agent 用的方法论层”。
116,646 stars（今日 +812） · https://github.com/addyosmani/agent-skills

**4. modern-web-guidance-src：Chrome 想让 agent 不再写 2015 年的前端代码**
Google Chrome 团队出品，由 Chrome、Edge、Firefox、MDN 四方共同维护。本质是一套给 coding agent 使用的 web 平台知识库，内容包括最佳实践和浏览器兼容数据；它会引导 agent 避开已废弃写法，直接采用新 API。`npx modern-web-guidance install` 安装后可以搜索指南、按 ID 取用，还有 `legacy-scan .` 直接扫出项目里的过时模式。这个项目值得关注，是因为浏览器厂商开始主动介入 agent 的知识来源。
2,845 stars（今日 +799，三天内从零起步） · https://github.com/GoogleChrome/modern-web-guidance-src

**5. OpenBot：每个 AI 同事配一台自己的电脑**
CopilotKit（AG-UI 协议作者）出品，自托管、可换模型、可接你已有的 agent。每个 bot 有独立的浏览器、文件系统、工具，关键设计是：动作执行前先做决策、执行后记录全过程，需要人批准时才发送。可以直接安装 macOS / Windows 桌面版，也支持 K8s 部署。定位是“企业内可审计的 AI 数字同事”。
11,569 stars（今日 +291） · https://github.com/CopilotKit/OpenBot

**6. free-claude-code：把 12 种 harness 接到 61 家 provider 上**
一个路由层，让 Claude Code、Codex、OpenCode、Cline、Aider、VS Code Chat 等 12 种客户端去调用任意 provider 的模型，保留了原生流式输出、工具调用和 interleaved thinking。宣称每月 1.3B+ 免费 token，还能通过 RTK / Headroom 降低 90% 的用量，并带有供应商宕机自动重试。它同时把 Hermes 列入了支持的 harness。需要注意的是，这类项目依赖各家 TOS 的容忍度，作者也声明了“一旦不再允许就移除”。
69,257 stars（今日 +461） · https://github.com/Alishahryar1/free-claude-code

**7. qwen-code：Qwen 的终端 coding agent 放出 1.0 Preview**
阿里的开源 coding agent，TypeScript 编写，支持 OpenAI / Anthropic / Gemini / Qwen 四种协议，可在运行时切换，也能接 Ollama、vLLM。1.0 Preview 把 Qoder 的 agent harness 能力合并了进来，支持 Auto-Memory、Auto-Skills、SubAgents、Agent Teams、MCP。有意思的是，它不光支持终端，还支持 IDE 插件、桌面端、Web UI，以及 Telegram/钉钉/微信/飞书集成。README 里称它现在用自己来给自己报 issue、提 PR、跑测试。
29,781 stars（今日 +151） · https://github.com/QwenLM/qwen-code

**8. TensorFold：用 Zig 写的推理引擎，不装 Python 也能跑**
用 Zig 二进制直接在 Apple Silicon 和 NVIDIA GPU 上跑 LLM，直接运行 Metal/CUDA kernel，读取 checkpoint、做分词都在引擎内完成，不需要 Python 或 MLX。工程上还有个值得一提的细节：作者另做了一个 Agent Traffic Control 工具，让多个 agent 在提 PR 前先“抢单”，避免重复劳动和冲突，说明 agent 协作已经开始需要调度机制。
1,926 stars（今日 +94） · https://github.com/ashhart/TensorFold

**9. llama.cpp：老牌本地推理引擎继续稳定在榜**
134,529 stars（今日 +287） · https://github.com/ggml-org/llama.cpp

---

## 非 AI 但涨势明显
- **we-promise/sure**：面向所有人的个人财务应用，13,874 stars（今日 +974，今日涨幅第二） · https://github.com/we-promise/sure
- **HermesEnabler**：在任意 Apple Watch 上启用爱马仕表盘，支持 watchOS 27.0–27.3 beta 1，需要侧载 IPA。跟我们的 Hermes 无关，纯属同名撞车，1,516 stars（今日 +300） · https://github.com/pookjw/HermesEnabler
- **nvm** 96,000（+107）、**node** 123,588（+133），属常规波动。

---

**读法建议**：如果你只关注一件事，就看看前三名，它们代表了同一个趋势：agent 的能力上限越来越取决于“喂给它的技能和规范质量”，而不是模型本身。Chrome 拿浏览器兼容数据做 skills、Meta 拿设计系统做 skills、Addy 拿工程流程做 skills，接下来很可能每个成熟领域都会有人做一份。
