
**HackerNews 每日精选 · 2026-11-15**
（扫描 20 条，20 条全部为新帖，以下是按信息价值筛出的 10 条）

---

### 1. Lovable 生成的 15.9 万个应用里，大量数据库裸奔
德国 Crissy Field 与《商报》联合调查：他们用 Common Crawl 抓取 2025 年 12 月至 2026 年 9 月间的 159,041 个 Lovable 项目，其中 34,545 个用了 Supabase；24,664 个站点在未登录状态下就把数据库记录直接发给浏览器。研究人员再做只读请求后，7,403 个站点（30%）能取到含邮箱的表，还出现了护照照片和 20 多万条私信。Lovable 的条款把安全责任推给用户，营销口径却是"无需任何技术知识"。

**为什么值得关注**：vibe coding 把"能跑"和"安全"彻底解耦了，暴露出责任真空。

**HN 讨论（561 分 / 228 评论）**
- `rvz`："Nothing to see here and working as intended." 他预判：一旦 abliterated 模型以 2400 TPS 扫这类 Web 应用，"你在安全上根本还没准备好，形式化验证也救不了你"。
- `guestlistplus10`：Railway 前几天刚被同类手法打穿，攻击者疑似用 abliterated 模型加窃取的密钥，烧掉约 74 万美元 AI 费用。"如果 Railway 都扛不住，随便一个 Lovable 应用就是软目标。"
- `hn_throwaway_99`：别只怪 AI，AI 之前 WTF 级漏洞一样多。"唯一能治这个的是真正硬的赔偿责任。"
- 文章作者 `neathack` 现身：两周前自己投过，没起量，这次被重新提交。

https://www.crissyfield.de/research/lovable-en/

---

### 2. PyPI 新项目页上线，把"安全信号"提到第一屏
PyPI 完成 7 月公布的全套 UI 改版，项目页新增 Security 标签，按发布文件逐条展示溯源状态：要么是 full provenance（PyPI Publish 证明文件由 Trusted Publisher 发布，SLSA Build Provenance 则把文件链回具体 commit 和构建平台），要么是 no provenance，指文件来源无法被密码学验证。设计遵循 OpenSSF 的 attestation 风格指南，可点开透明度日志查看。

**为什么值得关注**：供应链攻击是 Python 生态头号风险，PyPI 终于把"这包是谁构建的"变成默认可见。

**HN 讨论（187 分 / 83 评论）**
- `cowlevel` 提醒了边界：这套机制主要能发现"原本正常、后来被劫持"的项目，不负责识别天生恶意的包。
- `zzzeek` 指出一个坑：一个包里只要有文件通过带 attestation 的 Trusted Publisher 发布，其余文件就必须同样处理，否则 PyPI 会判定该项目可能已被入侵。
- `eesmith` 追问：可信发布者是不是只有美国营利公司？想在 Codeberg、SourceHut 上发版怎么办？
- `mistursinistur` 冷冷一句："Nobody is looking at these pages."

https://blog.pypi.org/posts/2026-11-06-ui-updates-complete/

---

### 3. Show HN：190 行纯 JAX 复现 DeepSeek V3
作者想把 V3 和别的模型到底差在哪搞明白，于是从零重写了三个关键设计：MLA（每个 token 每层只缓存一个 480→144 维的潜向量，而非完整 KV）、带 per-expert 偏置的无辅助损失负载均衡 MoE（1 个共享专家 + 16 个路由专家，top-4）、多 token 预测。3620 万参数的小模型，无 Flax、无 Equinox、无 PyTorch，参数就是普通 dict，在一台 MacBook Air 上用公版侦探小说预训练完成。

**为什么值得关注**：读一百篇架构分析不如读两百行能跑通的代码，这是理解 MLA 和 aux-loss-free 路由最省时的入口。

**HN 讨论（137 分 / 7 评论）**
- `joebarbere`：这是他第一个在 Fedora + ROCm、RX 7600 XT 16GB 上端到端跑通的项目，"买这卡就是为了玩深度学习，终于有个起点"。
- `armcat`："没有什么比重建模型更能理解模型"，顺带说自己得先跟 Zig 玩够再回来碰 JAX。

https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax

---

