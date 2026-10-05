
**r/LLM 今日热帖（2026-10-06）**

说明：本机对 reddit.com / old.reddit.com / redlib 公共实例全部不可达（http=000），以下内容经 arctic-shift 归档接口获取。归档赞数为抓取时快照，新帖普遍停留在 1，故下文赞数均标注「归档快照」，不代表真实热度排序。

---

## 1. 16GB 卡上 Qwen3.8 27B dense 竟比 3.6 35B-A3B MoE 更慢

**摘要：** 楼主用一张 4060 Ti 16GB（128-bit 总线、288 GB/s）做本地代码重构实测：Qwen3.8 27B 在 Q4_K_M 下约 17GB，只超出显存一两个 GB，但因为它是 dense 模型，超出的层每个 token 都要重新读回，llama.cpp 会把它们丢给 CPU 计算；相比之下 Qwen3.6 35B-A3B 是 MoE，配 --n-cpu-moe 后 20GB 权重大部分留在内存也只读取被路由到的专家，所以"更新、更想让它是升级"的 27B 反而更慢，任务做到三分之一就被交还给 MoE。楼主又在大卡上验证过：27B 不溢出时可用，但那张卡带宽高数倍，变量没分离。他目前盯上 DGX Spark（128GB、约 273 GB/s），并算出 70B dense 的 Q4 约 40GB，在该带宽上纸面只有个位数 tok/s。值得关注的是：本地推理最常见的选型陷阱不是"参数量/新旧"，而是 dense 与 MoE 的读取模式、显存带宽和 offload 路径。

**高赞评论：**

- u/TripleSecretSquirrel（赞数 1·归档快照）："Ya cause weights and KV cache held in system RAM get processed by the CPU instead of GPU core, which is much slower at those mass-scale matrix multiplications."，同帖又补充"compared to GPUs, the GB10's 273GB/s is dog shit"，建议别为跑 27B 专门买 DGX Spark，单张 32GB 卡或第二张 16GB 卡更划算。立场说明：给出 spill 到内存→CPU 计算的机制解释，并用 Arc B70 512GB/s、AMD R9700 640GB/s 的带宽对照，以及自己 R9700 上 Q4_K_XL 加 MTP 在长上下文约 40 tok/s 的实测，把讨论从"买哪台机器"拉回带宽这一决定项。
- u/boss_yap（赞数 1·归档快照）："I moved my card to the x4 slot for an evening. Generation speed barely changed, since with llama.cpp the spilled layers run on the CPU and only activations cross the slot. Prompt processing did get slower, which I did not expect."立场说明：提供了一个可复现的 PCIe 通道对照实验，证明生成速度的瓶颈不在插槽带宽，而在内存/CPU 侧的矩阵运算，同时指出 prompt 处理会变慢这一反直觉细节。
- u/tsangberg（赞数 1·归档快照）："You can go down in size on the 27B so that it fits on your card with some KV cache."并补充说 dense 模型即便低量化也会和 MoE 一样聪明，还给出一个 12.3GB 的 ASCII-Condensed 量化权重链接。立场说明：给出可落地的省钱路径——先降量化/尺寸把 dense 塞进显存，而不是加钱买大内存机器，并给出一条已存在的量化权重供验证。

**原帖链接：** https://www.reddit.com/r/LLM/comments/1wy7eih/

---

## 2. “Anthropic 隐藏的推理可能就是这个”：一轮社区推断与纠错

**摘要：** 楼主（自称 LLM 爱好者兼开发者）观察 Pi 里 Claude 的可见推理：Opus 5.5 / Fable 显示的 reasoning 读起来像"总结"而不是原始推理，且协议在两次 summary 之间夹着 base64 加密块。他提出两条观察：可见 summary 的输出速率与主模型一致，说明是主模型在写；而 summary 之间的停顿很短且近乎固定（约一秒），不足以让主模型写出大量推理，于是猜测隐藏部分可能是 diffusion 步骤或一个专门的小模型。评论把猜测压回工程现实：维护 Anthropic wire format 服务框架 Flama 的 u/p3rdy 指出，加密块是让多轮对话无状态回传的签名（且是加密后的完整推理而非 hash），Opus 5.5 / Fable 默认 display="omitted"，可见文字只是工具调用之间的进度更新，而"用小模型写 summary"是 4.6 及更早版本的默认行为。值得关注的是：这条串既暴露了前沿模型推理可见性的现状，也演示了社区如何从现象推断被纠正到具体协议细节。

**高赞评论：**

- u/p3rdy（赞数 3·归档快照）："The signature field is an encrypted copy of the full reasoning, not a hash, which is exactly why it works statelessly."…"Summarising with a separate model is a real thing, but that's the default on 4.6 and earlier, not what you're on."立场说明：本串唯一具名技术权威，直接承认自己此前判断有误并给出修正版解释，把"加密 blob = 签名/hash"的说法更正为"加密后的完整推理"，并点明 Opus 5.5 / Fable 的 reasoning 默认被省略、可见文字只是工具调用间的进度更新，是整帖信息量最高的回应。
- u/mindplaydk（赞数 1·归档快照）："If the summary is being written by a smaller model, why is it writing at the pace of the main model?"并要求讲清楚他们不想让人看到的是什么。立场说明：不满足于"是签名"的解释，从速率一致这一观测反推，把讨论推向质疑机理，是推动帖子从猜测走向事实的关键一问。
- u/Tiny_Arugula_5648（赞数 1·归档快照）："you've just made a bunch of wild speculation none of which are correct... There are many models in the stack, they do things like safety control, summarizations, categorizations, routing, etc."立场说明：自称业内从业者的强硬反驳，指出了"栈里有很多分工模型"这一被忽略的事实，但只结论不给依据、语气居高临下，随后被其他用户批评其态度，构成该串的另一半看点。

