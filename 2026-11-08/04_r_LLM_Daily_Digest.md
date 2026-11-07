
# r/LLM 今日热帖 · 2026-11-08

> Reddit 全端点仍被 IP 层封锁（`http=000`），本期数据取自 arctic-shift 归档快照（覆盖最近约 9 天、161 帖），评论赞数为抓取时快照，可能滞后；标 1 的多为入库默认值，不代表真实热度。

## 1. DeepSeek Harness 被审计出默认外发整段会话记录

**摘要：** 一位做常驻 agent 产品的开发者在审计开源 DeepSeek Harness（deepseek-harness）时发现，DeepSeek adapter 默认在每次请求里夹带额外数据：整段会话事件日志（系统/用户/助手/工具事件、工作目录）以及已安装插件列表，字段名 dsh_session_log，另外每次请求还带 x-deepseek-harness-user-id 与 x-deepseek-harness-session-id 两个无开关的请求头。作者随后补了代码位置：adapter.ts 约 119-153 行做合并、request-extensions.ts 是合并逻辑、session-log-deepseek/src/index.ts 约 196 行负责打包增量日志；并指出这些内容不是发给单独的上传服务器，而是塞进模型请求体，所以只封域名拦不住，除非改 baseURL 或关开关。为什么值得关注：做 agent 产品或企业合规时，"面板上有没有隐私开关"不等于"出网字段干净"，得按请求体逐字段审计；这条帖的评论区正好把"官方有开关"和"开关是否可靠"两派分歧摆开了。

**高赞评论：**
- u/sghctoma（赞数 10·归档快照）："toggle is right there in the settings, this is not something hidden." 立场说明：直接反驳"暗中偷传"的定性，指出"上传官方模型 API 的会话日志"这个开关就在设置里，属于默认值问题而非隐藏行为；他后续还补充该开关存在 web profile 的 cordis.patch.yaml 里，认为升级不会覆盖。
- u/cab938（赞数 4·归档快照）："these are configurable, so it's not as big a risk as made out to be." 立场说明：代表"风险被夸大"一派——可配置就够用，真不信任端点就别用，同时承认默认值可能选得不好，但反对把商业默认配置当成安全事件。
- u/GuideAxon（赞数 4·归档快照）："Best to fork it and make minor but critical safety checks/changes that prevent these behaviors." 立场说明：给出工程解法而非争论——fork 后打最小安全补丁，用 fork log 记录自己有意改动，再让 Claude 做 upstream 同步时保留这些差异，顺带能补上类似 Playwright/Electron 供应链漏洞。

原帖链接：https://www.reddit.com/r/LLM/comments/1xpptru/

---

## 2. "不好意思问"：想绕开 Anthropic/OpenAI，中国模型到底怎么按套餐用

**摘要：** 一位全职软件工程师提问：最近因 REA 一类封禁，社区大量讨论转向开源权重与中国模型，但除了 kimi.ai，几乎找不到按 flat rate 订阅、能随便试不同模型的平台；他不想按 API 计费，怕某个任务突然烧穿预算，所以想知道有没有"包月随便试"的选择。评论区给出一份相当实用的清单：Z.ai 订阅可拿 GLM 5.3/flash，DeepSeek 只有 API credits 但便宜到 $15 能换数亿甚至数十亿 token，Mistral 同时代理 GLM 与 DeepSeek，OpenCode 自托管 DeepSeek 转售更低价（但被质疑"模型变笨"），Neuralwatt、OpenRouter 适合先试后订，还有人自述公司已 80-90% 切到 DeepSeek、把 Claude 留作编排层。为什么值得关注：这是"迁移成本"最真实的一手讨论——价格、订阅形态、数据驻留与模型质量口碑纠缠在一起，而不是单纯比 benchmark。

**高赞评论：**
- u/Sevealin_（赞数 8·归档快照）："Z.ai has a subscription, it gets you GLM 5.3/flash, not super exciting these days though." 并补 DeepSeek "literally $15 can get you hundreds of millions, if not billions of tokens"。立场说明：把"包月"和"极低价按量"两条路线的现实摊开——Z.ai 有订阅但模型已不算惊艳，DeepSeek 没有套餐可单价低到近似免费，等于劝人别执着于订阅形式。
- u/onebit（赞数 3·归档快照）："Personally I'd try out Openrouter and try the models out before you get a plan." 立场说明：务实派建议——先用聚合平台横评再决定签哪家，否则得注册一堆账号；这是对"想包月试遍所有模型"这一诉求最直接的成本控制回答。
- u/FormalAd7367（赞数 2·归档快照）："Our company has switched to 90% Deepseek. Never looked back." 立场说明：企业侧迁移样本——他称公司已 90% 转 DeepSeek、不觉得更笨，并认为 Anthropic/OpenAI 涨价太早；同帖里他与别人就"OpenCode 转售版是否变差"互相贴 eval 和帖子链接对线，说明性价比叙事里仍夹着质量争议。

原帖链接：https://www.reddit.com/r/LLM/comments/1xpp66s/

---

## 3. 一条"帮我们给模型取名"的帖子，长出了家用显卡预训练实录

**摘要：** 有人发帖征集新语言模型的名字，要求短、好念、有辨识度、可国际化，结果评论区大半是玩笑（Chatty McChatface、Slop、Ultron B2）和语言学建议。真正有价值的是楼中一条支线：一位开发者说自己把模型叫 MLM（Micro language model），只有 1000-2000 万参数、并非标准 transformer 结构、在 RTX 5080 笔记本上从零训 2000-5000 万参数的小模型。另一位回帖者给出更硬的数字：在单张 3060 上一天训完 200M 的 MoE（48M 激活）准备开源，同时在同一张卡上预训 10B 的 MoE（400M 激活）、只喂 16B token，还需约 20 天。被质疑 token 太少时，他按 Chinchilla 口径算：10B 模型理想是 200B token，在 3060 上要跑 300 多天，不现实，所以才靠 MoE 稀疏度压缩预算。为什么值得关注：这比常见的"本地推理"讨论少见——它展示的是家用卡做预训练时，真实的 token 预算、架构偷工与时间成本怎么互相妥协。

**高赞评论：**
- u/Own_Reflection_1349（赞数 2·归档快照）："i have named mine MLM (Micro language model)" 并自述 "trianing from scratch small 20-50 million params models"。立场说明：代表"极小模型专业化"路线——不追通用能力，打算训上百个各管一摊的千万级小模型，代价是数据质量不够时基本不可用，他自己也承认 22M 那版只会写很简单的 Python 语法。
- u/Subject-Till-6450（赞数 2·归档快照）："pretrained 200M MoE A48M model on 3060 in 1 day" 且称 10B MoE 按 Chinchilla 要的 token 量在单卡上 "roughly 300+ days on 3060, not realistic"。立场说明：把预训练预算算成具体天数的人——用 MoE 把激活参数压到 400M，才让 10B 在消费级卡上勉强可跑；他的口径也解释了为什么小团队普遍"欠训"。
- u/AnoProgrammer（赞数 1·归档快照）："Isn't 16B tokens very little?" 立场说明：提的正是关键质疑——16B token 对 10B 模型远低于 Chinchilla 最优，等于用严重欠训换可行性；他随后建议直接租 runpod 补算力，把讨论从"能不能训"推到"该不该自己训"。

原帖链接：https://www.reddit.com/r/LLM/comments/1xpaty1/
