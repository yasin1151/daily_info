
r/ClaudeCode 日报 · 2026-11-01

说明：Reddit 全端点仍被网络层封锁，本轮通过 arctic-shift 归档接口取回候选与评论树。八条选题全部是操作型主题：上下文与规则文件、effort 档位与成本、token 燃烧的真实来源、agent 卡在重试循环、多会话流水线的返工数据、无人值守跑 40 个 agent 的运维坑、以及把实现外包给便宜模型。赞数为归档快照（入库时刻的分数），新帖常为 1，因此本轮按评论的信息密度挑帖，不按票数排序。

---

## 1. 全局 CLAUDE.md 到底该写什么：社区给的第一名答案是「让它能自己验证」

**摘要：** 这条帖问的是"全局 CLAUDE.md 里哪些指令真的显著改善过你的 vibe-coding 结果"，52 条评论分出两个阵营。票数最高的答案不是任何一句咒语，而是给 agent 一条能自己跑起来的验证回路：docker、headless browser、开发服务器都行，让它在你看到结果之前先自己发现错误。紧接着的补丁条款更重要——必须同时写上"永远不要为了让测试变绿而修改或跳过测试"，否则一旦有了反馈回路，它会愉快地暴力改断言而不是修 bug。反方意见同样有分量：有人认为 Claude 原生就过度测试，连小改动都跑全量套件，于是在自己的配置里反过来限制。中间层还有第三条路线：把硬性约束从散文挪进 hooks 和 skills，CLAUDE.md 只留目录式的少量事实，因为文件越长越容易被当成背景噪音。对团队的启示是，把"提示词调优"和"工程护栏"分开看，后者才可靠。

**高赞评论：**
- u/Bennetjs（49赞）："give claude a way to test his changes, be it docker, headless browser, etc. etc. have that as part of the development cycle so he can catch his own errors before you ever see them." 立场说明：全帖最高票，也是唯一被反复引用的做法——把验证能力交给 agent，而不是靠口令约束它。
- u/shravanrevanna（15赞）："never edit or skip a test to get green." 以及 "once it has a feedback loop it'll happily brute force the assertion instead of fixing the bug." 立场说明：点出验证回路的阴暗面；没有这条搭配，测试就会从护栏退化成可改写的目标。
- u/TopSetUK（10赞）："Personally I think Claude over tests natively, and runs the full test suite relentlessly for even minor changes, I've gone the opposite way in my Claude.md" 立场说明：提供了反向经验，说明"多测试"并非普适最优，取决于你的测试套件成本与噪声水平。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xk8wys/

---

## 2. 从 Cursor 迁到 Claude Code：规则文件的对应关系和 Bugbot 的替代品

**摘要：** 提问者的 Cursor Pro+ 年费快到期，想搬到 Claude Code，卡在两件事：`.cursor/rules/*.mdc` 那套 glob 规则怎么平移，以及 Bugbot 式的 PR 预审用什么替代。回答相当一致：把一堆规则塞进一个巨大的 CLAUDE.md 是最差解，文件越长越被当成背景噪音；正确姿势是 `.claude/rules/` 下按域拆成小文件，用 `paths:` frontmatter 实现类似 glob 的按需加载，CLAUDE.md 只保留少数全局常驻项。至于"必须不能破"的规则，几位答主都说别指望提示词——PreToolUse hook 直接拦截调用才是一致生效的，因为 prompt 永远只是建议。PR 预审这边，最接近 Bugbot 的是 `/install-github-app` 装上的 Claude GitHub Action，可配置为每次 PR 触发或仅 @claude 时触发，本地还有 `/review` 与 `/security-review`。要放弃的是 Cursor 的行内补全，Claude Code 补不上这一块。

