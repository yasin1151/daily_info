
**GitHub Trending 今日 AI 项目 · 2026-11-16**

今天趋势榜有一个清晰的主线：**围绕「Agent 能力」的周边设施正在快速成型**——技能库、技能评测、Agent 与前端交互协议，这些都在为「给 Agent 装手艺」铺路，而不是继续堆模型。

---

### 1. Google 出手做 Agent 技能库：stitch-skills
**google-labs-code/stitch-skills** · TypeScript · ⭐ 9,272（+248 today）

Google Labs 放出的 Agent Skills 技能包合集，专门配合 Stitch MCP server 使用，遵循 Agent Skills 开放标准，装进 Codex、Gemini CLI、Claude Code、Cursor、Antigravity 都能用。分三组插件：stitch-design（设计）、stitch-build（构建/组件）、stitch-utilities（工具），按需 sparse 安装，不用整包拉下来。

**为什么值得关注**：这是 Google 第一次以「官方出品」的方式进入技能市场。信号意义大于功能意义——如果连 Google 都在按 Anthropic 定的 Agent Skills 标准发技能包，说明围绕这个标准的生态竞争已经开始了。对日常用多个 coding agent 的人来说，它也能省去重复写 UI/设计类 prompt 的功夫。

🔗 https://github.com/google-labs-code/stitch-skills

---

### 2. NVIDIA 给「技能」做质检：SkillEvaluator
**NVIDIA/SkillEvaluator** · Python · ⭐ 1,640（+205 today）

一个评估 AI agent 技能质量的框架，属于 NVIDIA Verified Skills 流水线的组成部分。三层机制：先跑不花钱的静态质量检查（Tier 1，不需要 API key，直接 `skillevaluator validate ./my-skill --tiers 1`），再做语义重叠检测（防止两个技能干同一件事），最后生成合成评测数据集，做「有技能 vs 无技能」的对照实验，实测技能到底有没有改变 agent 的行为。能直接接进 GitHub/GitLab CI，每次 PR 自动检查改动的技能。

**为什么值得关注**：这是今天最值得关注的项目。整个行业都在不断生产技能包，但几乎没人回答「这个技能到底有用吗」这个问题。NVIDIA 用一个可测量的框架把「技能质量」变成了能进 CI、能阻止合并的工程指标。如果这套做法成为标准，以后发技能包可能要先通过质检。

🔗 https://github.com/NVIDIA/SkillEvaluator

---

### 3. 给 Claude Code 装一套网络安全技能包：Claude-BugHunter
**elementalsouls/Claude-BugHunter** · Python · ⭐ 6,390（+221 today）

面向漏洞挖掘和外网红队的 Claude Code 技能包：83 个技能、15 个 slash 命令、681 条已披露的漏洞报告模式（其中 433 条单独标注了出处、可审计），覆盖 24 类核心漏洞，外加 M365、Entra、Okta、vCenter、SSL-VPN、SharePoint、云 IAM 等企业身份与基础设施的攻击链。分四层：思考方法论（5 阶段非线性流程）、web 应用挖掘（58 个 hunt-* 技能）、外网边界突破、成果交付（分诊验证、VRT 严重性、脱敏、报告规范）。声称在 DVWA、Juice Shop、Hacker101 等靶场和授权红队项目里实战验证过。

**为什么值得关注**：这是「把资深红队人员的工作方法固化成技能」的典型样本，不是简单的 prompt 集合，而是一整套包含证据规范、报告模板和评分体系的作业标准。争议点在于审计性——681 条模式脱敏到 433 条可引用，剩下的部分来源不够透明。仅限授权测试使用。

🔗 https://github.com/elementalsouls/Claude-BugHunter

---

### 4. 量化推理的底层地基：ggml
**ggml-org/ggml** · C++ · ⭐ 15,896（+53 today）

老牌张量库重新进入趋势榜。纯 C/C++ 实现，不依赖任何库，2 到 8 bit 整数量化，另外支持 MXFP4/NVFP4 微缩放格式，运行时零内存分配，x86、ARM、RISC-V、LoongArch、PowerPC、s390x、WebAssembly 全平台，CPU/GPU/NPU/浏览器都能跑，SIMD 内核针对 x86、ARM、RISC-V 优化。也是 GGUF 格式的定义者。

**为什么值得关注**：它本身不算新闻，但 +53 的增幅出现在 AI 项目集体升温的背景下，说明关注点正在往推理基础设施转移。所有本地跑模型的工具（llama.cpp 等）都建在它上面，你今天用的任何端侧模型能力，都要经过这一层。

🔗 https://github.com/ggml-org/ggml

---

### 顺带值得一看（非新项目，但今日增长高）

| 项目 | 说明 | Stars |
|---|---|---|
| **GoogleChrome/modern-web-guidance-src** | 用最新 Web 最佳实践持续更新 coding agent 的知识，+1,220 今日最多 | 7,117 |
| **backnotprop/plannotator** | Agent 工作台：做计划、标注、审代码，一键把反馈推回 agent | 11,814（+860）|
| **ChromeDevTools/chrome-devtools-mcp** | 把 Chrome DevTools 交给 coding agent 用 | 56,889（+718）|
| **alibaba/open-code-review** | 阿里内部大规模实战的代码审查工具，确定性流水线 + LLM Agent 混合架构，精确到行级评论 | 52,032（+688）|
| **tradermonty/claude-trading-skills** | 给股票投资者的 Claude 技能：行情分析、技术图表、财报日历、选股 | 5,508（+707）|
| **Tencent/LoopForge** | 自建 coding-agent 交付流水线，编排 CodeBuddy/Codex/Claude Code，带人工审批关卡 | 1,450（+484）|
| **ag-ui-protocol/ag-ui** | Agent-User 交互协议，把 agent 接进前端应用 | 17,824（+393）|

---

**今日判断**：AI 项目占榜单约七成，但热度重心已经从「做一个更强的模型/agent」转向「怎么管理、评测、编排一堆 agent 和它们的技能」。SkillEvaluator 和 stitch-skills 同一天上榜不是巧合——技能生态正在长出它自己的质检和发行层。

已标记 4 条为已读。
