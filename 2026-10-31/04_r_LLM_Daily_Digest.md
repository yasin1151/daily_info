
# r/LLM 速递 · 2026-10-31

> Reddit 全端点本轮仍被 TCP 层封锁（www/old.reddit/redlib 均 http=000），内容经 arctic-shift 归档 API 与 feed2json RSS 通道取得。赞数为归档快照，可能滞后；标「RSS 未提供」的评论归档无分数。今日 r/LLM 新帖评论极薄：117 个未推过的候选帖逐个拉评论树后，达到「至少 3 条有信息量的真实发言」的只有 2 个，其余要么只有 0-2 条评论，要么是玩笑、单句附和或自推链接，因此只推这 2 条，不凑数。

## 1. 自托管 LLM 前该知道什么：评论区把「显存够不够」拆成三个乘数

**摘要：**
一位刚开始接触自托管的用户发帖说，LLM 推理对他「很难」，想在做之前先听有经验的人讲清必须知道的事，并请求入门材料。评论区把重点放在账算错上：模型卡上的显存数字不能直接用，要按上下文长度和量化档位重算；真正在中途把显存吃爆的是随上下文与并发增长的 KV cache，量化只压权重、不缩 cache，除非连 cache 的数据类型一起降，而那会伤长上下文精度。另一条被反复强调的是分词器和 prompt 模板必须与模型严格匹配，配错会让模型吐出胡话，新手容易误判成模型坏了；测量上则建议把首 token 和后续 token 分开计时，前者吃算力、后者吃显存带宽。为什么值得关注：自托管翻车多数不是选错模型，而是把「权重装得下」当成「能跑」，这条讨论给出的是可执行的显存预算拆法和验证顺序。

**高赞评论：**

- u/GrandioseScenario660（赞数 3·归档快照）：「the model card says one thing but then with context length and any kind of quantization it's a whole different animal」，并提醒分词器与 prompt 格式「each model is annoyingly specific」，配错会被当成模型损坏。立场说明：把显存要按上下文与量化重算摆在第一条，指出新手最常踩的其实是配置错配而非模型差。
- u/Fit-Corner2382（赞数 2·归档快照）：「The model file is only the weight budget; the KV cache grows with context and concurrency and is what usually OOMs mid-chat.」，并说明「Quantizing weights frees space but does not shrink the cache unless its dtype is reduced too」。立场说明：这是全帖技术密度最高的一条，把「能加载」和「能连续对话」的区别讲成了权重、KV cache、并发三者关系。
- u/ChillingChasuble（赞数 2·归档快照）：用 2019 年的两张旧卡加 32G 内存装 Ubuntu，从 llama.cpp 官网和 Hugging Face 的 GGUF 起步，回复测量问题时说「llama.cpp also comes with a benchmarking program called llama-bench.」。立场说明：给的是最低成本的上手路径和具体测量工具，把「学推理」落到可复现的步骤而不是抽象建议。

**原帖：** https://www.reddit.com/r/LLM/comments/1xim3d9/

---

## 2. 16GB 显卡跑成完整 coding agent：125 tok/s 靠 MoE + MTP + 激进量化 + 极简 harness

**摘要：**
帖子从一组市场数据出发：桌面用户最常见的显卡是 16GB 显存（帖中引 GaugeDB 称占 27.21%），而这一档跑 27B 稠密模型只有 10-20 tok/s，可顺畅使用编码 agent 需要 100-150 tok/s。作者的解法是一套组合：选 MoE 加 MTP（多 token 预测）的 35B-A3B 编码模型，量化到 UD-Q2_K_XL 的 GGUF，在 RTX 4070 Ti SUPER 上实测 125 tok/s，代价是上下文只有 65535。为压住上下文，他换了只吃约 1.5k token 的 Pi agent（称 Codex/Claude Code 开箱要 10-14k），并先用 /new 写 plan.md 再实现、用 subtask4llm 把大任务拆成十个子任务分实例跑、用 AGENTS.md 限制单文件 300-500 行并强制单测。为什么值得关注：它把「本地跑 agent」从模型选型变成工程配比问题，速度来自架构与量化，可用性来自 harness 和外部文件记忆，而不是指望小模型自己变聪明。

**高赞评论：**

- u/ea_man（赞数 2·归档快照）：「Running A3B at IQ2 is insane」，认为 16GB 上跑 27B 的 IQ4 就有约 80 tok/s，不必为速度把 MoE 压到这个档位。立场说明：直接质疑量化选择，指出作者用质量换速度的比例不合理，是这帖最主要的反对意见。
- u/amelech（赞数：RSS 未提供）：「Yeah that quant has got to be seriously brain dead」，附和上面的质疑。立场说明：代表社区对 Q2 级量化的普遍不信任，认为掉的不只是速度收益而是模型判断力。
- u/ievkz（赞数 1·楼主）：「it gets tasks to completion; sometimes it takes more than one round of revisions, but it does get the job done.」。立场说明：作者承认要来回改几轮，但认为本地零 token 成本下多迭代几轮是可接受的交换，正面回应了质量质疑。

**原帖：** https://www.reddit.com/r/LLM/comments/1xgqtmq/
