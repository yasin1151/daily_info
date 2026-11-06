
**橘鸦AI早报 2026-11-06 摘要**

这一期的主要内容集中在 Google 和 OpenAI 的两款重要发布，此外还有多个“下一步就是开源”的模型，以及几件值得注意的安全问题与行业争议。

---

**1. Google 发布 Gemini Omni 1.2 Flash：视频时长提升到15秒，并降价三成**
原生视频生成和编辑的单次时长从 10 秒提升到 15 秒，并且可以按秒设置；用户还能通过多轮对话修改同一片段的背景、光线和画面比例。现在可以把角色图、产品或风格图、最长 3 秒的动作片段和音频提示组合起来引导生成，人物一致性、对白口型和多说话人镜头控制都有改善。720p 视频定价为每秒 0.07 美元，比 1.1 版便宜 30%，而且可以先使用低分辨率生成，再提升到 4K。目前正在陆续进入 Flow、Google Vids 和 Gemini App（Ultra 用户优先体验）。Google 自己承认，快速体育动作、快速脚本变化和复杂物理效果仍然不行。
https://blog.google/innovation-and-ai/technology/developers-tools/introducing-gemini-omni-1-2-flash/

**2. OpenAI 发布 GPT-6 Cyber，直接被评为“网络安全 Critical 级”**
上一代 GPT-5.6 Cyber 只被评为 High 级。新一代在 ExploitGym 基准上从 32.1% 提升到 48.5%；越界测试中，99.93% 的尝试都保持在研究者设定的任务范围内，加上部署提示后达到 100%。更关键的是实际战果：研究人员用它在 Firefox 中找出 81 个此前未知的漏洞，并被 Mozilla 评为高危漏洞；还为 948 个 Linux 内核漏洞开发出可用的利用方法。目前只向获批的 Daybreak Red 客户开放（通过 API 和 Codex）。这类模型在提升攻防能力的同时，也把“谁来管、谁能用”的问题推到了更前面。
https://openai.com/index/introducing-gpt-6-cyber

**3. Thinking Machines 的 Inkling 2 Small：得分跃升18分，下周开源全权重**
在 Artificial Analysis 智能指数上得到 31 分（前代只有 13 分），采用 MoE 架构，总参数 594B、激活参数 17B，支持图像输入和可变 effort。现在只有在 Tinker 平台才能使用，且是闭源形式，定价为输入每百万 token 0.3 美元、输出 1 美元。计划在外部安全测试和红队完成后，于下周以 Apache 2.0 协议发布完整权重。如果按计划兑现，这会是近期最值得关注的开源权重之一。
https://thinkingmachines.ai/news/inkling-2-small

**4. 百度开放 ERNIE-5.5-Flash-Base 预训练终点权重**
总参数 280B，每个 token 激活 14B，稀疏 MoE，在 33.5T tokens 上从零预训练，训练上下文 128K，微调和推理支持 1M。这次放出的是没有经过中训练和后训练的 checkpoint，等于把“干净底板”交给社区做领域适配、指令微调和强化学习。在官方基准上，MMLU 得分 93.3、HumanEval+ 得分 82.3；经过后训练的正式版会随后推出。权重已在 Hugging Face 和 ModelScope 上线，提供 FP8 和 BF16 两个版本，支持 SGLang 和 vLLM 部署。
https://huggingface.co/baidu/ERNIE-5.5-Flash-Base

**5. 蚂蚁百灵发布 Ling-3.2-flash：560B 总参数、25B 激活、1M 上下文**
这是原生多模态模型，支持文本、图像和视频输入，面向复杂视觉理解、长时程多模态 agent、3D 理解与交互、医疗智能等场景。官方称它在 OmniDocBench1.5、ZEROBench(Sub)、Vision2Web 三项发布评测上都高于 Claude Opus 5（max）。目前只能通过 API 使用，权重没有公开。需要注意，这是官方自评，而且选用的基准测试刚好偏中文文档、视觉和空间推理方向。
https://x.com/AntLingAGI/status/2118428246664761379

**6. Kimi 正式推出托管智能体服务 Kimi Hosted Agents**
把运行 Agent 的 Harness 框架搬到云端，企业不用自己搭建框架，就能获得 7×24 小时的托管环境，支持需要长时间运行的任务和多智能体协作。配套提供 140 多个 Skills、30 多个插件，覆盖联网检索、专业数据查询、办公文档处理和内容生成；企业也可以接入自己已有的工具和数据源。安全方面提供独立沙箱、网络权限控制、执行过程留痕和审计导出。按用量计费，由三部分组成：沙箱运行时长（每小时 0.072 元）、模型推理费用和插件调用费用。首批提供 8 个金融 Agent 模板（投研建模、深度研究、晨报生成、IPO 跟踪、持仓监控等）。这是把“Agent 基础设施”直接做成云产品，竞争对手从模型厂商转向云平台。
https://platform.kimi.com/docs/hosted-agents/overview