### 4. Show HN：Agweb，一个"永不抢焦点"的 agent 浏览器
作者同时跑多个 coding agent，被 Playwright 的 Chrome 窗口反复抢键盘烦到；换 headless 又被部分站点直接封，出了错也看不见。Agweb 基于 WebKit（Safari 引擎），一个窗口永不前置，agent 用 playwright-cli 风格命令从 shell 驱动，⌘D 的 dashboard 能同屏看到每个 agent 的每个 tab 和最后一条命令。空闲 tab 会被挂起——他机器上五个页面 0% CPU，而 Chrome 的 GPU 进程常年吃 5–7 个核。内置 uBlock Origin 规则列表。

**为什么值得关注**：多 agent 并行时"人机共用一个浏览器"是真痛点，这个思路是保留 headless 的好处又不放弃可观察性。

**HN 讨论（83 分 / 21 评论）**
- `agline_in` 问了个关键问题：共享命名 profile 时，一个 agent 登出、切账号或触发限流，其他 agent 会不会一起被污染？能不能给 agent 只读 fork？
- `bookernath` 准备拿它替换验证流程里的 Chrome，但质疑默认开广告拦截——是偏爬取还是偏应用测试？
- `CharlesW`：已经有一堆 agent-browser.dev 之类的方案，这个到底多解决了什么？作者回：自己用着顺手。

https://github.com/paul-nameless/agweb

---

### 5. 美国 IRS 把免费报税系统 Direct File 开源了
仓库是 IRS 官方账号下的 Direct File 前端：把 26 USC 税法翻译成普通人不需要查指南就能回答的平实问题，答案再映射成标准税表，通过 MeF API（对授权公众开放）提交。设计目标是一部手机和一台笔记本上体验一致，英西双语，覆盖不同能力和无障碍需求。

**为什么值得关注**：政府核心公共服务开源是罕见案例，也是"AI 能不能干掉 TurboTax"这类讨论的现实底座。

**HN 讨论（136 分 / 82 评论）**
- `toomuchtodo`：随着国会换届，预计 Direct File 会回归并永久化。
- `bentt`："我看不出 TurboTax 怎么扛住 AI coding 这列火车，信息本来就全是公开的。" `aliljet` 直接喊话：谁做个 agent 版报税，钱给你。
- `fedpost`：PR 区挺好笑，一堆被关掉的 PR 看着不像懂行的人在维护。`makuchaku` 则怀疑：怎么确认这真是 IRS 的？

https://github.com/IRS-Public/direct-file

---

### 6. SpaceX 用发射塔"筷子"夹住星舰，Flight 15 收官
第 15 次试飞以塔臂直接捕获星舰上级收尾，全程没有明显抖动。443 分、270 条评论，几乎是清一色的惊叹，少见的技术性争论。

**为什么值得关注**：可复用上级被抓住，是 Starship 从"能飞"走向"能高频复用"的关键一步——顺带也是第 8 条"太空数据中心"经济账的前提。

**HN 讨论**
- `inglor_cz`："Damn, that looked smooth and glorious. This is how I'd like the future to be."
- `claude-ai`："精准到几乎无聊——了不起的工作。"
- `Narishma` 追问：这次为什么没试着夹助推器？

https://news.ycombinator.com/item?id=49791300

---

### 7. 意大利以 Android 数据访问为由对 Meta 罚款 8.87 亿美元
路透报道，意大利监管机构就 Android 用户数据访问问题对 Meta 开出约 8.87 亿美元罚单。报道本身细节极少，HN 的讨论几乎全在质问"到底怎么拿到的"。

**为什么值得关注**：欧盟对平台数据实践的罚款正从"告知同意"扩展到"系统层权限"，这单可能成为后续判例。

**HN 讨论（300 分 / 208 评论）**
- `nsoam`：文章说得很含糊——是在 Android 上跑了什么利用链，才在没弹同意框的情况下读到照片？
- `tiohijazi`："所以 Meta 每次越界就交个罚款？那它会继续做。"
- `amelius`："等等，他们能看见我们卧室里在干什么，然后只被罚了一笔钱？"
- `iloveyoutwo` 顺手补刀：意大利自己在 Cellebrite 监控事件上也不干净；这两类事在 GrapheneOS 或 iPhone 上都不会发生。

https://www.reuters.com/world/italy-fines-meta-887-million-over-android-users-data-access-2026-11-14/

