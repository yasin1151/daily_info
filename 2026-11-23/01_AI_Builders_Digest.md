
AI Builders Digest — 2026-11-23

今天 12 位 builders / 23 条推文 / 1 期播客。主线只有一条：**AI 参与证明黎曼猜想**这件事，把"人到底还剩什么价值"重新点着了；另一条是 Codex 桌面端在密集迭代，agent 协作出现了新玩法。

---

## 一、黎曼猜想余波：争的不是数学，是"人的位置"

**Box CEO Aaron Levie** 写了今天最长的一段。他转的那段话说，这次证明不是传统意义的"建理论"，而是一个需要穿过 25,000 页既有基础设施、且与目标没有明显连接的"虫洞"——没有人类大脑能独立完成，但"目前也没有哪个 AI 能独立完成"。Levie 的推论是：过去解决问题最终受限于个人或团队能装下多少信息，AI 第一次把"人类上下文容量"和"产出能力"解耦了。他还补了一句很实在的：解法可能不再优雅，但数量会多得多。
https://x.com/levie/status/2124252844710887549

**前 Claude Code 团队成员 Thariq** 的反驳更值得记：我们太急着"把自己 disintermediate 掉"（把自己从流程里删掉），这对人和模型都是伤害。"模型越强，和模型协作的技能就越重要，而我至今没看到这项技能出现边际收益递减。"他的立场是：Claude 确实干了很多技术活，但"和模型一起推前沿"本身就是一门硬技术。
https://x.com/trq212/status/2124239684536840682

**FirstMark VC Matt Turck** 泼了盆冷水，也是今天最好笑的一条：所谓"不懂黎曼猜想但兴奋地发推"的艺术。
https://x.com/mattturck/status/2124239403107459490

**Every CEO Dan Shipper** 直接把某条技术悲观论调，和当年"专利局长说该发明的都发明完了"并列进名人堂。
https://x.com/danshipper/status/2124315217936945171

**为什么重要：** 这轮讨论的价值不在数学，而在于给出了新的能力坐标——"能装载多少上下文"不再是上限。对做自研引擎的人是直接信号：瓶颈从模型能力转向"如何组织人类与模型的分工"。

---

## 二、Coding agent / 工具链在动

**OpenAI 负责 Codex & ChatGPT 的 Thibault Sottiaux** 在问用户：昨天桌面端更新之后，还有哪里不对劲？"团队正在准备下一个大更新。"这条 2158 赞、1116 条回复，是当前反馈密度最高的一条。
https://x.com/thsottiaux/status/2124322968499282388

**AI 教程作者 Peter Yang** 给了个实用 tip：新版 ChatGPT 手机端默认看不到 codex 线程，要长按最右侧 tab 才能把 codex 钉到底部导航——"这一点都不直观"。他还建议左侧栏应该把本地最近的 codex 线程也列出来，不只是 chat 线程。
https://x.com/petergyang/status/2124217176655843483
https://x.com/petergyang/status/2124217179717648537

**Replit CEO Amjad Masad** 提了一个我认为今天最有工具链价值的现象：一个高中生在把 GTA6 重编译到 PC 上，更有意思的是他们**用 GitHub issues 来在 agent swarm 之间协调任务**。"开源的新模型？"
https://x.com/amasad/status/2124345037408686228

**为什么重要：** 多 agent 协作的协调层一直是硬骨头。拿 issue tracker 当共享黑板，等于把任务分发、状态、认领全部交给一个天然可审计、可回溯的系统——比自研调度协议成本低得多，值得在自己的 agent 工具链里认真试一次。

另外 Masad 提到 Replit Missions 做的 Amuse 已开源。
https://x.com/amasad/status/2124277564596519355

---

## 三、基础设施信任问题

**smol.ai / Cognition 的 swyx** 转发并追问：这些 provider 在背后偷偷 phoning home，"到底有没有任何善意的解释？因为 wtf"。250 赞、109 条回复，说明这事戳中了痛点。（原推引用的具体内容 feed 里没有，不做推测。）
https://x.com/swyx/status/2124147427313861009

**为什么重要：** 只要 agent 跑在别人的模型/工具链上，遥测就是不可控的攻击面。选型时"是否静默上报"应该和价格、延迟一起进评估表。

---

## 四、播客：Isomorphic Labs 总裁 Max Jaderberg — 把药物发现搬进计算机

No Priors｜Powering AI-Driven Drug Discovery
https://www.youtube.com/watch?v=IiKf3BgBezE

**一句话结论：** 制药业所有成本都堆在"只能在真人身上才看得见失败"这件事上，所以真正的杠杆不是把实验做快，而是让大部分实验根本不发生。

Jaderberg 是 Isomorphic Labs 总裁兼创始团队成员，此前在 DeepMind 做 AlphaGo / AlphaStar，2014 年把公司卖给 DeepMind。他的核心诊断：这行业一百年来是纯经验驱动的——试、测、再试。低垂的果子已摘完，剩下的是维度极高的组合问题，靠穷举筛不动。而失败几乎都发生在临床阶段："我们从来没能提前看见问题，直到把药打进病人身体，才发现，哦不，有我们没算到的毒性。"

最扎人的一段是他拿大鼠实验开刀：大鼠对人体临床毒性的预测率大约只有 30%。"如果我的 AI 科学家跑来跟我说，我们有个很棒的模型，预测率 30%，我会说，行吧，能不能再好一点。"

所以 Isomorphic 的 North Star 是"把药物设计全部搬上计算机"——内部所有排行榜都有一条虚线叫 experimental accuracy（实验精度）。他自己的总结："I wanna get out of the real world." 真实世界只用来验证，不用来学习和迭代。他也承认物理定律绕不过去：合成一个分子要等反应，养一株细胞要等天数。

**对做引擎的人，这个框架可以直接搬：** 把迭代循环关进仿真里，真实验证只留最后一步；把"实验精度"当唯一北极星指标，而不是"跑得快"。

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
