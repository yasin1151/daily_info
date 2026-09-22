
# r/LLM 今日热帖推送（2026-09-19）

说明：Reddit 全部端点（www / old / .rss）本轮仍被网络层封锁，redlib 公共实例同样不可达，本推送通过 arctic-shift 归档 API 取数。赞数为归档快照，可能略滞后于实时值，排序仍按归档分数从高到低。

## 1. Uncensored Models（去审查模型到底是什么）

**摘要：** 背景：r/LLM 用户发帖提问，说自己平时玩 AI 和自动化，一直看到"uncensored 模型"这个说法，但从没装过，想知道它究竟是什么。核心：社区给出的解释是对正常模型做 abliteration，也就是用一批"本该拒绝"的有害提示和一批"本不该拒绝"的提示做对比，找出每次都会触发的那个特定拒绝向量并删掉，模型从此不再拒绝，常用工具是 heretic，之后还能再用数据集微调教它新的行为。为什么值得关注：这条讨论把"去审查"从道德口号拆成了具体工程步骤，同时暴露了社区的真实分歧——一派认为它把行为控制权交还用户，可用于研究、安全和敏感话题分析（例如中国模型会拒绝回答在本土语境下正常的问题），另一派指出去审查后的模型常常明显变笨，且大量现实需求其实是成人角色扮演。对关注模型可控性与对齐副作用的人来说，这是低成本了解 abliteration 实践的一手材料。

**高赞评论：**
- u/arcum42（49赞）：「Basically, it normally means someone takes a normal, censored model and does a process called abliteration on it, to prevent it from refusing to do things in its safety alignment... one of the better ones being heretic.」立场说明：这是全帖信息量最高的回答，给出了 abliteration 的完整定义、开源工具链和后续微调流程。
- u/Particular-Award118（22赞）：「Ask it a bunch of prompts it should refuse and equally many it shouldn't. For the harmful prompts, a specific vector will fire every time. Remove this vector. Tada, no longer refuses.」立场说明：用最直白的方式复现了 abliteration 的机制，说明它不是重训而是定向删向量。
- u/Memestonks2020（20赞）：「Uncensored models are exactly like the original except they aren't lobotomized to be aligned with whatever corporate or human moral standards... asking a Chinese model about Tiananmen will make it refuse even though it's perfectly acceptable to discuss in western culture.」立场说明：从"审查标准由谁定义"的角度支持去审查模型，并给出跨文化语境差异的具体例子。

**原帖：** https://www.reddit.com/r/LLM/comments/1wfflu7/

## 2. Running a 744B-parameter MoE model on 32GB RAM with no GPU

**摘要：** 背景：作者用 C11 写了一个纯 CPU 推理引擎，把 202GB GGUF 的 GLM-5.2（744B 参数 MoE）从 USB SSD 流式读取，在一台 i7-8550U、32GB 内存、无 GPU 的笔记本上跑起来，并开源为 pulsarforge（MIT）。核心：真正起作用的手段有四个——专家层用 int4 group-64 量化而 router 与修正偏置保持 f32；每 token 按需拉取专家并配 LRU 缓存与跨层预测预取，离线测得 80.8% 召回；计算与磁盘 IO 按到达顺序重叠而非锁步等待；8GB 专家缓存配合预取拿到 40-66% 命中率，成为延迟的主要杠杆。作者还报告了一个意外发现：GLM-5.2 的 router 权重与真实专家重要度相关性达到 ρ=0.859，接近 oracle 水平，因此可以安全地动态裁剪每 token 使用的专家数而不掉质量。最终从朴素的 196 秒/token 优化到约 9.3 秒/token，提速 21 倍。为什么值得关注：它说明决定推理速度的是每 token 激活参数量而不是总参数规模（Qwen3-30B-A3B 反而比 4B 稠密模型更快），为显存不足的团队提供了"用 SSD 换显存"的可复现路径。

**高赞评论：**
- u/MagnaZee（2赞）：「How does your performance compare to the same CPU, but with everything in RAM instead of streaming from an SSD on USB? Is all of the caching and other improvements just making up for the slow transfer bandwidth?」立场说明：提出最关键的质疑——预取和缓存究竟是真优化还是仅补贴 USB 带宽短板，逼出后续关于 NVMe 的上限讨论。
- u/Dependent_Ideal9870（2赞）：「Qwen3-0.6B runs ~13-15 tok/s here, Qwen3-4B ~2.6. But Qwen3-30B-A3B, bigger on disk than the 4B, comes out faster at ~6.8 tok/s, because it's MoE... Active params per token is the number that predicts speed, not total size.」立场说明：发帖作者本人用跨模型实测数据纠正了"模型越大越慢"的直觉，是理解 MoE 本地部署效率的核心结论。
- u/wwayush（1赞）：「It's really annoying when people running 1bit 2bit quant put the total parameter size of the model instead of mentioning the actual quant.」立场说明：代表社区对量化标注规范化的诉求，也促使作者补充说明本轮数字来自 int4 group-64 配置而非已退休的低比特格式。

