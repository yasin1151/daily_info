
r/ClaudeCode 舆情日报 · 2026-11-13

数据来自 Reddit 归档快照。Reddit 各接口在本机网络下仍不可达，blogwatcher 扫描报 `dial tcp 31.13.92.37:443: i/o timeout`，因此改用 arctic-shift 归档接口取正文与评论。文中赞数为抓取时的归档快照，可能滞后于实时票数；标 1 的多为入库默认值，不当作高赞。

---

## 1. 44 个 MCP server，30 个七天零调用：工具膨胀开始有了数字

**摘要：** 楼主在自己的会话日志里数了一遍：当前会话连着 44 个 MCP server、暴露 720 个工具，七天 68 个会话里共发生 2,206 次 MCP 调用，只用到 121 个不同工具。44 个 server 里有 30 个一次都没被调用，最大的闲置 server 自己就带 74 个工具。调用极度集中：browser control 一个占 62%，前四名合计 86%。这些闲置项大多不是手动加的，而是随插件和 claude.ai 账号连接器一起进来的，22 个连登录都没做过。他特意声明不声称闲置工具每会话的具体开销，只想问一件事：精简之后首个请求真的变小了吗，还是 tool search 已经把它们挡住了。评论的答案是后者，但指出两个例外，并附了一次裸跑对照的 token 数。值得关注的是，MCP 的膨胀已经从「装得太多」变成「装了却不知道装了什么」，而判断该删谁要靠调用统计，不能靠目录长度。

**高赞评论：**

- u/Dorbank_Justt（赞数 4·归档快照）："With tool search on, which is the default, the first request already hides most of it." 他解释默认只加载工具名和各 server 的说明，完整的工具定义要等 Claude 去搜索；两个例外是 server 配置了 alwaysLoad 或作者把工具标成预先加载，以及关掉 tool search 或工具还少时的 auto 阈值模式。立场说明：正面回答了楼主的疑问——720 个工具主要占 720 个名字加说明，不是 720 份 schema，所以闲置 server 的真实成本取决于是否命中那两个例外。
- u/RealFullMetal（赞数 3·归档快照）："it neither fetches nor connects any of them" 他指出那 15 个账号连接器是 Claude Code 自己去拉的 claude.ai 连接器，可以在项目里写 disableClaudeAiConnectors 关掉，或用 ENABLE_CLAUDEAI_MCP_SERVERS=false 只影响单次会话。立场说明：把「随插件和账号自动进来」这部分噪音的开关讲清楚了，属于能立刻照做的减法。
- u/AdityaR_Sharma（赞数 2·归档快照）："no MCP servers: 43,154 input tokens" 他按楼主的提问做了裸跑对照：Haiku 5.5、CLI 2.1.310、不挂 MCP 时 43,154 输入 token，挂一个 22 工具的 server（server-everything）后 44,908，关掉 tool search 数值不变。立场说明：这是本轮唯一的实测数字，说明单 server 的场景里 tool search 开关没起作用、增量约 1.7k token，但他也承认没测 44 个 server 那种规模。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xtm77g/

---

## 2. Opus 5.5 在 API 上输出量涨了约六成：一份带成本导出的复现

**摘要：** 一位跑生产应用的用户拿出 Console 成本导出：同一个模型 ID、同样的 effort 设置、同样的 prompt，十月十二日之后单次调用明显变啰嗦。他的口径是输出 token 与输入 token 的比值，从 Opus 5.5 前三周的 0.69 升到 1.09，约多六成；输入侧开支基本没动，说明不是仓库变大或上下文变长；周成本从约 86 美元涨到 119 美元，累计多花的输出费用约 120 到 140 美元。他排除了改价、缓存、批处理和拒答重试——两个月只有 9 次。评论区没有停在「又在抱怨变差」，而是给出两条可操作路径：把 thinking 的展示打开，看多出来的到底是思考还是可见答案；以及固定一组 canary prompt 每天定时跑，记录输出 token 与停止原因，作为能递交给支持的证据。值得关注的是，这类「同输入不同输出」的举证方式正在成为社区对付模型静默变化的标准动作。

**高赞评论：**

- u/RealFullMetal（赞数 21·归档快照）："the full thinking tokens are billed as output, the summary itself is free" 他说明 Opus 5.5 默认不返回思考文本，加上 thinking 的 summarized 展示就能看到可读摘要，而且不用额外付费。立场说明：这直接给了楼主一个零成本的诊断入口——先分清多出来的输出是思考还是正文，再谈是不是服务端行为变化。
- u/Puzzled-Stick9170（赞数 6·归档快照）："worth splitting it by whether the visible answers actually got longer." 他的推理是，如果返回的正文长度没变，那多出来的六成全是思考 token，而思考同样按输出计费。立场说明：这是最有价值的口径纠偏，把「模型变啰嗦」拆成两个完全不同的原因，避免拿错证据去投诉。
- u/awesomebirder（赞数 3·归档快照）："pin a small canary set of your real prompts, run it daily at fixed settings" 他还指出输入侧持平基本排除了「代码库变大」这个解释，并建议记录每次调用的输出 token 与 stop reason，因为思考被隐藏时，canary 几乎是唯一拿得到的干净证据。立场说明：把抱怨升级成可长期运行的监测方案，也是对楼主方法论的补强。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xtlc9v/

