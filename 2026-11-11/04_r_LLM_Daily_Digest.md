
Reddit 的三个端点仍被封锁（`www.reddit.com`、`old.reddit.com/r/LLM/hot/`、`redlib.perennialte.ch/r/llm/hot/` 全部返回 http 000），本轮改用 arctic-shift 归档通道（8 个时间窗口全部返回 200 → 185 条候选 / 154 条未推送），探测 40 个候选的评论树，其中 0 条失败。质检通过：8 条中每条的摘要 181–252 个中文字符，且各有 3 条真实评论；24 条英文引文经归档比对，problems=0。近 48 小时内的新帖评论几乎都还没有入库，因此部分条目取自 5–15 天前仍在继续讨论的帖子，并标注了发帖时长。

---

# r/LLM 热帖 · 2026-11-11

Reddit 的三个端点仍返回 000（TCP 层封锁），本轮数据全部来自 arctic-shift 归档快照。赞数是入库时的快照值，可能滞后，标 1 的多为入库默认值，不代表真实热度。

## 1. Ling-3.2-flash 发布：560B 总参、25B 激活、原生图像视频输入、1M 上下文（发帖 33 小时）

**摘要：** 蚂蚁的 Ling-3.2-flash 是原生多模态 MoE，总参数 560B、每 token 激活 25B，官方标注上下文最高 100 万 token，支持文本、图像、视频输入。发帖直接拿 Claude Opus 5 max 对标：OmniDocBench 1.5 为 92.21 对 90.56，ZEROBench 子项 43.71 对 39.52，Vision2Web 85.86 对 80.20，并演示了视觉编程、操作 Blender、参考图转 3D、以及用专家 agent 批量产出办公文档。API 同时提供 OpenAI 兼容和 Anthropic 兼容两种接口。值得关注的是它把「开源 MoE 能不能在文档、网页这类多模态任务上贴身对标闭源旗舰」从口头争论变成了可以复核的榜单；但评论区第一反应就是不信这份对标，因为同批被引用的 DeepSeek、GLM 在别的榜上离 Opus 还有明显距离。另外帖子只说 API 可访问，是否放权重并没有写清楚，这条也被追问了。

**高赞评论：**
- u/Bramoments（赞数 2·归档快照）："i call bullshit, deepseek 1017 and GLM 5.3 are nowhere near opus 5 max, and yet on these benchmarks theyre somehow magically on the same level." 立场说明：他认为这是自选榜单的常见套路——只要挑出三个刚好的指标，就能宣称追平旗舰，实际体感差距不会被这几个分项反映。
- u/look（赞数 1·归档快照）："Ling 3.1 is very cheap on OpenRouter. Not worth it at the list price, but at 85% off it's great for high volume summarization, LLM as judge, synthetic data generation" 立场说明：给的是采购口径而不是跑分口径——上一代在 OpenRouter 打折后适合大批量摘要、当裁判、造合成数据，期待 3.2 沿用同样价位。
- u/Frail_Waif（赞数 2·归档快照）："DS for coding and Ling for everything else is looking like a pretty solid high-RAM local LLM setup." 立场说明：把两款模型按能力分工来搭：编码交给 DeepSeek，其余多模态杂活交给 Ling，前提是机器内存足够大。

原帖：https://www.reddit.com/r/LLM/comments/1xrtf2b/

---

## 2. 模型会不会在你按下发送前就读输入框里的草稿？（发帖 40 小时）

**摘要：** 提问者听到一种说法：模型会在你提交前就读到输入框内容，于是担心粘了一段敏感文本再删掉，内容其实已经发出去了。评论区把这个问题拆成两层：模型侧和前端侧。多数人的判断是模型只看到一个 turn，也就是按下发送后组装好的那段输入；真正的风险在于 chat 应用的 JS 能读到每一次按键，草稿是否离开浏览器取决于产品实现，而不是模型厂商的能力。有人从工程成本反推：那要处理高频编辑、要为永远不会提交的 token 付算力，配上思维链这类机制后省下的时间可以忽略，所以没人有动机做。也有人提醒，粘贴图片在网页版 ChatGPT 里会立刻上传到存储，但上传不等于进入模型上下文，这两件事常被混为一谈。

