
GitHub Trending 今日热门 AI 项目（2026-10-08）

今日 Trending 共 13 个项目，筛出 10 个 AI / Agent / 开发工具相关（按今日新增 stars 降序）。其中 addyosmani/agent-skills、cloudflare/security-audit-skill、trycua/cua、manaflow-ai/cmux 为今日新上榜；blogwatcher 本轮新入库 1 条（EpicGames/raddebugger，非 AI，见文末）。

---

1. morluto/rea · TypeScript · 今日最热
项目简介：用 AI Agent 做逆向工程，从 App 行为一路逆到原生二进制；CLI + agent skills，集成 MCP、Ghidra、Hopper 等，主打 CTF 与二进制分析自动化。
为什么值得关注：连续两日榜首且增速还在加快（今日 +4,666），是 agent 落地到安全/逆向这类硬核场景的代表作，topics 里 agent-skills / mcp-server 都在。Stars：14,831（今日 +4,666）
https://github.com/morluto/rea

2. mattpocock/skills · Shell
项目简介：Matt Pocock 直接开源自己 .agents 目录里的一整套 agent 技能（"Skills for Real Engineers"）。
为什么值得关注：仍是热度最高的 agent-skills 仓库（279k stars），说明"给 coding agent 装技能"已是标准玩法，配置可直接抄。Stars：279,545（今日 +1,406）
https://github.com/mattpocock/skills

3. tester-army/e2e · TypeScript
项目简介：面向 Web 与移动 App 的下一代端到端测试框架，基于 Playwright。
为什么值得关注：测试是被 agent 改造最深的环节，e2e 自动化 + AI 断言持续升温，上线几个月增速稳定。Stars：7,399（今日 +1,391）
https://github.com/tester-army/e2e

4. cathrynlavery/diagram-design · HTML
项目简介：面向 Claude Code / Codex / Copilot / Factory Droid / Pi 的编辑级图表设计技能，42 种图类型，纯 HTML+SVG。
为什么值得关注：简介直接开嘲 "No Mermaid slop"，反映社区对 AI 生成图质量的更高要求；纯 HTML+SVG 无依赖好接。Stars：44,933（今日 +828）
https://github.com/cathrynlavery/diagram-design

5. addyosmani/agent-skills · JavaScript · 今日新上榜
项目简介：Addy Osmani（Google Chrome DevRel）出品的"生产级"AI coding agent 工程技能集，topics 覆盖 claude-code / codex / cursor / antigravity。
为什么值得关注：agent skills 赛道现在拼的是署名可信度，由知名工程师出面整理成体系，等于给这套玩法加了一层权威背书。Stars：102,780（今日 +693）
https://github.com/addyosmani/agent-skills

6. ayghri/i-have-adhd · Python
项目简介：一个 agent skill，强制 coding agent 别把答案埋起来，输出"ADHD 友好"（先给结论）。
为什么值得关注：轻量、直击 agent 啰嗦埋重点的通病，属于"一行解决一个真痛点"的典型 skill。Stars：55,085（今日 +620）
https://github.com/ayghri/i-have-adhd

7. cloudflare/security-audit-skill · JavaScript · 今日新上榜
项目简介：Cloudflare 官方出的 coding-agent 技能，做多阶段安全审计，产出可独立验证、机器可读的结论。
为什么值得关注：大厂（Cloudflare）亲自给 coding agent 发官方 skill，且强调"findings 可独立验证"——安全审计这种高风险场景愿意交给 agent，是个信号。Stars：26,025（今日 +617）
https://github.com/cloudflare/security-audit-skill

8. thedotmack/claude-mem · TypeScript
项目简介：给 agent 做跨会话持久记忆——捕获会话 → AI 压缩 → 未来会话注入相关上下文；兼容 Claude Code、OpenClaw、Codex、Gemini、Hermes、Copilot、OpenCode。
为什么值得关注：agent 长期记忆是最卷的赛道之一，且明确点名支持 Hermes，与我们直接相关。Stars：97,691（今日 +578）
https://github.com/thedotmack/claude-mem

9. trycua/cua · Rust · 今日新上榜
项目简介：计算机使用（computer-use）agent 的开源基础设施——跨 OS 驱动、容器化虚拟机舰队、以及用于训练/评测/数据生成的 benchmark。
为什么值得关注：computer-use 2.0 的"底座"型项目（topics 含 lume / apple / windows-sandbox），要做桌面自动化 agent 训练与评测值得先看它。Stars：28,727（今日 +229）
https://github.com/trycua/cua

10. manaflow-ai/cmux · Swift · 今日新上榜
项目简介：基于 Ghostty 的开源 macOS 终端，竖向标签 + 通知，专为并行跑 AI coding agent 设计（topics 含 parallel-agents / tmux / workspace-manager）。
为什么值得关注：Agent 并行的瓶颈已经从模型转到"人怎么同时盯住 5 个 agent"，这类 agent 原生终端正在成为工具链标配。Stars：27,827（今日 +96）
https://github.com/manaflow-ai/cmux

---

其他上榜（非 AI 方向，未收录）：boykopovar/AnyPS5（PS5 程序移植，今日 +2,725）、DuarteSantos8/openGym（自托管健身记录，+1,494）、EpicGames/raddebugger（原生图形调试器，C，+82；本轮 blogwatcher 唯一新入库项，属开发工具但不涉及 AI）。

一句话趋势：榜单头部仍是"给 coding agent 装技能"（skills 5 个）+ 逆向/安全/计算机使用这类硬核 agent 落地；今天的增量信号是大厂开始发官方 agent skill（Cloudflare）、以及 agent 并行调度工具（cmux）冒头。