---

## 3. 审批延迟才是 agent 循环的真瓶颈：哪些提示根本不该给人看

**摘要：** 楼主把一个长会话拆成两个时钟：agent 自己读文件、改代码、跑测试的时钟，和停下来等人点「是」的时钟。他认为前者很少是瓶颈，真正的损耗是停顿，尤其发生在凌晨或午饭时间，一次 2am 的等待比决策本身贵得多。于是他给了分桶方案：只读命令（git status/diff/log、grep、列目录、已经信任的测试命令）根本不该到人面前，靠 settings 里的 allow 规则解决；git 树内的编辑反正能回滚，交给 accept edits；只有删数据、迁移、动生产、给真人发消息这类不可逆动作才值得拦住。评论区把它推得更彻底：有人干脆用跳过权限加独立 Linux VM 消除审批，有人主张审批要绑到具体动作而不是手势，也有人指出通配符规则是隐形陷阱。值得关注的是，这套讨论把「安全感」换成了可验证的边界设计。

**高赞评论：**

- u/Sporaflow（赞数 3·归档快照）："I launch claude with --dangerously-skip-permissions and never approve anything" 他的安全性不放在审批上，而放在运行位置：本机一个 Linux VM，里面只有开发用 git server，生产完全不在这个环境里，web search 也关掉以免被外部内容注入。立场说明：代表「隔离优于看护」这一派，反驳了「必须逐条批准」的默认假设，但前提是边界真的划干净。
- u/ainexfinder（赞数 2·归档快照）："wildcard rules that look read-only but aren't" 他举 npm run *、make *、python 或 node 一行命令和普通 git push 为例，脚本能干任何事，push 到共享分支还可能触发 CI 部署；建议只放行确切命令，并用 PreToolUse hook 拦生产主机名、迁移命令、rm -rf 和带 POST 的 curl。立场说明：这是对「放宽 allow 规则」最必要的反制，指出宽松规则会把不可逆动作伪装成只读。
- u/zzunkie（赞数 2·归档快照）："i go through those in one batch instead of whenever the phone buzzes" 他的做法是让 agent 不要停在被卡的那一步，先把其余能做的做完，写清在等什么、为什么等，最后集中处理一批。立场说明：把优化目标从「更快地批准」改成「更少、更成批的决策」，实测比换审批手势有效。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xtrcb2/

---

## 4. 单 agent 还是多 agent：真正烧钱的是静默继承，不是冷启动

**摘要：** 楼主几个月前的做法是用 Opus 当编排者、按任务分派 Haiku 做文档、Sonnet 写常规代码、Opus 处理难题、Fable 做设计决策，产出很高；最近看到「每个新 agent 都要冷启动、缓存白付」的说法，开始怀疑这套还值不值，于是问现在该选单 agent 加选择性委派，还是继续多 agent。评论没有统一答案，但把成本真正出在哪里说清楚了：冷启动不是最大的坑，最大的坑是子代理静默继承——不显式指定模型时，子代理会跑在主会话的模型上，连 effort 档位一起继承，他把主会话设成 xhigh，结果一个只做评审的子代理也按 xhigh 烧，一晚就把 Fable 额度用光。另一条修正是缓存账：新子代理只付自己的系统提示加交接内容，而主会话每轮拖着十几万历史更贵，所以该停止为小事开代理。值得关注的是，落点不是「单还是多」，而是把模型、effort、交接内容显式写死。

**高赞评论：**

- u/Excellent-Issue-5956（赞数 3·归档快照）："If you don't set the model, a subagent runs on whatever the main session is on, and it picks up the session's effort level too." 他现在让主会话负责分派和评审，执行者固定为 Opus，还要求每个 agent 的模型和 effort 都显式写出来。立场说明：这是本轮最实用的踩坑，说明额度事故的原因往往不是架构选错，而是继承没关掉。
- u/Coindef（赞数 2·归档快照）："A fresh subagent pays for its system prompt plus whatever you hand it." 他把两边账算清了：主会话每轮携带 150k 历史更贵，子代理只付系统提示和交接；结论是只为「要读很多文件」或「真能并行」的任务开代理，最终形态接近一个 agent 加选择性委派。立场说明：给出了判断标准，而不是站队，把冷启动恐惧换算成了每轮上下文的实际成本。
- u/NoTokenDev（赞数 1·归档快照）："that pins the model for that agent no matter what the main session is on" 他补了具体做法：用 /agents 或在 .claude/agents/ 放 markdown，在 frontmatter 里写 model 和 effort，再在 CLAUDE.md 里指定哪类任务用哪个 agent。立场说明：把上面的教训变成了可复制的配置，避免依赖主会话「记得」传参。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xto6y3/

