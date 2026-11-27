
r/ClaudeCode 每日精选 · 2026-11-28

Reddit 全端点仍处于 IP 层封锁（www.reddit.com、old.reddit.com 和 redlib 公共实例均返回 000），本文经 arctic-shift 归档通道抓取正文与评论。赞数是归档快照，可能滞后；标注「归档快照」的多为入库默认值 1，不代表真实热度，也不据此做高赞排序。

---

## 1. Sonnet 加 /advisor Opus 的省钱策略被实测证伪

（原文：Sonnet with /advisor Opus was overhyped）

**摘要：** X 上流传一个省钱策略：主模型用 Sonnet，只在需要时通过 /advisor 让 Opus 插一句，就能以零头成本拿到 Opus 的能力，那条帖子拿到大量点赞转发。作者用多小时的编码会话实测：整场 Sonnet 只主动叫了 Opus 十几次，问题始终没解决，反而烧掉 Pro 计划 25% 的用量；一旦切换到 Opus 并让它读取聊天记录，问题立刻解决。他认为唯一站得住的技巧是反过来——让 Opus 派 Haiku 子代理去做低推理的杂活，其余热门 hack 基本无效。值得关注的是「弱模型判断何时该叫强模型」这个结构性缺陷：调度本身需要能力，越省越容易卡在错误的地方；想省钱应该用同任务对照验证，而不是照抄推文。

**高赞评论：**
- u/OkLettuce338（赞数 21）："Having opus design the implementation, having sonnet build it, and having opus review it before merge is a pretty solid strategy." 立场说明：有效的不是随机插话，而是把 Opus 固定在设计端和合并前审查端，Sonnet 只承担实现。
- u/Australasian25（赞数 14）："Sonnet is half the price of opus, but I think its more than half dumb" 立场说明：只认 Opus 加 Haiku 抓取的搭配，认为 Sonnet 价格减半但能力下降幅度超过一半。
- u/Lost-Air1265（赞数 11）："I don't use sonnet at all. Too expensive for its intelligence." 立场说明：用 Fable 编排、Opus 实现、Haiku 抓取，完全跳过 Sonnet，理由是事后返工比省下的钱更贵。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y6ltxz/

---

## 2. 规划和代码审查仍然吃掉全部人工时间

（原文：Planning and code review take too much time with Claude Code）

**摘要：** 作者使用 Opus 5.5 的 xhigh 档来开发一个复杂框架，遇到的问题集中在两处：规划和代码审查吃掉大量人工时间；即便给 planning 和 review 各写了 skill，也没有改善——只要不逐条讨论并核对，质量就会下降，Claude 也会犯很莫名的小错。他看到 Anthropic 和别家宣传「同时管理上万 agent、几乎全自动」，反而怀疑是自己方法不对。评论区的思路不是寻找更强的 skill，而是把质量保障从「人读代码」转到「机器可验证」：计划阶段先写验收测试，每次编辑后用 hook 跑 typecheck、lint 和测试，声称完成时必须故意破坏功能确认测试变红；审查交给另一个模型，而不是让同一个模型再审一遍。值得关注的是这条落差：官方演示多为边界清晰的 CRUD 任务，复杂框架里的人工判断仍是瓶颈。

**高赞评论：**
- u/Ok-Motor-9812（赞数 11）："High is enough for planning and medium for all other work." 立场说明：降档比加 skill 更有效，xhigh 会过度思考并制造更多错误。
- u/DARKUNIT22（赞数 6）："That's all marketing." 立场说明：指出宣传方不为自己烧的 token 付费，把他们的用法当成必须模仿的标准是误判。
- u/bostonaholic（赞数 2）："I don't read most of what my agents write anymore, and that time goes into the checks instead." 立场说明：把人工从读代码转到检查项，用验收测试、钩子和故意破坏来兜底。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y6v73q/

---

## 3. 跨模型交接到底该交什么：大家一致否掉 transcript 和摘要

（原文：Plan in one model, code in another: what do you hand over so the second one doesn't start from zero?）

**摘要：** 作者引用一份实践者写作的数据：模型之间切换平均要花 23 分钟做上下文管理，一天切四到五次就损失近两小时。他明确说明这是自报数据、不是独立基准，只当作提问的理由。真正的问题是交接内容：换模型或开新会话时，你交过去的是粘贴的对话记录、一份摘要，还是自己写的短笔记？哪部分最常重打？有没有哪次交接漏掉一条约束，几步之后才发现？评论区高度一致地否掉 transcript 和摘要——前者太长、重点被埋，后者保留结论、丢掉推理。大家实际在用的是仓库里的交接文件：写明目标、分支与未提交文件、已做的决定、被否掉的方案各一行原因、下一步指向哪个文件。值得关注的是「被否决的方案」最先丢失，而它恰是下一个模型重复踩坑的地方。

