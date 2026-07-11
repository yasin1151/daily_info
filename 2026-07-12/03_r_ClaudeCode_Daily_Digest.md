
# r/ClaudeCode 新帖精选（Claude Code / agent workflow）

## I’ve heard of people asking Fable to use Sonnet and Opus subagents to conserve usage, but has anyone successfully tried the inverse and asked Sonnet (or Opus) to use Fable or Opus subagents?

这帖讨论“反向子代理”编排：不是让 Fable 调 Sonnet/Opus 省额度，而是让 Sonnet、Opus 或 Codex 反过来调用 Fable、Codex、Grok 等外部 worker。背景是订阅额度收紧后，用户开始把不同模型拆成规划、实现、审查角色。值得关注的是，社区已把 Claude Code 用成多模型调度器；真正风险不在能否调用，而在命名、上下文传递和降级边界。如果提示词让模型误开昂贵子代理，省额度策略会立刻反噬。对重型项目来说，这已经接近一套小型研发流水线，也说明未来的 agent 能力会更多来自协作结构，而不是单一模型参数。

**高赞/高信号评论：**
1. u/Typical_Goat8035（7赞）：The pattern I settled on was Codex GPT-5.5 (at the time, haven't adapted it to 5.6 yet) supervises Fable via claude -p, with explicit directions for what to look for when there's an Opus downgrade, handing it a high level orche…
   - 立场：支持“强模型监督、低成本 worker 执行”的多模型编排，但强调要显式约束降级时的检查点，避免省 token 省掉质量。
2. u/Tartarus1040（3赞）：I'm doing something a little different. I'm using Fable as the Orchestrator, and I found a nifty little repo that lets Fable call Codex and Grok, and any other headless capable LLM as a "subagent" like it can call its own subag…
   - 立场：把 Fable 放在总控位，再通过 headless CLI 调 Codex/Grok/其他模型，说明社区正在把 Claude Code 当成调度层而不是单模型工具。
3. u/Typical_Goat8035（1赞）：Yeah another vote for this, I mentioned a similar workflow. Just organically starting with Fable and tell it that you’re trying to conserve usage and have {opencode, codex exec, etc} at its disposal, it does a really good job d…
   - 立场：提醒不要滥用“sub-agent”这个词，因为模型可能真的开 Fable 子代理烧额度；把外部模型称作 workers/typewriters 更稳。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1utlchk/

## Cache rewrites costed me 30% of my Fable consumption, here are the mistakes to avoid

这帖从 token 账单角度复盘“缓存重写”成本：长会话、间歇工作和模型/effort 切换，会让用户以为自己在读缓存，实际却频繁产生 cache creation。核心建议是不要迷信 55 分钟 keepalive，而要用 compact、handoff、项目 wiki 和小上下文重启控制前缀长度。它值得关注，因为 Claude Code 的真实成本越来越取决于会话工程，而不是单次 prompt；缓存、子代理和模型切换都要被当作系统设计问题。对团队使用者尤其重要，尤其是在多人并行、长任务暂停恢复、以及频繁切换模型的项目里，错误的缓存假设会直接变成预算黑洞。

**高赞/高信号评论：**
1. u/Sensitive-Cycle3775（8赞）：The 55-minute keepalive is clever, but I’d A/B it against a bounded cold restart before assuming preserving the cache is cheaper overall. A warm 400k-token session can keep paying cheap reads while also carrying stale context y…
   - 立场：建议用实验而不是直觉判断 keepalive 是否省钱：热缓存可能便宜，但也可能拖着大量过期上下文继续付费。
2. u/scodgey（5赞）：One nice way to handle this - run a precompact hook that spawns a cheap agent to digest your session log, saving out the relevant pieces you'd normally ask fable to save as a handoff. Then you can run hooks to inject that same …
   - 立场：给出可执行方案：compact 前用便宜 agent 总结 session log，再在新会话注入 handoff，绕开 Claude 自带压缩质量不稳定的问题。
3. u/coolreddy（1赞）：Run it in a different session as a bounded single shot task or ask fable to spawn sub agents and have sub agents single shot their task. Even here for short tasks letting fable spawn fable sub agents only comes out cheaper than…
   - 立场：指出同模型子代理可共享缓存、跨模型子代理要重新写缓存；这对“换模型省钱”的 workflow 是重要约束。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1utmegl/

## Anyone figured out reasonable and ethical ways to bill client hours when using Claude to support your work?

这帖讨论用 Claude Code 提升交付效率后，如何向客户合理计费。背景是自由职业和咨询场景仍常按小时报价，但 coding agent 会把执行时间压到原来的几分之一。高质量回复普遍倾向从工时转向里程碑、交付物、价值或分层工时，并承认 AI 生成后的审查、返工、责任承担仍是专业劳动。它值得关注，因为 agent 正在改变软件服务的定价单位，也会倒逼开发者重新解释自己的价值。透明沟通和结果责任会变得更重要。

**高赞/高信号评论：**
1. u/ChrisRogers67（4赞）：You bill by milestone and deliverables. Not hourly. Just because it takes you less time does that make the deliverable less valuable?  Forget “ai” for a second… if you were faster than me, should you charge less if we were buil…
   - 立场：主张按交付物/里程碑收费，不因 AI 提高效率就自动降价，把讨论从“工时”转向“结果价值”。
2. u/proxiblue（5赞）：I still bill by teh hours, but I had spoken to my clients about this, being open and honest. They all agreed to double my usual rate, as I now deliver in about 50% of the prior time. I gave the choice: I forgo AI usage, and bil…
   - 立场：提供透明沟通路径：向客户说明 AI 后速度变快、单价提高但总周期缩短，客户反而愿意接受。
3. u/Grand-Mix-9889（2赞）：I've been wrestling with this same thing since I run a similar setup (multiple concurrent Claude sessions across client + own projects). A few things that helped me:  Hourly is the wrong unit for this kind of work. You're not r…
   - 立场：把 AI 辅助工作拆成 active/review/结果三类计费，承认审查与返工仍消耗专业注意力，不是“11 分钟就完事”。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1utvrv1/

## unsnooze - wakes your AI coding sessions up when the usage limit resets

unsnooze 是一个围绕 Claude Code 限额重置的小工具：当会话因 usage limit 停住时，它解析重置时间并在窗口恢复后唤醒原会话，避免用户半夜手动按 continue。这个帖子值得关注，不是因为功能复杂，而是它击中了 agent loop 的实际痛点：长任务常被 rolling quota 打断，固定 cron 又会漂移。评论也提醒，自动恢复不等于省 token，仍要考虑上下文重发和服务端缓存；它更像可靠性补丁，不是成本优化银弹。若能扩展到更多 harness，会很实用，也可能成为本地 coding agent 编排里常见的守护进程组件。

**高赞/高信号评论：**
1. u/Gman325（3赞）：Awesome! Any plans to add support for other harnesses? E.g  Google Antigravity, Opencode, Openrouter etc?
   - 立场：直接追问是否支持 Antigravity、Opencode、OpenRouter 等 harness，说明这类恢复工具的价值在于跨 agent 生态。
2. u/saaransh_28（2赞）：Different problem. A routine runs on a schedule and starts a fresh cloud task. unsnooze resumes the exact session that hit the limit, with the same conversation and local working tree, at the actual reset time parsed from the b…
   - 立场：作者澄清 unsnooze 不是定时跑新任务，而是解析限额重置时间后恢复同一会话和工作树，解决 rolling window 漂移。
3. u/FudgeYouPaMa（1赞）：Not much you can do either way whether you manually say "continue" or use this itll send everything to the agent again. I don't recall the timeout for session cache though, but either way it'll be the same
   - 立场：提醒恢复会话仍会重新发送上下文，若服务端缓存过期，自动继续并不必然省 token，需要结合缓存策略看。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1utt1nz/

## Fable 5 Is Leaving and Weekly Limits will Be Cut by 50% after july 13, Is Claude Still Worth Renewing? Is It Even Usable After?

这帖围绕 Fable 5 离开订阅与 weekly limits 下调后的可用性焦虑展开，背景是很多 Claude Code 用户已把 Fable 当作复杂任务主力。高信号讨论没有停在抱怨，而是转向“用编排弥补单模型/额度变化”：让 Fable 保留总控和深度判断，把 Opus、Codex、GPT、opencode 或本地模型接成 worker、reviewer、researcher。它值得关注，因为用户正在从依赖旗舰模型转向可替换 harness，未来 workflow 的护城河可能是调度方式而不是某个模型名。对重度用户来说，这也是订阅不确定性下的风险对冲，能减少单点模型变动对项目节奏的冲击。

**高赞/高信号评论：**
1. u/outceptionator（107赞）：Honestly Fable as the orchestrator with opus sub agents doing all implementations and research/exploration and shelling out to gpt 5.6 for planning input and review will take it a long way at like 98% of the capability
   - 立场：高赞方案是把 Fable 留作 orchestrator，Opus 做实现/研究，GPT 做规划和 review，以组合维持能力上限。
2. u/rotellap（11赞）：Codex cli also ships a built in MCP that exposes a couple tools and also allows Claude to easier manage/resume sessions. I found it had a harder time with codex exec than with the MCP, and I couldn't see what was going on under…
   - 立场：补充 Codex CLI 的 MCP 比直接 codex exec 更便于 Claude 管理/恢复会话，也更透明，适合多模型协作。
3. u/Guinness（3赞）：I use Claude to utilize opencode and open models to save on tokens/cost. You can literally tell it to use whatever other model you want. GLM 5.2 in Opencode, or Codex, or Grok, or even your local LLM. All you need is to be on t…
   - 立场：强调 Claude Code 可以调用同机上的 opencode、Codex、Grok、本地模型等，核心前提是工具链可被 CLI 驱动。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1uttt60/
