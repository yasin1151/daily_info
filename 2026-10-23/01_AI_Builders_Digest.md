
**AI Builders Digest — 2026年10月23日**

数据源: 17 位 builder / 36 条推文 / 1 期播客（feed 生成于 10-22，新鲜）

---

## 一、今天最值得看的三件事

**1. Anthropic 发布 Claude Duet:常驻型个人 agent,不再等你开口**

Claude 官方账号连发三条,把定位讲得很清楚:它不是聊天框,而是一个独立的 app(iOS / Android / Web),有自己的频道(channel)分区、待办列表、文档与幻灯片编辑能力。核心变化是 **主动性**——它会自己发现"有活儿该干",然后在你开口之前动手。底层跑 Claude Opus 5.5,并且直接继承你 Claude 账号里的 memory、skills 和已连接应用,基本零配置。安全上做了三件事:永远不直接看到你的密码、新增分类器拦截敏感信息外泄、关键决策仍留给人。

目前是 early research preview,美区 Pro / Max 走 waitlist,官方自己承认"还会误判什么算紧急"。

Claude Code 团队的 Cat Wu 补充了产品动机:"我们听到反馈说,你们希望 Claude 主动多分担一点"。

Dan Shipper(《Every》CEO)做了两周实测,评价是目前为止第一个他愿意称为"专业工具"的个人 agent:他从主要用 ChatGPT 变成 ChatGPT / Claude 大约五五开,这是他近一年来在 Anthropic 上花时间最多的一次。他列出的短板也很具体——**它还不是 chief of staff**,能看到你电脑上的 Claude 会话但不能指挥它们;邮件草稿比 OpenAI 的 dot 差;语音只支持转写,不能真正对话。

为什么值得关注:这是"agent 从被动工具变成主动同事"的第一个大厂正式产品化尝试,而且它把竞争焦点从模型能力挪到了**上下文接管程度**(memory + skills + 连接应用)。对自研 agent 工具链的直接启示是:渠道化分区 + 待办 + 主动触发,这套结构正在成为产品共识。

https://x.com/claudeai/status/2112984666437546104
https://x.com/claudeai/status/2112984669943968099
https://x.com/_catwu/status/2112988751576330487
https://x.com/danshipper/status/2112997559463506059

---

**2. 一个 PHP 漏洞 + 一个 Node.js RCE:AI 找到漏洞,基础设施连夜补**

本周最大的一条技术新闻，Peter Steinberger（OpenClaw 作者,现于 OpenAI）单条 11229 赞:**"那个这周要搞出大乱子的 PHP 漏洞,是被 GPT-5.6 Sol 找出来的。"**

Vercel CEO Guillermo Rauch 从防守侧给了过程细节:行业在漏洞公开前数周就通过一个 Slack 频道协同,Vercel 提前在 Firewall 层上线缓解措施,**早于官方补丁发布**,所有部署的流量自动受保护;还成功拦截了针对 PHP 源的攻击尝试。同一天他又发了一条:Vercel 已为当天的 **Node.js RCE 漏洞**做了防火墙级缓解,并在滚动升级托管运行时。他的结语是"假设还有更多漏洞在路上,把 patch → redeploy 这块肌肉练起来"。

Dropbox 前 CTO Aditya Agarwal 的反应很直白:"Fucking PHP。It's always fucking PHP。"

为什么值得关注:这不只是安全新闻,而是 agent 能力的压力测试——AI 在找漏洞上的杠杆,和 AI 在补漏洞上的杠杆是同一个。Vercel 的做法(提前 WAF 缓解、不等官方补丁)可能会变成基础设施厂商的标准动作。

https://x.com/steipete/status/2112913060709228764
https://x.com/rauchg/status/2113050053724221732
https://x.com/rauchg/status/2112989629536440400
https://x.com/adityaag/status/2112977865432240524

---

**3. Vercel Token Pass 接入 DeepSeek v4.1 Flash,明确定位是"跑 subagent 的便宜模型"**

Guillermo Rauch:"DeepSeek v4.1 Flash (1017) 现已包含在 Vercel Token Pass 里。快、便宜到离谱、零数据保留(ZDR)。**它是跑 subagent 的绝佳模型——让便宜的模型去执行贵模型想出来的计划。你可以把 TypeScript 移植到 Rust 十遍都不会用完额度。**"