**高赞评论：**
- u/Amazing-Potato-3096（赞数 1·归档快照）："Pin the tree, not just the intent." 立场说明：交接必须钉住分支、HEAD 和未提交文件，否则新会话会自信地审查不存在的代码；还要求三行 read-back 验证读没读。
- u/AgentYurt（赞数 1·归档快照）："'continue' on its own isn't a handoff, and the blocking file is usually what the next session wastes time re-discovering." 立场说明：下一步必须指向具体文件和卡点，光说继续等于没有交接。
- u/tom_aa（赞数 1·归档快照）："Summaries are worse, because they keep the outcome and drop the reasoning." 立场说明：摘要比原文更糟，被否决的选项因为「丢掉时感觉已完成」而几乎不会进任何交接。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y60gzo/

---

## 4. 「不做清单」放在哪：负面需求正在成为 agent 上下文的关键一类

（原文：where do you write down what you decided not to build）

**摘要：** 作者团队在每个功能规格旁放一份「不做清单」，目的很具体：防止 coding agent 出于好意把它顺手建出来，agent 开工前会先读这份清单。他问大家的清单放在哪里、是否还维护。回复里位置不如写法重要：清单要放在 agent 每次都读得到的文件里，多半就是规格文件本身，或 CLAUDE.md 指向的规则文件；每一条「不做」后面必须跟原因，光写不要做某功能会被某个自认为有更好主意的会话推翻。再进一步是区分「这版不做」和「试过并否决」，前者要写清什么条件下值得重拾，否则下一个会话要么立刻重做，要么把临时缩范围当成永久决定。真正不能破的规则不能只靠文字，要落成构建检查或测试。值得关注的是负面需求正在成为 agent 上下文里被低估的一类。

**高赞评论：**
- u/Typical-Age3744（赞数 7）："we keep it in the same markdown file as the spec, right after the feature list" 立场说明：清单贴着规格放在同一文件，保证始终在上下文里，而不是另开一个没人打开的文档。
- u/Fancy-Proof-9449（赞数 3）："Text for the reasons, tests for the stuff that has to hold." 立场说明：文字只用来写原因，真正不能破的规则改成构建检查，因为他的规则被违反过三次。
- u/Starks1293（赞数 2）："decisions never get edited after the fact. if i change my mind its a new dated file that points at the old one" 立场说明：决定只追加不改写，避免会话把两个月前的否决当成现状。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y61zc3/

---

## 5. 让 Claude Code 以攻击者视角审自己的站，五个里三个只拿到 C

（原文：I had Claude Code look at my own sites like an attacker would and I didn't exactly love what it found）

**摘要：** 作者有五个用 Claude Code 搭的小站，从没从外部视角检查过安全性。他让 Claude Code 按攻击者视角扫：看每个站发给浏览器的 JavaScript、试 .env 和 .git 这类常见路径、检查响应头与 DNS 记录；更主动的越权测试放在本地副本上用测试账号做。结果五个里有三个只拿到 C：一个跑着带已知严重漏洞的旧版 Next.js，因为站点能用就没人提醒他升级；一个允许任何免费注册用户让他的应用代发邮件；两个域名可被任意人冒发邮件。当天全部修完，每个修复另开一个会话复核。值得关注的是这些都不是难发现的问题，只是没人看过；评论区还暴露另一层现实，很多人第一次尝试就被安全分类器拒答，之后再没敢问，而把上下文说清楚（自己的站、防御目的、生产只读）就能通过。

**高赞评论：**
- u/krum（赞数 81）："The last time I tried this Claude told me it wouldn't do it and I've been afraid to ask again since." 立场说明：拒答造成的「学会不问」比拒答本身更有害，这是分类器最隐蔽的副作用。
- u/silverace00（赞数 25）："Ask it for a security audit." 立场说明：换一句「做一次安全审计」就能过，措辞本身就是实际门槛。
- u/clintCamp（赞数 6）："They will always find something and then start overstaying the importance of their findings" 立场说明：AI 审计会不断找出东西并夸大严重性，缺少「我什么也没找到」的样本，需要人来判断何时收手。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y5iki8/

---

