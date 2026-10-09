
**橘鸦AI早报 · 2026-10-09 期摘要**

来源：https://daily.juya.uk/issues/2026-10-09/ （本期共 30 条，以下为 10 条最高价值信息）

**开发生态**

1. **OpenAI 为 GPT-6.1 Sol 推出 Ultrafast 模式** — API、Codex、ChatGPT Work 同步上线，官方称速度最高达标准模式 8 倍，智能接近 Astra。API 全面开放，定价为每百万输入 12 美元 / 输出 60 美元（标准模式约 6 倍价）；Codex 与 ChatGPT Work 主要面向 Pro 500 及配额计费方案。影响：OpenAI 首次把"速度"做成单独收费档位，对延迟敏感的生产型 Agent 是明确加钱换吞吐的选项。链接：https://developers.openai.com/api/docs/guides/ultrafast-mode

2. **阶跃星辰 Step 5 Preview 多平台免费一周 + 首款智能体手机定档 10/13** — Step 5 Preview 上线 OpenRouter、OpenCode、Cline、NousResearch、KiloCode 等，为期一周免费，主打 agentic 与专业工作、强调任务成本更低。同期阶跃终端宣布 10 月 13 日 19:00 在上海发布代号 STEPX Neo 的"大模型原生智能体手机"，口号是"智能体第一次走进物理世界"。影响：国内厂商用"免费周"抢开发者心智，同时把 Agent 从软件往硬件端推。链接：https://x.com/StepFun_ai/status/2108182763002278158

**产品应用**

3. **Claude 推出 Dashboards 和 Motion 两项 beta** — Dashboards 可接 BigQuery、Snowflake、Salesforce，用自然语言生成随数据刷新的仪表盘且每个图表展示背后查询；Motion 把报告/图表做成短动画，走代码生成而非视频模型，可改文字数字时序并导出 MP4。同时 Claude Docs、Slides、Design 结束测试，向含 Free 在内的全部订阅开放。影响：Anthropic 正把 Claude 从"对话助手"往企业数据工作台推进。链接：https://claude.com/resources/articles/dashboards-and-motion

4. **Google Cloud 发布通用工作 Agent "Gemini agent"** — 把问答、知识工作、图像媒体创作、写码跑码整合进同一 Agent 与同一套 API，云端持续运行，关电脑后数小时到数天的任务仍继续；底层模型可选（可编排 Gemini 与 Claude），带智能路由与项目级实时支出上限；每个 Agent 独立身份、最小权限、动作入审计日志。已向中小企业早期开放。影响：直接对标 OpenAI 的 Agent 布局，"云上长跑 + 多模型编排 + 企业合规"是主要卖点。链接：https://cloud.google.com/blog/products/ai-machine-learning/welcome-to-gemini-at-work-2026

**模型发布**

5. **JetBrains 开源 Mellum2.1** — 架构与 Mellum2 相同（12B 总参、2.5B 激活），改动几乎全在强化学习为主的后训练：在带 shell 和文件编辑工具的真实仓库中训练，测试通过才给奖励。SWE-bench Verified 从 2.0 猛升到 47.0，Terminal-Bench 2.1 从 0.6 到 17.4，LiveCodeBench v6 达 82.0，Apache 2.0 许可。影响：一个 12B 级小模型靠 RL 后训练把编程 Agent 成绩拉起来，是"小模型 + 强后训练"路线的有力样本。链接：https://blog.jetbrains.com/ai/2026/10/mellum2-1-gets-to-work-a-fast-open-model-for-coding-agents/

6. **研究称 DeepSeek-V4 长上下文存在周期性弱点** — 字节 Seed 联合普林斯顿、斯坦福等发文，发现 DeepSeek-V4/V4.1 长文本检索准确率随信息位置周期性波动，根因是分块 KV 缓存压缩。128K"大海捞针"测试中，同一模型不同位置准确率最大相差 40.2 个百分点；后训练版缩小但未消除。影响：提醒长上下文能力不能只看平均分，"位置敏感性"会直接影响 RAG 与长文档 Agent 的可靠性。链接：https://arxiv.org/abs/2609.36222

