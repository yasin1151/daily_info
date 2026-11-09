
HackerNews 今日 20 条新帖，筛出 10 条。整个人工智能板块的主线：Anthropic 发布新模型的同时把价格降了下来，Meta 在低成本执行层补位，而 Google 一方面推出专用硬件，另一方面在隐私方面出现重大争议。

---

### 1. Claude Fable 5.2 / Mythos 5.2：同一模型两种版本，价格反而下降
Anthropic 发布 Fable 5.2 与 Mythos 5.2，底层是同一个模型：Fable 带有网络安全与生物安全的防护性限制，面向所有用户；Mythos 去掉了这些限制，仅向通过审核的生命科学或网络安全机构开放。这一代生成速度快了 30%，价格降到 $8 / $40（每百万输入/输出 token），另有 2.5 倍速的 fast mode（$16 / $80）。官方给出的预发布案例包括：完成一项原本不可行的软件迁移、从零设计三台可工作的电子设备、解决两个黑洞物理开放问题，以及 30 小时内完成费马大定理的形式化证明。Artificial Analysis 智能指数给到 65 分，是目前最高。
社区最大质疑在对比基准：用户 shmoil 说，官方称“几乎所有项目都比 Opus 5.5 强”，他反问这是“在做 Opus 5.5 的防护性限制之前还是之后”得出的结论；bhu8 则从价格和速度变化推断“这其实就是 Fable 5.5，只是叫了 5.2”，并指出它可能就是 METR 报告里那个 Model 3，留了一手 5.5 没发。也有人嫌贵：“Too expensive for me”。
原文 https://www.anthropic.com/claude-fable-and-mythos-5-2
讨论 https://news.ycombinator.com/item?id=50429906 （828 分 / 495 评论）

### 2. Google 第八代 TPU 扩充：8tx 与 8i Max，一年发四个系统
8tx 主打硬件级机密推理，数据在芯片内即可处理敏感负载；8i Max 主打超大上下文窗口。两者配合已有的 8t / 8i，覆盖训练、推理、代理式负载全流程。Google 称 TPU 已是快速成长的业务，客户近 100 家，包括前沿实验室、量化交易公司、零售商和大学，并开始支持 PyTorch 与开源栈。
评论的措辞相当不客气。hi_hi 说：“典型的 Google。标题直写‘向每个开发者开放 TPU’，但对我这个开发者怎么用，零信息、零链接”；ur-whale 追问每个型号的 watt/token 和 $/token，以及和 NVIDIA 同价位产品的对比，帖子里也没有；qntty 问“Google 为什么不直接卖这个”。营销说“开放”，交付仍是云上配额，这是老问题。
原文 https://blog.google/innovation-and-ai/infrastructure-and-cloud/global-network/tpu-8i-max-and-8tx/
讨论 https://news.ycombinator.com/item?id=50432831 （91 分 / 10 评论）

### 3. Gemini 把个人 Drive 文件和邮件送去人工标注
一个 GitHub 仓库整理了相关证据，称 Google 会把 Gemini 处理过的个人 Drive 文件、邮件内容交给人工标注员人工阅读。这类条款在多数消费级 AI 服务里其实存在，但落到 Gmail 和 Drive 这两个承载了大量用户真实数据的存量产品上，性质不同。
评论区最有说服力的是具体经历。rustyhancock 说：他曾问 Gemini 某个公园改造的公众咨询流程，回答“异常贴合我刚收到的那封邮件”，而 Gemini 全程没提过它读过邮件；ninininino 的第一反应是“又一个尽快迁到本地 LLM 的理由”，随即被 ipsum2 纠正：“这不是本地模型能解决的问题，是 Google 把你的 Drive 数据发给真人”；reasonableklout 的反讽更能说明信任落差：“这太意外了，Drive 和 Gmail 几十年的信任基础，而且 Google 不是 OpenAI。”
原文 https://github.com/thisisme6598/gemini_files/
讨论 https://news.ycombinator.com/item?id=50429426 （264 分 / 50 评论）