## 6. 「模型更强了，但什么都变慢了」：一套可查的分诊顺序

（原文：I don't understand the models are getting better but it's now taking longer to do everything?!? Even with Claude Code. I am currently using Claude Max. Everything I'm doing in Claude code now feels almost 100% slower!）

**摘要：** 作者在 Max 计划上，觉得 Claude Code 现在几乎慢了一倍，怀疑 Anthropic 在用量上做手脚：一次较大的更新要两天多，给项目增加三条规则要将近两小时。评论没有停在情绪上，而是给了一套分诊顺序：先看档位，日常用 Opus medium 甚至 Sonnet 就够，xhigh 容易陷入过度思考反而更容易出错；再看是不是任务块变大、上下文变长，长上下文本身会显著降速；然后审计 memory，看 agent 是否把一次性指令写成记忆、反复跑同一套检查；最后要承认共享算力下吞吐会波动。有人给出更硬的实证路径：用 Claude 自己诊断，把每次合并要跑 43 分钟的测试套件压到 3 分 28 秒。值得关注的是这个最常见的抱怨多数是可查的工程问题，而不是单纯的限速阴谋。

**高赞评论：**
- u/LetOtherwise9755（赞数 26）："Maybe don't use Max then lol. Just use Opus medium for most tasks." 立场说明：先怀疑档位设置而不是限速，多数任务不需要最高档。
- u/Desalzes_（赞数 12）："Results should be better than older models, I don't mind slow if it's not building ontop of bullshit" 立场说明：变慢可能来自更厚的自动检查，只要结果更好、不是在烂代码上继续叠加就可接受。
- u/c0reM（赞数 5）："Also it's faster with less context. If your context is running long it will slow down a lot." 立场说明：长上下文与 memory 膨胀是主因，加上共享算力带来的吞吐波动，属于可验证的工程问题。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y66uc9/

---

## 7. 账号随时可能被封之后：自托管 LLM 到底能不能顶上

（原文：Considering self-hosted LLMs as an alternative to Claude）

**摘要：** 提问者是网络与系统工程师，用 Claude 一年半、一直在最高档订阅，对效果很满意。让他动摇的不是能力，而是最近一批账号被封、支持渠道基本无效的报告：个人订阅对 Anthropic 无足轻重，但失去访问会直接打断工作，出事时又找不到人，这种不对称让他开始考虑自托管。他不想买硬件，倾向租 GPU，问的是两件很实际的事：成本上是否划得来，以及在复杂多样的技术任务上能接近 Claude 到什么程度。回复结论相当一致：今天就替代不了，开源权重落后前沿大约九个月，Kimi 这类模型托管成本极高；真要投入就先用 Qwen、MiniMax 跑小模型，四张 5090 或 Mac Studio 能到每秒一百到一百三十 token。更务实的建议是把工作流和数据存储与厂商解耦，数据进 git，Claude、Codex、Gemini 都能接，开源模型作兜底。

**高赞评论：**
- u/ARKyal03（赞数 37）："Not viable as of today. Open-weight models aren't as good as Opus." 立场说明：自托管当前不可行，开源权重差距明显，大模型托管成本极高。
- u/jastice（赞数 5）："Build your workflows and especially the data storage separately from the model provider's tools." 立场说明：真正的对策是解耦工作流与数据存储，模型可换，流程不必重写。
- u/mother_a_god（赞数 4）："The open weight models are 9 months behind, which means they are very capable, and with a good harness can do good work" 立场说明：开源落后约九个月但配好 harness 能干活，别扭感来自已经用过前沿模型。

**原帖：** https://www.reddit.com/r/ClaudeCode/comments/1y6rfri/

---

抓取说明：Reddit 全部端点（www.reddit.com、old.reddit.com、/.rss 以及 redlib.perennialte.ch）本次仍返回 000，I/O 超时；GitHub API 正常，因此改由 arctic-shift 归档通道抓取。共拉取 7 个时间窗口、662 个候选帖；扫描 343 份历史 digest，排除已推送的 558 个 id 后，得到 641 个新帖；筛除展示、招聘、抽奖、梗帖后，预测 54 个候选帖的评论树（0 失败）；最终选定 7 条。质检结果：7 节摘要中文字数为 205/221/259/250/251/226/248，全部落在 150–300 的区间内；每节恰好 3 条评论，21 条引文都经归档原文逐字比对，0 处不符。blogwatcher 扫描因 RSS 超时失败，read-all 返回无未读，均已容错处理。
