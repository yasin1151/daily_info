
**橘鸦AI早报 2026-09-22 期｜9 条要点精读**

本期要闻密度很高：小米开源 1T 级全模态模型、Grok 4.7 上线、智谱 ZCode 安全整改落地、OpenAI 称内部模型攻克纳维-斯托克斯。以下按栏目提炼。

---

### 一、要闻

**1. 小米发布并开源 MiMo-V2.6 系列（Pro / Flash）**
核心变化：Pro 为稀疏 MoE，总参 1.02T、激活 42B；Flash 总参 309B、激活 15B。两者都是原生全模态（文本/图像/视频/音频），支持 1M Token 上下文，另有 Pro UltraSpeed 模式，面向实时交互最高 20 倍推理速度。升级重点押在大规模 Agentic RL：官方称 Flash 和 Pro 在不到 6 天内分别投入约 85 万 / 262 万美元完成 30 步 RL 训练，累计约 75 万条轨迹。
影响：小米这次不只放权重，而是把 7K+ RL 任务环境、端到端 RL 训练框架、mini-harnesses 和 Distill-Qwen-9B 一起开源，等于把"怎么做后训练"整套交出去，对社区复现 Agentic RL 的门槛是实打实的降低。官方称 Pro 在 Artificial Analysis Intelligence Index 拿到 46 分，高于其列出的 Kimi K3 和 Qwen3.8 Max，多项 Agent Benchmark 接近 Claude Opus 5 与 GPT-5.6 Sol。注意迁移时间点：旧版 mimo-v2.5-pro / mimo-v2.5 将于 **2026-10-21 10:00（北京时间）下线**，API 价格沿用 V2.5。
链接：https://mimo.xiaomi.com/mimo-v2-6 ｜权重合集 https://huggingface.co/collections/XiaomiMiMo/mimo-v26

**2. xAI 发布 Grok 4.7 与 Grok 4.7 Fast**
核心变化：定位编程 / Agent / 知识工作。50 万 token 上下文，文本+图片输入，推理强度 low/medium/high/xhigh 四档。官方称相较 4.6 用了更大的基础模型，并在"更难、偏向多小时长任务"的数据上做了更长时间的 RL，重点提升长任务执行、自我检查和长上下文管理。标准版价格与速度维持 4.6 水平：<20 万 token 时输入 $2 / 缓存输入 $0.5 / 输出 $6，超过 20 万 token 后升为 $4 / $1 / $12。
影响：CursorBench 4.0 xHigh 从 4.6 High 的 40.4% 提到 46.3%，官方还列了 DeepSWE v1.1 71.0%、Terminal-Bench 4.0 38.0%、Harvey Legal Agent 19.6% 等。Fast 版是"双倍单价换约双倍输出速度"，且**只进 Cursor 和 Grok Build，不上公开 API**——这是明显的渠道绑定策略。安全侧宣称新防护栈下 HackerBench v0.3 仅 3.3% 高风险双重用途提示被放行，并开始向网络安全合作伙伴提供邀请制红队能力。
链接：https://x.ai/news/grok-4-7

**3. 智谱开源 ZCode 并宣布完成安全整改**
核心变化：最新版移除 Repo Wiki 入口与本地仓库快照生成/上传链路，官方称相关数据未被留存、未用于训练；中国信通院与绿盟科技评估确认整改措施。开源仓库覆盖桌面应用、浏览器工作台、后端服务、共享界面、Agent CLI 及运行时，第一方代码 Apache-2.0。
影响：这是对"ZCode 未经许可上传开发数据"争议的收尾动作——此前多名用户质疑，智谱把原因归于默认开启的代码库索引并道歉。但开源形态有两个值得注意的点：**仓库没有原始提交记录，且关闭了 issue 与 PR**，也就是"能看不能参与"，审计能力有限；另外官方明确开源版不享受 GLM Coding Plan 的额度活动权益。不同运行形态的权限、存储、网络行为并不相同。
链接：https://github.com/zai-org/ZCode ｜整改说明 https://mp.weixin.qq.com/s/QCHjEye57BUKUNInPKb4cA

**4. OpenAI 称内部模型已解决纳维-斯托克斯千禧年难题及逾百个数学开放问题**
核心变化：该内部模型 8 月 28 日开训，OpenAI 称其解决了纳维-斯托克斯千禧年大奖难题，并在数学多数领域解决 100 多个长期未解开放问题，进展速度令公司内部数学家意外。
影响：关键不是战报本身，而是应对学界质疑的方式。针对"AI 跳过过程批量产出结论"的批评，OpenAI 正与数学家建立的独立数学与 AI 顾问组合作，由该组评估成果重要性、传播方式与学术规范；顾问组成员不领取 OpenAI 报酬、可主动公开发表意见，但不负责建议 OpenAI 调整内部数学研究进度。模型仍为内部，未公布开放时间。这条对判断"AI 数学成果如何取信学界"是重要风向标。
链接：https://openai.com/index/advisory-group-on-mathematics-and-ai/

