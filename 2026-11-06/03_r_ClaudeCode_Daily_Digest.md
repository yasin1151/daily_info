
今日 r/ClaudeCode 精选 8 条：订阅计费的实测口径、Opus「变笨变贵」的舆论与反证、Explore 子代理默认烧主模型额度、常驻上下文从哪来、compact 与交接的取舍、CLAUDE.md 拆分陷阱、agent 删库的机制复盘、skill 供应链安全。

赞数说明：Reddit 三端点在本机被 IP 层封锁（`http=000`，redlib 同样不可达），正文与评论取自归档快照（arctic-shift，765 个候选去重后取 48 帖探评论，全部成功），赞数为抓取时点，可能滞后；标「赞数 1」的多为入库默认值，不作高赞排序。

---

## 1. 有人把订阅配额拆成了公式：没有近期降级，但计费方式和 API 不一样

**摘要：**
作者用代理长期记录 Claude Code 每次请求返回的 usage 响应头，另开一个全新 Pro 账号做基线，每次只让一种 token 类型增长，用上千次读数把「配额百分比」拟合成可计算的权重公式。结论是配额基本等于 API 定价，但有三处系统性偏差：缓存读按 input 的 0.025 倍计（API 是 0.05 倍，而 Claude Code 流量约 97% 是缓存读，因此缓存读约占总消耗的四成）；1 小时缓存写入与 5 分钟同价（API 对 1 小时收 2 倍）；小模型反而被溢价，Haiku 每个 API 美元只换到 1.76 倍于 Opus 的额度，Sonnet 是 1.36 倍，所以按 API 美元算，Opus 5.5 才是订阅里最便宜能跑的模型。计划规模上 Ultra 的 5 小时窗口约等于 20 倍 Pro，但周额度只有约 10 倍。关于「是不是被 nerf」，他数据里唯一的削减是 9 月 14 日结束的加 50% 周促销（约每个百分点少 14%），9 月 28 日重置后基本持平。值得关注的是复现提醒：只统计百分比读数的新高，否则并发抖动会把「已用」虚增一到三成，足以凭空造出一次降级。

**高赞评论：**
- u/rhgg2cam（赞数 3·归档快照）："They've made Fable more sensible recently, I see, the 1.4x API pricing used to be around 3.5x (back in late July-early September). I reckon that was a really stupid bug." 立场说明：补充时间序列视角，指出 Fable 的溢价从 3.5 倍降到 1.4 倍，说明计费表本身在变，任何单点测量都得标明月份才有可比性。
- u/sukazu（赞数 2·归档快照）："Did you test fast ? Docs says only with usage credits But on sub , it feels like half the time you still git the option to enable it. Is it purely cosmetic ?" 立场说明：提出原帖没有覆盖的变量 fast mode，怀疑订阅端那个开关只是装饰，实际仍走 usage credits，属于待验证的空档。
- u/avogadro-（赞数 1·归档快照）："Do have actual numbers for the input (cached and uncached) and output tokens? ... The USD values still seem a little arbitrary without a proper token split" 立场说明：方法论层面的质疑——只给合并后的额度值、不给分项 token 数，美元换算就仍然带主观性，这条批评对复现者最有约束力。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xki1qr/

---

## 2. 「Opus 5.5 明显变笨也更贵」拿到 920 分，评论区一半在解释、一半在反证

**摘要：**
一位用了多年 Claude 的用户发帖说 Opus 5.5 最近明显退化且更烧 token：会反复回到已经被否掉的方案，一条严格指令下同一件事重复了九次。帖子迅速变成当天最大的讨论，375 条评论分成两派。解释派给出产业逻辑：新模型发布前要把算力腾出来所以静默量化、为 IPO 修饰成本、推理成本其实毛利很高。反证派拿出可重复任务和自动化质检，每天上万条 prompt 的团队表示什么都没感觉到，并认为多数「变笨」帖来自用户自己悄悄改过的项目和指令。真正可操作的一条来自中间立场：被否掉的方案只活在聊天记录里，会话越长它权重越低，所以模型会越走越回去，把「否决过什么、为什么」写成文件让 agent 每轮重读、并更早换会话，比等厂商回滚更有效。值得关注：这类体感帖每天都在涨，但能落到行动的结论是上下文治理和拒绝清单，而不是继续投票「是不是变笨了」。

