
**GitHub Trending 每日热门 · 2026-09-23**

今天 Trending 榜单 8 个项目里 7 个与 AI/Agent 直接相关，"Agent 基础设施"（编排 + 沙箱）成了绝对主线。以下按今日新增 Stars 排序。

---

**1. google/ax —— Google 的声明式 Agent 编排运行时**
今日 +2,324 ⭐（总 7,539）｜Go｜https://github.com/google/ax

Google 开源的"Agent 编排器"，用 YAML 声明任务，`ax apply -f task.yaml` 就跑起来，用法刻意做得像 Kubernetes。四个原语：Task（带 CPU/内存限额的隔离沙箱）、Workspace（预接 Git 仓库 / MCP server / skill 包，agent 一启动就是热的）、Gateway（出网流量锁到显式主机白名单）、Model（平台自己用哪个 LLM，凭据来自 K8s secret）。还能 `ax ssh` 进沙箱看 agent 在干什么、`ax suspend/resume` 暂停空闲 agent 再原地续跑。底层跑在 Agent Substrate 上，目标是单集群跑十亿级任务。
值得关注：它把 agent 明确定义成"既不是无状态微服务、也不是跑完即止批处理"的新一类负载，并给出了官方抽象。目前 v1alpha1，官方明说会有破坏性变更，现在是读设计而不是上生产。

**2. anthropics/financial-services —— Anthropic 官方金融行业 Agent 模板集**
今日 +436 ⭐（总 36,307）｜Python｜https://github.com/anthropics/financial-services

"Claude for Financial Services"：投行、股票研究、私募、财富管理四个方向的参考 agent、skill 和数据连接器。已具名成体系的有 Pitch Agent（comps/precedents/LBO 一路做到品牌化 pitch deck）、Market Researcher、Earnings Reviewer、Model Builder（DCF/LBO/三表/comps，直接在 Excel 里跑）、GL Reconciler、Month-End Closer、KYC Screener 等。一份源码两种交付：装成 Claude Cowork 插件，或通过 Claude Managed Agents API 部署在你自己的流程引擎后面。
值得关注：这是 Anthropic 官方示范"垂直行业 agent 该长什么样"，同时 README 里写得很直白——不作投资建议、不下单、不过账，所有产出都停在人工签字前。这条边界声明本身比代码更值得读。

**3. agent-substrate/substrate —— 高密度 Agent 沙箱运行时**
今日 +301 ⭐（总 2,952）｜Go｜Apache 2.0｜https://github.com/agent-substrate/substrate

Google 开源的 agent 专用执行底座（注明非官方支持产品）。核心是把大量"大多数时间在闲置"的 actor 多路复用到少量 worker 上：比标准容器运行时密度高 10 倍，resume 低于 500ms，每秒 500+ 次 suspend/resume，原生零信任内核与网络隔离，同时支持 microVM 和 gVisor 两种沙箱。官方 demo 是 250 个有状态 actor 挤在 8 个物理 Pod 上跑。
值得关注：它明确说自己"不是构建 agent 的 SDK，而是让 agent 规模跑起来的系统"，且框架无关——ADK、LangChain、Claude Code、Codex、MCP server 都能作为 actor 托管，文件和内存状态跨挂起周期完整保留。与 google/ax 是同一套技术栈的上下层，建议一起看。

**4. dream-num/univer —— 给 AI Agent 用的开源 Office 套件**
今日 +202 ⭐（总 15,364）｜TypeScript｜https://github.com/dream-num/univer

定位从"开源表格"升级为 "The Office Harness for AI Agents"：表格、文档、演示、关系表、看板、PDF（即将支持）共用一个运行时。Canvas 渲染 + 独立公式引擎 + 插件架构 + 一套 Facade API，浏览器和 Node.js 上同一套代码，既能嵌进 SaaS/BI 也能在服务端跑文档处理。
值得关注：它明确把"人和 agent 在同一个文件里协作"当设计目标，配套已有 Univer CLI（命令行让 agent 创建/检查/交付 Office 内容）、DeepSeek Harness 插件、OpenClaw 插件、Univer Workspace（含 agent 改动的评审流程）。国产团队项目，想给 agent 补"办公文档能力"的可以直接看这里。

**5. superdesigndev/treg —— OpenRouter，但对象是工具**
今日 +197 ⭐（总 2,199）｜Python｜https://github.com/superdesigndev/treg

一个 base URL、一个 token，就能让 agent 调用 60+ 家厂商的 3,000+ 个接口：SEO/外链、社交与趋势、人物与公司画像、广告、抓取、图片和视频生成，按次计费、低至一分钱起，不用逐个注册供应商账号（README 点名 Semrush $139/月、Moz $99、Crunchbase $99、Apollo $59/座）。也支持把团队自己的付费账号、OAuth、厂商 CLI、SKILL.md 注册进去，自有 key 优先且不计费。可自托管。
值得关注："Ask for the task, not the tool" 这个方向切中 agent 的真实痛点——工具散落在注册墙和订阅制后面。注意项目很新（2026-07 创建），团队 2 周内已涨到 2.2k stars，热度高但成熟度待观察。

**6. browser-use/video-use —— 让编码 agent 直接剪视频**
今日 +155 ⭐（总 25,817）｜Python｜https://github.com/browser-use/video-use

把原始素材丢进文件夹，跟 Claude Code（或 Codex / Hermes / OpenClaw）说"剪成一条发布视频"，拿回 `final.mp4`。自动删口癖（umm/uh/口误）和废镜头、逐段自动调色、每个切点加 30ms 音频淡入淡出防爆音、按你风格烧字幕、用 HyperFrames/Remotion/Manim/PIL 并发生成动画叠层（每个动画一个子代理）、渲染后在每个切点自评通过才给你看，会话记忆写进 project.md 下次接着做。所有产物落在 `/edit/`，不污染 skill 目录。
值得关注：browser-use 团队做的又一个"skill + 一堆 ffmpeg 脚本"形态的 agent 应用，README 直接给了一段可粘给任意 agent 的安装提示词。这是当前 agent 应用最务实的落地范式，值得抄作业。

**7. davila7/claude-code-templates —— Claude Code 配置模板集市**
今日 +113 ⭐（总 31,103）｜Python｜https://github.com/davila7/claude-code-templates

Anthropic Claude Code 的现成配置集合：100+ agents、自定义命令、settings、hooks、MCP 集成和项目模板，一行 `npx claude-code-templates@latest` 就能装整套开发栈，网站 aitmpl.com 可交互浏览。走 npm 分发。
值得关注：它相当于 Claude Code 生态的"包管理器 + 新手村"，也是外部模板正在形成规模化的信号。没有突破性技术，但实用价值高，适合快速搭出自己的常用组合。

**8. mvt-project/mvt（非 AI）**
今日 +441 ⭐（总 14,078）｜Python｜https://github.com/mvt-project/mvt
Amnesty International 安全实验室的移动端取证工具（源自 Pegasus 项目），今日冲榜是因为刚合并 v3 分支，带来破坏性变更，依赖其输出的脚本需要跟着改。做 iOS/Android 设备入侵痕迹排查的可以关注。

---

**一句话总结**：今天的信号很集中——Google 用 `ax`+`substrate` 把 agent 当"新一类工作负载"正面回答基础设施问题，Anthropic 用官方 FSI 模板回答"垂直行业 agent 长什么样"，而 `treg`、`video-use`、`univer` 代表社区在工具供给、skill 化应用、办公文档三个方向各自找路子。已标记 4 条新条目为已读。
