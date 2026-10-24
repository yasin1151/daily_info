
# HackerNews 日报 · 2026-10-25

今天 HN 前 20 条新帖里，热度几乎全被两件事吃掉：一条"AI 在科技业外没有回报"的宏观图表帖（417 分、400 条评论），和一场正在扩散的 brotli 压缩库 RCE（263 分）。以下是按分数排序的 10 条，附社区原话。

---

## 1. AI 在科技业之外看不到任何回报（417 分 / 400 评论）
Apollo 首席经济学家 Torsten Slok 的 Daily Spark 图表帖：AI 相关资本开支与收益高度集中在科技板块，非科技行业的生产率、盈利数据里几乎找不到 AI 的痕迹。帖本身很短，但它成了 HN 本周最大的战场。

**为什么值得关注**：这是"AI 资本开支能否被非科技行业消化"这个问题的数据侧版本。HN 讨论里最有价值的不是结论，而是从业者给出的解释分歧面。

**评论声音**
- **mbil**：AI 目前最明显有用的是写软件，"软件可以被自动验证"——验证闭环才让模型迭代到可接受解；写给人看的文档则要人仔细审，"审一份貌似合理但细节错误的材料，收益基本被抵消"。
- **jerf**："还在说 AI 一无是处的只剩几个老顽固"；真正的问题是这轮建设潮的结局，而天天用多个 session 的人不会惊讶它没立刻改造一切。
- **toomuchtodo** 贴了关联数据：另一份调查显示只有 13% 的公司看到真实回报（10 月 HN 另一帖）。
- **jstanley** 只留了一句 1987 年的老话："You can see the computer age everywhere but in the productivity statistics."
- **bob1029** 反向吐槽：科技业内部也没拿到回报——面向客户的场景有胜绩，研发团队反而是最大的问题。
- **eek2121** 泼冷水：LLM 幻觉是架构性的，"再怎么自我检查也解决不了"，别类比电力和轮子。

原文 https://www.apollo.com/wealth/insights-news/insights/daily-spark/no-signs-of-ai-payoff-outside-the-tech-sector
讨论 https://news.ycombinator.com/item?id=50224463

---

## 2. Node2Shell 演化为 HTTP2Shell：brotli RCE 波及大量 HTTP 库与应用（263 分 / 131 评论）
Aikido 披露 CVE-2026-111497：Google brotli C 压缩库存在缺陷，且是**双向**未授权 RCE——恶意服务端可以打客户端（只要客户端接受压缩响应），恶意客户端也能打服务端。因为几乎所有 HTTP 栈都带 brotli 解码，受影响面从 Python 的 `brotli` wheel 扩散到 Node、Bun、Envoy、Git for Windows，甚至自带 git 的 Codex 桌面端。

**为什么值得关注**：不是某个框架的问题，而是"网络路径上的 C 压缩库"这一层的问题。修复窗口内，任何拉包、拉仓库、访问第三方 API 的动作都是攻击面。

**评论声音**
- **aftbit** 给出实测：他花约 0.30 美元的 DeepSeek API 额度就写出一个劫持 PyPI 安装的 MITM 代理，并贴出可用的 SHA 固定升级命令——即"可利用性很高，别等"。
- **perching_aix** 点名：Git for Windows 最新版 2.56.0.windows.3 仍受影响，修复只在快照版，周一才可能发 .4；Codex 自带 git，风险更高。
- **TacticalCoder** 质疑补丁质量：加了几个 `isSafe?` 之类判断，"像给一头会溢出的 C 猪涂口红"。
- **netsharc** 骂命名："叫 HTTP2Shell 的人没用任何智能，人工的也没有"——名字既宽泛又不描述真实问题。
- **davedx / _flux**：该把安全关键路径上的 C 换掉；Dropbox 的 rust-brotli 是可直接替换的实现（代价是慢一些）。
- **saltcured**：这也是他坚持用发行版打包的 Python 与核心库的原因——"LLM 泡坏的世界里，这个取舍对小站点仍然更划算"。

原文 https://www.aikido.dev/blog/python-packages-vulnerable-node2shell-brotli-cve-2026-111497
讨论 https://news.ycombinator.com/item?id=50219177

