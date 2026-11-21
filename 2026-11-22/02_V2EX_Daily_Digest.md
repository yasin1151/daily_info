
**V2EX 精选 · 2026-11-22**
（RSS tech/index/qna + API latest/hot 共 80 条新帖，筛 22 条，推送 9 条；❤ 为页面实测值，V2EX 单楼点赞普遍偏低）

---

**1. Claude 被连封两个账号，不想折腾了，接下来用啥？**（43 楼）
https://www.v2ex.com/t/1258753

楼主两个 Claude 账号接连因 KYC 被封，问替代方案：听说 Gemini 4 不错但怕影响 Gmail，Codex「听说很拉」，想知道国产模型谁写代码最强。价值全在 43 楼堆出的迁移实战经验，以及封号从运维问题被拉回商业逻辑。

- 2 楼 SilentBlade（❤1）：「Google Pro 感觉额度有点少，感觉要上 5X 档的 Ultra。Codex 现在拉完了，之前用的土耳其的便宜绝版号现在养着基本不咋用了。国产应该是 DeepSeek 可以，但是是按量计费的，貌似马上会推 plan。」
- 17 楼 humbass：「Claude 财报，最近半年 23 亿美元收入来自中国地区，其中大部分是被封禁账号堆的收入。」——全场最狠的一句。
- 31 楼 ingramyang（❤2）回「你们都在做啥项目非得用 Claude」：「和做啥项目没关系，要用就直接用能力最好的啊，毕竟是生产力工具和知识来源，何必在能力一般的模型上浪费时间？人生苦短啊。」
- 附加坑位：33 楼用中国护照过 KYC「秒封」；6/15 楼指出大陆与香港 Play 地区不支持升级额度，得改新加坡/日本；41 楼「Claude 封我 3 个，我立马扭头就 Ultra 200 刀给了谷歌」。

**2. Gemini 4 Neon High 高强度实测：Ultra「太耐用」**（19 楼）
https://www.v2ex.com/t/1258799

Ultra 用户记录 CLI 模式下三个 Neon High 窗口并行、每天 8 小时的额度消耗，结论「完全 Opus 5.5 平替，差距不大」，已彻底弃用 GPT。回帖的质疑比正文更有料。

- 1 楼 matolv：「Pro 订阅一个比较复杂的数据分析 neon high 会让额度直接见底，耗时 1 小时 30 分钟，但回答质量还是令人满意的。无论是 google 还是 anthropic，不开放自家最顶级的模型给 pro 订阅，oai 起码把 astra 提供给 plus 用，这点上 oai 更慷慨些。」同楼还有少见的中立评价：Claude 的护城河已从前沿模型转到 desktop app 交互与 M365 集成。
- 2 楼 MuyuQ：「不要把重置考虑进去。这段时间在拉客，肯定会重置。刚刚重置过了，你是不是刚好在重置以后看的使用量。」——直接打掉实测的前提。
- 7 楼：「至少 gemini 用着不烧心。隔壁 A/ 隔三差五的捐款封号太烧心了。」8 楼 gibber 反向提醒：「年初 gemini3 刚出来的时候也是表现很突出，然后就是一路下坡，断崖式降智。」

**3. Mingle：零服务器，把 AI Agent 请进微信/飞书/Slack**（MIT 开源，新帖无回复）
https://www.v2ex.com/t/1258819

作者不满「云端中转」——聊天记录和工作上下文要过第三方机房——于是做了纯本地桌面工具：把 Claude Code、Codex、Kimi Code、OpenCode、Cursor 等 14 种 harness 以机器人身份接入微信、企微、飞书、钉钉、QQ、Slack、Discord、Telegram、iMessage 和 GitHub Issues。API 只监听 127.0.0.1，凭据只存系统钥匙串，角色与记忆就是本机目录里的 ROLE.md / MEMORY.md。同一 Agent 跨 IM 共享记忆（微信群问「上午飞书群定了什么」能直接答），群聊可旁听、被叫名字才接话、忙群自动降频省额度。作者如实标注：上周四起意，v0.4.8，仅 Claude Code/Codex/OpenCode/Kimi Code 端到端跑通，飞书在真实租户验证过，Windows 包未签名。本地优先 Agent 接入层第一次有可安装成品，值得直接看 README。

**4. Tools3000：用 C++20 + Rust 写的 Windows 全能箱**（9 楼）
https://www.v2ex.com/t/1258796

Everything + Snipaste + PixPin + WGestures 重度用户的合并替代：NTFS MFT 毫秒搜文件名、`content:` 走 Rust SIMD 穿透搜 Word/PDF/Excel/PPT/CAD/源码正文、空格免打开预览、滚动长截图、离线 OCR（贴图后可划选复制/原位改字）、带鼠标运镜录屏、全局手势（Lua 扩展）。工程上明确反 Electron：原生 Win32 + Direct2D，待机十余 MB，索引服务按需启动（主力机约 300MB），OCR 与编码放短命子进程跑完即回收。GPL3.0，作者当主力用了 4 个月。

