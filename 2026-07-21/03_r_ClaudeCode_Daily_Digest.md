
## Usage limits are getting out of control.

摘要：背景：Claude Code 用户继续围绕用量限制和订阅价值争论，帖子把问题集中到高强度日常开发时 5 小时窗口是否足够，以及不同模型和订阅方案到底能支撑多少真实工作。核心：评论区给出的不是单纯抱怨，而是具体比较了 Opus、Kimi、订阅窗口、API 价格和项目结构化上下文对消耗的影响，还有人分享用 Markdown map、知识文件和更小上下文延长会话的方法。值得关注：这类讨论直接影响团队是否能把 Claude Code 放进稳定开发流程，因为成本、限额和上下文组织方式会决定它是临时加速器还是可持续生产工具。

高赞评论：
- u/GradjaninX（1 赞）：I am able to stretch my 5h limit with full Opus 4.8 High Effort on $20. But I am heavily relying on MD map structure to the point that I have something like this /myProject - agent - CLAUDE.md - KNOWLEDGE.md - rest of the stuff includi... 立场说明：这条评论把 agent 的边界讲得更清楚，适合用来判断实现里需要 harness、任务输入输出和委派机制，而不是只依赖模型本身。
- u/luisoncpp（0 赞）：The Kimi claim is not true, probably if you measure API price is indeed cheaper than Fable, but subscription-wise the story is very different. Kimi K3 with a single prompt it exhausted 100% of a 5h window of my OpenCode Go subscription... 立场说明：这条评论把问题落到额度、价格和会话窗口上，提醒读者评估 Claude Code 时要同时看能力与长期运行成本。
- u/Ok_Principle_9459（1 赞）：If The OpenAI model is just as good then just switch to it dawg Idk wtf y'all are doing but I use Fable to do everything (senior SWE work). Planning, writing code, writing slide decks, data analysis, you name it. And it does a fucking... 立场说明：这条评论提供了真实工作流视角，能帮助判断 Claude Code 在规划、编码、校验和交付中的实际位置。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1v1t6tx/usage_limits_are_getting_out_of_control/

## Fable 5 on usage credits, eh?

摘要：背景：这帖继续追问 Fable 5 和 Claude Code 的 usage credits 体验，重点是用户在实际跑 subagents、长任务和高强度会话时是否能预期剩余额度。核心：评论提到有人需要用其他工具校验 Opus subagents 的产出，也有人认为定价与限额策略仍在快速试错，导致用户很难提前规划一天的开发节奏。值得关注：它反映了 agent 工作流的关键风险，模型能力之外，额度透明度、任务可恢复性和可计划性会直接影响交付节奏，也会影响开发者是否愿意把它用于客户项目。

高赞评论：
- u/dorkquemada（1 赞）：In this case it was basically babysitting Opus subagents building the work. Fortunately I have the Codex CC plugin validate the work, which has been more useful than Fable right now 立场说明：这条评论把 agent 的边界讲得更清楚，适合用来判断实现里需要 harness、任务输入输出和委派机制，而不是只依赖模型本身。
- u/sob727（1 赞）：They're making it up as they go along. In their defense, things are evolving so fast that it must be difficult to come up with the right pricing and monetization strategy. For the customer the experience is horrible. Can't plan ahead.... 立场说明：这条评论补充了使用者的一线观察，有助于把帖子观点和真实限制区分开来。
- u/paodal（4 赞）：I'm on pro plan and i still have access to Fable 5 from web for some reasons. what a bunch of amateurs 立场说明：这条评论补充了使用者的一线观察，有助于把帖子观点和真实限制区分开来。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1v1e5xv/fable_5_on_usage_credits_eh/

## Existential question: how on earth do you create an agent?

摘要：背景：作者提出一个基础但重要的问题：到底怎样才算创建了一个 agent，而不是只是在调用模型或写几条提示词。核心：评论区把 agent 拆成模型加 harness，并讨论 Claude Code、MCP server、任务委派、函数调用式子代理、输入输出约定、状态管理和任务结束返回等实现方式，还指出 agent 的自主程度取决于它能调用多少工具和外部系统。值得关注：这能帮助开发者区分概念包装和真实工程结构，尤其在设计多 agent loop、权限边界、工具调用、失败恢复和可验证结果时更有参考价值。

高赞评论：
- u/Zealousideal_Cup6458（1 赞）：I've been working all summer on a MCP server that helps you build agents. Its still work in progress but feel free to check it out. Orchestratemcp.dev Its open source completely free. Just hook it up to Claude or chat GPT. No sign in o... 立场说明：这条评论把 agent 的边界讲得更清楚，适合用来判断实现里需要 harness、任务输入输出和委派机制，而不是只依赖模型本身。
- u/Whole_Ticket_3715（16 赞）：Oh yes! So I do this for a living. The easiest way to say it, is that an 'agent' is just a model + a harness. Claude code is a harness, and Claude Opus is a model. When Opus runs Claude Code, it is an agent. Based on how many things it... 立场说明：这条评论把 agent 的边界讲得更清楚，适合用来判断实现里需要 harness、任务输入输出和委派机制，而不是只依赖模型本身。
- u/Dienes16（15 赞）：Claude can delegate tasks to other agents. In principle think of them as function calls in a software. Claude launches an agent, that agent is given an input (the task it should do) and it will eventually end itself and return an outpu... 立场说明：这条评论把 agent 的边界讲得更清楚，适合用来判断实现里需要 harness、任务输入输出和委派机制，而不是只依赖模型本身。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1v1u0wr/existential_question_how_on_earth_do_you_create/
