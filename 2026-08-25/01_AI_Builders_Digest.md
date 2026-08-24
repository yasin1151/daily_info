
All content extracted and fresh (feed generated 2026-08-24, ~1 day old). High-signal items identified across coding agents (Codex fixes), LLM infrastructure (price elasticity/gateways), agent tooling (fx open protocols, evals methodology, agent UI), and product shifts (systems of record, Apple Foundation Models). Assembling the Chinese digest:

**AI Builders Digest - 2026-08-25**

**X / Twitter**

**1. Vercel CEO Guillermo Rauch：推理降价引爆需求，网关赛道升温**
OpenAI 给 Sol 降价、Vercel AI Gateway 跟进折扣后，Sol 成为 Vercel 上增长最快的前沿模型。Rauch 的判断：智能的需求弹性极高，推理成本一降用量就暴涨；不用 gateway 等于错过这轮价格波动红利，路由/网关层成为必然。
为什么重要：推理价格战正在重塑 LLM 基础设施成本结构，网关和路由会成为 Agent 工具链的标配层。
https://x.com/rauchg/status/2091671326897713424

**2. Vercel CEO Guillermo Rauch：fx 的扩展哲学 = 开放协议 + Unix**
Rauch 公布新工具 fx 的扩展思路：全部走开放协议（MCP、agentskills.io 的 Skills、agent-plugins.org 的 Plugins），再加上 Unix 哲学（小而专、互相组合）和 libfx（可嵌入更复杂的程序，自建 CLI、后台 agent、软件工厂）。
为什么重要：Agent 工具链正在收敛到开放协议标准，自研引擎/Agent 平台可直接借鉴这套可嵌入架构。
https://x.com/rauchg/status/2091583525661384813

**3. OpenAI Codex 负责人 Thibault Sottiaux：Codex 用量问题已修复；2026 是模型效率之年**
Sottiaux 宣布 Codex 的 reset 已推广到全部账号，并修复了此前反馈的用量问题，后续还有改进。另一条高赞判断：2026 年是公司开始认真对待模型效率和可靠性的年份，因为模型已成为关键基础设施。
为什么重要：Codex 是 coding agent 的标杆产品，其用量策略与稳定性直接影响开发者工具链选型。
https://x.com/thsottiaux/status/2091688655828246890
https://x.com/thsottiaux/status/2091581575108653374

**4. YC 总裁 Garry Tan：系统记录类软件要么变成 AI harness，要么被 agent 取代**
Tan 的预测：systems of record 必须进化为 AI harness（能承接 agent 的载体），否则会被 agent 直接替换。
为什么重要：这是对下一代企业软件形态的激进判断：软件不再只是给人录数据的界面，而是给 agent 用的接口层。
https://x.com/garrytan/status/2091742825042030681

**5. Meta AI 高级总监 Madhu Guru：eval 要按"任务"度量，不是只看最终答案**
「构建优秀 eval」系列第 7 篇，Goldilocks 原则。以金融分析 agent 为例：最终输出是股票推荐，但真正要度量的是之前的多个子任务（理解客户、组合、风险偏好等）。团队最常见的错误是只拿 golden answer 比对最终推荐。
为什么重要：agent 评测方法论直接决定工具链质量，自研 agent 产品拆 eval 时可照这个框架做。
https://x.com/realmadhuguru/status/2091684812012875981

**6. OpenClaw 作者 Peter Steinberger：agent 的 UI 与团队可见性比 CLI 更香**
"CLI 是挺好，但在你工作的地方能看到 UI 可视化和你的团队，更香。"
为什么重要：agent 编排工具正从纯终端形态走向带可视化、面向团队协作的形态，这是 agent 平台的产品方向信号。
https://x.com/steipete/status/2091650136506327253

**7. Peter Yang：eval 分两种，top-down 和 bottom-up**
引用 Shreya 的观点：top-down eval 是"只给任务描述、在真空里推演"，Claude 很擅长帮你生成这类 eval；bottom-up eval 是从大量样本输出里把人的直觉反馈固化成评测，这部分 Claude 很差，必须人自己来。
为什么重要：划清了 LLM 辅助写 eval 的能力边界，搭建 eval 流程时可直接参考。
https://x.com/petergyang/status/2091586298779955512

**官方博客**

**8. Claude Blog：Claude 接入 Apple Foundation Models 框架**
Anthropic 发布 Swift package，让 Apple 开发者通过 Foundation Models 框架调用 Claude：本地 on-device 模型处理摘要、抽取等快速任务，Claude 承接多步推理、代码生成、联网搜索和执行代码，用 @Generable 注解直接返回类型化 Swift 值。支持 iOS/iPadOS/macOS/visionOS/watchOS 27（发布于 6 月，今日 feed 收录）。
为什么重要：端侧 + 云端模型分工的落地范式，对 Apple 平台原生 AI 应用和自研引擎有参考价值。
https://claude.com/blog/claude-for-foundation-models

---
Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
