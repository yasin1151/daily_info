
**GitHub Trending 每日热门 · 2026-09-24**

今天榜单 17 个项目里 14 个与 AI/Agent 相关，主线依然是「Agent 基础设施」，但新增量信号很清楚：一边是给 agent 补**上下文与记忆**（代码知识图谱、成品 harness），一边是把多 agent 编排**落到具体场景**（投研、3D 重建）。4 个新上榜项目按下面顺序详述，其余为回归条目。

---

## 新上榜（今日 4 条）

**1. strands-agents/harness-sdk —— 云厂商版「成品 Agent + 可下钻 SDK」**
今日 +96 ⭐（总 7,828）｜Python + TypeScript｜Apache 2.0｜https://github.com/strands-agents/harness-sdk

Strands Agents 把仓库整合成单体：新增的 **harness 层**让一行 `create_harness()` / `createHarness()` 就返回一个默认配好的 agent（模型、工具、记忆、会话、上下文管理都调过），想自己掌控循环再往下降级用底层 SDK。Python 和 TypeScript 同构，模型无关（Bedrock / Anthropic / OpenAI / Gemini / Ollama 等），MCP、多 agent 模式、结构化输出、guardrails、流式、tracing、evals 全都内置，另带 `strands` CLI 可在终端里直接原型化。
值得关注：卖点是「跑在你自己的进程里，没有托管控制面」，同时给一套经过 benchmark 的默认值——这和 LangChain 的 deepagents、OpenAI Agents SDK 的思路正在收敛：**不再只卖原语，而是先给你一个能直接上生产的 harness**。双语言同构是它区别于 Python-only 竞品的地方。

**2. DeusData/codebase-memory-mcp —— 纯 C 写的代码知识图谱 MCP Server**
今日 +266 ⭐（总 44,550）｜C｜MIT｜https://github.com/DeusData/codebase-memory-mcp

用 tree-sitter 解析 162 种语言、对 10 种语言额外加 Hybrid LSP 语义类型解析，把整个代码库索引成持久知识图谱（函数、类、调用链、HTTP 路由、跨服务链接），暴露 17 个 MCP 工具：搜索、调用追踪、架构总览、影响面分析、Cypher 查询、死代码检测、ADR 管理。单静态二进制、零依赖、无 API key、无语言运行时，一条 `install` 自动识别并配置本机已装的编码 agent（宣称支持 45 个客户端）。数据：Linux 内核 28M LOC / 75K 文件 3 分钟索引完，结构查询亚毫秒；论文（arXiv:2603.27277）称 31 个真实仓库里答案质量 83%、比逐文件探索省 10 倍 token、少 2.1 倍工具调用；README 另举 5 个结构查询约 3,400 token vs 逐文件 412,000 token。自带 localhost:9749 的 3D 图谱可视化。
值得关注：它把「代码索引」从 IDE 插件变成了 agent 可直接调用的本地服务，纯 C + 零依赖意味着部署成本几乎为零。另外它的**信任工程**值得单独看：README 主动写明「这个程序会读你的代码并写你的 agent 配置文件」，逐版本提交 VirusTotal、开 OpenSSF Scorecard、SLSA 3。也坦白 Defender 会把它误报成 `Wacatac.B!ml`（已知误报家族，gh、llama.cpp、Godot 同款）。高权限本地二进制以后大概都得按这个标准交代自己。

**3. TNT-Likely/PanWatch（盯盘侠）—— 自托管 AI 盯盘助手**
今日 +142 ⭐（总 1,480）｜Python｜MIT｜https://github.com/TNT-Likely/PanWatch

