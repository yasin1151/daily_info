
**橘鸦 AI 早报 · 2026-09-11 摘要**（共 30 条，筛出 9 条高价值 + 若干短讯）

---

**1. DeepSeek 发布并开源 V4.1 Flash，9/14 起 V4 Pro 被"降级顶替"**
552B 原生多模态 MoE，100 万 token 上下文，Causal Encoder-Decoder 结构：预填充每 token 只激活 8B、解码激活 16B。最大亮点是 KV Cache 压缩到每 token 890 字节，HBM 需求降到上代 1/4、SSD 降到 1/8。官方称性能、费用、速度、总用时全面超越 V4 Pro，因此 9 月 14 日 12:00 后至 V4.1 Pro 上线前，V4 Pro 的请求会被路由到 V4.1 Flash 并按新单价计费；旧版 V4 Flash 与 Flash Vision Exp 已下线，模型名暂路由到新版。API 新价已生效，仍是峰谷定价（闲时半价），权重以 MIT 协议开源。
影响：自家旗舰被"Flash"路线直接取代很罕见，说明长上下文推理的成本曲线又下移了一档；对做长文档/多轮 Agent 的开发者是直接降本。
配套开源 deepseek-recipe / DeepSelect / DeepJIT 三仓库，其中 DeepSelect 的 TopK 算子比 torch.topk 快 2–20 倍、DeepJIT 同时支持 CUDA 和华为昇腾，明显在铺国产 NPU 部署。Harness 同步发 v0.1.5（默认新模型、支持保 KV Cache 更新 system prompt、实验性 Agent Teams），App 与网页端把"快速/专家/识图"三模式合并。
https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash

**2. OpenAI 暂停 ChatGPT Pro 20x（200 美元档）新订阅**
Codex 负责人 Tibo 宣布停开 200 美元 Pro 新订阅，理由是"这类订阅对系统压力最大"，要优先保证现有用户继续用上 Astra；其他档位和 API 不受影响，网页端 Pro 购买入口已显示暂停提示。
影响：算力瓶颈第一次以"停售最高档"的形式公开化，正好卡在 GPT-6 Astra 上线期；对观望升级的用户是明确信号——现在买不到，且短期不会放开。
https://x.com/thsottiaux/status/2098113585683808624

**3. OpenAI 推出 Agents API 公测版：把 Codex 的运行时开放出来**
由驱动 Codex 的同一套开源 harness 和基础设施提供，一次 API 调用里指定任务、模型、工具和运行环境，就能创建生产级云端 Agent。OpenAI 负责跑 agent loop（模型调用、工具使用、上下文管理、长会话编排），运行环境可选自家托管沙箱、自带基础设施，或 Cloudflare / DigitalOcean / Vercel 的合作伙伴沙箱。API 本身不收额外费用，只按 token 和工具付费。
影响：Agent 的"运行时层"被平台化，OpenAI 从模型供应商直接跨进托管框架的赛道，和 LangGraph 一类自建方案正面竞争；沙箱可插拔说明它并不打算把云厂商全部吃掉。
https://openai.com/index/introducing-the-agents-api/

**4. Cursor 推出 Projects：一个不写代码的"协调 Agent"**
放弃"一任务一 chat"，改为在一个持久会话里和一个协调 Agent 长期共事：它自己不写代码，负责向写代码的 subagent 派活，可在数月跨度内维持上下文，还能设提醒、按计划运行、跟进 PR 修 CI、监听 Slack。默认在云端跑，合上笔记本不中断；需要本地测试时由协调 Agent 拉起本地 Agent，项目内 Agent 共享记忆与产出文件并在云/本地间同步。已进入 beta，左侧导航栏可直接新建 Project。
影响：AI 编程工具的重心从"补全+对话"整体迁移到"常驻的项目经理"，与 Claude Code 的多会话/子 Agent 路线正面撞车。对个人开发者是好用，对团队意味着工作流转方式要重写。
https://cursor.com/blog/projects

**5. Cognition 发布 SWE-2：拿中国开源模型做底座，价格砍到六折**
基于 2.8 万亿参数的 Kimi K3 后训练，已在 Devin Desktop 和 CLI 上线。FrontierCode 1.1 Main 得分 50.0%，与 Fable 5.1 差距不到 1 分而成本低 64%，官方口径是"最多低 70% 的成本达到前沿水平"。训练上首次把 RL 扩到多万亿参数规模，新增算法能在单次 RL 运行中同时训练 medium/high/max 全部推理力度档位，也是它首个支持力度档位的模型。Pro、Max、Teams 用户未来一个月免费用。
影响：中国开源基座正在成为海外编程 Agent 的训练底座，这是很实在的信号；同时"接近前沿 + 便宜六成"的打法会继续压制高价 API。
https://cognition.com/blog/swe-2

**6. GPT-Live-1 登陆 API：边听边说、可被打断的全双工语音**
此前只在 ChatGPT 里，现在向开发者开放。单一模型同时处理倾听和说话，用户打断、补充细节、中途改方向都能即时响应；深度推理和工具调用委托给 GPT-6 Astra 等后端文本模型或第三方模型。开发者可用 system prompt 调语气、语速、会话风格，模型原生输出 ASR 转写，抗背景噪声，支持在电话场景部署全双工语音 Agent。
影响：语音应用不用再拼"转写 + LLM + TTS"三条流水线，客服、外呼、语音助手的延迟和打断体验会有台阶式改善；"把推理甩给后端模型"也是值得注意的架构范式。
https://openai.com/index/introducing-gpt-live-1-in-the-api/

