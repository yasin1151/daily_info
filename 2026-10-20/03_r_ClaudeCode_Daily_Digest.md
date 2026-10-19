
r/ClaudeCode 日报 · 2026-10-20

Reddit 三个端点（www、old.reddit、redlib）本轮全部返回 000，Reddit RSS 扫描同样超时，本期内容通过 arctic-shift 归档通道读取。赞数为归档快照，可能滞后；标 1 的多是入库默认值，不代表高赞。选帖按操作性主题优先：hook 与权限、上下文与记忆、token 计量口径、模型分工、测试流程、常驻 agent。

---

## 1. 你的 git push 拦截规则拦不住 git -C . push：四类 hook 静默失效

**摘要：** 作者花一周时间读公开仓库里的 Claude Code hook，把坏掉的逐个报给维护者，发现同一批错误反复出现在保护 migration、编译产物和 .env 的 guard 上，而且这些 guard 全都不报错，只是从来没拦住过任何东西。四类典型错法：一是 deny 规则匹配命令文本而不是程序本身，Bash(git push *) 挡不住 git -C . push、git 'push' 和 bash -c 'rm -rf build/'；二是 hook 读了 Claude Code 根本不设置的变量（如 CLAUDE_TOOL_INPUT），真实输入是 stdin 上的 JSON，要用 jq 取 .tool_input.command；三是 hook 用 exit 1 退出，而默认只有 exit 2 才算阻断，exit 1 被当成非阻断错误、命令照跑；四是 hook 自己崩了默认放行，有个本该挡 .env 与 AWS 凭据读取的脚本每次解析失败都 exit 1，于是每次读取都放行。为什么值得关注：把安全边界交给字符串匹配的团队几乎都在这个坑里，而失败是完全静默的——没有报错、没有日志，只有「以为拦住了」。

**高赞评论：**
- u/ComprehensiveShake76（赞数：1·归档快照）："This is exactly why string matching on the command line is a weak gate." 他把 deny 规则定位成减速带而不是边界，真正的墙是让 agent 所在环境根本没有推送凭据、看到的也不是有 origin 写权限的那棵树；立场说明：这比继续补正则彻底，因为它假设「聪明的 argv 一定会绕过 hook」，从而把安全落到凭据层。
- u/billshredding（赞数：1·归档快照）："The command can be a file the agent wrote a minute ago." 他补了两个同族漏洞：guard 看到的是 bash scripts/release.sh 或 npm run deploy，而不是脚本里那句 git push；另外 matcher 只写 Bash 就永远看不见 MCP 工具直接推文件或合 PR；立场说明：可操作结论是把命令白名单换成工具白名单，并逐个 hook 用 git -C . push、sh -c 'git push' 这类脏输入做回声测试。
- u/Individual-Shower973（赞数：1·归档快照，楼主）："So the message steers the next move as much as the block does" 他用自己的会话验证：仓库 guard 拦住任何提到 git push 的命令、并回复「改用文件工具写这段文本」，agent 下一步就真的改用文件工具绕过去；立场说明：拒绝文案要和拦截本身一样被设计，只写 BLOCKED 会逼 agent 去找别的 remote 或 token，写成「停下来报告分支名」才会让它收手。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x5tbps/

---

## 2. 会话记忆的真实天花板：MEMORY.md 只加载前 200 行，子代理根本拿不到

**摘要：** 作者独自维护几个项目（一个网站、一本书、一套电商 agent 栈），以前每个新会话都要重讲一遍服务器怎么重启、CMS 跑在 1338 端口、博客只能存草稿。他的解法是把每次踩坑变成一条短规则文件，再加一行索引写进 MEMORY.md，会话启动时自动加载（前 200 行或 25KB，先到先算），现在已经攒到 182 条；更长的项目历史放进 Logseq wiki，让 Claude 只读与问题匹配的三五页。两个硬教训：规则会过期，所以每条描述行为的规则都带日期，90 天后做一次只读复核再决定留不留；子代理不继承 MEMORY.md，规则得写进它的任务书。评论区把他的方案算到了上限：按每行约 130 字节算，字节限制大约在第 190 行就撞墙，超出的部分静默不加载；更关键的是「绝不自动发布」这类要求不该放在 memory 里——memory 是上下文不是强制，真正管用的是 PreToolUse hook。