### 4. Meta Muse Ember：给 agent“跑量”的那一层
Meta Superintelligence Labs 目前最轻、最便宜的模型，定位很明确：工具调用、编码子任务、路由、信息抽取、长文档解析这些 agent 每天重复的活。输入 $0.10/百万 token，AA 智能指数 36 分，和 Claude Haiku 5.5 (max) 同分，但每任务成本 $0.14 对比后者 $0.41。策略是搭配大模型 Muse Wonder 使用，“Wonder 规划，Ember 跑量”，两者差 8 分，成本差约 50 倍。弱点是知识量最低（AA-Omniscience 21.1%），好处是很少幻觉、倾向于拒答。在自带的 Muse Code 里跑编码 agent 反而领先 Haiku 5.5。
评论区被 Simon Willison 的鹈鹕测试占了：他按六档 reasoning effort 各画一只骑自行车的鹈鹕 SVG，结果“推理 token 越多画得越好”的规律第一次失效了——minimal 档（约 10 个推理 token）反而最好，只有 max 档等了 27 秒才画出腿搭在车上的正确版本。jolt42 总结：“鹈鹕是新的茶壶。”
原文 https://research.meta.ai/blog/muse-ember
讨论 https://news.ycombinator.com/item?id=50429024 （214 分 / 88 评论）

### 5. USPS 官方发布 ZIP Code 边界多边形，评论区关注价格
美国邮政首次官方提供全国 ZIP 边界数据，按季度更新，提供 GeoJSON 样例，按 Internal / Enterprise / Publication 三档授权。
技术上的价值有，但 HN 的反应几乎全在商业条款。untessela 一句“起步价 $10k”定调，foxfired 提议众筹买一次然后公开，uqual 指出许可协议本身就禁止这样分发。真正专业的反对来自 mzagaja（长期做地理数据）：“ZIP 从来就不是严格的地理边界。你在边界内，不保证你就是这个 ZIP，它只是被一堆该 ZIP 的投递地址围起来的空间。”biker142541 补刀：多边形在某些流程里确实有用，“但我没见过哪个场景值得为此付一大笔钱”。
原文 https://postalpro.usps.com/zcb
讨论 https://news.ycombinator.com/item?id=50431058 （348 分 / 171 评论）

### 6. 树莓派 5 16GB 涨到 $385，两年内从 $120 起
又一轮涨价：Pi 5 16GB 加 $80 到 $385，CM5 16GB Lite 起价 $375，500+ 键盘机反而没动（$410）。文章把时间线列得很清楚：4 月 4GB 以上全线涨，7 月 Jetson 模块涨最多 101%，10 月连 2GB 板也涨。根因是内存，Micron 说短缺至少持续到 2028，SK Hynix 说可能要到 2030 才缓解。
评论分成两派。vannevar 赌反转：“12 个月内价格会崩，因为我不认为数据中心泡沫能撑那么久”；paxy 认为归因错了：“不是用户愿不愿买的问题，Pi Foundation 也得跟大家一样按市场价买内存”；throwa356262 则半开玩笑地给了个正面解读：“这波混乱至少让人开始质疑，一个计算器是不是真的需要完整浏览器后端和 4GB 内存。”
原文 https://www.cnx-software.com/2026/11/03/when-will-this-stop-the-raspberry-pi-5-16gb-sbc-now-sells-for-385/
讨论 https://news.ycombinator.com/item?id=50428801 （268 分 / 228 评论）

### 7. E-means：同等 loss 下 k-means 快 10 倍
核心是把深度学习那套优化搬进 k-means：mini-batch 加指数移动平均，batch size 和步长由 scaling law 自动定，因此不需要调参；再加更好的初始化、死簇复活、余弦衰减和收尾阶段。结果是达到低于 Lloyd 的测试 loss，只需 1.2–3 个 epoch（Lloyd 要 25 个），GPU 上端到端加速 10–45 倍（对比 Flash-KMeans），CPU 上 8–15 倍（对比 Faiss）。速度和精度通常互相冲突，这里两个都拿到了。
实践反馈比论文更有意思。real_faxenoff 说把它移植进自己的 IVF 索引，“在 GPU 上拿到 146 倍加速”；wood_spirit 希望它进 scipy，理由是 Faiss 在很多环境里装不上；jlhawn 实测了自己球面网格松弛的 hobby 项目，结论是不适用——那个场景没有数据集，每个 Voronoi 胞的重心可以直接算出来，mini-batch 只是给精确值加了噪声。bashhq_r 则怀疑那套“自动超参数规律”是事后拟合的。
原文 https://e-means.github.io/
讨论 https://news.ycombinator.com/item?id=50429734 （230 分 / 13 评论）

