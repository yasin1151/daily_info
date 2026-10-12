
# GitHub Trending 日报 · 2026-10-13

来源：GitHub Trending Daily（今日 9 个项目上榜，其中 **2 个为首次上榜**：open-webui、microsoft/BitNet）。已按 AI / Agent / LLM / 开发工具 / MLOps 相关性筛选。

## 今日焦点

**1. morluto/rea — 用 Agent 逆向一切的通用逆向工程台**
- 简介：把 LLM Agent 接进逆向工程链路，从 App 行为分析一路下探到原生二进制。内置 Ghidra / Hopper 反编译对接、MCP 协议、Claude Code 与 Codex 集成，覆盖二进制分析、CTF、静态分析。TypeScript。
- 为什么值得关注：单日 +45,495 star，是今天唯一量级破四万的项目。「AI Agent 做逆向」从零散脚本被做成了完整工具链，安全与 CTF 圈子讨论度最高。
- Stars：155,045（今日 +45,495）
- 链接：https://github.com/morluto/rea

**2. storytold/artcraft — 面向艺术家/设计师/影视人的 AI 创作引擎**
- 简介：Rust 编写的「有意图的创作引擎」，主打 AI 图像与视频生成工作流（topics: ai / aivideo / imagegeneration），偏影视级内容生产。
- 为什么值得关注：单日 +4,106 star，在「AI 视频」赛道里少见的本地优先、性能导向（Rust）实现，适合关注生成式内容生产管线的人。
- Stars：21,862（今日 +4,106）
- 链接：https://github.com/storytold/artcraft

**3. cathrynlavery/diagram-design — 给编码 Agent 用的「编辑级」图表生成技能**
- 简介：为 Claude Code、Codex、GitHub Copilot、Cursor、Factory Droid、Pi 提供 44 种图表类型的生成能力，输出自包含 HTML + SVG。作者口号很直白：No shadows, no Mermaid slop（拒绝 Mermaid 流水线味）。
- 为什么值得关注：单日 +2,100 star。Agent Skill 生态正在从「能写代码」扩到「能出可交付的设计稿」，这类审美向 skill 是很典型的信号。
- Stars：52,534（今日 +2,100）
- 链接：https://github.com/cathrynlavery/diagram-design

**4. lyogavin/airllm — 单张 4GB 显卡跑 2.8T 参数大模型**
- 简介：老牌分层加载推理项目回暖，主打在单张 4GB GPU 上完成 2.8T 级 LLM 推理（含 LoRA/QLoRA 微调相关 topics）。
- 为什么值得关注：+886 star。在显存仍是硬约束的当下，「小卡跑大模型」的低成本思路持续被重新发现，适合成本敏感的自部署场景。
- Stars：37,492（今日 +886）
- 链接：https://github.com/lyogavin/airllm

**5. Alishahryar1/free-claude-code — 白嫖 1.3B+ 免费 token 的多 harness 客户端**
- 简介：在终端 / App / IDE / 手机 / 浏览器里免费使用 Claude Code、Codex、VSCode、Pi、OpenCode 等 11 个 harness（多 harness + 多模型），号称 1.3B+ 免费 token，支持语音。
- 为什么值得关注：+705 star。名字本身就是流量密码，但也明显踩在服务商 ToS 边缘，属于「热度高、风险也高」，建议只当生态信号看。
- Stars：59,060（今日 +705）
- 链接：https://github.com/Alishahryar1/free-claude-code

**6. mksglu/context-mode — AI 编码 Agent 的上下文窗口优化中间层**
- 简介：把工具输出丢进沙箱（体积减少约 98%）、持久化会话记忆，并通过 MCP + hooks 在 17 个平台（Claude Code、Codex、Copilot、Cursor、OpenCode、Zed 等）之间做路由。
- 为什么值得关注：+394 star。上下文膨胀是编码 Agent 的头号工程痛点，做成跨平台 MCP 中间层是相当务实的解法。
- Stars：27,255（今日 +394）
- 链接：https://github.com/mksglu/context-mode

## 今日首次上榜

**7. open-webui/open-webui** — 最流行的自托管 AI 界面
- 简介：老牌开源 AI 对话界面，支持 Ollama、OpenAI API 及各类后端，自带 RAG、MCP 支持，靠自托管口碑长期霸榜。
- 为什么值得关注：首次进入本次监控的 Trending 列表（+142）。它上榜通常不代表新东西，而是「自托管 AI 入口」仍是刚需的常规信号。
- Stars：154,950（今日 +142）
- 链接：https://github.com/open-webui/open-webui

**8. microsoft/BitNet** — 微软官方 1-bit LLM 推理框架
- 简介：微软研究院官方 1-bit（三值）LLM 推理框架，用 C++ 在 CPU 上跑 BitNet 系列模型，主打极低内存与无 GPU 依赖。
- 为什么值得关注：首次进入本次列表（+134）。注意仓库最近一次推送是 2026-07-27，本次上榜更像是旧项目被重新捞起，而非有新迭代。
- Stars：40,892（今日 +134）
- 链接：https://github.com/microsoft/BitNet

---
**附注（非 AI，仅作趋势参考）**：`bilawalsidhu/gods-eye-view`（53,597★，+1,903）——浏览器里的开源「间谍卫星模拟器」，用真实数据在 3D 地球上做开放空间情报（OSINT/遥感），与 AI 无关但今日增速第二。

注：star / 今日新增数据来自 GitHub Trending 页面，总量已用 GitHub API 交叉核验一致；已通过 blogwatcher 将本次 2 条新条目标记为已读（当前该源无未读）。
