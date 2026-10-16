
HackerNews 精选 · 2026-10-17（前一日 top 10 新帖，按 HN 热度排序）

---

## 1. Claude 揭开了 ECDSA 曲线种子的来源之谜
原文：Claude reveals ECDSA curve origins（Anthropic Frontier Red Team）| 569 分 / 239 条评论
讨论：https://news.ycombinator.com/item?id=50122800 ｜原文：https://www.anthropic.com/research/ecdsa-curve-origins

摘要：NIST 标准椭圆曲线（P-192/224/256/384/521）的 seed 参数由 NSA 在 2000 年提交、来历不明，被密码学界怀疑了二十多年是否藏有后门（Koblitz/Menezes 著名的“A Riddle Wrapped in an Enigma”）。长期流传的说法是 NSA 的 Jerry Solinas 用一句幽默口令做哈希生成——这个说法是错的。Anthropic 一名员工让内部研究模型在不给任何线索的情况下重查，Claude 在半小时内发现：这些 seed 根本不是哈希，而是 1990 年代 C 标准库伪随机数生成器 lrand48 的输出，以 Unix 时间戳为种子，逐次抽 20 字节，P-256 抽到第 1842 次。方法是写扫描器逐位滑动、比对相邻块是否为同一 PRNG 的连续输出，并发现部分 seed 高位全 0（随机出现概率 1/5810）——这正是 lrand48 只返回 48 位状态中高 31 位的特征。Anthropic 强调这不是破解：参数生成方式简单可复现，反而让“NSA 故意植入后门”的说法更不可信。

社区原话：
- tptacek（安全圈知名人士，2 条回复）：“对整整一代 NIST 密码学阴谋论者来说，这是毁灭性的消息。”
- sweis：“为 srand48(time(NULL)) 戴了 13 年的锡箔帽。”
- EGreg：认为这是重大利好，比特币/以太坊社区可以放心为 P-256 上线校验 opcode 与预编译合约，不再担心基于 seed 的 NSA 后门（量子另当别论）。
- 真正吵起来的是 slowin 那条（17 条回复）：“Anthropic 想做这种事随时能做，但你我去做就会被拦……你把这个外推到更险恶的场景，就能看到模型厂商、他们的政府伙伴和公众之间的护城河在变宽。” 反方 comex、antics、Retr0id（“我本人就用 Claude 做过这个任务，没被拦，只是没做出来”）、st3fan（“GLM 5.3 或 Kimi K3 这种模型也能做”）普遍认为这个具体任务不会触发拦截；randomblock1 则认为主要是网络安全政策加 IPO 公关考量，不是“世界统治”心态。

为什么值得关注：罕见的“AI 直接为科学立功”的可验证案例（老证据 + 新方法 + 可复现结论）；同时把一个长期路线之争摆上台面——能查后门的能力被厂商护栏圈起来，只对少数人开放。

---

## 2. 美国 90% 的工作时间，落在 AI 基准测试覆盖不到的任务上
原文：A benchmark map of the US economy（Mercor Labs）| 361 分 / 311 条评论
讨论：https://news.ycombinator.com/item?id=50121179 ｜原文：https://www.mercor.com/research/labor-index/benchmark-map/

摘要：Mercor 把 29 个主流 AI 基准的 18797 条任务提示，逐条映射到美国 O*NET 的 923 个职业、22 个职业族上，做出一张“基准覆盖地图”。结论很刺眼：923 个职业里只有 208 个拥有至少 5 条基准提示覆盖的任务，22 个职业族里有 6 个连一条都没有；也就是说美国人 90% 的工作时间花在现有基准几乎不覆盖的任务上，因此完全无法判断模型在真实工作里到底多强。更关键的是覆盖并不随机：即便控制了 AI 暴露度，工资总额越大的职业被覆盖得越多——同属高 AI 暴露度，律师的任务覆盖充分，而法务秘书、法院书记员这类中等收入知识工作几乎无人测量。

