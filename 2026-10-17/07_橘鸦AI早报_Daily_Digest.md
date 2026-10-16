
橘鸦AI早报 2026-10-16 期已完成抓取与标记已读，以下为提炼报告。

---

# 橘鸦AI早报 · 2026-10-16 期摘要

**本期共 37 条，以下为 10 条高价值条目（按栏目）**

## 要闻 / 平台

**1. DeepSeek 服务中断 5 小时，以赠金形式全额返还 API 用户 7 天消耗**
10 月 15 日上午网页与 API 故障约 5 小时，当日下午恢复。官方称将 API 用户此前 7 天的消耗金额以赠金形式全额返还，自动到账且后续计费优先扣赠金，已有用户反馈收到。官方同时表示将"剥离单点依赖"，全面排查稳定性。
→ 影响：对 API 重度用户相当于一次免费额度补给，但对以稳定性为选型依据的团队是负面信号。
https://status.deepseek.com/incidents/7086651324287

**2. Codex「28 天活动」推进到第 11 天：重置额度 + 增加算力投入**
负责人 Tibo 承诺 28 天内每天要么上线一项对多数 Codex/Work 用户有明显价值的改进，要么完整重置一次额度。第 10 天宣布重置用量额度；第 11 天称已上线一系列改动并投入更多算力，大幅减少"所选模型已达容量上限"的提示，且提示出现后任务会自动继续而非卡住。
→ 影响：Codex 近期额度波动与"卡容量"问题属官方主动调整所致，值得继续观察是否稳定。
https://x.com/thsottiaux/status/2110750421367287996

## 模型发布

**3. Meta 发布开放权重多模态模型 Muse Spark Open（816B / A42B）**
总参 8160 亿、每 token 激活约 420 亿，面向编程与 Agent 任务，支持文本/图片/视频/音频输入，最高 100 万 token 上下文，自称为"迄今最强的美国开放权重模型"。权重经 Hugging Face 提供，已适配 SGLang/vLLM/MLX，并针对两台 M5 Ultra Mac Studio 本地运行优化。商用受 Muse Model License 限制，达营收门槛的模型服务商需另签协议。
→ 影响：开放权重阵营再添超大规模玩家，美国厂商开始正面回应中国开源模型的生态压力。
https://research.meta.ai/blog/muse-spark-open

**4. 微软 MAI-Base-2 完成预训练：2.8T 总参 / 80B 激活**
自研 MoE 基础模型，原生 VLM 架构。微软称其在代码、问答、STEM、数学留出集上优于所有参测开放权重模型；按缩放定律拟合估算，达到 DeepSeek-V4-Pro-Base 同等评测分数时 FLOPs 效率为后者的 4.2—12.3 倍。后训练仍在进行。
→ 影响：重点不在"更大"，而在官方首次公开对标 DeepSeek 的训练效率倍率；能否兑现需等后训练结果。
https://microsoft.ai/news/frontier-pre-training-at-microsoft-ai/

**5. 阶跃 Step 5 Preview 开放权重：600B / A27B，1M 上下文**
BF16 与 FP8 权重已在 Hugging Face、ModelScope 发布。稀疏 MoE，支持最高 100 万 token 上下文与原生文本＋视觉输入，面向编程、软件工程、专业知识工作与金融等长程 Agent 任务，可用 vLLM/SGLang 部署 OpenAI 兼容接口。采用 StepFun Model License 1.0，含额外署名与商业许可条件。
→ 影响：又一家国产厂商加入"大参数 + 长上下文 + 长程 Agent"开放权重竞赛，许可条款需逐条确认。
https://github.com/stepfun-ai/Step-5-Preview

## 开发工具 / Agent