**高赞评论：**
- u/pineapplecatz（赞数 345·归档快照）："They are probably quantizing the model because, most likely a new model is about to release and they need to provision compute for it. It doesn't justify their behavior, but it's a plausible explanation." 立场说明：全场最高赞的产业解释，把退化归因到新模型前的算力腾挪与静默量化，同时明确说不构成合理化的理由。
- u/MastodonFarm（赞数 62·归档快照）："That is not how it works. They already made their disclosures for the IPO." 立场说明：直接反驳「为 IPO 修饰财报所以砍算力」的流行猜测，指出披露已经完成，这条把讨论从阴谋论拉回公司流程。
- u/Ranjexa（赞数 13·归档快照）："the 'nine times' detail is the useful part. when it keeps circling back to something you already rejected, that's usually the rejection living only in chat history, and the longer the session gets the less weight it carries." 立场说明：把现象归因到会话状态而非模型权重，并建议把被否选项写成文件、更勤开新会话，是整串里最能直接照做的一条。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xodr56/

---

## 3. 内置 Explore 子代理默认跑主模型，改一行 frontmatter 就能把搜索降到 Haiku

**摘要：**
帖子指出 Claude Code 每次搜代码都会拉起内置 Explore 子代理跑 Glob、Grep、Read，而它默认继承主会话模型：在 Opus 或 Sonnet 上，每一次文件搜索的分发都按主模型价格消耗 5 小时额度。给出的两种覆盖方式是写 .claude/agents/Explore.md 并在 frontmatter 标 model: haiku，或启动时用 CLAUDE_CODE_SUBAGENT_MODEL=haiku。作者称自己在多个 TypeScript 与 Python 仓库上跑了三周，纯文件定位的准确度和 Sonnet、Opus 相当且更快，风险是多跳的架构问题偶尔会提前一跳收工。评论区补了两个关键修正：自定义 agent 不写 tools 或 disallowedTools 会继承全部工具，包括 Write 和 Edit，等于把只读的 Explore 变成可写；环境变量在当前版本并不会改变内置 Explore 和 Plan，只会影响其他干实活的子代理。值得关注：在「省额度」类技巧里，这条少见地可被反向检验，也暴露了覆盖内置 agent 时的权限回归风险。

**高赞评论：**
- u/NormalHumanBreathing（赞数 9·归档快照）："The example file has no `tools` line, and a custom agent without one gets every tool, including Write and Edit. ... Adding this to the frontmatter keeps it that way: `disallowedTools: Write, Edit`" 立场说明：最有价值的安全修正——照抄原帖示例会让 Explore 拿到写权限，必须先补 disallowedTools 才能谈省钱。
- u/DailyHarambe（赞数 4·归档快照）："Claude tends to churn by rebuilding search scripts from scratch. Instead, have it build reusable helper functions" 立场说明：提供另一条减少重复搜索的路径，把常用检索固化成仓库内的脚本或符号表，比单纯换小模型更治本。
- u/ClemensLode（赞数 2·归档快照）："Hmm... my benchmark say the opposite. On what do you base that they are 'mechanical', did you run benchmarks or do you just assume 'explore means search means mechanical'?" 立场说明：质疑「搜索就是机械劳动」这个前提，要求给出基准而不是直觉，代表了反方最有分量的一击。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xobgp2/

---

## 4. 没装任何 MCP 却每次开局吃掉 14k-20k：来源是桌面端 connectors

**摘要：**
有人发现自己在完全没有安装 MCP 的情况下，每个会话开场就带 14k 到 20k 的上下文，怀疑存在隐藏的工具开销。评论区把来源定位清楚：用订阅登录时，你在 Claude 网页端或桌面端添加的 connectors 会自动加载进 Claude Code，插件也会带自己的 server。可以先跑 /mcp 看清单，再在 settings.json 里加 "disableClaudeAiConnectors": true，或单次用 ENABLE_CLAUDEAI_MCP_SERVERS=false claude 启动，然后用 /context 复核。剩下的部分主要是内置工具定义、CLAUDE.md、memory 与 skill 描述，这些才是可以裁剪的。还有人提醒一个更重要的成本结构：这笔基线不是只付一次，它每一轮都随请求发出，多数是便宜的缓存读，但每个新会话、每次超过缓存窗口的停顿（几分钟量级）都要按全价重写一遍，所以频繁开关会话比基线数值本身更贵。值得关注：这是额度消耗里最容易被忽略的结构性开销，而且完全可自查。

