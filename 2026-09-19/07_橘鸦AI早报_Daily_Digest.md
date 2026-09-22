
**橘鸦AI早报 2026-09-18 期 · 中文摘要**
（源：https://daily.juya.uk/issues/2026-09-18/ ，本期共 21 条，已筛掉低价值更新）

---

**1. 智谱用 GLM-5.3 自建推理基础设施，10 万+ 国产加速器跑满生产流量**
GLM-5.3 驱动的 Infra Agent 在不到两周内完成 GLM-5.3-Flash 在超 10 万块国产 AI 加速器集群上的生产部署，端到端吞吐提到初始基线的 3.2 倍，官方称单 token 成本已可对标主流 NVIDIA GPU，支持 100 万 token 上下文与多模态请求。分工上，Agent 负责分析、提假设、改代码，人类工程师只负责定目标、搭反馈环境、审查高风险变更。
**影响**：这是一次罕见的"AI 写基础设施代码 + 国产卡承载全量生产推理"的公开实证，对国内算力替代叙事是硬证据。
https://z.ai/blog/glm-built-its-inference-infrastructure

**2. Claude Code 重构 Projects：一个项目变成能自我调度的并行云端线程群**
Projects 从"资料文件夹"改成"持续对话"：Claude 按用户目标拆任务、启动并协调多个并行云端线程，每个线程是独立 Claude Code 云会话，可在各自分支写代码、跑测试、提 PR，共享记忆，用户关电脑后任务继续。目前 Pro/Max 公测（优先给用过云会话的账号），Team/Enterprise 尚未开放。
**影响**：Agentic 编码从"单会话"走向"人离线、多线程长周期作业"，这也是 Anthropic 把 Agent 编排权收回自己手里的信号。
https://claude.com/blog/projects-redesigned

**3. 千问 Qwen3.8-Omni-Flash：1M 上下文原生全模态，音视频 API 价格砍掉 9 成以上**
支持文本/图像/音频/视频输入与 1M 长上下文，主打长音视频的"理解—规划—工具调用—交付"闭环（视频剪辑、短剧翻译、会议处理等）。官方称 29 项评测平均分比 Qwen3.5-Omni-Plus 提升超 25%，每小时音频输入价格降幅 >98%、音视频 >93%；同步开源 Qwen-MM-Plugins 与 Qwen-Live Harness。
**影响**：全模态长上下文的成本门槛被大幅压低，视频类 Agent 产品可以真正算得过账了。
https://qwenlm.github.io/zh/blog/qwen3.8-omni-flash/

**4. Anthropic 公布"前沿 AI 开发速度"三类指标，自曝 Claude 主导 26% 研发工作**
指标覆盖研发自动化程度、内部 Agent 监督、研发算力分配。内部数据：Claude 尚未在任何被测 AI 研发工作中完全自主运行，但已主导 26% 的工作，参与协作或更高自动化水平占比超 90%；最常用内部平台同时约有 3 万个研究与工程 Agent 在跑；所查一周内约 6% 研发算力用于安全工作（AI 驱动研发算力中约 12%）。Anthropic 计划让多家独立第三方接触其内部流程和数据做核验。
**影响**：这是厂商第一次把"AI 造 AI"的具体百分比摆上台面，既是透明度倡议，也是把披露标准定成对自己有利的先手。
https://www.anthropic.com/institute/measuring-pace-of-ai-development

**5. OpenAI 推出 Astra for Law，法律垂直市场正式开打**
把 GPT-6 Astra 与 Legal Search Index 结合，可检索超 2.3 亿个网址中的美国判例法、成文法、法规、法院规则与行政决定；同步推出 26 款合作伙伴插件 + 47 款社区插件，并与律所共建协议分析、并购尽调、IPO 准备工具。目前经 Trusted Access 在 ChatGPT 和 Codex 中向部分律所开放，API 即将开放。
**影响**：继医疗、生命科学之后 OpenAI 再切高价值专业市场，"模型 + 专有检索 + 插件生态"成为垂直行业标准打法。
https://openai.com/index/astra-for-law/