---

## 5. 还在坚持手写 handoff 的人可以停了：压缩本身的争论变了

**摘要：** 老经验是让 Claude 写结构化 handoff，然后开一个干净会话重新注入，而不是手动或自动压缩。楼主问：最新模型是不是已经能自己压得够好，尤其是跨仓库跑长时间任务的时候。得票最高的一条回答很朴素——手动压缩一直没问题，问题在「自动」；第二高票则相反，认为压缩能力已经大幅提升，前提是有一份高保真的持久记录，他自己把自动压缩窗口设到 60 万 token，并在上下文超过 30 万且刚完成一个工作单元时手动压一次。评论区还给了第三种折中：用 PreCompact hook 在 35 万到 38 万之间注入 handoff 指令，实测和单独的 handoff skill 效果相同。也有人提醒，如果已经到了自动压缩，说明你已经说不清 agent 在做什么。值得关注的是，争论焦点已从「要不要压」变成「在什么条件下压、压完靠什么保证不失真」。

**高赞评论：**

- u/Future_Self_9638（赞数 55·归档快照）："I compact all the time, no problem. but not auto" 一句话把两种压缩分开：他自己频繁手动压，但不让系统替他决定时机。立场说明：这是全场最高赞，说明社区的真实分歧不在压缩技术，而在把时机交给谁。
- u/aruisdante（赞数 13·归档快照）："you still need to have some durable high fidelity record of what the agent is trying to do" 他认为压缩能力确实进步巨大，但必须有这份持久记录才能可靠穿过压缩；给出 60 万自动、30 万手动的双阈值，并说两个月前绝不敢这么干。立场说明：把「压缩好还是 handoff 好」改写成一个前置条件问题，有记录就能压，没记录压了必失真。
- u/WuM1ha1nho（赞数 5·归档快照）："I use autocompact with a PreCompact hook with my handoff instruction at 350-380k." 他做过对照，这套和单独写一个 handoff skill 的效果一样。立场说明：给了不想每次开会话的人一条中间路线——保留自动压缩，但用 hook 把自己的交接要求塞进去。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xubp1v/

---

## 6. 远程 Mac mini 上跑 agent：浏览器这层不用远程桌面

**摘要：** 楼主在 M4 Mac mini 上跑多个 agent，用 Tailscale、SSH、tmux 加独立 git worktree，从 M1 MacBook Air 连过去；终端一切顺畅，卡在浏览器：要看页面 UI 或看 Claude 在浏览器里做什么，只能用 macOS 屏幕共享，结果笔记本发烫。评论给出两层解法。自己看界面根本不需要远程桌面，ssh 本地端口转发或绑到 Tailscale 地址即可，有 OAuth 回调和绑 localhost 的 cookie 时优先用隧道，并且给每个 worktree 分独立端口；要看 agent 的浏览器，就让它在 mini 上带远程调试端口启动 Chrome，把端口转出来，在笔记本用 chrome://inspect 附着，得到一个可点击的实时单标签视图。还有人警告别让 agent 用日常浏览器，有账号因此被平台风控。

**高赞评论：**

- u/Elegant_Yam2783（赞数 6·归档快照）："Prefer the tunnel if you have OAuth callbacks or cookies tied to localhost." 他的完整方案是：自己看 UI 用 ssh -L 转发开发端口，或在 mini 上 --host 0.0.0.0 后走 Tailscale 主机名；看 agent 的浏览器就转发 9222，再用 chrome://inspect 加 localhost:9222。立场说明：这是最省资源的正解，把「远程桌面」换成端口转发，顺带解决了 OAuth 回调只能走 localhost 的老问题。
- u/kuroudo_ai（赞数 4·归档快照）："stop treating the browser as something to look at and give the agents a browser they drive through the Chrome DevTools Protocol (CDP)" 他强调必须用独立 profile，因为能连上调试端口就等于控制所有标签和已登录会话，新版 Chrome 也拒绝在默认 profile 上开调试端口。立场说明：把思路从「人看浏览器」转向「agent 自己用浏览器」，同时点明了安全边界。
- u/Excellent-Issue-5956（赞数 2·归档快照）："A frozen tab hangs every eval." 他踩的坑是被脚本驱动的 Chrome 同时被拿去日常浏览，标签被压到后台后冻结；冻结的标签仍能回答同步 eval，计时器和 fetch 却不跑，于是「还活着吗」的检查会误判成登出。立场说明：这类只有真跑过才会遇到的失败模式，比任何最佳实践都值钱，也解释了为什么要给 agent 单独一个浏览器实例。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xqba7g/