社区原话：
- verdverm：人类做的很多事没有训练与 agent 所需的紧密反馈回路，所以既没出现“jobpocalypse”，生产力也仍然是长期年化 2% 那种曲线。
- qurren（10 条回复）：“我软件工程工作的大约 80%，是在调停‘利益相关方’之间的分歧。”
- 10111001（29 条回复，引爆全场）：引用原文后总结——“简言之，他们想让 AI 先拿下好工作。AI 不会来抢‘收垃圾’‘打扫厕所’这种活儿。我们软件工程师和律师最好现在就开始转行、并调整生活水准预期。” 反驳也很密集：robotresearcher 说“想不想的先放一边，我们现在就是做不了大多数需要物理操作的任务”；logicchains 认为编程数学能自动化是因为可以用编译器/定理证明器生成无限训练数据，投行和建筑业做不到；vanuatu 说这是把相关当因果，白领薪资本来就高。huijzer 分享自己刚从数据科学家转电工：“体力活开始一天挺难受的，但下班后的感觉比坐办公室好太多了。”
- smugglerFlynn 则从商业角度切入：他们并不“想要”什么，只是向企业销售焦虑、制造 FOMO 来拉客户，这也是为什么 B2C 产品毫无进展。

为什么值得关注：这是对“基准分数越来越漂亮=AI 真能干实事”这个叙事的定量反驳，可用于评估任何 AI 生产力宣称；评论区也罕见地把 HN 用户自身的职业焦虑摊开了。

---

## 3. Waymo 进军多伦多，实际问题变成“雪”
原文：Waymo in Toronto | 238 分 / 336 条评论
讨论：https://news.ycombinator.com/item?id=50118981 ｜原文：https://waymo.com/blog/2026/10/waymo-in-toronto/

摘要：Waymo 宣布在多伦多开展业务，博客后半部分用加拿大法语撰写（评论区认为是个好细节）。讨论几乎全部集中在气候与城市治理，而非技术亮点：落雪会让激光雷达回波四处反射，积雪盖住车道线后，司机们实际是在前车压出的车辙里排队行驶。有人贴出 Waymo 官方关于全天候驾驶与传感器加热除冰方案的文章，也有人指出 Waymo 要等到 2028 年才正式落地，中间正好有两个冬天的实测数据。

社区原话：
- hncbw02z5a（9 条回复）：“在雪里开车才是真正的考试。我做过一段激光雷达感知——落雪到处是回波；车道线被雪泥盖住之后，所有人就都开在前车压出的车辙里。很好奇他们怎么处理这种‘非官方车道’。”（随后被 yorwba 点名，指出该账号的大量发言都是“自称在一堆互不相关的技术领域有第一手经验”，套路太明显——HN 上常见的质疑方式。）
- scosman：FAQ 里写了有传感器清洁技术，2028 年才上线，两个冬天足够测试。
- fidotron：认为这正是激光雷达会被证明是死胡同的原因——它只是通往纯摄像头方案路上的临时使能技术。
- bix6：“Waymo 很棒。但我不想让它进我这座城。更多钱和更多数据给 Google，本地公交没有任何改善。”

为什么值得关注：自动驾驶的讨论重心已经从“能不能开”转到极端气候鲁棒性和城市政治（数据主权、公共服务替代），这是落地阶段的真实阻力清单。

---

## 4. Claude Code 团队怎么做代码评审
原文：How the Claude Code team does code review（Addy Osmani 等）| 188 分 / 178 条评论
讨论：https://news.ycombinator.com/item?id=50122951 ｜原文：https://claude.dev/blog/solving-code-review-at-anthropic/

摘要：官方披露：Claude 写了 Claude Code 自身约 90% 的代码；6 月到 9 月，合并的 PR 数翻了一倍以上，同时被 revert 的比例下降逾 40%；Anthropic 内部 monorepo 每日落地变更从 5 月的约 2500 条涨到 9 月的 3 万条以上。方法论是把“人是否读过代码”换成“这次变更可能怎么坏、该由哪个检查来抓”：评审左移、连续化（像写代码时的拼写检查），大部分问题在人看之前已由 Claude 与子 agent 修过一轮；一共六层检查加 rollback 兜底；目标是多数 PR 最多一个人类在环（可以是作者本人），并用 revert 率与事故率作为护栏——“you land it, you own it”。

社区原话：
- crooked-v（3 条回复）：“这大概就解释了那个有 5000 个 issue 的 GitHub 仓库，其中大约三分之一是以前行为的随机回归。”
- mixtureoftakes（4 条回复）：“每天合并 3 万个变更？不。就是不行。我们到底在干什么？我试图理解一下。”
- JackSlateur / devin / JamesSwift 一致炮轰“变更数/天”是无意义指标，和 LOC 一样：devin 提到此前那篇被戏称为“代码行数找到好公关”的文章；JamesSwift 讽刺——“所以你的意思是他们这周上线了 15 万个功能？还是说打了 149995 个性能/回归补丁、真正新功能 5 个？”
- vavkamil 质疑安全层：文中说安全问题“修掉或写个简短理由关掉线程”就算清掉误报，但关联的 claude-code-security-review 仓库 README 自己写明“未针对提示注入攻击做加固”——把它当作 AI 安全评审控制手段，这个前提就站不住。
- hyperpape：很惊讶团队现在还在说“90%”，是里程碑报腻了，还是增长到平台期了。