---

## 3. Roku 把开发者仓库从 GitHub 迁到 GitLab（233 分 / 156 评论）
Roku 官方博客宣布开发者仓库整体迁移到 GitLab，但通篇没给出明确原因——这恰恰是评论区最不满的点。

**为什么值得关注**：GitHub 近期连续故障 + 微软信任问题，正在把"代码托管"从默认选项变成一个需要论证的决策。这是大厂第一次公开用脚投票。

**评论声音**
- **tangotaylor**："真希望他们漏点内幕，说清到底为什么搬。"
- **skullone**：搬完了 README 还写着"欢迎来到我们的 GitHub 仓库"。
- **neya**："好，我希望所有人都这么干，我想看微软倒掉"——理由是 GitHub Desktop 在 macOS 上"不认 no"，装一堆助手进程，像灰色软件。
- **bob1029** 更冷静：GitHub 故障的主因不是工程师在写 AI 代码，而是所有用户的工作流速度都变快了、对系统压力全面上升，"哪个平台都不会长期保持草绿"。
- **stefan_**：GitLab 要好起来，得先把"功能打勾狂潮"时期堆的 Secure/Deploy/Operate/Monitor/Analyze/Auto DevOps 全删掉。

原文 https://blog.roku.com/developer/gitlab-move
讨论 https://news.ycombinator.com/item?id=50222622

---

## 4. Goose：aardappel 的新编程语言，用"多栈"替掉堆和 GC（168 分 / 131 评论）
Wouter van Oortmerssen（FlatBuffers、Lobster 作者）发布 Goose。核心设计是把内存当栈来管：编译期分析出程序同时"活着"的可变长数据最多 N 个，就开 N 条虚拟栈，每条可长到 2GB 但只占实际用到的物理内存；配合相对引用与内置的二进制结构校验，实现数据结构的直接内存映射和网络数据零拷贝。

**为什么值得关注**：它不是又一门语法糖语言，而是对"堆分配 + GC/借用检查"这条主线的一次结构性挑衅。而且 Carmack 已经在转它的推文。

**评论声音**
- **bobbydigitales** 引 Carmack 原话："自动分析、多数据栈、可调整字段，把这从'很多活可以这么干'变成'基本什么都能这么干'……'解析'文件和网络数据常常比需要的慢 100 倍。"
- **malisper** 追问关键边界：哈希表里随机增删字符串这种"任意数量的可变长值"怎么表示？固定条数的栈似乎不够。
- **vanderZwan** 代答：做活跃性分析，"睡着的"变量的栈可以复用，因为线程间不共享内存、也没有数据竞争。
- **pixelesque** 挑基准：bench/cpp 下所谓"手工优化"的对照代码缺少 `reserve()` 等基本操作，看着并不像优化过的。
- **mi_lk** 提醒：Carmack 那句话是在回复一条看不到上下文的推文，别过度解读。
- 作者 **Aardappel** 亲自下场："顺便说，语言是我做的，AMA"，并贴出 repo。

原文 https://aardappel.github.io/goose/ ｜ repo https://github.com/aardappel/goose
讨论 https://news.ycombinator.com/item?id=50224100

---

## 5. GPU-unlock：用内核模块解锁 Nvidia 30 系的 FP/BF16 发射率（163 分 / 59 评论）
一个 Linux 内核模块，把 GA102/103/104/106（RTX 30 系）的 FP/BF16 指令发射率解锁到专业卡水平：写入 speed selector（SS0 `0x88888888`、SS1 `0x8`）并在官方驱动绑定前做 FLR，不需要 UEFI 应用、也不用每次驱动更新后重新打补丁。实测 3090 Ti 在 450W 下 BF16 GEMM 从 87.5 涨到 157.4 TFLOPS，TF32 从 42.6 涨到 82.6。

**为什么值得关注**：消费卡被软件砍掉的算力被找回了一半，对本地推理/训练是直接的钱。代价是功耗和散热余量，以及"依赖固件漏洞"这件事本身。