国产项目：A股/港股/美股实时监控、多券商账户汇总、持仓管理、模拟盘净值曲线、技术指标共振（MACD/RSI/KDJ/MA/布林带）、条件组合价格提醒，外加盘前分析 / 盘中监测 / 盘后日报 / 新闻速递四个定时 agent。真正的卖点是把 **TradingAgents**（76k star 的多 Agent 投研框架）接进了持仓页——点一下图标触发「4 类分析师（技术/情绪/新闻/基本面）→ 看多看空辩论 → 风控审查 → PM 决策书」的 9-Agent 接力，3-5 分钟输出完整推理链，结论直推 Telegram / 企业微信 / 钉钉 / 飞书 / Bark。默认用 deepseek-chat，单次约 $0.05，README 明确写了月度预算可控。Docker 一键部署，支持 PWA。
值得关注：这是「多 agent 辩论框架产品化」的一个好样本——把学术原型包进有 UI、有推送、有成本账的产品里，并用国产模型把单次调用压到 5 分钱。不过投资建议类项目固有的准确性与合规风险仍在，README 没有做很强的免责声明，实际拿它下单前要自己掂量。

**4. harry7557558/spirula-studio —— 一个二进制跑完 3D Gaussian Splatting 全流程**
今日 +99 ⭐（总 723）｜C++｜GPLv3｜https://github.com/harry7557558/spirula-studio

严格说不是 agent 项目，属 3D 重建/CV 训练工具，但对做 3D 数据的团队价值很直接：照片/视频 → splat → 带纹理网格，全部在一个自包含二进制里完成，**不需要 Python/PyTorch，也不用单独装 COLMAP**。走 Vulkan 后端跨厂商跑在 NVIDIA / AMD / Intel / Apple GPU 上（打破 CUDA 垄断），量化训练让 8GB 显存能训 1000 万个 SH3 高斯；原生支持鱼眼与 360° 相机/等距柱状投影，无需预先去畸变。内置极速 SfM、AI 遮罩、视频抽帧、深度/法线、网格化、skybox。近期更新密集：9/10 加了从视频元数据 telemetry 恢复公制尺度的能力（治「重建结果过大过小或歪掉」的老毛病），9/3 接入 LoMa 特征匹配，8 月补上 macOS/Apple Silicon 和 13 种界面语言。
值得关注：Gaussian Splatting 的研究成果长期卡在「Python + CUDA + COLMAP 三部曲」的工程门槛前，这个项目把它压成双击即用的 GUI/CLI，且不再绑定 N 卡。数字孪生、房产/电商 3D、游戏资产扫描这类场景的入场成本明显下降。

---

## 榜单其余 AI 相关（回归条目，含昨日进度）