**7. Cohere 开源翻译模型 North Small Translate：官方基准压过 DeepL 和 Google**
稀疏 MoE，250 亿激活 / 2180 亿总参数，覆盖 50 种语言，16K 输入 + 16K 输出。WMT 全部语言平均分 83.6，官方称超过 DeepL、Google Translate 以及 GLM 5.2、Mistral Large 3 等开源模型。提供 BF16 / FP8 / NVFP4 W4A16 三种量化版本。但许可是 CC BY-NC 4.0 非商业，商用得联系 Cohere 销售。
影响：开源模型第一次在官方基准上公开压过商用翻译龙头，但"非商用"这条线决定了它更适合做研究和自建替换的验证，而不是直接上生产。
https://cohere.com/blog/north-small-translate

**8. CursorBench 4.0：难度上调，所有模型分数一起掉**
新基准取自真实 Cursor 会话里的模糊、多文件任务，新增 edit、refactor、investigation、intent understanding、managing jobs、design adherence 等长程问题。Lee Robinson 明确说"比上一版更难，所有模型得分因此下降"。当前榜首 Fable 5.1 Max 只有 51.8%，平均每任务成本 17.28 美元；Grok 4.6 Extra High 41.4%，并预告 Grok 4.7 即将推出。
影响：Agent 编程的真实难度被重新标定，之前那种跑分虚高的对比基本失效；榜单同时给出每任务成本，说明"贵不贵"已成为和"行不行"并列的评价维度——这比特看分数有用得多。
https://cursor.com/cursorbench

**9. Anthropic 红队评测：AI 在战术情报定位与武器开发上的能力**
Frontier Red Team 发布新评测，测模型在战术情报定位和常规武器开发任务上的表现。官方称部分任务过去只有稀缺的、受过高强度训练的人类专家才能完成，而模型正在这类任务上持续进步；其威胁情报团队已经发现威胁行为者把这些模型用于监控和常规武器开发的真实案例。Safeguards 团队已部署新分类器拦截武器开发相关请求，官方坦承这类分类器因能力两用"不会完全可靠"，但认为部署并迭代优于放任风险。同时提醒：只盯专有模型的防护不够，开源权重生态紧随其后，这个差距不能被误当成安全保障。
影响：两用能力的评估从论文话题变成运营级风控，后续前沿模型发布的"安全门"只会更硬；对开源社区则是一次公开的压力警告。
https://www.anthropic.com/research/intelligence-targeting-conventional-weapons-capabilities

---

**短讯**
- **杭州联合智谱推"全城 Coding 计划"**：9/10 起在杭个人买季卡补 44%、年卡补 51%（每人限 1 次、二选一），上城区企业年卡补 55%、单家上限 100 万；需 BigModel 实名 + 杭州社保或学籍。政府直接补贴 AI 编程工具，是第一例，厂商"政企联合拉新"模式开始成型。https://docs.bigmodel.cn/cn/coding-plan/hangzhou-rules
- **ElevenLabs × Universal Music Group 多年期合作**：首次牵手三大唱片之一，首个产品是让粉丝用签约艺术家/词曲作者的音乐做 Remix、mashup 和个性化演绎的 AI 平台，仍在开发中。https://x.com/ElevenLabs/status/2098049234465620251
- **ChatGPT for Financial Services**：基于 ChatGPT Work 定制，内置 Daloopa / PitchBook / LSEG News / Crunchbase 付费数据，引用可追溯到具体段落表格，能用公司自己的 Excel/Word/PPT 模板产出估值模型、研报和 pitchbook，Morgan Stanley 与 Evercore 参与设计。同时在 ChatGPT Work 上线 Data agent，可连 Redshift、BigQuery、Snowflake、Databricks、MongoDB 等，并在 Tableau / Power BI 里建仪表盘，权限沿用原账号。https://openai.com/index/introducing-chatgpt-financial-services/
- **Arena 72 小时免费开放 GPT-Image-2.5 Sunburst**（北京时间 9/13 23:00 截止），该模型在 Text-to-Image、Image Edit、Multi-Image Edit 三榜第一，之后转入匿名对战模式。
- **Codex 上线官方 Unity 插件**（技能由 Unity 工程师编写）、**Gemini API 文档首个预览版进 AI Studio**（URL 后加 .md 取 markdown，另配 Docs MCP 和 Agent Skills）、**Gemini Windows 桌面应用**（Alt+Space 唤起）。
- **传闻**：博主 Andrew Curran 称 OpenAI 已向《纽约时报》确认在"另一道千禧年大奖难题"上取得实质性进展、准备宣布；另有爆料指向霍奇猜想与 BSD 猜想，均未获官方确认。

*已处理 1 篇新文章（2026-09-11），并顺手把积压的 8/07–8/15 共 9 篇旧刊标记为已读，避免后续重复推送。*
