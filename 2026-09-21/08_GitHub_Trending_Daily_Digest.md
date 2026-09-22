
**GitHub Trending 每日推送 · 2026-09-21**
榜单共 13 个项目，筛出 11 个 AI / Agent / LLM / 开发工具 / MLOps 相关（含 3 个 blogwatcher 新增条目，已标记已读）。

---

**1. cloudflare/security-audit-skill｜今日 +2,375 ★（今日榜首）｜总计 17,973 ★｜JavaScript**
给编码 Agent 装上"安全审计员"的技能包：把审计拆成六个阶段跑——侦察（画出架构和信任边界）→ 按覆盖面派"猎人"找漏洞 → 每个候选漏洞交给全新 Agent 去证伪 → 输出结构化 findings → 再由独立 Agent 复核来源 → 生成报告。核心是"写代码的和审代码的不能是同一个上下文"。
值得关注：Cloudflare 官方开源，是他们内部漏洞挖掘 harness 的起点版本，配套有一篇官方博客讲怎么自建漏洞 harness。判断结果分三档（confirmed / needs_validation / rejected），给漏洞定级时强制留证据链——这套"对抗式自查"结构正在成为 Agent 工程的通用做法。
https://github.com/cloudflare/security-audit-skill

**2. trycua/cua｜今日 +1,012 ★｜总计 25,122 ★｜Python/HTML**
"给 AI Agent 一台能用的电脑"。提供开源桌面自动化驱动、隔离的云端桌面（Fleets，可批量开一堆机器给 Agent 用）、本地 macOS 虚拟机、专门做 computer-use 决策的小模型（CUA-S1），以及评测 computer-use Agent 的基准。
值得关注：computer-use 这条线一直卡在"没有干净、可丢弃的运行环境"和"没有公认评测"，cua 想同时解决这两件事，且今天在推 Fleets 云桌面集群——Agent 从"单机玩具"走向"成批干活"的基建。
https://github.com/trycua/cua

**3. affaan-m/ECC｜今日 +837 ★｜总计 263,705 ★｜JavaScript**
给 Coding Agent 的"工程操作系统"。一句话概括它的流水线：plan → test → implement → review → verify → remember → improve。内含 68 个专用 Agent、292 个技能、94 个命令，加 hooks、规则、记忆系统和 AgentShield（扫 prompt/hooks/MCP 配置/权限/密钥等攻击面）。
值得关注：它解决的是真实痛点——计划淹没在聊天记录里、"请用 TDD"模型会忘、同一个上下文既写代码又审代码。ECC 把 TDD 做成有 RED→GREEN 证据的强流程，支持 Claude Code 为主，兼容 Codex、Cursor、Gemini、Copilot 等；Memory Vault 用一个本地 Markdown 格式在多个 harness 之间共享记忆（README 里点名支持 Hermes、OpenClaw、Kimi）。
https://github.com/affaan-m/ECC

**4. addyosmani/agent-skills｜今日 +729 ★｜总计 97,657 ★｜JavaScript**
Addy Osmani（Google Chrome 团队）开源的生产级工程技能集。9 个斜杠命令覆盖完整开发生命周期：`/spec` → `/plan` → `/build` → `/test` → `/constraints` → `/review` → `/webperf` → `/code-simplify` → `/ship`。`/build auto` 一次批准计划后自主跑完全部任务，但每个任务仍单独测试、单独提交，失败即停。
值得关注：把"资深工程师的质量闸门"固化成技能，而不是靠 prompt 提醒。知名工程师的规范集通常会被社区当事实标准抄一遍。
https://github.com/addyosmani/agent-skills

**5. vercel-labs/json-render｜今日 +332 ★｜总计 17,276 ★｜TypeScript（新增）**
Vercel Labs 的"生成式 UI"框架：AI 用自然语言生成界面，但只能从你定义好的组件目录里选，所以输出受护栏约束、可预测。一套核心包适配 React / Vue / Svelte / Solid / React Native / Remotion（视频）/ react-pdf / HTML 邮件 / Ink 终端 / Next.js / react-three-fiber 3D。
值得关注：生成式 UI 最大的坑是"AI 瞎写组件导致崩"，json-render 用封闭组件目录的解法绕开了自由发挥。Vercel 官方实验室出品，很可能影响下一波 AI 应用的前端写法。
https://github.com/vercel-labs/json-render

