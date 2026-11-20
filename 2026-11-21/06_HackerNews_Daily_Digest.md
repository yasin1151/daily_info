
# HackerNews 精选 · 2026-11-21

抓取 20 条新帖，按 HN 分数取前 10。今天的绝对主线：**广义黎曼猜想在同一天被两个人以两种方式"证明"了**。

---

## 1. 广义黎曼猜想被"双杀"：人类手稿 + Anthropic 的 1740 万行 Lean 证明
🔗 https://math216.wordpress.com/2026/11/20/hurried-announcement-alessandro-masullo-grh/ （1297 分 / 599 评论）

Ravi Vakil（斯坦福代数几何学者）在 AMS 理事会上匆忙发帖：Alessandro Masullo 提出了 GRH 完整证明，Brian Conrad 已审阅数月，稿子"目前看起来站得住"。他特意强调一句："**It is all human, with no AI**"。原计划把人请到斯坦福打磨一年再公布，但因为同一天出了另一件事，只能立刻放出草稿（文件名《The Music Of The Primes》）。

另一件事：Levent Alpöge 声称让 Anthropic 内部模型产出了 GRH 证明，**1740 万行 Lean 代码**。Terry Tao 同日按"消化程度"确认三个结果：① AI 重度辅助的三维无外力 Euler 方程有限时间爆破证明（已 Lean 形式化）；② 同样 AI 重度辅助的 Navier–Stokes 爆破证明；③ 纯 Lean 的 GRH 证明（初看用到了 Langlands 纲领与算术几何的现代工具）。

**为什么值得关注**：这不是"AI 又赢了"的简单叙事。同一天，一个人用纸笔、一个模型用 1740 万行代码撞上同一道题。数学界第一次同时面对优先级危机和可理解性危机——证明成不成立是一回事，人类能不能读懂是另一回事。

- `A_D_E_P_T`（14 条回复）："如果这是真的，作者没在几个月前发布是个巨大错误。手里有跑了十年的项目就赶紧拿出来，否则某个 Anthropic 或 OpenAI 员工闲下来、算力够的时候就会把你的问题解掉。"
- `simplyluke` 反驳"模型自己搞定"："这是在严重低估 Alpöge。他是普林斯顿博士，不是某个无聊工程师对着无限 token 敲'请解 GRH'。专家驾驶员才能跑出好圈速。"
- `j2kun`："做也死，不做也死。保密就被 scoop；公开部分进展就被喂进模型，然后还是被 scoop。"

---

## 2. Scott Aaronson：这些"随机鹦鹉"好像把黎曼猜想证了
🔗 https://scottaaronson.blog/?p=10344 （169 分 / 136 评论）

标题是反讽。他给了两个真判断：一是 Lean 本身还不完全可信（内核 bug 历史上曾允许证出 0=1），"在修好之前，一个有动机的 AI 几乎肯定能利用它证明假命题"；二是"带 Lean 证书的 AI 结果至今没有一个需要撤稿，没带证书的撤了好几个"，所以他赌这次能站住。冷水在后面：数学家不会满足于 1740 万行 Lean，要能自己复述重建，"而这大概要几年，因为人类数学家只有生物级速度"。

**为什么值得关注**：目前对"AI 做数学"最克制的乐观派表态，把焦点从"AI 行不行"转到"验证基础设施行不行"。

- `1239982716`："标题为什么这么阴阳？就算鹦鹉能生成合理的证明片段，背后还有 Lean、ACL2 和一个人类数学家，它也还是随机鹦鹉啊。"
- `hoppp`："这 Lean 代码也太多了，有人能完整理解它怎么运作吗？"
- `jordemort`（6 回复）："到哪一步它就等价于从山上下来拿着两块石板说'上帝说的'？"

---

## 3. Thinking Machines 发布 Inkling 2 Mini：26.4B 总参 / 3.4B 激活，笔记本能跑
🔗 https://thinkingmachines.ai/news/inkling-2-mini/ （507 分 / 82 评论）

