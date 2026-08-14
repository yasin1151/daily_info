
# r/LLM 今日热帖

数据源说明：redlib 公共实例本轮 `/r/llm/hot/` 返回 503，已回退到 old.reddit 抓候选，并用 Reddit RSS 详情页补足评论。RSS 不提供评论赞数，统一标注为“赞数：隐藏”。

## 1. 326m model trained on local hardware in a week

**摘要：** 发帖者展示了一个约 3.26 亿参数的小模型：用两张 Tesla V100 在本地从零训练约 100 亿 token，再微调成偏数学推理的模型。它的价值不在“参数小却全面胜出”，而在证明窄任务中方法和数据设计可以压过规模：通过把列式计算、长除法、部分积乘法等步骤训练进模型，小模型在多位数算术上能明显优于只直接猜答案的大模型基线。值得关注的是，这类结果把讨论从“更大模型”拉回到“可解释训练目标、蒸馏质量、任务分解和评测协议”，对低成本专用 SLM、边缘部署和教育/工具型模型都有参考意义。

**高赞评论：**
- u/Strong_Essay1176（赞数：隐藏）：询问作者能否分享训练仓库。立场说明：社区最关心的是训练代码、数据处理和复现流程，而不是演示分数本身。
- u/nkthebass（赞数：隐藏）：作者回应正在更新 Hugging Face model card 和 loss curve，但训练数据是自制的，暂不公开，不过可以按需私下分享具体材料。立场说明：这提供了部分验证入口，也说明复现仍受限于数据不开源。
- u/Strong_Essay1176（赞数：隐藏）：补充自己正在试验 finetune liquid 模型做 autocomplete，希望看到其他代码和样例。立场说明：这把讨论落到实际开发场景，说明小模型训练的落点是自动补全、局部推理和可控专用助手。

原帖链接：https://www.reddit.com/r/LLM/comments/1vjbx1u/326m_model_trained_on_local_hardware_in_a_week/

## 2. Best LLM for professional writing

**摘要：** 这帖讨论“专业写作型 agent”应该选什么模型：发帖者需要事实性强、少 AI 腔、能遵守约束、还能兼顾工具调用和低延迟的模型。评论区的核心分歧很实用：写作质量、工具调用、约束执行不应全压在模型本身，很多能力要由 harness、风格指南、知识库、会话交接和外层校验来承担。值得关注的是，它把“选 Claude、Gemini 还是本地模型”的问题转成系统架构问题：模型决定上限，但稳定的专业文风、禁止项、资料引用和多步骤 agent 行为，往往依赖模型外的流程设计。

**高赞评论：**
- u/Unnamed-3891（赞数：隐藏）：指出没有单一最佳答案；擅长写作的模型不一定擅长工具调用，约束执行也不是纯模型特性，而应在外层系统实现。立场说明：这是最关键的工程判断，适合把模型选型拆成生成、调用、校验和策略执行。
- u/LaughterOnWater（赞数：隐藏）：推荐 Opus 4.7/4.8 做研究、非虚构、小说或歌词写作，但强调必须有 voicing guide、wiki、session handoff，并精简 Claude 自带 skills。立场说明：这给出的是一套完整工作流，而不是单纯模型名字。
- u/Healthy-Zebra-9856（赞数：隐藏）：列出若干本地 Vortex 系列写作模型，如 Phoenix-X-26B-A4B、G4-Moonlight-Dusk-26B-A4B、Chimera-X-26B-A4B 等，并区分纯叙事、连续性、轻量速度和 macOS MLX 适配。立场说明：这为偏本地部署的人提供了候选清单，但迁移到工程化专业文档时仍需重新评测事实性和约束遵守。

原帖链接：https://www.reddit.com/r/LLM/comments/1vkzry1/best_llm_for_professional_writing/

QA_OK