为什么值得关注：目前公开材料里最具体的“agent 大规模产码下的工程流程”一手描述，值得直接对照自己团队的评审流程；同时评论区的质疑（指标口径、安全评审可信度）也是这套流程必须回答的问题。

---

## 5. Anthropic 6 月被评到垃圾级最高档
原文：Anthropic assigned highest junk credit rating in June（FT）| 186 分 / 52 条评论
讨论：https://news.ycombinator.com/item?id=50122112 ｜原文（付费墙）：https://www.ft.com/content/5a310aee-f555-4266-874c-b1b4db20186d ｜免费镜像：https://finance.yahoo.com/technology/ai/articles/anthropic-s

摘要：FT 报道 Anthropic 在 6 月被 KBRA 给出“垃圾级中的最高档”信用评级。文中同时提到，Anthropic 与 OpenAI 的银行家一直在游说各大评级机构，希望两家在 IPO 时能拿到投资级评级，市场预期其 IPO 估值将超过 2 万亿美元。

社区原话：
- grumpymouse（6 条回复）引用原文：Anthropic 提交给 KBRA 的披露“遗漏了自由现金流和 EBITDA 等多项重要财务指标”，分析师只能基于假设自行估算，KBRA 因此改用“风险评分”而非传统完整财务模型——“再加上用的还是一家小评级机构，这个评级并不让人安心。”
- master_crab 认为不算新闻：KBRA 不是主要评级机构，债券买家根本不看它。
- nickysielicki（4 条回复）引用银行家游说段落后直言：“说白了就是打开公司债市场，好让养老金、人寿保险也能持有这些公司——于是每一个普通人、你爸妈，都在不知不觉中承担了这些公司和它们循环融资安排的风险。这很恶心。”他还指出 IPO 规则自互联网泡沫后已变，大量公司得以长期不上市。
- AnodicElegy：“先是 SpaceX，现在是 Anthropic。”影射评级机构为不得罪客户而给问题债务投资级的历史。
- Veliladon 泼冷水：到目前为止没有一家超大规模厂商表现出在乎借钱成本。

为什么值得关注：AI 资本开支叙事里最先被检验的一环是融资成本与信用，这条提供了具体评级事实；评论区的“循环融资 + 养老金接盘”担忧是当前 AI 泡沫争论最集中的表达。

---

## 6. JPEG XL vs AVIF，网页场景实测对比
原文：JPEG XL vs. AVIF for web use-cases（Jake Archibald）| 178 分 / 135 条评论
讨论：https://news.ycombinator.com/item?id=50120224 ｜原文：https://jakearchibald.com/2026/jpeg-xl-vs-avif/

摘要：JPEG XL 已在所有主流浏览器落地，作者做了带样本与基准数据的实测。结论：网页有损照片，AVIF 几乎总是更小——默认参数下最好的 JXL 比同类 AVIF 大约 15~25%，最高参数下差距缩到 6~20%（有零星个例 JXL 反超）；截图与插画 AVIF 明显更好，JXL 大 30~90%；需要无损时 JXL 占优。编码器影响极大：新编码器 jixel 通常比 libjxl 更小，只有细节透明度是例外。

社区原话：
- shmerl：AVIF 被忽视的优势是“基于容器”——将来 AV2、AV3 出来，站点不需要再经历一次艰难的适配，只需浏览器跟进。并补刀：AVIF 进浏览器很久了，但 GitHub、GitLab 这类大站至今仍有问题，因为站点代码里硬编码了已知格式白名单。
- quentindanjou：整体结论是“网上 AVIF 更好，除非需要无损就用 JPEG XL”。
- 0xy：AVIF 对“每帧透明区域会移动”的动画来说是救命方案，唯一替代是受 Safari 限制的 WebM。
- adzm 追问动画 AVIF 是否只有彼此独立的关键帧。

