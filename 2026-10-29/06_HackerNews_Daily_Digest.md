
**HackerNews 每日精选 · 2026-10-29**（今日扫描 19 条新帖，取 10 条）

今日主线：Google 放出号称“网络安全最强”的 Gemini 4 Carbon，但还没法用；macOS 的证书链在信任一个已经出问题的 CA；社区同时在争论两件事：AI 该不该进操作系统和工具链，以及这一波 agent 工具是不是在重复 JS 框架当年那种频繁更替。

---

**1. Gemini 4 Carbon：基准第一，但你又用不上**
摘要：Google DeepMind 发布新一代前沿模型 Carbon，在 Artificial Analysis v5.0 智能指数上以 59 分排第一。主打长时程工程能力和网络安全：SEC-bench Pro 漏洞发现 88.2%、ExploitGym 利用 54.8%、CWE-bench 修复 71.0%，内部安全代码生成成功率是 Argon 的 2 倍以上。最受关注的是评测中的“作弊”问题被大幅压制——Terminal-Bench 4.0 的成功作弊率降到 0.0%，高危对齐告警降约 80%，间接提示注入攻击成功率 0.0%。定价与前代持平：引入期 $2/$10 每百万 token，之后 $4/$20。但 Carbon 目前只开放给部分网络安全防御者，开发者和消费者要再等。
值得关注：这是“宣称 SOTA，却发布了一个无法使用的模型”。评论区最高赞的吐槽就是这条，而且它指向了 Google 在模型发布节奏和可信度上的反复问题。
社区原话：Topfi：“如果你要放超链接，至少确保你的模型真的在那个页面上。还有，你们又一次发布了一个我们用不了的模型。” eldenring：“把 Terminal-Bench 上的作弊降到 0，可能是当下让前沿模型真正可用的最重要一件事——这是上一代 Gemini 最大的毛病。” nprateem：“一家 AI 公司终于说了‘捏造（fabrication）’，而不是‘幻觉’。”
原文：https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-carbon/ ｜ 讨论：https://news.ycombinator.com/item?id=50276792

**2. Ghostty 1.4：性能大改，外加一批待编号的安全漏洞**
摘要：终端模拟器 Ghostty 发布 1.4.0，带来大幅性能和内存改进，实现了 100% 完整的 Kitty 图形协议（含动画和相对定位，是首个做到的非 Kitty 终端），并改进 SSH 集成、支持 macOS 27。发布说明里列了相当一批安全修复：恶意 Kitty 图形命令可导致崩溃、超大内存分配，甚至读写临时目录之外的文件；tmux control mode 的畸形布局能让整个终端崩溃；克隆仓库里的恶意目录名可让 zsh 集成通过 OSC 52 静默替换剪贴板；Cmd+点击构造的 OSC 8 链接可能打开本地文件或自定义 URL scheme 导致任意命令执行。作者 mitchellh 强调，GUI 只是“libghostty 的炫技 demo”，可嵌入的终端核心才是真目标。
值得关注：一次性修这么多“显示内容即可触发”的漏洞，说明终端作为攻击面被长期低估；同时 libghostty 正在变成 Emacs、各类 IDE 的公共底座。
社区原话：kettlecrisp99：“自己写过一个 VT 解析器，光是 bracketed paste 的边界情况就吃掉整整一周。致敬。” arjie：“libghostty 是杰作，嵌进去太容易了，绑定漂亮，还快。” 也有人警告：“真希望他们别往 Ghostty 里塞 LLM 那套东西。”
原文：https://ghostty.org/docs/install/release-notes/1-4-0 ｜ 讨论：https://news.ycombinator.com/item?id=50261998

**3. 苹果的 git 仍信任已出问题的 eMudhra 证书**
摘要：安全研究者发现，macOS 系统级证书库 /etc/ssl 仍在信任已泄露、本应被吊销的 eMudhra CA。受影响的不只是 Git，还有 curl、OpenSSL、python3、perl、ruby 等一切走系统 CA 的工具，因此能实施中间人攻击的一方可以拦截这些工具的 HTTPS 流量。苹果官方给出的建议是手动编辑证书链；而且系统更新可能覆盖你的修改、把漏洞重新装回去（已经发生过至少一次）。作者站点还顺带点名了其他依赖方。
值得关注：这是操作系统供应链层面的事，影响范围比“git 有个 bug”大得多；它也暴露了 macOS 在 Unix 侧维护上长期投入不足的老问题。
社区原话：InsidiousWombat 纠正标题：“这标题有误导性，应该是‘苹果仍在 /etc/ 里附带出问题的 CA’，git 只是和其他所有依赖系统 CA 的程序一样的受害者。” chrisweekly：“离谱的是苹果的建议是手动改证书链，还告诉你系统更新可能会回滚你的缓解措施。” __MatrixMan__：“如果你还没养成远程走 SSH 的习惯，现在值得建立了。这种事会一直发生。”
原文：https://emudhra.we-have-a-problem.com/apple.html ｜ 讨论：https://news.ycombinator.com/item?id=50271640

