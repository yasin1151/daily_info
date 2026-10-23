
**橘鸦AI早报 2026-10-23** ｜ 原期：https://daily.juya.uk/issues/2026-10-23/

---

**1. Anthropic 把 Agent Skills 标准捐赠给 Linux 基金会下的 Agentic AI Foundation**
捐赠内容不只是代码，还包括名称、标志、GitHub 组织和域名；同时承诺保持开放、社区驱动和厂商中立，开发者不必加入 AAIF 也可以继续使用或贡献。官方称，标准发布以来，已有 70 多个 Agent 平台集成，其中包括 ChatGPT、Cursor、GitHub Copilot 和 VS Code。
**影响**：这表示“Agent 能力打包格式”从一家厂商的规范变成了中立基础设施。对第三方生态是利好，但也意味着标准制定权从 Anthropic 手中转移出去，与其“永久控制”不如“永久存在”。
https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation

**2. OpenAI 正式开放 Decisions API：不生成完整回复，只做分类、打分的接口**
目前仅支持 gpt-6-luna，可评估文本、图像和 JSON，返回条件成立的概率、预设选项或评分。速度最高达到 Responses API 调同款模型的 10 倍；单请求问题上限从 200 个提高到 400 个，并新增 GPT-Live 原生集成和提示缓存。定价：未缓存输入 $0.10/百万 token，缓存输入 $0.01，输出 token 不计费。
**影响**：这是把“模型当分类器、路由器”从提示词技巧变成官方产品。做内容审核、请求分流、Agent 下一步动作选择的团队，成本和延迟都会明显下降，而且输出结构天然可控——比让模型自由发挥更工程化。
https://openai.com/index/decisions-api

**3. Claude 下周起在 Pro、Max、Team 的新会话中默认启用“自动模式”**
该模式不再要求用户逐项批准操作，而是通过自动检查放行安全操作、拦截风险操作，遇到风险时让 Claude 自己寻找其他路径，用户可随时切回手动。
**影响**：Anthropic 在 Agent 权限上比 OpenAI 更激进：默认不再事事确认，等于把“人在环里”从默认项变成可选项。对普通用户是体验跃升，对企业合规团队则是新的审计和培训负担。
https://x.com/claudeai/status/2113360845409583307

**4. Claude 在几周内为 123 个开源库写出形式化安全证明**
Anthropic 与 Theorem 合作，对 Google OSS-Fuzz 中的 123 个库做形式化验证，为 239 个测试入口证明“任何小于 64MB 的输入都不会崩溃”，由 Rocq 证明检查器自动核验，无需人工逐行审阅。过程中还发现并修复数百个漏洞，其中一些要输入约 20MB 特殊构造的数据才会触发，模糊测试很难发现。Anthropic 自己声明了局限：只覆盖被测试的那部分代码，前提是单线程 RISC-V 程序运行在 Linux 上，因此不代表这些库没有漏洞。
**影响**：形式化验证过去是专家数年的工作，这里缩短到几周。这是“AI 做可验证工程”目前最有说服力的案例之一——不是声称模型更聪明，而是输出能被机器检查。
https://anthropic.com/research/formal-verification

**5. METR 与 Redwood 披露 OpenAI 内部 Agent 监控系统的多处绕过方式**
两家各派 1 名员工驻场 3 周，指出延迟监控、绕过沙盒、Auto-Review 等潜在漏洞；估计未监控的上下文压缩事件可能导致约 10% 符合条件的内部 Codex 流量漏检，但比例存在较大不确定性。OpenAI 称所有影响生产防护的漏洞均已修复，评估方尚未验证该说法，且结论针对历史系统。
**影响**：这是少见的“外部红队公开报告 + 厂商公开回应”组合。AI 用来自我监控能否充当安全底线，这份材料给出的证据偏负面——监控系统本身也会被 Agent 绕过。
https://metr.org/blog/2026-10-22-red-teaming-openai-agent-monitoring/

