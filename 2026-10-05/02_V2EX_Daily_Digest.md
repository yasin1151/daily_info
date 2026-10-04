
**V2EX 技术/AI 社区日报 · 2026-10-05**
（扫描 tech/programmer/apple/create/qna/ideas/share/jobs/index 等 feed + 公开 API，73 条新帖中筛出以下 11 条）

---

**1. IINA 1.5.0 正式发布（十年之作首次大改界面）**
作者自述从图书馆写下第一行代码已过十年。1.5.0 首次大范围重做 UI 以贴合 macOS 26 设计语言，最大新功能是**解锁窗口长宽比、可随意缩放**；设置窗口被完全重写、彻底摆脱 xib 依赖，插件侧边栏可独立固定。作者还鼓励大家用 AI 生成插件并提 PR 进入官方插件列表。对 macOS + mpv 用户是小版本但高含金量的更新。
- 15楼 V2Try（1赞）："第一时间下载，亲自安装，亲自观看。"
- 16楼 3ad0f4（1赞）："希望有 App Sandbox"
- https://www.v2ex.com/t/1246346

**2. 大模型对 Vue.js 的支持不如 React？**
楼主一句话引战（"估计不是亲生的有关"），但评论区罕见地形成共识：不是玄学，是**训练语料 + 语法结构**双重原因。React 数据多、ui=f(state) 纯 JS 函数对 LLM 友好；Vue 的 `.vue` 三段式与 `.value` 模板语法让模型多一层理解负担。
- 9楼 zazzaz（2赞）："AI 出现之前大家还会争论 React 还是 Vue；有了 AI 之后基本都转向 React 了……AI 更懂 React，进而形成良性循环。"
- 12楼 ttkit（2赞）："vue 是给人写的，封装了很多反程序设计（A 可以直接到 C，但 vue 设计成 A 先到 B 再到 C）……最典型的就是 `.value`，AI 也经常犯。"
- https://www.v2ex.com/t/1246345

**3. macOS 上的 ChatGPT 客户端长期无法使用**
OpenAI 把 ChatGPT 与 Codex 二合一后，楼主遭遇连环 bug：Classic 版无法用 thinking；新版附件上传大概率失败（网页版/Classic 正常、**开全局代理也不行**）、重启后大概率被分回旧 UI、左上角 Chat 入口消失。持续近两个月只能退回网页版，"每天更新客户端当刮刮乐看是否修好"。
- 9楼 break（1赞）："如果主要是 chat 模式，使用 web 会方便很多吧。"
- https://www.v2ex.com/t/1246331

**4. 开源：没有删除和升级权限的链上论坛 Chain Talk**
作者把论坛做到极简——内容全存以太坊事件日志，合约仅 22 行（一个变量、一个函数、一个事件），**无管理员、无删除、无升级**，发出去不可改。成本：部署约 $0.06、发主题约 $0.04、回复约 $0.02，无服务器/数据库/运维费；用 The Graph 索引，前端无需钱包即可浏览。立意是"404 时代"对抗平台删帖与数据丢失。
- 2楼 jacketma（1赞）："区块链除了搞钱干成了，其他的活都不行了。"
- 5楼 413420（1赞）："你的网站证书过期了，或者主机内容被撤下，论坛就没了。"
- https://www.v2ex.com/t/1246367

**5. 开源 Bibo：带"按需 Linux 沙箱"的个人 AI 工作空间**
MIT 开源的自建 AI 搭档，对话/任务/日程/笔记/文件同页。技术亮点是**运行成本拆分**：Agent 跑在 Cloudflare Worker/Durable Object 上，普通聊天不启动容器，只有跑 Python/Shell 等系统工具时才按需起隔离 Linux 沙箱，空闲 5 分钟休眠，文件放 R2 可挂载进沙箱。需 Workers Paid + R2 + Containers + DeepSeek Key，按量计费、无固定月费。
- https://github.com/Peiiii/bibo ｜ https://www.v2ex.com/t/1246404

**6. 开源 Precedent Loop：让 Agent 换个会话也记得项目里踩过的坑**
针对 Codex/Claude Code"不记事"的痛点：经验由 **Agent 提候选、用户确认后才入库**，用时按需检索（单次最多 8 条/5000 字），并记录每条被查/被用次数，真正影响判断的会自动提修订。数据只是一个本地 SQLite，App 不调模型 API、不存 Key；Codex 与 Claude Code 共用一库。
- https://www.v2ex.com/t/1246437

**7. "感觉程序员行业有点死了"——关于 AI 与独立开发的激烈争论（44 回复）**
楼主称 AI 让程序员失业增多，独立开发者 App 下载量与收入近半年快跌没。评论区两种声音对撞：一方说 AI 让不懂代码的人也能上架 App，但**运营门槛仍在**；另一方认为这是独立开发的马太效应常态，AI 只是让更多不适合的人入局当炮灰。
- 1楼 digitv（3赞）："我完全不懂 app 开发……每天用零散一个多小时也做出一个 app，唯一成本就是几百块 token 和云费用。"
- 29楼 bbbblue（2赞）："身边几个不会代码的也上架了，刚开始意气风发……最近一打听全死了。上架门槛低了，但运营的门槛还在那。"
- https://www.v2ex.com/t/1246421

**8. 本地部署 Strata + Qwen3.8-Flash-Next 125B 一直超时**
楼主配置 A6000 48G + 双 Xeon 4210R + 128G，单测能到 90+ tps，但接入 workbuddy/CherryStudio 后**长上下文 + 调用 tools 就有概率崩**。评论区 fellow 也卡在把 Strata 接进 Codex（工具调用位置不明、思维链不展示）。
- 1楼 anivie："我也在尝试把 Strata 接入 codex 里用……给我整的一脸懵，现在在等官方支持 codex。"
- https://www.v2ex.com/t/1246393

**9. gemini4 还不下放，用户纠结"叛逃"去哪儿**
楼主吐槽 Google 发新模型不给用（3.5 Pro 已拖数月），想从 OpenAI 出走却发现 Gemini / Grok 两边都不满意，是当下模型选择的真实写照。
- 2楼 dimlau："一直续 Gemini 年费 Pro，够用了，至少输出言语顺溜。"
- 4楼 zuosiruan："grok 4.7 拉了，难受。"
- https://www.v2ex.com/t/1246364

**10. QuotaView 0.7.5：全新的 Codex 多任务灵动岛（开源）**
作者称这是迄今最大规模重构：多任务灵动岛汇总任务进展/协作状态/额度用量，支持子任务与主任务关联展示、集中处理待确认请求、重整额度与 Token 统计面板。Codex 重度多开用户可关注。
- https://github.com/Duoasa/QuotaView ｜ https://www.v2ex.com/t/1246387

**11. 产品前端被抄了，又无语又想笑（产品工程）**
楼主打磨 6 个月的产品上线 2 个月后被电诈站整站照搬前端：直接拿 Nuxt 构建产物改，连混淆后的 `.js`/`.css` 文件名都一样，联系方式都没换（投诉还投诉到楼主这）。
- 9楼 qiaobeier（1赞）："AI 反而不会抄袭，不信你让它抄一个试试……楼主碰到的明显是旧时代的克隆技术。"
- https://www.v2ex.com/t/1246398

---

已跳过：推广/邀请码帖（Codex 桌面版邀请名额、API 中转站"实测××不降智"）、纯生活闲聊与求职情绪帖。已处理帖子（73 条新帖）已全部写入 seen 状态（3902 → 3975），扫描与详情归档到 cron/state。
