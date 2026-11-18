
**橘鸦AI早报 · 2026-11-18 期摘要**

> 本期主线：OpenAI 用「贵/便宜」双模型拆分战场，微软立刻用半价模型贴身紧逼；Agent 侧从「会写代码」转向「自己组队干几周活」。

---

**1｜OpenAI 发布 GPT-6.2 双模型：Astra 打复杂任务，Sol 打日常**
Astra 主攻复杂编程、科研、长程任务，官方多步工作评测 Agents' Last Exam 比前代高 5.2 分、单项成本不到前代 1/3；Sol 主打日常多步工作，在 Cognition 的 FrontierCode 2.0 上两款最高推理档只差 0.5 分，但 Sol 单项成本仅 Astra 的 1/5。API 定价：Astra 输入 8／缓存 0.4／输出 40 美元每百万 token，Sol 是 2／0.10／10。落地 ChatGPT Work、Codex 与 API，Pro 200 可先在 Codex 给 Sol 开 Ultrafast。
→ 影响：OpenAI 第一次把「同代能力」拆成两档价格卖，明显是冲着"够用就好"的日常场景和成本敏感开发者去的，Astra 的定价也留出了给微软、Anthropic 打价格战的空间。
https://openai.com/index/introducing-gpt-6-2-astra-sol/

**2｜社区给新模型差评，Altman、Tibo 双双回应**
模型刚上线就吃了一波吐槽：Matt Shumer 直言两款都"很难用"，开发者 Theo Browne 批评 Astra 在长任务中容易中途停下来、完成后也说不清自己做了什么。Altman 在发布帖下承认"能力很强但用起来不够顺手"，称后续版本优先改易用性；Codex 负责人 Tibo 强调更快更便宜、团队会继续改。
→ 影响：能力指标涨了、手感掉了，说明 benchmark 和真实工作流之间的缝还在扩大。这条比发布本身更值得看：官方罕见地当场认账。
https://x.com/sama/status/2122798042734633452 ｜ https://x.com/thsottiaux/status/2122816458711548126

**3｜微软 Ignite 一口气发七款 MAI 模型，主打低价**
编程模型 MAI Code 2 / Code 2 Flash 已进 GitHub Copilot（五折优惠到明年 5 月 17 日）；微软称 Code 2 在四项编程基准平均以约 40% 的价格达到 GPT-6.1 Sol 的 98% 性能。另有图像 MAI Image 2.7（Artificial Analysis 图像编辑排名第一）、决策 Decision 1.1、安全 MAI Cyber 2 Flash（官方称单任务成本不到 GPT-6 Astra 的 2%）、实时语音 Realtime 1、医疗转写 Dragon Copilot Transcribe（每月 1000 万次医患对话）。微软自认这批模型没针对基础科研和超长周期 agent 任务调优。
→ 影响：微软不再只做"OpenAI 的分销商"，而是用自研模型在 Copilot 内部做成本替代，98%/40% 这个比例就是给企业采购算账用的。
https://microsoft.ai/news/microsoft-ignite-2026-mai-keynote/

**4｜Gemini Tasks 在美日韩加澳印免费开放，能代打电话、代结账**
Google 把 Gemini 的 Tasks 功能免费开放给六个国家数亿用户，免费用户也能用 Gemini 4 Hydrogen 跑任务。在应用内把 Chat 切到 Task 描述需求，Gemini 就在后台处理长项目、按周期执行；美国先上代打电话、Google Pay 结账、短信和邮件转发，可以代用户联系本地商家比价或预约。Workspace 集成同步升级。
→ 影响：Agent 的入口从"开发者工具"变成"普通人的聊天框按钮"，而且直接接入了支付和电话这种真实世界动作，权限和误操作风险随之上升。
https://blog.google/innovation-and-ai/products/gemini-app/tasks-in-gemini-free-new-features/

**5｜Perplexity 推出 Orchestrator API：45+ 模型一个接口**
把 OpenAI、Anthropic、Google、xAI 的专有模型和开放权重模型统一到一个接口，兼容现有 OpenAI / Anthropic SDK。按实际作答模型的公开 token 单价统一计费，与哪家提供商服务无关；同一模型跨提供商的故障切换是自动的——出错、限流、超时后在另一个部署上重试。
→ 影响：卖点不是模型多，而是"可靠性层"。多供应商冗余这件事被产品化成一行 API，对做生产环境的人比便宜几个 token 更有价值。
https://www.perplexity.ai/hub/blog/orchestrator-one-api-for-reliable-inference

**6｜Cognition 推出 Devin Bots：一支 agent 团队连干数天到数周**
用户只给指标或目标，Bot 带一支 agent 团队持续追求，负责规划、代码审查、自动化测试，直到 PR 可合并；可通过 Slack、短信、电话或群聊跟进进度并调整。Cognition 称测试用户平均每条消息合并的 PR 数增加 4.5 倍，有工程师从每周 50 个 PR 涨到近 2000 个。
→ 影响：从"结对编程"跨到"外包一个小组"。但 2000 PR 这个数字也意味着评审压力会整体后移到人类这边——量上去了，谁来看得完是个新问题。
https://x.com/cognition/status/2122737511684587551

**7｜Claude Code 实验性 Code Mode 上线：Claude 改写 JS 脚本串工具**
Claude 不再逐个直接调用工具，而是编写 JavaScript 脚本交给 Claude Code 在会话里运行；代码可并行执行命令，长命令转后台时还能继续对话。需设 `CLAUDE_CODE_EXPERIMENTAL_CODE_MODE=1`，要求 v2.1.323+ 和订阅或 Console 账号，仅支持终端交互会话。
→ 影响：和 OpenAI 的 code-as-action 思路撞到了同一条路上——工具调用的瓶颈从"模型会不会"变成"能不能编排"。并行执行对长任务的实际提速比换模型更明显。
http://code.claude.com/docs/en/code-mode

