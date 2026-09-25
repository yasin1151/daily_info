
# 橘鸦AI早报 2026-09-25 摘要

原文：https://daily.juya.uk/issues/2026-09-25/ （已标记已读）

**1. ChatGPT 或在筹备 500 美元/月的「Pro Max」订阅**
官方页面代码里被博主扒出未发布套餐文案，标价 500 美元/月（部分页面显示 600，报道解释为含税差额）。与现有 Pro 相比，文案只多了一句「最快的 Work 和 Codex」，指向更快的任务处理速度。媒体推测可能跑在 Cerebras 算力上，OpenAI 未确认。**影响**：Agent/编程类重度用户的付费天花板可能被抬高一个数量级，也侧面印证高速推理算力正成为分层收费的抓手。
https://x.com/testingcatalog/status/2103259620592542102

**2. DeepSeek Harness 桌面端安装包已可下载**
用户发现官方 `download.deepseek.com` 上已托管 Windows x64 与 macOS arm64 安装包，最新可见版本 0.1.7-rc.2，官方 GitHub 也出现 Desktop 相关代码与更新记录，但 DeepSeek 尚未发布任何公告，官网也没有下载入口。**影响**：DeepSeek 在做本地 Harness（Agent 运行框架）而非只卖 API，若落地，会直接影响 Claude Code / Codex 的本地同类竞品格局。
https://github.com/deepseek-ai/deepseek-harness/releases

**3. OpenRouter 推出服务器工具市场**
把网页搜索、网页抓取、图像生成、沙箱命令行等工具做成统一接口，不同模型都能调；工具可在请求期间由平台托管执行，开发者不必自己写工具调用循环。网页搜索可指定 Exa / Parallel / Perplexity 或自带 Firecrawl 密钥；托管 Shell 按每秒 0.0001 美元计费、最低按 30 秒起算。**影响**：Agent 工具层正在被平台化，「自带工具循环」这套自建工程的必要性在下降，成本结构对长任务尤其敏感（分钟级 Shell 调用的单价值得算账）。
https://openrouter.ai/tools

**4. Claude Code 两则产品动向：Projects 支持本地运行，plan mode 拟改为内置 mod**
Projects 加入本地支持，项目线程可跑在用户自己电脑上，仍处测试期，按候补名单向更多 Pro/Max 开放。另外开发者 Thariq 表示计划把 plan mode 改成内置 mod，允许用户自定义模式提示词、改 Shift+Tab 绑定，甚至干脆不用 plan mode。**影响**：前者回应了「上下文和代码别离开我机器」的隐私诉求；后者说明官方承认自规划型用户不需要专门模式，此前「取消 plan mode」的争议以委托给用户自定义收场。均未正式上线。
https://x.com/ClaudeDevs/status/2102893178273874102 ｜ https://x.com/trq212/status/2103212051065921632

**5. Anthropic 恢复对三类「回复前拦截」请求收费**
仅涉及生物学、蒸馏攻击、前沿大模型开发三类误判率较低的分类，Anthropic 称近期遭遇协同攻击，恢复计费是防御手段之一；官方称 99.7% 使用 Claude Code / Claude.ai / Cowork 的账号不会遇到重新计费拦截，分类器误判率调到 0.1% 以下，误拦可用 `/feedback` 反馈。**影响**：这是少见的「按拦截计费」条款，做安全对齐、模型蒸馏研究和生物方向的团队要重新评估成本与踩线风险。
https://platform.claude.com/docs/en/build-with-claude/refusals-and-fallback

**6. Gemini 3.8 Live with Live Avatar 在 Gemini Enterprise 正式开放**
企业客户可通过 API 构建实时对话、口型同步、带表情的视频形象 Agent，支持边对话边在后台调用工具，同时处理音频、实时摄像头画面和屏幕共享，自动识别并理解 97 种语言。**影响**：数字人从「念稿播放器」升级为可被 API 编排的多模态前端，客服、导览、销售场景的替代窗口开启。
https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-8-live-with-live-avatar/

