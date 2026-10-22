
r/LLM 今日推送（Reddit 全端点仍是 `http=000` 网络层封锁，数据经归档接口获取）

说明：今日 r/LLM 真实评论达到 3 条以上的帖子极少，只保留两条合格内容；赞数为归档快照，可能滞后，不作为热度结论。

---

## 1. 那些「让 LLM 重写代码还更快」的视频，到底靠什么做出来

**摘要：**

有人被「让 LLM 重写整个项目、性能还更好」的视频骗去实践：他把范围缩到一个 bug 很多的 Discord 主题 CSS 目录，让 Sonnet 5.5 思考模式找问题，结果模型找不到真问题，反而编造出并不存在的缺陷，于是他追问复现这类演示到底缺什么。评论区的答案相当一致：视频高度挑选过，没人给你看前面那 47 次失败；真正起作用的是把代码切成自包含的小块，而不是整仓丢进聊天框；CSS 尤其难，因为视觉行为取决于 DOM 结构、浏览器渲染怪癖和层叠规则，光读原始代码推不出来。另有人强调必须上 harness：写清 PRD，用 Claude Code 或 Codex 让 Opus 级模型做编排、拆子任务、指定模型与约束，再放开跑几小时；查性能问题要给性能 trace，只看 CSS 看不出 paint 成本。也有人提醒别指望超过四十分钟的高质量连续工作。值得关注的是，这类「一句话重写」神话的真正门槛是任务拆分、工具链和测量手段，不是聊天窗口里的提示词。

**高赞评论：**

- u/First_Artichoke_4707（赞数 2·归档快照）：「they're not all fake but they're heavily cherrypicked」，制作者不会展示前面 47 次失败；他们实际做的是「feeding the LLM small self-contained chunks of code, not entire repos」，并建议把问题切成最小可复现单元再交给模型。立场说明：这是对「演示效果」最直接的祛魅，把可复现性归因到任务切分而不是模型魔法。
- u/BonyCatButt（赞数 1·归档快照）：要配 PRD 和真正的 harness，并指出「Sonnet is bad at long running tasks」，建议「you would run an orchestrator like Opus 5.5 then tell it to use subagents」，交代清楚约束、自主决策范围和无人值守模式。立场说明：把成功案例拆成编排层与子代理分工，说明长时间任务靠的是架构不是单次提示。
- u/Ctbhatia（赞数 1·归档快照）：「give it the performance trace, css alone wont show it the paint cost」。立场说明：一句话点出模型缺的是测量输入，性能问题必须喂 trace 这类可观测数据，否则只能得到猜测式修复。

原帖：https://www.reddit.com/r/LLM/comments/1xbgr4x/

---

## 2. DeepSeek 网页版「承认」抄了竞争对手？评论区在纠正三个误解

**摘要：**

r/LLM 上有人贴出与 DeepSeek 网页版的对话截图，称它两次「承认」自己基于 ChatGPT 或 Gemini，于是质问 DeepSeek 是不是抄了对手。评论区反应分三层。技术上，模型在没有 harness 指定身份时根本不知道自己叫什么，换成 Claude 或 ChatGPT 裸聊也会自报错家门，所以这类自述不能当厂商认罪。事实上，DeepSeek 蒸馏其他模型早就是公开常识，有人用「水也是湿的」来形容这事毫不稀奇。情绪上老用户已经疲了，质问 2026 年还有人问这个、发帖前能不能先搜一下。这条帖子分数很低，但它把三个常见误解集中暴露出来：把模型自述当事实、把蒸馏当丑闻、以及同一个问题每隔几周轮回一次。对做产品的人来说，可操作的结论是别拿模型的自我介绍做合规或溯源判断，模型身份应由部署侧的系统提示与评测来定义，而蒸馏与否该看技术报告和权重行为，不是看聊天记录。

**高赞评论：**

- u/Fine-Drummer2604（赞数 2·归档快照）：模型若不在「specific harness that lets them know what they are and what their model name is」里运行，就「have absolutely no clue」，换成 Claude 或 ChatGPT 裸聊同样如此。立场说明：这是最有信息量的一条，直接解释了「模型自称是谁」为什么不构成证据。
- u/Sevealin_（赞数 1·归档快照）：「Yes DeepSeek distills other models. Water is also wet.」立场说明：把蒸馏还原成行业常态，语气里的不耐烦本身也说明社区对这条指控早已脱敏。
- u/Choice_Celery9481（赞数 2·归档快照）：「2026 and still people with this question???? cant move a finger to do a single google search before posting?」立场说明：代表老用户的疲劳感，也提示这类截图帖在版内已属重复内容，讨论价值主要在于纠正认知而非新闻本身。

原帖：https://www.reddit.com/r/LLM/comments/1xbloq4/

---

抓取与质检备注：八窗口归档（0–288h）去重 195 个候选，其中 137 个未推过（已排除前一天已推的 3 条新帖）；逐个拉评论树后，非楼主独立作者 ≥3 的仅上述 2 帖。今日被跳过的高热度帖包括 54 分、80 条评论的意识定义之争（属无证据的自我意识讨论）、以及 Meta Muse Spark 816B、Intel Dokimi、GLM-5.3 架构可视化等零评论帖——题材虽好但凑不满 3 条真实评论，按规则不补写。最终质检 `QA_OK sections=2 links=2`（摘要 CJK 294 / 281），8 条英文引文与归档原文逐条比对 `problems=0`。