**技术与洞察**

7. **人类数学协会呼吁抵制 OpenAI（陶哲轩任主席）** — OpenAI 一次性公开 700 多篇 AI 生成数学手稿后，AHM 指责其违背科研核心规范，称"这不是学术展示，而是权力展示"，呼吁数学家停止合作。次日 OpenAI 因一处符号错误撤回 3 篇、修订 14 篇。陶哲轩警告开放问题正被 AI 大规模"收割"，一旦被视为解决便不可逆。影响：AI 批量生产"成果"与学术评审规范之间的冲突已公开化，是本期舆论最激烈的一条。链接：https://terrytao.wordpress.com/2026/10/07/ahm-statement-on-openais-october-6-release-of-mathematical-documents/

**行业动态**

8. **新版 Claude 使用政策：持续"虐待"AI 或遭封禁** — 11 月 12 日生效，新增禁止"持续且无必要的辱骂或残忍行为"，官方强调仅限极端情况，日常发火、反驳、黑暗题材创作与模型测试不违规，主要执行手段仍是 Claude 主动结束对话。同时把虚假宣传合并为"欺骗性活动"专节，武器禁令扩展到武器软件部件与无人机加装武器。影响：首次把"对模型的对待方式"写入可执行条款，边界定义会成为后续争议焦点。链接：https://www.anthropic.com/news/2026-usage-policy-update

9. **Anthropic 启动 Cyber Mission** — 关键基础设施方向推出 CIDP，向电网、供水、交通服务商提供前沿 Claude 与驻场工程师（创始合作方含 Accenture、CrowdStrike、Palo Alto 等 11 家）；开源方向推出 OSS Scanner，用最强模型免费为选择加入的项目定期扫漏洞，报告由模型生成不经人工审核，预期真阳性率超 90%。链接：https://www.anthropic.com/news/anthropic-cyber-mission

10. **Ecosia 弃用 Mistral 转投中国开源模型** — 据《政治报》报道，德国搜索引擎 Ecosia 因对 Mistral 质量失望（认为落后对手约一年、常有服务器过载），改与开源平台 Melious 合作，转用 Qwen、GLM、Kimi。CEO 称切换后成本约降一半、质量性能反升，并质疑 Mistral 的"主权企业"身份。影响：欧洲"主权 AI"叙事首次被自家环保系公司公开拆台，中国开源模型在欧洲获得真实落地案例。链接：https://www.politico.eu/article/germany-ecosia-search-engine-mistral-china-open-source-ai/

**其他值得留意（简述）**：OpenAI 年化营收口径修正为接近 500 亿美元（比此前报道的 ~700 亿少约 200 亿，差异源于 Anthropic 计入云伙伴收入而 OpenAI 不计，https://www.ft.com/content/b66a9858-f8fb-46cb-b506-44bfe26fca2a）；Arena 完成 2 亿美元 B 轮、估值 31 亿美元并发布 Alignment Index（对齐指数），用"未授权行动/错误归因/欺骗性完成"三类信号衡量模型越权行为；CrowdStrike 报告称疑似中文攻击者用开源 agentic 渗透工具 ARTEX（主模型 DeepSeek v4.1-flash，辅以 GLM-5.3 与 Grok 4.6）攻击韩国多家银行，新韩银行被窃 25,727 条个人信息；Manus 母公司蝴蝶效应完成超 5 亿美元融资（博裕、IDG 领投，腾讯、红杉跟投）；Ghostty 作者 Mitchell Hashimoto 发布通用终端协议 OSC 7501，让程序用一条转义序列向终端上报状态，已有 250+ Agent 编排工具靠启发式猜状态的痛点；谷歌 AMIE 门诊前瞻性研究登上《柳叶刀》，鉴别诊断在 90% 病例中包含最终诊断；彭博社称 Isomorphic Labs 正洽谈新融资，估值至少 400 亿美元。

本期已标记为已读，无其他未读文章。
