
**橘鸦AI早报 · 2026-11-14 期摘要**
（共 24 条，筛选 10 条高价值，广告/小额产品更新/重复新闻已跳过）

本期主线：DeepSeek 把搜索、OCR、ASR、TTS 全部开放成独立 API 并直连对话接口，国内模型开始提供“全家桶”式服务；Anthropic IPO 招股书披露 9000 亿美元基建承诺；Agent 侧“标准”和“编排”同时推进——Sierra 联合 Meta、Shopify 推 Poppy 1.0，Antigravity 把并行子 agent 写成可复用脚本。

---

**1. DeepSeek 开放全家桶 API，工具调用内建进模型对话接口【要闻】**
DeepSeek 把 Search、Fetch、OCR、ASR、TTS 拆成独立接口，开发者可以单点调用或组合。更关键的是把这些能力整合进原有对话接口：开参数后服务端自动完成工具调用和上下文拼接，V4.1-Flash（deepseek-flash）在 Messages、Responses、Chat Completions 三类接口均支持，非思考模式可带引用搜索，思考模式可在多步推理中自主搜索读链。定价：搜索/抓取每千次 5 元、OCR 每千页 1.5 元、ASR 0.39 元/小时、TTS 1.5 元/万字符（后两项限时五折），均不含在 token 费内。
影响：以前要自己拼 firecrawl+tesseract+whisper 的 RAG 链路，现在一个 key 走完；也意味着 DeepSeek 从“卖 token”转向“卖工作流”，与 OpenAI/Google 的 agent 平台正面竞争。同时提醒：对外服务须开安全校验并承担内容审核、模型登记、AI 标识义务。
https://daily.juya.uk/issues/2026-11-14/ ｜ docs: https://api-docs.deepseek.com/quick_start/pricing/

**2. OpenAI 推出 ChatGPT Wallet，dot agent 可代付**
与 Amex、Mastercard、Visa 合作，用户录一次卡后，每次购买前查看商品和总价，再经 Face ID/指纹批准；支付网络生成限定用途的专用令牌（卡号、安全码、有效期），agent 与商家都拿不到真实卡信息。今日起对美国 18+ Pro 用户开放，初期不收交易佣金。
影响：这是 agent 商业闭环最关键的一环——解决“agent 能想但不能付钱”。用现有信用卡仍保留积分与权益保障，说明 OpenAI 走的是“不取代卡组织、只做授权层”的路子。
https://openai.com/index/introducing-chatgpt-wallet/

**3. 腾讯发布混元实时语音模型 Hy Realtime**
新增 Agentic 工具调用（结合上下文自行判断是否联网搜索，统一决策+调用+生成）和唱歌能力（与 TME 灵音 AI 联合，可按歌手/曲风/语种点歌）。已在元宝语音通话与腾讯客服上线，腾讯云 API 近期开放。
影响：语音模型正从“能听能说”转向“能办事”，工具调用内嵌是实时语音做 Agent 入口的前提；唱歌这类拟人能力则直接对标 GPT 实时语音的娱乐场景。
https://rtcube.cloud.tencent.com/component/hunyuan/index.html

**4. Antigravity：Dynamic Workflows 上线，Pro 用户解锁 Orchestrator**
Dynamic Workflows 让 agent 按任务描述写 Python 脚本，并发或分阶段调度多个 subagent，运行前需用户确认脚本，可保存复用——目的是用确定性控制流替代 prompt 漂移。Orchestrator 则由 Gemini 4 Argon 规划审查、轻量 Hydrogen 执行，官方称更快且能减缓 Argon 配额消耗。
影响：这是“swarm”从概念走向可维护工程的一步——把编排固化成脚本而非对话历史，是目前 agent 平台竞争的真实分水岭。负责人称内部使用极频繁。
https://antigravity.google/docs/dynamic-workflows

**5. llama.cpp 发布 v1.0.0，首个稳定主版本**
与 ggml 同步跨过 1.0。项目方承诺今后 API/ABI 不兼容改动通过主版本号体现，支持 150+ 模型架构变体，分发覆盖 Linux/macOS/Windows/Android/iOS。
影响：本地推理终于有了版本契约，企业可据此锁定依赖；对想在手机/工作站跑私有模型的团队是明确的稳定性信号。
https://github.com/ggml-org/llama.cpp/releases/tag/v1.0.0