**高赞评论：**
- u/Additional_Video2992（赞数 1·归档快照）："the connectors you added in the Claude web or desktop app load in Claude Code too. Run `/mcp` and you'll see them listed." 立场说明：给出根因和两条可验证的关闭方式，是从猜测走向定位的关键回复。
- u/awesomebirder（赞数 1·归档快照）："that 14-20k isnt paid once. its sent with every turn, mostly as cheap cache reads, but every new session and every pause longer than the cache window (a few minutes) writes it again at full price" 立场说明：把常驻上下文换算成「会话碎片化成本」，提醒真正的省钱点是别让缓存反复冷掉，而不是只砍基线。
- u/Coindef（赞数 1·归档快照）："Run `/context` in a fresh session and it breaks usage down by category" 立场说明：提供最直接的自查路径，并点出 ~/.claude/CLAUDE.md 会被所有项目加载、最常被忘掉。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xokwck/

---

## 5. 别卡着 300k 自动 compact：先写交接文件再开新会话更便宜

**摘要：**
提问者想知道能否让 Claude 在到达 300k token 时自动压缩上下文，并把会话交接给新的一个继续。回帖几乎一致反对「盯着数字自动 compact」：更稳的做法是在压缩前让模型写一份交接文件，内容是在做什么、已定的决策、动过哪些文件、下一步、未解的 bug，还有试过并放弃的死路，然后 /clear 或开新会话，用「读 handoff.md 继续」起步；也可以做成 slash command，在 70% 上下文时触发。技术上确实存在 CLAUDE_AUTOCOMPACT_PCT_OVERRIDE 这类阈值开关，但共识是压缩只重写前缀、不保留意图，压缩本身也是一次很大的请求，长会话继续跑往往比一次冷启动更贵。还有一条被反复强调的细节：死路必须写下来，否则新会话会把同样的「显然方案」再试一遍，白烧二十分钟。值得关注：这是把上下文焦虑转成可执行流程的一条，直接对应 token 账单和返工率。

**高赞评论：**
- u/beatwallstreet2021（赞数 3·归档快照）："Don't compact, have Claude do a handover document and create you a slash command that directs the next session to that document at 70% context" 立场说明：给出最简可落地的方案——交接文档加 slash command，在七成上下文时主动切换而不是等自动压缩。
- u/AdityaR_Sharma（赞数 1·归档快照）："CLAUDE_AUTOCOMPACT_PCT_OVERRIDE in env. What matters more is what you tell it to keep: task list, file paths touched, commands and exit codes, decisions and why." 立场说明：确认阈值开关存在，但把重点移到压缩保留哪些字段，属于对原帖的技术校正。
- u/SirRobinBlibs（赞数 1·归档快照）："Compaction rewrites the prefix, so the next turns often cost more than a clean handoff. ... skip the compact and pay for one cold start instead of two." 立场说明：成本视角的反直觉结论——既然已经决定交接，就不要再压缩，避免一次冷启动被拆成两次付费。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xobdmd/

---

## 6. 把 CLAUDE.md 拆成多个文件后发现：@import 一点也没省

**摘要：**
团队把庞大的 CLAUDE.md 拆成多个文件后实测发现 @import 根本不省 token：被 import 的文件会和主文件一起、每条消息都发出去，在 /context 里它们同属 memory files。真正有效的是「指针行」——每个文件一行，写清里面有什么、什么时候该打开，而且要写任务场景而不是只写路径，「改 auth 之前读 docs/auth.md」比「见 docs/auth.md」有效得多。还要维护一张「搬走了什么」的清单，否则没有任何地方指向的文件永远不会被读到。评论区补上了更细的层次：后代目录里的 CLAUDE.md 或按路径生效的 rules 才会真正按目录懒加载；也有人反驳说不该期待 @import 懒加载，它的设计目标只是模块化，渐进披露本来就是 skills 的职责；更尖锐的一条指出 .claude/rules 里写 @import 仍会被急切加载，等于把 rules 的懒加载彻底破坏。值得关注：CLAUDE.md 是常驻上下文的一部分，拆分方式直接决定每一轮的成本和指令命中率。

**高赞评论：**
- u/zirouk（赞数 2·归档快照）："You mistakenly expected @import to be lazily loaded. 99% of software engineers would not expect that behaviour." 立场说明：反驳原帖的问题设定，认为 @import 的设计目标是模块化而非渐进披露，把「没省」说成预期而非缺陷。
- u/HighwayNo8744（赞数 1·归档快照）："it also loads the `@import` eagerly if specified in .claude/rules files, breaking the lazy loading of rules file entirely ... the feature is broken" 立场说明：把批评推深一层——rules 文件的懒加载会被 @import 破坏，这是实际缺陷而不是使用姿势问题。
- u/ComprehensiveShake76（赞数 1·归档快照）："After moving something out, start a fresh session and give it a task that should need that file, then watch whether it opens it before editing." 立场说明：给出可验证的验收方法，并主张指针写路径比写主题更可靠，属于能直接照做的质检步骤。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xobl2u/