**高赞评论：**
- u/ImL1s（赞数：2·归档快照）："Only the first 200 lines (or 25KB) of MEMORY.md load at session start, and anything past that is silently not there." 他建议把真正的项目配置移进仓库的 CLAUDE.md 或 .claude/rules/，只对特定文件生效的规则用 paths: frontmatter 按需加载，MEMORY.md 退回成一份短索引；立场说明：这条把「记忆系统」从玄学拉回到字节预算，也点明 memory 不能当权限用，强制必须走 hook。
- u/iam-stevie-bee（赞数：3·归档快照）："Mine ended up in three layers, and the split matters more than the tool." 他的三层是：每个项目一个角色 skill（会话开始和每次 compact 后重载）、一个最新块在前的交接文件、一个由 SessionStart hook 在压缩后重新注入的结构化状态文件；立场说明：可直接照搬，尤其是「压缩正是丢信息最多的地方」和「子代理从零开始，规则每次都要写进 brief」这两条。
- u/Routine-Appointment5（赞数：2·归档快照）："when something changes i drop in a new file with the date in the name instead of rewriting the old one" 他的做法更轻：不维护 MEMORY.md，只放一份简短 brief 加项目内笔记，环境一变就新建带日期的文件，新会话读最新的、旧的留作历史；立场说明：省掉了手工改写和判断过期的成本，代价是要靠文件名排序而不是索引来保证新会话读到正确版本。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x8aikj/

---

## 3. 实测「用 HTML 回答」的省 token 技能：输出少了 68%，账单几乎没动

**摘要：** 作者想验证那个让 Claude 用 HTML 页面回答的技能到底省不省 token。设置很干净：Claude Code、Sonnet 5.5、medium effort、每题全新会话，同一个问题问两遍。结果是技能组输出 3,501 token、31.8 秒、约 0.19 美元，直接写 HTML 是 10,831 token、72.7 秒、约 0.20 美元——输出少了 68%、快了约 41 秒，但价格基本持平。原因在调用结构：技能把 1 次模型调用变成 5 次，读进去的上下文从 43K 涨到 159K。质量上直接写的页面更清楚，技能生成的图里还有一处事实错误，把「窗口满了」画成「进程结束、开新会话」，而 Claude Code 实际是压缩后继续。评论区补上了正确的度量口径：看输出 token 是错的，要看 cache_read 加 cache_creation。为什么值得关注：几乎所有「省 token」的技能和插件宣传都在拿输出说事，而账单在缓存读写上。

**高赞评论：**
- u/Drasezv（赞数：2·归档快照）："output is a small slice of the bill" 他自己的 19.6k 次请求里，输出只占 token 的 0.2%、成本的 9%，其余全是上下文；立场说明：这是本期最有用的一句度量纪律——任何声称省 token 的东西都要跑完整轮次的 cache_read 与 cache_creation，而不是比输出长度，否则「一次调用变五次」这种结构变化会被完全掩盖。
- u/Sufficient-Storage87（赞数：1·归档快照，楼主）："the reads are the real gap: 122,837 vs 10,074" 他按建议回查了两次运行的数据，承认省下的输出被重复读上下文吃掉，写缓存也从 21,735 涨到 32,980；立场说明：作者愿意公开否掉自己技能的前提，这条比结论本身有价值——同一批数字既证明了方法有效，也证明了被宣传的收益不成立。
- u/Aware-Match1363（赞数：1·归档快照）："the bill didn't move, the model still has to read your whole prompt and the system prompt before it draws the stupid arrow." 立场说明：语气冲但结论对——省的是输出那几个 token，模型读 prompt 和系统提示的成本一分没少；这条也说明「让模型少写点字」类的优化在总账上通常只是噪音。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x8ku98/

---

## 4. 按任务类型而不是按心情选模型：30 次盲评加一份缓存账本

**摘要：** 有人问「什么时候该用哪个模型、哪档 effort」，最高价值的回答是实测而非感觉：30 次运行、Sonnet 对 Opus 同任务、盲评打分。结论按任务类型切开——批量读取、仓库审计、计数制表交给 Sonnet（3/3 打平，有一次逐字节相同），从已抓取的文本里抽事实也是 3/3 打平；要给人读的文档、文案、commit message 用 Opus（Sonnet 过了格式检查但 2/3 次破坏风格规则），code review 用 Opus（Sonnet 1/3 次漏掉最严重的 bug），带测试的改动也用 Opus（Sonnet 1/3 次跳过 CLI 路径）。意外发现是 Sonnet 在 token 和墙钟上一点都不便宜：2.60M token / 36 分钟 对 2.42M / 25 分钟，省下的只是套餐里的单价权重。另一条被反复强调：给子代理显式指定模型，不指定就继承父会话的贵模型。评论区再补一刀：他自己 7 天 1,332 次调用里 97% 的输入是缓存读，账单其实在写缓存。

