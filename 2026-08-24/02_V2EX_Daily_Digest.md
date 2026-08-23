
All state files synced (max tid 1236649, all 59 new posts marked read). I have everything needed. Composing the final push now.

---

# V2EX 精选推送 · 2026-08-24

**1. Codex 宣布全量重置额度，官方承认三处烧量 bug**
🔗 https://www.v2ex.com/t/1236559

Codex 团队官宣：发现长会话多压缩场景下图片处理效率低、Computer History 高 p95 消耗、标题生成功能额外烧额度三个问题，已组队修复，并宣布**对所有付费订阅做一次额度全量重置**。重置时间推算为北京时间 8 月 24 日凌晨 5 点，帖子评论区连夜"蹬额度"，讨论热度极高。

- 1楼 @Eosdivus："'Reset will land around 14pm PST tomorrow.'我没算错的话，重置时间是北京时间 25 号凌晨 5 点？"——被楼下纠正后自己重算承认是 24 号，时间换算现场。
- 9楼 @2313670923zzy：完整推算"美国西海岸比北京慢 15 小时，当地 8 月 23 日 14:00 PDT 换成北京时间就是 8 月 24 日 05:00"——社区替官方把时区账算明白了。
- 17楼 @femsdfq："还是发卡吧，天天重置一惊一乍的"——吐槽重置常态化，与 29楼 @antidoom"刚用重置卡，这是坑爹啊"呼应，重置卡用户直接亏掉一次。

**2. Vibe coding 用 TUI 还是 GUI？31 楼大战各有立场**
🔗 https://www.v2ex.com/t/1236538

程序员圈经典争议：氛围编程的终端形态选择。TUI 派认为轻量、可 tmux 并行、不打断 vim；GUI 派强调可视化预览和内置浏览器；中间派点名 Zed、herdr 等混合方案，还牵扯出"GUI 提示词更重导致同模型智商下降"的玄学猜测。

- 5楼 @lozzow："TUI 一样可以啊，tmux herdr anytty 这些都可以在 TUI 中开启多个窗口，多个任务并行啊"——反驳"TUI 只能单任务"的刻板印象。
- 21楼 @MindMindMax："GUI 方便我手工处理小问题（节省 token）"——从 token 成本角度站 GUI，角度务实。
- 27楼 @undefined："app，Codex app 电脑控制能力很强，CLI 不方便拿来反复校对 UI 问题"——按任务类型选形态，而非立场先行。

**3. "Ox Alpha Free"神秘模型现身 opencode：疑似 GLM 系多模态**
🔗 https://www.v2ex.com/t/1236624（相关帖：https://www.v2ex.com/t/1236628）

opencode 上出现限时免费模型 Ox Alpha Free，中文圈昵称"牛来"，引发身份猜测：用户通过敏感信息测试认定是中国模型，多数人推断属 GLM 家族。已有用户拿来 review 代码并发现 Opus 4.6 漏掉的 bug，opencode 用量榜上已排第三（11T tokens），话题热度持续发酵。

- 11楼 @zsxzy："昨天拿来 review 代码，发现了一些 opus 4.6 没发现的 bug。今天在 opencode 居然用不了了"——实测体验+限时下架，含金量高。
- 7楼 @boringfish："发现已经是 opencode 上用量排名第三的模型了，跑了 11T"——用量数据佐证社区热度。
- 4楼（相关帖）@jh623："我感觉不比 Deepseek V4 Flash 差呢，就是比较慢，不过总比 Deepseek 最近一直死循环要好"——顺手diss了一波 DeepSeek 稳定性。

**4. 实测确认：Grok Build 周额度悄悄缩水约 48%**
🔗 https://www.v2ex.com/t/1236614

用户用 SuperGrok 正价订阅做同条件对照实验：相同模型、CLI 版本、缓存比例、并发设置，本周实测新增 token 只有上周的 51.998%，推定 Grok Build 周池被减半。这是 V2EX 用户少见的"用数据锤厂商"操作，对 API 重度用户是重要信号。

- 1楼 @Tiande：贴出自己 grok-4.6 中转用量明细（1,318 次调用、输入 166M tokens、合计 $104.21），问"这样算不算缩水"——真实成本账。
- 2楼 @dongzhimin："grok4.6 发布第一周有双倍用量"——给出缩水的可能解释：首周双倍促销到期。

**5. Codex pro20x 额度不够修一个系统：100 个 subagent 同开烧穿**
🔗 https://www.v2ex.com/t/1236638

用户开 Ultra+极速模式，接近 100 个 subagent 并发修系统，pro20x 额度"根本不够登"。评论区分成两派：一派质疑并行规模失控，一派认为核心问题是降智而非额度。

- 6楼 @SingeeKing："100 个。。。Sub Agent 不是银弹，这么多很可能变成一个各种冲突 + 浪费 Token 的现场，Codex 默认限制只有 3 个 Sub Agent 还是有一定道理的"——技术理性派，点出并行失控风险。
- 7楼 @night98："核心还是得不降智，降智了你这么玩除了额度在燃烧没啥意义，我感觉 codex 压根没对 ultra 做优化，只看见额度按照两分钟 1% 往下掉"——把矛头指向降智+优化缺失，社区共识感强。
- 4楼 @northluo："是一个女人生一个孩子要 10 个月，但是领导觉得给你 10 个女人，一个月就能生出来一个孩子"——用段子嘲讽"人多力量大"的并行幻觉。

**6. KimiCodeBar Windows 版发布：托盘盯额度，烧完图标变红**
🔗 https://www.v2ex.com/t/1236646

macOS 知名额度监控工具 KimiCodeBar 的 Windows 社区移植版发布：Tauri 2 + Rust + React，安装包不到 5MB，托盘图标按剩余额度变色+系统通知，支持多账号（Kimi/DeepSeek/智谱 GLM 余额一屏看全），还能扫本地 wire.jsonl 做 token 消耗统计。API Key 存 Windows 凭据管理器，凭证不出本机。（新帖暂无评论）

**7. Open Cottage：纯前端的 Agent 平台，无客户端无服务端**
🔗 https://www.v2ex.com/t/1236612

又一个 Agent 平台，但架构很特别：基于浏览器的纯前端实现，不调用 CLI、没有服务端，打开网页+自备 LLM API key 即用。通过浏览器授权读写本地文件夹（数据存工作区 .cottage 目录），可写代码、编辑文件，但不能执行系统命令。隐私和零部署是卖点，也意味着能力上限明显。（新帖暂无评论）

**8. Mac 防"中转站偷毒"：用 Google 开源的 Santa 锁死 Agent 文件访问**
🔗 https://www.v2ex.com/t/1236640

针对 AI Agent 被要求全权限访问的供应链投毒风险，推荐 Google 主导的 macOS 开源软件 Santa：基于 ESF 框架（普通程序拿不到权限，除非关 SIP），做到"只认进程不认权限"——给 Agent 程序 Full Access 也读不到敏感文件，比如导出 GPG 公钥只能走自带命令且需显式输密码。Linux 侧理论上可用 eBPF 实现。（新帖暂无评论，原帖含博客演示图）

---
*说明：本次通过 RSSHub 通道抓取（v2ex.com 直连超时被墙，SOCKS 代理在 cron 下需审批不可用），该通道不提供 ❤️ 点赞数据，故评论仅标注楼层与用户名，未虚标赞数。已处理 59 篇新帖并全部标记已读，下轮不再重复。*
