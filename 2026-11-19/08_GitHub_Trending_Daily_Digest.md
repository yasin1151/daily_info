
# GitHub Trending 日报 · 2026-11-19

今日共扫描 20 个项目，筛出 12 个 AI、Agent 与开发工具相关项目。**主线上看，这是 Skill 与 harness 生态的一次集体上榜**：前十里有一半是 Claude Code、Codex、Cursor 的“技能包 + 评测 + harness”项目，说明社区关注点已从“写模型”转向“给 agent 装工具、评工具质量”。

---

### 1. Claude-BugHunter — 给 Claude 装一套白帽子技能库
把 82 个技能、15 个 slash command、24 类漏洞的 681 条真实披露报告模式打包成 Claude Code 技能包，专门用于挖洞和外部红队；另附企业身份与基础设施攻击矩阵。
**为什么值得关注**：这是今天涨幅第一的项目（+2,322）。它代表一个新趋势：安全从业者不再写自己的脚本，而是把渗透方法论固化成 agent 可以调用的 skill，降低了红队的门槛，同时也说明安全对齐的攻防面正在扩大。
**Stars**：11,320（今日 +2,322）· Python
https://github.com/elementalsouls/Claude-BugHunter

### 2. PaperOrchestra — Google 的多智能体“论文写作机”
一个多 agent 框架，把 AI 研究论文的撰写流程自动化：文献梳理、实验叙述、成稿编排分工协作。
**为什么值得关注**：由 google-research 官方发布，仅 4.2k stars 却单日涨 1,529，是典型的“官方背书 + 痛点直击”型项目。学界对 AI 代写论文的争议本来就大，这类工具一出现，就会直接冲击评审与署名规范，后续讨论值得跟进。
**Stars**：4,241（今日 +1,529）· Python
https://github.com/google-research/paper-orchestra

### 3. ECC — 给 agent 做“性能调优层”
自我定位为 agent harness 性能优化系统，向 Claude Code、Codex、Opencode、Cursor 注入技能、直觉、记忆、安全约束和研究优先的工作流。
**为什么值得关注**：30 万 stars 的体量说明它已是事实标准之一。它切中的是真问题：同一个模型，harness 写得好不好，产出质量能差一倍；这类“模型外挂层”正在成为新的竞争赛道。
**Stars**：306,462（今日 +1,109）· JavaScript
https://github.com/affaan-m/ECC

### 4. last30days — 跨平台“近 30 天”调研技能
一条指令就能让 agent 同时翻 Reddit、X、YouTube、HN、Polymarket 和网页，汇总成有出处的研究简报。
**为什么值得关注**：它把“舆情 + 预测市场”两类信号合并进研究流程，接近我们自己每天在做的事。它的走红说明：通用搜索已经不够，能按平台特性分别取数的 agent 才有价值。
**Stars**：69,964（今日 +1,062）· Python
https://github.com/mvanhorn/last30days-skill

### 5. superpowers — 有方法论支撑的技能框架
一个 agentic skills 框架，附带一套完整的软件开发方法论，主打 subagent 驱动开发、头脑风暴和 SDLC 各阶段技能。
**为什么值得关注**：32 万 stars，是“技能标准化”路线的代表。它与其他项目的区别在于强调流程：不只是提供工具，还要求 agent 按人类工程规范一步步执行；这类项目直接影响 coding agent 的稳定性上限。
**Stars**：321,296（今日 +823）· Shell
https://github.com/obra/superpowers

### 6. Arcane — 面向所有人的现代 Docker 管理面板
Go 写的自托管 Docker 管理界面，把容器、镜像、网络、compose 的日常运维可视化。
**为什么值得关注**：在满是 agent 项目的榜单里，它是少数纯基础设施工具，单日 +547 说明自托管需求依然强劲。对跑一堆 agent 服务的人来说，这是比 Portainer 更现代的替代选项。
**Stars**：9,778（今日 +547）· Go
https://github.com/getarcaneapp/arcane