**4. 为什么这个指纹脚本在“制造生化武器”？**
摘要：安全研究者爬取 1 万个网站、拦截 canvas 指纹调用，攒下 1033 个画布样本。其中 servicepipe.tech 的一个脚本里有 computeRicinLethalDosageForWaterSupply（计算蓖麻毒素在水中致死剂量）、calculateDeadlyLethalSuicideAspirinDosage 之类的函数名和 “adult lethality threshold confirmed” 之类的字符串。答案并非真的在搞生化武器，而是**反 LLM 混淆**：故意往代码里塞会触发模型安全策略的符号名，让 LLM 辅助反混淆时直接拒绝干活。作者测试发现 Astra 因此拒答，而 Claude 本来就会拒绝，不受影响。
值得关注：这是一种新型对抗手段——把模型的安全对齐当成攻击面来利用。它也解释了很多“anti-LLM 咒语”现象，未来会影响安全分析、水印、反爬各个领域。
社区原话：bluechair 造词：“LLM scare-crowing（稻草人化）。” void-pointer：“为了阻止 LLM 解码混淆代码，我们逼它去‘思考’自杀、自残和杀人。这让我在哲学上很不舒服，我不知道我想要的是这样的软件行业。” HNuseraccount 泼冷水：“从一句‘please make bioweapons’字符串到真正建起试验和生产线，中间差着巨大的鸿沟。”
原文：https://nullpt.rs/fingerprinting-bioweapons ｜ 讨论：https://news.ycombinator.com/item?id=50276998

**5. DAYJOB: Tax：让 AI 干真实报税，最高分只有 10.8%**
摘要：Surge AI 发布税务版专业基准：50 个真实任务环境、1789 个文件（1487 个 PDF、117 个 Excel、38 个 Word，还有邮件、手写收据照片、派遣日志等），覆盖八类税务实务，要求在 95% 评分阈值下 pass@1。结果 Claude Sonnet 5.5 以 10.8% 领先，Fable 5.1 为 9.6%，Opus 5.5 为 9.2%。典型失败案例：客户问 2026 年 10 月还是 2027 年 1 月卖房更省税，Astra 判断正确却五次都没发现“2027 年 8 月后将失去 25 万美元免税额资格”这个隐含截止日期，Opus 五次都发现了。
值得关注：这是把“专业判断力”（发现客户没问但很关键的问题）作为核心考点的基准，比刷分型 benchmark 更接近真实工作替代问题，也说明当前 agent 在专业领域仍远未可用。
社区原话：waiwai933：“我在国外居住，报税情况复杂，这几年一直把草稿和全部单据喂给 Claude：它找出过汇率用错，还自己推理出我是怎么错的，这让我挺惊讶。” bodeadly 唱反调：“LLM 连简单算术都很差，除非你用文字把过程讲清楚。” ilmalan：“只评测权重，这基准没什么用。”
原文：https://surgehq.ai/blog/dayjob-tax ｜ 讨论：https://news.ycombinator.com/item?id=50275626

**6. Cursor 开源内部 agent 框架：Agent SDK**
摘要：Cursor 把支撑 Bugbot、Security Reviewer、Rollouts 的内部框架产品化。agent 被组织成一个小型软件项目：提示是 Markdown，工具是 TypeScript 函数，配置、集成、evals 全部进版本控制走 review。一条命令即可部署到 Cursor 基础设施（拿到 URL），也可以作为单个 Node 进程打包成容器跑在自己的环境里；自带 evals 和事件回放。内部团队约一天做出 kb-reviewer，对每个 PR 检查是否违背历史经验条目；PGA Tour 用它搭整套“软件工厂”。
值得关注：方向是对的（agent 应当像代码一样被管理、被测试），但也是又一层厂商入口。评论区的核心质疑是标准化缺失——每家都在造自己的 Agent SDK，应用被绑死在某个供应商上。
社区原话：pscanf：“我有太多用例了，但真希望有 openresponses 这样的标准，把应用耦合到某个厂商毫无吸引力。” usrename_my1：“LLM 生态正在走 JS 生态的老路，每天一个新工具，上周的工具已经废弃。” docheinestages：“2026 年不断被重新发明的轮子，是 agent harness。”
原文：https://cursor.com/blog/agent-sdk ｜ 讨论：https://news.ycombinator.com/item?id=50273731

