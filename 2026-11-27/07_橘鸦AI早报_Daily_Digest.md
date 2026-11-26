
**橘鸦AI早报 · 2026-11-26 期摘要**

---

### 模型与产品

**1. Sand.ai 发布 MAGI-2 视频模型，4800 亿参数还打算开源**
MAGI-2 独家上线 Higgsfield 和官方 API，能接受最多 20 个参考素材（10 图 + 5 视频 + 5 音频），生成最长 30 秒、1080p/25fps 的带声音视频，并支持时间线、镜头切换和首尾帧控制。总参数 4800 亿，激活约 280 亿（MoE）。真正的看点是它支持“对已有视频做定向编辑”，而且官方称计划开源权重并发布技术报告。价格按秒计费，每秒 0.08 美元。
影响：在视频模型普遍只开放生成能力时，可编辑+计划开源是差异化卖点；对做内容生产的团队来说，按秒定价比包月更可控。
https://higgsfield.ai/announcing-magi-2

**2. NVIDIA 开放 Nemotron-Labs-Image-30B-A3B 权重**
自回归图像生成模型，MoE 架构，300 亿总参数、30 亿激活，属于 Nemotron-Labs-VisualCreation 框架的图像组件。NVIDIA 公布的测试中，LongTextBench 得 97.98、GenEval 得 92.86，均高于 GPT Image 2；但在 GenEval2 和 Qwen-Image-Bench 上落后。
需要注意：使用 NVIDIA 许可证，仅限非商业研究和评估，不能直接商用。
https://huggingface.co/nvidia/Nemotron-Labs-Image-30B-A3B

**3. PrismML 开源三值模型 Bonsai 2.5 27B，仅 5.9 GB**
三值（ternary）量化模型的升级版，基于 Qwen3.8 27B，体积只有全精度版的约九分之一，262K 上下文，Apache 2.0 可商用，提供 GGUF 和 MLX 格式，能在 NVIDIA、Intel GPU 和 Apple 设备上跑。
关键数据：五项工具调用基准平均 77.2 分，全精度版 77.7 分，几乎无损；agent 编码能力达到全精度的 90%（上一代只有 63%）。
影响：这是“本地跑得动、且真能干活”的量化模型路线，对想在 Mac 上做 agent 的人是实际可选项。
https://prismml.com/news/bonsai-2-5-27b

---

### Agent 与开发工具

**4. ShellBench 基准发布：最好的模型也才 62.5% 完成率**
OpenClaw 基金会联合多家机构发布 agent 基准，基于 1000 万次以上真实交互设计了 100 项日常任务，对 12 个模型 × 5 个 harness 共跑了 53100 次。GPT-6 Astra 以 62.5% 平均完成率居首，前三名只差 1.1 个百分点。
两个值得注意的结论：(1) 模型选择对完成率的影响 **大于** harness 选择；(2) **15.7% 的运行至少没通过一项安全检查**——这意味着 agent 上生产的失败率仍高得离谱。20 项任务公开、其余私有，Kaggle 已上线复现排行榜。
https://openclaw.ai/blog/shellbench

**5. Anthropic 把 Claude Messages API 从 Python 迁到 Rust，CPU 降 70%**
Messages API 是客户和 Claude Code 访问 Claude 的主要通道，2024 年初到 2026 年秋流量涨了约 1800 倍，Python 扛不住了。Claude 约一周写出核心请求路径初版，团队用生产流量灰度对比新旧版本，自动派 agent 修复问题、工程师审核。
结果：单请求 CPU 消耗降约 70%，首个 token 中位延迟缩短约 20%，而且**全程没停线、没冻结功能开发**。
影响：这是“AI 写代码 + agent 自动修复”在核心基础设施上真正跑通的案例，比任何 demo 都更有参考价值。
https://anthropic.com/research/migrating-api-to-rust

**6. Antigravity 缓存命中率再提升，额度内可做任务多 28%**
负责人 Varun Mohan 称 Gemini 4 Neon 的缓存命中率又提升 4.5%，换算成用户能感知的收益是“订阅额度内可完成任务 +28%”。过去 5 天靠缓存和运行框架改进，Neon 的有效使用量累计提升近 75%，主要来自增大缓存容量、减少长期缓存淘汰和优化路由。
影响：对订阅用户是直接的成本等效降价——同样额度能干更多活。
https://x.com/_mohansolo/status/2125641696377712968

**7. OpenAI 承认 Codex 此前“少扣额度”，已修正，用户会更快撞限额**
多位用户收到邮件：部分 GPT-6.2 Astra 和 Sol 请求、以及 Ultrafast 模式下的部分请求此前计入的额度偏少，现在计费修正了，订阅价格不变，但按原有用法“可能更快达到限额”。
影响：这不是涨价也不是降价，而是之前一直在“送”。对重度用户等于隐性配额下调，社区讨论集中在“为什么不补偿”。
https://linux.do/t/topic/3239841

---

### 产业动态

**8. Claude Code 核心成员 Thariq Shihipar 加入 OpenAI**
他曾参与 Claude Code 核心开发和开发者社区运营，十月下旬离开 Anthropic，现官宣加入 OpenAI，称要在 OpenAI 与 Cat Wu、Tibo 等人一起做“面向十亿用户”的 AI 产品。
影响：这是 Claude Code 团队连续流失中的又一例，开发者工具赛道的人才正在集中到 OpenAI 一侧。
https://x.com/trq212/status/2125675533761671405

**9. OpenAI 小范围测试 Private Inference**
属于 OpenAI Private Intelligence 旗下的新服务，以预览形式提供给少量客户。结合 Confidential Computing 与可验证的控制措施，ZDR（零数据保留）搭配 Private Safety Processing 做自动安全审查，OpenAI 员工无需访问底层内容。
影响：这是冲着金融、医疗、政企这些“数据不能出门”的客户去的，等于 OpenAI 开始正面接企业私有化需求。
https://x.com/sama/status/2125638790593274259

**10. Dario Amodei 公开驳斥“向 AI 让渡治理权”的报道**
Axios 报道称“Anthropic 内部有人支持把决策权交给超级智能 AI”，引发同行抨击。Dario 发长文否认：让 AI 自动驾驶、写代码、研发药物，跟把社会与政治治理权交给 AI 是两回事；AI 过度自主地迭代下一代模型同样要设限，AI 必须受合法民主程序治理。
影响：这是头部实验室第一次把“AI 能替人干活”和“AI 能替人做决定”的边界公开划线，对后续监管话语有参考意义。
https://www.axios.com/2026/11/25/anthropic-ai-human-control-debate-free-will

---

*本期已跳过：Antigravity 员工涨粉/开发 banked reset 的琐碎动态、OpenCode 的 Gimme Kimi 促销（$10 换 $60 额度，属优惠信息）、ChatGPT 桌面端内存优化 40%（工程细节，影响有限）、Gemini Live 无障碍视觉功能上 iOS。*

已标记该期（2026-11-26）为已读，当前无未读文章。