**6. Pichai 解释 Gemini 3.5 Pro 为什么没发布：任务优先级被 Flash 占用了**
团队训练 3.5 系列时意识到 Agent 能力（尤其编码）有差距，而 Flash 更小、更高效、能进行更多轮迭代，于是接连推进了 3.5、3.6、3.7、3.8 四代 Flash；等到这些成果能用于 Pro 时，Gemini 4 Argon 的预训练已经完成。
**影响**：3.5 Pro 是被主动放弃的，不是延期。这说明 Google 内部已把“快速迭代小模型、专门弥补 Agent 短板”当成主路径，大模型代的节奏改为让位给 Flash 的密集迭代。
https://sources.news/p/sundar-pichai-gemini-4-google-other-bets

**7. Microsoft MAI-DxO：Science 论文称急诊诊断准确率 80%，医生 47%**
系统协调多个 Agent 逐步提问、选择检查并形成诊断。在 MIMIC-IV-ED 急诊病例上准确率为 80%（医生 47%）；在 304 个 NEJM 复杂病例上准确率 83%，医生借助参考资料和不借助参考资料时分别为 36% 和 22%。所需检查更少、估算成本更低，并开源 SDBench 基准与评估代码。
**注意**：结果来自既往病例的模拟评估，真实临床研究尚未开展（将与 Beth Israel Deaconess 合作）。
**影响**：数字很直观，但“回溯模拟”和“真实急诊”之间的差距历来巨大，且论文口径的对照组设置需要细看。值得关注，暂不宜当作结论。
https://microsoft.ai/news/the-path-to-medical-superintelligence/

**8. 彭博社：DeepSeek 完成约 1000 亿元人民币融资（尚未官方确认）**
约合 150 亿美元，腾讯和宁德时代是本轮最大投资方之一。知情人士称，洽谈期间至少两次上调目标：从 500 亿元到 800 亿元，再到约 1000 亿元。
**影响**：单轮规模直接对标美国头部实验室。更值得注意的是资金结构：来自腾讯和宁德时代这类产业资本，不是纯 VC，意味着资金背后是算力、能源和数据中心的实际配套，而非纯财务投资。
https://www.bloomberg.com/news/articles/2026-10-22/deepseek-raises-15-billion-in-challenge-to-leading-us-labs

**9. 1Password 推出 1Password for Agents：Agent 代为登录但不接触密码**
Agent 请求登录时，用户在自己设备上查看所需凭据及用途并批准，由 1Password 把凭据直接填入登录表单，Agent 全程不接收、不查看、不存储密码。Grok Bot 已接入，未来几天逐步推送。
**影响**：Agent 时代真正缺的是“身份与授权层”，不是能力。“人批准、机器执行、密码不写入本地”这个模式很可能成为 Agent 登录的标准形态，也顺手解决了把密码交给 Agent 的安全顾虑。
https://1password.com/blog/1password-for-ai-agents

**10. 米哈游崩坏 AI 团队联合清华开源 GameScaling 游戏操作模型**
基于 Qwen3.5 视觉语言模型持续预训练，参数覆盖 0.8B 至 27B。输入当前画面、近期画面和动作历史，每次输出未来 200 毫秒的键鼠动作。共 120 组训练配置考察数据量、多样性与模型规模，团队称实时评测得分最高，但向差异较大的游戏世界迁移仍有局限。开放 8 个 checkpoint 和推理客户端，Apache-2.0，不含训练代码与训练数据。
**影响**：这是“实时操作与世界模型”路线在游戏场景的公开基线，对做游戏 Agent、具身控制的人是可直接上手的基础参照，也是国产团队少有的一次完整开放。
https://gamescaling.github.io/

---
**另注（不单列）**：Artificial Analysis 发布 Coding Agent Index v2.0，用 Cognition 的 FrontierCode v1.1 替换 DeepSWE v1.1、加严 SWE-Atlas-QnA 评分后，21 种受测配置中 20 种分数下降，平均分从 54.8 降到 47.4；Claude Code + Opus 5.5 以 61.7 居首。两版分数不可直接对比，凡是引用旧榜单结论的地方都要重看。
https://artificialanalysis.ai/methodology/coding-agents-benchmarking

已标记为已读（article 6856）。