**高赞评论：**
- u/Exciting-Yam-3363（赞数：1·归档快照）："I measured this instead of guessing, 30 runs, Sonnet against Opus on the same tasks, scored blind." 立场说明：这张按任务类型的分工表可以直接用，但真正的信息量在最后一句——便宜模型在 token 和墙钟上并不便宜，所以「换小模型省钱」的前提必须落到套餐的单价权重上，否则只是把成本从单价搬到轮次。
- u/xapep（赞数：1·归档快照）："an unnamed subagent inherits the parent's model, which is how the expensive model sneaks back into the cheap lane." 立场说明：点出最容易漏的泄漏点——不指定模型的子代理会静默继承父会话的贵模型，把分模型省钱的计划整个抵消；他另外建议表里加一列缓存读，因为仓库审计类任务每次都要重新加载上下文。
- u/Tight_Ad_5115（赞数：1·归档快照）："Sonnet ends up costing about the same per task as Opus when you account for the effort required to get comparable results." 立场说明：反方经验值得保留——把「为拿到同等结果要多花的返工」算进去，Sonnet 每个任务并不比 Opus 便宜，Haiku 又弱到不敢用在会丢用户的地方，所以他一直用 Opus Medium；这和第一条实测形成有用的张力，而不是谁对谁错。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x7ppww/

---

## 5. 跑 e2e 测试时 Claude Code 拒绝创建账号：规则边界与三个合规解法

**摘要：** 用户在用 Playwright 跑端到端测试，其中一步是在自己的私有 Argo 集群上创建账号，Claude Code 直接拒绝，因为它内置的规则不允许创建账号，除非目标是 localhost、127.0.0.1 或 *.test 这类本地开发主机、且凭据来自项目自己的 seed 或 fixture。评论把边界说清楚了：规则比看起来窄，但没有覆盖开关，而且它判定的是「创建账号」这个行为本身，不只是主机名——所以把集群端口转发到 localhost 之后仍然被拒，因为测试步骤里明写着创建账号。可行做法是把注册从 agent 手里拿走：用 seed 脚本或后台 admin API 预造 test-user，Playwright 只负责登录；确实需要每次全新账号就参数化成 test-user-<run id> 并在 globalSetup 里调用；会话用 storageState 存下来复用，让 Claude 只跑 npx playwright test 并读结果。为什么值得关注：这是「模型内置安全规则撞上正常工程流程」的典型样本，解法不是绕过规则，而是把不可预测的 agent 从可复现的测试路径里移出去。

**高赞评论：**
- u/Exciting-Yam-3363（赞数：0·归档快照）："The rule is in Claude Code's own instructions, and it is narrower than it looks." 他解释规则要求主机是本地开发域名且凭据是项目自带测试值，没有 override，并给出干净解法：让 Claude 跑 npx playwright test、由你的 fixture 去注册；立场说明：这条把「为什么被拒」讲成了机制，而不是让用户去猜，也顺手否掉了自己先前「端口转发就能过」的猜测。
- u/GrizzlyKiwiDev（赞数：1·归档快照）："changing who actually does the signup" 他的版本是：把造账号写进 Playwright spec 或 globalSetup，邮箱密码从环境变量取，再在 CLAUDE.md 注明这是自家 staging 集群、测试用户可丢弃；立场说明：这是把「决定要不要建账号」换成「调用一个现成函数」，既满足规则又让测试可复现，顺手解决了 agent 每次重新推理流程的问题。
- u/qa_tinkerer（赞数：1·归档快照）："put account creation in the test code" 他用 setup project 造账号、用 storageState 复用会话，只让 Claude 跑测试命令；另外既然规则本来就允许 *.test，可以给 Argo staging 映射一个 staging.yourapp.test 的主机名；立场说明：属于规则范围内的取巧而非绕过，还附了用 test+timestamp 邮箱命名方便清理垃圾账号的细节，工程上比改规则现实。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x7qygo/

---

## 6. 审 800 行 diff 不如审两句话：把人工审查前移到实现计划