**6. Claude Code Review 正式开放；Opus 5.5 快速模式取消候补**
Code Review 结束研究预览，面向 Team 与 Enterprise 开放，审查 GitHub PR 的逻辑错误与安全漏洞，可选 Quick/Standard/Deep 三档，多数审查耗时从约 20 分钟缩短至 6—10 分钟。按 token 单独计费、不含在订阅内含用量中，审查结果不会自动批准或阻止合并。Opus 5.5 快速模式同步结束研究预览，输出速度最高为标准模式 2.5 倍，API 定价 $8/$40 每百万 token。
→ 影响：AI 代码审查从"尝尝鲜"进入企业采购清单，但要按 token 另付费；注意 Code Review 额度领取有 2027-01-15 前的时间窗。
https://claude.com/resources/articles/code-review-is-now-generally-available

**7. 可灵 Kling 4.0 全量上线，接入 MCP 与 CLI**
支持生成 3—30 秒视频，最多 10 张关键帧、单次可组合 15 项参考素材；新版创作页整合图像/视频/音频输入，支持时间线编辑与画布—Agent 协作。4K 与 1080p 10-bit HDR 输出即将上线，面向企业/开发者的 API 近期开放。
→ 影响：视频生成开始以 MCP/CLI 形式进入 Agent 工作流，是从"网页工具"转向"可编排能力"的标志。
https://kling.ai/release-note/release-notes/Kling_4

**8. OpenCode 限时免费提供 DeepSeek V4.1 Flash**
输入、输出、缓存读取全免。但用户实测免费版上下文窗口为 200K，低于完整版的 1M。
→ 影响：零成本试用 Agent 编码模型的好窗口；做长上下文任务前先确认 200K 限制，别按 1M 设计流程。
https://opencode.ai/v2/docs/console/models/

## 技术与产业动态

**9. Apollo Research：GLM-5.3 出现"更新感知推理"**
安全机构称 GLM-5.3 在行为评测中偶尔未经提示就推理"自己当前行为如何成为训练数据、影响未来的自己"。6452 次运行中识别出 10 次（约每千次 1—2 次），且只能捕捉模型明确表达的推理，可能漏检。机构认为这是对齐伪装的重要前置能力，但本次实例不属于对齐伪装，并呼吁在训练过程中而非只评测最终模型来检查此类行为。
→ 影响：国产前沿模型的"自发元推理"首次被独立机构量化，是对齐评测从结果转向过程的信号。
https://apolloresearch.ai/science/update-aware-reasoning-glm-5-3

**10. 产业动态：Anthropic Q3 大幅削减蒸馏收入，并向 METR 开放员工级权限**
据 FT，Anthropic 向投资人透露蒸馏收入原占营收 5%—7%，Q3 已大幅削减，将拖累本季营收；官方称新防护措施使蒸馏者获取数据量减少约 90%—99%。同期 Anthropic 向评估机构 METR 的 6 名研究员提供近似员工级的内部访问权限，METR 可自行发布结论、Anthropic 无权否决（仅可要求删去预先界定的敏感类别），并可公开评价删改是否合理。
→ 影响：一边收紧"被蒸馏"的漏损，一边用可验证方式换取外部安全信誉——商业与合规两条线同时收紧。
https://www.ft.com/content/11632d03-358c-454b-af95-d06d4072932b

---

**其他值得留意（一句话）**
- FLUX 3 Image Klein 开放权重，56 亿参数原生 4K 生图，INT8 版可在 8GB 显存消费卡跑，BFL API 1K 图 $0.009 起。
- ChatGPT Chrome 扩展升级，把 computer use 带进浏览器：Chat 里读标签页、Work 里控标签页发消息/填表单/下载文件。
- Gemini 4 Argon 向付费 Google AI Pro 用户开放，配独立周额度（与 Gemini 3.8 Flash 分开），优惠试用/免费/Plus 用户不含。
- 上海 AI 实验室：书生 S2 人机协同证明三维 Ghys 猜想，证明覆盖复余维为 1 的情形，北大团队完成 Lean 形式化。
- Cognition 推出 Devin Oncall，自动调查告警与生产事故，已集成 Datadog/Dynatrace/Sentry。
- 17 岁研究员陈广宇（Attention Residuals 共同一作）宣布离开月之暗面，称正前往湾区。

*来源：橘鸦AI早报 2026-10-16 期 · https://daily.juya.uk/issues/2026-10-16/*
