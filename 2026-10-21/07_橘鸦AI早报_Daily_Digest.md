
**橘鸦AI早报 · 2026-10-20**

本期 26 条，按栏目筛选出 9 条值得看的。

---

**1. MiniMax 正式发布 M3.1 Flash，匿名模型 Space Bunny 身份确认**
此前在匿名状态下处理了 200 万亿 token 的 "Space Bunny" 就是它的早期版本。官方称 Agent、编程、Computer Use 和网络安全能力全面提升，线上推理速度提升近 3 倍，Agent 类任务综合成本较前代降 70%。定价：输入 1 元 / 输出 4 元 / 缓存读取 0.1 元每百万 token。已上线 MiniMax API、M Plan、MiniMax Code，权重 10 月 23 日开放，Pro 版稍后。
影响：这个价格 + 3 倍速度直接压到 DeepSeek 的价格区间，Agent 场景的成本曲线又被拉低一截。
https://www.minimax.cn/blog/minimax-m31f

**2. 美国国土安全部下令联邦文职机构移除全部 DeepSeek 产品**
依据《2018 年联邦采购供应链安全法》，联邦文职机构不得采购深度求索及其关联实体的 IT 产品和服务，并须从系统中移除所有 DeepSeek 产品——**基于 DeepSeek 开发的第三方产品也在移除之列**。此前商务部、海军及纽约、田纳西、弗吉尼亚等州已先行禁用。
影响：这条的杀伤面在"下游"——任何嵌了 DeepSeek 的第三方软件都要一起清，出海企业的合规清单要重排。
https://public-inspection.federalregister.gov/2026-21447.pdf

**3. Meta 开源 Muse Glimmer 30B：面向消费级硬件的 Agent 模型**
30B 参数，Apache 2.0，可在单张消费级 GPU 的 Mac 或 PC 上以约 4 位精度本地跑起来，支持文本+图像输入，集成了多步推理、工具调用和失败恢复。Meta 称其在工具使用、多步规划、Agent 任务完成上领先 Gemma4-31B、Qwen3.6-27B 等同规模开放模型。
影响：本地 Agent 的可用门槛从"服务器"降到"一台带显卡的笔记本"，端侧自动化方案开始有实际选择。
https://ai.meta.com/research/publications/muse-glimmer-30b-an-on-device-agentic-model/

**4. 蚂蚁百灵开源 5 款 Ming-3.0 语音模型**
覆盖 TTS、音频理解、ASR 三条线：最小 0.5B 的语音生成；音频理解主力 Flash 总参数 126B、每步只激活 6.5B，支持长录音分析、语音问答、音乐与环境声理解，还能生成供 App 执行的工具请求；ASR Tiny 8.6B/2B 激活，支持方言口音和热词识别，无需额外训练。Flash 采用 MIT 协议，提供 vLLM-Omni 和 SGLang 部署方案。
影响：语音这条栈（听、说、识别）一次性开源齐了，中文方言场景是明显差异化。
https://github.com/inclusionAI/Ming-3.0-audio-flash

**5. Inception 发布扩散语言模型 Mercury 3**
官方称多项基准超过 GPT-6 Luna 和 Claude Haiku 5.5，速度是二者 4–8 倍，NVIDIA GPU 上每秒输出 1068 token。规模是 Mercury 1 的 40 倍，上下文从 26 万扩到 100 万，支持工具调用和结构化输出。价格 0.20/0.70 美元每百万 token，发布期半价，新用户 1 亿免费 token。
影响：扩散式 LLM 第一次在"速度"和"够用质量"上同时站住，适合做高频低延迟的批处理层。
https://www.inceptionlabs.ai/blog/introducing-mercury-3

**6. vLLM 团队推出 Decision 3.0：不生成文本的决策模型**
0.6B 到 27B 六种规模，接受文本/JSON/图像/视频输入，只返回选择、是非判断、评分及选项概率。27B 在 Jev Decision Index 文本榜和视觉榜均第一（66.3 / 71.3）。在单张 AMD MI325X、64 并发的混合负载下，经 vLLM 服务的吞吐是其自带服务器的 1.8 倍。部署配方已并入 vLLM Recipes。
影响：把"路由/分类/打分"从大模型里拆出来做小模型，是降本最直接的一刀，Semantic Router 场景值得试。
https://huggingface.co/collections/vllm-sr/decision-30

**7. Notion AI 升级：Auto 自动选模省 90% 成本，Agent 可连续跑 24 小时**
官方称在 20 多种常见用例中 Auto 效果接近 Opus 5.5 和 Astra，平均成本低约 90%。可把 ChatGPT Plus/Pro/Go 订阅接入个人 Notion Agent。新积分体系：Business/Enterprise 每席位每月 1500 点 Standard + 500 点 Select，现有客户 11 月 2 日迁移。Notion MCP 已支持记忆同步。
影响：SaaS 产品开始把"自带订阅"当卖点，模型层的话语权正被应用层拿走一部分。
https://www.notion.com/blog/notion-ai-more-for-less

**8. 微软 Project Perception 扩展：动态管控企业内部 Agent**
原本防外部 AI 攻击的系统，现在延伸到内部 Agent 的风险管控。汇集身份、数据、云、端点、网络、运行时信号来发现 Agent 并分配身份与权限，本地 Agent 发现支持从 25 种增至 60 种。引入动态权限、动态 Agent 风险、面向 Agent 的条件访问——按任务限定权限，风险升高时限制读写、要求人工批准或直接隔离运行时。
影响："Agent 是新的内部威胁"成了大厂正式假设，企业上 Agent 的审批流程会跟着变严。
https://blogs.microsoft.com/blog/2026/10/19/securing-the-agentic-insider/

**9. OpenAI：低资源语言编程能力大幅提升（COBOL 迁移准确率 97.9%）**
在官方 MultiLangBench 上，用 20 种语言从零构建兼容 SQLite 的数据库引擎，GPT-6 Astra 最高推理强度下平均通过率 87.4%，GPT-5.6 Sol 仅 26.8%。COBOL 保行为迁移评测中，GPT-6.1 Sol 低推理强度即达 86.6%（前代 5.4%），成本低 39%；提高推理强度后到 97.9%。
影响：银行、保险那些跑了几十年的 COBOL 系统，第一次有了经济上算得过账的迁移路径——这是真金白银的 To B 市场。
https://openai.com/index/low-resource-programming-languages/

---

**快速带过（低价值/重复，不展开）**：OpenCode、Qoder（10/24 前免费）、Command Code 均已上 DeepSeek V4.1-Flash-1017 或 MiniMax M3.1 Flash，属常规接入；TRAE 1024 抽奖、腾讯 WorkBuddy 教师版、Grok Bot 实体键、ChatGPT 桌面端可编辑历史消息均为小功能更新。行业侧：Meta Prometheus 吉瓦集群一期完工（数十万 GPU，目标百万），豆包公关否认"一半算力造爽剧"（称字节仅约 10% 用于视频模型），火山引擎 AI 剧单部最高 20 万元激励。

已标记该期为已读。
