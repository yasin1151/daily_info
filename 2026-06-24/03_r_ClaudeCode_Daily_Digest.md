
**r/ClaudeCode 推送**
- `I built a fairly detailed medieval peasant sim by directing Claude Code agents in parallel.`：作者展示了一个用 Claude Code 多 agent 并行搭建的中世纪农民模拟项目，核心亮点不是游戏题材本身，而是“如何让代理团队自测、自修复、再由视觉模型检查渲染结果”。这篇值得关注，因为它把“coding agent + headless testing + 视觉验收”串成了完整工作流，很接近可复用的 agent 开发范式。
  - 代表评论：u/Interesting-Bee-113（隐藏/RSS未提供）认为自己也在做战斗模拟，并分享了 AI 逻辑与动画/兵种编队之间的难点，说明这种并行 agent 流程确实能支撑复杂模拟。
  - 代表评论：u/pandulfi（隐藏/RSS未提供）追问“盾墙去哪了”，把讨论拉回到具体系统设计，体现出社区对可玩性/历史真实性的关注。
  - 代表评论：u/Interesting-Bee-113（隐藏/RSS未提供）补充说自己惊讶于模型能较轻松写出 AI 逻辑，但喷嚏一整天都在修 sprites/animations，说明 agent 擅长逻辑、视觉资产仍是瓶颈。
  - 原帖：https://www.reddit.com/r/ClaudeCode/comments/1udoz3w/i_built_a_fairly_detailed_medieval_peasant_sim_by/

- `Coding is largely solved.`：这条更像“AI coding 已接近完成”的挑衅式观点，引发了大量反驳，讨论焦点迅速转向运营、稳定性、token 泄漏、Claude 自家产品质量等现实问题。值得看，因为它把“代码能不能写”与“软件能不能长期稳定运行”切分得很清楚，也反映了社区对 Claude Code 的期望已经从写代码扩展到工程全链路。
  - 代表评论：u/Phaedo（隐藏/RSS未提供）直接指出 ops 远没被解决，并提到 Claude Code/Desktop 本身也有不少 bug，反驳“coding solved”的乐观论。
  - 代表评论：u/NullzInc（隐藏/RSS未提供）列出超长函数、超大文件和 token leak，强调“100% solved”明显言过其实。
  - 代表评论：u/KyleDrogo（隐藏/RSS未提供）补刀说 Claude iOS/desktop 是自己日常最坏的软件之一，进一步把争论从“编码能力”推向“产品成熟度”。
  - 原帖：https://www.reddit.com/r/ClaudeCode/comments/1udr97p/coding_is_largely_solved/

- `When Claude is down.. post your setup 🤣`：这是典型的社区轻松帖，但信息密度不低，评论区意外暴露了很多人已经把 Claude Code 当成主力开发环境，并围绕 Raycast、Stream Deck、worktrees、CMUX、并行 session 形成了一套相对成熟的操作体系。值得关注，因为它很像“Claude Code 实战配置分享帖”，能直接反映真实工作流。
  - 代表评论：u/Sketaverse（隐藏/RSS未提供）提到自己用 Raycast 连接 Figma、CMUX、Claude MD、GitHub、Linear 等入口，说明他把快捷启动和 agent 流程做成了统一控制面板。
  - 代表评论：u/PhoenixUNI（隐藏/RSS未提供）追问多 session 的用途，得到的回答是“单人做全栈并发，agent 已经像多个操作员”，这很符合多 agent 开发的现实。
  - 代表评论：u/Sketaverse（隐藏/RSS未提供）建议“先进 terminal，学 worktrees，再进化到 cmux”，这是很直接的实践路线。
  - 原帖：https://www.reddit.com/r/ClaudeCode/comments/1udla1a/when_claude_is_down_post_your_setup/

已完成 `r/ClaudeCode` 已读标记。
