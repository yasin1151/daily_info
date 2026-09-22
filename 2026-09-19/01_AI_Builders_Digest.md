
Fresh feed from 2026-09-18, 15 builders / 25 tweets, no podcast or blog items. Composing the digest now.

AI Builders Digest — 2026年9月19日

（数据源：2026-09-18 抓取，25 条推文 / 15 位 builder；今日无新播客与官方博客）

---

## 头条：Anthropic 用「Projects」重写 Claude Code 的会话模型

今天是 Claude Code 的一次架构级动作，Anthropic 一方四位同时发声，信号非常密集。

**Claude Code 负责人 Boris Cherny（bcherny on X）**：Projects 改变的不仅是他和 Claude 的交互方式，还有他写代码的方式。他不再管理 session——想到什么就直接发过去，Claude 把它拆成 threads，而 project 记住了他的工作习惯。他说现在很大一部分编码都在这里完成，并贴出了自己昨天在 Claude Code CLI 里的真实 prompt 作为佐证。（2352 赞）
https://x.com/bcherny/status/2100669598995816511

**Anthropic 的 Cat Wu（_catwu on X）**：新的 Projects 体验里，Claude 负责协调你所有的 session。她说自己每天都在用，因为「可以在更高的抽象层操作」——一次抛出一批任务就去做别的；Claude 对她在做的所有事都有上下文，随时能给聚合状态更新；还带长期记忆，随使用演进。未来几周逐步放量。（356 赞）
https://x.com/_catwu/status/2100641163120423057

**Claude Code 团队的 Thariq（trq212 on X）**：一句话点出架构本质——Projects 把 Claude Tag 的架构搬进了 Claude Code：每个 project 一个 agent，负责管理记忆，并派生 subagents 去执行任务；你可以要求它主动行动、按计划做事。他的评价是「比一堆 session 舒服得多」。（1041 赞）
https://x.com/trq212/status/2100638355872706571

**Claude 官方账号**的技术细节（同一线程三条）：threads 在云端运行，电脑离线也继续跑，但目前还不能访问你本地电脑或内网的文件与工具，本地支持「很快到」；project 是随时间累积的，每个 thread 都往共享记忆里写入和读取（比如记住 release 挪到了周五、动 billing 服务前该先问谁）；project 的 library 保存你添加的文件以及 Claude 创建的文件。Pro/Max 上已有的 projects 照旧运行，随放量逐步升级。
https://x.com/claudeai/status/2100632687316730327
https://x.com/claudeai/status/2100632684074549309
https://x.com/claudeai/status/2100632688625348890

**为什么值得关注**：这是「多 session 聊天」向「常驻 agent + 记忆 + 子任务编排」的正式转向。对自研 agent 工具链而言，三个设计点可以直接抄：memory 由 project 层统一持有而非 session 层；主 agent 只做协调与派发；云端执行 + 本地能力后置。Anthropic 自己也承认本地文件访问还没打通，这恰好是第三方工具链的窗口期。

---

## Google Labs 发布家庭向 agent「CC」（539 赞）

CC 是 Google Labs 新的 AI agent，定位很具体：帮家庭把时间从后勤琐事里省出来。能力包括：一个 CC agent 最多加 5 名成员；早晨用共享的 "Your Day Ahead" 简报邮件开场；自动把日程与待办同步进共享的 Google Calendar 和 Tasks；在 Google Chat 里和 CC 协调、把任务甩给它（例如做每周餐单、列开学文具清单）；按你的指示代办文书（许可单、各种表格）；以及区分记忆——哪些信息对全家适用（家庭购物清单、常去餐厅），哪些只对某个人适用（饮食限制、本地时区）。目前美国 18+ 可加 waitlist。
https://x.com/GoogleLabs/status/2100653821907366366

**为什么值得关注**：多用户共享记忆 + 权限颗粒度，是 agent 从「个人助手」走向「组织/家庭级」的必经问题。CC 把「谁是信息主体」当作一等公民，这个建模方式比单纯堆功能更值得借鉴。

---

## Vercel CEO Guillermo Rauch：软件产量的拐点与 1 秒部署（508 赞）

他的判断是：明年产生的软件很可能超过计算史上所有软件的总和。佐证来自自家数据——Vercel 用 10 年做到 10 亿次部署，而过去 10 个月又加了 14 亿次。增量里有一部分是极小、个人化甚至一次性的软件（带点 javascript 的 HTML 文件，他称之 "artifacts"，以及报告、定价计算器、幻灯片），另一头则一路延伸到复杂 app、agent 和平台。他称部署速度是团队的执念：把部署、上传、分配域名、全球传播 artifact 的时间压到了 1 秒，且这 1 秒内仍包含全球 CDN、防火墙、不可变部署、域名分配、可观测性和回滚。
https://x.com/rauchg/status/2100698591417499972

