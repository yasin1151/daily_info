
AI Builders Digest — 2026-11-12

今日 15 位 builder / 32 条推文 + 1 期播客。主线很清晰：**模型换代进入实测阶段，Agent 的竞争重心从"能力"转到"接入面"**——MCP、连接器、官方集成谁在维护，开始直接影响采购决策。

---

## 一、模型与产品

**Google 的 Gemini 4 Carbon 正式向 Ultra 订阅者全球推送**
Google 副总裁 Josh Woodward 只发了一句"Right now, Gemini 4 Carbon is in the GeminiApp for Ultra subscribers worldwide"，没给 benchmark，也没给价格。
https://x.com/joshwoodward/status/2120186249281778135

同日最有信息量的是 Every CEO Dan Shipper 的 day-zero 实测（他在 Every 内部拿 coding / writing / design / knowledge work 全线跑了一遍）：

- 写代码明显变强：Senior Engineer benchmark 单次跑分 44%，上一版 Argon 只有 21%，但仍属中游。他同事把一整个 backlog 丢给它，它判断"6 个任务 ready"，实际做了 15 个，还顺手做了别人正在做的事，4.5 小时后被人工叫停。
- "它能在野心很大的项目上连续干几个小时，但它不知道自己什么时候该停。"
- 大工程：同事给了播客棚的 3D 扫描和设备清单，它一次就搭出可判断新设备会不会入镜的浏览器内模型；估计还写了内部视频剪辑器 Everycut 一次大更新的约 95%。
- 代码质量：大项目上的测试和文档（包括"考虑过但否决的方案"记录）受好评，但**容易产出超大文件，模块化不如 Fable**。
- 音视频能抓到别的模型漏掉的剪辑问题；设计上物体和 3D 场景更好，界面则团队分裂（有人一直拿到"box 里套 box"）。
- 写作与 Argon 基本持平，但**更贵**，他没找到切换理由。他的结论评级是"会用，但只是有时"。

https://x.com/danshipper/status/2120187507396530309

> 为什么值得关注：这是目前少见的、带具体分数和行为观察的对照评测。核心结论不是"更强了"，而是"自主性上来了、终止判断没跟上"——这正好是 Agent 产品层要补的那一环。

---

## 二、Agent 工具链：接入面成为竞争点

**Claude 一次性铺开四个产品面：Whiteboards、Sheets、Data、interactive connectors**
其中最有分量的是 interactive connectors：可以把 Adobe、Atlassian、Box 的**完整版本**开在 Claude 里，你手动改，或者让 Claude 和你一起改。Claude Data（原 Dashboards）在付费版 GA，能从指标里起草 data story 和带旁白的视频。
https://x.com/claudeai/status/2120206375137484875
https://x.com/claudeai/status/2120206372478566799
https://x.com/claudeai/status/2120206379315261702

**Box CEO Aaron Levie：与 Anthropic 打通 Box 内容的完整读写 MCP**
"Agents are going to work with enterprise files 100X more than people do today." 现在 Agent 不只能把内容拉进工作流，还能把文件更新写回 Box，并直接在 Claude 里查看——合同、演示、战略文档都能创建/编辑/更新，全走 MCP。
https://x.com/levie/status/2120261416733036905

> 为什么值得关注：连接器从"只读检索"走到"双向写入 + 内嵌完整应用"，这一步跨过去，Agent 才算真正接管企业文件而不是在旁边围观。对自研 Agent 工具链来说，权限模型（OAuth/RBAC）会成为比工具数量更硬的瓶颈——这一点在下面的播客里被讲透了。

**Aaron Levie 的"agent swarm"判断**
他把演进分成三段：chat（快，但被交互次数卡住）→ agent（把几小时到几天的工作压成几分钟）→ swarm（目标驱动、自己找路径，生产力上限不再天然存在）。适用边界是"价值可以在自包含数字环境里创造"的领域：游戏开发、编程、交易、生命科学研究、IT 自动化、安全、数学、动画。他特别点出机会在"harness、应用层产品和基础设施"，以及大量新的 FDE（前向部署工程）工作。
https://x.com/levie/status/2120385739342897469