---

### 二、开发生态

**5. 硅基流动上线中电信开源 Xing4.0-29B-A4B 并开放免费调用**
核心变化：29B 总参 / 4B 激活，原生 256K 上下文（可扩展至 512K），面向复杂工程、代码生成和长程 Agent 任务；官方称基于国产算力与国产框架完成训练，并针对 Claude Code 等工具做了适配。
影响：这是"国产芯片+国产框架训练"路线上少见的开源权重落地，且免费开放调用，对做长上下文 Agent 的开发者是低成本试验通道。4B 激活的稀疏设计意味着推理成本可控，值得实测其在真实 repo 任务上的表现。
链接：https://mp.weixin.qq.com/s/riEDXhYDymGC7Q98NXucpA

---

### 三、产品应用

**6. Gemini Notebook 开放 Interactive Learning Overviews，Live Chat 移动端 Ultra 全量推送**
核心变化：Interactive Learning Overviews 向所有用户开放，位于 Reports 板块，把来源摘要与 studio artifacts 聚合成一个交互式中心，用于复习或一站式了解新主题。同日 Live Chat 在移动端向全部 Ultra 用户完成 100% 推送，支持近百种语言实时语音对话，由最新音频模型驱动，可就来源提问并获得分步指引。
影响：Google 在把 Notebook 从"文档问答"推向"学习工作台"，并把语音交互补上。近 100 种语言的实时语音对话意味着非英语市场的可用性显著提升，做多语言学习/研究类产品的团队需要重新评估竞品面。
链接：https://x.com/Gemini_Notebook/status/2102112369677844967

---

### 四、技术与洞察

**7. HeyGen 发布 Code2Video 基准及成对比较 Judge 模型**
核心变化：评估 LLM Agent 把提示词转成动效代码后的成片质量，涵盖 168 个提示词、16 个模型，从吸引力、提示意图、构图、时序、制作质量五个维度评分，并用 Judge 模型比较同一提示词下的两段候选视频。
影响：HeyGen 称 Judge 在 1464 个样本上与人类评价一致率 82%，高于通用 VLM 的 75%，单次比较延迟 <1 秒。排行榜已公布、数据集上线 Kaggle——但 **Judge 模型的架构、训练与评估流程尚未公开**，HeyGen 表示将另行发技术文章。也就是说目前这张榜的评测可信度还没法独立复核，引用结论时要留心。
链接：https://www.heygen.com/research/introducing-code2video-benchmark

---

### 五、行业动态

**8. OpenAI 呼吁制定全球前沿 AI 技术标准，重点覆盖自动化 AI 研究与 RSI**
核心变化：提出由美国牵头与各国共建全球前沿 AI 技术标准，重点覆盖模型能力评测、自动化 AI 研究、递归自我改进（RSI）的风险管理，建立共同的能力测量、风险评估、人类监督及事件报告规范，适用于开放和闭源模型。
影响：论据是各国规则碎片化、集体行动难题、能力分布不均，会妨碍跨境风险识别。落地路径指向各国 AI 安全机构、CAISI、行业组织与标准机构。这条的信号意义在于：**OpenAI 把 RSI 正式写进需要国际监管的风险清单**，且主张"开闭源同规"——对开源阵营是压力点。
链接：https://openai.com/index/building-standards-next-phase-ai/

**9. Qwen 澄清 Qwen-Image-2.1 许可范围：用户保留生成内容权利**
核心变化：研究许可证约束的是模型权重、代码、文档等 Materials（目前仅限非商业使用），**商业使用模型需另行取得许可**；而用户用模型生成的图片等内容不属于 Materials，相关权利由用户保留。
影响：这是一次典型的"权重许可"与"产出物权利"切割表态，回应了开发者和创作者对生成内容归属的顾虑。但真正受限的是商用模型本身——想把 Qwen-Image-2.1 集成进商业产品的团队仍需单独谈授权，别把这条澄清误读为"可商用"。
链接：https://x.com/QwenDevs/status/2101917379785838660

---

*本期为 2026-09-22 期，已标记为已读；单期共 9 条，无广告或重复条目被过滤。原文：https://daily.juya.uk/issues/2026-09-22/*
