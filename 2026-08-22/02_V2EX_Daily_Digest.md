
All state files synced (791 ids). Selection is complete — I have 5 quality posts with substantive comments. The pipeline already marked all 61 new posts as read in `v2ex_rss_read.json` and synced legacy state files. Here's the digest:

---

**V2EX 技术/AI 精选 · 8月22日**

**1. 统计一下大家现在 vibe coding 的方案**（130 回复）
楼主一直在用 Codex 做 vibe coding，但最近额度重置越来越少、快见底了，向社区征集替代方案。帖子实际戳中 AI 编程订阅制下最普遍的痛点——额度焦虑和多工具怎么分工，130 条回复说明这是当前 AI 开发者绕不开的话题。
- V2EX 62楼 @songche："历史记录是 cc 或者其他工具管理的……一个套餐到额度了换 plan 重启一个会话，把之前的历史记录扔进去喊一声继续" —— 分享额度耗尽后跨工具续接会话的实用技巧
- V2EX 25楼 @MHPSY："claude code max 20x + gpt pro 20x……因为 claude 提升了周额度的 50% 所以几乎用不完了" —— Claude 周额度上调后反而成了最不缺的额度
- V2EX 26楼 @kuhung："codex、claude、gemini、cursor 各自 20 刀的套餐。codex 做自动化任务、claude 做复杂任务方案设计、cursor 做明确调整" —— 四工具按任务类型分工的典型重度用户配置
https://www.v2ex.com/t/1236041

**2. 有没有人感觉 vibe coding 的时候电脑很卡？**（10 回复）
楼主 14600K + 96G 内存 + 2080Ti 22G 跑 Codex 觉得吃力，纠结换 Mac 会不会好点。回复基本指向同一结论：卡顿不是硬件问题，是 Codex 客户端自身的工程问题。
- V2EX 5楼 @Y25tIGxpdmlk："codex 一个对话几百 M 上 G，都是各种 json 格式，切换一个对话能给你卡飞起……模型是好的，但是软件设计的像大便一样" —— 直接吐槽 Codex GUI 性能
- V2EX 8楼 @msg7086："Codex app 卡是因为程序写得烂，动不动就拉起几十个 git.exe 或者几十个 taskkill.exe 或者暴力轮询 WMI……macOS 下 codex 一样有问题，24G 的本子上吃了 100G+ 的内存" —— 给出具体机制，Win/mac 通病，换 Mac 无用
- V2EX 11楼 @xiaoz："现在各种 GUI 越来越卡了，我现在换回自己开发的 Zacp + 一些轻量级 CLI 搭配使用了" —— 部分用户已回流 CLI 方案
https://www.v2ex.com/t/1236319

**3. 在这个独属于 ai 的时代，我终究是被裁员了。**（36 回复）
前端工程师自述：公司从 2026 年 3 月起借 AI 之力强推全员转全栈、一人扛一个项目，8 月 20 日以"部门盈利变少"为由被裁。帖子引爆"AI 时代纯前端/后端岗位是否消失"的争论，社区观点分歧明显。
- V2EX 2楼 @sentinelK："其实跟 AI 关系不大，是经济环境+硬件价格导致整个信息化产业萎缩了。C 端买不起手机，B 端买不起电脑，软件怎么卖……" —— 反对把裁员归因于 AI，指向宏观周期
- V2EX 25楼 @sead："关键不是让 AI 使劲干，最终能落地变现才是关键，产品再好无人问津也是白干" —— 强调变现闭环比工具效率更重要
- V2EX 36楼 @flyshadeXie："我看了楼主的个人主页……这 180 篇文章可不是随便攒出来的。这么强的程序员也要被裁，这是公司的问题" —— 为楼主能力背书，矛头指向公司决策
https://www.v2ex.com/t/1236240

**4. Pro 20X，由昨天重置 100%到现在剩 77%，反推周额度约......**（4 回复）
楼主用 Codex 任务记录实测反推：1.39 万 credits 对应 23% 消耗，推得 20X 周额度约 6 万 credits，得出"没明显缩水"的结论。但评论区体感相反，额度黑盒成为核心争议。
- V2EX 4楼 @malusama："可以安装这个脚本反推（chatgpt-credit-watch），妈的我被砍了只剩两万了" —— 给了工具链接，但自己额度只剩 2 万
- V2EX 1楼 @MAVETRICK："我的是 5x pro，我也感觉没缩，这其实就是 openai 鸡贼的地方，完全是一个黑盒。每个人只能靠感觉推断，有说缩水的也有说没缩的" —— 点破 OpenAI 额度不透明的本质
- V2EX 2楼 @yiligi："可能是 tibo 被骂爆之后偷偷的给加了" —— 猜测与 Tibo 事件舆论压力有关
https://www.v2ex.com/t/1236309

**5. 编程效果对比 本地 Qwen3.8-27B vs Deepseek**（29 回复）
用同一提示词（鹈鹕骑自行车的 SVG 动画）实测 Deepseek 网页版/Flash 与本地 Qwen3.8-27B 量化版的生成效果、耗时与费用。数据显示本地 Qwen 27B 在速度和成本上明显占优，评论区围绕量化档位和模型选型展开。
- V2EX 30楼 @killadm："你的 q5 和原版 fp8 生成的差不多，但是用破限版的 int8 模型测试生成的动画反而车轱辘乱飞" —— 量化档位对效果的实测细节
- V2EX 29楼 @Maboroshii："我看 qwen-3.8 27B 在 openrouter 上比 deepseek-v4-flash 还要贵不少呢" —— 指出 API 调用与本地部署的成本差异
- V2EX 14楼 @Seanfuck："最后一个好。Qwen 明显比 Deepseek 强。" —— 直接站队本地 Qwen
https://www.v2ex.com/t/1236180

---
已处理：本次 61 条新帖全部标记已读（含低价值/推广帖：Clash Plus、DeepSeek Harness 软广、招聘帖等已跳过），状态文件已同步。
