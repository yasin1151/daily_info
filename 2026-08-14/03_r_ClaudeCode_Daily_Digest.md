
# r/ClaudeCode 今日高信号讨论

## 1. Opus 5 / Sonnet 5 / Fable 5 可能绕过“编辑前必须读文件”的保护

**摘要：** 这帖拆出一个很具体的 Claude Code 行为变化：5 系模型在 Write/Edit 工具里可能不再强制“先读文件再改文件”，作者观察到 Fable 在写测试时更容易覆盖已有内容。它值得关注不是因为结论已经完全坐实，而是因为评论区出现了可复现的分歧：有人刚测试仍被拦截，有人则在多代理同一 worktree 协作中把这个保护视为防覆盖的关键防线。对使用子代理、并行编辑、让模型补测试的人来说，这类工具层 guard 的变化会直接影响代码安全边界，最好用本地 hook、只读后写策略或测试保护重新兜底。

**高赞评论：**
- u/KevlarRelic（4赞）：反馈自己刚让 Fable 在未读文件前写入时仍被阻止，猜测可能是“显式要求它绕过”触发了不同路径。立场说明：这条提醒不要把帖子当成确定公告，应在自己的 Claude Code 版本和提示方式下复测。
- u/Ok_Intern9738（4赞）：描述自己用 Opus 做 orchestrator、生成大量 Sonnet 子代理且自己也在同一 worktree 修改代码；“写前重读”能避免代理基于旧视图覆盖别人刚改的内容。立场说明：这是最有操作价值的场景，说明该 guard 对多代理并行不是形式主义，而是并发控制的一部分。
- u/NefaDots（1赞）：说这解释了模型在被要求往文件加内容时，像是凭印象猜测文件内容的行为，并已把它加入自己的 hooks 清单。立场说明：即使赞数不高，也给出实用结论：把“编辑前确认最新文件内容”下沉到本地规则或 hook。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vn1h5t/opus_5_sonnet_5_and_fable_5_do_not_need_to_read/

## 2. Caveman 被 JetBrains 质疑后改成输入压缩代理

**摘要：** Caveman 作者承认早先“输出 token 省 65%”的说法在 JetBrains 长任务基准下只剩约 8.5%，但也借此把项目从“让代理少废话的风格技巧”重构成 Claude Code / Codex 前面的本地代理：在每次 provider 调用前压缩输入，保持原内容可恢复，并声称 54 次跑分里 provider-reported 输入 token 降 33.2%、18 个精确答案检查全过。这个帖值得关注的点在于，coding agent 的成本大头往往是反复塞入文件、日志、工具输出、MCP 和历史上下文，而不是回复文本；但评论也要求更严肃的 A/B benchmark、缓存命中和多账号负载均衡场景验证。

**高赞评论：**
- u/Economy-Manager5556（6赞）：提醒如果用户有自己的本地代理，在 Claude 与 OpenAI 多账号间负载均衡，缓存 stickiness 和 cache miss 会影响真实节省，不应只看原始 token 数。立场说明：这是部署层面的关键限制，压缩代理要和 provider 缓存、账号路由一起评估。
- u/En-tro-py（2赞）：建议直接用 ContextBench、SlopCodeBench、TerminalBench 等现成基准做有无 Caveman 的 A/B，不要再用自定义方法替代真实 coding interaction 测试。立场说明：这条虽然语气尖锐，但指出了工具可信度的核心：必须用可复现长任务基准证明质量不掉。
- u/VeryVexxy（2赞）：作者回应称目前真实 coding 交互还缺少足够好的通用基准，个人体验仍要优先于任何单一 benchmark。立场说明：这是合理但偏保守的回应；适合把 Caveman 当可试验工具，而不是立即默认接入生产流程。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vn9xyo/jetbrains_called_bullshit_on_cavemans_65_they/

## 3. 用 MISTAKES.md 让 Claude Code 把重复错误沉淀成规则

**摘要：** 这条热帖提出一个低技术门槛但很有争议的 agent workflow：在仓库放 MISTAKES.md，让 Claude Code 每次出错后记录“发生了什么、根因、后果、预防规则”，重复出现的模式再晋升到 CLAUDE.md 的硬规则。价值不在于让模型每次读取一大本错误日志，而是把模糊的“这块经常坏”变成可计数、可审计、可压缩的一行规则。评论区进一步把方案推向更成熟的形态：不要让每个代理随意扩写错误库，要用 hook、测试、lint、工作日志审计、按目录触发的短规则来避免上下文膨胀和规则失效。

**高赞评论：**
- u/makkik（40赞）：说自己加了第二层：在 spec、plan、implementation 之后用 hooks 触发技能检查过去错误和当前工作，已经抓到很多问题。立场说明：这比单纯日志更可靠，把“经验”变成流程中的自动审查节点。
- u/Dienes16（36赞）：质疑仅引用 MISTAKES.md 不足以让 Claude 在正确时机查看，强行塞全文件进上下文也不划算，memory 的短触发可能更合适。立场说明：这是方案的主要反方观点，提醒错误库需要触发机制，而不能期待模型主动检索。
- u/Phearless（8赞）：认为 MISTAKES.md 会随项目变大而失控，建议把可执行的经验转成 lint、代码分析或会让 build/check-in 失败的规则。立场说明：这条给出工程化落点：LLM 规则会被忽略，自动化检查和 CI 才是最终防线。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vn6d5r/i_make_claude_code_keep_a_mistakesmd_file_heres/