### 7. CLI-Anything — 让所有软件都变成 agent 原生
港大数据智能实验室出品，主张把任意 CLI 工具包装成 agent 可以直接调用的能力层，配套 CLI-Hub 分发站。
**为什么值得关注**：这解决的是 agent 落地时最脏的一环：绝大多数专业软件只有命令行，没有 API。把 CLI 标准化成 agent 接口，比再写一个 MCP server 更通用，路线选择很值得观察。
**Stars**：59,711（今日 +384）· Python
https://github.com/HKUDS/CLI-Anything

### 8. stitch-skills — Google 官方的 Agent Skills 库
为 Stitch MCP server 提供的一组 Agent Skills，遵循 Agent Skills 开放标准，兼容 Antigravity、Gemini CLI、Claude Code、Cursor。
**为什么值得关注**：Google 明确押注跨 agent 的技能互操作标准，而不是绑定自家 CLI。如果这个开放标准真的被采纳，技能包就能一次编写、到处运行，生态格局会明显不同。
**Stars**：10,385（今日 +369）· TypeScript
https://github.com/google-labs-code/stitch-skills

### 9. SkillEvaluator — NVIDIA 的“技能质检”框架
多层评估框架：质量门禁、语义重叠检测、合成评测集生成，以及衡量技能如何实际改变 agent 行为的在线评估。
**为什么值得关注**：技能数量爆炸之后，必然要回答“哪些技能是有害的、冗余的”。NVIDIA 抢先布局评测层，相当于在技能市场里做“评级机构”，这个位置一旦立住，话语权很大。
**Stars**：3,699（今日 +323）· Python
https://github.com/NVIDIA/SkillEvaluator

### 10. cursor/plugins — Cursor 的插件规范正式开源
包含 Cursor 插件规范说明与官方插件实现，供第三方扩展编辑器能力。
**为什么值得关注**：编辑器厂商开始把扩展生态标准化，与 Anthropic 的技能包、Google 的 MCP 技能库形成三套并行标准。今天榜单同时出现这三家，标准之争的信号非常明确。
**Stars**：17,179（今日 +315）· TypeScript
https://github.com/cursor/plugins

### 11. n8n — 带原生 AI 能力的工作流自动化平台
Fair-code 授权的工作流引擎，可视化搭建 + 自定义代码 + 400 多个集成，可自托管。
**为什么值得关注**：+315 的稳定涨幅说明它已是“AI 工作流编排”的默认选项之一。对于不想写代码又要接模型的人，它比自研 pipeline 划算得多。
**Stars**：211,052（今日 +315）· TypeScript
https://github.com/n8n-io/n8n

### 12. uv — Rust 写的 Python 包管理器
极快的 Python 包与项目管理器，单二进制，兼容 pip 工作流。
**为什么值得关注**：+260 属于长尾稳定增长。做 AI 工程几乎绕不开 Python 环境，uv 目前是解决依赖地狱最省事的选择；如果你还在用 pip + venv，迁移成本很低。
**Stars**：92,214（今日 +260）· Rust
https://github.com/astral-sh/uv

---

**其他相关但不展开**：appwrite（+239，自称“面向 agent 与开发者的开源云”，Auth/DB/存储一站式）、punkpeye/awesome-mcp-servers（+52，MCP 服务器索引）、openvinotoolkit/openvino（+18，AI 推理部署工具链，动量偏低）。非 AI 类今日上榜：svelte、jQuery、solid、nvm、江山时序历史地图。

**一句判断**：今天榜单的真实信息量不在单个项目，而在结构：Skill 包（供给）、harness（优化）、评测（质检）、标准（Google/Cursor/Anthropic 三家）已经凑齐一条完整产业链。半年内大概率会出现“技能市场 + 评级”的整合者，值得提前关注 NVIDIA 和 Google 这两条线。
