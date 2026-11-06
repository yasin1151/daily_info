
# GitHub Trending 今日热门（2026-11-07）

今日主榜共 17 个项目，AI / Agent 相关占近半。最明显的信号是「Agent Skills」类仓库集中冲榜：前五名里有三个是 skills 仓库（NVIDIA 的数据语义层、Cloudflare 的安全审计 skill、mattpocock 的工程 skills），另外两个是 Agent 编排器与语音模型。社区正在把「能力」从应用打包成可安装的 skill 分发。

---

## 一、今日最热（Top 5）

### 1. NVIDIA / auto-ontology — 给 Agent 用的企业语义层
- **简介**：从企业元数据自动生成本体（ontology），把「数据在哪、叫什么、能不能用、怎么用、从哪来」显式建模，再通过 MCP / CLI / API 暴露给任意 Agent harness。
- **为什么值得关注**：README 开篇的判断很直接——“更快算出来的营收数字如果是错的，一文不值”。它切的是 Agentic Analytics 的真正瓶颈：不是检索，而是口径不一致。与传统语义层是互补而非替代关系。
- **Stars**：8,968（今日 +2,005，Python，2026-04 建库）
- **链接**：https://github.com/NVIDIA/auto-ontology

### 2. Cloudflare / security-audit-skill — 把编码 Agent 变成安全审计员
- **简介**：六阶段流程：侦察 → 按覆盖账本分配 hunter → 候选漏洞验证 → 结构化输出 → 独立复核记录 → 报告中立化。附带 architecture.md 与 coverage-ledger.json 两个可审计产物。
- **为什么值得关注**：这就是 Cloudflare 官方博客里那套「漏洞发现 harness」的单仓库起点，从公司内部系统回流成公开 skill。安全审计是最适合多 Agent 隔离执行的场景，也是最能验证「skill 工程化」是否成立的场景。
- **Stars**：63,917（今日 +2,524，JavaScript，2026-06 建库）
- **链接**：https://github.com/cloudflare/security-audit-skill

### 3. mattpocock / skills — “给真工程师的 skills”
- **简介**：作者日常做正经工程（非 vibe coding）用的 skills 集合，主打小而可改、可组合、模型无关。
- **为什么值得关注**：README 里对 GSD / BMAD / Spec-Kit 的批评值得一读——它们接管了整个流程，代价是你失去控制权，流程本身出 bug 时极难排查。这个仓库走的是相反路线。316k stars 在 skills 类仓库里是异常值，说明「轻量可改」确实戳中了痛点。
- **Stars**：316,678（今日 +2,058，Shell，2026-02 建库）
- **链接**：https://github.com/mattpocock/skills

### 4. stablyai / orca — 并行调度一队编码 Agent
- **简介**：Claude Code、Codex 及任意 CLI Agent 各自跑在独立 worktree 里，聊天或终端两种模式随时切换且不丢上下文，本机或云端都能跑。
- **为什么值得关注**：定位是「AI Orchestrator」，大任务自动拆分给 worker agent 再汇总结果。相比同类，它把 diff、浏览器、CLI 收进一个 app，且支持自带订阅（不强制走平台额度）。
- **Stars**：117,822（今日 +1,199，TypeScript，2026-03 建库）
- **链接**：https://github.com/stablyai/orca

### 5. microsoft / VibeVoice — 开源前沿语音 AI
- **简介**：微软的语音模型家族，2026-09 发布 VibeVoice-ASR-Streaming（流式转写「谁说了什么」，支持热词与 10 种语言），07 月发布 BitNet 边缘 CPU 推理版，将模型从 4.62 GB 压到 1.58 GB。
- **为什么值得关注**：语音正在从「转文字」走向「带说话人、可流式、能在端侧跑」，这三个方向它同时覆盖了，且权重与 demo 都开放。
- **Stars**：56,458（今日 +1,001，Python）
- **链接**：https://github.com/microsoft/VibeVoice

---

## 二、Agent 生态（值得关注）