---

## 三、Coding agents 与代码安全

**Vercel CEO Guillermo Rauch：Agent 一周修掉 1.4 万个漏洞**
Vercel Security Review 上线不到一周：识别 57,897 个漏洞，其中 6,029 个 critical/high，**14,665 个已被 Agent 自动修掉**。他自己的惊讶点有两个：一是"会有这么多严重漏洞被无视"，二是"Agent 修起来这么轻松"。任何 repo 都能开，不限于部署在 Vercel。
https://x.com/rauchg/status/2120188488628977819

**同一个人对语言的判断（对做引擎/工具链的人更相关）**
"Rust 是一门极好的语言和生态，尤其考虑到它是在 agentic coding 之前被发明出来的。有了 agent，新语言会大量涌现，甚至为特定场景专门造语言，也包括随意的 C，甚至 LLVM IR、汇编……AI 是流动的，不再有一刀切。"
https://x.com/rauchg/status/2120337388178379178

**Peter Steinberger：换成 GPT-6 Astra 重跑，又多出 3.5 万个漏洞**
他引用的一段报道：某机构对约 700 套系统做诊断，发现 10,500 个漏洞，开了紧急发布会，花了三个月修；随后用 OpenAI 最新发布的 GPT-6 Astra 重跑，**又确认 35,000 个新漏洞**。文中的原话是"Honestly, we're completely exhausted"。
https://x.com/steipete/status/2120228665946710248

> 为什么值得关注：这三条合起来说明一件事——模型能力提升正在把"存量技术债"变成可被批量发现、批量修复的对象。安全扫描类 Agent 可能是当下 ROI 最容易被量化的一类 agent 产品。

---

## 四、观点

**前 Claude Code 团队的 Thariq：少一点 one-shot 演示，多一点协作工具**
"we need fewer one shot demos and more tools that show how you can collaborate with models to bring your vision to life"（1590 赞，当天互动最高的一条之一）。批评的是那类"一句话生成完整应用"的展示型 demo。
https://x.com/trq212/status/2120223476279869875

**Cursor 设计师 Ryo Lu：反对各自养一支 Agent 军队**
"working together with other humans is where the magic happens, not each of us running our own army of agents in silos." 他另一条讲得更远：我们造软件不只是为了优化和完成任务，而是像电影人和音乐家那样，让人做到以前做不到的事。
https://x.com/ryolu_/status/2120337691661443081
https://x.com/ryolu_/status/2120380317429350654

**OpenAI Codex 团队的 Nan Yu：把语音输入的边角做对**
他披露了 dictation 的一个细节：可以映射 Apple 的听写键（F5 的特殊变体），并支持按住说话、双击、单击三种快捷键。评价是"很少有听写应用把这类边角做对"。
https://x.com/thenanyu/status/2120203450223104012

---

## 五、播客深读：Latent Space — Designing for Agents（Zeno Rocha, Resend）

这期主角是 Resend CEO Zeno Rocha，但真正的题目是**"为什么 Agent 总选它"**——Swyx 开场就承认自己是被这个现象勾住的："I finally asked Zeno, why tf my agents keep choosing Resend even when I don't want them to."

**规模事实**：Resend 现在服务 430 万用户（当天早上数字）、12 万付费客户，客户里有 Warner Brothers、HBO。NPM SDK 下载量今年反超 SendGrid，现在是它的两倍多。