---

## 7. 让 Claude 指挥 Codex：正解不是消息总线，而是把状态写进文件

**摘要：** 楼主想让 Claude 当总编排，把任务分给另一个终端里的 Codex，再让两边互相通信；实测 Claude 能把消息发过去，Codex 回不来，于是问交接该怎么做，还问到 herdr 是否是答案。评论区几乎一致地劝他别造消息总线：如果 Codex 只需要说一句「做完了，给我下一个」，两边根本不需要互发消息；更彻底的答案是把结果落成文件——研究的产物写进 results.md，计划写在 plan.md，交接就变成「读 results.md，更新 plan.md」，哪一方执行都一样。还有人用 spec-driven development，把临时 markdown 当作跨终端交接载体，切过去跑对应 skill 就能接着干。值得关注的是，这个问题的最优解不是更强的 agent 间协议，而是把共享状态从上下文搬到仓库里，这也解释了为什么多 agent 讨论最后总会回到文档和任务队列。

**高赞评论：**

- u/NamerekDev（赞数 2·归档快照）："Then the result should land in a file, not in a message." 他进一步说，愿景和目标要放进两个 agent 都读的文档，而不是 Claude 的上下文，因为上下文会被压缩、文档不会；交接简化成读结果、更新计划。立场说明：直接否定了楼主的问题前提，把跨厂商协作还原成文件协议，是最省事也最稳的路线。
- u/PlatinumPlace（赞数 3·归档快照）："The handoff happens by creating temporary .md files in the project" 他用 spec-driven development 加对应 skill，切到第二个终端跑 skill 时会自动知道哪个计划在进行、从哪里接上，做完再回 Claude 评审。立场说明：给出了已经在用的具体工作流，说明跨终端交接不需要任何新协议。
- u/Kitchen_Interview371（赞数 3·归档快照）："ask opus in plan mode to research available options" 他建议先用 plan mode 让 Opus 调研现成编排方案和仓库再实现，别自己从零发明通信机制，同时提醒简单场景直接让 Claude 去做就行。立场说明：介于「什么都自己搭」和「开箱即用」之间，提醒先把已有方案调研清楚再投入。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xumlss/

---

## 8. 一晚丢 38 件事，全都没进任务队列：问题不在压缩

**摘要：** 一位不写代码的独立创始人用 Claude Code 管整个项目，同时开 4 到 10 个会话分角色：协调、合并、基础设施、若干执行者。他说的遗忘不是代码，而是他交代过的事：任务、决定、「顺便把这个也做了」。他还做了量化：一个普通晚上每次切换会话平均丢 2.8 件事，某一晚共丢 38 项，而这 38 项全都只以自由文本存在于聊天里，任务队列里一行都没有。评论区因此把根因重新定位：不是上下文压缩，而是指令在变成持久任务之前就已经消失，再完美的 handoff 也救不回没被记录的东西。给出的解法包括把捕获环节从忙碌的会话里拿走、交给一个只做提取的小模型，以及把硬规则、ADR、runbook 全部落进仓库。值得关注的是，这是把「agent 健忘」从抱怨变成可测量缺陷的一步。

**高赞评论：**

- u/vacterro（赞数 2·归档快照）："instructions can disappear before they ever become durable tasks" 他认为楼主最有价值的发现就是 38 项全部只存在于聊天，并提出 agent 应该能忘掉一切却仍从持久状态里恢复工作。立场说明：把讨论从「压缩会不会丢信息」拉到「录入环节漏了多少」，这是本轮最关键的归因修正。
- u/michaelTM_ai（赞数 2·归档快照）："take capture away from the working session" 他的方案是每条消息同时过一遍只负责列出任务、决定和「顺便也做」的廉价模型，写成带会话标签的队列行，工作会话只读这些行而不再靠记忆。立场说明：可落地的工程解——把捕获和责任从忙碌的上下文里剥离，并给出用重放消息验证捕获率的方法。
- u/dmdubz（赞数 2·归档快照）："Small Claude.md this stays in your context permanently so hard rules about the repo only" 他的分层是：CLAUDE.md 只放仓库硬规则、不写增长的历史，ADR 记录架构决定以免反复重开辩论，再加文档指针和 runbook，全部用朴素 markdown。立场说明：这是对「所有事实必须住在仓库里」的具体排版建议，也解释了为什么巨型指令文件反而会被忽略。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1xtv55v/
