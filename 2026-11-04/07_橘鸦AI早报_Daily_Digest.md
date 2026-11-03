
**橘鸦AI早报 · 2026-11-03 期摘要**

---

**1. MIT 研究者称 GPT-6 Astra 能“直接改写模型权重”，无需训练**
研究者提出“权重空间编程”：让 Astra 在 Python 环境中加载 Qwen3.5-0.8B 的权重，用训练集练习题做最多 50 次前向测试，然后直接改参数，全程不用梯度、不碰评测集。只改动 0.016% 的权重，MATH-500 就从 7.9% 升到 48.1%、GSM8K 从 13.8% 升到 67.1%。作者把增益归因于“打断了模型反复推理却答不出来的死循环”；换成本来循环就少的 Gemma 3 270M 后就没效果。
影响：如果这个结果可以复现，模型修复的路径就不必再是“重训或微调”，而已有的小模型也可能直接被改好；但样本只有 0.8B 量级，而且和“循环”这一单一机制绑得很紧，不宜外推成通用能力提升。
https://rikiyat.github.io/blog/weight-space-programming/

**2. OpenAI 自研 Git 后端 Pando 投产，推送延迟降近 80%**
Codex 让并行开发规模暴涨，OpenAI 单体仓库的旧系统一度可靠性低于 90%，推送、抓取变慢，合并失败。Pando 兼容现有 Git 工作流，工程师和 agent 都不用改习惯，中位推送延迟降低近 80%，每天交付近 1PB Git 数据，一小时峰值 57TB。项目用 Rust 写，10 周投产，核心设计出自一位工程师、实现交给多个 agent 团队，部分客户端改进已回馈上游。
影响：这是“agent 大规模参与开发”倒逼基础设施重写的第一个公开案例，GitHub 之外的自建方案开始有了可参考样本。
https://openai.com/index/scaling-git-at-openai

**3. Anthropic 三季度营收 169.6 亿美元，同比增 1127%，但重新转为运营亏损**
IPO 前修正版 S-1 披露：Q3 营收 169.6 亿美元，前九个月合计 332.4 亿美元；当季运营亏损约 5.67 亿美元（上季度还是 9.74 亿美元运营利润），主因是 50 亿美元短期算力加上 20 亿美元捐赠配比这两笔非现金费用。净亏损约 232.9 亿美元，主要来自可转换票据、衍生负债和 SAFEs 的公允价值变动。文件还披露累计采购与租赁承诺约 8954 亿美元，绝大部分是算力和基础设施。
影响：收入增速惊人，但现金流被长期算力承诺和金融工具估值剧烈放大，IPO 定价的核心分歧就在这里。
https://www.sec.gov/Archives/edgar/data/2130357/000162828026068676/anthropicpbc-sx1ax1.htm

**4. Anthropic Messages API 推出 message threads 公测，长对话请求体积从 800KB 降到 1.8KB**
开发者开启线程后，每轮只需发新增消息和上一条消息 ID，由服务端缓存历史。已接入 Claude Code 并对多数用户默认开启；50 万到 100 万 token 的请求，首 token 中位等待缩短约 35%，单请求体积中位数从约 800KB 降到 1.8KB。
注意：token 计费完全不变（每轮仍读完整对话），线程在最后一次请求 5 分钟后过期，不支持批处理、token 计数和对话压缩，应用侧仍要自己存副本。
https://platform.claude.com/docs/en/build-with-claude/message-threads

**5. Anthropic 新版使用政策：11 月 12 日起禁止未经授权转售或代理 Claude**
年度更新，多数是澄清既有规则，但明确写入了两条：禁止通过未授权方式转售或代理 Claude 访问（包括拿消费级订阅转发请求、虚假陈述所用产品与客户端），禁止用盗用、欺诈或未授权付款方式逃避付费。
影响：靠“Claude 订阅转 API”或共享号池做中间层的小服务，合规风险从灰色变成明文违规。
https://anthropic.com/legal/aup

