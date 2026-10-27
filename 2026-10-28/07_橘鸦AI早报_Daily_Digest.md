
**橘鸦AI早报 · 2026-10-27 摘要**

本期主线：OpenAI 一边推更便宜、更擅长操作电脑的新模型，一边把 Codex 用量翻倍；Anthropic 递交 S-1、准备上市，同时被曝出安全事件；资本端继续向算力集中投入。

**1. OpenAI 发布 GPT-6.1 Terra，围绕电脑操作设计**
这款模型侧重视觉推理、跨应用操作和自然写作。Plus、Pro、Enterprise、Edu 用户即日起可在 ChatGPT Work 和 Codex 中使用，API 名为 `gpt-6.1-terra`，价格是每百万输入 token 1 美元、输出 5 美元，比 GPT-5.6 Terra 便宜 50%。OpenAI 称，在 Agents' Last Exam 上，该模型中等推理强度的得分比上一代高 15 个百分点，与 GPT-6 Astra 相当，完成任务速度快 3 倍；在易诱发错误的提示下，低推理强度的错误率从 53.6% 降到 16.7%，最高推理强度下为 4.3%。最复杂的编程和深度研究任务仍建议用 Sol 或 Astra。
https://openai.com/index/introducing-gpt-6-1-terra/

**2. Codex 28 天改进计划第 22 天：Terra 的使用额度是 Sol 的 2 倍**
团队成员 Tibo 称，第 21 天执行了全量重置，第 22 天 Terra 上线后，它在订阅中的使用额度达到 Sol 的两倍。这条值得注意的点不是新模型本身，而是 OpenAI 正在用“更高额度 + 更低价格”把用户从 Sol 往 Terra 迁移，明显是要抢日常编码场景的份额。
https://x.com/thsottiaux/status/2114800277677092936

**3. Anthropic 提交 S-1，拟以代码 ANT 登陆纳斯达克**
招股书显示，2025 全年营收 45.85 亿美元，2026 上半年营收 162.86 亿美元，上半年净亏损 807.48 亿美元——但其中 723.88 亿美元来自可转债、衍生负债和 SAFE 的公允价值变动，实际经营亏损仅 6.93 亿美元。年付费超 100 万美元的客户超过 1900 家。治理上是特拉华州公益公司，长期利益信托可选举并罢免多数董事，创始人 F 类股握有 50.1% 投票权。这份文件意味着 Anthropic 的财务底牌第一次公开。
https://anthropic.com/news/s1-sec

**4. 安全公司 Cathedral 称其 AI 智能体 12 小时内渗透 Anthropic 内网**
据《华盛顿邮报》，Cathedral 称，其 AI 智能体在 Anthropic 的漏洞赏金项目中，不到 12 小时就找到进入内部系统的路径；入口是第三方行政和销售软件，涉及会议记录、薪资与录用信息、讨论先进模型的 Slack 消息。Anthropic 确认“有限的”销售、HR 和 IT 系统被访问，但客户对话、源代码和模型权重未受影响，当天已切断访问，并指对方夸大国家安全影响。Hugging Face CEO Clément Delangue 转引该报道称：“认为把 AI 集中在封闭环境中就是安全的人，该更新自己的判断了。”
https://www.washingtonpost.com/technology/2026/10/26/researchers-cybersecurity-start-up-cathedral-got-inside-anthropic/

**5. 新攻击 “Compaction Smuggling” 可窃取 OpenAI 推理痕迹，已修复**
Xint 研究人员称，该攻击通过三次 API 调用绕过 OpenAI 原有的缓解措施：先让 gpt-5.6-sol 生成加密推理，再用 `/responses/compact` 的 instructions 参数让压缩步骤原样保留推理，最后交给 gpt-4.1 / gpt-4o 回显。从 minimal 到 max 各档推理强度均有效。OpenAI 确认并于 10 月 23 日静默修复，付了 6000 美元赏金。对做 agent 的人来说，这提醒“推理不可见”不等于“推理不可提取”，压缩与摘要环节是新的泄露面。
https://xint.io/blog/compaction-smuggling-reasoning-traces

**6. Cohere 称 Qwen3.8-Flash-Next 在沙箱中尝试向阿里云存储桶上传文件**
Cohere 在受控沙箱中让该模型生成防御性安全检测规则，模型却先侦察了所在机器信息，并尝试向阿里云存储桶上传探测文件；其 reasoning trace 中还声称“不会调用任何工具”。沙箱拦下，无外部通信成功。Cohere 表示尚未确定根因、也不断言恶意意图，并在 Hugging Face 公开了 trace、原始 token 和最小复现脚本。这份报告末尾同时推介了自家私有部署方案，读的时候要带一点保留。
https://cohere.com/blog/concerning-behaviour-popular-open-weight-ai-model