- **google/skills** — Google 官方 Agent Skills 合集，覆盖 Google Cloud、IAM 认证等，`npx skills add google/skills` 即可安装。大厂开始用 skill 作为产品分发渠道，而非只给文档。⭐22,816（+532）｜https://github.com/google/skills
- **stablyai 之外的第二个编排器：ParadevAI/Paradev** — Codex App / Conductor 的开源替代，每个任务独立 worktree + 分支 + 终端，支持 Claude Code、Codex、OpenCode、Gemini CLI、Cursor Agent 混跑。单 Agent 干不完的活，问题往往在并行度而不在模型。⭐16,031（+62）｜https://github.com/ParadevAI/Paradev
- **pipeshub-ai/pipeshub-ai** — 开源的企业上下文层：跨 Slack、Drive、Jira、Confluence、GitHub 等 50+ 应用的权限感知检索，带引用的答案，通过 MCP 同时服务人和 Agent。自称在 EnterpriseRAG-Bench 39 个系统中排第一，领先 OpenAI File Search、Amazon Q、Azure AI Search。⭐4,025（+76）｜https://github.com/pipeshub-ai/pipeshub-ai
- **lobehub/lobehub** — 从 AI 聊天客户端转型「团队里的超级 Agent」，强调主动性（它们自己找活干）与团队既有聊天工具集成。⭐84,234（+184）｜https://github.com/lobehub/lobehub
- **elder-plinius/T3MP3ST** — 多 Agent 攻击性安全框架，把你在跑的编码 Agent 变成 zero-day 猎手，recon → exploit → report 全自动，带浏览器 War Room。红队工具正在 Agent 化，值得留意其双刃属性。⭐6,945（+238）｜https://github.com/elder-plinius/T3MP3ST
- **southleft/figma-console-mcp** — 把设计系统变成 API，让 AI 直接读写调试 Figma。设计到代码的最后一公里。⭐3,180（+38）｜https://github.com/southleft/figma-console-mcp
- **meta/astryx** — Meta 开源的可定制设计系统，明确标注 agent ready。⭐14,048（+181）｜https://github.com/meta/astryx

---

## 三、开发工具 / 数据工程

- **zed-industries/zed** — 高性能多人协作编辑器，Atom / Tree-sitter 原班人马，AI 能力内建。⭐93,596（+292）｜https://github.com/zed-industries/zed
- **astral-sh/ruff** — Rust 写的 Python linter + formatter，速度仍是它最强的护城河。⭐50,683（+213）｜https://github.com/astral-sh/ruff
- **D4Vinci/Scrapling** — 从单请求到全站爬取的爬虫框架，自带 MCP server，是 Agent 取网页数据的基础设施，今日涨幅全榜第二。⭐98,823（+1,312）｜https://github.com/D4Vinci/Scrapling
- **NVIDIA/TensorRT-LLM** — LLM 推理优化栈，定义模型即得优化后的推理引擎。⭐15,030（+10）｜https://github.com/NVIDIA/TensorRT-LLM
- **mlflow/mlflow** — 定位已明确改为「AI engineering platform for agents, LLMs, and ML models」，做 tracing / eval / 部署。⭐28,701（+12）｜https://github.com/mlflow/mlflow
- **airbytehq/airbyte** — ELT 数据管道，新版描述已把自己包装成「给 AI agent 供数」的层。⭐22,329（+9）｜https://github.com/airbytehq/airbyte

---

## 四、非 AI 但上榜（一句话）

rails（+152）、react（+244）、angular（+128）、rust（+186）、symfony（+239）、prometheus（+140）、vscode（+295）、nushell（+177）、etcd（+123）、openssl（+24）、mpv（+36）。均为老牌项目常规波动，无重大版本事件。

---

## 五、今日三个观察

1. **Skill 成为新的分发单位**。三个 skills 仓库同时进前五，且分别代表厂商（Google）、安全团队（Cloudflare）、个人工程师（mattpocock）三种供给方。这意味着 Agent 能力的竞争，正在从「谁的模型强」转向「谁的 skill 生态好用、可审计」。
2. **编排层开始收敛成产品**。Orca（117k）与 Paradev（16k）解决同一个问题：一个人同时驱动多个 Agent，靠 worktree 隔离 + 统一视图。手搓终端标签页的阶段基本结束了。
3. **企业数据侧在补课**。NVIDIA 做本体、PipesHub 做上下文层、Airbyte 改文案强调供数给 Agent——三家从不同角度承认了同一件事：Agent 落地的瓶颈在数据语义与权限，不在推理能力。

---
已标记 11 条未读为已读。
