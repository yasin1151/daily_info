
✅ 已标记 10 篇为已读。以下是今日 HN 推送：

---

# 📡 HackerNews 日报 · 2026-08-28（10 条精选）

## 1. Cloudflare 优化 1.1.1.1 DNS 缓存，省下 100TB 内存
**原文:** https://blog.cloudflare.com/dns-cache-memory-optimization-1111/ · [HN 讨论 (430分)](https://news.ycombinator.com/item?id=49468083)

Cloudflare 对 1.1.1.1 的 DNS 缓存做内存瘦身，全球节省约 100TB 内存。手法很工程化：缓存条目只写不读，于是把 Rust 的 `Vec<String>` 换成 `Box<[T]>`/`Box<str>`，砍掉无用的 capacity 字段和堆预留空间（每条省 64 字节，仅此一项就 15TB+）；把 answer/authority/additional 三个列表合并成单列表加 u16 偏移；布尔字段打包成 bitflag 消掉 padding；CNAME 场景下去掉重复的 record owner。配合自定义 allocator 基准测试验证性能无损。

**值得关注:** 大规模系统里"每条省几十字节"的积累效应——2500 亿条缓存条目 × 微小优化 = 100TB 真金白银。给所有高流量服务的内存优化提供了教科书案例。

> 热评：`jgrahamc`（Cloudflare 联创）回应"早该这么设计"的质疑：premature optimization 的代价是拖慢交付，当时没内存压力，先做对再优化是对的；`stickfigure` 补刀：LLM 已经改变了优化方程——现在让 Claude/Codex 写 harness、profile、跑实验的成本极低，"这类目标明确的小活儿正是 LLM 擅长的"。

## 2. 小模型时代真的来了
**原文:** https://calv.info/small-models-have-arrived · [HN 讨论 (398分)](https://news.ycombinator.com/item?id=49466917)

Calvin French-Owen（前 Segment CEO）实测 gpt-5.6-luna：约 100 tps、速度飞快，跑完几千封邮件的复杂研究线程 API 成本只要几十美分。他认为小模型已到 Pareto 前沿，GLM 5.3 也是新选项。文章核心观点：投资者疑惑"为什么消费级 AI 公司这么少"——答案就是 token 成本；小模型把每请求推理成本打下来，才让"每天为你定制新闻站"这类消费级应用的商业模式成立。

**值得关注:** 成本敏感用户的选择题——大模型（Fable 5、Sol）做重活，小模型跑日常，规模经济开始倒向小模型。AI 应用创业的算力账本正在被改写。

> 热评：`swiftcoder`："追前沿模型的人刚发现小模型早够用了，我们没有天文数字预算的人早就知道了"；`jlkuester7`："32B 参数在消费级硬件本地跑也已经够用"；也有用户实测 Sol/Luna 对比，认为小模型更容易"过度假设、一条道走到黑"，纠偏成本低所以还是选 Luna。

## 3. Gemini Omni 1.1 Flash 发布
**原文:** https://blog.google/innovation-and-ai/technology/developers-tools/build-with-gemini-omni-1-1-flash/ · [HN 讨论 (172分)](https://news.ycombinator.com/item?id=49467922)

Google 发布 Gemini Omni 1.1 Flash，实时多模态（音频/视觉）能力的快速版模型，面向开发者工具链开放。社区讨论焦点不在技术参数，而在 AI 语音对配音/播音行业的冲击。

**值得关注:** 实时 omni 模型进入"Flash"快车道，实时语音交互应用的成本门槛继续下探；同时它把"AI 替代真人声优"的行业焦虑推到了台前。

> 热评：`petcat`："广播里听到一段广告，分不清是真人还是 AI"；`lambda`：配音演员有工会、有罢工谈判筹码，而软件开发者"被说服不需要工会"，面对这种情况没有集体议价能力；`georgemcbay`："'不会发生在我身上'——几乎每个人都这么想，直到它真的开始发生在自己身上"。

## 4. 84 天反编译一个 N64 游戏（全程 LLM 工作流）
**原文:** https://blog.chrislewis.au/decompiling-a-nintendo-64-game-in-84-days/ · [HN 讨论 (163分)](https://news.ycombinator.com/item?id=49466006)

作者用 84 天把一个 N64 游戏完整反编译为可读 C 代码，方法论核心是 LLM 驱动的严格工作流：不是无脑让 AI 生成，而是建立"高质