为什么值得关注：可直接落地的选型结论（照片 AVIF、无损 JXL、截图 AVIF），也顺带说明“浏览器支持 ≠ 站点可用”这个常被低估的普及瓶颈。

---

## 7. StarSkirmish Bench v0.2：让 LLM 用一小时写星际争霸 bot
原文：Show HN: Gemini 4 Argon plays StarCraft | 177 分 / 82 条评论
讨论：https://news.ycombinator.com/item?id=50118688 ｜原文：https://starskirmish.com/bench/v0-2/

摘要：这个基准让每个模型在自家官方 CLI 工具里用 1 小时写一个 C++ 神族 bot（基于 BWAPI 4.4.0 与 OpenBW），然后与人类手写的强 bot 和官方 demo bot 对战算胜率，每个模型跑 5 次。v0.2 加入了 OpenAI、Anthropic、Google、Meta 的新旗舰：GPT-6 Astra 第一，GPT-6.1 Sol 第二；Gemini 4 Argon、Claude Opus 5.5、Claude Fable 5.1 基本并列在 37~39 分。最关键的反差是：最强的人类手写 bot（Stardust、PurpleWave、BananaBrain）仍然碾压所有模型，最好的 GPT-6 Astra 对它们只赢 7%。胜率最强的预测因子是模型在那一小时里“找前 7 强 bot 打了多少练习局”——Astra、Sol、Gemini 4 Argon 很早就在自己还打不过的时候跑去练，Claude Haiku 5.5 等几乎从不练。Sol 性价比最好，单次运行成本约为 Astra 的十分之一。Gemini 4 Argon 的 run 间波动最大（最好与最差相差 18 分，Astra 只有 9 分）。

社区原话：
- BeaverGoose：应该拿 Pluto 来测——那是能赢顶级人类选手的神经网络 bot。
- qsort：“Astra 能超过 50% 简直离谱。模型是否被允许针对它要对战的那个特定 bot 练习？否则它面对强 bot 掉到个位数胜率该怎么解释？”
- jstummbillig：好奇他们怎么排除模型利用预训练里已有的 bot 代码（既然人类手写 bot 赢了，应该确实排除了，但仍是个谜）。
- m_w_：喜欢这里有一小时时限（其他基准很少）；反过来测“各模型需要多久才能对各级 bot 达到 50% 胜率”也很有意思。

为什么值得关注：少见的把“长时间 agentic 编码 + 自我迭代练习”量化对比的基准，而且暴露了“会不会主动去练”这种行为差异比分数本身更有信息量；同时清楚说明当前最强模型仍打不过人类手写 bot。

---

## 8. Big Fish：利用 OpenBSD 一个 37 岁高龄的内核漏洞拿下 root
原文：Big Fish: Exploiting a 37-Year-Old Kernel Bug in OpenBSD（Calif）| 155 分 / 44 条评论
讨论：https://news.ycombinator.com/item?id=50118977 ｜原文：https://calif.io/research/big-fish

摘要：Calif 披露，该漏洞可追溯到约 37 年前的原始 BSD 源码：共享内存 attach 计数器被定义为有符号 16 位 short，反复 fork 带共享内存记录的进程可把它推过 32767 上限并回绕为负数，从而引发 use-after-free 竞态，再配合另一个内核越界写，实现本地提权到 root。他们在开启 KARL/SMAP/SMEP、且不使用任何信息泄露漏洞的情况下拿到了本地 root。漏洞已由 errata 026 与 018 修复。

社区原话：
- phendrenad2：有意思的是，这个 bug 似乎在 1999 年 8 月 NetBSD 重写那段代码时被意外修掉了。
- ozereray1（5 条回复）：“一个 bug 能在审计最密集的代码库里存活 37 年，说明有些内核漏洞靠人工评审根本难以发现。你们觉得 fuzzing 或静态分析现实上能找到这一类问题，还是必须有人类去想那套利用原语？”
- shevy-java 挖苦：OpenBSD 首页现在得列出三个漏洞了。
- ewy1：吐槽正文之前先放一张 AI 生成的配图很劝退。

为什么值得关注：教科书级的“整数宽度 + 计数器溢出 + 竞态 → 提权”链条，而且发生在以安全著称、长期作为内存安全争论参照物的 OpenBSD 上。

---

## 9. 在越狱 PS5 上跑 llama.cpp（PS5LM）
原文：Llama.cpp on a jailbroken PS5: run any GGUF model natively on the console | 148 分 / 42 条评论
讨论：https://news.ycombinator.com/item?id=50122431 ｜原文：https://github.com/cobanov/PS5LM