- **google/ax** +1,542 ⭐（总 9,009）｜Go｜连续第二天领涨。「声明式 agent 编排」：YAML 声明 Task/Workspace/Gateway/Model，`ax apply` 起任务、`ax ssh` 进沙箱调试、`ax suspend/resume` 原地续跑，底层跑在 substrate 上，目标单集群十亿级任务。仍是 v1alpha1，官方明说会有破坏性变更——现在读设计，别上生产。
- **dream-num/univer** +1,140 ⭐（总 16,309）｜TypeScript｜定位从「开源表格」变成「给 AI Agent 的 Office Harness」：表格、文档、演示、关系表、PDF 共用一个运行时，配 Univer CLI 让 agent 创建/检查/交付办公文档，还有 agent 改动的评审流程。国产团队。
- **browser-use/video-use** +745 ⭐（总 26,479）｜Python｜把素材丢进文件夹、跟编码 agent 说「剪成发布视频」就得到 `final.mp4`：删口癖和废镜头、逐段自动调色、每个切点 30ms 音频淡入淡出、按风格烧字幕、并发子代理生成动画叠层、渲染后每个切点自评通过才给你看，会话记忆写进 `project.md`。
- **anthropics/financial-services** +665 ⭐（总 36,920）｜Python｜Anthropic 官方金融行业 agent 模板集（投行 / 股票研究 / 私募 / 财富管理），一份源码两种交付（Cowork 插件或 Managed Agents API 部署）。README 里「不下单、不过账、结论停在人工签字前」的边界声明比代码更值得读。
- **agent-substrate/substrate** +560 ⭐（总 3,481）｜Go｜高密度 agent 沙箱运行时：actor 多路复用、resume <500ms、每秒 500+ 次 suspend/resume、microVM + gVisor 双沙箱，demo 是 250 个有状态 actor 挤在 8 个物理 Pod 上。
- **superdesigndev/treg** +502 ⭐（总 2,688）｜Python｜「工具版 OpenRouter」：一个 base URL / 一个 token 调 60+ 厂商 3,000+ 接口（SEO、社媒、公司画像、抓取、图/视频生成），按次计费，也支持接入团队自有 key 且不计费，可自托管。
- **obra/superpowers** +485 ⭐（总 **290,669**）｜Shell｜给编码 agent 的完整软件开发方法论：自动逼出 spec → 分块确认设计 → 出足够蠢的初级工程师也能执行的计划（强调真红绿 TDD、YAGNI、DRY）→ 子代理驱动逐任务实现与评审，可连续自主跑几小时。支持 20 个 harness，**包括 Hermes Agent**。这个 star 量说明 skill 化方法论已经被广泛接受。
- **davila7/claude-code-templates** +393 ⭐（总 31,484）｜Python｜Claude Code 的配置集市：100+ agents、命令、settings、hooks、MCP 集成，`npx claude-code-templates@latest` 一行装完，相当于这个生态的包管理器。
- **pbakaus/impeccable** +287 ⭐（总 70,316）｜JavaScript｜给 AI 编码 agent 补「设计品味」：1 个 skill + 24 条命令（polish/audit/critique/distill/animate/bolder/quieter…）+ 61 条确定性检测规则（CLI 与浏览器扩展本地跑，不用 LLM 不用 key）。它点名要治的病是：所有模型都在同一批 SaaS 模板上训过，于是每个项目都长出「Inter 字体 + 紫蓝渐变 + 卡片套卡片 + 标题上一个圆角方块图标」这套通病。
- **BuilderIO/agent-native** +135 ⭐（总 6,523）｜TypeScript｜构建「带 UI 的 agent 应用」的框架：一个 capability 定义成一个 action，agent 当工具调、UI 当代码调，共用同一套校验/权限/实现，数据与应用状态双向共享——agent 不去点 UI，而是走和 UI 相同的 action 层。
- **HKUDS/CLI-Anything** +41 ⭐（总 49,907）｜Python｜口号是「让所有软件 Agent 原生」，配 CLI-Hub 包管理器（`cli-hub install <name>`）做社区 CLI 的分发。
- **Open-Dev-Society/OpenStock** +379 ⭐（总 18,798）｜TypeScript｜非 agent 项目但今日冲榜：免费开源的股票行情/提醒/公司洞察平台（Next.js 15 + Finnhub + TradingView，AGPL-3.0），叙事是「知识不该被订阅墙锁住」。社区热情高，实际能力受限于数据源延迟。
- **mvt-project/mvt** +546 ⭐（总 14,472）｜Python｜非 AI。Amnesty 安全实验室的移动端取证工具，今日冲榜因 v3 分支合并带来破坏性变更。

---

**一句话总结**：硬件层（ax + substrate）继续领涨但仍是 alpha，今天的真正增量在两处——**给 agent 的上下文工程**（codebase-memory-mcp 用纯 C 把代码库变成亚毫秒可查的知识图谱，harness-sdk 直接交付调好默认值的成品 agent）和**垂直场景落地**（PanWatch 把 9-Agent 投研辩论做成 5 分钱一次的推送产品，Spirula 把 Gaussian Splatting 压成一个二进制）。skill 化方法论（superpowers 29 万 star）和设计规范（impeccable）这类「软约束」项目同时走高，说明生态竞争正从模型能力转向**工程规范与默认值**。

已标记 4 条新条目为已读（blogwatcher 已无未读）。
