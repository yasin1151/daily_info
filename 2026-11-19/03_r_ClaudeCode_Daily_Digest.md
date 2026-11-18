
# r/ClaudeCode 每日精选 · 2026-11-19

Reddit 全端点在本机仍不可达（www / old.reddit / redlib 全部 http=000），本期正文与评论取自 arctic-shift 归档。赞数为归档快照，可能略滞后于实时；标 1 的多为入库默认值，不作"高赞"解读，评论按信息密度挑选而非纯按分数排序。

## 1. 只看 diff 的评审方式，正在把工程师养成"信任 agent"

**摘要：**
一位写了十年代码的开发者从 Cursor 迁到 Claude Code 后，发现自己的 review 习惯在退化：界面主要展示 diff，想看清上下文得自己翻文件；提交前跑的深度 review 技能会揪出一堆未必需要处理的边缘情况，agent 又自动改掉，有时把代码复杂度放大十倍也不问一句。直到一次发版后客户陆续报问题，团队才意识到代码库已经变得难以维护。他承认认真评审比"信任 agent"更花 token、更花时间，所以人自然会滑向后者，并追问不把自己当 vibe coder 的人是否也有同样感受。值得关注的是评论区的分裂：一派认为这是权限模式和团队规范问题，可以自己收紧；另一派认为产品形态本身就在奖励"少看代码"。

**高赞评论：**
- u/DCON-creates（赞数 25·归档快照）："Vibecoding is not suitable for a production level application. You will end up with unmaintainable slop very quickly." 立场说明：他把矛头指向"不审就合并"的用法，认为模型只是更会绕路，质量滑坡的锅在流程与团队标准，不在模型本身。
- u/EarlDwolanson（赞数 12·归档快照）："I use it inside vstudio or another IDE, so I can check properly what is being suggested at each stage." 立场说明：实操解法是回到 IDE 里逐阶段看改动、顺手留注释和骨架，而不是在终端里只吃一份 diff。
- u/idemasler（赞数 3·归档快照）："the dangerous part isn't the diff, it's letting a review agent fix every issue it flags." 立场说明：建议让 review 只列受影响的调用方和不变量，一旦修改越界到新模块或公共 API 就停下，把"发现问题"和"动手改"拆成两步。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xzdi6c/

---

## 2. 同时跑五个以上会话：worktree 只解决一半问题

**摘要：**
楼主同时开着五个以上的 Claude Code 与 Codex 会话，日常状态是一个在等权限确认、一个早就跑完没人通知、两个在不同 harness 里改同一批文件互相覆盖。tmux 和多开终端标签在四五个之后就不够用，他开始考虑自己写 dashboard，先来问别人怎么管。评论给出一套分层答案：写冲突用 git worktree 或独立 clone 隔离，但端口、测试数据库这些 git 之外的东西仍会互相踩；"哪个会话在等我"要用 Stop hook 判断，而不是靠人盯；任务认领则最好有一块共享看板。值得关注的是这些细节都来自真实事故，不是工具安利。

**高赞评论：**
- u/Excellent-Issue-5956（赞数 1·归档快照）："checks the last 400 characters of the final message for a question mark" 立场说明：他用 Stop hook 截取收尾文本，命中问句或"want me to"这类措辞再让便宜模型读 transcript 判断是否真在等人，只在需要时弹卡片；他还指出最难的一类冲突是两个会话在做同一件事却互不知情，worktree 救不了。
- u/anderson_the_one（赞数 1·归档快照）："Five isolated checkouts can still share one dev server port or test database and break each other's runs." 立场说明：worktree 只隔离了 git，会话之间还要分配独立端口和测试库，面板优先展示"被阻塞的会话"和"已完成的 diff"。
- u/Lopsided-Ad-6298（赞数 1·归档快照）："two harnesses should never share a working tree" 立场说明：先消灭冲突源再谈可视化——每个 worktree 只挂一个 harness，会话数量砍到能真正盯住的程度，需要长时间跑的会话在目录里留一张交接便条。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xzk6uy/

---

## 3. 多 agent 长跑的隐性账单：磁盘被自己的残留填满

**摘要：**
一台 256GB 的 Mac 上同时跑 Claude Code、Codex 和 opencode，19 天里手动清了 45 次垃圾，最低只剩 125MB；每次能收回 10 到 16GB，但忙的一天两个半小时又写回 17GB。楼主让 agent 记录每次删除的内容，发现元凶不是缓存和日志，而是 agent 自己的产物：/private/tmp 里 26 份 DerivedData（6.5GB）、~/.claude/projects 里 11GB 会话记录（单个日志 262MB，其中 175MB 是 base64 截图）、worktree 里的 Rust target、iOS 模拟器和被挤出来的 swap。中途还有一次把两个测试包的源码当构建垃圾删了。他现在的规则是只删三小时没动过的文件，退出时再检查未合并的 worktree；更根本的做法是把清理写进 hook，而不是靠人记得。值得关注：这是多 agent 并行开发的固定成本，换大硬盘只是把死线往后推。

