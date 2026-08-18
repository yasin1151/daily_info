
数据齐了:14 位 builder / 30 条推文 + No Priors 播客(46K 字转录,已通读)。筛选掉低价值内容后直接组稿。

---

# AI Builders Digest — 2026-08-19

数据新鲜度:feed 生成于 8/18 15:00 (CST),内容为 8/17-8/18 的发言。本期聚焦:Agent 工具链、编码 Agent 产品动向、模型/算力格局、以及与自研引擎/创意工作流相关的观点。

## X / Twitter

**Swyx (Latent Space / smol.ai 主理人)** — 转述 Trajectory 在 Continual Learning 赛道的分享:持续学习的数据问题正被系统性解决,但 **GRPO 已不够用,他们被迫转向 on-policy,再逐一修复随之而来的一堆问题**。Swyx 称 Trajectory 是"这个领域早期领导者之一",并提示该赛道其他分享也值得看。对关注 RL/持续学习路线的人是个信号:社区对 on-policy 的依赖正在加深。
https://x.com/swyx/status/2089393073327653344

**Josh Woodward (Google VP,负责 Gemini/Google Labs)** — 回应用户反馈,给出 Gemini 体验改进路线图:重做的 Workspace tools 将在 1-2 周内测试;**3.7 Flash 工具调用能力改进中**(对 Agent 工具链直接相关);新 "Projects" 设计已完成、进入实现;已支持 49 个 connectors。多项 backlog 已清零。Google 正在明显加速 Agent 侧基建的收尾。
https://x.com/joshwoodward/status/2089520767281324112

**Boris Cherny (Anthropic, Claude Code)** — Claude Code 发布一批"小而美的体验改进",称"这类改动积累起来很可观",并向社区征集反馈(两条推文 678+739 赞)。内容为产品迭代常规动作,但可视为 Claude Code 在打磨细节体验的信号。
https://x.com/bcherny/status/2089537919795212565

**Thibault Sottiaux (OpenAI,Codex & ChatGPT 负责人)** — 抛出一个高互动问题:"**Codex、API 或我们的模型,有什么显而易见该做、却一直没做的事?**" 3700+ 赞、4700+ 回复,基本是 Codex 用户的一次大规模需求征集。社区最想要什么,直接看评论区即可,值得持续跟进(对自研 Agent 工具链的取舍也有参考价值)。
https://x.com/thsottiaux/status/2089500941842342287

**Madhu Guru (Meta AI 高级总监,曾领导 Google Gemini/Veo/Nano Banana)** — 分享做 evals 的实操方法论:挑一个你熟到不行的工作流,先让"质量"可度量;研究真实 traces(典型用户的 prompt 序列、每一步的合格输出长什么样);把产品失败点——混乱的 tool call、缺失的上下文——固化成 traces;再考虑如何自动化、反复跑,并持续让 eval 对齐线上流量变化。做 Agent 产品的人可以直接抄作业。
https://x.com/realmadhuguru/status/2089480958571331623

**Thariq (Anthropic, Claude Code)** — 两条都值得看:
- 在 Claude Code 里输入 `/design <想设计的东西>` 即可直接做设计(880 赞,新能力曝光);
- 观点更新:最近的程序化生成艺术、视频编辑和 3D 游戏 demo,让他**越来越认为 LLM 编码模型在大量创意工作上会强于 diffusion 模型**——因为代码更容易编辑、微调,且能导出到现有工具链。这条与自研引擎/创意工作流直接相关,值得留意 LLM 生成资产进入游戏管线的趋势。
https://x.com/trq212/status/2089529798850969805
https://x.com/trq212/status/2089415712007938315

**Amjad Masad (Replit CEO)** — 转述一家"pitch 里完全没有 AI 字眼、却有 AI 级增速"的团队:"如果他们不是这么 AI 重度化,需要 10 倍的人力"——AI-native 团队的结构性优势再次被量化。另一条:光扫描代码漏洞不够,**要真正用渗透测试去攻破自己的系统**。
https://x.com/amasad/status/2089525819567739264
https://x.com/amasad/status/2089435606338416884

**Guillermo Rauch (Vercel CEO)** — **Cursor Origin 现在可直接托管 repo,并一键部署到 Vercel**(而 Cursor Origin 本身也跑在 Vercel 上);顺手调侃"不像 GitHub,它是在线可用的"(暗指 GitHub 近期宕机)。3600 赞。编码 Agent 厂商开始自建代码托管 + 部署闭环,对 GitHub 的生态位是直接挤压。
https://x.com/rauchg/status/2089409162270965858

