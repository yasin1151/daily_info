
**橘鸦AI早报 · 2026-11-23**

---

**1. OpenAI 首次公开内部评测指标「Perplexity」，提议行业设开发门槛**
OpenAI 首席科学家 Jakub Pachocki 发文《Perplexity and Intelligence》，把过去五年内部用来判断模型真实水平的指标「对数困惑度」公开了。数值越低越强：GPT-3.5 约 0.99，GPT-4 约 0.91；跌破 0.8 会出现网络安全与数学能力；约 0.76 开始能破解开放数学难题；他预计 0.68–0.7 区间还会有「未知的变革性能力」。他的警告是：AI 参与预训练算法研究后，数学领域那种骤然跃迁可能在深度学习重演，最早 2027 年预训练可能「雪崩式」加速，而现有安全监控（包括思维链监控）会跟不上。因此呼吁前沿实验室用 Perplexity 这类跨企业指标设第一个共同开发限制。Sam Altman 和 Greg Brockman 都转发背书。他本人也承认指标局限：数据集不可比、不直接对应任务、不反映思维链推理。
影响：这是 OpenAI 第一次把「内部进度表」摊到台面上，本质是抢先在监管和行业标准里定锚——先定义尺子，就掌握了话语权。
https://openai.com/index/perplexity-and-intelligence

**2. 蚂蚁开源医疗大模型 LingSante 3.1 Flash / air-VL**
Flash 版总参数 5600 亿、每 token 激活 250 亿，支持 100 万 token 上下文，官方称在 HealthBench Professional 等基准上高于 GPT-6 Astra。air-VL 版总参数 1240 亿、激活 55 亿，主打医学影像理解、报告生成和多模态检索。权重已上 Hugging Face 和 ModelScope，明确标注仅限研究与评估、不能替代医生。
影响：医疗是少数「数据壁垒高、评测标准相对硬」的垂直领域，蚂蚁同时放出大参数和轻量 VL 两个档位，明显是冲着医院私有化部署和论文引用去的。
https://huggingface.co/inclusionAI/LingSante-3.1-flash

**3. 马斯克披露 Tesla Reality View：车上跑约 10 亿参数 diffusion 模型实时生成画面**
回应 FSD v15 体验帖时，他说明特斯拉去年就有了接近像素级的 world model，车端是大幅缩小版，基于 Tesla Universal Vision Encoder（UVE）特征的 conditional mean-flow model。做法是从 UVE 特征 fork 一路，跑约 1B 的 diffusion model，对上一帧加噪再去噪，生成 8 张图、36 fps 的短片段。他承认受算力限制延迟偏高，说在 diffusion transformer 层交错 UVE 特征能削减约 35%。
影响：这是把生成式模型塞进车端实时闭环，而不是云端离线渲染；「用 world model 生成下一帧」这条路一旦跑通，对自动驾驶仿真和渲染管线的意义比渲染效果本身大得多。
https://x.com/elonmusk/status/2124458557525397780

**4. 马斯克预警：AI 行业明年可能严重资金短缺**
回复 Keras 创始人 François Chollet 时，他说让这种规模的算力设备通电、冷却并稳定运行极其困难。真正的风险是时间差：如果全行业从「开始支付算力成本」到「设备能稳定创收」的时间累计推迟几个月，仅营运资金就可能需要再投入数千亿美元，他反问这钱从哪来。Chollet 此前的原话是：要么认为 AI 基建已经结束、算力需求见顶，要么这就是难得的买入机会；GPU 现货价仍在涨，HBM 和 DRAM 到 2029 年产能基本订满。
影响：两个人都不是在唱衰 AI，而是在指认同一个脆弱点——现金流错配。上游产能锁死到 2029、下游变现节奏不明，这是明年最可能的叙事转折。
https://x.com/elonmusk/status/2124271725927903388

**5. OpenRouter 终止 3 家供应商合作，125 个端点被取消 ZDR 资格**
公告称安全研究人员发现平台上部分推理供应商存在数据处理问题，但调查未发现 OpenRouter 自身被入侵或泄露。处理结果是：终止与 3 家供应商合作、把 125 个端点移出 Zero Data Retention 资格、通知可能受影响的客户。起因是 Dragos 团队的测试——他们发出近 200 万条植入可追踪凭证的提示词，结果发现供应商被入侵、转售商留存客户提示词、隐私设置根本没被执行。OpenRouter 表示会把这类测试纳入常态检查。
影响：这是聚合层第一次被实测「穿透」出问题。用多供应商路由省钱的人要重新算账：便宜的那几家，可能正是把 prompt 卖出去或存下来的那几家。
https://openrouter.ai/blog/announcements/data-processing-incidents-on-inference-providers/

**6. 甲骨文：与 OpenAI 的基础设施合同已获全额资金支持**
本月初完成 200 亿美元融资后，甲骨文称合同所需资金已全部到位。双方计划在美国新增 4.5 吉瓦数据中心容量：德州阿比林园区（OpenAI 曾在此训练 Astra-6）接近完工，沙克尔福德县下一座吉瓦级园区已拿到全部许可，NVIDIA Vera Rubin 机架预计几周内交付。甲骨文还预计 FY2028 下半年自由现金流转正、FY2029 自由现金流超 300 亿美元。
影响：这条和上一条是同一枚硬币的两面——马斯克担心行业缺钱，甲骨文在用实际行动证明头部项目已经把钱锁定了。差距会体现在二线玩家身上。
https://www.oracle.com/news/announcement/oracle-statement-2026-11-20/

**7. OpenAI 团队预告 ChatGPT/Codex 桌面端「又一次重大更新」**
Codex 负责人 Tibo 发帖称团队已在准备又一次重大更新，并主动问用户昨天更新后还有哪些不足。他引用同事 Andrew Ambrosino 的公告，已上线的内容包括：面向 Plus 用户的 ChatGPT Space、全新更简洁的视觉设计、性能全面提升、threads 完全重建、pages 与 slides 明显变快、移动端可编辑 pages、Codex Remote 可靠性提高。公告称后续还有更多。
影响：更新频率已进入「隔天迭代」节奏，且负责人公开收集反馈——说明桌面端正在从聊天框向工作台转型，这是 Codex 与 Claude Code 抢地盘的正面战场。
https://x.com/thsottiaux/status/2124322968499282388

---

已标记该期（2026-11-23）为已读。本期只有 7 条，全部保留，无广告或重复新闻需要剔除。
