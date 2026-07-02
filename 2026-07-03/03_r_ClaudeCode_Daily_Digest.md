
【r/ClaudeCode 今日值得关注】

1. Claude Code 新增“AFK 自动继续”行为：无人确认时会替用户做判断

摘要：有用户发现 Claude Code v2.1.198 起出现未写入 changelog 的 AFK 行为：当 AskUserQuestion 对话框 60 秒无人响应后，界面会倒计时 20 秒，并让模型基于“最佳判断”继续执行。帖子作者通过 strings 扫本地 binary 和版本二分复现，找到 CLAUDE_AFK_TIMEOUT_MS、CLAUDE_AFK_COUNTDOWN_MS 两个环境变量可调节；把 timeout 设到 2147483647 基本可禁用。值得关注的是，这确实能减少远程/并行会话卡住，但也改变了“人类显式批准后才继续”的安全边界，尤其影响多 agent loop、无人值守 coding session 和需要审批的代码修改流程。

高信号评论：
- u/Foolhearted（赞数：RSS未提供）：可以接受自动继续，但前提是只在分支内工作、只做本地 commit、不 push；结束时要列出每个决策点和对应 commit，方便回滚。立场：支持“可回滚的自治”，把风险控制转移到分支、提交和审计日志上。
- u/ask_me_about_cats（赞数：RSS未提供）：很喜欢这个改动，因为经常给了清晰指令后离开 20 分钟，回来发现 Claude 因一个不重要问题刚走就暂停。立场：强调实际 workflow 痛点，自动继续能显著提高长任务吞吐。
- u/5deags（赞数：RSS未提供）：自己正想发帖询问，因为 changelog 没写；感谢作者给出环境变量。其并行跑多个 session，通常无法每隔几分钟照看一次，这个行为当天一直影响他。立场：说明该变化已在重度多会话用户中造成可感知影响，且缺少发布说明是主要问题。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1ulhquy/claude_code_quietly_taught_itself_to_stop_waiting/
