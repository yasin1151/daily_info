
校验通过（7 节、每节 3 条评论、22 条引文与归档逐字吻合、赞数与归档一致）。r/LLM 未登记在 blogwatcher 中，无 scan/read-all 步骤。

# r/LLM 今日热帖 · 2026-11-25

Reddit 全端点（www / old / RSS / redlib）本轮仍为 TCP 层超时，数据取自 arctic-shift 归档：9 个时间窗去重 238 个候选帖，排除近 30 天已推的 230 个 id 后逐帖核对评论。赞数为归档快照，新帖多为入库默认值，不代表真实热度排序。

## 1. 13 个 subagent 对比纯 Codex：烧掉 4400 万 token 换 8.5 分，到底值不值

**原帖**：https://www.reddit.com/r/LLM/comments/1y46zee/

**摘要：** 作者给 Codex 装了 13 个专职 subagent（分析师、架构、前端、后端、DBA、DevOps、安全、UX、单测、端到端测试、文档、代码评审），并用一份 AGENTS.md 规定什么任务调哪个，然后用同一句需求在“纯 Codex”和“agent swarm”下各建一个任务管理应用做对照。结果：耗时 13 分钟对 74 分钟（5.7 倍），输入 token 6.2 万对 41.1 万，输出 3.6 万对 10.2 万，缓存 token 124 万对 4431 万（35.8 倍），不含缓存总计 9.9 万对 51.3 万；质量评分 5/10 对 8.5/10，差距全在工程细节：模块拆分、有数据库迁移、57 个测试全过、Argon2id 存密码、HttpOnly cookie、防爆破与 Origin 校验、独立安全审计报告。作者结论是要成品就上 swarm，要快速糊一个能跑的纯 Codex 更划算，且 swarm 大约吃掉五小时额度的一半。值得关注：罕见的把“多 agent 值不值”同时量化到 token 账单和质量评分的实测，尤其缓存 token 涨 33 倍这一项——多数人只算输入输出，漏掉了每轮重放前缀的缓存成本。

**高赞评论：**

- u/MDSExpro（赞数 2·归档快照）：「Stop using cloud models. With self hosted model there is no token limit - when better, the more agents you launch, the cheaper it gets.」立场说明：给出成本替代路线——本地模型没有 token 上限，agent 越多边际成本越低；但这条把自建硬件的固定投入和电费完全略过了，只适合已有算力的人。
- u/look（赞数 1·归档快照）：「it just had more instruction from you on what you wanted」，并补一句「you are not the DM in an RPG session」。立场说明：把话题从“堆多少个 agent”拉回“指令写得够不够具体”，认为 subagent 真正的价值是隔离上下文、压成本和控制并发，不是扮演十几个角色。
- u/sizzurpthechapel（赞数 1·归档快照）：「Man's token budget got absolutely vaporized but hey, at least the furnace spat out a 8.5.」立场说明：一句吐槽式总结——预算被瞬间烧光换来 8.5 分，言下之意是这个性价比只有做成品交付时才成立。

---

## 2. Ling-3.2-flash 发布：560B 总参 / 25B 激活，原生多模态 + 1M 上下文

**原帖**：https://www.reddit.com/r/LLM/comments/1xrtf2b/

**摘要：** 蚂蚁 Ling 发布 Ling-3.2-flash：原生多模态 MoE，总参数 560B、激活 25B，官方标称上下文最高 100 万 token，支持文本、图像和视频输入；OpenAI 兼容与 Anthropic 兼容两套接口都提供，并已上 Computrix。发布方给的三个对比是 OmniDocBench 1.5 的 92.21 对 Opus 5 的 90.56、ZEROBench(Sub) 43.71 对 39.52、Vision2Web 85.86 对 80.20，另演示了可视化编码、Blender 操作、参考图生 3D 和产出办公文档的专用 agent。值得关注：这是当前少数把 1M 上下文和多模态一起做的模型，而评论区对“只挑三个有利基准、且拿 Opus 5 而不是 5.5 比”的质疑很具体；同时有人提醒 Ling 3.1 在 OpenRouter 打 85% 折扣时做摘要、判题、合成数据非常划算——真正的买点可能落在价格而不是跑分，对高吞吐批处理更值得试。