为什么值得关注:这是把"贵模型规划 + 便宜模型执行"的分层架构,从社区玩法变成了平台方的官方卖点。如果你在做自研引擎或 agent 工具链,这句话基本就是成本模型的结论:规划层贵一点没关系,执行层必须是每百万 token 几毛钱的模型,而且要能横向开几十个。

https://x.com/rauchg/status/2113010010766913815

---

## 二、X / 推特

**OpenAI Codex 团队的额度口径**

Thibault Sottiaux(Codex & ChatGPT @ OpenAI)连发两条,一条只有三个词 **"Dot, Dotter, Dottest"**(3981 赞),另一条紧接着说"**完全包含在 Pro 计划内,不占用你的每周用量额度**"(1840 赞)。两条没有明说指的是哪个功能,但从上下文(以及 Dan Shipper 提到 OpenAI 的 dot 产品)看,是对某项 Pro 内含能力的额度说明。如果你在用 Codex,这条意味着 Pro 档的一部分用量被"豁免"了周配额——具体以官方公告为准。

https://x.com/thsottiaux/status/2113029655095836957
https://x.com/thsottiaux/status/2113029854417600834

**Box CEO Aaron Levie:网络安全会成为 AI 创造就业的最大领域,而且会烧掉 100 倍的 token**

他连发两条,逻辑链很完整:我们现在有一支不知疲倦的劳动力,可以追查、发现、修补或攻击任何存在过的系统和软件。防守方用 agent 找历史遗留风险,攻击方用 agent 加速找缺口,防守方再用 agent 拦截并发现异常模式。"**我们在这个循环上烧掉的 token,大概是我们现在能想象的 100 倍**,因为我们可以扫描每一条日志、看每一行代码、过一遍流量,以过去不可想象的规模处理数据。"

他特别强调就业方向:即使工作变得更 agentic、更自动化,**你仍然需要更多人来把 agent 指向最关键的工作、审阅发现、打补丁、响应事件**。所以"想知道 AI 会造出哪些岗位,看网络安全就够了"。

https://x.com/levie/status/2112964214818283917
https://x.com/levie/status/2113137032633757773

**Replit CEO Amjad Masad:prompt → corporation**

只有一句"prompt -> corporation"，但概念密度很高——把"写一个 prompt 生成一家公司"当成终局形态的隐喻。配合 Replit 最近的方向,值得留意他下一步要发布什么。

https://x.com/amasad/status/2112975002027147545

**SPC 合伙人 Aditya Agarwal:做东西比用东西更好玩,而这可能是所有人的新红利**

他观察儿子看完《星球大战》三小时后,花了二十小时做关于自己看到内容的游戏,**但只玩了一小会儿——他更感兴趣的是做游戏本身**。作为程序员他本来就懂这种快乐,也一直为无法体验这种快乐的人感到遗憾。"但也许现在每个人都能体验到了?"

这是一条少见的、从动机层面解释 AI 编程工具价值的观察:它卖的不是效率,是**创造的入口**。

https://x.com/adityaag/status/2112923959176106056

**FirstMark Capital 的 Matt Turck:一天之内两个大 round**

Pigment 2.5 亿美元 E 轮、Legora 5.5 亿美元 E 轮,他称之为"有意思的一周"。他的判断:"在 token、API 和 agent 的时代,世界正在转向持续性的财务规划。"——企业软件的形态在被 agent 重写。

https://x.com/mattturck/status/2113026098669777365

**其余速记(信息量较低,仅备案)**

- Zara Zhang:做了个"一张照片变 3D 立体贺卡"的 demo(284 赞),并抛出一句"个人网站是新简历"。https://x.com/zarazhangrui/status/2113055591954526444
- Google Labs:Dreambeans 系列第二期,主题之一是"如果 app 被设计成让你离开手机"。https://x.com/GoogleLabs/status/2112968628861878648
- Peter Yang:正在用 AI 帮忙把所有账号的安全设置全部加固一遍,并终于付费买了 1Password——和上面那条 PHP 漏洞是同一天的应激反应。https://x.com/petergyang/status/2113122021567848450

---

## 三、播客

**《AI & I》by Every — How a Frontier Team Can Help Your Company Keep Up With AI**

**一句话结论:当每个人都在"把活干完"和"跟上 AI"之间二选一时,解法不是让人更努力,而是把这两件事拆给两拨人干。**

这一期是 Every 把自己内部的"前沿小组(Frontier team)"整个拆开给人看:六个人分别讲自己那一片,是目前少见的、带有真实操作细节的组织方法论,而不是抽象战略。