**6. higgsfield-ai/higgsfield｜今日 +461 ★｜总计 5,361 ★｜Python/Jupyter**
容错、可大规模扩展的 GPU 编排与机器学习框架，面向训练场景。
值得关注：今天 AI 基建里"GPU 编排"是硬需求，小团队做的容错编排方案值得看他们怎么做故障恢复。
https://github.com/higgsfield-ai/higgsfield

**7. anthropics/claude-code｜今日 +415 ★｜总计 147,100 ★｜TypeScript**
Anthropic 官方终端里的 Agent 编码工具，仍在日榜常驻。
https://github.com/anthropics/claude-code

**8. coder/coder｜今日 +382 ★｜总计 16,031 ★｜Go**
给开发者和他们的 Agent 提供安全、可复现的开发环境（远程开发环境平台）。
值得关注：Agent 要跑代码就必须有隔离环境，coder 的定位正从"给人类开发者"扩到"给 Agent 当工位"。
https://github.com/coder/coder

**9. anthropics/financial-services｜今日 +236 ★｜总计 35,349 ★｜Python**
Claude for Financial Services：面向投行、股票研究、私募、财富管理的参考 Agent、技能和数据连接器（Pitch Agent、Market Researcher、GL Reconciler 等）。同一份源码既能装成 Claude Cowork 插件，也能通过 Managed Agents API 部署。README 明确声明所有产出必须由持牌专业人士复核，不做投资建议、不执行交易。
值得关注：这是"垂直行业 Agent 打包"的模板示范——注意它的合规边界写得很硬，值得同类项目抄。
https://github.com/anthropics/financial-services

**10. mihail911/modern-software-dev-assignments｜今日 +174 ★｜总计 4,543 ★｜Python（新增）**
斯坦福 CS146S《现代软件工程》的课程作业集。
值得关注：课程把"现代软件开发"（含 AI 辅助工程）正式搬进课堂作业，是看学界怎么教这件事的现成教材。
https://github.com/mihail911/modern-software-dev-assignments

**11. BuilderIO/agent-native｜今日 +89 ★｜总计 5,185 ★｜TypeScript（新增）**
开源的 TypeScript Agent 应用框架。核心设计是"共享 action"：每个能力只定义一次，Agent 把它当工具调用，UI 从代码里调用，两条路径共用同一套校验和权限；数据和状态也双向共享，Agent 不用去"点 UI"，而是通过和 UI 相同的 action 层干活。
值得关注：它回答了"Agent 产品该长什么样"——不是给聊天框套壳，而是 Agent 和界面共用一层能力抽象。Builder.io 出品，MCP/A2A/HTTP/CLI 都能直接挂同一个 action。
https://github.com/BuilderIO/agent-native

---

**非 AI 补充（今日涨势很猛）**
- **Open-Dev-Society/OpenStock**｜+752 ★｜16,777 ★：开源版行情平台，可自托管，替代昂贵的付费行情终端。
- **paperless-ngx/paperless-ngx**｜+32 ★｜45,546 ★：老牌自托管文档扫描归档系统。

**今日观察**
1. 榜首不是模型而是"技能/流程"——security-audit-skill、agent-skills、ECC 三个都在做同一件事：把工程规范固化成 Agent 可执行、可验证的流程。今天 GitHub 上最热的东西已经从"Agent 能做什么"转向"怎么让 Agent 做得可靠"。
2. 环境与遥控成为瓶颈点：cua（云端桌面集群）、coder（隔离开发环境）同日上榜，说明"给 Agent 一台干净的机器"是当下最缺的基建。
3. Anthropic 一次性推两条线（claude-code 日榜常驻 + financial-services 垂直行业模板），垂直行业 Agent 的打包方式正在被官方示范。