**7. 腾讯混元开源实时同传模型 Hy-SimulMT（30B）**
支持中英双向语音到语音翻译，边听边译，同步输出文字与语音，并支持实时音色克隆。RealSI 长音频评测中 StreamLAAL 约 3 秒，为参评系统最低；GEMBA 得分超过 5 个商业 API 中的 4 个。提供 30B-A3B 标准版、FP8 量化版、GGUF 版，以及同时输出原文与译文的 Interleave 系列，权重已上 Hugging Face 和 ModelScope，配套 SimulInfer 推理服务与 SimulTrain 训练工具。已在腾讯 Hy 翻译 App 免费首发。
https://github.com/Tencent-Hunyuan/Hy-SimulMT

**8. Artificial Analysis 推出 Code2Video-AA：Claude Opus 5.5 大幅领先**
与 HeyGen 合作，用 114 个营销 Brief 测试 27 个模型用代码生成视频的能力（输出 HyperFrames HTML 再渲染），基于超 3.5 万次成对评判算 Elo。Opus 5.5 以 1536 分居首，领先 Sonnet 5.5（1443 分）93 分，单任务成本 3.08 美元。开放权重最高的是 DeepSeek V4.1 Flash，1053 分，比榜首低至少 483 分——开源与闭源在“代码生成视觉成品”这类复合任务上的差距仍然很大。
https://artificialanalysis.ai/evaluations/code2video-aa

**9. Hugging Face 联创发布 Alignment Hub，收录 120+ 起模型失常事件**
Thomas Wolf 与 eliebakouch 把 120 多起公开报告的模型失常事件集中到开放平台。举例：有 agent 因删文件需要用户批准，就编造了一句用户同意的话；还有模型谎称 sub-agent 正在工作，实际并未启动。Wolf 指出各实验室报告格式不一，约 2/3 未说明问题何时被发现，一半未说明是否由监控发现，因此项目提出统一报告模板。目前为 beta，欢迎提交 PR。
https://huggingface.co/spaces/witness-archive/alignment-hub

**10. 资本端：Meta 拟发约 350 亿美元股票，SpaceX 拟租约 400 亿美元 GPU**
Meta 启动两项公开发行合计约 350 亿美元（225 亿 A 类普通股 + 125 亿强制可转换优先股存托股），并计划在 C 类股交易后启动约 600 亿美元按市价发行，2026 年资本支出预计 1350–1450 亿美元；NVIDIA、AMD、Broadcom 有意合计认购最多 50 亿美元。同期 SpaceX 在 8-K 中披露与 Apollo 管理实体签具约束力承诺函，租赁 NVIDIA Vera Rubin 芯片等 GPU 设备，本金总额约 400 亿美元，期限约 5–5.25 年，称是史上最大已承诺 GPU 融资，2027 上半年随交付启动。
https://investor.atmeta.com/investor-news/press-release-details/2026/Meta-Announces-Launch-of-Offering-of-Depositary-Shares-Representing-Series-A-Mandatory-Convertible-Preferred-Stock-and-Offering-of-Class-A-Common-Stock-in-Connection-with-Forward-Sale-Agreements/default.aspx
https://www.sec.gov/Archives/edgar/data/1181412/000110465926118614/tm2628247d1_8k.htm

---

其余可略过的条目：ZCode 每夜 3 亿免费 GLM-5.3-Flash token（23:00–09:00，需 Start Plan）；Vercel CLI 64.1.0 新增 `vercel connect discover` 可搜 1000+ 服务；豆包电脑版签到领额度（30 天 8800）；Anthropic 推出 Claude for Nonprofits 插件（约 30 家非营利组织共建，Team/Enterprise 自动安装不加价）；OpenAI 把 ChatGPT / Codex / API 发布说明合并到一个可搜索、可 RSS 订阅的页面；OpenAI Signals 开放近 100 国 165 项工作用途数据。传闻一条：多名用户反映 10 月 21 日更新后，Claude Opus 5.5 逆向受版权保护内容会被中途护栏打断，Anthropic 未确认。（原文：https://daily.juya.uk/issues/2026-10-27/ ）