**8｜OpenAI 把模型"版本化"进垂直行业：法律 Astra、ChatGPT for Sales**
法律版 Astra 基于 GPT-6.2 Astra，叠加专门的法律搜索索引和研究/权衡/撰写指令。Harvey LAB-AA 评测满分率 20.8% 排第一、比通用版高近 40%，每任务平均实质性幻觉 0.03 次为对比最低；Vals AI 法律研究通过率从 9 月约 46% 升到 54.81%。Enterprise 客户可申请，API 需单独审批。同期推出 ChatGPT for Sales，含 Sales 插件和 30 多个合作伙伴插件，可接 Salesforce、HubSpot。
→ 影响：OpenAI 开始卖"检索+指令+评测"这套封装，而不是裸模型。"实质性幻觉 0.03 次"这种指标也说明专业场景的竞争标准已经换成了可靠性而非智力。
https://openai.com/zh-Hans-CN/index/astra-law-6-2/ ｜ https://openai.com/index/introducing-chatgpt-for-sales

**9｜Isomorphic Labs 完成 50 亿美元 C 轮融资**
超额认购，Greenoaks 与 Sequoia 联合领投，a16z 等新投资方加入，Alphabet 继续跟投，全部现有投资者参与。资金用于继续开发药物设计引擎 IsoDDE、扩大候选药物管线并推进临床试验；公司称肿瘤、免疫学内部项目与合作项目已取得积极临床前结果。
→ 影响：AI 制药单轮 50 亿美元的体量说明资本已从"看故事"转到"等临床"。真正的分水岭在候选药物能不能进临床，而不是模型评分。
https://www.isomorphiclabs.com/articles/isomorphic-labs-announces-series-c-investment-round

**10｜英伟达高层震荡继续：黄仁勋称愿回归，董事会称无意让其复任**
黄仁勋 11 月 17 日在 X 表示若董事会认定符合各方利益他愿重新任 CEO，并承诺配合独立调查；Axios 报道董事长 Harvey Jones 在财报电话会上称董事会一致接受辞呈、无意让其复任。CFO Colette Kress 暂代 CEO。同期：SEC 正就英伟达信息披露是否误导投资者展开民事调查（WSJ）；董事会新设"国家安全与出口管制监督委员会"，至少每季度开会，国安与全球贸易合规团队直接向其及临时 CEO 汇报。
→ 影响：一家全球最关键的算力公司同时处于 CEO 空缺、监管调查和出口管制三重压力下。这个委员会的设立，本质是把"卖给谁"的决策从管理层上升到董事会层面。
https://x.com/JensenHuang/status/2122726005219737649 ｜ https://www.wsj.com/business/sec-is-probing-nvidia-amid-departure-of-ceo-jensen-huang-ee7643f8

**11｜国产两则：可灵 Image 4.0、商汤开源 SenseNova-Loop-9B**
可灵 Image 4.0 把视觉理解与图像生成放进同一架构，原生 8K，单图最多排 2000 字，一次描述可生成最多 10 张同创意系列图，支持电商详情页与网页设计长图，同时开放企业与开发者 API。商汤以 Apache 2.0 开源 SenseNova-Loop-9B，约 9B 参数，靠循环复用共享中间层把 32 层扩成 56 次计算，支持文本+图像、512K 上下文，首日提供官方 AWQ 4-bit 量化版，称在部分 Agent 与数据分析任务上接近 Qwen3.8-27B。
→ 影响：一条走商用落地（电商长图/详情页是最直接的付费场景），一条走开源小模型+长上下文，路线不冲突但都很务实。
https://mp.weixin.qq.com/s/p3_DIBRUUgmxShjD5Wp27w ｜ https://github.com/OpenSenseNova/SenseNova-Loop

**12｜治理两条：Anthropic 收紧漏洞披露，微软拉 40+ 家组织做 AI 透明度标准**
Anthropic 自 2027 年 1 月 1 日起把高危/关键漏洞披露期限从 90 天缩到 30 天、其他级别缩到 45 天；维护者 15 天不回应就请外部协调机构介入（原 30 天）；补丁后公开完整细节的等待期从 45 天降到 30 天。正在被利用的漏洞仍为 7 天。理由是 AI 提升了漏洞挖掘效率、重复发现风险上升，"不再认为漏洞能长期保持私密"。微软则在 Ignite 启动 AI Transparency Initiative，联合 Accenture、Adobe 等 40+ 组织做跨模型跨厂商的开放标准，让企业能独立核验 agent 的行为与数据访问，成果计划并入 MAI、Foundry、Copilot。
→ 影响：两条都是同一个判断——AI 让攻防和审计的速度都变快了，旧的 90 天/厂商自证节奏撑不住了。
https://www.anthropic.com/research/coordinated-vulnerability-disclosure-timelines ｜ https://news.microsoft.com/source/2026/11/17/microsoft-and-organizations-across-industries-launch-ai-transparency-initiative-to-strengthen-enterprise-trust-in-ai-models-and-agents/

---
已标记第 7490 期（2026-11-18）为已读。本期无广告类条目，已跳过 AI Studio 自定义域名、Vids 虚拟形象、Antigravity 配额重置与 OpenCode 额度提升等纯运营/额度类更新。
