
I have everything needed: all 32 tweets reviewed, podcast fully read (168 speaker blocks). Composing the digest directly — dataset is well within single-context range. Content is fresh (feed generated 2026-08-26, tweets from 08-25/26).

**AI Builders Digest — 2026-08-27**

## 头条：OpenAI 自研芯片落地

**Sam Altman（OpenAI CEO）** 发了一条只有 6 个词的消息：「we made a chip and it is fast」（我们造了颗芯片，而且很快），获 3.28 万赞。这是 OpenAI 自研芯片计划最直接的公开确认——继此前与 Broadcom 合作的传闻后，Altman 亲自官宣。对 LLM 基础设施格局意义重大：推理成本曲线、对单一 GPU 供应商的依赖度、乃至下一代模型定价都会因此改变。
https://x.com/sama/status/2092339694210040187

## Claude 记忆体系升级（本周最大产品动向）

**Claude 官方账号**连发三条，宣布记忆功能正式落地：Chat 与 Claude Cowork 共享同一份记忆（跟 Cowork 交代任务时它已知道你聊过的项目、老板偏好、上季度的客户）；记忆以「主题列表」形式存在 Settings 里，可读、可改、可删，也会随对话自动更新，也可主动说「remember this」；健康、宗教信仰等敏感话题默认不记忆，需在设置里手动打开。Free/Pro/Max 默认开启。
https://x.com/claudeai/status/2092299704864284888
https://x.com/claudeai/status/2092299707653439497
https://x.com/claudeai/status/2092299710002319742

**Boris Cherny（Anthropic，Claude Code）**：「memory is now simpler and more powerful」——Claude Code 的记忆也同步简化增强（1.4K 赞）。
https://x.com/bcherny/status/2092355642363453943

**Cat Wu（Anthropic，Claude Code）**：基于用户反馈，Chat 和 Cowork 的记忆已统一——跟 Claude 说一次「记住这个」，所有界面都有该上下文。
https://x.com/_catwu/status/2092337156455051345

背景：昨天 YC CEO Garry Tan 还在调侃「cross-harness memory maxxing」（跨工具链记忆拉满），今天 Anthropic 就全线铺开了。记忆正成为 coding agent 的标配竞争点。

## OpenAI 推出 Codex/ChatGPT 团队版

**Thibault Sottiaux（OpenAI，Codex 与 ChatGPT 负责人）**：需求量太大，推出面向团队和小公司的套餐——含全部 ChatGPT/ChatGPT Work/Codex 功能，可连 Google Workspace、Slack、GitHub、Microsoft 365，带 SAML/SSO/MFA 安全工作区、集中计费管理、用量分析与支出控制，**且无 5 小时限额**（2.9K 赞）。直接对标 Claude 的团队方案，无 5h 限制是卖点。
https://x.com/thsottiaux/status/2092345330272780499

**⚠️ Swyx** 发 PSA：暂时别用 Codex 的「locked use」能力——它依赖不稳定的 macOS 特性，一周内两次把整台 Mac 的 keychain 锁死；Apple 开发者论坛已确认是已知 bug。想全云化但云还没准备好。
https://x.com/swyx/status/2092492963435946494

## Agent 工具链动态

**Vercel CEO Guillermo Rauch** 两条：
- **Run SDK**：为动态 Code Mode 执行提供安全的 `eval`——agent 写代码时不一定需要完整沙箱，可在轻量 QuickJS 安全上下文里直接跑，更快更省成本（`npm i run`）。
https://x.com/rauchg/status/2092382653161107534
- **Vercel Connect GA**：解决「构建 agent 最难的问题——服务与数据的安全连接」。`vercel connect create notion` 即可拿到一个 MCP client，以已认证用户身份查询服务。
https://x.com/rauchg/status/2092352411839193234

**Thariq（Anthropic，Claude Code）**：预告「soon」——Claude Code 会变得更可 hack（可扩展/可定制），1.1K 赞。对自研 Agent 工具链是直接利好信号。
https://x.com/trq212/status/2092303682616627311