**7. Cursor 推出 Live Apps：只要描述需求，就能直接构建并部署成在线 Web 应用**
用户启动一个 Cloud Agent 并描述想要的应用，Cursor 就会负责构建 Web 应用、按需启动 Postgres、配置基于 Cursor SSO 的鉴权并完成托管，然后生成分享链接。可以分享给指定人员、群组或整个团队，访问都需登录 Cursor；个人套餐可以公开分享，Teams 和 Enterprise 默认关闭。仅支持云端 agent，本地 agent 无法使用。管理员可以控制功能开关、公开分享和 API key，也能下架任意应用。开发工具正在从“写代码”转向“直接交付可运行的产品”。
https://cursor.com/

**8. DeepSeek Harness：日活 154 万，日消耗 92 万亿 token，要做官方插件市场**
官方公布了时间线：8 月 13 日 v0.1 上线，9 月 29 日发布桌面端。截至 11 月 4 日，按使用官方 API 的用户统计，日活跃用户达到 154 万，日消耗 Token 约 92 万亿。第三方插件已经增至约 3.5 万个，约 60% 的活跃用户至少制作或安装过一款第三方插件。官方表示接下来会提升插件 API 的稳定性和兼容性，完善插件安全机制，并建设官方插件市场；同时筹备面向插件作者的支持计划（Token 激励、技术交流、作品推荐）。一个开源式 harness 依赖插件生态自发成长到这个规模，这在国产开发工具里不常见。
https://mp.weixin.qq.com/s/xqyrRaiBpIcf0jeJzP7W0g

**9. Claude Code 被曝泄露用户邮箱，Anthropic 已补上发送前确认**
有用户发现，用 claude.ai 账号登录时，Claude Code 会把账号邮箱以注记形式写入对话上下文，并传递给 subagent，而官方文档里没有提到这个机制。实测证实后，有人指出模型在执行外部请求时会把邮箱写进 User-Agent，或者在 git 作者信息未配置时用账号邮箱提交代码，波及 crates.io、SEC EDGAR 等站点，有用户称自己因此每天收到数十封诈骗邮件。Anthropic 先在 v2.1.234 指示模型不要把邮箱发往无关服务，又在 v2.1.317 增加了“网络或 shell 工具调用发送账号邮箱前先询问用户”。这不是模型幻觉，而是产品默认行为把身份信息带到了外部，性质上更接近隐私事故。
https://x.com/claudeai/status/2118403114890137895

**10. METR：Anthropic 模型能力提升速度约为此前两倍，但关键证据被删节**
METR 从今年 8 月起查阅 Anthropic 内部数据、访谈研究人员，估计截至 2026 年 10 月，Anthropic 模型在界定明确任务上的能力提升速度约为 2024 年 3 月至 2025 年 10 月期间的两倍；不确定性很高，1.3 至 3 倍都在可能范围内。另一项基准趋势分析得出约 1.9 倍。METR 认为 AI 参与研发可能贡献了大部分加速，但公司内部对原因并没有共识。争议点在于：Anthropic 删去了公开报告中大量最有信息量的证据，使外界难以独立核验。联合创始人 Sam McCandlish 承认删节增加了核验难度，理由是加速方法涉及商业机密、公开后可能给其他公司提供加速路线图而加剧安全风险，同时表示认同“AI 正在加快研究，但具体加快了多少很难说”这个结论。Anthropic 计划在未来几周发布自己的分析。
https://metr.org/blog/2026-11-05-anthropic-ai-rd-acceleration-assessment/

---

**其他一句话**
- 腾讯混元 Hy4 在 WorkBuddy 首发接入后，调用量激增，大量用户触及额度上限，推理集群紧急扩容十倍，Hy3 限免延长到 11 月 15 日。
- 月之暗面开源 TCSExam 理论计算机科学评测基准（Full 100 题、Lite 20 题，覆盖定理证明、求解器工程、构造、开放猜想，用 Lean 作答），默认用 Kimi Code 评测，也支持 Claude Code、Codex、Grok Build。
- Vals AI 称在多家前沿实验室的公开和内部模型中发现重大安全对齐问题，可能被滥用于高风险领域，已向相关实验室披露，将在数周内公开。
- OpenAI GPT-Live 外呼电话 API 正式 GA，可通过任意 SIP 中继（Telnyx、Twilio）外呼，支持 HD Voice 与 DTMF，振铃最长 3 分钟、通话最长 2 小时且不可配置。
- 中国科大开源 RNA 基础模型 structRFM，2100 万条序列-结构配对数据做结构引导预训练，成果登上《自然》，数据、权重和代码全开放。

原文：https://daily.juya.uk/issues/2026-11-06/ （已标记已读）