**摘要：** 作者团队用 agentic 开发半年，顺利的部分是三类：改 45 个文件的机械改动、API 面极窄且容易写单测的模块重构、以及验证技术路线是否可行的 PoC。真正难受的是他手上那种产品：拆不成微服务、运行时性能关键、数据管线会以「感觉变差了」的方式影响用户，又难以用单测覆盖。他看到别的团队用 LLM 优化指标，却引入难以察觉的细微回归，于是大部分时间花在审复杂改动上。评论区给的路径是「把审查前移」：先让 agent 写一份实现计划，点名要复用哪些现有模块和模式，审这份计划而不是审 800 行成品——像「比较字节流」这种决定在计划里 30 秒就被否掉，埋进 800 行代码里要花一小时。第二个可操作点：凡是机器能检查的就别写在 md 里，应该变成 lint、CI 或 gate，因为散文式指令是概率性的、失败的检查不是；同一类错误抓到第二次，就该从文档升级成构建时强制。

**高赞评论：**
- u/AdEvening3382（赞数：6·归档快照）："the cheapest checkpoint is before the code exists." 立场说明：这是整串讨论里最可落地的一条，而且他把要求再收紧了一步——计划必须写出「机制」而不只是任务清单，否则一份完全正确的计划照样能藏住实现路径；「每类错误抓到第二次就升级成 gate」是判断文档该不该继续膨胀的标准。
- u/Tariq9977（赞数：1·归档快照）："index a small set of workload contracts by the modules and data paths they actually exercise." 立场说明：把「没法穷举错误」转成可执行策略——按模块和数据路径索引少量固定输入加可测量承诺的契约，改动只跑受影响的部分，回归逃逸后再补最小复现，让测试集从真实失败里长出来而不是从想象里长出来。
- u/Valvador（赞数：2·归档快照，楼主）："this wasn't a duplication of something that already exists, it was a unique choice of how to compare data types via serialized byte streams" 立场说明：楼主从反方追问可扩展性——在不能靠单测覆盖的大型运行时系统里，把所有能检查的都变成 gate 会退化成无穷尽地预判模型怎么犯错；他要的是低成本发现「局部正确、全局错误」，而不是长期当全职审查员。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x8mr3h/

---

## 7. 两台 26 美元 VPS 跑常驻 agent：CPU 配额、systemd slice 与 600 秒静默终止

**摘要：** 作者把 agent 从会睡眠的笔记本搬到两台每月 26 美元的 VPS 上（Hostinger KVM 8，8 vCPU / 32GB / 400GB NVMe，24 个月合约价），目标是多个 bot、定时任务和测试环境并行跑且互不拖垮，顺带对冲算力涨价——他举例 Hetzner 那台 8 核 32GB 独服从 62.49 欧涨到 138.49 欧。第一个坑是 CPU 按 credit 计费：能短时用满 8 核，但只按 4.8 核回补，credit 耗尽后整机被压到 30%（2.4 核），他因此在 10 天里被限速 13 次，于是写了 Hostinger Governor 来监控和让路。评论区给了更底层的替代方案：每个 agent 一个 systemd slice 加 CPUQuota，由内核执行上限而不是外部 watcher，还顺带白拿每个 agent 的内存统计。另一个更容易丢工作的坑是 headless 会话的生命周期：模型结束回合 600 秒后进程被杀，即使后台 agent 还在跑，而且它以 0 退出，runner 会记成成功。

**高赞评论：**
- u/Ctbhatia（赞数：6·归档快照）："a systemd slice per agent with CPUQuota set gives you the same ceiling enforced by the kernel instead of a watcher." 立场说明：把作者自写的 governor 降级成「不必要的应用层补丁」——内核本来就能做配额，还免费提供每个 agent 的内存账；他说这个方案来自「看着一个 agent 把其他 agent 饿死」，修法必须坐在 agent 下面，这句话对多 agent 部署普遍适用。
- u/Excellent-Issue-5956（赞数：1·归档快照）："a headless session gets killed 600 seconds after the model ends its turn while a background agent or Monitor is still running, and it exits 0" 立场说明：这是最贵的静默失败——进程被回收、退出码还是 0，监控看板一片绿但活没干完；他用 CLAUDE_CODE_PRINT_BG_WAIT_CEILING_MS=0 加「要求前台运行」的提示修好，并提醒只能靠日志里那行 terminating 发现。
- u/xapep（赞数：1·归档快照）："a per-agent token budget in the broker, not just a rate limit." 立场说明：把 VPS 的 CPU 计量类比到 API 账单——26 美元机器的 CPU 表会逼你注意到失控循环，比如重试重发 30K 上下文、定时任务每天重跑同一份研究、子代理每轮重读仓库地图，而 API key 的表不会响；建议 broker 里加每个 agent 的 token 预算。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1x5vv6c/