**原帖：** https://www.reddit.com/r/LLM/comments/1wdg1vn/

## 3. What's the best small local model for coding right now? (16GB RAM limit)

**摘要：** 背景：用户求推荐 16GB 系统内存下真正能用的本地编码模型，明确说不看大上下文和跑分，只看代码质量、终端与工具调用是否可靠、会不会随机幻觉、会不会陷入死循环、是否足够跟手，并希望找到"Qwen3.8 27B 的年轻表亲"。核心：社区给出的是具体型号加实测条件，而不是抽象建议——Ornith 1.5 9B 被多人推荐但在纯 16GB 系统内存下偏慢，Qwen 3.5 9B 在 8bit 量化下占 9.6-11GB 显存，Ling 3.0 tiny 在一台无独显的 16GB 笔记本上被评价为速度快且"足够好的编码器"，实测稳压多个 4B/9B Qwen；也有人提到 Agents-A1-4B、Maple-Preview，并有用户用 3.7bpw 量化的 Qwen3.8 27B 在 Vega FE 上跑到 16+ token/s，称是第一个"半可用"的 27B。为什么值得关注：这是低成本本地替代闭源 API 最现实的一份选型清单，也说明在内存受限时量化格式和激活参数比绝对参数规模更决定可用性。

**高赞评论：**
- u/XenophobicSemifinal（6赞）：「the 4b-8b range has some surprisingly decent options if you're willing to live with a few quirks... for snappy terminal work on 16gb i'd probably grab one of the 7b/8b models at q4 or q5, ollama makes it dead simple to swap between them.」立场说明：代表务实派立场——16GB 下不要追求全能，用 q4/q5 量化配合 ollama 快速轮换试错即可。
- u/Miller4103（6赞）：「Ornith 1.5 9b is pretty good. Might be kind of slow though. I use it with rtx 5060 ti 16gb vram and it does pretty good work.」立场说明：给出带硬件前提的一手体验，提醒同样的模型在 16GB 系统内存（无独显）下速度会明显掉档。
- u/SnooWalruses6610（3赞）：「Ling3.0 tiny. I run it on a laptop with 16GB system ram (no dedicated GPU). it's fast and a damn decent coder. I've tested against the smaller 4b/9b qwens and it consistently outperforms them all.」立场说明：与提问者硬件条件最接近的推荐，并给了横向对比，是目前最可复现的答案。

**原帖：** https://www.reddit.com/r/LLM/comments/1wdkbtb/

## 4. 为什么大家都说 Gemini 很差，但它在榜单上分数一直不错

**摘要：** 背景：用户发帖提问，说自己并不常用 Gemini，但测试时发现它在推理、单任务成本等基准上得分一直不错，好奇为什么社区评价与榜单分数如此脱节。核心：评论区分成了两条主线。第一条是"产品 vs 模型"，有人强调要分开看 Gemini 消费端产品与模型家族，认为消费端以速度优先、定位是找菜谱和设提醒，真正的短板在 prompt/上下文工程与 harness 层，并有人举出具体案例：在 Gemini 应用里用带 notebook 知识库的 Gem 时，模型会被注入其他对话的随机片段；也有人纠正了"Gemma 是 Gemini 蒸馏产物"的说法。第二条是"榜单是否被刷分"，有人用测试饱和的类比质疑跑分，另一人给出具体证据说 3.8 Flash 在新引入的基准上分数大幅回落，TerminalBench 直接被"打回原形"。为什么值得关注：它把"榜单分数 vs 实际体验"的争论落到可验证的细节上，也说明选型时产品层工程（harness、上下文管理）和模型权重同样重要。

**高赞评论：**
- u/Reddit_Fu_Sucks（5赞）：「There are 2 parts to this. Gemini frontend (Gemini AI) and Backend (Gemma etc)... Gemini AI is designed poorly and targets speed over accuracy. It is essentially intended to help people search for recipes or the nearest store or set a reminder.」立场说明：提出整帖最有解释力的框架——问题出在消费端产品设计而非模型能力，后续争论都围绕这个区分展开。
- u/jomi-se（2赞）：「Google so far seems to be far behind in prompt/context engineering and harness engineering on their AI based products... on the Gemini app when I had a Gem that had a notebook as knowledge base... gemini would be injected with random parts of other conversation.」立场说明：把批评精确到 harness 与上下文隔离层，并给出可复现的串话案例，比笼统骂模型更有工程价值。
- u/Mean-Elk-9439（1赞）：「3.8 flash uniquely has a massive score loss across new benchmarks phased in to test models that were trained too heavily on the old ones. Terminalbench is good example, where it had its score nuked.」立场说明：给出"旧榜虚高、新榜回落"的具体证据，是支持刷分质疑一方最实的一条。

**原帖：** https://www.reddit.com/r/LLM/comments/1wcsmqn/
