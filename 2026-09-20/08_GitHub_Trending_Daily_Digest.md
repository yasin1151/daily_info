
已扫描完成，本轮 6 条新增已全部标记已读。

---

# GitHub Trending 今日热门项目
**2026-09-20 · 趋势榜 15 个项目 · 本轮新增 6 条**

## 🔔 本轮新增（blogwatcher 首次发现）

**1. higgsfield-ai / higgsfield** ⭐ 4,936 · Jupyter Notebook · 今日 +314
一句话：跨多节点训练千亿~万亿参数模型的 GPU 编排 + 训练框架，口号是「multi node training without crying」。
简介：一个 GPU 资源调度器兼机器学习框架，干五件事——给用户分配独占/非独占节点、封装 PyTorch FSDP 与 DeepSpeed ZeRO-3 做万亿参数分片、提供训练全流程的启动与监控、用队列管理实验间的资源争抢、把训练 CI 挂到 GitHub Actions 上。写代码时只要 `@experiment("alpaca")` 装饰一个函数，里面用 `Llama70b(zero_stage=3, precision="bf16")` 建模型就能跑分布式训练。要求节点是 Ubuntu + SSH + 免密 sudo，官方实测 Azure / LambdaLabs / FluidStack，提供 pip 包（0.0.3）。
为什么值得关注：它针对的是分布式训练最脏的两块泥——环境地狱（PyTorch/CUDA/依赖版本漂移导致实验不可复现）和配置地狱（HuggingFace 那 600 个训练参数 + Hydra YAML 魔法）。路径是绕开 Slurm/K8s 那套重活，直接用 Git 仓库 + GitHub Actions 当训练编排层，「提交代码即触发训练、checkpoint 与实验 UI 都在 GitHub 里」。今天是趋势榜今日新增第一梯队里唯一的「训练侧」基础设施项目。（注：代码仓 2018 年就建了，2026-09 仍在推更新，属于老项目重新进榜。）
https://github.com/higgsfield-ai/higgsfield

**2. docling-project / docling** ⭐ 67,019 · Python · 今日 +94
一句话：把 PDF / DOCX / PPTX / XLSX / HTML 解析成给大模型吃的结构化 Markdown / JSON。
简介：原 IBM DS4SD 团队出品、现独立为 docling-project 的文档解析库（MIT，配套论文 arXiv:2408.09869）。覆盖 PDF 版面分析、表格还原、阅读顺序、公式与图片提取，输出 Markdown/JSON/HTML，带统一文档对象模型，可接 chunker 与向量库做 RAG 入库。生态上已有 CLI、LangChain/LlamaIndex 集成、Docling Serve（HTML API 服务）等一批下游仓库。
为什么值得关注：RAG 最容易被低估的一环就是解析质量——表格错位、跨页断行、扫描件丢字直接毒化检索结果。docling 是目前开源里解析保真度和工程成熟度最均衡的选择之一（6.7 万 star、4,833 fork），也是「文档 AI 预处理」这个赛道的事实基准。今日 +94 属于稳定长跑型热度，不是短期爆发——这类项目通常被真正在生产里用。
https://github.com/docling-project/docling

**3. yynxxxxx / Codex-X** ⭐ 3,385 · Rust · 今日 +59
一句话：给 OpenAI Codex 桌面端 / CLI 套一层可视化控制台，把提示词、Provider、会话、Skills/MCP、TOML 配置全搬进 GUI。
简介：Tauri 写的跨平台桌面工具（macOS Apple Silicon/Intel、Windows MSI/便携版、Linux，MIT）。核心功能：① 提示词注入管理，内置 5 套模板、联网后从 GitHub 再同步 6 套，可分类、可导入自己的 .md、每个模板独立开关，写入方式可选「追加保留原提示词」或「整体替换」，每次写入前自动备份；② 多 Provider / API 管理，官方登录与第三方供应商统一命名、一键复制切换，支持连通性检测、模型拉取测试、从 cc-switch 导入；③ 本地会话搜索/按项目分组/批量删除；④ Skills 与 MCP 可视化启停、ZIP 装 Skill、检查更新；⑤ config.toml 与 auth.json 集中查看，旁边有「开启 1M 上下文窗口」开关；⑥ Token 用量按日期/模型统计，能看每日趋势、缓存命中率，子代理用量归入主会话。
为什么值得关注：Codex CLI 现在一堆配置散落在 config.toml、auth.json、prompt 文件里，切 Provider、切提示词全靠手改文件——这是所有重度 Codex 用户共同的摩擦点，也是 community 工具最密集的缝隙市场。值得注意的是它的模板库里有「破甲/逆向」这种中文圈的越狱提示词分类，说明这类工具已经在做「绕过官方护栏」的分发，平台方后续会不会封这类写入点是变量。
https://github.com/yynxxxxx/Codex-X ｜ 官网 https://codex-x.site

**4. cloudflare / quiche** ⭐ 12,008 · Rust · 今日 +84
一句话：Cloudflare 的 QUIC 传输协议 + HTTP/3 实现（Rust，BSD-2）。
简介：IETF QUIC 与 HTTP/3 的成熟实现，提供处理 QUIC 包与连接状态的低层 API，含 C 语言 FFI 头文件，Cloudflare 自家网络在跑。
为什么值得关注：不是新项目，但 HTTP/3 已是新部署默认选项，quiche 是 Rust 侧最主流的两个实现之一（另一个是 quinn）。做边缘网关、自建 CDN、代理层的人绕不开。今日上榜更多是协议侧关注度回升的信号。
https://github.com/cloudflare/quiche

