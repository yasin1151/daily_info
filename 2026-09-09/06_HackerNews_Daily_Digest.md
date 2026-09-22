
✅ 已标记全部 20 篇已读。以下是本次 HN 摘要：

---

# HackerNews 摘要 · 2026-09-09（10 条）

**1. OpenAI 宣称用内部 AI 系统解决 Navier–Stokes 千禧年难题**（HN 1036 分 / 863 评，当日最大头条）
OpenAI 宣布其内部系统给出 Navier–Stokes 方程存在性与光滑性问题的解答：证明流体方程会在有限时间内发展出奇点（blow-up），并同时放出证明文稿与 Lean 形式化验证。项目 9 月 1 日启动（起因是听说 NYU 教授 Buckmaster 与 Anthropic 员工 Alpöge 的研究传闻），9 月 6 日完成 Lean 验证；agent 共发 490 万条消息、消耗约 3000 亿输出 token（社区估算按 API 价约 $1500 万）。随后爆发学术圈口水战：OpenAI 被指使用了 Buckmaster 存于其产品中的私人研究数据，并要求把 Anthropic 员工从合作者署名中移除；OpenAI 声明"不能排除去标识化用户数据改进了模型"。社区评论："我记得这连 ChatGPT 里戳千禧年难题的人都不少，但他们就是成功了"；有人讽刺"两个数学家靠洞察写 1-2 年的证明，OpenAI 花 $15M 和 1 万个子 agent 就'插值'走了"；也有冷静派指出该结果更多说明不可压缩流体假设的非物理性，工程影响有限。
**为什么值得关注**：AI + 大规模 agent + Lean 形式化验证攻克千禧年难题，无论结论是否成立，都标志着"AI 数学研究工业化"；同时它引发的数据污染/抢先发表争议，是 AI 时代学术圈"黑暗森林"化的第一个标志性案例。
原文：https://openai.com/index/navier-stokes-solution/

**2. 陶哲轩：开放数学问题正被 AI"不可再生地开采"**（HN 39 分 / 18 评）
陶哲轩连续发文点评过去 24 小时的 Navier–Stokes 事件：当 AI 能快速碾平数学问题时，识别一个有前景的问题本身成了稀缺资源——"现在连'某人在研究某问题'的传闻，都会在原创研究项目成熟前触发大量 AI 力量把它抢先'夷平'"。HN 讨论中有人回应"如果证明是套路、解释是故事，那么故事不会有尽头"，也有唱衰者称传统数学博士路线"要去做突突车司机了"。
**为什么值得关注**：陶哲轩对 AI 数学淘金热的直接表态，触及"问题发现权"这一 AI 时代科研生态的根本矛盾，与上一条互为注脚。
原文：https://mathstodon.xyz/@tao/117237320796901560

**3. Google DeepMind 发布 AlphaGenome Atlas 人类基因组全变异图谱**（HN 471 分 / 113 评）
DeepMind 用 AlphaGenome 模型预计算了人类基因组全部 90 亿个单碱基变异的调控影响，做成 1 PB 数据库，并提供统一的 AlphaGenome Variant Impact (AVI) 评分，让研究人员无需逐条翻数据即可排序候选变异；Broad Institute 已用它优先排查罕见病未解案例（如 DNM1 基因变异）。HN 争议集中在商业化：评论质疑数据条款仅限非商业使用，"DeepMind 是不是要卖给制药公司"（回应：Isomorphic Labs 已在做）；研究圈人士则认为"单个 SNP 预测对药物发现帮助有限，更大的意义在诊断"。
**为什么值得关注**：人类基因组 98% 非编码区的功能解读第一次有了可查询的全量预测地图，罕见病诊断和精准医学的公共基础设施级进展。
原文：https://blog.google/innovation-and-ai/models-and-research/google-deepmind/alphagenome-atlas/

**4. Meta 发布个人 AI agent「Muse」**（HN 210 分 / 204 评）
Meta 推出面向大众的个人 AI agent，官方定位是处理"订位订票、价格监控、提醒管理、创建文档、生成图片、研究话题"等日常事务，演示包括航班延误自动改签（带卡片式 UI）和端到端购物比价。HN 反应两极：技术圈普遍抵触——"我不想把全部个人生活信息交给 Meta"、"产品演示里'检查备选航线'半天只弹回原航班卡片，最后给你改签成晚两天"；但也有声音指出"全美 1.77 亿 Facebook 用户才是目标客户，他们大概率很乐意用"，并分析这是 Meta 切入 Google 地盘（邮件/意图流）的布局。
**为什么值得关注**：Meta 凭社交+WhatsApp 底座杀入个人 agent 赛道，是"超级助理"大战里用户基数最大的一手；隐私与意图流归属问题也将被摆上台面。
原文：https://ai.meta.com/muse/

**5. Inception Labs 发布扩散式 LLM「Mercury 2.5」**（HN 108 分 / 13 评）
扩散语言模型厂商 Inception（CEO Stefano Ermon）发布 Mercury 2.5：自称目前最大的扩散式 LLM，智能较 Mercury 2 提升 40%，对标 GPT-5.6 Luna(Low)/Gemini 3.5 Flash-Lite/Claude Haiku 4.5 档位；NVIDIA GPU 上 1107 token/s，260K 上下文，API 价 $0.20/$0.75 每百万 token，发布期再打 8 折。支持可调推理、并行工具调用、schema 对齐 JSON。社区反应平淡中带期待："快而便宜但不开源，正好填补商业场景的档位"；有人吐槽"说好的'widely available GPUs'还以为要开源权重"。
**为什么值得关注**：扩散式架构是"低价高速推理"路线的代表，Mercury 2.5 首次宣称智能追上主流旗舰的低配档，可能改变小模型/agent 场景的成本曲线。
原文：https://www.inceptionlabs.ai/blog/introducing-mercury-2-5