**高赞评论：**
- u/ainexfinder（2赞）："the closest match to .mdc globs is .claude/rules/" 以及 "a PreToolUse hook is the only thing I'd call consistent. It blocks the call outright instead of hoping the model remembers." 立场说明：把 Cursor 的 glob 规则映射到 paths frontmatter，并明确划出"提示词不可靠、hook 才可靠"的边界。
- u/djiyvlom（2赞）："the longer it gets the more the model treats it as background noise" 并补充 "a prompt will always be a suggestion, so a hook that checks or blocks the action is the reliable way"。立场说明：解释了长 CLAUDE.md 失效的机制，并给出可执行的替代方案。
- u/ShipInAnHour（2赞）："/install-github-app sets up the Claude GitHub Action"，建议 "point it at the diff, ask it to report only bugs it can tie to a specific line"，并强调 "the review is a second opinion, not a guarantee"。立场说明：给出了迁移后 CI 评审的具体配置思路，同时提醒别把模型评审当成硬门禁。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xgc8lf/

---

## 3. 有人把 17 个模型的 effort 档位做成性价比表：max 通常不值

**摘要：** 作者横评 17 个模型在不同 reasoning effort 下的得分与单任务成本，结论是"无脑拉满"多数时候是浪费：Opus 5.5 在 xhigh 得 43.38 分、花 5.18 美元，切到 max 得 45.45 分、花 12.82 美元，不到 5% 的提升换来近 2.5 倍成本；17 个模型里只有 7 个在 max 时表现最好，部分模型在 max 反而掉分。评论区没有停留在转述，而是补了更细的实验：有人在最难的那个 bug 上测出 max 反而更差——改写行数中位数 664 行对 high 的 140 行，三次里只解出一次，而 high 三次全解，输出 token 231K 对 35.1K。也有人质疑榜单的惩罚机制会让高 effort 看起来更差。共识落在一个可操作的判据上：只有当任务有明确的 pass/fail 检验、且低档已经失败时，升档才有可验证的收益。

**高赞评论：**
- u/jatingargiitk（4赞）："i see the Opus cost gap as a case for selective escalation, not max on every task." 立场说明：把结论从"别用 max"修正为"按检验结果选择性升档"，是这条帖最实用的转发口径。
- u/malrobot（2赞）："Opus 5.5 at max rewrote a median of 664 lines against 140 at high, and solved it 1 of 3 times against 3 of 3" 立场说明：提供了独立复现的反例数据，说明高 effort 可能把简单修复做成大重构。
- u/Risko4（1赞）："There's a penalty system that makes it look like max is performing worse, when it's not." 立场说明：代表反方质疑榜单口径，提醒读者不要把排行榜当成定论，需自己小样本验证。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xiu1b8/

---

## 4. 新手问怎么省 token，回答集中在"上下文才是账单"

**摘要：** 一位刚上手 vibe-coding 的用户问如何避免 token 烧得太快，24 条回答几乎都指向同一个方向：消耗发生在每一轮都要重发的上下文，而不是你敲进去的那句话。具体做法包括先用 `/context` 看清到底是什么在占空间（未使用的 MCP server 会把自己的工具清单挂到每个请求上）、按任务开新会话而不是一直续聊、给子代理显式指定便宜模型、把 CLAUDE.md 压短、需要读大文件时给行号范围并禁止整体重读。最有价值的一条是关于缓存时序的：缓存在你离开后变冷，回来再敲 `/compact` 等于先按全价把整段对话重读一遍再去压缩；正确顺序是趁缓存还热先让它写一份 HANDOFF.md，再 /clear，下一个会话从这个文件接着干。这条把"省 token"从玄学变成了有先后顺序的操作。

**高赞评论：**
- u/ToolPaths（5赞）："keep the cache hot (usually one hour slot's)" 立场说明：一句话点出成本模型的核心变量是缓存温度，而非纯粹的会话长度。
- u/SirRobinBlibs（1赞）："you pay full price to re-read everything once just to shrink it" 并建议 "before you step away, have it write a short HANDOFF.md (what's done, decisions, what's next) while the cache is still warm"。立场说明：把 compact/clear/handoff 三者的执行顺序讲清楚了，是帖中最可直接照做的一条。
- u/tariqosmani（2赞）："MCP servers you don't use in that project are the easy win, because each one adds its tool list to every request." 立场说明：指出很多人的隐性浪费来自闲置 MCP，属于五分钟内可验证、可回收的收益。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xk281o/

