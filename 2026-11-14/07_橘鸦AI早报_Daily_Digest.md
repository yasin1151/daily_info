
**橘鸦AI早报 · 2026-11-13 摘要**
原文：https://daily.juya.uk/issues/2026-11-13/

**1. Google 发布 Gemini 4 Hydrogen，同时上线 Antigravity「Orchestrator」**
Hydrogen 主打日常编码和 Agent 任务，官方称完成速度是 Gemini 3.8 Flash 的 2.5 倍，提供四档思考级别、100 万 token 统一上下文；API 每百万输入 $1.5、输出 $7.5，并设有免费层，Pro/Ultra 可在 Antigravity 与 Sheets 中使用。基准结果并不压倒性：SWE-sweep 13.5% 超过 Sonnet 5.5 和 GPT-6.1 Terra，但 Terminal-Bench 4.1 反而落后 Sonnet 5.5，可见它强在「改代码」，弱在长链路终端操作。配套的 Orchestrator 由 Carbon 规划、Hydrogen 执行，官方称成功率接近 Carbon，但平均少用 24% 配额、快 19%，目前仅面向 AI Ultra 用户。这说明多模型编排正从用户手动切换模型，变成产品内置的节省用量策略。
https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-hydrogen/

**2. Jensen Huang 辞任英伟达 CEO**
董事会宣布，他即日起辞去总裁、CEO 及董事职务，CFO Colette Kress 出任临时 CEO（保留 CFO 职务），Harvey C. Jones 担任首任董事会主席，新 CEO 遴选同时考虑内外候选人。此事发生在算力扩产与出口政策最敏感的时期，且接任者是财务出身，过渡期资本开支口径与供应链承诺是观察重点。
https://nvidianews.nvidia.com/news/nvidia-announces-ceo-transition

**3. Anthropic 推出 Claude Meetings**
Claude 以「可见参会者」身份加入 Google Meet，会中记笔记、回答提问、实时共建文档和白板，会后纪要与转录稿存到 claude.ai 的会议页。Team/Enterprise 计划的 beta 版，当前只支持 Meet；测试期内纪要转录免费，会议中生成的文档免费到 2027-02-10。会议 Agent 从「录音转写」推进到「在场协作」，但对 Zoom/Teams 的支持缺失是明显短板。
https://claude.com/resources/articles/claude-meetings

**4. Claude API 支持对话中途调整 effort；Managed Agents 推出企业自托管私测**
可在消息序列插入一条内容为空的 system 消息，用 output_config.effort 中途改变模型努力程度，且不改顶层参数、prompt cache 照常命中，省成本的细节做得很实用。另一条是企业可把 harness、sandbox、凭据、会话历史整套部署进自家云或机房，模型调用可路由到 Anthropic、Bedrock、Google Cloud、Foundry 或自建网关。一边给成本细控，一边解决大企业「数据不出门」的采购障碍。
https://platform.claude.com/docs/en/build-with-claude/effort-per-message

**5. 火山引擎发布 Seedance 2.5 flash**
视频生成模型，官方称效果最接近 Seedance 2.5、优于前代旗舰 2.0，速度翻倍；720P 约 0.99 元/秒，比 2.5 便宜约 34%，单段最长 30 秒，单次可输入 10 图 + 5 视频 + 5 音频，提供 480P/720P。已陆续上即梦等平台，API 11 月 15 日上线火山方舟。视频生成单价继续下压，短剧、广告批量生产的经济性又被重算一遍。
https://docs.volcengine.com/docs/ark/seedance-2-5?lang=zh

**6. Thinking Machines 开放 Inkling 2 Small 权重**
Apache 2.0 放出多模态 MoE 权重：总参 594B、激活 17B，支持图文输入与 1M 上下文，提供 NVFP4 / MXFP8 两种精度，NVFP4 版至少需 500GB 显存。vLLM 当天支持并集成视觉编码器、专家并行、DSpark 推测解码与 LoRA，SGLang、Unsloth 与 NVIDIA/Together 也已跟上。开源阵营多了个「大而稀疏」的多模态选择，但显存门槛决定它基本是云上和团队推理的菜。
https://huggingface.co/thinkingmachines/Inkling-2-Small

**7. IBM 发布 LLMON 标记语言，防间接提示注入**
用保留特殊 token 把指令、数据、约束显式切成独立块，再由 exec 块声明执行哪条指令、作用于哪些数据；配套开源基于 Granite 4.1 微调的 3B/8B 模型（Apache 2.0）。IBM 称在 OPI 基准上比最佳前沿模型多挡 47% 攻击、比最佳开源模型多挡 95%，通用能力与 Granite 4.1 Instruct 持平。注意官方明确两个模型是实验预览、不用于生产。防线思路从「写更强的提示词」转向「格式 + 微调」。
https://huggingface.co/blog/ibm-granite/llmon-an-llm-native-markup-language-now-in-granite

**8. OpenAI 推出 Daybreak Red Team 与 Defense Factory**
Red Team 是一组协同工作的安全 agent，测 Web 应用漏洞、验证可利用性并检查补丁是否有效，目前早期接入、已开放等候名单；Defense Factory 为研究预览，可扫描接入的 GitHub 仓库、审 PR、定时或持续监控新提交，发现漏洞后通知负责人并在 Codex 里给补丁建议。安全测试开始被 agent 化，且「AI 找漏洞—AI 提补丁」闭环成型。
https://openai.com/zh-Hans-CN/cyber-at-the-frontier/

**9. Google 发布生成式 UI 开放协议 A2UI 1.0**
首个稳定版：agent 用 JSON 描述界面，应用侧用预先登记的原生组件渲染确认表单、图表等可交互内容；1.0 支持 UI 与 agent 双向调用函数、单条消息生成完整界面，并把无障碍写进规范。Web、Flutter、iOS 渲染 SDK 已可用，Android Jetpack Compose 渲染器仍是 0.9.1。Agent 的输出形态从文字流转向可交互界面，做 agent 前端的人值得现在就试。
https://developers.googleblog.com/a2ui-10-build-delightful-fast-reliable-agentic-experiences

**10. 行业两条：百度做 Token 交易所；张一鸣给出「追平时间表」**
百度世界大会推出大模型交易平台「词元所」，比价 + 统一 API 切换，做准入测试、上线抽检，并给供应商建公开信用档案；官方称上线一月入驻资源超 100 个，日均调用 7000 亿 token、5000 万次。国内 API 转售正从灰色代理走向平台化，价格战有了公开市场。另一条，张一鸣在字节 AI 团队内部会表示有能力与 OpenAI、Anthropic 竞争，但真正追平最早要 2029-2030 年，并承认 Seed 预训练数据规模仍偏少是最需关注的问题；外媒称 Seed 正在预训练最高 10 万亿参数模型。这是少见的官方口径差距时间表。
https://cloud.baidu.com/product-s/token_exchange.html ｜ https://www.thepaper.cn/newsDetail_forward_34458935

已标记 2026-11-13 这期为已读。跳过的低价值项：OpenRouter 网站 7 语种本地化、Google Flow 五款艺术家工具、Gemini 眼镜预购（12/10 发货，$395 起）、ChatGPT dot 自定义指令、Codex banked reset 发放、腾讯「裁员 50%」辟谣（已属澄清类）。