**评论声音**
- **Tiberium**：自己复现了，"结果是真的，相当惊人，虽然有点冒险——它靠的是利用固件里的经典栈溢出 + ROP"。
- **jacquesm**：真，但要注意：卡会跑得更热；部分卡要吃到 450W 才拿到完整收益，远超原装散热设计。
- **superkuh** 纠错标题：不是解锁 16 位算子，而是把被减半的 FP32 放出来；且目前只看到 3090/3090Ti 有实际报告。
- **Scene_Cast2**：只对部分负载有用，训练常常是显存带宽瓶颈；功耗影响还待观察。

原文 https://github.com/Zagitta/gpu-unlock
讨论 https://news.ycombinator.com/item?id=50219700

---

## 6. 为什么 AI 生成的语言这么难懂？（144 分 / 141 评论）
一篇 cs.CL 论文用心理语言学特征做量化对比：九款前沿/准前沿模型相比人类写作，都更爱用"无生命主语 + 有生命动词"、更多低频 n-gram；在对话场景里多数模型还有更长的句法依赖、更多名词堆叠、更多缩减式宾语关系从句。作者给出的解释是：人类语言为"沟通成功"优化，而 AI 文本被优化去服务数学、代码、推理，压力转向**信息密度**。他们用长度惩罚微调模型做验证，确实让语言进一步偏离人类习惯。

**为什么值得关注**：把"AI 味"从主观感受变成了可测量特征，而且给出了成因假说——这比"感觉生硬"有用得多。

**评论声音**
- **paid_dot_expert**：AI 文本"活在自己的世界里"，知道意思但只会用 buzzword 和 slop 表达，补一句"ELI5"通常能治好；他用的 Opus 5.5。
- **silverFork** 唱反调："我理解 AI 写的东西比理解人写的更容易，我的脑子大概被计算机调过频了。"
- **codeulike** 只问了一句："他们说的 low frequency n-grams 到底指什么？"——也代表了一批读者的困惑。
- **skeledrew**：我没觉得难懂，所以真问题应该是"为什么有些人觉得难懂"。

原文 https://arxiv.org/abs/2610.29162
讨论 https://news.ycombinator.com/item?id=50223647

---

## 7. 小程序与小编程语言（121 分 / 45 评论）
Dave（ratfactor）的短文，从自己写 Forth 的反馈讲起，列举了一批极小实现：46 字节的 Forth（Philippe Brochard）、Luke Jackson 那个只有几行的 DOM diff 库 ijk、Arthur Whitney 一页纸一下午写出来的 J 解释器"Incunabulum"。

**为什么值得关注**：这是对"代码量与可理解性"关系的直接论证——200 行的东西你会读，20,000 行的不会。适合当周末读物，也适合用来反驳"必须上框架"的默认反射。

**评论声音**
- **agentultra**：尺寸编程很好玩，想入门去看 demo scene 和 lovebyte；他业余在写"尽可能小的事件存储数据库"。
- **asplake**：有没有基于类型化 λ 演算的极小 ML 系语言，或者更小、更 Lisp 但柯里化的？
- **forinti**：这就是 1980 年代计算机杂志的魅力——每月一个小项目（分形、碰撞星系、小游戏），小到你可以手敲进去。
- **WillAdams**：惊讶 Oberon 没被提到。

原文 https://ratfactor.com/cards/pl-small
讨论 https://news.ycombinator.com/item?id=44200797

---

## 8. Dan Luu：我们应该把软件做得更有野心（35 分 / 23 评论）
文章借 Michael Malis 的 pgrust（用 Rust 重写 Postgres，并用 LLM 生成 Lean 证明来验证 C 与 Rust 行为等价）论证：当下最该做的是"以前不敢做的项目"。它同时承认大多数 AI 重写项目是 slop——但 pgrust 在测试中顺手挖出了 Postgres 的真 bug（SP-GiST 数值错误、JSONPath 格式缓存导致错误结果、pgcrypto、字典加载器多处内存安全问题、money 溢出）。

**为什么值得关注**：这是对"AI 时代还要不要做长期硬工程"最具体的回答，而且它的证据是上游 bug 修复，不是 benchmark 数字。

