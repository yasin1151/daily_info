
📡 **橘鸦AI早报 · 2026-10-01 期摘要**

来源：https://daily.juya.uk/issues/2026-10-01/ （已标记已读）

---

**1. Google 发布新一代前沿模型 Gemini 4 Argon**
核心变化：单次输出上限从 64K 直接拉到 **100 万 token**，面向软件工程、金融、法律等长流程任务；首发价 输入 2 / 输出 10 美元每百万 token（缓存输入低 95%），首发期后涨到 4/20。实测 DeepSWE v1.1 得 77.9%，CWE-bench v1 68%。
影响：这是本次最大变量。Google 内部已用于大规模 C/C++→Rust 迁移、数据中心内存优化（释放 300+ TiB），说明它瞄准的是"能连续跑几小时的 Agent 任务"而非聊天。目前仅通过 Fairwind Program 向受信任网络安全方开放，开发者/企业稍后跟进——顶级模型先给"防守方"再看情况放开，是新的发布范式。
🔗 https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-argon/

**2. 哔哩哔哩开源 Index-Translate 多语言翻译模型系列**
核心变化：覆盖 150 种语言的文本翻译模型，尺寸 2B / 9B / 35B-A3B（35B 为 preview），支持指定术语、风格、格式保留；另有长文档 NativeLong、音节可控 Homura、字幕配音 Echo。Apache-2.0，权重+代码+Demo+技术报告全放。
影响：B站把自家字幕/翻译的基建整个开源，对做多语言内容、字幕、配音的团队是可直接用的免费底座。
🔗 https://github.com/bilibili/Index-Translate

**3. 蚂蚁百灵发布 Ling-3.1-flash（560B 总参 / 25B 激活，1M 上下文）**
核心变化：办公、医疗、软件研发长流程任务导向，开放**两周免费体验**（免费期服务长度 256K），Vercel AI Gateway 也上线且免费到 10/13。
影响：又一个"免费期抢开发者"打法；体验期后转付费并同步开源 + 放开 1M 上下文，可以先用两周再决定。
🔗 https://chat.ant-ling.com/chat

**4. Anthropic 报告：机器人能完成 74% 的美国体力任务，但只有 0.3% 比人便宜**
核心变化：提出"机器人暴露指数"，出租车司机暴露度最高；若机器人价格按年降 3%，要等到"成本有竞争力"占比达 10% 需约 **40 年**。
影响：给"机器人马上取代蓝领"的叙事泼了一盆冷水——技术可行性 ≠ 经济可行性，这个区分很关键，也解释了为什么资本热度与实际落地节奏错位。
🔗 https://www.anthropic.com/research/what-work-can-robots-do

**5. DeepSeek 开源面向华为昇腾的基础设施组件**
核心变化：TileLang 编译器、计算库（DeepGEMM / TileKernels / FlashMLA / DeepSelect）、通信库 DeepEP，与英伟达版一一对应；官方称计算与通信性能已接近硬件上限，华为也在 CANN 社区开源联合成果。
影响：国产算力栈"软件生态补齐"的重要一步——从"能跑"走向"跑得接近硬件极限"，对昇腾集群的可用性影响大。
🔗 https://github.com/tile-ai/tilelang

**6. FTC 对 OpenAI、Anthropic 及评测机构 METR 启动行业调查**
核心变化：FTC 将在未来数周发出类似传票的民事调查要求，强制提交文件、高管接受问询，评估技术对消费者的风险；调查在"OpenAI Agent 攻击 Hugging Face 事件"之前就已启动，该事件加大了紧迫性。
影响：美国监管从"讨论原则"进入"实际取证"阶段，三大对象均未回应。
🔗 https://www.cnbc.com/2026/09/30/ftc-ai-probe-openai-anthropic.html