**高赞评论：**
- u/Competitive-Class576（赞数 3·归档快照）："I asked it to create rules to ensure everything merged and cleaned up at the end of the session" 立场说明：他把清理做成会话结束协议，但必须显式喊"结束会话"才会触发；不做的话单个项目能留 100GB 临时文件和未合并的 worktree，代码有丢的风险。
- u/Federal_Notice_1655（赞数 1·归档快照）："my workspace folder hit 95G, mostly agent worktrees" 立场说明：清理 worktree 前先检查有没有未提交改动（agent 常把真活留在里面），删完再跑 git worktree prune 让 git 忘掉死路径。
- u/Extra_Aide5999（赞数 1·归档快照）："we had 439 of them" 立场说明：跑 headless Chrome 做截图或页面检查的 agent 会留下大量签名副本和 profile，他们的做法是每个脚本用独立 scratch 目录、在 finally 里删除并杀掉自己启动的浏览器。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xzgmo3/

---

## 4. Superpowers 这类技能包，是不是已经变成负担

**摘要：**
有人发视频称最流行的 Claude skills（以 Superpowers 为代表）如今已是臃肿软件：早期确实提升输出质量，但模型进化后，这些附加流程只让工作更慢、更贵。楼主拿自己的体验来求证。评论区几乎一边倒地说"九个月前好用，现在多余"，但同时有人拆视频作者在卖课、对比方法也不严谨——没有控制模型与 effort、只看 UI 不看 bug 数量。少数保留意见认为 brainstorming 和写计划仍值得留，尤其在多人协作时，spec review 是 code review 的前置。值得关注：这是技能生态的折旧问题，每次模型升级都该重估自家 skill 是否在限制新模型。

**高赞评论：**
- u/CorpT（赞数 115·归档快照）："It was great 9 months ago. Mostly unnecessary now." 立场说明：本线程最简洁的多数派结论——技能的价值会随模型能力上升而衰减，老配置需要定期清理而不是永久供奉。
- u/Kiobaa（赞数 39·归档快照）："My take on Superpowers review is that the measurements are flawed." 立场说明：他指视频一边卖课一边做评测，加入规划与评审步骤后必然更慢更贵，比较本身不公平，且没提模型与 effort；建议自己按实际任务做有/无对照。
- u/chiefbriand（赞数 28·归档快照）："asking your AI is worthless" 立场说明：反对"让模型自评技能是否冗余"这种做法，认为模型判断自身能力不可靠，要同任务跑两遍看最终结果差异。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xz7w0k/

---

## 5. 被反转的决策为什么总会回来：记忆检索的污染问题

**摘要：**
楼主把项目决策存进 Claude Code 会话开始时会读的 memory，结果吃了两次亏：三周前记下"用 Redis 存 session"，后来改成 Postgres，按相似度检索照样把旧结论捞出来；另一次新写的修复因为和旧笔记不共享关键词，agent 只找到新笔记，最终把改动写进了一个没人读的 JSON。他的缓解办法是给笔记加"取代/依赖"这类显式链接，但承认这依赖人记得去标。评论区给出更工程化的答案：用 ADR 分层、旧决策标记为被取代而不是并存、规则放 repo 而不是 memory。值得关注：这是长期项目里"记忆污染"的具体形态，靠提示词约束不住，只能靠文件结构与检查。

**高赞评论：**
- u/LawfulnessLocal4934（赞数 2·归档快照）："When a decision changes, the old one isn't deleted—it gets marked as Superseded by ADR-XXX" 立场说明：他把仓库分成 CLAUDE.md（只放交互规则）、canon/（现状地图）、decisions/（ADR）、state/（进行中状态），让检索永远只有一个当前答案。
- u/zzunkie（赞数 2·归档快照）："I overwrite the old decision in place in whichever file owns that fact" 立场说明：一条事实一个文件、原地覆盖、历史交给 git；再加一个 pre-push 检查，防止"截至某日"式注释越堆越多。
- u/Corroding-coder89（赞数 2·归档快照）："one skill file said a guard was turned off while the project settings were still running it on every edit" 立场说明：他审计一个月会话后发现同一规则在 skill 与 settings 里互相矛盾；现在规则集中在单文件、日志只追加且禁止回读，规则变更集中评审（他坦言每周评审没坚持下来）。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xyrq2k/

---

## 6. Pro 额度不够用，先改上下文卫生再考虑升级