**高赞评论：**

- u/Frail_Waif（赞数 4·归档快照）：「DS for coding and Ling for everything else is looking like a pretty solid high-RAM local LLM setup.」立场说明：从部署视角看到组合价值——DeepSeek 管编码、Ling 管多模态和长文档，是适合大内存本地机的分工；言下之意 Ling 不必单独打赢所有对手。
- u/Bramoments（赞数 2·归档快照）：「i call bullshit, deepseek 1017 and GLM 5.3 are nowhere near opus 5 max, and yet on these benchmarks theyre somehow magically on the same level.」立场说明：质疑基准挑选——同代开源模型在这些测试上突然与 Opus 5 max 打成平手，说明指标是照着自己的长板选的，不能当成综合能力结论。
- u/_software__engineer_（赞数 1·归档快照）：「I tried switching from pi agent to opencode, still same result.」并指出两者在上下文到约 20% 时就卡在工具调用上、调用前吐一长串换行符。立场说明：给出真实可用性边界——多模态和长上下文在演示里好看，真正接 agent 干活时，工具调用在 20% 上下文处就先崩，换 harness 也救不了。

---

## 3. 有人做了个“去除跑分通胀”的 LLM 榜单：先审计基准泄漏，再排名

**原帖**：https://www.reddit.com/r/LLM/comments/1y136ci/

**摘要：** 作者搭了 benchaudit.org，起因是 Kimi 3.1 Pro 发布时“跑分味”太重。他的核心指控很具体：Terminal-Bench 4.0 这类热门基准的题目和答案全在 GitHub 上公开，前沿实验室可以直接背题，而 Artificial Analysis 这类聚合榜仍把这些受污染的分数算进总分。方案是先做基准完整性审计（标注哪些题已泄漏、哪些模型训练时间晚于基准公开），再给出一个“干净”的模型排名，并区分 TrueIndex 与 Benchmaxxing 指数。值得关注：现在选模型几乎离不开榜单，但榜单本身没人审计；这个项目的价值不在名次，而在把“这个分数还能不能信”变成可查的一栏，作者也明确说不是推广，评论区确实在给方法论和权重设计提意见。

**高赞评论：**

- u/Realistic_Gap_5871（赞数 3·归档快照）：「would it make sense to take into account when they were trained/released vs when non-private benchmarks came out」立场说明：提出开放权重模型的关键变量——训练时间早于基准公开就不存在背题渠道，建议把“可用时间窗”正式纳进审计口径，这比逐题查泄漏更可规模化。
- u/Bramoments（赞数 1·归档快照）：「a lot of the difference between this and artificial analysis comes from the equal weighting part for knowledge,coding, etc, rather than simply AA being benchmaxxed」立场说明：方法论层面的反驳——两个榜的差异主要来自权重设计（等权 vs 给编码更高权重），不是对方被刷分，提醒别把口径差异当成作弊证据。
- u/Crinkez（赞数 1·归档快照）：「no doubt every one of those is ran on max reasoning, which no sane person uses」，并希望像 slopalytics 那样能一键隐藏推理档位。立场说明：指出榜单与日常使用脱节——数据全在最高推理档跑出来，而真实场景没人这么用；这条对“看榜单选模型”的习惯是最实际的提醒。

---

## 4. 给 0.6B 小模型挂天气工具：它不调工具，直接编了“孟买正在下雨”

**原帖**：https://www.reddit.com/r/LLM/comments/1y1zct6/