摘要：开源项目 PS5LM 在越狱后的 PS5 上用主机 GPU 跑 llama.cpp，可直接跑任意 GGUF 模型（首个适配 Qwen 3.8），对外提供 OpenAI 与 Anthropic 兼容 API，并有一个为电视设计的界面——定位是“你的 PS5 跑模型，家里每台设备都能用”的私有模型服务器。新版还支持决策类模型（d1、Clef、OpenJev 等），走与 Ollaya 相同的 /v1/systemone 接口，返回带校准概率的类型化决策。

社区原话：
- shiftpgdn：理论上也能跑在 BC250 卡上——那是围绕 AMD “Cyan Skillfish” APU 做的前加密货币矿机主板，是 PS5 定制芯片的缩减版，eBay 上 150~200 美元还能买到。
- ThrowawayTestr：11.4G 共享显存，如果你没有独显，这东西就有点意思了。
- pwython：联想到 LLM 驱动的 NPC 会是标配。
- drewg123：好奇和 codex/claude 相比如何，估计慢很多、能力也弱不少。
- Rabbit504030201：认真建议别把项目主站放在 GitHub——PS5 不是历史古董，索尼随时可能下架，这类项目应该自建域名。

为什么值得关注：家用“闲置算力再利用”（游戏主机、退役矿卡）跑本地模型这条路线的代表案例，对成本与隐私敏感的自建场景是现实选项。

---

## 10. Home Assistant 未经授权扫描用户 secrets
原文：I never authorized an integration that scans my secrets（GitHub issue #49314）| 146 分 / 95 条评论
讨论：https://news.ycombinator.com/item?id=50124251 ｜原文：https://github.com/home-assistant/home-assistant.io/issues/49314

摘要：用户在 Home Assistant 2026.10.1 上发现内置的 pwned-passwords 集成会在未经授权的情况下扫描用户的 secrets（哈希后发往 HIBP），issue 中写道“这是相当严重的隐私侵犯……我从没授权任何集成或插件去扫描并把它们送出去，哪怕是哈希过的。这个机制也可能被能访问 Home Assistant 仓库的恶意行为者以多种方式滥用。我该怎么关掉它？”建议方案是改为 opt-in。维护者的回复（大意：“如果你因此要卸载并 fork……那就这样吧，毕竟是开源”）被社区普遍认为傲慢。该 issue 已关闭（标记为 more-info）。

社区原话：
- TavsiE9s：为难，但出发点我理解——这本就该是 opt-in。
- onionisafruit：“我另一个标签页正开着准备买 Home Assistant Green 开始折腾自动化。这让我有点犹豫。不是关于把哈希发给 haveibeenpwned，而是关于这件事在 GitHub 上得到的回应。”
- flanz_10 引用维护者回复后评价：“好小气的回答。‘你自己 fork 呗’。”
- Rygian（4 条回复）：怀疑该集成在欧盟可能直接违反 GDPR，进而让 HIBP 因“无合法依据摄取 PII”陷入麻烦；并指出“第一句回复是‘这不是侵犯隐私’，就说明在隐私议题上不专业，这种回答永远不成立”——对一个使命书写着捍卫隐私的家居自动化项目来说很令人担忧。
- janice1999：自己被“有毒的开发者”劝退，不再用 Home Assistant，并附上同一开发者在 NixOS 的相关争论链接。

为什么值得关注：一个“默认开启的隐私相关功能 + 维护者沟通翻车”的双重案例。对任何自建服务或隐私敏感产品来说，这条 issue 与它的回复都是可以直接拿来当反例的教材。

---

本期跳过：eBay 限制无线电设备交易（138 分，偏监管/硬件，信息量有限）、Dekton 材料科普（114 分）、/dev/null 开发者社交网络（110 分）、GifCities（2024 年旧帖被重新捞起）、Piramidal 招聘贴（无 HN 讨论）。20 篇新帖已全部标记已读。

采集说明：本机直连 news.ycombinator.com 超时被拦，评论与热度改由 HN 官方 Algolia API 抓取，文章正文来自各源站直接抓取（FT 与 Waymo 官博超时，相关部分依据讨论区内容撰写）。HN 不公开单条评论分数，因此引用按 HN 自身的顶层排序给出，并标注回复数。