---

## 7. 一次空变量引发的删库：agent 把仓库根目录连 .git 一起删了

**摘要：**
作者复盘一次 auto 模式下的事故：测试脚本用 && 串起来跑，前一步失败导致临时目录变量 T 为空，而清理命令挂在分号后面照样执行，于是 find $T -type f -delete 退化成 find -type f -delete，GNU find 默认作用于当前目录，把仓库根目录连同 .git、SSH key、凭据和 gitignore 掉的文件全部删光；约四十分钟后，另一步「先写失败测试」又差点在线上服务器的 home 目录执行 rm -rf，被及时杀掉。恢复靠前一晚的 restic 备份，四秒完成。评论区追问为什么 agent 会有这种权限、为什么没有远端：作者承认本地 main 落后远端三十个提交、feature 分支从未 push，所以「有 GitHub」也救不了这次。也有人给出真正的教训，要审的是变量填进去之后命令变成什么，而不是它敲出来时的样子。值得关注：agent 自主性提高后，破坏半径由 shell 语义而不是模型意图决定，备份和权限边界必须在事故之前就位。

**高赞评论：**
- u/DevOnTheStreets（赞数 15·归档快照）："Why can it even do this to start with? You don't work out of branches? You don't protect main with human PRs only?" 立场说明：最高赞的权限质疑，指出破坏前提是 agent 拿到了本不该有的写与删的权限，备份只是兜底不是防线。
- u/Ok-Lobster-919（赞数 6·归档快照）："I think he doesn't have a remote origin at all. So when he deleted his local .git repo he deleted all the history including the branches." 立场说明：点出最低成本的保险被忽略——一个免费私有远端就能保住全部历史，成本几乎为零。
- u/riyazhyder（赞数 1·归档快照）："Sometimes an empty name in a cleanup command quietly means 'everything here.' ... The deeper lesson is approving what a command becomes after the blanks fill in, not just how it looks typed out." 立场说明：把事故抽象成可复用的审阅原则，看变量展开后的实际命令而不是模板，对写 hook 和审批流的人最有用。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xnt15t/

---

## 8. 「skill 只是文本」已经不成立：脚本、二进制和运行时拉取的 URL

**摘要：**
帖子质疑那句流行回答「skill 只是 markdown，读一遍 SKILL.md 就行」：现在很多 skill 自带 scripts 目录并在 shell 里执行，插件从 2.1.91 起可以带二进制，还有 skill 在运行时才从 URL 拉取指令，于是你读到的和下周实际跑的不是同一份东西。回帖的做法大致三档：最保守的是根本不装别人的 skill，只把需要的文件抄进自己仓库、读一次之后不再自动更新；中间派先 fork，再让 Claude 审一遍，删掉外部上报、多余依赖、别人的 marketplace 名称等不想要的部分，改造成自己的版本再从自有 marketplace 分发；工程派则主张把带脚本的 skill 当依赖对待，钉住 commit、复制进仓库、每次升级像审依赖包一样 diff。共识是「运行时从 URL 取指令」等于一个无法审阅的 prompt，直接拒绝。值得关注：skill 与插件生态正在变成新的供应链攻击面，装之前该看的是权限与外部调用，而不是文案质量。

**高赞评论：**
- u/muikrad（赞数 5·归档快照）："I always fork the source repo, then ask Claude to audit it. Then I ask Claude to modify anything that isn't self-contained, for instance pinging external usage monitoring servers or dependencies, marketplace names, etc." 立场说明：给出完整可操作的 fork、审计、去外部依赖流程，是这三档里最容易照抄的一档。
- u/alanvnk（赞数 4·归档快照）："Don't install third party skills unless they are form a tool provider (figm, Jira or the like). Just make your own using the ideas you like from the other skills" 立场说明：以来源可信度划线，只信工具厂商官方产物，其余照着思路自己重写，属于风险最低的策略。
- u/f3xjc（赞数 4·归档快照）："Skill is just text but text can be bundled with a script (and Imo should) then you read the script too." 立场说明：直接修正「只是文本」这个前提，文本和随附脚本必须一起读，否则审阅是假的。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xn0w8d/
