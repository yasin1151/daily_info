
AI Builders Digest — 2026-09-12

数据源：18 位 builder / 35 条推文 + 1 期播客（feed 生成于 2026-09-11，新鲜）

# 一、X / 推特

## Boris Cherny（Anthropic，Claude Code 团队）

本周最值得读的一条长回复（1155 赞）。背景是有用户抱怨 Claude 写出来的代码质量差，他给出正面答复：一次性原型和丢弃型代码可以完全当黑盒，坏了也无所谓；但生产代码的标准应该比人写的还高。Anthropic 内部为此上了一整套护栏：大量 lint 规则、大量测试、Claude 驱动的端到端测试、每天跑的 Claude fuzzer、自动化 code review 和安全审查、自动化重构。他明确说"你的职责是守住代码质量这条线"，如果 Claude 的产出不达标，依次尝试：换成最新前沿模型（Opus 5 或 Fable 5.1）、把 effort 调到 high 或 xhigh、投资 CLAUDE.md 和 skills 来教会 Claude 在你的代码库里怎么工作；都不行就多介入 steering，或者让 Claude 先还技术债、重写代码库。

为什么值得关注：这是 Claude Code 负责人少见的把"生产级 agentic coding 的质量体系"讲成一份可执行清单，lint + 测试 + fuzz + 自动 review + 规则文件这套组合，是自研引擎护栏设计可以直接对照的模板。
https://x.com/bcherny/status/2098217573276131577

另一条（338 赞）：Anthropic 最新 Threat Intelligence 报告"极其可怕且重要"。模型越强，没有正确的防护和监控就越危险；很多能力是双用途的，会写代码的模型可以拿来攻击关键基础设施，能协助生物研究的模型也能被用来制造下一次大流行。
https://x.com/bcherny/status/2098281805770309686

## Thibault Sottiaux（OpenAI，Codex 与 ChatGPT）

"Scaled agents on demand"（2715 赞）：基本上就是把跑在 ChatGPT Work 底下的 agent 基础设施整个打包成一个 API，1 分钟内就能上手开写。

为什么值得关注：OpenAI 把"按需扩容的 agent 运行时"直接产品化成 API，agent 工具链从"自己搭一套"转向"直接调用"的分水岭很难比这更清晰了。
https://x.com/thsottiaux/status/2098238138334548260

同一天他宣布暂停 200 美元 Pro 计划的新订阅（15157 赞）：为保证现有用户的体验和 Astra 的持续访问，最高价套餐对系统压力最大，所以取最小的一步保证尽可能广的访问；其他套餐和 API 不受影响，正在尽快扩容。

为什么值得关注：算力紧张已经从"排队慢"进化到"停止收钱"，这是模型供需失衡最直白的证据。
https://x.com/thsottiaux/status/2098113585683808624

## Aaron Levie（Box CEO）

本周走访银行、媒体、信息服务、保险、咨询的几十位技术负责人后的企业 agent 现状清单（220 赞），七条：安全，所有人都在担心 AI 带来的漏洞增速和 OpenAI 与 Hugging Face 事件，但态度务实而非硅谷式存在主义；模型混战，多数公司同时部署多个前沿模型、难以标准化，open weights 在企业里仍处婴儿期，缺"本土前沿"开源选项；agent 安全与身份，agent 想进每一个系统，企业还没法给所有 agent 配身份并控制其行为，而有时 agent 又必须完全以用户身份行动；流程再造，真正 ROI 来自改流程本身而不是把 agent 叠在旧流程上，最佳实践是嵌入式 FDE；架构的无情替换，过去一两年里换供应商好几轮，"试了 X 不行就换 Y"比以往任何时候都多；evals，企业对自身工作流怎么运转、AI 干得如何几乎没把握，是当下最大的机会；遗留系统，数据散落在为人类而非 agentic 世界建的旧平台上。

为什么值得关注：七条里至少四条（agent 身份、流程再造、evals、遗留数据）直接就是自研 agent 引擎必须解的问题，这是目前最具体的一份企业落地现状。
https://x.com/levie/status/2098218284139311615

## Madhu Guru（Meta AI 高级总监，前 Google 主导 Gemini 与 Veo）

"如何做好 evals"第 10 篇：测步骤，不要只测结果（133 赞）。两条 agent 轨迹可能给出同一个正确答案，但一条查对来源、检索对文档、4 次干净的工具调用就完成计算，另一条调了 17 次、同一个东西搜了 3 遍、从 2 个错误里恢复才勉强到达，高下立判。做法四步：1 定义整条工作流；2 定义每一步的任务；3 想清楚每一步怎么测（单独 eval 还是某个大 eval 的一个切片）；4 定义中位任务和困难任务并反映进 eval。看结果时先看步骤、再看最终结果。

为什么值得关注：agent 评测最容易踩的坑就是只看最终答案，这是可以直接落地的 trajectory 级评测方法论。
https://x.com/realmadhuguru/status/2098064969464217720

## Guillermo Rauch（Vercel CEO）

Vercel 每天约 1000 万次部署，累计 23.5 亿次，是全球多租户程度最高的系统之一；CDN 底下是一个几百毫秒内全球同步的元数据存储。他们把系统 p99 提速了 91%，同时还在承受 agentic 部署暴增带来的压力（509 赞）。

为什么值得关注：agent 正在把部署量推到基础设施质量的新极限，"每个 agent 一台计算机、每个区域都有"是下一代 infra 的真实负载画像。
https://x.com/rauchg/status/2098091056302833837
https://x.com/rauchg/status/2098158541932794222

