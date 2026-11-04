
GitHub Trending 今日热门 AI 项目 · 2026-11-05

今日榜单 16 个项目，新增 7 个（其中 5 个属 AI/Agent 方向）。以下为详细版，另附仍在榜的高热度 AI 项目。

## 今日新上榜

**1. NVIDIA/auto-ontology — 给 Agent 和企业数据之间加一层“语义理解”**
NVIDIA 开源的 Python 库，从企业元数据自动生成本体（ontology），把散落在各系统里的指标定义对齐，再通过 MCP、CLI、API 暴露给任意 Agent 框架。它解决的问题很实在：Agent 查数据库不难以查不到，难的是查出来的数字含义是错的；README 的原话是，“一个更快返回但算错的营收指标毫无价值”。它负责告诉 Agent 数据在哪、是什么意思、该不该用、怎么用、来源是什么，以及哪些数据相似。
为什么值得关注：这是大厂在“Agent 数据底座”上的正面入场，直接对标各家 semantic layer 和数据目录产品，而且采用 MCP 原生设计，说明 MCP 已成为 Agent 接入企业数据的默认方式。新仓库第 1 天就上涨 2000+ 星，说明这个痛点是公认的。
Stars：4,868（今日 +2,053，全榜第一）
https://github.com/NVIDIA/auto-ontology

**2. The-PR-Agent/pr-agent — 老牌 AI 代码审查工具换了新组织**
开源 PR-Agent 的仓库迁移到了 The-PR-Agent 组织下，README 现在有一句话很值得注意：“这是原始开源 PR 审查器，不是 Qodo 的开源免费版”。母项目 Qodo 另有功能更全的商业产品，这个仓库被定位为“社区维护的 legacy 项目”，靠赞助继续开发，支持 GitHub、GitLab、Bitbucket、Azure DevOps。
为什么值得关注：这不是新项目，而是一次归属和定位的重申。对正在用它的团队，意味着自托管路线仍然可行，但官方支持重心已经转移，长期要看社区能不能接下维护责任。选型时需要把“停止更新”的风险算进去。
Stars：14,729（今日 +279）
https://github.com/The-PR-Agent/pr-agent

**3. FareedKhan-dev/kimi-k3-in-c — 2.78 万亿参数模型跑在单核 CPU、8.24GB 内存里**
用纯 C99 重写的 Kimi K3 推理引擎，无 BLAS、无框架、无 GPU。根据仓库标签，它靠三件事实现：MoE 稀疏激活（每次只走少数专家）、MXFP4 4-bit 量化、线性注意力，再加上 SIMD 和按需加载权重，零依赖。
为什么值得关注：这是极限系统编程的教学样本，不是可用的推理方案：2.78T 参数要过 8GB 内存，代价必然是巨量的磁盘 IO，速度会慢到无法交互。但它是理解“大模型如何在极小内存里运行”的最佳实物教材，适合想搞清量化、MoE、线性注意力如何彼此配合的人读代码。
Stars：10,268（今日 +351）
https://github.com/FareedKhan-dev/kimi-k3-in-c

**4. Thysrael/Horizon — 自建 AI 新闻雷达，中英双语日报**
收集 RSS、论坛、时间线内容，做去重、打分、排序，生成带“为什么重要”和社区讨论的中英双语简报。亮点是 profile 机制：不同内容类型用不同评分标准和输出方式——新闻类回答“为什么重要”，工程长文回答“我能用什么”。支持飞书、邮件、微信推送，有 live demo。
为什么值得关注：和我们的信息流工作流高度同构，它的“按内容类型分评分标准”比单一排序分更合理，值得借鉴到自定义筛选规则上。中文作者，文档有简中、日文版。
Stars：12,465（今日 +121）
https://github.com/Thysrael/Horizon

**5. scenario-labs/skills — 让 Agent 直接产出图片、视频、3D 资产**
面向 Claude Code、Cursor、Codex、Copilot 等 70+ Agent 的 Skills 集合，通过 Scenario MCP server 生成图像、视频、音频、材质、天空盒、3D 资产和定制训练模型。卖点是“会挑对模型、先报价再花钱、保持角色和品牌一致性”，直指生成式素材最大的两个问题：一致性差和费用不透明。
为什么值得关注：Skills 生态正在从“写代码”扩到“做内容”。底层还带一批驱动 ZBrush、Blender、Maya、UE、Unity、Godot 的专家技能，从教程和官方文档蒸馏而来，这是把 DCC 软件操作知识结构化的尝试。
Stars：2,404（今日 +224）
https://github.com/scenario-labs/skills

## 其他仍在榜的 AI 项目（今日新增星数）

| 项目 | 说明 | Stars | 今日 |
|---|---|---|---|
| vercel-labs/agent-desktop | Agent 的 computer use CLI（Rust） | 14,981 | +2,463 |
| D4Vinci/Scrapling | 自适应网页抓取框架，单请求到全站爬取 | 96,470 | +2,006 |
| mattpocock/skills | 作者 .agents 目录直出的工程师技能集 | 313,261 | +1,376 |
| thedotmack/claude-mem | 跨会话持久记忆，压缩后按需注入上下文 | 112,810 | +1,165 |
| github/spec-kit | 规格驱动开发（SDD）起步工具包 | 147,273 | +810 |
| harry0703/MoneyPrinterTurbo | 关键词一键生成高清短视频 | 138,915 | +615 |
| max-sixty/worktrunk | Git worktree 管理 CLI，为并行 Agent 设计 | 11,003 | +524 |

## 一句话观察

今日榜单前五名里四个和 Agent 基础设施有关：数据语义层（NVIDIA）、记忆、worktree 隔离、computer use。竞争重心已经从“谁的模型强”转到“谁的 Agent 周边更可靠”。另有两个非 AI 项目进了榜（DiscImageStudio 光盘盘面刻录、90DaysOfDevOps 学习路线），未展开。

已标记 7 条为已读。
