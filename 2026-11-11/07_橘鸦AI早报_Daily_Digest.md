
# 橘鸦 AI 早报 · 2026-11-10 期摘要

> 本期共 21 条，已筛掉限额重置公告、Ollama 用量页、OpenCode 安卓端等低价值项，保留 10 条。

## 一、要闻

**1｜Anthropic 双发 Fable 5.2 与 Mythos 5.2，编程能力反超 Opus**
Fable 5.2 在 FrontierCode 2.0 的 Xhigh 档得 49.1%（Fable 5.1 为 32.4%，Opus 5.5 为 45.5%），FrontierSWE v2 得 69.9%（Opus 5.5 为 62.3%），输出速度最高快 30%。官方称 High 档成绩接近 Opus 5.5 的 Max 档，单任务成本仅约一半——这意味着中端价位模型开始吃掉旗舰模型的编程预算。Mythos 5.2 侧重漏洞发现与修复，Fable 5.2 侧重数据密集知识工作。API 定价：输入 8 美元、输出 40 美元每百万 token，快速模式 2.5 倍速、价格翻倍。反蒸馏上，API 的 preserved thinking 扩展到全部账户。
影响：对日常编码任务，官方自己建议「先从 Opus 5.5 开始」，但性价比天平已明显偏向 Fable。
https://anthropic.com/claude-fable-and-mythos-5-2

**2｜Seedream 5.5 主打「改图百轮不走样」，单张降价 60%**
字节称模型通过专项训练保持非编辑区域像素一致，演示中同一作品连续编辑 100 轮、每轮以上一轮结果为输入。支持生成带 Alpha 通道的透明素材、最多分层输出 100 层，复杂小字崩坏率降至严重 0.4%／轻微 1.7%。价格：2K 方图编辑单张 0.28 元，较 5.0 Pro 降 60%，速度快近 40%，文本 token 免费。
影响：多轮编辑一致性一直是图像模型的痛点，这直接把「反复改稿」变成可用工作流；分层输出对设计排版链路意义更大。
https://seed.bytedance.com/zh/blog/more-realistic-images-more-stable-editing-across-100-rounds-introducing-seedream-5-5

**3｜阿里云 Token Plan 个人版降价 + 提额，Pro 月费 499→312 元**
Lite、Essential、Standard 三档月费不变但额度提升 74%~78%（2 万／4.5 万／8 万 Credits），Pro 额度 18 万→20 万 Credits 且月费降 37.5%。四档单位额度成本均下降约 43%。存量用户同步补齐，Pro 新价格下个订阅周期执行。
影响：国内个人开发者订阅价格战继续，单位成本几乎腰斩；结合上面的模型降价，token 成本下探是今年主线。
https://mp.weixin.qq.com/s/jHMi-kO0VpjQKqezGEiK9g

**4｜OpenAI dot 可连接多台电脑，按任务指定执行机器**
每条线程一次只用一台机器，可为任务指定哪台执行。典型场景：让 dot 在第二台 Mac 的 Xcode 里测试 iOS 改动并回传截图；复现 Bug 时在笔记本与装有旧 SDK 的机器上跑同一测试比对结果。权限独立设置——连接 Codex 或开启 Work Sync 不会让 dot 获得该机访问权。
影响：agent 开始从「一个会话一台机」走向「任务级调度算力」，多机异构环境（不同 SDK/系统版本）测试是真实痛点。
https://learn.chatgpt.com/docs/dots/computers-and-apps

## 二、模型发布

**5｜Meta Muse Ember：迄今最小模型，专攻 agent 重复劳动**
muse-ember-1.0 面向工具调用、编码子任务、信息抽取等重复性 agent 工作，原生支持文本／图像／音频／视频，100 万 token 上下文、单次最多输出 51.2 万 token。Artificial Analysis 智能指数 36 分，与 Claude Haiku 5.5 最高分持平，单任务成本约为其三分之一。已在 Meta Model API、Muse Code、Google Cloud、Oracle Cloud 上线。
影响：agent 流水线里大量调用是「廉价重复工」，这类小模型的成本优势比跑分更重要。
https://research.meta.ai/blog/muse-ember

**6｜美团开源 LongCat-2.5：1.6 万亿参数 MoE，MIT 协议可商用**
原生多模态 MoE，每 token 激活约 480 亿，100 万上下文，针对国产算力芯片优化——面向单卡显存不足 80GB 的芯片，推理用专家权重与激活量化到 4bit 的 W4A4 方案，长序列 SFT 单卡吞吐较 DDP 基线提升 86%。权重已上 HuggingFace／ModelScope。
影响：MIT 协议 + 国产芯片适配，是国内私有化部署最实用的一条路，比跑分更值得关注的是它 4bit 部署的工程取向。
https://huggingface.co/meituan-longcat/LongCat-2.5