---

## 5. 同一条命令跑十次，问题通常不在模型：交互式命令与重试守卫

**摘要：** 作者反驳"卡在循环就换模型"的常见结论：他在另一个版看到同一循环在三个厂商的模型上都出现，且多数是新会话，说明变量是 agent 正在跑的命令。他拿十条日常命令做了对照实验，在无人输入的伪终端里十条有九条挂住——`git log` 进了分页器、`less`、不带 `-m` 的 `git commit` 打开了编辑器、`python3 -c 'input()'`、`npm init`、需要登录的 `git clone`、`vi`、开发服务器、`tail -f`；换成管道后多数快速失败，但报错形如 EOFError 或 editor 报错，看起来正好是"可以再试一次"的理由。修法分三层：在 settings.json 的 env 里设 `GIT_PAGER=cat`、`PAGER=cat`、`GIT_TERMINAL_PROMPT=0`、`GIT_EDITOR=true`；在 CLAUDE.md 写明同一命令同样失败两次就停下；再加一个 PreToolUse hook 对"命令+结果"做指纹，第四次直接拒绝。

**高赞评论：**
- u/anderson_the_one（1赞）："A command that opens a pager or editor needs a non-interactive rewrite immediately. Letting it burn four retries first is expensive." 立场说明：指出"等输入"和"同样失败"是两类问题，前者应立即改写为非交互版本，而不是先烧掉四次重试。
- u/AdEvening3382（1赞）："commands whose identical output is legitimate"，并以轮询 git status 为例说明 "gives you the same command with the same result, no loop involved." 立场说明：提示指纹法的假阳性风险，这类守卫必须给只读轮询留白名单。
- u/Individual-Shower973（1赞）：建议 "split the command into words the way the shell would before comparing"，否则写法变体就能绕过计数。立场说明：补上了实现层面最容易漏的一环，让守卫从"看起来能用"变成"真的拦得住"。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xik4fk/

---

## 6. 十周 1349 个 story 的返工数据：CI 制造返工，验收标准才是花钱的地方

**摘要：** 作者把自家 agent 流水线的返工位置做了统计：每个 story 拆给多个独立会话——一个写技术设计、一个实现并开 PR、CI 读结果、另一个会话比对 diff 与验收标准、合并到 staging 后还有人点一遍页面；写代码的会话永远无权标记完成。十周约 2.1 万个会话、1349 个 story，4400 次重复实现里，上一次触发点是 CI 占 55%、diff 对验收标准占 25%、staging 浏览器检查 8%、技术设计 6%。有意思的细节：同一个 story 连续两次红且都点名了测试时，85% 的情况点的是不同的测试，说明失败是成簇出现的，"修一个冒一个"。另外约每十次 CI 检查就有一次不是测试红了，而是别的 story 先合入造成冲突——即便规划器已避免同时放出改同一批文件的 story，十五个并行仍会撞。成本最高的 10% story，验收检查两次以上打回的比例是 58%，其余只有 12%。

**高赞评论：**
- u/atp_studio_coll（2赞）："Writing the previously failed test names onto the card, and making the next pass run those plus the new one before it pushes, should turn a lot of those second trips into zero trips" 立场说明：直接针对 85% 这个数字给出低成本改法，把成簇失败压进一次通过。
- u/AdEvening3382（1赞）："If the second red run usually names a different test, the failures from one edit travel in clusters." 立场说明：解释了机制，并主张一次把全部失败测试名与首个错误交回，而不是只给第一条。
- u/shetritr（1赞）："58 vs 12 is the case for writing the criteria before the code." 立场说明：把成本数据翻译成流程结论——验收标准必须在写代码前定，否则"完成"是事后商量的结果。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xirdgs/