## Zara Zhang（builder）

"为什么 computer use 还是慢得让人抓狂？？"（49 条回复，80 赞）。一句话就是当下 agent 工具链最真实的体感痛点，评论区值得翻。
https://x.com/zarazhangrui/status/2098136119154254287

## Thariq（Anthropic，Claude Code）

一个可直接抄的 prompt（1774 赞）：让 Claude 用自由文本深入采访你（需要多选时用 askuserquestion 工具），把你生活里它还不知道的相关部分问出来，全部存进 memory。

为什么值得关注：context 与 memory 工程的一个现成模式，比手写"关于我"文档效果好得多。
https://x.com/trq212/status/2098157600361861579

## Peter Steinberger（OpenClaw 与 OpenAI）

"复制逻辑不再痛苦了，抽象仍然是。"（2293 赞）另一条说 Astra 的需求涨得太快，赶紧上车。

为什么值得关注：写代码的边际成本塌下来之后，真正的成本项从"重复"转移到了"抽象"，这句话概括了 agentic coding 带来的架构取舍变化。
https://x.com/steipete/status/2098089196800098798
https://x.com/steipete/status/2098088917782413740

## Amjad Masad（Replit CEO）

AI 的风险很多，比如网络安全他就很担心。但"灭绝风险"，也就是字面上 100% 人类死亡，完全不在此列（516 赞）。

为什么值得关注：一线创业者对 AI 安全叙事的公开反驳，这类分歧本周在社区里被反复引用和争论。
https://x.com/amasad/status/2098171265924116732

## 其他简讯

Josh Woodward（Google，Gemini 与 Google Labs 副总裁）：Gemini 上 Windows 了（459 赞）。https://x.com/joshwoodward/status/2098131750660772342

Google Labs：Dreambeans 向全美 18 岁以上用户免费开放 iOS 与 Android，并可连接 Gemini app，用你跟 Gemini 的聊天理解生成更个性化的每日故事。https://x.com/GoogleLabs/status/2098110018289803558

Claude 官方：Fable 5.1 Build Days 从 9 月 11 日到 25 日在全球多城办 buildathon（2687 赞）。https://x.com/claudeai/status/2098138736642933143

Peter Yang（AI 教程作者）："干活的话 Sol 比 Astra 强"（401 赞，67 条回复）。https://x.com/petergyang/status/2098215935467544604

Aditya Agarwal（SPC 普通合伙人，Dropbox 前 CTO）：如果有一台机器只能做一件事，找到我们最紧迫疾病的解药，你愿意投入多少 GDP？他的答案是"非常高"。这就是我们现在所处的世界。https://x.com/adityaag/status/2098112281267843264

# 二、播客

## The MAD Podcast with Matt Turck：When AI Improves Itself，嘉宾 Richard Socher（Recursive）

核心结论：任何能被模拟的东西，AI 都会解决，而人类距离任何一种智能的真实上界都还差得远。

Richard Socher 是 AI 领域被引用最多的研究者之一，前 Salesforce 首席科学家，刚为 Recursive 融到约 6.7 亿美元，其中约 4.1 亿直接签给了一个亚马逊算力交易。他的新书 The Eureka Machine 在 9 月 22 日出版。

他先讲了一个反直觉的判断：科学进展其实在变慢。知识从一个"知识体"膨胀成一座"迷宫"，三万多种期刊就像挂满"禁止入内"的牌子，每个细分领域都要花多年才能深入，文艺复兴式的通才已经不可能存在。破局的办法是让 AI 把碎片重新缝回系统层面。

他划出 AI 必然超越人类的那条线：只要一个领域既能模拟又能验证，AI 就会攻克它。围棋、数学、编程都在其中，编程是最强的一类，因为可以无限生成"你看，结果对不对"的验证。生物学是下一个，方向是把生物学从"阅读"变成"写作"：他 2018 年训练了最早的蛋白质语言模型 ProGen，一作 Ali Madani 后来创办 Profluent，已与礼来签下数十亿美元合同，做出了比 CRISPR-Cas9 更精准的基因编辑蛋白。

一个非常反直觉的观点是幻觉。他说要探索全新蛋白质，你需要的恰恰是"合理地跑到分布之外"的能力，幻觉在某些场景是 feature 不是 bug，历史上不少科学家也是在半幻觉的状态下做出发现。当然查事实的时候得接搜索引擎。

他也明确不相信"硬起飞"，因为医学等现实约束需要时间；但变化是真实的：过去一家药企花 8 到 10 年才拿到一个分子药进 III 期，现在 6 到 18 个月就能让多个药物进 II 期后期，上市时带着八个以上的药。

他把整个框架叫 Eureka Machine，四根支柱：LLM 吞下人类知识；现实的测量数据（人看不到引力波和伽马射线，但机器能测）；模拟，比如虚拟细胞；真实世界的机器人实验。四根支柱上面再叠一层 agent swarm，像科学共同体一样并行探索大量方向再重组。Recursive 的执行顺序是先做"AI for AI"，让模型达到"五万个博士的知识量"，再去打物理、化学、生物；他们已经展示过生成的 CUDA kernel 能大幅加速推理，也在很窄的领域里超越了人类数月甚至数年的工作。

关于智能的定义，他给出预测、行动、目标三个主成分，并把智能拆成十个空间分别研究。他的结论是："我们离任何一种智能空间的真实上界，都还差得非常远。"
https://www.youtube.com/@DataDrivenNYC/videos

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
