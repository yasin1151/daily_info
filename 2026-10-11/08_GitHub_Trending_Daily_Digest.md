
# GitHub Trending 今日热门项目（2026-10-11）

数据源：github.com/trending（daily）。blogwatcher 的 scan 接口本次返回 504，已改为直连 GitHub Trending 页面抓取。已执行标记已读（队列中无未读项）。

---

## 一、AI / Agent 方向重点

**1. morluto/rea — 用 Agent 逆向一切**
- **简介**：让 Agent 做逆向工程，从应用层行为一路下探到原生二进制（native binaries）。TypeScript 实现。
- **为什么值得关注**：今日榜首，单日 +25,784 stars（总量 71.6k，一天涨了近 36%），是今天全站最猛的爆发。把「Agent 自主执行」从写代码、查资料推进到了逆向/二进制分析这种高门槛、强对抗的领域——过去是安全研究员的活儿，现在被包成通用能力。后续很可能会出现一批围绕它的 MCP/插件生态。
- **Stars**：71,619（今日 +25,784）｜**链接**：https://github.com/morluto/rea

**2. mattpocock/skills — 工程师的 Agent 技能库**
- **简介**：Shell 项目，「Skills for Real Engineers」，作者直接从自己的 `.agents` 目录搬出来的技能集合。
- **为什么值得关注**：今日总量第二（284.4k），单日 +1,737。它代表了一个明显趋势：**「技能（Skills）正在成为 AI 编码工具的一等公民」**——从个人 dotfiles 性质的自用配置，变成公开分发的工程资产。如果你在用 Claude Code / Codex，这类仓库就是可以直接抄作业的提示词与工作流模板。今天 Trending 上同类项目还有三个（见下），说明这个方向已经形成赛道。
- **Stars**：284,424（今日 +1,737）｜**链接**：https://github.com/mattpocock/skills

**3. multica-ai/andrej-karpathy-skills — 一个 CLAUDE.md 文件，修 Claude Code 的毛病**
- **简介**：单个 `CLAUDE.md` 文件，源自 Andrej Karpathy 对 LLM 编码常见坑的观察，用来改善 Claude Code 的行为。
- **为什么值得关注**：极简思路的典型——不写代码、不装依赖，一份配置文件就是全部。单日 +279、总量 218k，说明「把大佬的经验固化成一行行规则」比做一个新框架更容易被大规模接受。适合立刻拿来对比自己现有的 CLAUDE.md / AGENTS.md。
- **Stars**：218,238（今日 +279）｜**链接**：https://github.com/multica-ai/andrej-karpathy-skills

**4. anthropics/knowledge-work-plugins — Anthropic 官方的知识工作者插件库**
- **简介**：面向知识工作者、用于 Claude Cowork 的开源插件集合，Python。
- **为什么值得关注**：官方下场做插件市场信号意义强——**「通用 Agent」正在往「岗位化 Agent」走**。今天 +626 stars。看官方把哪些任务定义成「可插拔的插件」，基本等于看它认为知识工作里哪些环节最值得自动化。
- **Stars**：28,801（今日 +626）｜**链接**：https://github.com/anthropics/knowledge-work-plugins

**5. mksglu/context-mode — 给 AI 编码 Agent 省上下文**
- **简介**：上下文窗口优化工具。把工具调用输出沙箱化（官方称减少 98%），持久化会话记忆，并通过 MCP + hooks 在 17 个平台上做路由。
- **为什么值得关注**：解决的是所有重度 Agent 用户最真实的痛点——上下文被工具输出撑爆。它的做法（沙箱化 tool output + 会话记忆外置 + 统一路由）大概率会成为下一代 Agent 框架的标准配置，值得当架构参考读。今天 +178，热度不高但方向务实。
- **Stars**：26,300（今日 +178）｜**链接**：https://github.com/mksglu/context-mode

**6. hugohe3/ppt-master — AI 直接生成原生 PPT**
- **简介**：把文档或主题变成真正的原生 PowerPoint 文件——带原生形状、转场动画、按需生成的图表表格、由演讲者备注生成的旁白音频，并支持你自己的 `.pptx` 模板。Python。
- **为什么值得关注**：+515 今日。它和一堆「AI 生成幻灯片图片」的项目有本质区别：**输出的是可继续编辑的原生 pptx，而不是一堆缩不动的 PNG**。对必须交付可编辑文档的职场场景，这是分水岭。
- **Stars**：59,402（今日 +515）｜**链接**：https://github.com/hugohe3/ppt-master

**7. cathrynlavery/diagram-design — 给 AI 编码工具用的图表设计规范**
- **简介**：面向 Claude Code、Codex、GitHub Copilot、Cursor、Factory Droid、Pi 的编辑级图表规范，44 种图表类型，自包含 HTML + SVG。作者原话很有态度：**「No shadows. No Mermaid slop.」（不要阴影，不要 Mermaid 那堆糊弄人的东西）**
- **为什么值得关注**：+1,189，是今天「AI 辅助设计」里涨得最实在的一个。它的火说明社区已经对 Mermaid 默认审美彻底疲劳了，开始追求**由设计规范约束、而非模型随手生成**的图表输出。做技术文档/汇报的人值得直接拿来用。
- **Stars**：48,904（今日 +1,189）｜**链接**：https://github.com/cathrynlavery/diagram-design

---

## 二、其他高增速项目（非 AI，但今天很猛）

- **boykopovar/AnyPS5**（C++，26,698 stars，**+5,831**）：PS5 可执行文件自动移植到 Linux 和 Windows 的工具。今日增速第二，纯技术硬核。
  https://github.com/boykopovar/AnyPS5
- **storytold/artcraft**（Rust，14,395 stars，**+3,217**）：面向艺术家、设计师、影视从业者的「有意图的创作引擎」。增速第三。
  https://github.com/storytold/artcraft

---

## 三、老牌 ML 框架（今日小幅上榜，仅列示）

| 项目 | 语言 | Stars | 今日 + | 链接 |
|---|---|---|---|---|
| huggingface/transformers | Python | 167,236 | +94 | https://github.com/huggingface/transformers |
| pytorch/pytorch | Python | 104,134 | +81 | https://github.com/pytorch/pytorch |
| tensorflow/tensorflow | C++ | 200,719 | +24 | https://github.com/tensorflow/tensorflow |
| flutter/flutter（非 AI） | Dart | 179,503 | +164 | https://github.com/flutter/flutter |

---

## 今日一句话总结

榜单被**「Agent 的外围配套」**整体占领：逆向（rea）、技能库（mattpocock / karpathy-skills）、上下文治理（context-mode）、官方插件（Anthropic）、Agent 可用的设计规范（diagram-design）。纯模型框架只在底部象征性露脸，**说明这一天的注意力全在「怎么把 Agent 用好」而不是「再造一个模型」**。唯一非 AI 的爆款是 PS5 移植工具 AnyPS5，属于技术宅自发的硬核狂欢。