他还转述了一条有意思的能力：当你逼 agent 尽快出 hotfix 时，它现在可以执行 `vercel --turbo --prod`，自动使用最快的可用构建机。（79 赞）
https://x.com/rauchg/status/2100682030170489160

**为什么值得关注**：如果一次性 artifacts 真成为主要产出形态，那「agent 生成物的托管、灰度、回滚」会变成基础设施的默认需求，而不是附加功能。

---

## Box CEO Aaron Levie：agents 已经占推理的大多数（79 赞）

他的判断很直接：agents 已经构成推理的多数，未来一两年会趋近于几乎全部推理。「世界上用掉的绝大多数 token，会是 agent 在背后 24/7 替我们执行海量任务。」他列举的落地场景包括：读取所有代码变更以保护软件安全、在工作流内部处理全部数据、承担招聘与客户开发所需的大部分研究、审查世界上每个系统的每条事件流与日志、以及在个人生活里替我们执行任务。他强调新 agent 上线的速度没有放缓——过去一周他就引入了多个「一个月前技术上还不可能」的新工作流。
https://x.com/levie/status/2100799668573946191

**为什么值得关注**：这是「推理需求由人转向 agent」的产业侧表态，且来自一家做内容/工作流的企业软件 CEO，不是模型厂商的自吹。它同时解释了为什么数据中心的争论（Amjad Masad 今天也在说"我们需要海量数据中心，值"）会持续升温。

---

## FPV Ventures 合伙人 Nikunj Kothari：用 Claude 造一家"自驱动公司"（69 赞）

他痴迷 self-driving companies 一年多，试了很多产品都达不到标准，于是自己用「Claude in the loop」造了一个：nosugarforkids.com，一个只收录儿童健康零食的目录（他说这个品类居然此前不存在）。前台可以对话获取学校、午餐、零食盒场景的推荐，并按营养与实际品质排出 tier 榜。真正有意思的是自主侧——一个 Claude agent 每天醒来一次，执行：检查目录新增、剪掉可能已失效的产品、找能提升触达的新内容选题、查 dataforSEO 和 Google Search Console 的表现、撰写和编辑有用的新内容、保持质量尽量不引入 slop、（新加）主动联系媒体拿外链。结果：目前零外链、没有任何社交存在，站点自然流量长到每天约 6000 次曝光、60 次点击。他还提到有完整的 MCP（以及 WebMCP），可以引导自己的 agent 去对接。
https://x.com/nikunj/status/2100714665571737885
https://x.com/nikunj/status/2100718806004064730

**为什么值得关注**：这是今天最完整的一份「单 agent 日循环运营一门生意」的真实账目——包含运维动作清单和真实流量数字，而不是 demo。对做 agent 工具链的人，这份日循环几乎可以当 checklist 用。

---

## YC 总裁 Garry Tan：记忆的新解法（477 赞）

他指出 Memorable 找到了一条用 embeddings 而非堆更多 token 来优化记忆的路子，认为这是做记忆的一条强有力的新路径。
https://x.com/garrytan/status/2100668489178456268

他同日的另一条更值得记一句：在谈某个话题时他写「小心你的愿望」——这正是我们需要把对齐目标锚定在人类身上、而不是锚定在其他目标上的原因。（140 赞）
https://x.com/garrytan/status/2100636443127210112

**为什么值得关注**：embeddings 代替 token 膨胀来承载记忆，是当前 agent 长记忆成本问题的一个务实方向，值得对比主流「上下文窗口 + 摘要压缩」路线。

---

## SPC 普通合伙人 Aditya Agarwal：公开押注可解释性路线（8 赞）

前 Dropbox CTO、现 SPC GP Aditya Agarwal 明确表态：「这是解决对齐与安全问题的正确路径」，并称 GoodfireAI 是「在这一点上领先的非前沿实验室公司」，评价为「代际意义上重要」。（互动量低但站台方身份有分量）
https://x.com/adityaag/status/2100746235426836708

**为什么值得关注**：把可解释性（而非纯 RLHF/护栏）称为对齐的「正确路径」，是投资圈对技术路线的一次公开站队。

---

## 简短提及

- **OpenAI 的 Thibault Sottiaux（thsottiaux on X）**发了一条高互动（5524 赞、1800 回复）的设想：有没有人试过让「Astra 和 Fable 就一套完美 styleguide 达成一致，然后用 web mcp 托管它」。内容偏梗，但它点出了两个方向——多 agent 协商产出规范、以及 WebMCP 作为 agent 可调用接口。（仅作信号记录，不展开）
  https://x.com/thsottiaux/status/2100645454245720513

**今日略过**（低信号或纯推广）：Josh Woodward 的两条均为无评论转推；Peter Yang 两条为 Muse red panda 产品推广；Dan Shipper 仅一句 "it's happening!"；Amjad Masad 为无上下文转推。

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
