
Reddit 所有端点与 redlib 实例今天仍然全部不可达，因此我改用归档（arctic-shift）与 feed2json 两个通道把 r/LLM 逐帖核了一遍，结果如下。

---

# r/LLM 速览 · 2026-11-16

说明：Reddit 的三个端点和 redlib 实例在本机仍然全部不可达（`000`），本期继续通过归档接口和 RSS 两个通道取数。今天新增的、发布 0-10 小时的帖子全部 0 评论（包括 Ling-3.2-flash 的 1M 上下文说明、Temperature 0 不确定、Arborformer 决策树模型等），社区今天基本没有讨论。以下三条是归档里尚未推送、讨论质量最高的技术帖，发帖时间为 10 月上旬，标为补读。每帖总共只有 2 条真实回复，按实际数量呈现，不补写第三条凑格式。赞数为归档快照（多为 1-2 分），不代表真实热度。

---

## 1. 188 个真实并发 bug 的基准：单价便宜三倍的模型，每修一个 bug 反而贵四倍

**摘要：** 有人从真实开源 Python 项目里收集了 188 个并发 bug（竞态、死锁、取消处理），搭了一个端到端基准：模型只能看到修复前的仓库、没有网络，最后用项目自带测试判定补丁是否真的修好。成绩是 GLM-5.3 Flash 81.9%、GPT-5.6 Luna 81.3%、DeepSeek V4 Flash 72.1%，前两名在误差范围内打平；简单的一半任务三家都接近满分，最难的 55 个任务掉到 50%、45%、23%。真正值得看的是成本计算方式：按“修好一个 bug”计算，Luna 与 GLM 约 2 美分，DeepSeek 约 8 美分——单价低不等于总花费便宜，因为它每次尝试要跑约 54 次工具调用，而 Luna 只要 15 次。一半题目保留为私有集，用来排查训练数据泄漏。对做 coding agent 的人来说，这比总跑分更有用：同样的任务，步数差异会直接放大 token 账单。

**真实评论（按归档快照赞数标注）：**

- u/Frosty-Source8816（2赞·归档快照）："fascinating that the" … "model ends up costing more per fix because it needs more attempts" 以及 "50% vs 23% is a canyon, not a margin of error thing" 立场说明：一眼抓住单价与总账的差别，并指出最难档的差距不是统计噪声，说明社区看跑分表时已经从总分转向分档表现和步数成本。
- u/heyitsdannyle（1赞·归档快照，楼主）："every model gets the same number of attempts per task. DeepSeek costs more because each attempt takes more steps, about 54 tool calls against 15 for Luna" … "The 95% intervals on the hard set don't overlap" 立场说明：作者亲自纠正误解并给出区间（GLM 39–61%、Luna 35–55%、DeepSeek 15–32%），承认全量上打平、难档上确实落后，属于少见的老实口径。

原帖：https://www.reddit.com/r/LLM/comments/1x03urv/

---

## 2. 61 天 Claude Code 转录实测：三个成功信号同时显示，只有 11% 的内容真的进了上下文

**摘要：** 一位独立开发者把 61 天、190 个主会话、918 个子代理文件的 Claude Code 转录全量测了一遍，想弄清到底什么内容真正到达了模型的上下文窗口。他把注入分成三层：常驻（hook 载入的项目地图、记忆索引）、按需翻页（子目录 CLAUDE.md、文档）、事件触发（命令或文件命中才注入），全部用原生 hook、settings、skills、subagents 实现，不装 MCP。三个反直觉结果：190 个会话里 0 次自动召回，记忆只有被 agent 主动打开文件时才进窗口；压缩极其激进，某次单个事件删掉 96.6% 的上下文（607,378 降到 20,766 token），36 条历史消息里有 8 条在摘要中没留痕迹；最值得注意的是 8 月 13 日，载入项目地图的 hook 输出 18,057 字节，只有约 11% 到达模型——因为超过 1 万单位的 hook 输出会被转存成文件，模型只看到约 2KB 预览。而 hook 运行时报成功、脚本日志报完成、自测 9/9 通过，三个信号都是真的，却没有一个在检查「送达」。唯一能抓到问题的手段，是把脚本输出与转录逐字节比对。

**真实评论（按归档快照赞数标注）：**

- u/boilingabundance（2赞·归档快照）："three different success signals and none of them actually mean the model got the whole thing" 立场说明：把问题抽象成可观测性上的假阳性——指标全绿但语义丢失，认为逐字节比对该成为默认动作，只是没人想到。
- u/JhouHate（2赞·归档快照，楼主）："all three were telling the truth … None of them was checking whether the text reached the model" 立场说明：补充关键细节，三个信号都没撒谎，缺的是送达校验，并给出低成本的复现方法：转录里记了 hook 回传内容，直接和脚本打印比对即可。

原帖：https://www.reddit.com/r/LLM/comments/1wu26si/

---

## 3. 换模型前到底该测什么：除了裁判打分，还要测「下游会不会崩」

**摘要：** 换模型是生产环境里最容易翻车、又最少被认真验证的动作：提示词一个字没改，输出却变了。发帖人问社区怎么做迁移验证，两个回答拼出一套可落地的做法。其一是同一批提示词跑新旧两个模型，用 LLM-as-judge（通常拿 GPT-4 当裁判）按准确性、语气、完整性打分，样本至少几百条，并且不能只看平均分，要专门翻最差的那批，看新模型有没有系统性盲区；同时记录每个请求的 token 与延迟，把成本和质量一起加权——如果场景能容忍，稍微笨一点但便宜很多的模型可能才是对的选择。其二是如果输出要进代码，光有裁判分数不够，必须加 parser/schema 校验和工具调用检查：一段读起来很顺、却让下游代码崩掉的回答，照样算迁移回归。可接受差异取决于场景，面向客户的语气漂移要零容忍，内部数据抽取只关心事实是否对得上。

**真实评论（按归档快照赞数标注）：**

- u/submissivebounds（1赞·归档快照）："you want at least a couple hundred examples, and don't just look at averages, dig into the worst performers" 立场说明：给出样本量下限和关注尾部的方法论，并强调成本要与分数一起加权，容忍度按场景取值。
- u/Ctbhatia（1赞·归档快照）："a fluent answer that breaks your downstream code is still a migration regression" 立场说明：把判定标准从「读起来对不对」拉回到「下游能不能跑」，指出裁判分数只是第一层，schema 与工具调用才是硬门槛。

原帖：https://www.reddit.com/r/LLM/comments/1x0h2tw/

---

补充：为了判断是不是漏抓，我另外用 feed2json 拉了 `/hot`、`/new`、`/top?t=week` 三个榜单，发现 `1xpp66s`（49 评论）、`1xrkt4l`（22）、`1xtnuex`（20）、`1xuh32n`（6）确实有较多评论，但这四帖分别已在 11-08 到 11-14 的推送里出现过（`grep -rl comments/<id> cron/output` 可查证），属去重过滤而非漏抓。今天 0-10 小时的新帖全部 0 评论，因此没有「今日新增且有人讨论」的帖子可推。
