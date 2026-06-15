
r/ClaudeCode 新帖扫描完成：blogwatcher 发现 21 条新帖，已筛选 Claude Code / agent workflow / token usage / CLI / 大项目上下文相关内容，并已标记已读。

---

**1. 会话一开始 compact，结果第一条 prompt 吃掉大量 token**

📝 摘要：作者在前一天长会话后没有新开 session，而是在新一天开始时先 compact conversation，结果发现第一条 prompt 直接消耗约 50% token，后续每条也维持在 5% 左右。讨论核心不是“compact 坏了”，而是长上下文会在继续会话时重新计入成本，compact 更像长会话末期的急救手段，不适合当作每日 fresh start。值得关注的是，社区给出的主流实践是把长期上下文迁移到 `CLAUDE.md`、docs、handoff prompt 或 handoff skill，而不是依赖模型自动摘要。

💬 高赞评论：
- u/Biomech8 +58：认为 compact 是长会话最后手段；新任务/新一天应直接开新 session，避免缓存外长上下文反复烧 token。
- u/Biomech8 +27：建议把重要信息沉淀到 `claude.md` 和文档里，需要时再让 Claude 读取。
- u/josephbrostar +24：主张创建 handoff skill，用显式交接机制替代自动 compact。

🔗 原帖：https://www.reddit.com/r/ClaudeCode/comments/1u5gj4r/i_compacted_the_conversation_at_the_start_of_the/

---

**2. `/clear` 后 CLI 还记得上下文：远程聊天环境疑似没有真正执行命令**

📝 摘要：作者通过远程 app 控制 Claude Code，执行 `/clear` 后发现 CLI 似乎仍然知道之前任务，于是怀疑是否有新的上下文记忆机制。评论区更倾向于判断这是远程控制链路的 bug：`/clear` 可能被包装成普通用户消息，前面还被插入 `<system reminder>`，导致 slash command 没有被 CLI 识别。这个帖子值得关注，因为它暴露了 Claude Code 在远程 app、CLI 命令层和上下文清理之间的边界问题：用户以为清空了，实际可能只是模型“假装理解了清空”。

💬 高赞评论：
- u/Zhaelthas +6：指出远程 chat 会在消息前插入 `<system reminder>`，阻止 `/clear` 真正触发。
- u/Ok_Champion_5329 +3：认为 `/clear` 被当成普通消息，LLM 只是幻觉式地回应“已清空”，实际什么都没发生。
- u/ramit_m +3：提醒检查是否接入了 memory service，或有记录 todo/context 的 Markdown 文件。

🔗 原帖：https://www.reddit.com/r/ClaudeCode/comments/1u5t9ce/cli_remembers_context_after_clear_is_this_new/

---

**3. Claude Code 空闲时也烧 credits：可能是旧会话、后台 subagent 或账号 token 问题**

📝 摘要：作者说自己只是把 Claude Code CLI 留在 Windows terminal，没有主动输入任务，但用量窗口一开始就显示已消耗 40%，随后状态栏快速到 85% / 104%。评论区没有给出单一结论，但集中在三个排查方向：账号 OAuth token 是否被其他地方使用、是否有前一轮 Claude 启动的 subagent 在后台继续跑、是否延续旧 session 导致长上下文重新计费。这个帖子值得关注，因为“agent 没在做事但额度在掉”对个人 Pro/Max 用户很敏感，实际排查应从进程、后台任务、会话恢复和授权 token 入手。

💬 高赞评论：
- u/johnerp +4：建议清理 desktop app 设置里的 Claude Code OAuth token 和 setup token 后重新认证，以排除其他设备或泄露使用。
- u/Background_Ranger917 +2：分享自己遇到过旧 subagent 在后台继续执行，表面空闲但实际持续消耗。
- u/havnar- +1：提醒继续旧 session 会重新处理旧上下文，且不一定命中缓存。

🔗 原帖：https://www.reddit.com/r/ClaudeCode/comments/1u5x92j/claude_code_burn_credits_when_not_doing_anything/

---