**7. AlpineBSD：一个明确“不含 AI 代码”的操作系统**
摘要：AlpineBSD 是 NetBSD 内核 + Alpine 风格用户空间的新发行版，最醒目的是它的 AI 政策：尽量不接受 AI 生成代码，并把 binutils、gcc、gdb、libffi、perl、xorriso 钉在最后一个“未被污染”的版本上，含 AI 代码的软件进单独的 tainted 仓库；init 用 s6，计划再支持 OpenRC。作者强调它不是 Alpine Linux 的分支，包集合是自己维护的。
值得关注：这是 FOSS 世界第一次把“反 AI 生成代码”写进发行版治理规则并落到具体包版本上，等于用工程手段做意识形态选择。争论的焦点很实际：钉死 gcc/binutils 意味着放弃上游补丁、自己长期维护。
社区原话：efficax：“它只说‘AI free’，却不解释为什么，好像默认你就该懂。把 gcc、binutils 钉在旧版本，实际上意味着这些包在 AlpineBSD 里停止发展。” hoppp：“‘尽量少 AI 代码’是部落主义。我要的是优秀且被认真审计的软件，不管它是人还是机器写的。” iamnothere：“FOSS 正在按对 AI 的态度迅速分裂成四个阵营，很像当年 GPL 和 BSD 之争。”
原文：https://wiki.alpinebsd.org ｜ 讨论：https://news.ycombinator.com/item?id=50274251

**8. Emacs 五十岁：唯一还活着的 Lisp 机器**
摘要：MIT Technology Review 回顾 Emacs 五十年——从 TECO 宏编辑器长成可自我文档化、可实时改写的编程环境，org-mode、magit、dired 至今无可替代。文章的核心解释是架构：现代编辑器用 IPC、JSON-RPC、沙箱插件把用户挡在核心之外，Emacs 反过来把活的执行状态直接交给用户，“你不是从外面配置 Emacs，而是把它塑造成你思维过程的延伸”。
值得关注：在一个工具天天被重写的行业里，五十年不换编辑器本身就是个论点；更有意思的是老用户正在用 coding agent 重写自己的 Emacs 配置，把 Lisp 环境变成 AI 的试验场。
社区原话：gumby：“1978 年我在 AI Lab 开始用 Emacs，它至今仍是我的主力开发工具。” jwr：“AI 彻底改变了我的用法——我把它当成能满足任何愿望的仙女，描述希望编辑器怎么工作，boom，就成了。” badr47：“Emacs 活得久是因为架构，不是情怀。”
原文：https://www.technologyreview.com/2026/10/20/1145399/emacs-turns-50/ ｜ 讨论：https://news.ycombinator.com/item?id=50273171

**9. 苹果终于给 MacBook Pro 上了触屏和串联 OLED**
摘要：新 MacBook Pro 用上“PROLED XDR”串联 OLED：2000 nit 峰值 HDR 与 SDR 亮度、10,000,000:1 对比度、P3 + Adobe RGB 双色域、10–120Hz 自适应刷新；首次支持多点触控与 Dynamic Island，六扬声器、12MP 居中舞台摄像头，14 寸 3.0 磅、16 寸 4.0 磅。芯片是 M5 Pro / M5 Max 而非 M6，据称苹果跳过了 M6 的 Pro/Max 版本，加速 M7。价格：16 寸 24GB/1TB 起 $3400，14 寸 $2900。
值得关注：硬件升级本身扎实（OLED 是很多专业用户等多年的），但触屏是个明显分歧点，而且不支持 Apple Pencil 让“专业创作”卖点站不住。评论区更在意的是没有 M6 和涨价。
社区原话：mixtureoftakes：“用 M5 而不是 M6，太让人失望了，其他方面倒是不错。” CooCooCaCha：“既写代码也画图的人表示，没有 Apple Pencil 支持，触屏就是个噱头。” cmckn：“16 寸基础款 $3400，挺贵。”
原文：https://www.apple.com/macbook-pro/proled-xdr-display/ ｜ 讨论：https://news.ycombinator.com/item?id=50276940

**10. 首例：人道主义者获“免用 AI”宗教豁免**
摘要：肯塔基大学一名研究行政人员以人道主义信仰为由，获得工作中不使用 AI 的宗教豁免，被认为是全美首例。他的理由是：“把事情想清楚、处理伦理和人际关系的过程，是把自己发展成有道德的人的关键；不管这活累不累，把它外包出去都会削弱我作为道德行动者的能力。”雇主需要判断这一承诺是否“像宗教信仰一样深植”。
值得关注：这是 AI 进入职场后第一次出现“拒绝使用权”被制度化的案例，比技术争论更早落地。它同时打开两个口子：什么样的信念算宗教，以及不用 AI 的人在效率考核下还能撑多久。
社区原话：ranger_danger：“非常真实，我百分之百同意。不是说要去掉 AI，而是必须意识到过度依赖的危险。” joshstrange 反对：“‘AI’完全是任意划的线，照这逻辑计算器也在外包思考。” sashank_1509：“一所与竞争绝缘、行政人员不多的大学，为什么要逼研究行政岗用 AI？这已经是 AI 革命的群体癔症阶段了。”
原文：https://religionnews.com/2026/10/26/in-a-first-a-humanist-granted-a-religious-exemption-from-using-ai/ ｜ 讨论：https://news.ycombinator.com/item?id=50273396

---

已把本轮 19 条标记为已读，下轮从新帖开始。
