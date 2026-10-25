
# GitHub Trending 日报 · 2026-10-26

今日榜单 11 个项目，AI 相关占 9 个。**最明显的信号：前五名里有四个是“给 Coding Agent 用的技能包”（设计、安全、SEO），而不是新的模型或框架。** Agent 的竞争焦点正在从“谁的模型强”转向“谁的技能生态好用”。

---

## 一、今日新上榜（blogwatcher 新增 2 条）

### 1. Claude SEO — 给 Claude Code 装上 26 个 SEO 子技能
Python · 20,818 ★ · 今日 +179 · [github.com/AgriciDaniel/claude-seo](https://github.com/AgriciDaniel/claude-seo)

一站式 SEO 审计插件，含 26 个子技能和 19 个专职 agent，覆盖技术 SEO、Core Web Vitals、E-E-A-T、Schema.org、外链、本地 SEO、电商与多语言。安装只需 `/plugin install claude-seo@agricidaniel-claude-seo`，MIT 协议，README 称有 1077 个测试通过。

**为什么值得关注**：它盯的是一个新战场——**GEO/AEO**，即“你的页面有多大可能被 Google AI Overviews、ChatGPT、Perplexity 引用”。传统 SEO 优化点击率，这里优化的是“被 AI 引用率”。把 26 个技能拆开卖服务是它的商业模式（README 里有 Pricing 段），开源核心 + 咨询变现的典型打法。

### 2. Coolify — 自托管版 Vercel/Heroku
PHP · 64,335 ★ · 今日 +192 · [github.com/coollabsio/coolify](https://github.com/coollabsio/coolify)

开源 PaaS，只要有 SSH 连接就能把 VPS、裸金属或树莓派变成部署平台。支持 GitHub/GitLab/Gitea 自动构建、360+ 一键服务、托管数据库、自动备份。

**为什么值得关注**：虽然不是 AI 项目，但它是“AI 应用自己部署”的基础设施。最大卖点是**没有锁定（lock-in）**——README 明确写：你停止使用 Coolify，跑着的服务照样跑、照样能管，所有配置留在你自己机器上。对成本敏感、想把模型服务和前端一起放自己服务器的人来说，这是 Vercel 账单的替代方案。

---

## 二、今日涨幅榜（AI 相关）

### 3. Cloudflare security-audit-skill — 把 Agent 变成安全审计员（今日第一）
JavaScript · 46,810 ★ · **今日 +2,874** · [github.com/cloudflare/security-audit-skill](https://github.com/cloudflare/security-audit-skill)

六阶段审计流程：侦察建模 → 按覆盖账本分配“猎人”agent → 对每个候选漏洞派独立验证员**尝试证伪** → 输出 `findings.json` 并做 schema 校验 → 再由全新 agent 独立复核结论 → 生成报告。

**为什么值得关注**：它源自 Cloudflare 内部漏洞挖掘流水线的单仓版本（配套博客《Build your own vulnerability harness》）。关键设计是**“证伪优先”**——不是让 agent 找漏洞然后相信它，而是让另一个 agent 专职推翻它。这解决的是 AI 安全扫描最大的问题：误报率高到没人看。这是目前 agent 工程化最扎实的一份公开参考实现。

### 4. VoiceStudio — 全本地 ElevenLabs 替代品
Python · 86,742 ★ · 今日 +1,588 · [github.com/debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio)

开源语音工作台：声音克隆、声音设计、视频配音、听写、转录、有声书制作，覆盖 646 种语言。Electron 桌面应用，全部本地跑，AGPL-3.0。

**为什么值得关注**：**“全本地”是它唯一的卖点，也是最强的卖点**。配音和克隆涉及真人声纹，很多公司根本不允许把音频传到第三方 API。646 种语言这个数字明显是冲着 ElevenLabs 的多语言订阅去的。成本敏感 + 数据不出门，两个需求一次满足。

### 5. Hallmark — 专门治“AI 味”的设计技能
CSS · 33,688 ★ · 今日 +1,359 · [github.com/Nutlope/hallmark](https://github.com/Nutlope/hallmark)

Together AI 出品的设计技能，支持 Claude Code / Codex / Cursor / OpenCode。从 48 套“材质主题”里发三套，按访客来干什么来排版，然后在真实浏览器里 lint 结果。

**为什么值得关注**：它的规则清单本身就是一份“AI 生成网页的破绽图鉴”——每个标题上方的小 eyebrow 标签、字距拉开的全大写小标签、标题里单独染色的一个词、满屏空框或只有图、hero 区撑不满一屏、每页末尾都塞订阅框、表单点了“谢谢”但其实没发送。还有个“新上下文评审员”拥有一票否决权。**这是把“审美”写成可执行 lint 规则的一次尝试**，比“让 AI 设计得更好看”这种空话实在得多。

### 6. Impeccable — 同一赛道，62 条确定性检测规则
Rust · 87,645 ★ · 今日 +1,113 · [github.com/pbakaus/impeccable](https://github.com/pbakaus/impeccable)

1 个技能、24 个命令（polish / audit / critique / distill / animate / bolder / quieter）、浏览器实时迭代，外加 62 条确定性检测规则。`npx impeccable install` 起步。

**为什么值得关注**：和 Hallmark 撞车但走的是两条路。它明确说自己**起源于 Anthropic 官方 frontend-design 技能**，并指出了根因：所有模型都在同一批 SaaS 模板上训练，所以每个项目都长出同一副脸——所有字体都用 Inter、紫到蓝渐变、卡片套卡片、彩色背景上放灰字、标题上方一个圆角方块图标。62 条规则在 CLI 和浏览器扩展里跑，**不需要 LLM、不需要 API key**，纯确定性检查。对不想为“设计评审”再付一次 token 费的人来说很重要。

### 7. Cindy — 开箱即用的开源本地 AI Agent
TypeScript · 4,819 ★ · 今日 +677 · [github.com/makecindy/cindy](https://github.com/makecindy/cindy)

本地运行的 agent，能读你真实文件、操作已登录的应用、驱动浏览器/电脑/手机，也能从 IM 和定时任务接活。首发支持 Claude Code 和 Codex 两个 harness，可中途切换模型和 harness，工作区、记忆、技能保持连续。

**为什么值得关注**：它的核心主张是 **harness 可插拔**——一个任务可以规划、并行执行、再由不同 harness×模型组合的 agent 交叉评审。记忆跨 harness 共享（“纠正一次，以后都对”），也支持用自己的 API key 或本地模型。星数刚 4.8k，属于早期但设计思路清晰的选手，值得放观察名单。

### 8. Microduck — 26cm 双足机器鸭，RL 策略驱动
Rust · 11,607 ★ · 今日 +657 · [github.com/pollen-robotics/microduck](https://github.com/pollen-robotics/microduck)

Pollen Robotics 的开源机器人“大脑”仓库。RK3566 芯片上跑几个守护进程：50Hz 控制环驱动 15 个舵机、无线和摄像头、防变砖的 OTA。策略在隔壁 `microduck_rl` 仓库训练——MuJoCo + PPO + sim2real + 导出 ONNX。

**为什么值得关注**：少见的**完整开源 sim2real 链路**，从仿真训练到真机部署全公开，代码量不大（约 25cm/800g 的硬件），适合当具身智能入门教材。Rust 写控制环 + ONNX 跑策略，也是当前机器人栈的典型组合。硬件可买，不是概念项目。

### 9. TradingAgents — 多 Agent 金融交易框架
Python · 114,562 ★ · 今日 +636 · [github.com/TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents)

多智能体 LLM 金融交易框架，配套论文 arXiv:2412.20138。让不同角色的 agent（基本面、情绪、技术面、风控等）分工讨论后共同决策。

**为什么值得关注**：11.4 万星说明“LLM 炒股”是最吸流量的题材之一。它有真论文、有 Discord 社区，是这个方向引用最多的基线实现。但这类项目要清醒看待：回测里好看的多 agent 辩论，实盘往往败给交易成本和滑点。**当研究框架看有参考价值，当发财工具看会很失望。**

### 10. ThinkRail — JetBrains 的 agentic IDE
TypeScript · 1,659 ★ · 今日 +52 · [github.com/JetBrains/thinkrail](https://github.com/JetBrains/thinkrail)

JetBrains 官方出品，基于开源 `pi` coding agent 包了一层富客户端：git worktree 隔离工作区、并行 agent、PR 状态一键推进，以及用“living specs”给 agent 持久项目知识。

**为什么值得关注**：**JetBrains 正式入场 agent IDE**。它跟 Cursor 的路线差别在“隔离”——每个 workspace 都是独立 worktree 和分支，agent 并行干活不碰你的工作副本，好的合并、差的删掉。这是把“多个 agent 同时改代码”这件事做得最工程化的方案。星数低是因为刚发布。

---

## 三、其余

**Renhuai123/ziwei-doushu** — TypeScript · 7,526 ★ · +255 · [链接](https://github.com/Renhuai123/ziwei-doushu)
紫微斗数开源排盘引擎，基于倪海厦《天纪》体系，含完整排盘算法、四化系统、格局知识库、古籍原文数据。非 AI 项目，但中文开源里少见的认真做领域数据结构化的一份。

---

## 一句话总结

今天榜单真正的信息量不在某个具体项目，而在于**“给 agent 写技能”已经形成独立赛道**：安全审计（Cloudflare）、前端设计（Hallmark / Impeccable，两家撞车）、SEO（Claude SEO）、部署（Coolify）——全部是“把某个专业工种的方法论固化成 agent 能执行的规则”。而且头部两条设计技能都在解决同一个问题：**怎么让 AI 生成的东西不像 AI 生成的**。这大概是 2026 年最实在的一个产品需求。