**高赞评论：**
- u/Ambitious-Prompt-975（赞数 5·归档快照）："It's not a choice an llm would be actively making" 后面接着说，这取决于调用模型的 App 或 harness 怎么实现那个输入框，技术上可以把输入流式喂给模型，但想不出谁会这么做。立场说明：把讨论从「模型是否会偷看」拉回到「harness 实现了什么」，这也是唯一能靠抓包验证的层面。
- u/New-Yogurtcloset1984（赞数 6·归档快照）："It's safe to assume that anything you do on a work machine is captured by your employer and can be reviewed by your employer." 立场说明：他认为真正的威胁模型不是远处的 AI 公司，而是公司设备本身；这条把提问者的恐慌换成了可执行的安全前提。
- u/logic_circuit（赞数 2·归档快照）："If they would stream continuously, that would be serious fuckup for inference cache." 立场说明：从推理侧给出技术理由：持续流式输入会不断改写前缀，把 KV 缓存反复作废，要避免就得再造一套预取机制，收益完全不值。

原帖：https://www.reddit.com/r/LLM/comments/1xrkt4l/

---

## 3. 文档预处理比 OCR 精度更决定 RAG 效果？（发帖 5 天）

**摘要：** 发帖人做了多年文档处理，观察到 RAG 讨论几乎都集中在 OCR 质量、embedding 模型、chunk 大小和向量库上，却很少谈源文档在进入流水线之前的形态。真实语料往往是多来源拼合：重复页眉页脚、附录、证物、邮件往来链、扫描插页、手写批注，甚至多年材料并进一个 PDF。他的判断是很多被归咎于模型的检索失败，其实发生在更早的环节。评论区一半人认同并补充做法，另一半人认为随着解析能力变强，预处理的价值会下降。这场争论本身有信息量：它划出了「整理数据结构」和「把任何格式读成文本」这两件常被混为一谈的事，也解释了为什么预算总是给到模型而给不到数据准备。

**高赞评论：**
- u/gkanellopoulos（赞数 1·归档快照）："and are not willing to spend a bunch of time prepping their data" 原文前半句是 stakeholders 想「昨天」就用上新技术。立场说明：他指出这是「把数据做成 AI-ready」的通用问题，卡点不在技术而在预算与耐心，多数故障确实源自没准备好的数据。
- u/Potential-Wrangler58（赞数 1·归档快照）："split the big PDF into separate documents, work out what type each one is (contract, email chain, exhibit), and only then index them" 并补两条便宜做法：给每份文档加 ID 和版本或日期防止检索到旧版本，把扫描插页和手写批注单独标记。立场说明：这是本轮最具体的工程建议，他也披露自己在做拆分类工具，属于带利益相关方视角。
- u/FirestormCold（赞数 1·归档快照）："besides video we can digest basically any format" 他表示自家流水线字段准确率能到九十多且全链路可追溯，经典原始 OCR 已经死了。立场说明：代表反方——当解析足够强、可以整包丢进去只取所需时，预处理的重要性会下降，这与上一条形成正面冲突。

原帖：https://www.reddit.com/r/LLM/comments/1xp16m1/

---

## 4. ollama 装上却「不好用」，到底是哪里错了（发帖 7 天）

**摘要：** 一个刚上手本地推理的用户抱怨：装了 ollama、也拉了 Qwen 这类高评价模型，实际用起来却很糟，怀疑是不是要先训练或做特殊配置。回复几乎一致地把「先微调」这个直觉否掉，并给出排查顺序：chat 模型要先确认装的是 instruct 版本而不是 base，base 只会续写提示；必须套模型自带的 chat template，模板错了模型会输出胡话，让人误判成模型不行；上下文超出可用显存时会往 CPU 掉层，表现是「卡顿、答非所问」而不是报错；微调几段私人对话反而可能破坏指令跟随，判据应该是留出集的答案变差而不是 loss 下降。这一串正好是一份最小可行的本地部署体检表，比换更大的模型省钱得多。

**高赞评论：**
- u/Fit-Corner2382（赞数 3·归档快照）："A base checkpoint continues the prompt instead of answering" 他还强调要用指令微调过的权重配原始 chat template，并在留出集变差时停下微调，而不是等 loss 下降。立场说明：这条把「模型不听话」拆成 checkpoint 选错、模板配错、误微调三类可检查的原因，是整串里最系统的一份排查表。
- u/slowtractor（赞数 1·归档快照）："Run ollama ps while it's answering. The PROCESSOR column shows how much landed on CPU" 立场说明：给了一条一行命令的可验证诊断法：回答过程中看 PROCESSOR 列，就能确认慢是不是因为层掉到了 CPU。
- u/confused-photon（赞数 1·归档快照）："The limiting factor really is VRAM and the 4080 doesn’t have much" 他补充 4080 能跑较激进的 Qwen 27B 量化并带一些上下文，但 100k 以上长上下文是 agent 场景的硬需求，这张卡的显存顶不住。立场说明：把「效果差」翻译成显存与上下文预算问题，避免用户继续在参数上试错。