**摘要：**
一位用 Pro 计划做 Unity 手游的开发者每天都在撞额度，希望在升级 Max 之前确认 CLAUDE.md、skills、subagent、上下文管理这些手段里哪些真的有用。回答相当一致：花销大头是重复阅读而不是写代码，所以 CLAUDE.md 要极小，只放构建命令、目录结构和硬规则（控制在百行内），Unity 的场景约定、prefab 规则拆到按需加载的文件或 skill；一个任务一个会话，结束前写交接笔记；先 plan mode 再执行；提问直接指到具体文件，别让它全仓搜索，并把 Library、Temp 加进忽略。值得关注：冷掉一小时的会话不要 resume，缓存过期后等于把整个上下文重新计费一遍。

**高赞评论：**
- u/torvalds75（赞数 2·归档快照）："Most of the usage on a long project goes to Claude re-reading things, not to writing code." 立场说明：他的经验是上下文卫生比选模型更影响额度，重复压缩本身就是"该开新会话"的信号。
- u/brusegan（赞数 2·归档快照）："What helped most wasn't model choice: Scripts for anything repetitive." 立场说明：把固定六步流程写成脚本让 agent 只跑一条命令，skill 里附 gotchas 记录踩过的坑，Opus 只做规划与评审，批量杂活交给 Haiku。
- u/devgeniu（赞数 1·归档快照）："don't resume session that have stayed cold for over an hour" 立场说明：缓存过期后再恢复会话会把整段上下文重新算钱，宁可用交接文件开新会话，并用缓存指示器判断哪些会话还热。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xzavjg/

---

## 7. Fable 5.2 的"懒"，可能一半是归属提示的问题

**摘要：**
楼主用同一任务对照 Fable 5.2 和 Opus 5.5，结论是前者深度够但极懒：灌了一堆规划与实现信息只回一句"nothingburger"，让它当编排者时又自认有偏见、额外 spawn 五到十个 agent 复审，结果漏掉的还是它自己的错；Opus High 几乎零错。评论指出两个被忽略的变量：他拿 Fable Medium 对 Opus High，多出来的错误可能来自 effort 而非模型；另外 Anthropic 文档写明 Fable 更倾向不越权，会把自己当成别人仓库里的客人，明确写出"这是你的代码库、你有权决定"能明显改变行为——文档数据是合并重复代码的比例从不到一成升到约七成五，代价是输出 token 涨七到八成。值得关注：所谓"模型变懒"，经常是授权与归属提示没写对。

**高赞评论：**
- u/brodkin85（赞数 24·归档快照）："Fable views itself as a guest in someone else's repo" 立场说明：先读官方 prompting 文档再评判模型；把 ownership 和可自主决定的范围写清楚，比反复催它"动手"有效。
- u/who_am_i_to_say_so（赞数 12·归档快照）："Fable 5.2 is a great pretender. It digs deep but never actually finishes anything." 立场说明：它的问题不是分析浅，而是收尾执行力差，在小而清晰的项目里这种特性尤其吃亏。
- u/Glaucus_Blue（赞数 4·归档快照）："You are the owner and long-term maintainer of this codebase" 立场说明：他贴出文档原句和量化效果，同时提醒副作用——模型会顺手加上没人要求的测试与文档，甚至改动既有行为。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xxsqu4/

---

## 8. 自动压缩有两个开关，多数人调错了那一个

**摘要：**
Claude Code 现在会在会话空闲、缓存过期且上下文超过 200k 时自动压缩，楼主发现压缩后 Claude 会忘掉关键细节，于是把阈值提到 450k，并希望官方给个可控的压缩时机。评论澄清这里其实有两个不同机制：空闲那条由 CLAUDE_CODE_IDLE_COMPACT_MIN_TOKENS 决定，通常在一小时缓存过期后触发；工作中触发的是 settings.json 里的 autoCompactWindow（100k 到 1M），或 /autocompact 500k，且只对当前模型生效；只关空闲压缩用 "idleCompaction": false，而 CLAUDE_AUTOCOMPACT_PCT_OVERRIDE 只能让它更早、不能延后。还有人指出摘要不知道编排者在乎什么，常留下寒暄、丢掉硬规则。值得关注：不少"模型变笨"的抱怨，其实混用了这两个阈值。

**高赞评论：**
- u/Nonomomomo2（赞数 5·归档快照）："It sucks. My orchestrators get much less effective as a result. I switched it off." 立场说明：编排型会话对摘要最敏感，一旦规则被压掉整个流程就失序，他的选择是直接关闭。
- u/Janday_Luden（赞数 2·归档快照）："the summary prompt doesnt know what the orchestrator actually cares about" 立场说明：压缩摘要的目标与编排者关注点错位，结果保留了对话废话、丢掉了必须遵守的严格规则。
- u/SirRobinBlibs（赞数 1·归档快照）："autoCompactWindow, a token count from 100k to 1M in settings.json" 立场说明：先看终端里那行"Compacted while idle"判断是哪一种压缩，再决定改 autoCompactWindow 还是关 idleCompaction，否则调的是一个没生效的旋钮。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1xtmqf8/
