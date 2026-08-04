
### Opus 5 is a practically unusable model

**摘要：** 这条高热帖集中反映 Opus 5 在 Claude Code 长任务中的退化体验：楼主把完整执行计划交给模型后，发现它在十几万 token 内就开始忘指令、漏上下文、修一个问题又制造新回归，明显不如 Opus 4.6/4.8 的稳定窗口。值得关注的是，抱怨并不只是“模型变笨”，而是 agent loop 的工程风险：无限返工、token 快速消耗、代码库被悄悄改坏，都会把原本省时间的自动化变成持续看护。对于依赖 Claude Code 跑计划的人，这意味着必须缩小任务范围、加强验收与中断机制，并把每轮修改绑定到可回滚的检查点。

**高赞评论：**
- u/KrayeBaby（370赞）：指出模型经常解决一个问题却留下另一个缺口，像在不断制造后续 prompt。立场说明：这说明问题不只是输出质量，而是闭环任务的收敛性变差，长链路自动执行应增加回归测试和阶段性人工闸门。
- u/Deep-Palpitation8315（104赞）：说自己也遇到遗忘、无限循环和新 bug，并认为模型已经对部分代码库造成损害，幸好还能回滚。立场说明：这条评论强调版本控制、快照测试和小步提交的重要性，不能把大型修改一次性交给模型裸跑。
- u/dontTakeMeSerious6（25赞）：描述它会重新解决旧文档里已经完成但未标记的问题，甚至用另一套方式重做。立场说明：这提醒团队维护任务状态与文档同步，否则 agent 会把陈旧 TODO 当成真实需求并引入重复实现。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1veeuy5/

---
### Anthropic could reduce costs by 50% in Opus 5.1

**摘要：** 这帖从“Opus 5 写太多无用注释和长篇解释”切入，讨论的核心其实是 Claude Code 的单位任务成本：新模型即使有更大上下文，也可能因为输出更啰嗦、推理更绕而让 token 消耗翻倍。评论区分歧在于，有人认为 Opus 5 质量仍足以抵消成本，也有人把它与 Codex、GPT-5 系列和更便宜模型对比。对日常 coding agent 使用者来说，值得关注的是成本不只由标价决定，还由模型能否少废话、少返工、少 hallucination 决定。换言之，真正该量化的是“一个可合并 PR 的总 token 与人工修复时间”，而不是单次调用价格。

**高赞评论：**
- u/enjdusan（39赞）：用同一 prompt 对比 Opus 4.6 和 5.0，前者约 75k token 完成，后者超过 150k。立场说明：这是很直接的成本信号，评估模型时应记录同任务 token、修改轮数和最终 diff，而非只看上下文窗口大小。
- u/davyp82（3赞）：表示自己业务测试中 Opus 5 虽然贵，但需要人工修的错误比 frontier GPT 模型少 1.5 到 2 倍。立场说明：这提供了反面平衡，若错误修复成本高，贵模型仍可能划算，关键是按真实业务缺陷率核算。
- u/carvingmyelbows（4赞）：反驳 GPT-5 指令跟随更强的说法，称自己无法让其独立运行太久，会出现反向执行、擅自决策和反复停工。立场说明：模型切换不是简单比价格，agent 场景还要比较遵循规格、停止条件和自我纠错能力。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1vf6pd9/

---
### I just switched (again) to Claude but I simply can't understand Opus 5's output

**摘要：** 楼主从 Codex 切回 Claude 后，主要问题不是功能失败，而是 Opus 5 每次回答都输出一两页难懂、抽象、像内部术语的解释，迫使用户再花 token 要求“说人话”。这类问题对 Claude Code 工作流很关键：即使代码能跑，沟通噪音也会拖慢 review、增加上下文污染，并让用户错过真正重要的 diff 与风险。评论区给出的方向包括用 Fable 生成对比技能、把输出规则写入 CLAUDE.md 或 output style，而不是临时口头提醒。它提示我们：模型输出风格也需要工程化治理，否则会侵蚀 agent 带来的效率收益。

**高赞评论：**
- u/liojian（23赞）：让 Fable 5 用同一任务比较 Opus 5、Opus 4.8 和 Fable 5 输出，再据此生成改进 Opus 5 的 skill，效果像迷你 Fable。立场说明：这是可操作的校准方法，用模型间对照提炼行为约束，比凭印象写提示更稳。
- u/Budget-Marketing-260（5赞）：认为 Opus 5 解决问题能力强，但会使用自造术语和开发过程中的内部名字，需要明确让它面向真实读者写作。立场说明：这把问题定位为受众建模失败，适合通过 CLAUDE.md、技能或风格文件约束输出语域。
- u/Euphoric_Daikon_3582（8赞）：建议把输出规则写进 CLAUDE.md，例如默认 bullet、比较用表格、不要总结刚做过的事，因为用户能看 diff。立场说明：这条给出低成本治理办法，可直接减少冗长复盘和无效 token 消耗。

原帖：https://www.reddit.com/r/ClaudeCode/comments/1vf5f8b/