**4. 6 月 15 日 Agent SDK credit 政策：`claude -p` / headless 自动化会被单独计费池管理**

📝 摘要：作者试图梳理 Anthropic 新的 Agent SDK credit：从 6 月 15 日起，`claude -p`、Claude Agent SDK、Claude Code GitHub Actions、第三方 SDK app 等非交互/程序化使用，不再走普通订阅额度，而是走单独月度美元 credit：Pro $20、Max 5x $100、Max 20x $200；耗尽后要么按 API 价继续扣费，要么停止。关注点在于真实 agent loop 的成本不透明：$200 到底能跑几小时？prompt caching 如何计价？GitHub Actions 是否也算？这对依赖 headless Claude 的自动化工作流影响很大。

💬 高赞评论：
- u/Maasu +16：表示这正是自己转向 Codex 的原因，因为很多 agentic loops 依赖 `Claude -p`。
- u/ApeInTheAether +9：认为 $200 可能只够几小时，也可能撑几天，完全取决于使用模式。
- u/nutterly +5：粗略估算这相当于每周使用上限的约十分之一；好处是额外额度，坏处是不能再把订阅额度大量用于官方前端外的自动化。

🔗 原帖：https://www.reddit.com/r/ClaudeCode/comments/1u5jq8x/did_anyone_actually_understand_anthropics_new/

---

**5. 大型/遗留项目中如何组织 Claude Code 上下文：层级文档比单一 CLAUDE.md 更受推崇**

📝 摘要：一位 staff engineer 已在中小项目中熟练使用 Claude Code，现在想迁移到大型 legacy / DDD 项目。他已有一个 `CLAUDE.md`，包含测试方式、架构、技术栈等，但还没有放业务域、PRD 和 domain 细节，于是询问应拆多份 MD、为每个 domain 建 skills，还是采用其他上下文压缩方式。评论区主流建议是构建层级化项目文档：顶层 `CLAUDE.md` / `AGENTS.md` 负责入口，`ARCHITECTURE.md`、`HANDOFF.md`、TODO、领域子文档负责按需展开。重点不是让 agent 一次性读完项目，而是让它能发现正确文档路径。

💬 高赞评论：
- u/SyntharVisk +7：建议配合 `ARCHITECTURE.md`、`HANDOFF.md` 和 TODO 文件，帮助不同 session 保持项目地图。
- u/ItsJustManager +2：介绍用项目管理应用让 agents 维护 ideas、bugs、docs、plans、tasks 等集合，并通过 MCP/前端消费。
- u/BeatTheMarket30 +2：强调大型项目需要层级 Markdown，顶层只放摘要和指向子文档的引用。

🔗 原帖：https://www.reddit.com/r/ClaudeCode/comments/1u5jbu0/using_claudecode_on_large_project/

---

**6. 用户分析 Fable 5 与 Opus 4.8 日志并试图把 Fable 风格“移植”到 Opus：评论区认为提示词治理也可能制造上下文负担**

📝 摘要：作者从本地 Claude Code JSONL 日志中分析 26 个 Fable 5 session 和 145 个 Opus 4.8 session，声称 Fable 并非总字数更少，而是默认更短、更结果导向；Opus 则更容易中等长度啰嗦。作者据此做了三层改造：行为 governor、回复格式约束、hook-based prompt 注入，试图让 Opus 更像 Fable。这个帖子有价值的部分是“从实际 agent 日志量化行为差异”的方法，但评论区强烈质疑其结论与实现：如果为了减少废话而加入大量治理 prompt，可能反而填满上下文、增加 token 成本。

💬 高赞评论：
- u/Yetiski +368：讽刺文中“我必须诚实面对的大 caveat”等措辞本身就像模型生成，质疑帖子质量。
- u/Famous__Draw +154：认为这种做法是在用不必要的文字沙拉填满上下文。
- u/Sarithis +110：用“Load-bearing comment”附和前面质疑，认为评论本身点出了关键问题。

🔗 原帖：https://www.reddit.com/r/ClaudeCode/comments/1u5dq2y/i_analyzed_26_sessions_9k_messages_of_fable_5_and/
