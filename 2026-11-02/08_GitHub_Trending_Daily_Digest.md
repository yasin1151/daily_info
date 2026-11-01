
今日 GitHub Trending 扫描完成（17 个项目，筛出 13 个 AI/Agent/开发工具相关，合计今日新增约 1.1 万 stars）。blogwatcher 识别 7 条新条目，已全部标记已读。

---

## 今日 AI 热门项目（按今日新增 stars 排序）

**1. t3code — 把本机所有编码 Agent 收进一个控制台**
- 简介：pingdotgg（Theo）出品的 "agent harness control surface"，通过 iOS/Android 应用、Web 和 Electron 桌面端远程控制本机上的 Claude Code、Codex、Cursor、Grok Build、OpenCode、Antigravity、fx。免费开源，作者明确说不卖东西，方向不对可以直接 fork。
- 为什么值得关注：今天榜首（+3,100）。它不生产 Agent，只做"遥控层"，正好补上各家 CLI Agent 缺移动端和统一入口的短板；对同时订了 Claude + Codex + Cursor 的人是刚需形态。
- Stars：37,859（今日 +3,100）
- https://github.com/pingdotgg/t3code

**2. claude-mem — 给所有 Agent 装一个跨会话记忆**
- 简介：记录 Agent 在每次会话中的所有动作，用 AI 压缩后把相关上下文注入后续会话。支持 Claude Code、OpenClaw、Codex、Gemini、Copilot、OpenCode，以及 Hermes。
- 为什么值得关注：109k stars、今日 +1,527，说明"Agent 记不住上一轮"已成普遍痛点。它是外挂式记忆层，不改 Agent 本体，接入成本低；描述里点名支持 Hermes，值得本地试一次对比现有 memory。
- Stars：109,180（今日 +1,527）
- https://github.com/thedotmack/claude-mem

**3. hex — 本地语音听写（Rust）**
- 简介：anomalyco 出品，mac/Windows/Linux 全平台本地语音转文字，纯 Rust。
- 为什么值得关注：今日 +1,329，是榜上增速第二。和同榜的 Handy 撞车，说明"离线听写"正在变成独立品类——隐私 + 零延迟 + 不按 token 计费，比云端 STT 更适合长时段写码口述。
- Stars：3,223（今日 +1,329）
- https://github.com/anomalyco/hex

**4. Claude-Code-Game-Studios — 用 49 个 Agent 搭一间游戏工作室**
- 简介：把 Claude Code 改造成完整游戏开发工作室：49 个 AI Agent + 72 个工作流 skill，加一套模拟真实工作室层级的协调系统（Shell 脚本 + skill 编排）。
- 为什么值得关注：今日 +970。它是"多 Agent 组织架构"最激进的一次公开实验——不是并行跑几个助手，而是复刻策划/程序/美术/QA 的汇报链路。对做 Agent 编排的人，这套层级与交接协议本身比游戏产出更值得读。
- Stars：32,214（今日 +970）
- https://github.com/Donchitos/Claude-Code-Game-Studios

**5. OpenMausBot — 开源版 Grok Bot，给 Bot 一台虚拟机**
- 简介：开源的 Grok Bot 替代品，每个 Bot 配一台可操作的虚拟机。
- 为什么值得关注：今日 +919。Grok 的 Bot 能力一直闭源，这里是"Agent + 真机环境"的开源复刻路线，VM 隔离解决了 Agent 执行任意代码的安全顾虑。
- Stars：10,485（今日 +919）
- https://github.com/milind-soni/OpenMausBot

**6. lightpanda — 为 AI 而生的无头浏览器**
- 简介：Zig 写的 headless browser，定位 AI 与自动化场景，主打低资源占用（对比 Chromium 系）。
- 为什么值得关注：今日 +827。Agent 抓网页的瓶颈常在浏览器本身太重；一个 Zig 实现、专为程序化访问优化的内核，可能把单机并发抓取成本压下一个量级。属于 Agent 基础设施层的关键拼图。
- Stars：40,076（今日 +827）
- https://github.com/lightpanda-io/browser