**6. Ternary Bonsai 2 27B：5.9GB 塞进 27B 模型，保留 98.2% FP16 性能**
基于 Qwen3.8-27B，采用 ternary g128 权重 + 低比特内核，主版本约 5.9GB，比 FP16 基线小约 9 倍；14 项思考模式基准保留 98.2% 综合性能，并加强 Agentic 编码、多模态推理和长周期工具使用。262K 上下文，提供 GGUF 和 MLX 版，可在 CUDA/Metal/CPU 跑，Apache 2.0。
**注意坑**：GGUF 必须用 PrismML 自己的 llama.cpp 分支，原版跑不了。
https://prismml.com/news/bonsai-2-27b

**7. Jina AI 开源 jina-ocr-v1：34 亿参数文档解析，专为低预算 GPU 优化**
端到端视觉文档解析模型，把 PDF、扫描件、表格、图表、发票转成干净的 Markdown。基于 DeepSeek-OCR 后训练，每 token 约激活 5.7 亿参数，用 FastMTP 推测解码提速，支持 25 种语言，面向 NVIDIA L4 这类低预算卡优化。可通过 Jina Reader、托管 API、Hugging Face 或本地 Transformers/vLLM 使用。
**注意**：权重是 CC BY-NC 4.0，商用需单独联系 Jina。
https://huggingface.co/jinaai/jina-ocr-v1

**8. Kimi 一天两发：Code 桌面端 + 开放平台三个独立检索接口**
Kimi Code 桌面端发布，可在图形界面打开本地项目、对话让 Agent 读写代码，靠改动面板、文件预览、终端和内置浏览器验证结果，支持接入第三方模型供应商。开放平台同时上线联网搜索 Basic、联网搜索 Pro、网页读取三个独立 REST 接口，按次计费（Basic/网页读取 10 元每千次，Pro 15 元每千次），失败或空结果不收费，Pro 还会返回来源权威性等级。
**影响**：桌面 Agent 客户端赛道再挤进一家，检索 API 的"按有效结果计费"对 RAG 应用方很友好。
https://www.kimi.com/code/docs/kimi-code-desktop/getting-started.html ｜ https://platform.kimi.com/docs/guide/web-search-best-practice

**9. Epoch AI 上线外部基准审查体系，首批 15 项里 9 项被判定有缺陷**
用统一量表审查基准的任务设计、评分逻辑和运行配置，结果与限制全部公开。首批覆盖 15 项基准：4 项 Verified、9 项 Flawed、2 项因资料不足标为 Not enough info。Epoch 不审自家基准，未来可能委托外部机构来审。
**影响**："某模型在某榜单涨了几分"的可信度问题终于有了第三方评级，厂商引用基准数据会越来越难糊弄。
https://epoch.ai/data/benchmark-reviews-documentation

**10.【传闻】OpenAI 据报接近解决霍奇猜想，但可能压着不发**
The Information 报道称 OpenAI 正在研究千禧年大奖难题霍奇猜想（关于形状的几何性质能否用更简单的代数构件描述），员工预计很快有结果，但因此前 Navier-Stokes 问题的公关风波，公司希望谨慎处理对外信息，公告可能推迟。目前未获 OpenAI 正式确认。
**影响**：如果成真，这是 OpenAI 的第二个千禧年问题级宣称；但"接近"与"证明"之间的距离，正是上次翻车的所在。
https://the-decoder.com/openai-reportedly-closes-in-on-solving-the-hodge-conjecture-its-second-millennium-prize-problem/

---

**其他速览（保留但不展开）**
- Union Alpha 揭晓真身为 Unbiased 的 **Pareto 26.9**：多模型协同系统，靠检查机制按需调用更强模型；隐身测试提前结束，付费接入推进中，输入/缓存/输出 $2.50/$0.25/$7.50 每百万 token，26.10 版本下月公开发布。
- **TRAE 国际版新套餐引争议**：老 Pro+/Ultra 升级后仍按原价扣费，但月度额度从 $90/$400 降到 $60/$200（Ultra 直接减半），不升级则用不了新增模型（GPT-6-Astra、GPT-5.5、GLM-5.2）；linux.do 有用户发帖吐槽"等了 5 个月没有新模型，老用户权益没保障"。
- **ChatGPT for Word** 全套餐开放（含 Free），Business/Enterprise 用户 9/17–9/30 可限时免费体验 GPT-5.6 Sol。
- **联合国 UN System Data Commons** 上线，全球统计做成 AI-ready 知识图谱，支持 MCP 让 AI Agent 取数并生成图表，目标 2027 年前纳入 80% 数据集。
