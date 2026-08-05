
# GitHub Trending 今日 AI / Agent / 开发工具项目

本次扫描发现 2 个未读 Trending 项目，均与 AI Agent / 开发工具基础设施相关，已完成标记已读。

---

## 1. Cloudflare Computer：给 Agent 一个可执行的“云端电脑”

**项目简介**  
Cloudflare Computer 是 Cloudflare 推出的预览级虚拟文件系统与执行环境，运行在 Durable Object 之上。它把权威状态保存在 SQLite 中，并通过统一的 `workspace.runtime.exec()` 暴露多种执行后端，包括容器、隔离 shell、隔离 JavaScript Worker 等。

**为什么值得关注**  
这是一个非常典型的“Agent Runtime / Agent Computer”基础设施方向：  
- 为 AI Agent 提供持久化文件系统、可执行环境和状态同步能力；  
- 同时支持真实 Linux userland、Dynamic Worker shell、JavaScript 模块执行；  
- 很适合观察 Cloudflare 如何把 Workers、Durable Objects、容器和 Agent 工作区组合成下一代云端执行层。  

项目目前明确标注为 Preview，不适合生产，但对 Agent 沙箱、远程工作区、云端 IDE / 自动化执行平台都有参考价值。

**语言**：TypeScript  
**Stars**：2,824  
**今日新增 Stars**：796  
**链接**：https://github.com/cloudflare/computer

---

## 2. LoopX：面向长期运行 AI Agent 团队的本地控制平面

**项目简介**  
LoopX 是一个轻量级状态内核和本地控制平面，用于管理长期运行的 AI Agent 工作流。它不替代 Codex、Claude Code、Cursor 等 Agent Runtime，而是负责维护目标、关卡、TODO、证据、配额、交接和可复盘状态。

**为什么值得关注**  
LoopX 抓住了当前 Agent 工程里的一个核心痛点：单次任务容易，长期任务难。它试图解决：  
- Agent 多轮执行中的目标漂移、证据过期、交接困难；  
- 多 Agent / peer agent team 的任务声明、租约、边界和状态同步；  
- Scheduler 持续唤醒 Agent 时的配额和有效性控制；  
- 把长期 Agent 工作变成类似“Agent-native Kanban”的可治理流程。  

如果关注 Codex / Claude Code 自动化、长任务 Agent、数字员工、工程化 Agent 团队，这个项目值得跟踪。

**语言**：Python  
**Stars**：2,080  
**今日新增 Stars**：327  
**链接**：https://github.com/huangruiteng/loopx