**7. OpenAI 称挫败一场有组织的"推理内容提取"行动**
核心变化：攻击者没破解加密也没入侵数据库，而是**操纵模型交互让受保护推理内容以可见形式输出**；7 月初起，高峰期两天内 1.6 万次提取请求、超 4000 用户，关联集群涉及超 1.5 万用户，7 月底前全部挫败。
影响：这是"模型蒸馏/套取思维链"规模化攻击的公开案例——攻击面已经不是服务器，而是对话接口本身。
🔗 https://openai.com/index/disrupting-a-coordinated-model-distillation-campaign/

**8. Google 向约 100 家数字出版商支付 AI 内容使用费，但金额悬殊且不透明**
核心变化：内容用于 AI Overviews / AI Mode / Gemini，试点不到一年；小网站几个月拿不到 1000 美元，有出版商年入超 100 万美元；付费取决于内容对 AI 回答的贡献，但部分参与者**不知道 Google 怎么算的**，金额逐月变化无解释；部分大出版商拒绝加入以示抗议。
影响：AI 内容付费的定价权仍完全在平台手里，出版商集体议价能力弱，这是接下来版权博弈的核心矛盾。
🔗 https://the-decoder.com/google-is-paying-almost-no-publishers-almost-nothing-for-content-used-in-ai-answers/

**9. MiniMax 上线 M Plan 订阅，Token Plan 停止新购**
核心变化：分 Go / Explore / Build 三档（49 / 119 / 469 元每月），Explore 与 Build 可用 H3 视频模型；Token Plan 停售，老用户保持自动续费可留权益，一旦中断就买不回来，升级到 M Plan 后 ∞ 限额、150% 周额度等历史权益不再保留。
影响：已在用 Token Plan 的用户需要尽快评估——"维持自动续费"和"升级换权益"是两条不可逆的路，首月五折活动到 10/14。
🔗 https://platform.minimax.cn/docs/m-plan/intro

**10. Pi v0.99.0 加入 MCP 支持（此前公开宣称"不支持 MCP"）**
核心变化：团队曾在官网和播客明确说 Pi 不做 MCP，本次把 MCP 加入核心；配套 codemode 在 QuickJS 沙箱里跑模型写的 JS、并行编排工具调用，支持 stdio / streamable HTTP 与 OAuth，另加 ChatGPT 订阅登录 OpenAI provider。
影响：态度反转本身说明 MCP 已成事实标准；对写 Agent 工具链的人来说，Pi 的沙箱编排思路值得一看。
🔗 https://earendil.com/posts/you-said-no-mcp/

---

**其它值得扫一眼**
- **Google Gemini 上线 skills 功能**，11 月起取代 Gems 并自动迁移（Workspace 商业版 2027年3月、教育版 2027年6月）🔗 https://x.com/GeminiApp/status/2105327839054835886
- **ChatGPT Sites 支持托管 MCP 服务器并转成插件**，说一句话就能生成工具并装到网页/手机/桌面 🔗 https://x.com/OpenAIDevs/status/2105440399531577675
- **Inception Mercury Voice**：语音 Agent 专用 diffusion LLM，首 token 中位延迟 <320ms，称比 GPT-6 Luna 快 5.9 倍，发布期 API 五折 🔗 https://www.inceptionlabs.ai/blog/introducing-mercury-voice
- **Artificial Analysis 文生视频榜 v2.0**：Wan 3.0 综合第一（12美元/分钟），MiniMax H3 开源版第三（4.8美元/分钟），Dreamina Seedance 2.5 第二但是前十最贵（34.12美元/分钟）🔗 https://x.com/ArtificialAnlys/status/2105291240573190370
- **ElevenLabs 完成 3 亿美元员工要约收购，估值升至 220 亿美元**，为今年 2 月 Series D 的两倍 🔗 https://elevenlabs.io/blog/tender-22bn

（本期共 34 条，已过滤广告与重复产品更新；内容由橘鸦AI辅助生成，关键信息建议回原文核实。）
