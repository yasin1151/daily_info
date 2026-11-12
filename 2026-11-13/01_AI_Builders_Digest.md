
**AI Builders Digest — 2026-11-13**

数据源抓取于 2026-11-12 06:28 UTC（约 1 天前）。本期 16 位 builder、32 条推文、1 期播客，无官方博客更新。

---

## 一、基础设施：谁在用谁的模型（本期最硬的料）

**Nikunj Kothari（fpvventures 合伙人）** 抓了 803 家公司的 subprocessor（子处理商）名单，做了第二版基础设施普查，和今年 3 月的版本对比。结论比任何行业报告都直接：

- 44% 的公司同时挂两家以上模型供应商，3 月还是 33%。样本不大，但 **Anthropic 的增速是 OpenAI 的两倍**。
- 33% 的公司明确列了推理服务商，3 月是 22%，**Modal 继续强势扩张**。
- 出现 86 对「互相把对方写进 subprocessor」的组合，比如 Anthropic 与 Cloudflare、Vercel 与 SpaceXAI。
- 中国模型主要通过**视频**（字节这类）进入这些公司的技术栈，而不是文本模型，至少在名单上看是这样。
- 他自己点名 **typesafeai 是今年的黑马**，短时间内从 0 变成一堆公司的供应商。

他补了一句很关键的限定：subprocessor 名单是滞后指标，但它是「这家公司确实在用某样东西」的确定证据。原始数据在 deploygraph.com。
https://x.com/nikunj/status/2120669243918418237

---

## 二、Agent 与工作方式

**Dan Shipper（Every CEO）** 发了本期最长的一篇，也是他播客闭幕演讲的文字版。核心不是「AI 有多强」，而是「强了之后人还剩什么」：

他用 Fable 5.2 在自己一周的碎片时间里做了原本要五个人、二十万美元的活：分析客户问卷、做团队小游戏、发现对团队销售的机会、搭了个 CRM、开始外联。OpenAI 的 GDPval 基准上，AI 击败人类专家的比例从 2024 年的 12.4% 涨到 2026 年的约 83%。但他说聚合曲线漏掉了一件事。

同一份问卷、同一批模型，给全团队每个人都看一遍，四个人读出四种完全不同的东西：他看到「卖给团队」的机会，Yash 看到首次订阅者因为邮件太多而流失，Douglas 发现很多读者感到孤独（周围人觉得他们疯了），Jack 把它做成一档黏土动画游戏节目。

他引用了同事 hammer_mt 的实验：让 Claude 预测他在 Slack 里会说什么，给 400 次尝试，能产出和他一样的答案的概率是 93%；但让模型对自己的答案排序时，他真正会说的那句只有 60% 的概率落进前 10%。他的结论是**「生成可能性很便宜，知道哪个重要很难」**。

对「模型迟早会学会排序」这个反驳，他给了一个挺漂亮的拆解：大家比的其实是「2026 的 Yash vs 2027 的 Claude」，但 2027 年 Yash 也在，而且用的是 2027 的 Claude，两边可以约掉；剩下真正的问题变成「你要一个有具体责任和视角的人，还是要一个默认 prompt」。所以衡量 AI 的方式也该变，别只问模型在公认值得解决的问题上多强，要问「它做我的活做得怎么样」。
https://x.com/danshipper/status/2120539547620790424

**Thariq（前 Claude Code 团队）** 在 AIE Code 拿到了闭幕 keynote（因为那时候人已经累了或者赶飞机），题目叫「the sweet side of the bitter lesson」。他明说内容是关于**明年用 coding agent 的体验可以是什么样、以及这个体验怎么被塑造出来**。这条只有 117 个赞，但题目本身是本期最值得盯的一个方向性信号。
https://x.com/trq212/status/2120621112807866620

**Thibault Sottiaux（OpenAI，Codex & ChatGPT）** 只发了两句含糊的话：「Thursday is feeling codexy to me. Perhaps also a good time for a banked reset.」和「It's been a while without resets. Maybe I should come back out of the basement」。两条合计近 2.8 万赞。这是他一贯的预告风格，指向**Codex 额度重置**，不是官方公告，别当成已确认。
https://x.com/thsottiaux/status/2120410480204525936

**Peter Steinberger（OpenClaw）** 只吐了一句：「读这些评论让我的脑子疼。开源已经够难了，就别再搞政治了。」指向开源圈最近的政治化争吵。
https://x.com/steipete/status/2120711266759258616

---

## 三、产品与工具

**Guillermo Rauch（Vercel CEO）** 三条：一是反 AI 万能论的表态，「做出好东西仍然需要巨量的人类专注、努力、动机、爱，以及注意力跨度」；二是他们在给框架启动速度做基准测试，拿去和「极致优化过的纯汇编版本」比；三是 Beam by Reflection 免费开放到 11 月 12 日，主打**美国开源权重 + 零数据留存**。
https://x.com/rauchg/status/2120601000176439478
https://x.com/rauchg/status/2120581196363268265

**Google Labs** 上线新实验 **Tabletop**：把链接和文件丢进一个共享空间，拉上人，然后让模型现场生成各种定制空间，公路旅行地图、晚餐决策转盘、匹克球赛程、拖拽式座位表。目前仅美国 18+ 排队。
https://x.com/GoogleLabs/status/2120549258692882702

---

## 四、产业判断

**Aditya Agarwal（SPC 普通合伙人，前 Dropbox CTO）** 把当下值得做的公司分成两类。第一类「AI 的扩散」，就是今天的垂直 SaaS，把 AI 推到实际干活的地方，代表是 Profound、Cognition、Harvey。第二类是「AI 的前沿」，用 AI 加速科研、再从科研里长出产品，他认为**模型驱动的回报绝大部分会来自这一类，但外部几乎没人讨论**。他举的组合：Externa 往蛋白质里加化学构件、Epana Bio 用基因组做自免疫疗法、VenomicsAI 从毒液里做药、Equivariant 做半导体多物理场建模。
https://x.com/adityaag/status/2120578134177464356

---

## 五、圈内舆论：Jensen Huang 事件

这块不涉及技术，但昨天的 AI 时间线基本被它占满，几位 builder 的发言有代表性，收在这里。

- **Peter Yang**（2019 赞）：「我对 Jensen 太失望了。那么多人仰望他，包括我。从洗碗工和服务员做到全球市值最高公司的 CEO，和大学恋人结婚 41 年。到底发生了什么？」他随后补了一句更冷静的：「我觉得他出轨很恶心，但这和被解雇是两件事。董事会动手之前应该做正经调查，让股东参与决定。Jensen 建了一家时代级的公司这点无可否认。」
- **Amjad Masad（Replit CEO）**（3430 赞）直接质疑时机：「为什么这些根本没怎么遮掩的旧事会突然变成国际地缘新闻？时机很可疑，值得问一句：谁受益，为什么是现在？如果 Jensen 这个开放模型头号旗手被拿掉，想让 AI 封闭、集中、可控的人会受益。为什么是现在？中期选举有关，即将到来的 IPO 可能也有关。」
- **Garry Tan（YC 总裁）**：「考虑到他对我们未来丰裕引擎的运转有多核心，NVIDIA 董事会罢免他看起来非常不明智。他的日常是主力演员级别的工作。很难相信这场交接不会伴随市值崩塌。」
- **Matt Turck（FirstMark）** 只留了一句「第二个 Jensen 故事浮出水面，法国高管们」，指向还有后续。

---

*Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders*