**7｜Sophon-Realtime v1 开源全双工语音模型，Apache-2.0 可商用**
Tag／Flash／E2E 三版本共用同一个 32B「大脑」，区别只在回复如何转成声音。特性：用户说话时持续倾听、停顿即接话、被打断立即停；能从声音里识别情绪、重音、叹气，回答时自行决定何时笑或重读。VoiceBench 82.8 分、Big Bench Audio 准确率 81.8%，官方称居开源全双工模型第一。
影响：全双工是语音交互体验分水岭，Apache-2.0 且可商用，做语音助手的产品可以绕开闭源 API。
https://github.com/adventists-ai/sophon-realtime

## 三、开发生态

**8｜OpenAI Agents API 三个新功能：12 小时 prompt cache、Async functions、预算控制**
prompt cache 保留时长提升到 12 小时（长时运行的个人 agent 场景省成本）；Async functions 让 agent 调用工具后不必等结果就继续工作，可提前发起慢查询、先回答请求中相互独立的部分；budget control 以 beta 形式提供，支持会话级限制与监控，防止单个客户耗尽全部 token，需申请开通。
影响：Async functions 是结构性变化——agent 的编排从同步串行转向异步并发，长任务延迟会明显下降。
https://x.com/AzianMike/status/2119876908066427244

**9｜Inkling 2 Small 上架 OpenRouter，限时免费**
Thinking Machines 的模型，视觉 + agent 编程结合，靠视觉反馈搭建和迭代网站、游戏与 3D 设计。可在 Claude Code、Codex 和 Hermes Agent 等 agent 环境中以 0 美元调用，暂不支持欧盟路由。
https://openrouter.ai/thinkingmachines/inkling-2-small:free

## 四、技术与产业

**10｜OpenAI Control Room：35 秒内可叫停研究中的模型任务**
中央系统追踪研究基础设施的全部推理负载（含训练与评估用的 agent 采样、数据处理），与模型偏离监测系统联动。从决定干预到切断输出最长 35 秒。采用失效关闭设计——Control Room 本身宕机时，引擎拒绝所有推理请求。已覆盖全部前沿模型研究工作负载。
影响：这是把「AI 失控应急刹车」做成基础设施，失效关闭（fail-closed）是个强承诺，也意味着可用性风险被主动接受。
https://openai.com/index/control-room

**11｜Fireworks 确认被入侵：账单、数据集、不完整模型权重外泄**
第三方云商 10 月 23 日出事，攻击者次日进入研发机器运行未授权任务，10 月 25 日后未再发现越权访问证据。事件与 LLMJacking（窃取大模型访问权转售）手法有关。支付卡号不由 Fireworks 存储、未受影响；期间已停用自助数据集上传下载。Forbes 称已有两家客户把大部分业务迁出，The Information 称部分客户在考虑迁出。
影响：推理服务商的「研发机」成了供应链薄弱环节，选型时要把数据隔离与客户流失风险算进去。
https://fireworks.ai/security/bulletins/october-2026-security-incident-update

**12｜Google 一次性再发两款 TPU：8tx（首款机密计算）与 8i Max**
8tx 是 Google Cloud 首款支持机密计算的 TPU，与 AMD 合作在硬件层加密主机↔TPU 传输、使用中的权重也隔离保护；8i Max 单封装集成两颗芯片，384GB HBM、17.2TB/s 带宽，均为此前 8i 的 2 倍，面向长上下文高吞吐推理。同时开源 TPU Sync 软件，把 HBM、主机内存、共享存储与网络整合为统一内存层级，KV cache 传输与 TTFT 降低 90% 以上。
影响：一年四款 TPU 的节奏，加上 TTFT 降 90% 的软件层优化，直接压的是推理经济性。
https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/tpu-8i-max-and-8tx/

## 顺手记两条

- **Google Antigravity 推出 Knowledge Work 布局**：隐藏终端、Git、代码 diff，突出对话/文档/成果，与 Software Engineering 布局共用同一 agent 和全部 skills/MCP 能力。官方称 Google 内部大量非开发人员已每日使用。https://antigravity.google/blog/antigravity-for-knowledge-work
- **钉钉千问办公 2.0**：定位 Team Agent，推出协作空间（关联群聊、文档、AI 表格、AI 听记）与数字员工「小Q」，支持事件订阅式自动任务（纯云端任务关机仍运行），人机共创可在原文档内按选区批注直接改。https://mp.weixin.qq.com/s?new=1&signature=WsAlCDU%2AkZymDtJJKpBstmU9mr6qalSPhltNuojPmJRmdt6zEI9ML7NDVp6td56cW49Wvd3T3cJ-69M7goAA9Ug39P8og2Lhs7uyB4aXMjdyv5WYspcMq0Ok94F9c3A9&src=11&timestamp=1794218499&ver=7078

---
已标记 2026-11-10 期（article 7298）为已读，无其他未读。