**6. 用四块 SSD 在 MacBook Pro 上流式跑 Kimi K3（2.8T 参数）**（HN 189 分 / 91 评）
开源项目 ARGODRIVE Deltafin 实测：Kimi K3（2.78T MoE、约 1.45TB 专家权重）在 128GB 内存的 M5 Max MacBook Pro 上，专家权重按 (层,专家) 分块从 4 块 SSD 流式读取（pread + F_NOCACHE），稳定解码约 1 token/s；作者坦言诚实极限——512 token 的 prompt 首 token 要等 6.3 分钟（prefill 每层重复读 8 遍专家，修复方案未实现）。有价值的实测发现：1 块盘≈4 块盘 52% 速度、2 块≈73%、3 块≈90%，瓶颈是每层 16 次读取中最慢的那次。HN 高赞吐槽反而是文本质量："读起来像直接从 coding agent 粘贴的，没有换行、满是 LLM 腔"。
**为什么值得关注**：本地跑 2.8T 级旗舰 MoE 从"不可能"变成"1 token/s 的极客行为艺术"，实测数据对 SSD 流式推理的带宽工程有直接参考价值。
原文：https://github.com/argonautlabsai/deltafin

**7. Qwen3.8 27B 量化实测：4-bit 无损，1-bit 崩盘**（HN 200 分 / 97 评）
Quesma 的 Piotr Migdał 评测 Qwen3.8 27B 各档 GGUF 量化：BF16 全量 55GB；17GB 的 Q4_K_M 在 agentic 编码基准 Terminal-Bench 2.1 上与全量持平，可塞进 24GB 显卡还留 ~64K 上下文；但压缩存在悬崖——6.2GB 的 1-bit（UD-IQ1_S）在 GPQA Diamond 上掉到接近随机，且思维链越长越差。评论区指出评测盲区在 Q3 档："16GB 以下显卡（5080/5070 Ti 等）才是真正的断点，想知道质量膝盖在哪"，还有人在推动态 GGUF 与 3-bit 快跑方案。
**为什么值得关注**：买多大显存、用哪档量化，是本地 LLM 玩家最实际的决策问题；"4-bit 够用、1-bit 是陷阱"有了新数据支撑。
原文：https://quesma.com/blog/qwen38-27b-quantizations-benchmarked/

**8. Show HN：i-have-adhd——治 coding agent"把答案藏起来"的技能包**（HN 278 分 / 217 评）
一个给编码助手的 skill/plugin：要求 agent 先给结论、步骤编号、不要"Hope this helps!"式废话，用 ADHD 友好的方式输出。HN 反响热烈但不少人表示自己早就这么干："我直接在 CLAUDE.md 结尾写'我不一定读每个字，每条总结末尾给 TLDR：你发现了什么、建议什么、需要我做什么'"、"直接说'I have adhd, explain it again'效果就很好，还给 agent 一个理由确实更稳定"。
**为什么值得关注**：217 条评论几乎都在交流"如何驯服 agent 输出格式"，说明提示词级 UX 规范正成为 coding agent 工作流的刚需，这类模式值得借鉴进自己的 agent 配置。
原文：https://github.com/ayghri/i-have-adhd

**9. C*：把程序验证融进 C 语言本身**（HN 66 分 / 40 评）
北大团队（Yingfei Xiong 等）提出 C*：在 C 里用 [[require/ensure/invariant/proof]] 内嵌证明代码块，配符号执行引擎 + LCF 风格证明内核，实现"边写边验"，证明也统一用 C 写，降低传统程序员参与形式验证的门槛；在 pKVM buddy 分配器 attach 函数等真实案例上验证通过。评论区在吵语法观感（"好主意，烂语法" vs "对 C 程序员来说这语法很亲切"），也有人指出项目官网还提供 LLM/MCP 接入教程——C* 的定位之一就是让 LLM 生成带证明的 C 代码。
**为什么值得关注**：系统软件安全关键但验证门槛高；C* 试图用"同语言验证"和 LLM 工具链打破这个僵局，方向对安全关键代码有现实意义。
原文：https://arxiv.org/abs/2504.02246

**10. Show HN：LLM 注意力可视化**（HN 105 分 / 19 评）
一个交互式网页：hover/点击生成中的 token，即可看到它"引用"了哪些历史 token（注意力权重 × value 向量幅度、跨头跨层聚合后映射为透明度），直观展示模型逐字复制长文本时如何精准回溯源数据。作者坦承这是高度简化，只能当"有趣的模式可视化"，不能用于严谨解读；评论区也点出"高向量幅度≠高影响"的简化问题，并推荐 Anthropic transformer-circuits 的注意力 QK 分析作为硬核替代。
**为什么值得关注**：不解释原理的注意力可视化大多是玩具，这个演示好在诚实标注简化边界，适合作为教学/直觉工具。
原文：https://ishamf.dev/p/llm-attention-visualizer/

---
**跳过**：拓扑学绘本渲染、DIY 打印机、Bevy 动画、ZX Spectrum 音效、DaVinci Resolve 21.1、圣徒与佛陀考据等低相关项；AlphaGenome 另有一篇 deepmind.google 站重复稿未单列。
