
全部 20 篇已标记已读,资料齐全。成稿如下。

---

# 📡 HN 每日精选(2026-09-05)| 今日主题:费马大定理被 AI 11 天机器验证

20 条新帖 → 精选 10 条。注:GPT-6 Astra 主发布昨日已推,今日为"上线 OpenRouter / Pro 解锁"进展跟进。

## 1. Anthropic:Claude 自主工作 11 天,完成费马大定理 Lean 4 机器验证
**HN**:414 分 / 268 评论
Anthropic 宣布放出**首个计算机完整验证的费马大定理(Fermat's Last Theorem)证明**:Claude 在人类只给出零散高层指令("Jacobian 作为 scheme 优先"、"推 Mazur 定理")的情况下,11 天内生成了 **1300 万行 Lean 代码、证明 30,300 个中间定理**(终稿用 29,500 个),规模是社区数学库 Mathlib 的 5 倍以上;多 agent 协作、沿 Wiles 证明的简化版(Darmon–Diamond–Taylor)推进。而人类数学家 Kevin Buzzard 牵头的帝国理工项目本计划数年完成——HN 评论直呼 "Buzzard 的团队被截胡了"。Buzzard 回应称这是"非凡的自动形式化成就……除数学公理外不依赖任何假设"。
**为什么值得关注**:从"需要几年、£1M 经费的社区工程"到"11 天自主完成",AI 数学验证的性价比拐点已现;对形式化验证、数学审稿流程是范式冲击(评论区估算其输出 token 成本约 $30 万,但 Anthropic 自用远低于此)。
🔗 原文:https://www.anthropic.com/research/formalizing-fermats-last-theorem | 代码库:https://github.com/anthropics/fermats-last-theorem | HN:https://news.ycombinator.com/item?id=49568506

## 2. GPT-6 Astra 上线 OpenRouter;Pro 用户时隔 24 小时解锁
**HN**:60 分 / 21 评论
昨日头条的后续铺开:Astra 模型页已在 OpenRouter 上线(第三方 API 通道打通);Pro 用户陆续获得访问权,恰逢 OpenAI 发放"每缺一天补偿一次可累积重置额度"——评论 `kingstnap`:"Pro 也终于能用了!等了整整 24 小时";`InsideOutSanta` 玩笑道:"既然欠一天补一次额度,我倒希望他们再晚几天给我开。"Business + Cyber 验证用户已能在 Codex 与 OpenAI API 中使用。此前 HN 估算定价约为 $10/$50 每百万 token(比 GPT-5.6 Sol 贵 2.5 倍)。
**为什么值得关注**:做模型接入的可以开始实测排期了;补偿机制也坐实了官方"容量稀缺、Pro 优先"的运营策略。
🔗 原文:https://openrouter.ai/openai/gpt-6-astra | HN:https://news.ycombinator.com/item?id=49570545

## 3. ⚠️ 所有 Chromium 内核浏览器受影响:沙箱内 RCE 已被在野利用
**HN**:80 分 / 27 评论
CVE-2026-85046:V8 引擎类型混淆(type confusion),攻击者用构造的 HTML 页面即可在**沙箱内执行任意代码**,影响 Chrome 152.0.7977.82 之前的所有版本(即所有 Chromium 系浏览器:Edge、Brave、Opera 等)。Chromium 官方定级 High,CVSS 8.8,9 月 3 日公开,标题明确"已在野外被利用"。HN 冷静派提醒:沙箱内 RCE 仍需配合第二个漏洞才能逃逸提权(`teravor`:"需要链上另一个 0day"),但评论 `petra303` 质疑"在野利用了才 8.8 分?"
**为什么值得关注**:在野利用 + 全系浏览器波及 = 请立即升级到最新版,尤其内网办公机器。
🔗 详情:https://nvd.nist.gov/vuln/detail/cve-2026-85046 | HN:https://news.ycombinator.com/item?id=49570669

## 4. 政府 Rails 站遭攻击:CVE 补丁发布数小时后即被利用
**HN**:62 分 / 14 评论
rietta.com 披露:一个政府 Rails 网站在漏洞补丁发布**数小时后**即被攻击。漏洞链指向 Rails ActiveStorage 图像处理:libvips 的 Matlab v5 (.mat) 加载器可被恶意文件触发(研究者命名为 "Kindarails2shell" 的攻击面);补丁后 Rails 对恶意 variant 渲染直接抛异常拦截。作者评论澄清:不需要服务器装 MATLAB,默认配置 + ActiveStorage 就可能中招(`fishtoaster`:"影响任何默认配置使用 ActiveStorage 的 Rails 应用");Cloudflare/WAF 只能纵深防御、挡不住所有 payload。libvips 的 `block_untrusted` 模式本就把 .mat 标记为不可信,社区质疑为何默认未启用。
**为什么值得关注**:打补丁与被打之间的窗口期正在被压缩到小时级——"补丁竞速"已成常态,默认配置的安全姿态(trusted loader 白名单)比应急更关键。
🔗 原文:https://rietta.com/blog/ruby-on-rails-cve-exploited-hours-after-patch/ | HN:https://news.ycombinator.com/item?id=49568828

## 5. Show HN:开源 eInk 自行车码表(209 分 / 68 评论)
一款全开源硬件自行车码表:电子墨水屏 + 高续航,亮点是用 **BLE 硬件直接接收 ANT+ 传感器信号**(心率/速度/踏频)——评论 `kccqzy` 惊叹:"你居然用 BLE 硬件收到了 ANT+?!两个协议底层居然这么像"(同为 2.4GHz GFSK 1Mbit/s 物理层)。作者 `stingrae` 称已实测骑行 500+ 英里无问题。社区争议集中在实用性:荷兰用户担心雨天、ePaper 强光下刷新发虚、无触屏的物理按键取舍,以及 Garmin 竞品差距。
**为什么值得关注**:209 分说明"开源替代 Garmin"的号召力仍在;BLE↔ANT+ 物理层复用的实现思路对低成本传感器生态也有参考价值。
🔗 原文:https://opentrailpaper.com | HN:https://news.ycombinator.com/item?id=49567437

## 6. Mullvad 关闭公共加密 DNS,转投 Quad9
**HN**:205 分 / 66 评论
以隐私著称的 VPN 商 Mullvad 宣布**关停自家公共加密 DNS 服务(含广告拦截 DNS)**,改为赞助 Quad9 基金会。官方原话:"运营隐私友好的公共 DNS 是高度专业的事,Quad9 基金会是该领域公认的领先者,与其重复造轮子不如支持他们。"评论区最大吐槽是**功能缺口**:`oofdere`:"Quad9 没有广告拦截 DNS,所以它并不是真正的替代品。"另有技术派担心转发器 + Quad9 双重 DNSSEC 校验的性能与 BOGUS 误报问题;也有人主张"广告拦截这种事不如自建"。
**为什么值得关注**:隐私圈头部玩家主动"砍自建、投基金会",标志公共 DNS 服务走向专业化集中;对依赖 Mullvad 广告拦截 DNS 的用户是迁移信号。
🔗 原文:https://mullvad.net/en/blog/shutting-down-our-public-encrypted-dns-servers-and-sponsoring-quad9-instead | HN:https://news.ycombinator.com/item?id=49568579

## 7. AI 能设计电路板了吗?EEBench 用"声明式电路代码"建评测基准
**HN**:121 分 / 71 评论
受 OpenAI 在 GPT-6 Astra 发布演示中展示 KiCad 布板刺激,EEBench 团队发布评测基准回答"AI 画出来的电路到底行不行":让 agent 在 **atopile(声明式 HDL,电路即代码)** 上工作而非 GUI 点鼠标——因为模型"读过教科书、数据手册,懂的电子学远比在 CAD 里点出来的多",代码环境能直接构建、仿真、看失败原因。评论区实战派 `amelius` 更期待 Astra 直接做 PCB 布线,"下一个痛点是 Digikey/LCSC 元器件选型与替代料";`nickff` 泼冷水:"布线是布局里最容易的部分,难的是元器件摆放。"`thesz` 翻出 80 年代 Eurisko 的先例感叹"AI 在原地绕圈"。
**为什么值得关注**:AI 硬件设计的可测性缺口终于有人补;声明式 EDA 可能是 agent 进入硬件设计的实际路径。
🔗 原文:https://eebench.org/blog/can-ai-design-circuit-boards-yet/ | HN:https://news.ycombinator.com/item?id=49569366

## 8. Rust 版 React Compiler 原生进入 Vite
**HN**:98 分 / 19 评论
继 oxc 团队 8 月 4 日发布官方 Rust 版 React Compiler 后,`@vitejs/plugin-react` v6.1.0 加入实验性原生支持(配置 `{ compiler: true }` 即可),非 Vite React 插件场景可用 `@acusti/vite-plugin-react-compiler`。Master.dev 实测 1036 文件代码库:**编译器阶段 14.3s → 0.81s(约 17.6×)**,整机构建 22.1s → 9.3s;评论 `adzm` 换用后 "dev server ready 从 6 秒变 2 秒,构建管线里终于没有 Babel 了"。新版还修掉了 Babel 版 1.0 的多个 JS 支持限制(try/catch 任意条件、解构 prop 重赋值等)。
**为什么值得关注**:React 工具链"去 Babel"完成临门一脚;agent 化开发让 CI 分钟数成为真金白银的成本,构建提速直接省钱。
🔗 原文:https://blog.master.dev/react-now-rusted-all-the-way-out/ | HN:https://news.ycombinator.com/item?id=49567873

## 9. GitHub Copilot 的 Project HydraFusion:多模型编排换"前沿质量 + 降本"
**HN**:57 分 / 29 评论
GitHub 开源 Copilot 内部的 HydraFusion 方案:把"人肉多模型协作"(选模型、交叉评审、难题升级)搬进运行时,按请求在三种模式中自动选路——**Single**(单模型直解)/ **Cascade**(便宜模型先答,质量门不过再升级强模型)/ **Critique**(A 家模型起草,B 家模型只读评审,起草方修订一次)。离线评测 TerminalBench 2.1:**任务质量 +4.9pp,成本较 Claude Opus 5 估算降低 67%**;已在 Copilot CLI `/experimental` 对所有套餐开放。HN 工程派 `gopalv` 点出关键:"多模型厂商是 critique 模式的前提——同厂模型共享训练数据与偏见";也有评论质疑编排 overhead。
**为什么值得关注**:GitHub 用生产数据验证了"弱模型打底 + 异厂评审 + 按需升级"的路线的性价比,这是 agent 成本优化的直接参考模板。
🔗 原文:https://github.blog/ai-and-ml/github-copilot/project-hydrafusion-frontier-quality-via-multi-model-orchestration/ | HN:https://news.ycombinator.com/item?id=49566788

## 10. "LLM 是 next-token 预测器"是错误的心智模型
**HN**:55 分 / 141 评论(话题帖,讨论远多于点赞)
博客文章主张:预训练阶段模型确实是 next-token 预测器,但**后训练(尤其 RLVR 强化学习)之后就不再是"预测数据里下一个词",而是在决定"哪个 token 能赢"**——类比:没人会称国际象棋引擎为"next-move 预测器",它在选择制胜的一步。141 条评论吵成哲学论战:支持派 `Veedrac`:"它不是预测下一个 token,而是基于对奖励信号的预测来决定下一个 token";反驳派 `danielmarkbruce`:"下棋是选择不是预测,因为没有既成的'真值'可核对——可这跟采样下一个 token 有何本质区别?";折中派:next-token 只是驱动整个系统的"时钟/适应度函数"。
**为什么值得关注**:这个争论直接决定你怎么 debug agent、怎么设计奖励与评测——"它在预测"与"它在优化奖励"是两套完全不同的心智模型,而后者才是调 RLVR 时代的正确姿势。
🔗 原文:https://gmcgoldr.github.io/2026/09/04/llm-next-token-predictors.html | HN:https://news.ycombinator.com/item?id=49567310

---
✅ 已抓取 20 条 → 精选 10 条,全部标记已读。明日见。