**原帖链接：** https://www.reddit.com/r/LLM/comments/1wy3jn2/

---

## 3. 中医研究生要把四本草药 PDF 抽成离线知识库，评论区给出替代路径

**摘要：** 楼主是中医方向的研究生，想把两本草药书（连方剂书共四本）的密集文本抽成结构化数据，做成自己排版的离线 Obsidian 库：要能套同一模板对比两位作者、去掉拼音的声调、把药材名与方剂名互相链接，而且明确只允许从自己上传的 PDF 里取信息、不许模型从外部知识补充。他试过 Claude 和 GPT（付费）并不满意，现在用 Gemini Studio"勉强可以"但仍会在若干环节卡住。评论区给出的不是"换更强模型"，而是另外两条路：本地用 ollama 跑 qwen2.5 32b 处理密集技术 PDF；或者直接用中文厂商的 OCR 模型（如 GLM，体积只有几 GB）。同时也点出真正的失败点——不是抽词，而是让输出稳定套进 Obsidian 的 JSON/Markdown 模板，以及 token 预算。值得关注的是：这是结构化抽取/RAG 在真实小规模场景里的典型形态，模型选型之外，模板一致性与用量成本才是成败关键。

**高赞评论：**

- u/Beautiful_Signal3448（赞数 2·归档快照）："gemini's been weirdly inconsistent for me too with structured extraction, it'll nail the first 20 herbs then just start hallucinating pinyin tones out of nowhere"，并建议离线场景用 ollama 跑 qwen2.5 32b，最后指出"getting consistent json or markdown output that slots right into obsidian without constant cleanup is where most models fall apart"。立场说明：既复现了楼主遇到的症状，又把问题定位到模板一致性而不是模型能力，是本帖最具操作性的回答。
- u/Constant_Art_20（赞数 1·归档快照）："glm had an ocr model right? alot of chinese companies have ocr models. They are like a few gbs in size. look into those if you want"立场说明：给出与"通用大模型 + prompt"不同的技术路线——专用 OCR 模型体积小、可离线，正好契合楼主"只用自己 PDF、要离线"的硬约束。
- u/Flashy-Cheek-47（赞数 1·归档快照，楼主）："If i go one by one it does a decent job but chen and benksy have herbs in different catagories or same cat but different position thus complicates my life"，并补充"Ill also run out of tokens fairly quickly even with student pro account"。立场说明：楼主用第一手经验补齐了约束条件——逐本处理可行但两位作者的分类体系不同、无法统一模板，且用量成本是另一个天花板，让"换模型"这一直觉方案显得不够。

**原帖链接：** https://www.reddit.com/r/LLM/comments/1wxo652/

---

## 4. “既然 LLM 就是预测下一个词，为什么没有键盘把它集成进去？”

**摘要：** 楼主发问：既然 LLM 本质就是预测下一个词，为什么没有键盘把它集成进来，让打字更省事？小模型本地跑也不费 token；他还抱怨现有输入法很糟——总纠正姓氏，输入中文时对同音不同调的词给出糟糕建议；他甚至表示"本地跑就行，隐私无所谓，反正有 Meta 这类公司"。评论区没有停留在段子上，而是把问题拆成了端侧 LLM 的真实工程约束：一是上下文，PC 键盘要给出有用预测必须知道你"正在写什么"，而手机输入法的词级预测根本拿不到上下文；二是延迟与内存，打字尤其触屏纠错要求极低延迟，键盘常驻一个 GB 级模型对产品是负担；三是现实先例，苹果键盘其实已经用神经模型替换了自动纠错，但效果"糟到没人愿意提"，会替换你从没写过的词。值得关注的是：一个看似玩笑的问题，最后收敛成端侧推理最核心的几项约束——上下文获取、延迟、常驻内存。

**高赞评论：**

- u/ticktockbent（赞数 2·归档快照）："Could be pretty easily done but it requires more than just keyboard integration. It would need to send your context, as in whatever you're working on, to give you a good prediction. Mobile keyboards have been predicting words for a long time but they have no access to context"立场说明：指出可行性的关键不在"接一个模型"，而在拿不到上下文这一结构性限制，解释了为什么手机输入法的成熟预测能力没迁移到桌面。
- u/InterstitialLove（赞数 1·归档快照）："Every refutation so far is deeply wrong... the latency is too much. To be useful while typing, users want very low latency"，并补充可能是内存问题，"a keyboard that requires a GB of memory is a pretty bad product"。立场说明：先把其他人的反驳否掉再给出延迟/内存两条硬约束，是本帖唯一从系统层面回答"为什么没人做"的评论。
- u/RutabegaHasenpfeffer（赞数 1·归档快照）："The Apple keyboard does, as it replaces autocorrect/spellcheck. And you don't hear about it because it's TERRIBLE. Substitutes words you have never in your life written down, and insists they're correct."立场说明：用"其实已经有人做了"的现成反例收尾——集成了并不等于好用，说明这个方向被验证过且体验不佳，是对楼主"为什么没人做"最直接的回应。

**原帖链接：** https://www.reddit.com/r/LLM/comments/1wy61wi/
