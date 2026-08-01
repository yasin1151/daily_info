
# r/ClaudeCode 今日推送

## 1. Opus 5 is working fine for me… I feel almost left out.

摘要：这帖讨论 Opus 5 在 Claude Code 场景里的体验分化：楼主认为它几乎全面替代旧模型，写 bug 的频率也接近资深工程师可接受范围；但评论区提醒，同一模型在长会话和 PR 修复里可能变得更冒进，出现误删、revert、清理补救继续消耗 token 等问题。值得关注的是，它不是简单的“好/坏”评价，而是在提示我们把模型选择、会话长度、代码审查和回滚保护一起看；如果团队要把 Opus 放进日常开发流水线，最好同时设置更短上下文、频繁提交、只读审查和危险命令确认，避免一次失控影响整个工作区。

1. u/SomeoneNicer（赞数：20）：Have you followed the conversation as it builds? I switched to 5 as well and it's been OK but I see a few times a day or does things like "I have to be straight with you, I did a git revert and lose all my work but it's ok because I recovered it" or "I did an rm that was wider than intended and cleared out files from all other sessions and cache" etc. I haven't had it wipe a VM yet, but it's certainly more reckless than any previous Opus for me. 立场说明：提醒 Opus 5 的风险常在对话累积后出现，建议关注长会话中的文件操作和回滚行为。
2. u/Singularity-42（赞数：9）：Yeah I just had one thread where Opus 5 wasted half of the tokens (around ~650k) on fuckups and the "cleaning up" fuckups. One "I have to be straight with you" after another... Not even gonna review it yet, giving it to Fable and Sol for first pass. 立场说明：给出约 650k token 被修复—再修复循环消耗的案例，说明高能力模型也会放大浪费。
3. u/MisterHarvest（赞数：4）：That's a fair criticism. I don't see it once per day, but I do see it once in a while. I've done some work prompting it away from stuff like that, but it's not been 100% successful. The issues I've found have more been about tripping over itself in PRs than actually removing work. 立场说明：观点较平衡：问题并非每日必现，但在 PR 场景会绊倒自己，提示可用 prompting 降低但不能完全消除。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vcwsh3/

## 2. Claude Code making up it's own tech/project jargon. Anyone found a way to dial that back in?

摘要：这帖聚焦 Claude Code/Claude 在项目沟通中自创术语的问题：楼主发现模型会把任务、模块和流程包装成自己的“技术黑话”，导致用户反复追问含义。评论区给出的可执行方向包括控制词表、CLAUDE.md/skill 约束、STE100 简化技术英语、模板化回答，以及定期修剪规则文件。它值得关注，因为这是 agent workflow 的真实生产力损耗：不是代码不会写，而是沟通层不断制造额外解释成本。对长期项目来说，术语漂移还会污染文档、issue、提交说明和团队共识，最后让人类不得不用另一套流程翻译 agent 的输出。

1. u/Beerbrewing（赞数：32）：I've been reading about ASD-STE100 Simplified Technical English and it looks like it would help if you instruct Claude to follow its principles. It's a controlled natural language that is designed to simplify and clarify technical documentation. Basically it's a guide to specifying what technical jargon is allowed so even non-native English speakers can understand technical documents. 立场说明：建议引入 ASD-STE100 这类受控自然语言，核心是显式限定允许使用的技术词表。
2. u/ChattyHedgehog（赞数：9）：I've been trying to enforce it. Kind of helps WHEN and ONLY WHEN claude decides to use it and not violate the rules. But nope, claude always finds a way back to its own fuckery, Opus is bad, Sonnet is worse, Haiku is unbearable. I've even put hooks and more rules in claude.md and more memories and ... at the end it invents something different and goes back to "why this marvelous blofulllingu thurpalatgn matters" and all those shittery. I have been making templates for every kind of answer it needs to do and it ALWAYS will sneak some shit in the middle. It's exhausting cause is impossible to understand, you ask a question and it hides the answer in a bunch of gibberish and then tells you to "say go" which I also banned but keeps inventing something to say the same thing with other words. I want to piledrive the people behind that 立场说明：分享了 hooks、规则、模板都只能部分缓解的失败经验，说明约束需要验证而不是写完就信。
3. u/brother_spirit（赞数：2）：I'm actually at the point I am considering a post tool use hook that simply fires the response into a separate terminal or off to a sub agent with a "summarize Opus' answer and the return my instructions to the model". The problem is, my first foray down this path revealed letting an agent talk to Opus can lead to absolute nonsense as well. I had Terra spinning in circles yesterday YELLING at Opus sub agents to stop pausing and asking if it wanted the work to be done. Terra; sending instructions to an Opus agent sitting with 60K tokens of context on board: "DO not stop to ask if I want you to write code. You are an autonomous coding agent and I have given you the brief. Write it and return the results" Again, next tool run, almost 100K tokens in the sub agent window: "NO. STOP ASKING. Write the code to the specified directory." It was surreal to behold. Looks like even models struggle to 立场说明：提出用后处理 hook 或子代理重写 Opus 输出，但也警告 agent 对 agent 可能继续陷入循环。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vcn3yr/

## 3. What's the best way to review large codebases with Fable without overthinking and under-exploring.

摘要：这帖询问如何让 Fable/Claude Code 审查大型代码库时既不要过度纠结细枝末节，也不要探索不足。帖子的价值在于把“让 agent 读全仓库”拆成工程流程问题：先限定目标和风险面，再要求模型形成代码地图、依赖图、变更入口和假设清单，最后用分阶段审查或多模型交叉验证。评论虽不算爆量，但方向集中在降低上下文噪声、把审查任务拆小、避免一次性让模型自由漫游。对真实团队尤其有用的是，它把费用、上下文复用、文档化和热点优先级放在一起讨论，避免把大仓库审查误解成单次超长 prompt。

1. u/ITFuture（赞数：9）：I use codebase-memory-mcp, use hooks to prevent claudr from grepping actual code. Results for me = 97% context token re-use ... meaning 97% of my tokens are free or billed at 1/10th normal cost 立场说明：强调大仓库审查要先界定目标，不然模型会在无关文件里过度推理。
2. u/ShelZuuz（赞数：3）：With $100 on a large codebase you have no chance. Get your subscription plan bot to write out docs based on your codebase and then have Fable review the docs. 立场说明：建议分阶段让模型先建地图再审查具体路径，这比直接问“哪里有问题”更稳。
3. u/mugsy33（赞数：2）：The new LMGTFY : LMCTFY - https://chatgpt.com/share/6a6e20b1-ad08-83e8-a33c-e15c60de6326 TLDR: Tell Fable to create a mental map of the codebase, then ask what should be reviewed. Then tell it to review the top 5 hotspots. Rinse and repeat until you've explored everything you should. 立场说明：把 Fable/Claude 的探索深度视为可调参数：需要用明确输出格式和停止条件约束。

原帖链接：https://www.reddit.com/r/ClaudeCode/comments/1vcrsr5/