- 3 楼 xclimbing：「初步试用了一下，大赞，非常对我的胃口」，随后提三条具体意见（窗口不能最大化、结果排版不如 Everything、路径通配搜索）。
- 4 楼 作者（❤1）：「1 和 2 我用了一段时间适应了，就没改，回头我看看；3 我简单测试了下可以。」
- 8 楼 ccyixia：「赞一个，有了 ai 每个人都可以给自己做一个专属的工具集。我刚给自己的 mac 做了一个，名字叫 Superman，跟楼主的有异曲同工之妙。」——今天最能概括 create 板块气氛的一句。

**5. xalfred：三个 Agent 轮流等你点「同意」，于是他做了个手表审批 App**（1 楼）
https://www.v2ex.com/t/1258818

Claude Code 跑重构、Codex 补测试、另一个查文档，人成了并行流水线的瓶颈：谁跑完、谁报错、谁卡在权限确认上，界面不会喊你。作者做了统一通知层：任何能调 MCP 的 Agent 都把「需要人」的事件推到同一处（iPhone + Apple Watch）——手表一震看清谁要做什么、抬手点同意、提问手机回、多方案手表选。这是 Agent 可观测性 / human-in-the-loop 通道一个很具体的产品切面。

- 1 楼 likewater：「>>那一刻我想明白了：Agent 越多，我自己反而成了瓶颈。说得太棒了，我现在就是这样。你的这个程序给了我很好的灵感，可能，我们不用坐在位置上一直等答复了。」

**6. 模型「偏科」恰恰证明 skill 不可能被完全取代**
https://www.v2ex.com/t/1258820

论证短但硬：GPT 被开发者嫌「防御性编程」（到处加测试和 guardrail），科研与维护岗反而喜欢；Claude 则被偏爱「意图识别 + 许愿式编程」。说明再强的模型也必然带偏好与行事取向，而 skill 提供的正是中层可预测性。作者以自家 ponytail skill 为例：它服务维护性编程而非探索式——一个 skill 都无法时刻适用，吃掉 skill 的模型更不可能保证取向符合需求。

- 1 楼 cybort：「需求-理念-方法-工具使用，越靠近底层越适合内置集成，越靠近上层就越多变，需要接受输入。」
- 2 楼 hrdom：「或者说 skill 的存在证明模型还有完善的空间。」

**7. limo：在终端里直接跑 Web APIs**（2 楼）
https://www.v2ex.com/t/1258788

基于 moli（V8 + 完整 Web APIs 的无头浏览器）的命令行运行时。动机很具体：维护浏览器端 WebAssembly 项目时测一次要起 http server + 桌面浏览器或 chromedriver，版本对不上还起不来；node/deno 又没实现完整 Web APIs。limo 让 JS 像 node 一样直接跑但带 DOM/fetch，作者认为适合日常调试、CI 和自动化。

- 1 楼 ldm0：「spxg NB!」；2 楼作者：「只是 moli 众多生态之一，哈哈。」

**8. 近两周 create 板块项目总结（从 229 条里挑的）**
https://www.v2ex.com/t/1258800

把 11/07–11/21 的 229 条 create 帖按回复数排了一遍，等于一份免费社区产品雷达：Fotilo（157 楼，Mac 截图录屏）、Dis 看帖（132 楼，一个 App 刷 V2EX/NGA/Linux.do/Chiphell）、Ebb（100 楼，SwiftUI 系统监控，⌃⌥E 回放最近 60 秒找闹事进程）；技术含量最高是 Ferry（逆向 macOS 屏幕共享高性能模式做免费远程桌面）和 Airhand（Rust + AV1 硬编 120fps）；AI 侧有 TaroBird、wechat-use（让 Agent 操作真实微信桌面）。彩蛋是一条很诚实的流量复盘：蹭 Fortnite 热词的小站 GSC 单日点击从几十涨到 1 万+，挂 adsterra 赚回 GPT Pro 的 token 费，然后排名掉了。

**9. Enter Guard：Enter 换行、Ctrl/Cmd+Enter 发送**（争议点在回复里）
https://www.v2ex.com/t/1258823

解决 DeepSeek 回车即发送、打一半就发出去还没法改的痛点，覆盖 ChatGPT/Claude/Gemini/Kimi/Qwen，IME 候选确认不受影响，无统计无追踪，权限只有 storage 和 activeTab。免费版够用，Pro 一次性 $9.99 买断。

- 1 楼 UnknoownUser：「如果我把你的这段描述喂给 Claude，它也能帮我做出一模一样的东西吧？感觉 $9.99 太贵了」
- 2 楼作者 liuliangsir：「是的，对国内用户来说是有点贵，推荐使用其它可替代的功能。我这个插件面向的主要用户群体是海外用户。」——AI 时代「薄壳工具该不该收费」的现场标本。

---

已处理：80 条新帖全部写入 seen（9789 → 9869）。跳过：招聘内推（SHEIN）、送码/黑五推广（Enconvo、磁带猫、Gemini 优惠长文）、建站 SEO 模板、Android 小工具堆帖。归档：`state/2026-11-22-v2ex-精选.md`。
