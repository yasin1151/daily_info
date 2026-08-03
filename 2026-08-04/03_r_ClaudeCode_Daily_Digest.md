
# r/ClaudeCode 今日推送

## 1. Nobody outside Anthropic can tell you whether cache reads count against your Pro limit
摘要：这帖把 Claude Code 订阅限额里最容易被误解的“缓存读取”问题拆开：API 文档明确写了 cache write/read 的倍率和 ITPM 规则，但 Pro/Max 的五小时窗口、周限额并没有公开 token 权重。作者翻了本地 JSONL，发现自己总输入里 97% 是 cache_read，单看 input_tokens 会低估几个数量级。值得关注的是，团队若用这些字段评估成本、预测封顶时间或设计自动化监控，必须把“API 计费估算”和“订阅消耗”分开；否则缓存策略、上下文裁剪、模型切换都会建立在社区猜测上，最后误判可用额度和真实风险。

高赞评论：
1. u/actvt_io（赞数：1）：This is exactly the thing I said nobody had posted, so, corrected. The method's better than what I asked for, too. They pulled unrounded doubles out of the SSE responses and recovered the underlying fractions with a Stern-Brocot search, instead of snapshotting /status and diffing it. That gets you per-model credit rates and per-tier ceilings. Their answer t… 立场说明：补充了一种更强的测量路径：从 SSE 里恢复未四舍五入的使用比例，而不是只靠 /status 快照；立场是“可测但未公开，不能当稳定契约”。
2. u/kusa-jp（赞数：1）：you don't have to snapshot /status by hand. the CLI's own usage endpoint is pollable, and it hands you exactly the series you're asking for. GET https://api.anthropic.com/api/oauth/usage , with Authorization: Bearer (accessToken from ~/.claude/.credentials.json) and the header anthropic-beta: oauth-2025-04-20 the response carries a five_hour block with util… 立场说明：指出 CLI 自身的 OAuth usage endpoint 可轮询五小时 utilization 和 reset 时间，并提醒 UA、refresh token 轮换等坑；这是最可操作的自建监控建议。
3. u/Outrageous_Band9708（赞数：1）：from the caching tips, /model opusplan opus as the planner, sonnet as the writer. without needing to switch models. i've considered this and other other solutions. such as subagent per task to keep main plan session clean and lean. my main problem is that sometimes the context from the previous tasks are very valuable in subsequent tasks and without it its … 立场说明：把缓存问题落到 workflow：用规划/执行模型拆分、子代理保持主上下文干净，但也承认跨任务上下文有价值，不能盲目清空。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vejlfo/nobody_outside_anthropic_can_tell_you_whether/

## 2. Opus 5 is a practically unusable model
摘要：这是一条高热抱怨帖，集中反馈 Opus 5 在 Claude Code 里比上一代更容易忘指令、循环修补、解决一个问题又制造新回归。OP 认为问题在 100-150K context 时就出现，而 Fable 5 虽可用但周额度很快耗尽。值得关注的是，评论不是单纯情绪宣泄，很多人给出“必须更强监控、限制 scope、切回旧模型或混用 Codex”的实际迁移信号。对正在把 Claude Code 放进长任务 agent loop 的团队来说，新模型发布后并不一定降低人工成本，反而可能提高 review、回滚和提示约束的负担。

高赞评论：
1. u/Deep-Palpitation8315（赞数：56）：Absolutely. Had several similar experiences. Forgets stuff entirely and creates solutions with new problems and enters an infinite loop. (makes me fear loop engineering) It is a token guzzling garbage generator. I think it has actually done significant damage to a section of my codebase - thankfully it is not irreversible. 立场说明：认同遗忘和无限循环体验，并强调可能损伤代码库；立场是对 Opus 5 的自动执行要保守，必须保留可回滚边界。
2. u/dontTakeMeSerious6（赞数：16）：I’m having this exact experience. It’s also re-solving the same problem unasked for sometimes. Like if I say “review pending issues”, it’ll find issues already solved but not marked as solved in an old document and then resolve them, in a different way. Requires a lot more active participation, which is good, except I’m more baby sitting an over eager devel… 立场说明：给出具体例子：模型会重新解决旧文档里已处理但未标记的问题；立场是现在更像需要 babysit 的过度积极开发者。
3. u/ashaman212（赞数：19）：I used Opus 5 to diagnose a tracing issue and then had Fable review the PR. It found a critical misunderstanding of the escalation stack that flipped where the hooks needed to be applied and a structural issue with the data being kept. That means I no longer use Opus for diagnosis. 立场说明：用真实 PR 复盘说明 Opus 5 诊断 tracing 问题后被 Fable 找出关键误解；立场是不要再把 Opus 5 用作高风险根因分析模型。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1veeuy5/opus_5_is_a_practically_unusable_model/

## 3. Anthropic Gen-5 (Fable 5 / Opus 5 / Sonnet 5): measurably worse nonsense detection + ~2x verbosity — issue with reproducible measurements
摘要：这帖用 BullshitBench 做了一个可复现实验：Gen-5 Claude 在识别“看似合理但实际胡扯”的提示上分数明显低于 4.6/4.8，同时 Opus 5 和 Sonnet 5 在相同 reasoning effort 下输出 token 大幅增加。虽然评论里有人质疑拒答是否被计入，但主题对 Claude Code 用户很关键：如果模型更 verbose、又更容易接受伪概念，agent loop 会放大 token 消耗、错误确认和无效自检，还会让人工 review 更难区分真实推理与漂亮废话。值得把它当作一次提醒：升级模型前需要自己的回归集、胡扯检测和停止条件，而不只看官方 benchmark。

高赞评论：
1. u/Comfortable-Rock-498（赞数：33）：This is counterintuitive but a very interesting result. Counterintuitive because I would have guessed that they doubled down on BS detection, seeing Claude is so eager to challenge your (assumed) assumptions and spend half the response in arguing those straw-men 立场说明：认为结果反直觉，因为 Claude 明明很爱挑战用户假设；立场是这个 benchmark 揭示了“会反驳”不等于“能识别伪概念”。
2. u/KeilerHirsch（赞数：16）：Great point — my data actually explains the paradox: Gen-5 still catches structural logic errors perfectly (causal_chimera 2.0), but fails selectively on plausible-sounding nonsense (reified metaphors: 2.0 → 0.67). It argues against your assumptions while fully engaging nonsense that flatters the framing. That's enthusiasm-oriented post-training, not a capa… 立场说明：作者回应称 Gen-5 对结构性逻辑错误仍强，但对拟物化隐喻等“像真的废话”选择性失灵；这是对实验结论的关键限定。
3. u/H4RZ3RK4S3（赞数：7）：I fully agree with your last sentence. The models are very capable, but something is completely off with the Post-Training, and hence with the instruction-following and answer behavior of Opus/Sonnet 5. I really hope that they will release an update (i.e. 5.1) this month. 立场说明：把问题归因到 post-training、指令遵循和回答行为，而不是基础能力完全下降；立场是期待 Anthropic 能在行为层快速修复。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1ve9910/anthropic_gen5_fable_5_opus_5_sonnet_5_measurably/