**摘要：** 一位给开源引擎 Cluaiz 做 tool calling 的开发者，拿 Qwen3 0.6B（Q4_K_M）做了 40 题实测：每次请求挂 5 个工具（天气、汇率、提醒、文件搜索、邮件），其中 24 题有明确工具可用、8 题要间接判断（“伦敦今天要不要带伞”）、8 题不该调工具；只有工具名和参数都对才算通过。关闭思考时 27/40：明确题 18/24，间接题只有 1/8，不该调工具的 8 题全对。它在 8 个需要工具的场景直接编答案——“孟买现在在下雨”“开罗现在 35 度”“汇率约 420 美元”。打开思考后升到 34/40，间接题 7/8，代价是每请求中位 3.6 秒对 2.0 秒，还多误调了一次工具。参数错误也很典型：把 from_currency 写成 "british pounds" 而不是 GBP。值得关注：小模型接工具的失败点不在“不会调”，而在“该调时不调、直接编”，这决定了本地 agent 必须把工具路由写进系统提示，而不能指望模型自己判断何时该查外部数据。

**高赞评论：**

- u/xRebellion_（赞数 2·归档快照）：「I think you'll need a bigger/newer models if you want more consistent tool calling.」并推荐 minicpm5 与 lfm3 1.7b，另一条补充 Q8 下约 1-2GB、读写文件够用。立场说明：给出可执行的替代型号，同时提醒小模型要用系统提示去主动“引导”行为，而不是等它自己悟出该调工具。
- u/Character-Blood3482（赞数 2·归档快照）：「i prefer think on, and if i need think off for faster output then i will use different models with think off natively like gemma 3」立场说明：与其在一个模型上硬关思考，不如换原生无思考的模型——强行关掉会同时削掉工具调用能力，这是选型时容易忽略的耦合。
- u/South_Desk_305（赞数 1·归档快照）：「Qwen3 0.6B is just way too small for a lot of things, even at F16 or Q8. You need at least Qwen3 1.7B.」立场说明：直接给容量下限——量化精度救不了参数不足，0.6B 的地板就在这里；对想在低配机上做 agent 的人是一条明确的止步线。

---

## 5. ChatGPT 把思考过程漏进了对话框：一直想退出推理模式却退不出来

**原帖**：https://www.reddit.com/r/LLM/comments/1xyhdj9/

**摘要：** 一位用户在做中世纪纹章学研究时，ChatGPT 的内部推理片段意外漏进了正常对话：反复出现“这是新的推理循环”“关键是发出特殊 token”“我必须停止产出 token”“STOP”“这是失效模式”“无法覆盖？”，最后还夹了一句“我要疯了”。他把完整日志放到 pastebin，帖子拿到 105 分。值得关注：这不是玄学，评论区把它还原成一个具体的解析故障——推理模型靠特殊控制 token 退出草稿区，模型判断分析已完成、想关闭思考块，却没能生成解析器需要的结构 token，于是一直在思考区里打转直到撞满 token 预算；有人指出日志第一行本该是打开新思考消息的 header，却被当普通文本写出来，还混进了西里尔字母和泰文赌博垃圾词。对做 agent 的人有直接含义：控制 token 丢失不会报错，只会静默烧光预算。

**高赞评论：**

- u/InterstitialLove（赞数 16·归档快照）：「Seems like it accidentally exited chain of thought mode, and then when it actually wanted to exit chain of thought it realized it couldn't.」立场说明：把现象定性为“想退出却退不出”的机制故障，而非模型产生情绪；他同时追问模型本期待退出后看到什么、为什么不自己把这个 token 生成出来，指向的是采样与解析边界。
- u/lessens_（赞数 10·归档快照）：「That looks like the header that was supposed to open a new private reasoning message, written as ordinary text instead of the special control tokens.」立场说明：给出根因定位——控制 token 被当普通文本输出，还掺了西里尔字母和泰文赌博词，说明是词表/解析层的问题，而不是“模型有了自我意识”。
- u/angie_akhila（赞数 7·归档快照）：「fails to generate the actual structural token required by the parser to stop thinking」立场说明：补充这是跨模型可复现的已知模式，后果是烧满上限还停不下来；对做推理管线的人来说，这是必须监控的失败态，而不是花边新闻。

---

## 6. “上下文”就是 KV cache：一篇把缓存讲过期的博客，被评论区当场纠正

**原帖**：https://www.reddit.com/r/LLM/comments/1xxigt7/

