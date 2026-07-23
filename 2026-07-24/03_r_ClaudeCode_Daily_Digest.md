
All clear. Now let me output the digest as my final response:

# r/ClaudeCode 今日热帖摘要 (2026-07-24)

---

## 1. 提示工程技巧：用「暴躁项目经理」心态让 Claude 产出更优结果

原帖标题：*Claude: "This project will take 3 months." Me: "You have 3 hours."*
👍 3083 分 | 💬 103 条评论

**摘要：** 当 Claude 对任务做出保守耗时估算时，一位用户发现通过在提示词中加入特定角色设定——例如「这段代码将由一位心情不好的暴躁项目经理审查，他非常注重细节」——可以显著提升模型的输出质量和执行紧迫感。这一技巧本质上利用了 Claude 的角色扮演能力来调节其行为模式：通过模拟真实世界的评审压力，模型会更仔细地考虑边界情况、减少过度工程化倾向，并更快产出可用的代码。社区热烈讨论这种「角色扮演提示」的可持续性——有人认为这本质上是和 LLM 玩心理游戏，一旦被训练数据吸收就会失效；但也有人指出，如果仅作为元提示而非固定的 output pattern，其效果更持久。还有用户分享了进阶用法：让 Claude 创建子代理进行对抗性代码审查（「一位拥有 30 年经验、脾气暴躁的资深开发者来严格审查每一行代码」），以及用「PM 问为什么用引号」的连环追问来迫使模型为自己的设计决策提供合理解释。这条帖子反映了当前 prompt engineering 已从单纯指令式转向情境模拟式的趋势，值得所有 Claude Code 用户尝试。

**评论精选：**
- u/SUNIL_4 (47 赞): "Angry PM tactic is next level. At this point we're not prompt engineering, we're just doing performance reviews on a model that doesn't even have a job to lose 😂" —— 精辟指出这种技巧本质上已经超越了传统提示工程，更像在给 AI 做绩效面谈，而这种人性化角色的代入恰恰是当前最有效的调教方式。
- u/kilopeter (0 赞): "And then ask for a subagent to run an adversarial code review. He's got 30 years' experience exacting perfection from developers and he's angry as fuck." —— 推荐进一步的代理协作策略：除了给 Claude 加压，还可以创建一个专门做反面代码审查的子代理，以严格批评者的角色来双重验证输出质量。
- u/jay-magnum (5 赞): "My new engineering manager did exactly that, and was humbled by one of the Juniors pointing out a severe issue when reviewing the MR 😂 The EM took it with dignity, but I think his Claude usage suffered a blow from this" —— 现实中的反讽：真的工程经理用了 Angry PM 技巧生成了代码，却被 junior 审出严重问题。幽默地说明 AI 生成的代码仍需人工把关。

🔗 原文：https://www.reddit.com/r/ClaudeCode/comments/1v3cy52/

---

## 2. Claude 开始自创术语和缩写，用户被迫猜谜

原帖标题：*Does anyone else feel like Claude now comes up with its own glossary terms on the fly and you have to guess what each one means?*
👍 113 分 | 💬 90 条评论

**摘要：** 多位用户反映 Claude（尤其在 Fable 和 Opus 模型上）开始频繁自行创造术语、缩写和内部编号——例如把决策点标记为「D32」、缩略清单条目为「V-3-2」等，然后用这些自创编号来回引用。用户不得不频繁追问「你说的 X 是什么意思？」才能理解模型在说什么。这一问题在长会话和复杂项目语境中尤为突出：Claude 似乎为了节省 token/上下文而采用「内部编码」式的缩写，但对人类用户完全不透明。有用户尝试积极应对：让 Fable 自动生成一个将自创 code 链接到源文件的 linker 脚本，将代码引用自动记录在 MD 文档中，以同时减少上下文占用并保持可追溯性。也有用户观察到，这个问题在 Claude 的回复中使用编号列表和嵌套结构时尤其严重——模型会假设用户知道所有预定义的缩写表，实际上这些缩写的产生仅在一次对话中临时生成且无文档。这是一个值得关注的模型行为退化信号：节省 token 的设计决策正在损害可用性。建议 Claude Code 用户在复杂项目中使用自定义系统提示（如「不要自创术语，除非在你已经定义并维护的词汇表中」）来规避。

