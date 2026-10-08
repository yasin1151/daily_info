
# 橘鸦AI早报 2026-10-08 摘要

本期是模型与 Agent 密集更新的一天：Anthropic、OpenAI 同日发新，微软把 Agent 安全/本地化一次性铺开，微软和英伟达还把"桌面级超算"搬进 Windows。以下 10 条按栏目提炼。

## 要闻 / 模型

**1. Anthropic 发布 Claude Haiku 5.5：平均成本降约 75%**
首个支持可调 effort 的 Haiku，默认自适应思考，上下文提到 100 万 token、最大输出 12.8 万 token。10 万 token 以内输入/输出为 $0.10/$0.50 每百万 token。官方评测 OSWorld 2.1 离线子集从 Haiku 4.5 的 15.7% 飙到 72.4%，Terminal-Bench 4.0 从 0% 到 39.2%。**影响**：高吞吐、低延迟场景（摘要、分类、实时客服、浏览器操作、编程子智能体）成本结构被重写；但新 tokenizer 会让同一文本 token 数增加约 30%，接入前要重新核算。
链接：https://www.anthropic.com/claude-haiku-5-5

**2. OpenAI 向全员推送 GPT-6，上线智能交互界面**
GPT-6 支持"边思考边回答"，网页搜索的响应速度与质量均提升，同步推出 Intelligent UI。Plus 及以上用 GPT-6 Sol，Free/Go 用 GPT-6 基础档。**影响**：OpenAI 把最强模型直接拉平到全民可用，对"模型分层收费"逻辑是一次松动。
链接：https://openai.com/index/gpt-6-for-everyone/

**3. Claude 双降：Sonnet 5.5 缓存读取半价 + 订阅用户发月度 API 额度**
缓存读取价降至每百万 token $0.10，长时间运行任务成本约降两成。同时向 Max/Team 按月发 Claude Platform API 额度：Max 5x $100/月、Max 20x $200/月，Team 按席位汇总上限 $500。额度覆盖 Claude API、Managed Agents、Agent SDK 和 playground，但**不含 Claude Code 与云平台（Bedrock 等）**，且不结转。**影响**：Anthropic 在诱导订阅用户把 Agent 真正跑在自家 API 上。
链接：https://x.com/claudeai/status/2107894060229034197 ｜ https://platform.claude.com/docs/en/about-claude/api-credits-for-subscribers

**4. 开源模型两连发：Liquid AI 决策模型 + Perplexity 多模态嵌入**
Liquid 开源 d1-3B 与实验版 d1-omni-600M，前者在 Decision Index v0.2.1 以 48.57 分居 10B 以下首位，RTX 4090 上单问题延迟仅 8ms，首日支持 llama.cpp。Perplexity 发布 pplx-embed-v2-late（0.6B/9B），同源蒸馏共享嵌入空间，9B 建索引可用 0.6B 查询，PDF/扫描件无需 OCR。**影响**：端侧决策 + 免 OCR 检索，都是能直接落地的低成本路线。
链接：https://www.liquid.ai/blog/d1-open ｜ https://www.perplexity.ai/hub/blog/multimodal-embeddings-beyond-a-single-vector

## Agent / 开发工具

**5. Anthropic 开发工具双更：html-plan skill + SDK 内置 computer/browser use**
Claude Code 团队成员 Thariq 推出 html-plan skill（用整洁 HTML 呈现方案、代码片段、待确认问题，并带 lint 减少常见失败），可通过社区插件市场安装；同时 computer use / browser use 工具集被内置进 Claude 的 Python 和 TypeScript SDK，点击点击、按键映射这类循环改由 SDK 承担，支持 browserbase、e2b、daytona 等驱动。**影响**：写"电脑操作型 Agent"的门槛从自建循环降到一个 SDK 调用。
链接：https://x.com/trq212/status/2107192901537329354 ｜ https://github.com/anthropics/claude-quickstarts/tree/main/computer-toolset

**6. 微软把 Agent 治理做成品：MXC 正式可用**
Microsoft Execution Containers 在 Windows 11 GA，开发者先划定可读写文件与可连网络，隔离环境执行规则、智能体不能自行扩权，提供跨平台 SDK，GitHub Copilot、Codex、Replit 已接入。GitHub Copilot 的本地沙箱也正式开放（CLI/App/VS Code），CLI 可发现本机 Ollama 模型，本地+云端混合推理（HydraFusion 路由）将于 10 月底实验预览。**影响**：Agent 从"能不能跑"转向"跑了会不会越权"，这是企业采购的硬门槛。
链接：https://blogs.windows.com/windowsdeveloper/2026/10/07/microsoft-execution-containers-policy-driven-containment-for-ai-agents/ ｜ https://commandline.microsoft.com/local-models-sandboxed-tools-github-windows/