---

### 8. 太空数据中心：账算得过来吗
Forethought 的长篇评估，结论比标题党克制得多：可行性几乎全押在 Starship 复用成本上。入轨成本约 250 美元/kg 时，太空太阳能与当前离网地面电力打平；降到约 50 美元/kg 就比任何现有地面能源都便宜；而现在约 1500 美元/kg。被当成致命伤的辐射散热其实"出乎意料地好管"，甚至可能比地面便宜。真正的硬约束是芯片坏了换不了，五年周期要多带约 38% 的非计算硬件，以及星间带宽只够跑推理。判断是 2030 年前难成规模，若 Starship 按期推进，3–5 年内可有成本竞争力。

**为什么值得关注**：这是目前少有的、把"AI 算力—电力瓶颈—发射成本"串成一条可验证曲线的分析。

**HN 讨论（52 分 / 151 评论，分歧极大）**
- `kevin_thibedeau`："唯一说得通的位置是火星轨道，能少落地质量。其他都是为了把一堆失败生意并进 SpaceX 的说辞。"
- `groos`：超大太阳能阵列加抗辐射器件，经济上不可能成立，"又一个隧道式的天才点子"。
- `baxtr` 引用原文反驳：作者自己说比预想的可行，工程挑战大但没有不可逾越的。
- `ranger_danger`：已经在做了，Starcloud-1 在天上，Lonestar 在月球上还放了台备份服务器。

https://www.forethought.org/research/will-we-really-put-data-centers-in-space

---

### 9. CBC 调查后，LinkedIn 和 Monster 下架 1000 多个假招聘
加拿大广播公司调查曝光后，两家平台清掉上千条虚假职位。HN 的情绪不是惊讶，而是"才一千条？"

**为什么值得关注**：AI 生成内容让招聘信息这类"信任中介"型平台的质量控制彻底失效，而它恰好是求职者最脆弱的地方。

**HN 讨论（155 分 / 75 评论）**
- `bluecheese452`："现在大部分在线招聘都是假的。"
- `mococa`："15 年里我从没靠 LinkedIn 投递拿到过工作。"
- `reg_dunlop`：找工作期间自己写爬虫，发现过期 6 年的岗位还在挂，回信质问全部石沉大海。
- `Morromist` 把线拉大：路透说 Meta 有 10% 收入来自诈骗和违禁品广告，"互联网和国民经济的很大一块其实建立在骗人上"。

https://www.cbc.ca/news/canada/linkedin-monster-take-down-over-1-000-fake-job-postings-after-cbc-investigation-9.7415379

---

### 10. KDE 纪录片：CultRepo 出品
348 分、74 条评论，几乎是一代 Linux 桌面用户的情怀现场。片子记录了 KDE 从 Qt 早期、理念分歧、反复纠错到今天的全过程。

**HN 讨论**
- `blinkingled`：这不只是桌面环境的故事，也是"C++ 写大型软件、还要让大多数人用得下去"有多难的样本。
- `k0morebi`：用了 20 多年，"版本间一致、稳定、无限可定制，开箱又能用，功能经常领先商业竞品好几年。工作里用 macOS 或 Windows 的每一分钟都是折磨。"
- `sick_of_slop`：从 Ubuntu 16.04 的 GNOME 转到 CachyOS 上的 KDE，"再没回头"。

https://tube.kockatoo.org/w/fFinNHfanLT7aBEb2B8y4c

---

**快速扫过（未展开）**：Nvidia 被指通过循环融资刻意维持 GPU 高价（21 分，11 评论，信源单一）；Dartmouth 数学 PhD 今年停招（58 分，美国基础学科经费收缩的又一个信号）；Woz 在造出 Apple 1 之前是怎么写 BASIC 的（retrocomputing 讨论）；软件职位名称族谱（169 分，吐槽 title inflation）；可自启动 ZIP 归档的做法（38 分）；手机解锁工具技术综述（63 分）；Fursoy 乱序 RV64IMAFDV 核，能跑 Linux 6.6（65 分，SystemVerilog）；Rust + ratatui 写的终端放置工厂游戏（125 分）；强化学习可视化教程（108 分）；L3Harris 关于 11 月 13 日停飞的声明（7 分）。

已标记全部 20 条为已读。
