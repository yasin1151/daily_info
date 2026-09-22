
# GitHub Trending 今日热门推送（2026-09-11）

本次扫描发现 6 个新项目（已标记已读），并从今日 Trending 全榜中筛出 AI / Agent / LLM / 开发工具方向的重点条目。

## 一、本次新增（6 条）

**1. vercel-labs/skills —— 开放 Agent Skills 生态的官方 CLI**
简介：Vercel Labs 出的 Agent 技能包管理器，一条 `npx skills add vercel-labs/agent-skills` 就能给 Claude Code / Codex / Cursor / OpenCode 等 75+ 个 agent 装技能，也支持不安装直接生成 prompt 喂给 agent。
为什么值得关注：Skills 正在从各家私有格式走向跨 agent 的标准分发方式，这条如果成主流，会决定以后"技能"怎么写、怎么装、怎么复用。做 agent 工具链的人应该现在就跟。
Stars：31,124（今日 +175）｜https://github.com/vercel-labs/skills

**2. diegosouzapw/OmniRoute —— 免费 AI 网关，一个端点接入 352 家供应商**
简介：MIT 协议的免费聚合网关，单端点覆盖 352 家供应商（150+ 有免费额度）、1200+ 模型（Kimi、Claude、GPT、Gemini、GLM、DeepSeek、MiniMax），对 Claude Code / Codex / Cursor / Cline / Copilot 都兼容；带配额感知的自动降级、号称省 15–95% token 的压缩、MCP/A2A、桌面端与 PWA。
为什么值得关注：把"手动薅各家免费额度"这件事自动化了，README 里认真算了每月约 14.7 亿免费 token 的口径；对成本敏感的开发者是绕开 API 账单的现实方案，但也需要注意各家 ToS 与合规风险。
Stars：64,214（今日 +591）｜https://github.com/diegosouzapw/OmniRoute

**3. nashsu/llm_wiki —— 会自己长大的个人知识库**
简介：跨平台桌面应用，LLM 读你的文档后自动建成互相链接的 wiki，并持续维护更新。作者明确对比传统 RAG：不是每次问答都从零检索，而是增量构建一座持久化的知识库；支持 PDF/Office/EPUB/图片/网页多格式摄取，图片用视觉模型自动生成描述。
为什么值得关注：这是"RAG 之外的第二条路"的代表——把检索结果沉淀成资产而不是每次重算。已有 1.8 万 star，说明很多人对反复检索的低效确实不满。
Stars：18,076（今日 +94）｜https://github.com/nashsu/llm_wiki

**4. JustVugg/colibri —— 纯 C 写的 MoE 推理引擎，把消费级硬件榨到极限**
简介：无引擎依赖的纯 C 推理引擎，靠"AI 内存分层"把存储/RAM/VRAM 当成统一层级、专家从磁盘流式加载，号称能在自己已有的硬件上跑 744B 到 2.8T 参数的 MoE 模型。已支持 GLM-5.2/5.3（744B）、Kimi K3（2.8T）、DeepSeek V4 Flash（284B）、Qwen3.6（35B-A3B）、OLMoE 等八个模型家族。
为什么值得关注：大模型推理的瓶颈正从算力转向内存与 IO，这种"把 SSD 当显存用"的路线直接冲击"必须买卡才能跑大模型"的前提，是本地部署方向最值得跟踪的工程实验。
Stars：27,439（今日 +130）｜https://github.com/JustVugg/colibri

**5. alsk1992/CloddsBot —— 自主交易 AI Agent（预测市场 + 加密 + 期货）**
简介：基于 Claude 的开源 AI 交易终端，可在 1000+ 市场上自主运行：10 个预测市场、7 家期货交易所，通吃 Solana（Jupiter/Pump.fun/Raydium）与 5 条 EVM 链，自称内置 118+ 交易策略、巨鲸追踪、套利检测、跟单与 DCA；支持 21 种聊天平台操控，并带机器对机器支付的 agent 商务协议。
为什么值得关注：Claude 直接下场的"真金白银 agent"，还是黑客松 12 天赶出来的。金融场景是 agent 自主决策最有争议也最先落地的地方，围观价值高于实操价值——自托管也意味着风险自担。
Stars：1,618（今日 +299）｜https://github.com/alsk1992/CloddsBot