**为什么需要这个小组**:Every CEO Dan Shipper 的描述很准——要么你忽略前沿,直到某个 agent-native 版本的你的产品把你颠覆;要么你天天追新玩具,最后一件事都没做成。Frontier team 的作用就是做"关注点分离":一拨人专门追前沿,其余人专心交付。

**两种人必须配对**:Dan 的搭档 Natalia 提出"海盗与建筑师"。海盗(比如她自己)只想跑得飞快,两天里试一万件事,大部分是垃圾但能试出有用的;建筑师擅长看着一堆烂摊子说"这个我们维护不了,对内部五种使用场景都不成立",然后把它压成一个能长期跑的系统。关键机制是:**实验大多数被丢掉,少数在推向全公司之前,必须先过建筑师这一道**,否则就是一堆无法维护的 vibe-coded 项目。

**岗位是造出来的,不是发出来的**:Mike Taylor 给自己起的 title 是 "head of evals"。他的工作是把团队的 qualitative vibe check 变成有数字的东西——"我们说一个模型 sycophantic(谄媚),到底指什么?能不能测?"他给每个人建**个人基准集(personal benchmark)**:把你自己的真实工作存成一小份样本,让模型反复在上面跑。他本人最兴奋的用法是用 Opus 剪视频:让它翻遍所有 Slack 消息和会议记录,把叙事线拉出来并**带出处(receipts)**——每一句结论都能点回是哪次会议说的,全程可审计;然后自动配上截图标注和 Gemini 生成的旁白。

**他的两条"cheat sheet"值得单独抄下来**:
1. **大家给 AI 的上下文还远远不够**。"我今年早些时候也是那种人,没让它接 Gmail 和 Slack。现在我是完全放开的——一旦你给它访问权限,它挑出好上下文的能力好得惊人,你也可以更信任它自己做判断。"
2. **保护别人的注意力,现在成了你的工作**。"我经常被同事说在污染公司频道,满屏都是 Mike。生产得越多,你就越有义务让别人能消化。"

**记 token 账这件事,他们真的做了产品**:运营负责人 Arielle Shipper 的 title 是 "Frontier Wrangler"。她做了个用量看板:扫遍每个人电脑上所有 harness 的 token 消耗,实时采集**模型和 effort level**,再自动把所有 session 按工作类别归类、跑一遍给你审批,最后算出每类工作的 token 占比和估算美元成本。判断标准就一句:"这笔钱值不值?"

**两个具体的 agent 工程实践**:
- Every 的工程师 Jannik 展示了他的编排器 "Minga":你只跟一个 orchestrator 对话,说清需求和 tech stack,它拆成带依赖关系的任务计划,在后台自主执行,需要决策时才 ping 你,给你看 UI 草稿收反馈再继续。他下一步要试的是**多人共享上下文**——海盗和建筑师同时在一个项目里干活,不用交接。
- 高级编辑 Jack Cheng 嫌浏览器标签页太耗注意力,**直接给自己写了个无标签页浏览器**,还内置了一个 agent 面板可以任选模型做编辑,以及"偷看一眼"模式——临时开页查完就回到文档。他的结论很锋利:插件和扩展从来没法真正改动应用本身的工作方式,但这一代前沿模型让"为我自己重写这个应用"变得可行。

**给其他公司做前沿小组的人的唯一建议**(来自 Kieran):**做一些能留下来的东西**。"你做一百个实验却不落地、不整合,就没用。别把一百个实验一股脑倒进频道里,那是把整个组织淹没掉的最快方式。自由探索是你的权利,但整合才是你的工作。"

节目链接(该 feed 提供的是播放列表地址):
https://www.youtube.com/playlist?list=PLuMcoKK9mKgHtW_o9h5sGO2vXrffKHwJL

---

## 四、串起来看

今天的内容其实在讲同一件事的两面:**agent 的瓶颈已经从"能力"挪到"上下文和注意力"**。Claude Duet 卖的是接管你的上下文、主动替你判断优先级;Every 的前沿小组把"给模型全部上下文"列为第一条建议,同时把"保护别人的注意力"列为第二条;Jack 写无标签浏览器,也是为了同一个东西。而 Levie 说的 100 倍 token、Rauchg 说的拿便宜模型跑 subagent,则是这个趋势的成本答案。

---

*Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders*