**6. Anthropic 发布自动化红队系统 Anvil**
基于 Claude 构建，部署前自主找防护漏洞。生物安全 24 组问题与分类器组合中 23 组找到比人工更严重的越狱方案，发现时间压缩到 24–48 小时；反蒸馏测试仅 435 次请求命中首个实质推理泄露，人工专家约需 10.22 万次。
影响：安全测试的“规模差”被彻底拉开——但也意味着红队能力与底层模型能力强绑定，Anvil 用的是关闭安全防护的内部模型，攻击力随模型升级同步上升。
https://safeguards.anthropic.com/2026/automated-red-teaming/

**7. Sierra 联合 Meta、Shopify 发布个人智能体标准 Poppy 1.0**
基于 MCP、OpenAPI、UCP，规范个人 agent 如何通过网站/API/企业 agent 与企业交互，用户用 OAuth 控制 agent 可执行的操作。Meta 的 Muse 每访问一个网站都会优先查找该协议，Shopify 全平台商家默认启用，设计伙伴超 100 家。
影响：agent 电商的“接入协议”之争开打。谁定义协议，谁就掌握 agent 流量分发权——这对 MCP 生态也是重要外延。
https://sierra.ai/blog/releasing-poppy

**8. LangChain 完成 3 亿美元 C 轮，估值 30 亿美元**
CapitalG（Alphabet）领投，GIC、DFJ Growth 新进，老股东 IVP、Sapphire 跟投。估值较一年前的 12.5 亿翻倍多。LangSmith 已有超 7000 家机构客户，员工计划明年底从 435 人扩到 850 人。
影响：agent 基础设施层仍在被资本重仓，且 Alphabet 亲自下注“编排层”，与自家 Antigravity 形成有意思的双轨。
https://www.langchain.com/blog/series-c

**9. Anthropic IPO：9000 亿美元基建承诺，目标估值 1.4 万亿**
招股书披露已承诺约 9000 亿美元基础设施投资，约一半需 2030 年前支付；拟募资最高 904 亿美元，预计 11 月 19 日开始交易。Amodei 在与 Jamie Dimon 对话中称“不超支地拿到足够算力”是上市前最深的商业困境，公司惯例是按低于增长预测锁算力、缺口走现货。
影响：这是整轮 AI 泡沫争论的核心数字——算力承诺已经变成资产负债表上的硬约束，一旦增速不及预期，调整会很剧烈。
https://ipo.anthropic.com/us/

**10. 开发者订阅额度战：Devin、Vercel、Command Code 同时加量**
Cognition 升级 Devin Teams，成员无需加席位即可用 Devin Desktop（每人 2 个 SWE-2 并发免费会话），免费 SWE-2 成为 Teams/Pro/Max 永久权益（仍限量），但席位上限从 200 降到 100；Vercel Token Pass 维持 30 美元月费、所含 token 价值从 80 涨到 150 美元，可用于 Kimi K3/K3.1 Pro、GLM 5.3/5.3 Flash、DeepSeek V4.1 Flash；Command Code 把 GLM-5.3 额度从 20 美元提到 70 美元，10 美元套餐用量增至 7 倍（支持 1M 上下文）。
影响：开放权重模型 + 转售额度正在把编码 agent 价格打到极低，同一价位能买到的 token 数量几个月内翻倍以上。
https://devin.ai/blog/devin-teams-plan ｜ https://vercel.com/changelog/vercel-token-pass-now-includes-one-hundred-fifty-dollars-of-monthly-tokens

---

**其他值得一眼扫过的**
- 四家美国非营利机构在旧金山高院起诉 OpenAI、Anthropic、Google、Meta、SpaceX 超级智能公司，援引加州不公平竞争法，请求冻结先进模型开发直至被证明可控；Bernie Sanders 公开支持。（https://abcnews.com/Technology/wireStory/advocacy-groups-sue-ai-giants-freeze-new-models-138081070）
- OpenAI 解散独立机器人团队，人员并入主研究团队与应用部门，官方称 GPT-6 Astra 等通用前沿模型已能直接驱动机器人，无需单建专用模型。
- 微软为 Microsoft 365 近一天半的大规模中断致歉，明确与网络攻击和 AI 无关；Claude 的 M365 连接器受波及。
- 传闻：SpaceXAI 裁撤 Grok Imagine 约 60 人，仅留少数维持运营，重心转向 AI 编程与 agent 产品。

已标记该期（article 7395）为已读，下期扫描将只推新内容。