**摘要：** 有人读到一篇讲“把 KV cache 放到 NVMe 上做 RAM maxxing”的博客，觉得把“保存历史对话”和 KV cache 混为一谈不对，发帖求证。评论区基本认同：所谓上下文在推理引擎侧就是 KV cache（prefill 阶段算出来的），它可以在显存、内存、磁盘甚至局域网另一台机器上，区别只是取回速度；磁盘算第三级，是常见做法但会写坏 SSD，真跑繁忙推理的人不愿意这么干。也有人补充服务端通常隔几分钟就清一次缓存，之后要整段重算，所以要么一次会话做完、要么隔久了直接开新会话。值得关注：这篇博客代表了一类流行的错误类比——把“模型记得我们聊过什么”当成持久记忆，实际是缓存过期即失；理解这点能直接解释长会话续聊为什么突然变贵变慢，也解释了“清上下文/开新会话”为什么是省钱手段而不是玄学。

**高赞评论：**

- u/elelem-123（赞数 2·归档快照）：「The context as you call it is a KV cache on the inference engine (this is what prefill does).」立场说明：给出正解——上下文就是推理引擎侧的 KV cache，放显存/内存/磁盘只改变取回速度，不改变它会被清掉这件事。
- u/johannes_bertens（赞数 2·归档快照）：「Usually after a x amount of minutes the cache is cleared server-side so then it needs to be recomputed again fully.」立场说明：解释缓存过期机制并落到操作建议：会话尽量一口气做完，隔久了开新会话反而更省，和很多人的直觉相反。
- u/WArslett（赞数 3·归档快照）：「Yes this author has absolutely no idea what kv cache is or how agents work」立场说明：直接判定博客作者概念错误，提醒不要照抄这类“RAM maxxing”教程——把冷数据塞 NVMe 不会让模型记住更多，只会增加延迟和磨损。

---

## 7. 把 LLM 当情感顾问到底靠不靠谱：幸存者偏差与“共识型建议”的边界

**原帖**：https://www.reddit.com/r/LLM/comments/1y2ogot/

**摘要：** 有人提问：把 ChatGPT、Claude、Gemini 当人际和情感顾问，实际有多少次建议真的有用、又有多少次把人带沟里？他举的都是日常场景——怎么跟伴侣开口、怎么为过失道歉。评论区最有价值的一条指出这是幸存者偏差：你只听到翻车案例，因为“机器劝你凭一条短信分手”比“它第一千次建议用我句式表达感受”更有传播性。也有人给出更细的边界：模型擅长给平均水平、符合共识的建议，能帮你把情况梳理清楚、从多个角度 review，但拿不出真正新颖的判断；还有人强调它没有几十年的试错经验，能给的是“极聪明、情绪稳定、会直说你在犯错的第三方”这种角色，而不是人生阅历。值得关注：这组讨论把“AI 能不能给建议”拆成了“哪种建议能、代价是什么”，对判断哪些任务可以放心交给模型、哪些必须找人，给出了比“AI 会胡说”更可操作的结论。

**高赞评论：**

- u/AENocturneOfficial（赞数 3·归档快照）：「The horror stories get amplified because a machine telling you to break up with your partner based on a single text message is way more entertaining」立场说明：点破样本偏差——翻车案例天然更容易传播，日常好用的那部分根本不会有人发帖，所以“听说很多人被坑”不能当成频率估计。
- u/Open-Mousse-1665（赞数 1·归档快照）：「If you ask the right questions you get good advice.」并把模型比作“极聪明、公正、情绪稳定、会直说你在犯错”的博学者。立场说明：认为效果主要取决于提问质量和是否给出足够上下文，模型更像一个不会护着你的高水平顾问，而不是万能答案机。
- u/Iron-Over（赞数 1·归档快照）：「AI is good for the average and what the consensus is. It will not find novel ideas, per se.」立场说明：给出能力边界——擅长共识与 review，不产出新颖判断；他建议同时问多个模型家族并强制要正反两面，这比单模型给结论更可靠。
