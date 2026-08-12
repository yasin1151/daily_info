
# r/ClaudeCode 今日精选

## 1. My Claude Code workflow after months of daily use

**摘要：** 作者把 Claude Code 当成可并行调度的开发系统，而不是单个聊天窗口：Git 和 worktree 负责隔离变更，单任务单会话避免长上下文退化，主会话负责编排 worker 会话，CLAUDE.md/Rules.md 负责项目规则，完成后必须跑端到端 smoke check。值得关注的是，评论区把这套经验进一步落到文档结构、计划文件、hooks、skills 和会话收尾流程上，核心共识是：提示词只是建议，真正稳定的 agent 工作流需要可追踪的状态、可执行的检查、可复用的项目知识和明确的验证闭环。

**高赞评论：**
- u/truncat（3赞）：把“让 Claude 记住”改成“让 Claude 写到明确文件路径”，并建议用 GitHub Issue、docs/decisions.md、docs/reference.md、HANDOFF.md 分别承载待办、决策、技术参考和交接上下文。立场说明：这条评论的价值在于把记忆问题转成工程化信息架构，能减少 agent 声称已记录但实际丢失上下文的风险。
- u/jd_bruce（3赞）：建议复杂任务开始前先让 agent 写详细 plan 文件，项目层面维护 PLAN.md 和 TASKS.md/TODO.md；接手已有项目时再生成 SURVEY.md，记录文件结构和技术栈。立场说明：这是对“先规划再执行”的具体落地，适合降低 agent 对陌生代码库的误读。
- u/Turbo-Sloth481（2赞）：补充可以先基于计划创建 5-15 个 domain skills，并在每个里程碑结束后做 retrospective，把技能文件和记忆更新掉；还建议给第三方 CLI 做认证并把文档转成 skill。立场说明：这条把一次性提示升级成可积累的操作手册，但也需要控制 skill 数量，避免噪音扩散。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vmey7d/

## 2. How do you actually manage multiple parallel Claude Code sessions without losing your mind?

**摘要：** 这帖讨论的不是“能不能同时开很多 Claude Code”，而是多 session 真正进入日常后如何避免状态失控。楼主的场景偏 DevOps/sysadmin，经常从不同目录启动 Claude、SSH 到远端机器、处理不属于某个 repo 的任务，因此 worktree 中心化工具并不完全适配。评论区形成的实用结论是：并行 agent 要按团队管理，而不是按窗口管理；需要 ticket、状态面板、恢复路径、工作目录约定、质量门禁和更少的交互式上下文切换。对 infra 类用户尤其值得关注，因为它提醒我们不要机械套用 repo/worktree 工作流。

**高赞评论：**
- u/satoramoto（11赞）：认为每个 session 都应像 senior developer 一样管理，人类扮演 EM/PM；任务要拆到足够小，给清楚背景、验收标准和技术边界，并让 agent 在不确定时先提问。立场说明：这是多 agent 编排的基本原则，核心不是更多窗口，而是更明确的委派契约。
- u/freeasinbird（1赞）：分享自己同时跑 2-6 个 Claude Code/Codex session，工作都定义在 GitHub issues 中，tracker issue 记录依赖顺序和可并行部分，并把 Fable 用于规划、Opus 或 Sol 用于实现。立场说明：这条把“多开”转成 issue-driven 调度，能让模型选择、任务分解和后续接力都有可查依据。
- u/actvt_io（2赞）：指出 Claude 会按启动目录保存 transcript，`claude --resume` 可恢复；对非 repo ops 任务，应固定一个启动目录，否则恢复列表会散落在多个目录里。立场说明：这是非常具体的 Claude Code 操作细节，能直接解决重启或窗口关闭后找不到会话的问题。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vm8u30/

## 3. Did Anthropic Decreased the Usage Limit?

**摘要：** 多名用户反馈 Claude Code/Claude 近期用量消耗明显变快，尤其是 20x、Max、Fable/Opus 工作流中出现“同样做法更快触顶”的体感；部分人把问题归因于上下文窗口、compact、缓存或模型路由变化，也有人报告公司计划突然提前耗尽。值得关注的是，这不是单纯抱怨额度，而是会影响 agent 架构：长会话、自动 compact、多 agent fan-out、Fable 编排和未受控的技能/文档读取都可能放大成本。对重度用户来说，应该把 token/usage 当作系统约束，主动记录 /context、拆新会话、限制 fan-out，并把异常用量和具体 workflow 一起复盘。

**高赞评论：**
- u/rifi007（61赞）：表示 20x plan 以前一天最多用 10%，这次从晚上 9 点重置到次日下午 5 点已经消耗 25%；后来即使用新 chat 分成 backend、frontend、api 三个任务，燃烧速度仍和上周不同。立场说明：这条提供了前后对比和新会话复测，比单纯体感更有参考价值。
- u/crugerdk（18赞）：建议如果要 compact，最好在夜里上下文仍在 cache 里时做；早上再 compact 可能要重新加载全部内容来生成摘要。立场说明：这是一个具体的成本优化提醒，说明 compact 本身并不免费，甚至可能触发大量上下文重读。
- u/thePsychonautDad（3赞）：称个人和公司订阅都看到相同现象，公司计划在 8 月 11 日就耗尽；同时 Claude 开始更频繁忽略 CLAUDE.md 中“不要提交 main”等规则。立场说明：这条把用量异常和指令遵循下降联系起来，提示需要同时检查模型行为、上下文长度和组织级配额监控。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vm9135/