**7. Kronos — 金融市场的"语言模型"**
- 简介：面向金融 K 线/时序的基础模型，把行情当语言建模（Python）。
- 为什么值得关注：今日 +611。金融时序长期被 Transformer 霸占但又难做通用基础模型，这条"行情即语言"的路线在开源里少见且已有 45k stars，做量化或时序预测的可以直接对标。
- Stars：45,346（今日 +611）
- https://github.com/shiyu-coder/Kronos

**8. ai-engineering-hub — LLM/RAG/Agent 实战教程库**
- 简介：patchy631 维护的深度教程集合，全部 Jupyter Notebook，覆盖 LLM、RAG 和真实 Agent 应用。
- 为什么值得关注：今日 +573。教程类能持续上榜说明"能跑通的代码"仍是稀缺品；比起又一篇综述，它是可执行 notebook，适合当 Agent 工程的参考实现。
- Stars：40,192（今日 +573）
- https://github.com/patchy631/ai-engineering-hub

**9. AiSOC — 开源 AI 安全运营中心**
- 简介：告警融合 + LLM Agent 分诊 + MITRE ATT&CK 调查，加一份可回放的决策账本（decision ledger）。
- 为什么值得关注：今日 +436。"可回放决策账本"是安全场景最实用的设计——LLM 判断必须能审计复现。安全运营是 Agent 落地最容易算清 ROI 的方向之一。
- Stars：6,194（今日 +436）
- https://github.com/beenuar/AiSOC

**10. Handy — 完全离线的语音转文字**
- 简介：免费开源、可扩展的语音转文字应用，完全离线运行（Rust）。
- 为什么值得关注：今日 +383。和 hex 同日上榜，两者一起把"本地听写"推成趋势；Handy 更偏应用化（可扩展、开箱即用），hex 更偏轻量内核。
- Stars：36,506（今日 +383）
- https://github.com/cjpais/Handy

**11. FreeToken — 把数据中心级推理搬到桌面**
- 简介：在本地桌面上跑超大模型，主打"快且高效"的本地服务化推理（Python）。
- 为什么值得关注：今日 +232。本地推理的瓶颈从"能不能跑"转向"跑得像不像服务端"，这类项目直接决定个人机器能否替代 API 账单。
- Stars：15,373（今日 +232）
- https://github.com/FlashML-org/FreeToken

**12. OpenBot — 每个 AI 同事配一台自己的电脑**
- 简介：CopilotKit 出品，开源 AI 同事，每个 Bot 拥有独立浏览器、文件和工具，且"每个动作在执行前先被决定"（预决策 + 审批门控）。
- 为什么值得关注：今日 +178。"动作先决策再执行"是对 Agent 失控问题的直接工程回应，对做企业内 Agent 权限设计有参考价值。
- Stars：9,498（今日 +178）
- https://github.com/CopilotKit/OpenBot

**13. kornia — 空间 AI 的几何计算机视觉库**
- 简介：PyTorch 生态的几何 CV 库，可微几何变换、相机模型、3D 视觉基础算子（Python）。
- 为什么值得关注：今日 +88。具身/空间智能热起来后，几何视觉重新变成基础设施；它是这个方向最稳定的开源底座之一。
- Stars：11,767（今日 +88）
- https://github.com/kornia/kornia

---

## 一句话观察

今天的榜单结构很清楚：**上层全是 Agent 的控制面与记忆（t3code、claude-mem、Claude-Code-Game-Studios、OpenBot、OpenMausBot），底层是 Agent 的感官与算力（lightpanda 浏览器、hex/Handy 语音、FreeToken 本地推理）**。中间层"模型本身"几乎没有新项目——说明社区这波精力已经从"训模型"整体转向"把模型接进工作流"。另外语音输入一天冒出两个 Rust 项目，是可以提前关注的信号。

未入选（非 AI 向）：public-apis、ziwei-doushu（紫微斗数排盘）、jailbreaks、Hyprland。