**7. Odyssey 发布多 Agent 世界模型 Agora-2**
开放可试玩研究预览版，最多支持 20 名人类与 Agent 同时参与共享实时模拟（是 Agora-1 的 5 倍），预览版为 4 名玩家对 16 个 Agent；画面由模型实时生成，后台不用游戏引擎，模型基于《暗黑破坏神 II》带动作与状态信息的画面训练。**影响**：多智能体共存、且彼此行为互相改变对方观测的实时环境，是 Agent 社会性评测的稀缺基础设施，对做多 Agent 训练/评测的团队价值明显。
https://odyssey.systems/introducing-agora-2

**8. 国内两家同期开放「决策模型」API 限时免费**
硅基流动上线 Kev-4B、SemIf、DiffusionGemma 三款开源快速决策模型（Serverless，10 月 8 日前免费），接口支持是非判断、单选、评分，一次请求可组合多类问题；博查发布 Bocha Jev（模型标识 `bocha-jev-v1`），按状态+指令+候选项返回选择/评分/条件判断，单次最多 32 个问题、1024 个候选项、默认 200 QPS。**影响**：「不让 LLM 写文字，只让它做结构化判断」正在成为一个独立品类，客服分流、搜索排序、Agent 分支决策这类高频低延迟环节用 4B 级模型即可替代大模型调用，成本能显著压低。
https://mp.weixin.qq.com/s/HPbVrM8kevJXAETXbjC6ug ｜ https://jev.bocha.cn

**9. 谷歌 Project Suncatcher：10 月 1 日发射原型卫星验证太空 TPU**
与 Planet 合作建造的原型卫星将搭乘 SpaceX Transporter-18 任务发射，检验 TPU 能否承受太空飞行、辐射和热环境，并测试光学星间链路与卫星协同执行机器学习任务的可行性。**影响**：把算力放到轨道上吃太阳能，是「电力-散热」这条 AI 最硬约束的绕行路线，若第一阶段验证通过，算力基建的想象空间会被改写。
https://blog.google/innovation-and-ai/models-and-research/google-research/google-project-suncatcher-facts/

**10. DeepSeek 融资与营收数据曝光：估值约 5000 亿元，70% 以上算力用于训练**
报道称 DeepSeek 正敲定约 500 亿元人民币新一轮融资，目标估值约 5000 亿元，计划最晚 10 月底完成；年化营收运行率达 10 亿美元（数月前不足 5 亿），梁文锋在投资者会议上称涨价后客户数未下降，但增收不是当前首要任务；公司超 70% 算力用于新模型训练，不到 30% 用于在线推理。**影响**：这是国内少见的「训练算力占比 >70%」公开口径，说明其仍处于以训练换代差的阶段，而非靠推理变现，也预示即将到来的模型迭代力度。
https://www.reuters.com/world/asia-pacific/chinas-deepseek-annualised-revenue-hits-1-billion-information-reports-2026-09-24/

**传闻速览（一句话版）**
- 谷歌、OpenAI、Anthropic 正推进组建无政府监督的 AI 安全标准自律组织 SAFA，可能 2026 年底至 2027 年初启动，拟管测试、审计与事件报告。https://www.theinformation.com/articles/inside-ai-industrys-behind-scenes-push-police
- 谷歌 DeepMind 透露 Gemini 4 已进入后训练初期，正在做防护机制与安全测试，内部已用 Antigravity 编程工具跑它；希望「远早于年底」推出早期版本，但仅为意向。https://www.theinformation.com/articles/google-nears-release-flagship-gemini-4-ai-model
- 马斯克称 SpaceX 可能在两三个月内拥有 Fable 或 GPT-6 级别模型，约半年后有望领先。
- Anthropic 拟在 IPO 前调整股权结构，七名联创合计掌握 50.1% 表决权（条件为七人中至少三人持续持股），不涵盖董事选举。

**已跳过**：豆包再送 30 天订阅、腾讯 Hy 翻译 APP 上线、Arena.ai 排行榜改版、Meta 智能眼镜/Muse Charm 硬件（属 CES 式硬件发布，对开发者与 Agent 生态当期影响有限）、腾讯 QClaw 12 月 24 日停运（存量产品退场，用户可退款并迁移至 WorkBuddy，获 1000 积分补贴）。

无其它未读内容，已全部标记已读。