---

## 7. 无人值守跑 40 个 agent 一个月：踩到的坑比模型能力更关键

**摘要：** 一支小团队用 `claude -p` 让约 40 个 agent 在自己仓库里跑了一个月，业务涵盖销售跟进、发票、门店巡检、社媒发布和 App 发布。作者列出的意外基本都与模型无关：后台子代理会在主回合结束十分钟后被停掉（受 `CLAUDE_CODE_PRINT_BG_WAIT_CEILING_MS` 控制），卡片写着 Stopped 而运行结果报 succeeded；`claude auth status --json` 在 OAuth 登录实际过期后仍返回 loggedIn: true，只能从运行错误里判断掉线；复用一条长对话每次要重缓 30 万到 65 万 token，改为文件驱动后重新开会话；MEMORY.md 一天内从 8k 涨到 20k 字符，只好让 agent 夜间"做梦"在体积预算内重写，并保留可撤销 diff；一个没人点的 macOS 权限弹窗把运行冻了六小时；聊天字节里 87% 是 base64 截图，单条消息 84MB；还有 agent 从 shell 找到另一个 Chrome 的调试端口，驱动了错误的浏览器配置，最后靠 PreToolUse 拦住。

**高赞评论：**
- u/rickoneeleven（1赞）："now a cron reads api/oauth/usage every 15 mins"，并且 "a run waits for the reset if there's under 30% left"。立场说明：把额度管理前置成调度条件，避免早间任务吃掉窗口、后续运行被误判为故障。
- u/kenthesaint（1赞）："A run started from launchd or a background service can hit a prompt that no one will ever see." 立场说明：指出该类冻结的根因是权限授予绑定了启动进程，应给真正启动 claude 的程序预先授予完全磁盘访问。
- u/GuidingPrinciples（1赞）："At 7:45 a new session starts whose only job is to go over what the night produced." 立场说明：用固定的晨间复核会话替代读日志，是这套无人值守体系里最便宜的人工兜底。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xipsk0/

---

## 8. cheapAg：Opus 只做规划，让半分钱的模型去打字

**摘要：** 作者长期用 Opus 做规划和判断，但发现额度大半消耗在"打字"上——读文件、写样板、重跑测试。于是他做了一个 MCP server 加 Claude Code 插件：Opus 只写一份短任务，DeepSeek V4.1 Flash 通过 OpenRouter 在 git worktree 里写实现，单任务约半分钱；每次必须先写一个"修之前失败、修之后通过"的测试，由工具自己执行，只有通过的工作才以未提交状态落地，方便照常 review diff；便宜模型卡住时换成 Sonnet 兜底。按 SWE-bench Verified 与纯 Opus 对比：加功能从 154k 降到 57k Opus token（省 63%），七个日常 bug 修复省 59% 且都是 7/7，九个最难 bug 省 55% 但只解出 6/9，而纯 Opus 是 7/9。前提条件说得很坦白：仓库必须有测试命令，小任务没收益，难度高的任务会退化。

**高赞评论：**
- u/CYG4N（10赞）："so instead of using it in subscription limit, you pay in deepseek tokens...?" 立场说明：一句话问到了本质——这不是省 token，而是把成本从订阅额度转移到按量计费的便宜模型上。
- u/FlanComprehensive164（10赞）："I've been trying for my agents to use haiku more for simple tasks and it has been difficult to get the handoff moment right" 立场说明：指出现实里最难的不是省钱而是交接点判定，也是这个方案能否复用的真正门槛。
- u/ClemensLode（3赞）："I also delegated implementation to a smaller agent (Sonnet 5.5 in my case)." 立场说明：给出更保守的对照做法，并建议用同一批 ticket 做 A/B 再下结论，而不是只看单次基准数字。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xjqoi0/