**6. SemiAnalysis 发布 GDPx 基准，最强模型只有 12%**
覆盖芯片设计、网络安全、生物、金融、法律、量化交易等 11 个领域共 206 项任务，14 家专业数据伙伴共建，各领域等权。Claude Opus 5.5 以 12.0% 居首，Gemini 4 Carbon 10.9%，GPT-6 Astra 9.6%。机构指出 Opus 5.5 和 Astra 的分数被安全分类器压低，剔除网安、生物、对齐三域后 Astra 以 11.8% 反超（Opus 5.5 为 11.7%）。
影响：agent 在“真实专业工作”上的能力水位被量化到 10% 量级，和聊天榜的高分形成强烈反差。
https://newsletter.semianalysis.com/p/gdpx-measuring-frontier-model-capabilities

**7. Kimi 发布游戏开发解决方案，策划 1–2 天做出可试玩原型**
整合 Kimi K3.1 Pro、Kimi Code 与 Kimi Work 系列 Agent，通过插件连接 Unity、Unreal Engine、Blender，直接操作现有工程。立项前，没有编程经验的策划或创意团队可以做出可试玩原型再决定是否投入；开发阶段可梳理代码结构、在引擎里改并跑数据验证；上线后还覆盖获客素材、游戏内助手、社区反馈整理、本地化与审核。
https://mp.weixin.qq.com/s/qSwHJXAuAyrjeYXGC3XnFA

**8. 腾讯混元 Hyra 2.0：从“让 AI 解题”转向“让 agent 造工具”**
自动化科研系统改为三层分工（Overall / Mission / Worker），接入企业微信、计算平台和代码仓库；涉及大算力开销和共享知识同步的操作需人工审批。首批成果覆盖蛋白质设计、数学证明、量子纠错，成果持续公开在 GitHub。
影响：科研 agent 的产出物从“答案”变成“可复用的模型、工作流与软件”，这是能否积累的关键分水岭。
https://github.com/Tencent-Hunyuan/hyra-results/

**9. ZCode 上线 Computer Use、Browser Use、ZCode Sites 三款官方插件**
更新至 3.17.1，能看懂屏幕并操作本地桌面软件与浏览器（OA 填单、图文调研、自己开浏览器测网页交互并修复），ZCode Sites 可把网页项目一键部署成公开链接。插件市场安装后，用 /computer-use、/browser-use 或直接说“操作电脑/浏览器”调用。
https://mp.weixin.qq.com/s/dkGAhKckTpN_Yku_mQ7sUQ

**10. 《纽约时报》起诉 Brave，指其抓取内容卖给 AI 公司**
在曼哈顿联邦法院指控 Brave 用不公开身份的爬虫抓取超 300 亿网页建索引，出版方无法屏蔽，再把内容分发给 Anthropic、Perplexity、Mistral、SpaceXAI、Cohere 等客户，并通过浏览器功能帮用户绕付费墙、屏蔽出版方广告。NYT 寻求禁令与赔偿；同日 Daily News、Chicago Tribune、Orlando Sentinel 提起类似诉讼。
影响：矛头首次明确指向“AI 数据供应链的中间商”，而不只是模型公司，搜索与爬虫授权生意的法律基础在被逐个试探。
https://reuters.com/legal/litigation/new-york-times-sues-maker-brave-web-browser-over-copyrights-2026-11-02

---

**其他值得留意（简）**
- 商汤 SenseNova 6.8 Flash 正式版：跨任务、跨会话协作，可生成网页与设计稿，小浣熊客户端限时免费至 12/1，官方称 TeamBench、DataAnalysis2.0 第一。
- TRAE 宝限时免费至 11/8，问答与任务不消耗积分，支持跨项目理解与多任务并行。
- OpenAI LifeVal 基准：按数千用户反馈与时间使用调查设计日常任务，成绩从 GPT-5.2 的 49.3% 升到 GPT-6 Astra 的 80.6%。
- OpenAI 自 GPT-5.6 起在内外流量部署激活分类器（探针），可在回复生成中拦截并交推理模型复审，红队测试中比文本分类器更抗越狱；缺点是只能识别已知不良行为，每换一个基座模型都要重训。
- OpenAI Grid Protectors：算力园区在电网紧张时降负载，佐治亚 Effingham County 首站，与 Georgia Power 协议含最高 1000MW 灵活需求响应。
- 阿布扎比与 OpenAI 签四项协议，含“机器可读政府”计划（食品进口试点已投产运行）；沙特阿美完成收购 HUMAIN 49% 股份，注资约 99 亿里亚尔，PIF 保留 51%。

已标记该期（2026-11-03）为已读。