**Aaron Levie (Box CEO)** — "数据是新石油"的具象化:AI 对数据的饥渴让信息几乎以任何形态都变得值钱,数据交易正在发生,**信息将作为资产进入公司资产负债表**;未来公司管理、挖掘组织智能的方式,将决定竞争力和价值创造。企业数据资产的重新定价正在成为显学。
https://x.com/levie/status/2089499887905997272

**Garry Tan (YC CEO)** — 开源他的 "Personal AGI" 方案:一个私有 GitHub repo,内含 **70 个他验证过的 skills + Karpathy 式个人知识 wiki 起步包**,MIT 协议、免费,可直接配合现有 Claude Code 或 Codex 订阅使用(贴图给 CC/Codex 即可自动搭建)。对搭个人 Agent 工具链的人是现成模板。
https://x.com/garrytan/status/2089438298540519821

**Nikunj Kothari (FPV Ventures 合伙人)** — 病毒式吐槽(1483 赞):"模型没有护城河(OpenAI/Anthropic/xAI),IDE 没有(Cursor/Windsurf),harness 没有(Cognition/Factory/LangChain),应用搭建没有(Replit/Lovable/Bolt),wrapper 没有(Harvey/Abridge),推理层没有(Together/Fireworks/Groq),语音层没有(Sierra/Decagon/ElevenLabs),数据标注没有(Scale/Surge/Mercor),AI 基建没有(Baseten/Modal/Railway),neocloud 没有(CoreWeave/Lambda/Crusoe),生成式媒体没有(Runway/Suno)……**AI 圈谁都没有护城河,除了风投公司**"。另一条观点:如果 agent 成为多数产品的主要用户,人类注意力愈发稀缺,**品牌营销将成为最关键的差异化资产**,未来十年这类人才会被聘为 cofounder 而不是被边缘化。
https://x.com/nikunj/status/2089486802356961364
https://x.com/nikunj/status/2089374392295842086

## Podcasts

**No Priors — Chasing Trillion-Dollar Companies, Founder Ambition, Token Budgets, and Regulatory Capture**(Sarah Guo 与 Elad Gil 对谈)

The Takeaway:过去 5 年三家万亿公司的诞生是罕见的"间断平衡"爆发,**未来 3-5 年很难再出现多家万亿公司**;与此同时,AI 实验室正处在 RSI(递归自我改进)前夜的狂躁期,而真正的约束是物理算力,不是算法可能性。

- **万亿公司是异常值**:OpenAI/Anthropic/SpaceX 五年内从零冲到万亿,但历史上 Google、SpaceX 都是 15-20 年的弧线;全球能支撑 500-1000 亿美元年收入流的市场只有十几个,未来五年能再孵化几家存疑——"上百亿美元的公司还有很多,万亿是另一个量级"。
- **创始人野心收缩**:Elad 观察到越来越多好创始人避开与实验室正面竞争,逃向硬件、"American Dynamism"和 AI 细分应用,显得过于谨慎——"我更常对创始人不够有野心感到失望"。
- **退出纪律**:Elad 建议每年固定开一次"是否在未来 6 个月考虑退出"的董事会讨论,非情绪化、预先排期;因为"AI 的一年相当于正常的 3-4 年",3 年就是十年。
- **RSI 时间线**:Elad 称实验室里"狂躁能量"巨大,"大约明年底会出现某种轻量级 RSI,模型开始自己训练模型的一部分,初期主要是 post-training"。Sarah 泼冷水:过去五年每隔 18 个月就有一批顶级科学家宣称 ASI 还有 18 个月,**真正的瓶颈是物理算力可得性**——而算力天花板反过来强化了寡头格局(实验室放缓研究员招聘,因为成本不是人,是分配给人的算力)。
- **监管俘获**:用核电类比——"法国 70% 电力来自核电,美国只有 18%,四十年没建过新堆。70 年代的安全游说扼杀了充裕的清洁能源。**安全真实地伤害过我们**。"(金句)结尾直接号召"对抗监管俘获";同时讨论加州 billionaire tax 与可能的 exit tax 会推动人才外流。

原视频(本期为双主持人专题,无嘉宾):
https://www.youtube.com/watch?v=6l8oAO_LBx4

---

**与自研引擎/Agent 工具链最相关的三条**:Thariq 的"LLM 编码模型在创意/3D 内容上优于 diffusion"判断、Codex 社区的需求征集(评论区即产品路线图)、以及 Cursor Origin 自建托管-部署闭环对现有 Git 工作流的冲击。
