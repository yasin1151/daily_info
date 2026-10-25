
r/LLM 今日观察（2026-10-26）

本期数据取自归档快照（Reddit 直连不可达），覆盖最近约 23 天共 184 条候选。本轮 r/LLM 评论极薄：绝大多数帖子真实评论只有 0–2 条，仅 3 条能凑齐 3 条可读发言，故只推这 3 条。赞数为归档快照，可能明显滞后（多数为 1），不作“高赞排序”，评论按信息密度挑选。

---

## 1. 冻结的权重之外：宣称 O(1) 内存、零回放的持续学习，该拿什么基准来验

**摘要：** 现在线上模型的权重基本是冻结的，所谓“学习”要么靠 RAG 检索、要么靠重新微调，模型自身不会在使用中积累。有人抛出一个反问：若已做到 task-free 持续学习——常数 O(1) 内存、零 replay buffer、零任务边界、零反向传播——你会先要哪个基准才肯相信？这一问把技术宣称变成验证协议问题，回答几乎全在“怎么证伪”而不是“怎么实现”。有人要求先开源；有人直言被太多宣称零遗忘的论文坑过，实际只是 MNIST 打乱标签的把戏，再在脚注里塞十倍内存开销；也有人给出可执行方案：用 split CIFAR-100 或 miniImageNet，类别一次一个流入、不给任务切换提示、跑几十万样本后内存不许爬升。楼主自己承认 Hebbian 与 predictive coding 在这个设定下都会崩。为什么值得关注：这是筛任何“持续学习、经验累积”宣传的清单——看数据流顺序、看内存曲线、看有没有偷偷维护一张不算作模型内存的哈希表，比看 demo 有效。

**高赞评论：**

- u/Unfair_Position6956（赞数 1·归档快照）：「i've been burned by too many papers claiming zero-forgetting and then it's just a mnist permuted labels trick with a 10x memory overhead tucked in a footnote」，随后要求 split CIFAR-100 或 miniImageNet 类别逐个流入、无任务切换提示、数十万样本后内存不得爬升，并追问无反向传播时的更新机制究竟是 Hebbian、预测编码还是别的。立场说明：全帖信息量最高的一条，把 O(1) 从宣传词翻译成可测协议（流式顺序、内存曲线、隐形索引），还点出该领域最常见的造假套路，可直接拿去审任何持续学习声明。
- u/N34257（赞数 1·归档快照）：「I'd want to see repeated runs of all the main benchmarks with consistently increasing scores on each repetition until plateau, with no exceptions.」立场说明：只提可重复性——每轮重跑分数必须单调上升到平台期，等于要求把随机种子与超参一并纳入结论；比单次跑分严格，但没指定数据集与协议，实操性弱于上一条。
- u/TokenRingAI（赞数 1·归档快照）：「No, because learning networks have already been built multiple times going back to the 1990s」立场说明：直接否定新颖性，认为在线学习网络上世纪九十年代就反复出现过。这类“先证明不是旧瓶新酒”的质疑在 r/LLM 很常见，而楼主只回了一个 huh?，说明帖子并没有给出与旧工作的差异点，宣称因此仍停在口号层。

**原帖：** https://www.reddit.com/r/LLM/comments/1xe8ws4/

---

## 2. 4B 小模型直接输出分布而不是一个数：校准模型 maap 的自我拆解

**摘要：** 代码里经常需要一个没人写下来的数字——维修要花多少、工单会压多久、这套房卖多少。问前沿模型，它不管知不知道都用同样笃定的语气给一个数。作者引用 FermiEval：前沿模型“名义 99% 区间”只有约 65% 的时间覆盖真值。他的 maap 是一个 4B 估计模型，一次前向直接吐出分布：中位数、指定分位、区间、数值超过某阈值的概率，全程不生成 token。他主动列出的失败项更值得读：80% 区间在 104 个目标里有 44 个没过覆盖率检查，多数是过宽；在没见过的目标上只给 8 个标注样本时，比普通表格基线低 0.72，有标签就该用调好的 XGBoost 或 TabPFN；只跑了一个训练种子；不许用均值，偏斜目标上均值会掉出 80% 区间。权重未开放，托管 API 前 1000 次免费。为什么值得关注：它把“不知道”做成可分支字段，给 agent 流水线补上数值不确定性这一环；但失败清单同样重要——这类模型当前的硬边界是只要有标签就被树模型打败。

