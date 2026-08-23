
今日 GitHub Trending 扫描完成：18 个热门项目中 7 条新内容，筛出 6 个 AI/Agent 相关项目（vaultwarden 为密码管理器，非 AI 领域，已略过），已全部标记已读。

---

# GitHub Trending 日报（2026-08-24）

## 1. block/buzz — 人类与 AI Agent 共处一室的开源协作空间
- **简介**：Block（Jack Dorsey 旗下）开源的 Rust 项目。自托管的协作工作区，人类和 AI Agent 共享同一"房间"：每条消息、工作流步骤、代码评审、git 事件都是 Nostr relay 上的签名事件，单一日志、统一身份模型、完整审计链。"on a relay you own"——数据主权在自己手里。
- **为什么值得关注**：大厂下场做"人机协作空间"，直接把 Nostr 协议当成 Agent 协作的事实日志层。自托管 + 签名事件意味着 Agent 行为可审计、可溯源，对"Agent 基础设施该长什么样"是一个强信号。30k stars 五个月涨完，社区热度极高。
- **Stars**: ★30,083（今日 +349）| Rust | Apache 2.0
- **链接**: https://github.com/block/buzz

## 2. anthropics/claude-plugins-community — Anthropic 官方社区插件市场
- **简介**：Anthropic 官方的 Claude 插件社区市场镜像仓库（read-only），支持 Claude Code 和 **Claude Cowork** 两个产品。插件经 claude.ai 提交、自动安全扫描后上架，每夜从内部审核管线同步。
- **为什么值得关注**：这是 Anthropic 首次放开插件生态的官方入口——插件生态的"App Store"模式正式落地。注意 README 里出现的新产品名 **Claude Cowork**，配合官方插件库（anthropics/claude-plugins-official）和知识工作插件（knowledge-work-plugins），说明 Anthropic 正在系统化布局 Agent 生态位。
- **Stars**: ★920（今日 +257）| Python
- **链接**: https://github.com/anthropics/claude-plugins-community

## 3. VoltAgent/awesome-agent-skills — 1000+ 跨平台 Agent 技能合集
- **简介**：精选官方团队与社区的 1000+ 个 Agent 技能（skills），兼容 Claude Code、Codex、Gemini CLI、Cursor 等主流工具，附官网 officialskills.sh 检索。
- **为什么值得关注**：Skills 正在取代提示词成为 Agent 能力复用的主流载体，这份清单相当于该领域的"awesome 清单"基准——找技能、学范式、看各厂商官方实践，一个仓库全搞定。
- **Stars**: ★31,270（今日 +223）
- **链接**: https://github.com/VoltAgent/awesome-agent-skills

## 4. virgiliojr94/book-to-skill — 技术书 PDF 一键变 Claude Code 技能
- **简介**：Python 工具，把任意技术书 PDF 转成可直接使用的 Claude Code skill——看书时随时调取、引用、边学边用。
- **为什么值得关注**：把"读书"变成"给 Agent 装知识包"，是上下文工程（context engineering）方向的实用落地。五个月冲到 24.6k stars，说明"知识资产管理"需求真实且旺盛。
- **Stars**: ★24,626（今日 +423）| Python
- **链接**: https://github.com/virgiliojr94/book-to-skill

## 5. freestylefly/awesome-gpt-image-2 — GPT-Image2 工业级提示词引擎（中文项目）
- **简介**："Prompt as Code"理念的 GPT-Image2 提示词模板库：470+ 个案例逆向工程、20+ 套工业级模板，并提炼成可复用 Skills，持续更新。作者为中文开发者。
- **为什么值得关注**：把图片提示词做成"工程化资产"（模板化、版本化、可复用），是目前图片生成领域少见的系统化打法，对做 AI 图像产品的团队参考价值高。
- **Stars**: ★12,673（今日 +440）| JavaScript
- **链接**: https://github.com/freestylefly/awesome-gpt-image-2

## 6. Comfy-Org/ComfyUI — 模块化扩散模型工作流引擎
- **简介**：最流行的扩散模型 GUI/API/后端，图节点式工作流，支持 Stable Diffusion 系全生态。今日 +179 再次回到 Trending。
- **为什么值得关注**：129k stars 的老牌项目再度上榜，说明图像生成工作流社区仍在持续活跃；作为 Comfy 生态的底座，每次上榜都值得关注配套节点的动向。
- **Stars**: ★129,361（今日 +179）| Python
- **链接**: https://github.com/Comfy-Org/ComfyUI

---
**今日趋势小结**：Agent Skills 生态（VoltAgent、book-to-skill、claude-plugins-community）占据半壁江山，Anthropic 插件市场 + Block 的 Nostr 协作空间是两条值得深挖的新叙事。