**Google Labs** 新实验 **Putty**：多人实时协作的 vibe coding 工具，可一起搭工具和网站（仅美国、18+，排队中）。
https://x.com/GoogleLabs/status/2092293667688173593

## 值得读的观点

**Box CEO Aaron Levie**：模型与企业实际工作流之间存在巨大鸿沟，这正是应用型 AI 公司的机会窗口。「世界不想要裸模型和 agent，它想要问题被解决、结果被达成。」价值在于：理解业务上下文、变革管理、跨模型路由的 harness、接入关键业务系统、把用户接入 agent 工作流的 UX、领域 evals——这些都远超模型智能本身。
https://x.com/levie/status/2092466424694649066

**Madhu Guru（Meta AI 资深总监，前 Google Gemini/Veo 负责人）**：eval 系列第 9 篇《The Eval Roadmap Problem》——大多数 eval 失败是因为被当成静态工件，而用户期望和行为一直在演化。以金融研究 agent 为例：早期「总结 5 页财报」→ 3 周后「对比最近 5 份财报」→ 2 个月后「基于 15 份文件构建投资论点」→ 最终「监控持仓自动告警」。每个阶段需要不同能力、不同 eval。建议：映射使用演化维度 → 挖生产 trace → 为下一阶段预建 P0 eval。自研 agent 的评测体系必读。
https://x.com/realmadhuguru/status/2092426017118028266

**Peter Yang** 开源 `/fuck-cancer` skill：帮患者/家属整理病情简报（护理团队信息、下一步行动、已知事实、医学术语白话解释、护理日志），用 ChatGPT/Codex 和 Claude Code 都能跑，可存 Markdown 或同步 Google Doc。是「skill 生态」的落地示范——单个领域技能如何系统化 Agent 工作流。
https://x.com/petergyang/status/2092249012913258946

**Aditya Agarwal（SPC 合伙人，前 Dropbox CTO）**：大众反感数据中心建设毫不意外——AI 目前只服务知识工作者和最高薪人群；真正的转折点是 AI 能治好困扰所有人的疾病时。行业还总在贩卖恐惧，而不是描绘积极未来。
https://x.com/adityaag/status/2092290497826173186

## 播客

**Training Data：Parallel 的 Parag Agrawal——为 AI Agent 建一个全新的 Web**
前 Twitter CEO Parag Agrawal 详解他的新公司 Parallel 及其核心论点：**人类的点击数据是一个 bug**——agent 做搜索应依赖 agent 反馈而非人类点击。Parallel 三年前押注 agent 的搜索量将是人类的 1000 倍，先做「搜索 agent」而非搜索引擎，用推理时算力换爬虫成本（先发布时只覆盖少量页面也能靠 agent 的深度检索弥补）。已发布 TurboNow，号称「市面上最快、质量最高的 agentic web search」；同日官宣与 Google Cloud 合作，为 GCP 上的 Gemini 等模型提供 grounding。

最精彩的部分是**互联网经济学**：广告是高效的差别定价机制，但 agent 访问无法变现——你没法对一台替你干活的 agent 展示广告。内容授权大单（类似 OpenAI 买内容）只存在于头部且规模不涨。Parallel 的解法是用博弈论中的 **Shapley value**（公司原名就叫 Shapley Inc.）做归因与分成：通过模拟「移除某内容源后质量下降多少」来公平计算每个数据源对 agent 产出的边际贡献。他判断 agent 生态分三层演进：web 作为 agent 工具 → 子 agent 网络 → web 从 pull 变 push（agent 主动全天候在网络上执行工作）。他还建议内容方「双端发布」——同时写给人和 agent 读。
https://www.youtube.com/playlist?list=PLOhHNjZItNnMm5tdW61JpnyxeYH5NDDx8

---
*生成工具：Follow Builders skill（https://github.com/zarazhangrui/follow-builders）*