**7. Codex：投票重置额度、4000 万活跃用户、Codex Cloud 内置 Tailscale**
Codex 负责人 Tibo 发起"要不要重置额度"投票，76% 选重置并已执行；随后宣布 Codex 与 ChatGPT Work 合计活跃用户达 4000 万，所有付费账户再送一次可留存的重置机会。新上线的 Codex Cloud 还内置 Tailscale 作为唯一 VPN 选项，可访问用户 tailnet 内资源——Tailscale 称双方**并无合作**，是 OpenAI 用公开版自己搭的，事后才知情。**影响**：AI 编程工具的用户规模已经到消费级量级；顺便贡献了一个"厂商被动集成"的趣闻。
链接：https://x.com/thsottiaux/status/2107913674593644711 ｜ https://tailscale.com/blog/codex-cloud-tailscale

## 产品应用

**8. 谷歌 SynthID Detector 面向全球开放**
任何用户都可上传图片、视频、音频，检测是否带 SynthID 隐形水印，合作方含 OpenAI、英伟达、Kakao，苹果即将加入。谷歌称已为超 1800 亿张图片/视频、24 万年音频加水印，Search/Gemini/Chrome 内验证每天处理超 100 万次请求；编辑后水印仍可识别，但检测非 100% 准确。**影响**：AI 内容溯源从"媒体专用工具"变成公共设施。
链接：https://synthid.com/

**9. 谷歌同日两款新东西：Playground 游戏生成 + Mac 端侧会议助手**
Playground 是实验性游戏平台，纯文字描述即可生成、游玩、分享游戏，无需编程，已面向美国 18+ 开放，创建权限按 Google One 等级分批。AI Edge Foresight 是 Mac 端本地 AI 会议助手，由 EmbeddingGemma 2 + Gemma 4 驱动，自动生成纪要并支持实时问答，可完全离线、无云订阅费。**影响**：Google 在"生成内容"和"端侧隐私"两端各插了一面旗。
链接：https://blog.google/innovation-and-ai/technology/ai/playground-experimental-gaming-platform/ ｜ https://developers.googleblog.com/en/google-ai-edge-with-embeddinggemma-2/

**10. Grok Bot 三连更：跨模型路由、做幻灯/发邮件、直接读 X**
马斯克宣布 Grok Bot 不再只用自研模型，会按任务调用 Claude Opus 5.5、Midjourney、Suno 等第三方 API，简单问题给小模型、复杂问题给大模型。0.68.1 版支持一起做幻灯片（导出 PPT/Google Slides）、发送带格式的邮件、管理 Gmail 垃圾箱，电脑操作分辨率升到 1920×1200。还开放了搜索/读取/持续监控 X 内容（无需配置 X connector），X 端 @bot 提及功能上线。**影响**：马斯克自家产品公开"不用自家模型当默认"，是对 Grok 定位的一次罕见松口。
链接：https://x.com/elonmusk/status/2107849623364895151 ｜ https://x.ai/changelog/bot

## 产业动态

**11. Nous Research 完成 9000 万美元 B 轮，估值 15 亿美元**
开源 AI Agent 开发商 Nous Research（Hermes Agent 的母公司）获 NVIDIA、微软 M12、三星、Y Combinator、Menlo Ventures 等参投，资金用于打造面向企业的 Hermes for Businesses 并开发移动应用。官方称 Hermes Agent 已被克隆超 2400 万次，按其内部估算约占全球 token 用量 2.5%。**影响**：开源 Agent 路线拿到了顶级产业资本背书。
链接：https://nousresearch.com/a-note-on-our-fundraise

**12. 算力与能源三条大额交易**
韩国宣布明年启动国家级前沿 AI 项目，以约 34.8 亿美元政府股权投资开发对标中国开源模型的国产前沿模型（含 3.9 万亿韩元购 1 万块 Nvidia Vera Rubin GPU，仍需议会批准）；Google 与 Constellation 签 20 年核电协议，升级 11 台机组为 PJM 电网新增 890 MW，首项扩容预计 2028 年完成；据彭博，SpaceX 正洽谈举债 400 亿美元采购 Nvidia 芯片（约 100 亿银行贷款 + 300 亿投资级债券，Apollo 领衔），谈判仍在早期。**影响**：模型竞争正在变成"电力 + 债务 + 国家预算"的竞争。
链接：https://nousresearch.com/a-note-on-our-fundraise ｜ https://investors.constellationenergy.com/news-releases/news-release-details/google-and-constellation-announce-landmark-agreement-bring-890/ ｜ https://www.bloomberg.com/news/articles/2026-10-06/spacex-seeking-to-raise-40-billion-to-buy-nvidia-chips-ft-says

---
另有一条值得留意的舆情：加拿大一名 16 岁少年按 Claude 给出的下山路线离开步道，被困「Widowmaker」陡壁后由救援队绳降救出，当地救援队公开提醒不要用聊天机器人查野外路线（https://www.ctvnews.ca/vancouver/article/teenager-rescued-from-bcs-widowmaker-after-getting-stranded-using-ai-instructions/ ）。

已标记文章 #6515（2026-10-08）为已读。