"循环 transformer"：每个 token 中间层重复跑三遍，用更多内部计算换更少输出 token。MoE，26.4B 总参 / 3.4B 激活，总内存约 20GB，单 batch 解码理论上限 614 GB/s，官方称能在笔记本跑。100B 以下开放权重模型里 DeepSWE v1.1 拿 48.2%、Vals Index v2.2 拿 46.5%，都第一。还放了可变循环层数的研究版：不做 CoT 的时间视野从 16 秒提到 37 秒，串行推理到十次循环还在涨（训练只用了五次）。选循环而非长 CoT 的关键理由是可监控性——模型想得更久但不写出来，CoT 反而更短更可读。

**为什么值得关注**：测试时计算的另一条路：不靠更长思维链，靠同一批权重多跑几圈。对本地部署和 CoT 监控同时有意义。

- `mattnewton`："benchmark 好看，实测比 benchmark 更好。我更感兴趣那个 varloop 研究版，不知道还有别的开源工作在做这个。"
- `liuliu`："感觉挺聪明，能解我扔过去的开放问题。但回答偶尔很怪（他们也承认了），markdown 语法会用错。"

---

## 4. 语言模型可以改写自己的权重（无需梯度、无需训练）
🔗 https://arxiv.org/abs/2611.21885 （313 分 / 102 评论）

论文主张 self-rewriting：27B 模型拿到自己的权重、评分答案和运行自己的能力，诊断失败并直接改写权重，在没见过的题上提升 6.6 个点；连续八次会话每次都更好；还能把损坏到几乎全错的副本恢复到原准确率 80% 以上。能力随规模涌现——同家族小模型要么改不动要么把自己改坏。核心论点："训练与推理之间的墙是我们工具的限制，不是智能的属性"，并把它定位为递归自我改进的必要一步。

**为什么值得关注**：若成立，动摇了"部署模型是冻结的"这个行业默认前提，也绕开了所有"重训需审批"的安全假设。全文一次没提 alignment。

- `zodwick`："不是我们想要的 RSI，但是我们应得的 RSI。"
- `xhrpost` 的技术质疑："保真度提升总得来自某处……它靠练习题筛选，本质还是在做题学习。"

---

## 5. 英伟达会计被 SEC 调查，市值蒸发规模创纪录
🔗 https://finance.yahoo.com/markets/article/nvidia-stock-extends-25-trillion-rout-as-sec-probe-reportedly-investigates-its-accounting-194945274.html （177 分 / 72 评论）

消息人士称 SEC 正调查英伟达会计处理；同期纳斯达克抹平 2026 年全部涨幅。HN 最热类比是"Enron 2.0"，最扎心的冷知识是：英伟达正是当年替换 Enron 进入标普 500 的那家公司。

**为什么值得关注**：AI 资本叙事第一次触及"账目是否可信"，比任何模型发布都更能影响明年的算力投资节奏。

- `voidfunc`："我 bingo 卡上可没写'英伟达是安然 2.0'。"
- `throwawaypty`："英伟达在真出货。安然纯粹是骗局。"
- `kovacs`："巧了，英伟达就是替换安然进标普 500 的那家。"

---

## 6. 谷歌员工请愿：别惩罚不想上 AI 的学校
🔗 https://www.motherjones.com/politics/2026/11/google-alphabet-union-school-ai-protest-gemini-workers-petition/ （237 分 / 174 评论）

Alphabet 工会联名要求公司不要因学校拒绝 Gemini/AI 功能而报复或切断服务。争议核心是谷歌把 AI 打包进教育产品的策略，以及学校有没有说"不"的权利。

**为什么值得关注**：AI 进校园的阻力第一次以"员工 vs 雇主"形式公开化。评论区分歧不在 AI 好坏，而在工会该不该管产品方向。

- `AlexandrB`："工会该专注工作条件、薪资、反报复，不该影响业务方向。如果这决定错了谁负责？员工愿意降薪弥补营收吗？"
- `zzzeek`（技术派）："一条 CSS 规则就能把 AI overview 那个 div 藏起来，学校要的就是这个。"

---

## 7. 我们把开发者"升"成了架构师，却没告诉他们
🔗 https://manidoraisamy.com/developer-to-architect.html （233 分 / 151 评论）

