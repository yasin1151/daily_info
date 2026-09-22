
**橘鸦AI早报 · 2026-09-09 摘要**（10 条）

**① OpenAI 宣称 AI 解出 Navier–Stokes 千禧年难题**
核心变化：内部系统用约 1 万个智能体协作 88 小时（270 万条消息、约 1300 亿输出 token）构造出三维不可压流体在光滑外力下有限时间内形成奇点的解，再由 GPT-6 Astra 花 17 小时完成 Lean 形式化验证。证明文稿与形式化证明均已公开，OpenAI 表示不申领千禧年大奖。
影响：首个 AI 主导攻克的千禧年难题级候选成果，"智能体集群+形式化验证"的科研范式落地；但结论需数学界独立审验。
链接：https://openai.com/index/navier-stokes-solution/

**② 同一成果引发署名与数据争议（值得关注）**
数学家 Tristan Buckmaster 发声明：OpenAI 获知他与 Alpöge（现任职 Anthropic）的流体方程进展后才开展研究，并提议由他单独署名介绍性论文、排除 Alpöge；他还追问两人上传 Codex 的草稿是否被用于训练。OpenAI 回应：研究确由传言触发，公开前未看过两人工作、未为解题访问特定用户数据，但"无法排除"去标识化产品数据曾帮助改进模型；Bubeck 为"毁掉职业生涯"措辞道歉。
影响：核心争议是 AI 公司科研是否使用了用户数据、以及学术署名伦理，讨论热度高。
链接：https://cims.nyu.edu/~tristanb/statement.pdf

**③ ChatGPT Images 2.5 发布**
核心变化：生成延迟较上代最高降 50%，光影纹理更自然，支持"只改指定部分"的多轮精准编辑；ChatGPT 新增 @Sketch 草图生图与评论编辑；API 推出 Flare（默认）/ Sunburst（高精度慢速）两款分层模型。所有 ChatGPT / Work / Codex 用户可用。
影响：图像模型从"生成"走向"可精确修改的生产工具"，API 快/精分层是明显的定价策略。
链接：https://openai.com/index/introducing-chatgpt-images-2-5/

**④ DeepSeek 两连发：V4.1 Flash 中间版开测 + flash 系列降价**
核心变化：(1) V4.1 Flash 中间版本测试开启，新模型结构、原生多模态、更快更便宜，base_url 不变，模型名改 `deepseek-v4.1-flash-expires-on-0910` 即可调用，计费同 V4 Flash，限 20 并发；(2) 今日（9/10）12:00 起 flash 调价：空闲时段缓存命中 0.02 元 / 未命中 1 元 / 输出 4 元，高峰时段为 2 倍；对比原价（0.05/1.5/4.5）降幅 60%/33%/11%。
影响：成本敏感用户今天起直接受益；V4.1 Flash 是下一代多模态路线的信号，官方问卷还在问能否全面替换 V4 Pro。
链接：https://platform.deepseek.com/usage

**⑤ Meta 正式上线个人 AI Agent「Muse」**
核心变化：由 Muse Spark 1.3 驱动，运行在用户专属云端虚拟机，可用完整浏览器、连第三方服务及 Instagram/Facebook，设定目标后在后台持续执行并主动发消息；配备 Sentinel 权限审批与人工确认，漏洞赏金最高 30 万美元。目前仅限美国 18 岁以上用户，Confidential VM（更强隐私隔离）年内推出。
影响：大厂"托管式个人 Agent"首个产品化形态，安全审批机制设计是行业参照。
链接：https://introducing.muse.ai/

**⑥ 小米 MiMo Desktop 桌面客户端开放邀测**
核心变化：面向真实工作场景的桌面 AI 应用，支持多格式输入、自动拆解任务调工具，可交付 PPT/网页/3D/App 等可继续编辑成果，带可交互预览与局部修改；邀测用户限时免费体验 MiMo-X-Pro/Flash-Preview。电脑操控仅海外版，暂不含欧盟、英国、韩国。
影响：国产桌面 Agent 客户端入局，与 Muse 形成"云端托管 vs 本地桌面"两条路线对照。
链接：https://mp.weixin.qq.com/s/TmLyeR6eo-5jNtCEHNDeig

**⑦ Mistral 完成 30 亿欧元 D 轮，估值超 210 亿欧元**
核心变化：三星电子领投，EQT Scaleup Europe Fund 与 PSG Equity 联合领投，a16z/ASML/NVIDIA/Salesforce Ventures 等跟投；官方称是欧洲科技公司迄今最大股权融资，距成立仅三年。资金用于前沿研究、算力扩充与国际扩张。
影响：欧洲"主权开源 AI"叙事得到资金背书；三星领投暗示端侧/移动 AI 合作想象空间。
链接：https://mistral.ai/news/mistral-makes-sovereign-open-weight-ai-to-frontier/

**⑧ Cognition 完成超 20 亿美元 E 轮，估值 480 亿美元**
核心变化：a16z、Accel 领投；run-rate 收入从 5 月的 4.92 亿美元增至近 9 亿美元；Devin 已用于 NVIDIA 芯片设计、Citi 金融、奔驰汽车等场景。公司自称"独立 Agent 实验室"，按任务组合最合适的模型（含自研），不绑定单一供应商。
影响：应用层 Agent 公司估值与收入双爆发，"模型无关"策略直接对标大厂自研路线。
链接：https://cognition.com/blog/series-e

**⑨ Google DeepMind 发布 AlphaGenome Atlas**
核心变化：AI 可搜索数据库，预测人类基因组全部 90 亿种单字母 DNA 变化的影响，预计算数据达 1PB（官方称比 AlphaFold 数据库大 30 倍以上）；浏览器直接查询、无需编程，学术研究免费，并开放 API 与 Antigravity 技能。
影响：继 AlphaFold 之后，基因组变异解读进入"全图谱可查"时代，精准医学查询门槛大幅降低。
链接：https://alphagenome.google/atlas

**⑩ DaVinci Resolve 21.1：剪辑软件接入 Claude / Codex 等 AI 助手**
核心变化：重大更新版可通过提示词让 AI 助手完成项目分析、媒体管理、批量渲染、长视频自动高光剪辑等操作（配合 Claude Code、ChatGPT Codex 等）；注意 Python 高级脚本功能从免费版移至 Studio 版，Win/Linux 仅支持单 GPU。
影响：AI 开始"直接操作专业剪辑软件"，是创意工具被 Agent 接管的前沿案例。
链接：https://www.blackmagicdesign.com/media/release/20260908-03

---
已标记 2026-09-09 期为已读。另注意到 8/7–8/15 有 9 篇历史积压未读（之前疑似未处理），如需补出摘要可回复告知。