**评论声音**
- **mindcandy**："我看到太多'我写了二十年代码，现在只剩给 AI 下指令'，太少'我写了二十年代码，最近几个月靠 AI 做出了以前根本不敢想的东西'。抱怨无聊比重新上强度容易得多。"
- **Supermancho** 引文中一段：用 AI 加速某个流程，往往塞进一堆只对测试过的场景过拟合的烂代码，"性能上不通用，未来也难维护——我司几百个应用就这么硬掉了"。
- **malisper** 本人补充技术路线：写了把 C 和 Rust 编译到 Lean 的编译器，已为约 7 万行 C 证明行为等价；瓶颈是每次增量所需上下文。
- **anonymous908213** 泼冷水：就在昨天 pgrust 因作弊 benchmark 被 ClickBench 除名——"正因为这些重写项目大多是 slop，我不查就信才是坏选择"。
- **happytoexplain**：让人难受的是很多人无法同时容纳"AI 对我有正面感受"和"它确实造成别人的痛苦"。

原文 https://danluu.com/ambitious/
讨论 https://news.ycombinator.com/item?id=50225695

---

## 9. 陶哲轩：oai-math-revised，一个修订 OpenAI 数学写作的社区 hub（27 分 / 21 评论）
陶哲轩在自己博客上介绍 oai-math-revised：一个把 OpenAI 近期数学成果的 write-up 拿出来，由社区共同修订、澄清、核验的协作空间。

**为什么值得关注**：形式验证已经能给出"结果为真但没人读懂证明"的状态，数学界正在被迫发明新的协作与署名机制。而 HN 的反应，基本是对"给公司免费干活"的本能抵触。

**评论声音**
- **1293475**：作者们都在计算数学和 AI 领域，"这是 OpenAI 仓库的软实力版本，让你免费打工，不如叫 OpenOpenAI"。
- **vishna**："OpenAI 版的从博士生那里拿无薪实习。"
- **sdenton4** 提了个有用的概念：数学需要一个新状态"Verified-but-Unproven"——形式验证为真但没有连贯证明，用来给人/机器正确分配credit。
- **bemtevi** 更激烈："我绝不会参与。把机器生成的证明翻译成人话是一种可鄙的时间用法"，数学的目的是"通过人类共享的实践获得对世界的精确理解"。
- **sebzim4500** 反问：这对 OpenAI 有什么好处？头条已经拿到了。

原文 https://terrytao.wordpress.com/2026/10/24/oai-math-revised-a-community-hub-for-revising-openais-math-write-ups/
讨论 https://news.ycombinator.com/item?id=50222283

---

## 10. 自由软件是一场彻底的失败（8 分 / 6 评论）
Jake Bauer 2021 年的旧文（今年 8 月更新）重新被翻出来。作者自称曾是 GPLv3 布道者，现在认为自由软件运动"在理念上是烂摊子，阻碍协作，法律上无效，让开发者更累，对用户毫无实际好处"，明确把 Copyleft 的"自由软件"和宽容许可的"开源"区分开来打。

**为什么值得关注**：分数不高但立场少见——它不是反 FOSS，而是从运动内部拆 Copyleft 的合法性叙事。适合和最近一连串供应链事件（见第 2 条）放在一起读：许可证保护不了用户，补丁速度才能。

**评论声音**（该帖仅 6 条，讨论较薄）
- 作者自己在文首加了防御性说明：请批评观点，而不是揣测我的人格和经验。
- 讨论主要集中在"Copyleft 是否真的阻碍了协作"与"许可证能否约束云厂商"两点。

原文 https://www.paritybit.ca/blog/free-software-is-an-abject-failure/
讨论 https://news.ycombinator.com/item?id=50226261

---

**顺手扫到但没展开**：bbtree 号称最快有序 map（22 分，页面是纯 JS 渲染抓不到正文，评论区有人指出其亮点是把跨核一致性流量纳入设计）；SpeedCrunch 1.1 计算器发布（45 分）；Argus 开源 agentic 安全运营平台（19 分）。

20 条新帖已全部标记已读。今天如果要只做一件事：把你手上依赖 brotli 的组件（含 git for Windows、以及任何自带 git/HTTP 栈的客户端）先升掉。