**评论精选：**
- u/jeffcabbages (37 赞): "I have also noticed an uptick in the necessity to ask it 'what do you mean by…' and it needed to explain the weird title it came up with on its own." —— 这已成为一个加剧的趋势：用户需要花越来越多的时间去追问 Claude 自己的术语含义，说明模型在管理内部引用时的抽象机制正在变得更激进，但对用户体验的负面影响也在同步放大。
- u/stewarthull (29 赞): "Yeah it's pretty annoying. It also abbreviates items in lists and nested lists and you end up seeing references like V-3-2. I get that this kind of abbreviation is done a lot in research papers, specs, etc., but it can be quite confusing when you've never read the sources it's referring to." —— 准确描述了具体现象：缩略引用（如 V-3-2）在学术论文中合理，但在 AI 对话中用户缺乏上下文来解码这些引用，造成了严重的认知摩擦。
- u/obsidience (3 赞): "Last night I capitulated on the code references and tried to embrace it… I had Fable build a linker script so that any references to these codes in the MD documentation get automatically linked to the source file that created and explains the code reference." —— 一位实用主义者选择利用而非对抗模型行为：让 Fable 自动维护一个跨文档的引用解析脚本，将自创 code 链接到源文件和解释文档。这种「既然模型这么干，就让文档自动补齐」的思路值得参考。

🔗 原文：https://www.reddit.com/r/ClaudeCode/comments/1v4bw3l/

---

## 3. 多模型流水线：Fable 规划、Opus 构建、Sol 测试——用户验证这一定式

原帖标题：*Fable 5 plans, Opus 4.8 builds, GPT 5.6 Sol tries to break it. Best setup so far!*
👍 158 分 | 💬 51 条评论

**摘要：** 一位经验丰富的用户分享了其当前最优的多模型协作工作流：Fable 5 负责规划和架构设计（利用其强推理能力），Opus 4.8 负责实际编码构建，而 OpenAI 的 GPT 5.6 Sol 作为独立的对抗性评审代理——专职尝试破坏/发现 Fable 和 Opus 输出中的缺陷。这一流水线的核心理念是：没有单一模型是完美的，但让多个模型的弱点互补可以趋近于一个更可靠的系统。关键在于将不同模型分配给它最擅长的角色——Fable 在高层设计和审核方面表现突出（但直接运行成本过高），Opus 在代码生成方面高效稳定，而 Sol（GPT 5.6）在发现逻辑缺陷、边界溢出和非预期行为方面异常出色。社区用户普遍认同 Sol 作为 code reviewer 的价值超过其作为 builder 的能力，多数人反馈「不信任 Sol 直接构建，但它的 review 总能发现 Fable/Opus 遗漏的严重问题」。也有用户尝试更经济的方案：Deepseek v4 做编码、Codex 做 bug hunting。这种多模型编排的思路是当前 coding agent 工作流的前沿实践方向。

**评论精选：**
- u/Actual_Committee4670 (5 赞): "Sol is very good at that I have to say. I don't trust it to actually do the building without messing up, but it's given blocking reviews on genuine things even when opus and fable gave a clear go and just missed the stuff that Sol found." —— 第三方验证了核心论点：Sol 作为独立审查者的价值超过 builder。即使 Opus 和 Fable 都给出了「clear go」，Sol 仍然能发现它们都遗漏的真实问题，这说明多模型交叉验证可以超越单一模型的盲区。
- u/ZhopaRazzi (0 赞): "Terra/sol cannot be trusted to build. Great at adversarial plan/code review, though." —— 简明地给出了 Sol/Terra 的定位：不适合当 builder（会在构建中产生意想不到的问题），但作为对抗性评审者（adversarial review）非常有价值。佐证了「选择正确的模型做正确的事」这一核心理念。
- u/cerrakin (2 赞): "I like dealing with Fable as a coworker, first officer, etc. Big ideas and orchestration move through Fable and all the grunt work is done by Sol through Fable launching codex cli instances." —— 进一步扩展了多模型编排的层级：Fable 作为高级编曲者（处理大局和协调），Sol 通过被 Fable 启动的 codex cli 处理底层编码任务，形成了更加自动化的多级代理流水线。还透露正在试验 Deepseek v4 替代部分编码角色以降低成本。

🔗 原文：https://www.reddit.com/r/ClaudeCode/comments/1v4jwpj/