原帖：https://www.reddit.com/r/LLM/comments/1xn3frf/

---

## 5. 7 万条销售样本微调的小模型，能追上 Claude 写销售邮件吗（发帖 9 天）

**摘要：** 一个团队用 7 万条销售样本微调小开源模型，输入包含卖方的报价、理想客户画像和每个潜在客户的已知信息，然后与 Claude Haiku 在「回复分类」和「销售邮件撰写」两项上做盲评对比。发帖人自称在采信结果前想先听意见，评论区的火力集中在评测设计而不是模型：如果两边看到同样的报价、语气和客户笔记，这些材料会主导成稿，两个模型写出近似文本，盲评最终只在比谁的措辞更漂亮；正确做法是按整个客户账户切分训练与测试，否则同一客户的邮件会漏进训练集；邮件应按「claim 是否与笔记一致、ask 是否匹配报价」来打分，编造痛点的流畅文案即使读着舒服也该判负。还有人指出「失败可以重试直到通过」的判分方式其实在测耐心。

**高赞评论：**
- u/Fit-Corner2382（赞数 4·归档快照）："Hold out whole accounts, not random emails, so nothing from a test prospect sits in the 70,000." 他还要求分类按已一致的标签评分，邮件按 claim 与 ask 是否对得上评分。立场说明：这是最实质的方法论修正——随机切邮件会造成同账户泄漏，盲评偏好会被材料本身拉平。
- u/Ctbhatia（赞数 1·归档快照）："if it retries until it passes, a test passed on the fourth try counts the same as one passed cold, so the total ends up measuring patience." 立场说明：他指出发帖人描述的「失败重试直到过关」计分方式会让结果失真，应改成统计两边首次通过率。
- u/Sayali-Pinge（赞数 1·归档快照）："a perfectly toned email with a wrong claim is worse than a generic one" 她的核心论点是微调改变的是说话方式而不是知识，7 万条样本教的是销售邮件长什么样，并不会让模型知道你产品的真实事实。立场说明：她自曝在相关厂商工作，属带立场发言，但对「语气对、事实错」的风险判断确实切中这类微调项目的通病。

原帖：https://www.reddit.com/r/LLM/comments/1xlfhqc/

---

## 6. 自托管 LLM 之前必须知道的事（发帖 12 天）

**摘要：** 一个正在自学推理部署的人直接问老手：自托管前最该知道的是什么，有没有推荐材料。评论给出的是三层递进的答案。第一层是显存真相：模型卡上的数字只是权重预算，真正让人在对话中途 OOM 的是随上下文长度和并发数增长的 KV 缓存，短提示能加载成功、缓存填满就崩，调大 batch 是成倍放大缓存而不是复用权重；量化权重能腾空间但不缩小缓存，除非连缓存的 dtype 一起降，而这会伤长上下文精度。第二层是把首 token 时间和后续出 token 分开计时，前者吃算力、后者吃显存带宽。第三层是可观测手段：llama.cpp 启动日志会打印 KV 缓存 MiB，vLLM 会记录缓存 token 数与最大并发，边拉上下文边看 nvidia-smi 就能找到临界点。

**高赞评论：**
- u/GrandioseScenario660（赞数 3·归档快照）："start with a tiny model like a 3b or 7b, get that running smooth, then scale up" 他强调从修小问题里学到的东西比硬扛一个勉强塞得下的 70B 多得多，并建议随手记配置和计时数字。立场说明：这是最省学费的上手路径，把「先小后大」和「记录可比较的数据」绑在一起。
- u/Fit-Corner2382（赞数 2·归档快照）："the KV cache grows with context and concurrency and is what usually OOMs mid-chat" 立场说明：这条纠正了最常见的误解——把显存需求等同于模型文件大小，实际上并发与长上下文才是压垮服务的部分。
- u/Future_AGI（赞数 2·归档快照）："llama.cpp prints the KV cache size in MiB in its startup log when a model loads" 他补充 vLLM 会打印 GPU KV 缓存 token 数与在最大上下文下能容纳的并发，配合 nvidia-smi 观察加上下文或并发时的拐点。立场说明：把「怎么测」落到具体工具输出上，比笼统地说要看显存更能直接执行。