真实 bug 复盘：同事用 AI 写注册日志，为了每周看到新装用户，依次 try 拿邮箱、拿 userID、失败记错误——每行都是一次 Google API 调用，全串在欢迎页第一行执行，欢迎页要 15 秒才加载。正确做法是只记时间戳并向营销说"做不到"，或先渲染欢迎页再异步取邮箱。结论：架构师的工作就是顶回会拖慢产品的需求，而这恰恰是 AI 不会做的——它不知道你是在发版还是有百万用户。

**为什么值得关注**："AI 写得对但架构错"的典型样本，比抽象的"AI 会不会取代工程师"有力得多。

- `viklove`："'懂每个方法背后有多少次 API 调用'——这话听起来只有初级或实习生才会说。"
- `mellosouls`："开发转架构不是升职。架构并不比软件工程更免疫 AI，作者描述的是有人把 AI 用错了。"
- `esseph`："在我待过的每家公司，架构岗等于非银行 VP，钱更多活更少。"

---

## 8. 用 AI"氛围编程"写出一块推理芯片（FPGA 跑 LLM）
🔗 https://ankitg.me/blog/vibecoding-inference-chip/ （97 分 / 31 评论）

作者从没碰过 FPGA，凭常识 + Codex/Claude，租 AWS F2，把 Verilog 和底层 C++ 全交给 agent，最后真在 FPGA 上跑起 LLM 推理，70+ 到 200+ token/s（20B 模型，量化）。代价被评论区挖出来：**约 1 万美元 Claude API 费用**（YC 报销）。核心观察不是"agent 会写 Verilog"，而是"coding agent 让我能进入完全陌生的领域"。

**为什么值得关注**：AI 编码的价值正从"写我本来会写的代码"转向"做我本来不会做的事"。同时给了成本上限参考：一次跨领域硬核项目 ≈ 1 万美元 token。

- `risyachka` 的冷水："FPGA 是软件驱动的，模型能自己验证输出，一点都不意外。"
- `cpldcpu`："我用 Opus 4.5 干过类似的。实现 transformer 已经成了 AI 辅助编程的 hello world。"

---

## 9. Winedroid：用 Rust 重写 Android，浏览器里跑真实 APK
🔗 https://winedroid.soham.sh/demo/ （79 分 / 25 评论）

纯 Rust 复刻 Android 运行时（不是模拟器、不带 Linux 内核），编译成 WASM，浏览器加载 12MB runtime 就能跑 F-Droid 的真实 APK。名字致敬 Wine：当年在 Linux 上重实现 Win32，现在在 Web 上重实现 Android 的 DEX 层。目前只有计算器、记账、天气几个 demo 能跑，web 无 JIT 所以慢。

**为什么值得关注**：API 兼容层思路在移动生态的复现，也说明 WASM 正在吃掉原本必须靠虚拟机的场景。

- `haunter`（实测失败）："一个 app 都启动不了，'While executing DEX method dex file' 之类的报错。"
- 作者 `sohzm`："确实还很早期，只有我测过能跑的几个 F-Droid app。"

---

## 10. DreamCoder：Mastering Emacs 作者做的 AI 编码 IDE
🔗 https://www.masteringemacs.org/article/announcing-dreamcoder （58 分）

Mickey Petersen 憋了 15 个月。他不满 Claude Code"在终端里跑 agent"的形态，做了个把 AI 编码放进图形 IDE 的 harness，并顺带写了一篇 AI 与 Emacs 小史（首页 dreamcoder.ai）。

**为什么值得关注**：编码 agent 的形态还在剧烈分化——终端派、IDE 派、Slack 派（同日的 OpenComputer 就是 Slack 派）。胜负取决于人机协作粒度，而不只是模型能力。

- `weavermarquez`："太期待了。我一直觉得死守 Emacs 反而限制了 AI 编码。"
- `julienchastang`："我把定制 Emacs 装进容器，里面还有 codex，并排使用是超能力——可以直接让 AI 写 elisp 来塑造编辑环境。"

---

**本轮略过**：移民律师 AMA（370 分，身份话题）、Nine Inch Nails 现场档案、Nasdaq 行情、逆向猫砂盆（兴趣类）；DeepMind "math horizon" repo（仓库 404）。备选：Show HN **OpenComputer**（42 分，开源 Devin 替代，Slack 里 @Computer 派活，VM + rootless podman 双层隔离）。

已把 20 篇文章全部标记为已读。