**5. ruanyf / weekly** ⭐ 103,110 · 今日 +151
一句话：阮一峰的《科技爱好者周刊》，每周五发布，已 10 万 star。
简介：每期一篇主文 + 一堆工具/资源/文摘/言论聚合，9127 个 open issues 实际是投稿与讨论区。
为什么值得关注：中文技术圈最稳定的信息源之一，今日 +151 是长期订阅型热度。想快速补中文技术圈共识和工具发现，性价比很高。
https://github.com/ruanyf/weekly

**6. ZuodaoTech / everyone-can-use-english** ⭐ 37,769 · TypeScript · 今日 +31
一句话：李笑来的《人人都能用英语》开源项目（GPL-3.0，配套 1000h.org）。
简介：把「用英语」的方法论做成了电子书 + Web 学习应用，TypeScript 实现。
为什么值得关注：与 AI 无关，属于中文社区长尾高 star 项目（3.7 万 star、5.2 千 fork），今日上榜是小幅波动。本周报 AI 相关度低，仅作记录。
https://github.com/ZuodaoTech/everyone-can-use-english

## 🔥 持续在榜（AI / Agent 方向，按今日新增 stars）

**cloudflare / security-audit-skill** ⭐ 16,260 · JS · 今日 **+3,162**（今日涨幅第一）
Cloudflare 出的编码 agent 技能：多阶段自动安全审计，产出可独立复核、机器可读的漏洞发现。大厂亲自下场做 agent skill 是明确信号——skill 正在成为新的分发格式。昨日 13.6k，一天涨约 2.7k。
https://github.com/cloudflare/security-audit-skill

**trycua / cua** ⭐ 24,374 · HTML · 今日 +1,124
「computer-use 2.0」：开源驱动 + 跨操作系统机群 + 基准测试，用于训练、评测 agent 的电脑操作能力并生成数据。方向是给 computer-use agent 做基础设施而非再做一个 agent。
https://github.com/trycua/cua

**addyosmani / agent-skills** ⭐ 97,000 · JS · 今日 +547
Google 的 Addy Osmani 出的「生产级 AI 编码 agent 技能库」，覆盖 Claude Code / Codex / Cursor / Antigravity。工程老兵沉淀的 skill 集合，是当前被引用最多的 skill 库之一（昨日 96.4k）。
https://github.com/addyosmani/agent-skills

**anthropics / claude-code** ⭐ 146,693 · TS · 今日 +482
终端 agentic 编码工具，仍是该品类基准线。
https://github.com/anthropics/claude-code

**Open-Dev-Society / OpenStock** ⭐ 16,011 · TS · 今日 +477
开源替代付费行情平台：实时价格、个性化提醒、公司洞察，永久免费。属于「AI 时代用开源重做垂直 SaaS」的代表样本（今日榜单里少数非 AI 原生的项目）。
https://github.com/Open-Dev-Society/OpenStock

**asciimoo / hister** ⭐ 5,218 · Go · 今日 +430
自建个人搜索引擎：索引浏览器历史，带 MCP server，主打隐私本地化，是给 agent 提供「个人记忆检索」的候选方案。
https://github.com/asciimoo/hister

**coder / coder** ⭐ 15,606 · Go · 今日 +406
给开发者和他们的 agent 提供安全可控的远程开发环境（Terraform 驱动）。当 agent 自己写代码跑命令，「人与 agent 共用沙箱」成了刚需。
https://github.com/coder/coder

**anthropics / knowledge-work-plugins** ⭐ 25,114 · Python · 今日 +280
Anthropic 官方知识工作者插件库（面向 Claude Cowork），官方插件生态起点，值得盯它的插件规范。
https://github.com/anthropics/knowledge-work-plugins

**cactus-compute / needle** ⭐ 11,591 · Python · 今日 +207
面向微型设备的自动化基础模型：2-bit 量化、8–29 MB，支持工具调用、结构化抽取与嵌入，可跑在手机、可穿戴、智能家居、机器人、汽车与单片机上。端侧小模型赛道里少见的「极致体积 + 真实功能」组合。
https://github.com/cactus-compute/needle

## 今日观察

新增的 6 条里只有 3 条与 AI 直接相关，且都不是新项目（higgsfield 是 2018 年的旧仓回榜、docling 是 2024 年的成熟库），说明今天趋势榜的「新鲜度」偏低，是新项目供给的间歇期。值得看的两个方向：**训练侧基础设施回温**（higgsfield 用 GitHub Actions 当训练编排层，绕开 Slurm/K8s 的路线）、**Codex 生态的社区外挂开始出现**（Codex-X 把 config.toml/auth.json 这类文件配置做成 GUI，并顺带分发越狱提示词）。持续在榜部分仍然被 agent skill 与 computer-use 基础设施占据，Cloudflare 的 security-audit-skill 单日 +3,162 稳居第一。

（本轮 6 条新条目已标记已读，GitHub Trending 当前无未读）

> 运维提示（与本推送无关但需处理）：「GitHub 每日产出入库」任务昨日失败，GITHUB_TOKEN 已失效（HTTP 401 Bad credentials），需到 https://github.com/settings/tokens 生成新 classic PAT（repo scope）写入 `~/.hermes/profiles/info/.env`，重跑任务会自动补推积压提交。