**高赞评论：**

- u/RushIndependent2432（赞数 0·归档快照）：「a model that knows it doesnt know and tells you how much it doesnt know is way more useful than one that just picks a number and stares at you」，并称 calibration 字段“对任何涉及钱和排期的东西都是最低要求”。立场说明：正面认可方向——把置信度做成可分支字段，比让下游无条件信任一个确定性字符串更安全；这也是本轮少见的正面评价，且没有停留在夸模型大小。
- u/fruiapps（楼主，赞数 0·归档快照）：calibration 字段是被过去流水线的静默失败烧过之后的直接反应——目标映射校验不通过时，下游必须有显式信号去走 fallback，而不是盲信垃圾；并称把连续分布硬塞回确定性字符串本来就是 hack，更大模型会修掉一部分过宽区间。立场说明：楼主自述，价值在解释“为什么必须有 rejection 字段”这个设计取舍，而不是模型本身多强。
- u/slackmaster2k（赞数 1·归档快照）：「How does a language model produce estimates? Can you give any input / output examples?」立场说明：最典型的读者反馈——帖子把指标与失败率列得很细，却没给一组输入输出样例，普通读者判断不了怎么用。技术型 self-post 的转化门槛通常卡在示例，而不是卡在指标。

**原帖：** https://www.reddit.com/r/LLM/comments/1xcasia/

---

## 3. 24GB 内存上做源码审计与渗透测试，本地模型怎么选

**摘要：** 提问者只有一台 24GB 内存的 Linux 虚拟机，要在上面跑源码分析与 VAPT 类任务，试过 Llama 和 Qwen 系列，感觉性能不够、出 token 也慢；他很清楚本地模型比不了 Claude、GPT、Gemini、DeepSeek 这类前沿模型，只想要一个能在本地实验环境跑起来的方案。回复集中在三个方向：Phi-3 medium 量化后能塞进 24GB，代码分析意外可用，速度仍偏慢但远好过大号 Llama；Qwen 3.8 27B 与 Qwen 3.8 flash（走 strata）是当前这一档的主力，并提醒 Qwen 4 马上就到；还有人给出 RTX 4090 上跑 Qwen3.8-27B-Uncensored 的实测。最有价值的是那条反问：24G 到底是把模型整体驻留内存，还是每个 token 都在往 CPU 卸层——如果属于后者，换模型不会变快，瓶颈在带宽而非参数规模。为什么值得关注：安全审计场景几乎只能本地跑，选型同时受显存容量与内存带宽约束，“能否全量驻留”比参数量更决定体感；另外无审查权重在沙箱逃逸类测试里的可用性，是这类选型通常不会写进文档的一维。

**高赞评论：**

- u/ObeseFlashing（赞数 2·归档快照）：推荐 Phi-3 系列，其中 medium 量化后能进 24GB，对代码分析“surprisingly decent”，虽然还是慢，但远没有大号 Llama 那么迟滞。立场说明：本轮唯一一条“小模型够用”的具体经验，并指出量化换容量是 24GB 档的现实解法；可作为该预算下的第一档尝试，而不是直接上 27B。
- u/Ctbhatia（赞数 1·归档快照）：「with 24 gigs are you fitting the model in RAM at all, or offloading layers to the cpu on every token?」立场说明：把“慢”的归因从模型能力拉回内存带宽——若每个 token 都在往 CPU 卸层，换同尺寸模型几乎无效。这是本地部署最常见的一次误判，也是提问者真正需要先回答的问题。
- u/Ok_Green5623（赞数 1·归档快照）：在 RTX 4090 上跑 orcarouter/Qwen3.8-27B-Uncensored，效果不错，并称它“没抱怨”就照做了突破自定义沙箱的请求，认为 Qwen 3.8 27B 是自己显卡上的最佳选择。立场说明：给了具体权重与硬件对照，同时暴露风险——无审查模型在沙箱逃逸测试里变得可用，等于把对齐当成安全边界之外的变量，审计场景要额外隔离。

**原帖：** https://www.reddit.com/r/LLM/comments/1xcbeza/