**6. armory3d/armorpaint —— 开源 3D PBR 纹理绘制工具（非 AI）**
简介：Armory3D 家族的 3D PBR 纹理绘制软件，仓库面向开发者，官方发行版付费以支撑项目，可直接编译 git 版本使用。
为什么值得关注：与 AI 无关，但属于长期缺位的"开源 Substance Painter 替代"。如果你做 3D/游戏资产管线，这是稳定可靠的老牌选项；单纯为追 AI 热点可略过。
Stars：4,401（今日 +87）｜https://github.com/armory3d/armorpaint

## 二、今日全榜里其他值得看的 AI 条目

- **obra/superpowers**（284,684 星，+731）Shell｜把"技能 + 开发方法论"打包给编码 agent 的框架，支持 Claude Code、Codex、Cursor、Gemini CLI、OpenCode、Pi，**且明确列了 Hermes Agent**，是同类里 star 数最高的一个。https://github.com/obra/superpowers
- **cathrynlavery/diagram-design**（37,705 星，+1,287）HTML｜39 种编辑级图表类型的 skill，直接给 Claude Code / Codex / Pi 生成自包含 HTML+SVG，作者的口号是"No Mermaid slop"，能反向重绘 draw.io / Mermaid / Excalidraw 源文件。https://github.com/cathrynlavery/diagram-design
- **ayghri/i-have-adhd**（38,193 星，+3,854，今日全榜第一）Python｜一个让编码 agent 别再绕圈子的 skill：结论先行、步骤编号、删掉"希望这有帮助"。增长最猛的一条，说明"agent 输出啰嗦"是普遍痛点。https://github.com/ayghri/i-have-adhd
- **THU-MAIC/OpenMAIC**（35,272 星，+806）TypeScript｜清华团队的多 Agent 互动课堂，v1.0 上了 Pro 工作台：用对话让 agent 规划课程、生成和改稿全部页面，带 20 个内置技能与 .pptx 导入，模型/媒体/搜索/存储都可自带。https://github.com/THU-MAIC/OpenMAIC
- **Tencent/teamai-cli**（3,755 星，+837）TypeScript｜腾讯出的团队级 AI 资源管理 CLI，把 skills、rules、MCP 和知识库跨 Claude Code、Codex、Cursor、CodeBuddy 等统一分发，`teamai init <repo>` 一条命令同步团队共享经验。https://github.com/Tencent/teamai-cli
- **AlexsJones/llmfit**（35,716 星，+247）Rust｜扫描你的 CPU/内存/GPU/显存，一条命令告出哪些开源 LLM 能在你这台机器上跑得起，新增"跑分并回传"机制，用真实 tok/s 替换估算值。选本地模型前值得先跑一遍。https://github.com/AlexsJones/llmfit
- **vastsa/PI-Desktop**（2,273 星，+636）TypeScript｜本地优先的 AI 编码 agent 桌面工作台（Electron + Rust 宿主核心），不做账号、不强制走中转、不锁定编辑器，目前 Early Preview。https://github.com/vastsa/PI-Desktop
- **freestylefly/awesome-gpt-image-2**（30,814 星，+957）JavaScript｜中文的 GPT Image 2/2.5 提示词与案例库，530+ 案例、20+ 工业级模板与可复用 Skills，主打"Prompt as Code"。https://github.com/freestylefly/awesome-gpt-image-2

**今日主线判断**：榜单已经被"Agent 周边"占满——技能分发（vercel-labs/skills、superpowers、teamai-cli）、输出质量控制（i-have-adhd、diagram-design）、成本与本地化（OmniRoute、colibri、llmfit）三条线同时爆发，而模型本身几乎没上榜。社区热度明显从"训模型"转向"怎么把模型用得省钱、顺手、可控"。