### 8. CUI：用 C 写原生 UI 组件
纯 C 的立即模式（immediate mode）UI 组件库，示例干净，视觉上像把 shadcn 那套搬到了 C。作者同时踩中一个缩写：CUI 也是美国政府“受控非机密信息”的缩写，评论区玩了一阵梗。
真正有分歧的是评论里那场关于“C 该不该回来”的争论。wg0 的第一反应是“像 ShadCN，但是 C 写的，真的非常优雅”；piker 给了个当下很典型的论点：“如果能用 Fable 单独跑一遍内存安全检查，C 在编译速度上越来越说得通”；lpghatguy 直接反驳：“把内存安全交给模型太疯狂了，那对任何东西都不是可靠的安全保证。”comex 从另一个方向观察：他最近在监督下用 vibecoding 写了个 2.5 万行 Rust 项目，每次构建 15 秒，手写早就受不了了，但 agent 不在乎，因为它大部分时间在思考或跑测试，反而很少犯需要反复重建的低级错误。
原文 https://yappologistic.github.io/CUI/
讨论 https://news.ycombinator.com/item?id=50430621 （125 分 / 69 评论）

### 9. DeepX 宣称 5W 跑 100B 参数，评论区逐条检查
韩国 AI 芯片公司 DeepX 第二代芯片流片，LPDDR5X 存内计算（PIM），宣称性能提升 6.7 倍、功耗低于 5W 可跑最多 100B 参数。
评论区的核对比原文更有信息量。augment_me 列出四条：性能数字是模拟出来的；达到该性能需要 2.7 倍整体功耗，约 13.5W；编译器也是模拟原型，不是能直接替换 NVIDIA ISAAC 的东西；5W 指的是 4B 以下模型。NewJazz 补了最关键的一句：芯片设计目标是 20B–100B 总参 / 3B–20B 激活，也就是 MoE，“100B 稠密模型根本不在讨论范围内，有点误导”。PaulKeeble 按 80 TOP/s、150GB/s 带宽推算，prefill 大约只有消费级显卡（9070 XT）的十分之一。方向值得跟，数字先别信。
原文 https://www.eetimes.com/deepx-tapes-out-second-gen-chip-projects-6-7x-performance-gain-with-lpddr5x-pim/
讨论 https://news.ycombinator.com/item?id=50429545 （125 分 / 21 评论）

### 10. DBDelve：Rust + GPUI 的开源数据库客户端
Show HN，跨平台数据库客户端，用 Zed 的 GPUI 渲染，作者 shayan_abbas 全程在评论里答疑。定位是 DBeaver / TablePlus 的轻量替代，支持从这两个工具导入连接。
需求是真实的。dofm 说：“我找无痛的 MySQL Workbench 跨平台替代很久了，要给数据产品推荐的那种。Workbench 能干但太老，我会去试。”技术上被追问最多的是为什么不用 Tauri，作者回答：“DBX 用 Tauri，比 JVM 和 Electron 好，但拿不到 GPUI 这种原生框架的性能。”他也承认了 GPUI 生态的实际情况：Zed 团队上游 crate 一年多没更新，社区各自发布 gpui-ce / gpui-pre，他最后选了 gpui-kit。
原文 https://news.ycombinator.com/item?id=50427934

---

已标记 20 条全部已读。本轮未纳入：停车 App 附加费统计、Infineon 300mm 碳化硅、Payments Canada 实时支付、卫星过境影像站、Pigshell（2015 年老项目重发）、两个 Show HN 小工具、一条招聘。
