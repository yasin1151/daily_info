
# r/LLM 热帖 · 2026-11-21

说明：本机访问 Reddit 的三个端点与 redlib 公共实例仍然全部超时（`000`），rss2json 明确回复「Reddit stopped serving RSS feeds on 13 November 2026」，因此本期只有归档接口一条通道。r/LLM 这两天依然很安静：把窗口一路拉到 65 天、逐个拉了 371 个帖子的评论树，真正有 3 条以上实质发言的帖子只有个位数，其中大半是纯情绪帖、meme 或自推项目。下面两条是本期过滤后留下的，评论赞数是归档快照，可能滞后，不代表真实热度。

---

## 1. 有人做了个「benchmark 完整性审计」榜单，专门对付 Terminal-Bench 这类题目答案全公开的跑分

**摘要：** 一位 r/LLM 用户搭了 benchaudit.org，起因很直白：Terminal-Bench 4.0 这类热门 benchmark 的题目和答案全都公开在 GitHub 上，前沿实验室想刷分几乎没有成本，而 Artificial Analysis 这类榜单并不做区分，照样把低质量 benchmark 的分数加权进总分。他的方案是先对每个 benchmark 做完整性审计，再给出一份「干净」的模型排名，并强调不是推广、想听真实反馈。评论区把问题推向了更硬的层面：开放权重模型存在时间污染——如果某个 benchmark 的发布时间晚于模型的训练数据截止时间，它就不该被当成「模型没刷过」的干净证据；另外榜单默认跑满推理档位，与实际使用场景脱节。作者回应会给 benchmark 元数据补上发布日期，凡是晚于开放权重模型发布时间的低阶 benchmark，一律从「低分补偿」计算里剔除，但仍保留在细分表里并标注 pre-release。对做模型选型的人来说，这套「审计 + 元数据」的拆法比看总分更实用。

**高赞评论：**

- u/Realistic_Gap_5871（赞数 3·归档快照）："would it make sense to take into account when they were trained/released vs when non-private benchmarks came out" … "what if the benchmark is recent enough to be unavailable for benchmaxxing an older model, whether intentional or through scrapes?" 立场说明：这条把「刷分」从主观作弊扩展成客观的时间污染问题——老模型没机会见过新 benchmark，反而是干净的，榜单如果不区分先后顺序，就会系统性低估老模型、高估刚发布的模型。
- u/Crinkez（赞数 1·归档快照）："every one of those is ran on max reasoning, which no sane person uses" … "allows users to hide reasoning levels?" 立场说明：质疑跑分条件本身不可比——榜单默认把推理档位拉满，而日常使用里没人这么跑，建议像 slopalytics 那样让用户自己切换推理档位看排名，等于指出「单一分数」这件事本身就掩盖了成本与延迟的取舍。
- u/Bramoments（赞数 1·归档快照）："a lot of the difference between this and artificial analysis comes from the equal weighting part for knowledge,coding" … "AA measures coding as much more important than the rest by design" 立场说明：提出一个反向解释——两家榜单的差异未必来自对方被 benchmaxxed，而是权重设计不同，AA 本来就把 coding 权重放得更高；这是社区里少见的「先怀疑方法论而不是先怀疑对手」的发言。

原帖：https://www.reddit.com/r/LLM/comments/1y136ci/

---

## 2. 「能不能做一种字体，让人一眼看出这段是 AI 写的」——顺手把数字水印的真实机制讲清楚了

**摘要：** 有人提问：既然 Anthropic 等厂商会在模型输出里嵌入不可见的机器可读水印，那能不能设计一种字体，让整段文字在视觉上就呈现出「AI 写的」特征，从而人工一眼识别。讨论先纠正了一半题目：模型选什么字体、偏好什么排版并不是重点，字体本身承载不了「谁写的」这个信息。更关键的是第三条回复把现有水印机制说透了——所谓数字水印并不是往字符里塞额外符号，而是一套统计检验：用同一个模型把每个 token 重新生成一遍，比对实际输出与模型自身高概率分布的重合程度，重合度越高越可能是该模型生成的；除了弯引号、en dash/em dash 这类排版细节，文本本身不带任何额外标记。所以靠换字体在视觉层面识别 AI 文本这条路走不通。对做内容溯源、审稿与合规的人来说，价值在于把「水印」从神秘概念还原成了一个可复现、也可被改写的概率测试。

**高赞评论：**

- u/EchoImpossible7697（赞数 1·归档快照）："Ai is already using very distinctive fonts when you ask it to create a design or a website" … "i'm not sure i see how it would change anything right now" 立场说明：先把提问里的混淆点挑出来——大家看到的「AI 味」其实是模型在生成设计稿时的字体与排版偏好，不是文本内嵌了可检测标记，因此换字体解决不了识别问题。
- u/AnastasisKon（赞数 1·归档快照，楼主）："the point is not what font the AI chooses, but the shape of the whole text" 立场说明：楼主澄清原意——不是问模型爱用什么字体，而是问能不能设计一种字体，使整段文本在视觉上暴露生成来源；这条把讨论从「风格像不像」拉回到「有没有可判定的视觉特征」。
- u/ricperry1（赞数 1·归档快照）："The digital watermarking is a statistical analysis that basically re-generates each word (token) of the content" … "It doesn’t actually use other characters other than curly quotes or en/em-dashes" 立场说明：这是全帖信息量最大的一条——水印是拿同一模型重生成、比对概率分布的统计检验，文本里不会多出任何特殊字符，所以「用某种字体把 AI 文本显形」在原理上就不成立。

原帖：https://www.reddit.com/r/LLM/comments/1y0zd1d/