**AEO 是硬做出来的，不是撞上的**
- 早期 SEO 完全打不过做了十年 SEO 的 Twilio/Postmark/Mailgun，于是转向长尾 docs 和"几乎每页都放 FAQ"，按 ask-and-answer 的格式写。
- 全套 llms.txt：docs 有，营销页也有；**每个页面都能在 URL 后加 `.md` 拿到 markdown 版本**（也支持 content negotiation）。
- 一个具体因果链：某个周日他让模型比较各家用 120 万封邮件的报价，模型把 Resend 说成"定价非常不透明"，还说得很差。原因是"agents don't really drag a JavaScript widget"——价格计算器是 JS 组件，Agent 根本不会执行。他做了 pricing 页的 `.md` 版，几天后再问，数字就对了。
- 对比页、迁移页同理：**所有数据都用文字再写一遍**，因为 Agent 不跑 JS。
- 他对 AEO 的判断很克制：那些 AEO 工具（他自己订了四家，包括 Profound、Gauge）"基本只是报表工具，不会告诉你该做什么"；老派 SEO 工具反而更有主张。他自己搭了 AEO tracker，并且挂了一套自动研究循环：Latent Space 和 AIE 各有一个 CMO agent，会再 spawn 其他 agent 做研究、记录试过的实验，他签字后才跑实验，再由另一批 agent 监控。

**MCP 的实战数据（这一段对做 Agent 工具链的人最有用）**
- "几个月前所有人都在说 MCP 死了，唯一重要的是 CLI。"结果 Resend 的 MCP 调用量每月至少 2 倍增长，8 月到 120 万次。
- 他们的第一个 MCP 是投资人 a16z 的 Yoko 写的本地版；要做 remote MCP 时被迫回头重建整个权限模型——先补 OAuth，再补 RBAC，然后才是分发（进各家的官方插件/连接器商店，"talking to the labs" 比写代码难）。
- 工具数量：上线时约 20 个，现在 80 多个。他明确站在 Cloudflare 那种"只给 search + execute 两个工具"的反面。"工具太多模型会混乱"这个担忧他说现在基本看不到了。
- 真正的难点不是 90%，而是最后 10%：usage、billing、团队邀请、账号开通、删除——这些要不要暴露成工具？"这是很难的问题。"
- 一个反直觉的采购结论：**"如果这个 MCP 不是厂商自己维护的，我就不信任它。"** 他因此把一个用着 Sentry 写的 MCP 的分析工具（Plausible）换成了有官方 MCP 的 PostHog；跑步数据也因为 Strava 官方有 MCP 而选了 Strava。"如果不在那儿（官方连接器里），我就不用。"

**架构上两个可迁移的判断**
- 他批评 Next.js/server components 的最大问题是"让你很容易永远不暴露公共 API"——数据直接绑在页面上。正确做法是后端彻底 headless，前端只是众多 client 之一。Resend 早期 API 跑在 Next 上，账单太高才迁到常规 Node 服务，dashboard 一直当私有 API 复用同一套。
- 发送链路已经从 JavaScript 换成 Go。"现在语言不重要了，选个问题，把整块用快的语言重写一遍就行。"他自己在跑 Rust 项目，"理论上知道点 Rust，从来没认真学过"。

**即将推出的方向**：Agent 读邮件。他已经在做"程序化创建几十个 inbox，以及这些 inbox 怎么被 Agent 访问"——inbound 之上的读/标未读/加星/打标签 API，产品很快发。

**一句商业侧的提醒**：他承认 Resend 目前是"品类统治"而不是"品类创造"。品类创造的标准是——听到那两个词，你就不想要别的东西，不需要长文宣言。他还点名 Dharmesh Shah 的 inbound vs outbound 是范本。

播客链接（本期节目页在频道下，JSON 未提供单集 watch 链接）：
https://www.youtube.com/@LatentSpacePod

---

**一句话收束**：这一天的信号是同向的——Claude 把第三方应用搬进对话框，Box 把文件写权限交给 Agent，Resend 用 llms.txt / 官方 MCP / 纯文本数据把自己做成"Agent 默认选项"。竞争已经不是谁模型更强，而是**谁被 Agent 正确地读到、并信任地调用**。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