原帖：https://www.reddit.com/r/LLM/comments/1xim3d9/

---

## 7. RTX 4070 Ti SUPER 上 125 tok/s 跑本地编码 agent，但代价是 Q2 量化（发帖 14 天）

**摘要：** 发帖人说 16GB 显存是最主流的桌面配置，而这类卡此前跑不动「又聪明又快」的编码 agent：27B 稠密模型只有 10–20 tok/s，而编码 agent 需要 100–150 tok/s。他的解法是换成两个 35B-A3B 的 MoE 模型，叠加多 token 预测（官方称提速约 20%）、MoE 只激活部分参数，以及一套精简 chat template 的系统提示，把推理再砍一半，最终在 4070 Ti SUPER 上跑到 125 tok/s，但上下文只有 65535 token，他用三种办法绕。评论区的反应几乎全是反对量化档位：同样 16GB 完全可以跑 27B 的 IQ4 并拿到约 80 tok/s，把 A3B 压到 Q2 是拿质量换速度，有人直说这种量化「脑子已经死了」。发帖人承认有时需要多轮返工，但能完成任务。

**高赞评论：**
- u/ea_man（赞数 8·归档快照）："You should be able to run an IQ4 of 27B on 16GB with a speed of some ~80t/s on that GPU. Running A3B at IQ2 is insane" 他还贴了具体的 IQ4 27B 混量化仓库。立场说明：这是本轮技术含量最高的一条反对意见——省下的 45 tok/s 是否值得把权重压到 2bit，取决于返工率，而他判断不值。
- u/PayBrave5035（赞数 2·归档快照）："Delete that q2 junk or download q4 version ASAP and offload some layers to cpu" 他补充 MoE 的最大优势正是可以把层卸到 CPU 而几乎不掉速，不像稠密模型那样一卸就崩。立场说明：给出替代方案：换 Q4 并利用 MoE 的卸载特性，在 16GB 上换回质量。
- u/ievkz（赞数 -1·归档快照，楼主）："It’s fast and decent, it gets tasks to completion; sometimes it takes more than one round of revisions, but it does get the job done." 立场说明：作者的反驳是纯经验式的——在真实任务上能收敛，只是偶尔要重跑；这条把争论落到「返工次数对不对得起速度」这个可测的判据上。

原帖：https://www.reddit.com/r/LLM/comments/1xgqtmq/

---

## 8. 5 美元换 150 美元额度的第三方「订阅站」，到底是什么生意（发帖 15 天）

**摘要：** 发帖人看到一个叫 xkiro 的服务，5 美元给 150 美元用量，直觉是骗局，来问有没有人真用过。回帖分成两拨：一拨确认自己付了 5 美元、三天用下来与页面描述一致，还贴出累计 395 美元用量的截图，说 15 美元用了两个月；另一拨从商业模式上怀疑——它宣称的用量是付费额的 30 倍，如果靠转售 200 美元档的订阅再放大，理论上能靠「很多人用不满」赚差价，也可能只是把批量折扣或者别人的订阅转手。讨论里还夹着支付渠道的现实摩擦：越南的支付方式不被支持，只能转加密货币还多付手续费，模型清单里 4.1 flash 的可用性也和页面宣传对不上。对成本敏感的用户值得看的是这段「便宜额度从哪来」的拆解，而不是 5 美元本身。

**高赞评论：**
- u/Cyvster（赞数 2·归档快照）："they are claiming you get 30x more usage than you pay for" 他的推算是：如果它转售 200 美元档订阅而很多人每月能用出一万二千美元的量，那 60 倍差价就是利润来源。立场说明：这是唯一尝试解释商业可行性的回复——低价不必然是骗局，也可能是对「用不满」的套利，但前提是账能对上。
- u/8dmin（赞数 1·归档快照）："i have 5$ tier for 3days and everything works as described on the page" 他还纠正了别人对模型清单的期待：4.1 flash 不在该档，可用的是 Luna。立场说明：提供了一手体验，但同时说明宣传页与实际可用模型存在差异，这正是这类服务最容易踩坑的地方。
- u/XheirBang（赞数 1·归档快照）："the quality idk if its lower or if i just have a bad harness" 他说两个月下来总共只花了 15 美元、累计用量近 400 美元，但无法判断输出质量下降是服务方降级还是自己 harness 的问题。立场说明：这条点出关键风险——用量便宜但模型可能被换档，用户缺少对照基线时很难察觉。

原帖：https://www.reddit.com/r/LLM/comments/1xglohi/
