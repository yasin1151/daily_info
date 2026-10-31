
# HackerNews 每日精选（11 月 1 日）

扫描 20 条新帖，按讨论热度与信息密度筛出 10 条。以下均附 HN 评论原话。

---

## 1. Karpathy 做了个「HN 版 YouTube」：只推 HN 上被推荐过的视频
463 分 / 182 评论

Karpathy 上线 HackerTube，把 Hacker News 上历年被推荐的演讲、纪录片、技术视频聚成一个可搜索、可按主题筛选的视频站。首页不再是算法投喂，而是「HN 用户投票选出来的」。评论区一边鼓掌，一边有人担心站点哪天消失、想先把 URL 列表备份下来。

值得关注：提供了一种对抗「推荐流劣化」的样本思路——用社区投票代替算法排序。

> **privacyishuman**：我一直在想，能不能分享自己的 YouTube cookie，让别人直接继承你调教好的推荐算法？另外你这边能不能把 youtube-nocookie 的追踪器全挡住？
> **mentalgear**：周五晚上 11 点我累得不行，打开 YouTube，看到的就是一堵被劣化的垃圾墙。请把这套东西同样做给 Facebook、X、Reddit、Instagram。
> **vfclists**：源码在哪？我想照着搓一个自己垂直领域的视频站。

原文：https://karpathy.bearblog.dev/hacker-tube/ ｜ 讨论：https://news.ycombinator.com/item?id=50319510

---

## 2. Signal 分支 Molly 三个月没更新，被指存在未修补漏洞
291 分 / 167 评论

有人指出隐私强化版 Signal 客户端 Molly 自 7 月以来未发新版，而官方在此期间更新了协议与安全修复，Molly 沿用旧代码因此处于风险中。讨论很快转向更根本的问题：Molly 存在的理由（多设备、去 Google 推送）正被官方逐步补齐，第三方安全分支的维护成本由谁承担。

值得关注：安全软件的分支维护是长期成本，用户常高估「开源 = 安全」。

> **_heimdall**：真巧，昨天我还在想这事——主力机用 Signal，备用机用 Molly。Signal 昨天推了更新，我才意识到想不起来 Molly 上次更新是什么时候。
> **ada-h00k**：有时候我觉得 Signal 讨厌非普通用户。Unified Push 在 Molly 上跑得很好，官方客户端要做也不难；F-Droid 版、彻底不要 Google 的版本也一样。他们就是不做。
> **jttnr**：今天才知道官方 Signal 已经支持一个账号分两个设备用了——那正是我当初用 Molly 的主要理由。

原文：https://piefed.world/post/1503394 ｜ 讨论：https://news.ycombinator.com/item?id=50314666

---

## 3. 安全团队复盘：怎么用一个链接接管 ChatGPT 账号
293 分 / 142 评论

Parameter 实验室公开了 OpenAI 的一个漏洞链：攻击者只要让受害者点开一条链接，就能接管其 ChatGPT 账号。文章写明 OpenAI 前后端都拒收了上报的消息、随后修复，并支付了 5000 美元总赏金。HN 的争论不在技术细节，而在赏金太低，以及这类「点链接就中招」的漏洞在大模型产品里正变成常态。

值得关注：AI 产品把浏览器、插件、文件系统权限揉在一起，攻击面比传统 SaaS 大得多。

> **yellow_lead**：OpenAI 确认两个前端都拒收了上报的消息、问题已修复，总赏金 5000 美元。虽然要用户点链接，但这赏金还是太低了，别人以后可能就不报了。
> **lxgr**：再叠加上「只要在 ChatGPT 桌面版里开过一次 Work 聊天，就能被远程访问文件系统」这件事，感觉相当糟糕。
> **15o9o**：我们快走到「还要密码干嘛」的地步了。是不是以后就靠荣誉制度：拜托别用我的账号登录？

原文：https://www.parameter.ai/labs/we-found-a-gap-at-openai ｜ 讨论：https://news.ycombinator.com/item?id=50314699

---

## 4. Linux IPv4 TCP 释放后使用漏洞，CVSS 9.8，可 root 远程执行
249 分 / 117 评论

复盘文章描述 CVE-2026-98432：内核把 request socket 里保存的 TCP 选项直接交给新连接而未拷贝，随后立即释放，另一个 CPU 仍可能读取——典型的多核竞态 UAF。Anthropic 称 Claude 在「初步提示后」写出了利用，在多路径 TCP 监听的服务上无需凭据、无交互即可 root 执行任意命令；PoC 中先花 48 分钟泄露内核指针，再用 5 分钟拿到 shell。评论区最刺眼的一句是：Ubuntu 和 RHEL 怎么还没修。

值得关注：既是内核级 9.8，也是「AI 挖洞并写利用」进入实战的标志性案例。

> **mrob**：如果真需要多核才能触发，那对大多数永远收不到更新的消费级路由器反而是好消息——被廉价单核硬件救了。
> **swinglock**：Ubuntu 和 RHEL 怎么会还没修？没有哪个系统比它们更把自己宣传成服务器专用，他们那边到底在干什么。
> **wiskinator**：有百分之多少的 TCP/IP 服务是「多路径」的？另外 IPv6 不受影响，要是这个漏洞才逼得大家上 IPv6，那还挺好笑。

原文：https://atlasum.net/blog/cve-2026-98432-linux-ipv4-tcp-uaf ｜ 讨论：https://news.ycombinator.com/item?id=50319143

---

## 5. GCC 是怎么把 switch 编译成跳转表的
195 分 / 36 评论

长文拆解 GCC 的 switch lowering 流程：什么时候生成跳转表、什么时候退化成二分查找、密集与稀疏 case 的阈值判定，以及「跳转表里再套一层跳转」这种反直觉的间接跳转是怎么来的。核心是编译器要在代码体积、缓存局部性和分支预测之间做取舍。

值得关注：想理解「为什么我的 switch 慢了」，这是最直接的一手材料。

> **sylware**：想窥探硬件推测和 BTB 的行为，看 switch lowering 是个好路子。大 switch 会做很复杂的变换去讨好硬件，因为它天生就是分支预测失败的重灾区。
> **rurban**：clang 和 gcc 到现在都没给大型稀疏 switch 实现完美哈希，挺可惜的。我在自己的 C 编译器里做过，一天就写完了，对 Unicode 处理特别有效。LLVM 那个 patch 十年前被拒了。
> **tsukikage**：为什么要多一层间接？跳转表为什么不直接指向 f0..fX，而要跳到一个跳转？

原文：https://xoranth.net/gcc-switch/ ｜ 讨论：https://news.ycombinator.com/item?id=50314085

---

## 6. Jepsen 拆了台「形式化验证」的数据库：96 个问题
170 分 / 94 评论

Jepsen 对 ParticleDB 1.1.4 的报告罕见地严厉：共列出 96 个问题，从崩溃、死锁、丢数据，到「WHERE 4 = 5」、删不掉的半可见行、被删的表以扭曲形态复活、字符串变整数。而它官网此前主打「Written in Rust、TLA+ 形式化验证、兼容 PostgreSQL」。HN 普遍认为这是「AI 生成基础设施」最典型的一次翻车。

值得关注：形式化验证的宣称和实际正确性之间可以差多远，这份报告是教科书级案例。

> **the_duke** 引原文：1.1.4 声称是 PostgreSQL 兼容数据库……我们发现的是一个混乱库，在我们能测的几乎每个维度上都表现出深刻的 transactional 异常。提交成功的写入会稳定丢失。
> **Powdering7082**：ParticleDB 首页宣传自己「已被 TLA+ 形式化证明」。也许他们想说的是「formerly（曾经）」，大概是个语音转文字的问题。
> **Thaxll**：Rust 写的 slop DB。他们大概是在结果变难看之后改了 landing page，旧版还能在 Wayback 里看到：Written in Rust · Formally Verified · PostgreSQL Compatible。

原文：https://jepsen.io/analyses/particledb-1.1.4 ｜ 讨论：https://news.ycombinator.com/item?id=50316100

---

## 7. GPT-5.6 Sol 打通了 Factorio（和平模式）
148 分 / 159 评论

作者让模型在和平模式下玩 Factorio，最终发射了火箭。但文章自己承认：这个成绩靠大量「人工介入」——Sol 后期没能把生产系统正确连起来，只能靠反复在区域间搬运物资把产量硬凑上去。评论区因此分裂：一派说这就是又一个被夸大的 demo，另一派说能长期规划到发射火箭本身已经不容易。

值得关注：衡量 agent 能力时，「人类兜底了多少」往往比「它做成了什么」更关键。

> **mwt** 引原文：火箭发射只是靠 Sol 大量「手动」努力才实现的，它靠不断在厂区之间搬运物资，掩盖了自己后期没能连通生产系统的失败。然后补了一句：机器人：跟我们一模一样。
> **VoidWhisperer**：Factorio 没有虫子骚扰、扩张不痛苦的时候简单太多了。我很好奇 Sol 会怎么处理虫群。
> **dfedbeef**：知道它至少有一件事擅长，也算是安慰吧。Sol 感觉总是在浪费我的时间，还写一手烂代码。

原文：https://ryanmadden.net/gpt-56-beats-factorio/ ｜ 讨论：https://news.ycombinator.com/item?id=50318871

---

## 8. Anthropic 封号：只要涉及「训练更大的模型」
128 分 / 39 评论

一条 X 帖子称用户在 Claude 上做与训练大模型相关的工作就会被封号，引发讨论。最高赞的冷静解释是：该用户位于香港，Claude 本身对该地区封锁，只能走 VPN；用 VPN 做大模型训练相关操作本身就是极强的可疑信号，触发分类器并不奇怪。也有从业者说自己用 Claude 训 BERT 一直没事，界线大概在「让模型帮你标注训练数据」这一步。

值得关注：AI 厂商的 ToS 执法正在变成事实上的能力管制，边界模糊且不透明。

> **tristanj**：这个用户在 Hong Kong，Claude 在那里是被地区封锁的，访问会直接提示不可用。他很可能在用 VPN。通过 VPN 做大模型训练相关的工作是高度可疑的信号，会触发 Anthropic 的分类器，被封不奇怪。
> **gdiamos**：我的底线是让 Claude 帮忙标注训练数据，这个我不做。问它关于大 MoE 的问题我天天问，从来没被拒过。要训练数据我就让开源模型自己往外吐。
> **nubinetwork**：有点旧闻了，他们已经这么干好几个月了。

原文（X 帖）：https://twitter.com/jiahaoshao1/status/2116475922190922088 ｜ 讨论：https://news.ycombinator.com/item?id=50319358

---

## 9. 瓶颈是内存延迟，不是带宽
92 分 / 27 评论

文章主张：现代优化的主要矛盾已经从「数据搬得够不够快」转向「访问的延迟」——指针追逐、缓存未命中、跨 NUMA 的随机访问，都是延迟问题而非带宽问题，所以数据结构布局（数组 vs 链表、索引 + 世代号而非指针）比换硬件更有效。评论区一位嵌入式工程师用亲身对比佐证：同一颗芯片上，用机械同情心写的数据结构比「现代 C++ 风格」快一个量级。

值得关注：所有「为什么扩容后反而更慢」的问题，都值得先看一眼内存访问模式。

> **boricj**：我另一个团队在 STM32MP1 上用大量消息传递、深层继承的 C++ 虚函数、大 DOM 和现成 STL 容器，那芯片只有顺序执行的 Cortex-A7 和少得可怜的缓存。我这边在不到 1MB RAM 的 STM32H5 上，自己写了内联分配的容器、SAX 解析和索引 + 世代号的对象池。机械同情心在很多人眼里已经是一门失传的手艺。
> **brcmthrowaway**：Ulrich Drepper 那篇《What Every Programmer Should Know About Memory》有人按 2026 年的硬件重写一遍吗？
> **drivebyhooting**：我觉得文章给的方案本质就是一个聚簇哈希表，或者说「局部性敏感」的索引。还是没有数量级的提升。

原文：https://pivotlake.io/blog/its-the-memory-latency-stupid/ ｜ 讨论：https://news.ycombinator.com/item?id=50318720

---

## 10. Show HN：一个 USB-C 的 LTE 猫，给电脑接一条真正的电话线
41 分 / 31 评论

作者做了一块 4 层 USB-C 板，围绕 Quectel EC25-EUX 模块，让电脑同时看到一个 LTE 网卡、一组 AT 串口（来电显示、短信、接听）和一个由 RP2040 充当的 USB 声卡，从而在自己的耳机上接打电话，或交给脚本 / AI agent 代接。动机很具体：云号码会被当 VoIP 处理，旧安卓机没法干净地把通话音频通过 USB 进出。评论区主要质疑 VoLTE——2G/3G 退网后这块板可能几年就变砖。

值得关注：硬件黑客对「AI agent 需要一个真实电话号码」这个需求的直接回应。

> **gruez**：2G/3G 已经关停的地区，通话需要模块固件支持 VoLTE、且运营商允许——这是个巨大的前提。请问你的方案到底支持 VoLTE 吗？否则运营商一关网，这东西就成砖了。
> **Vaushite**：很明显是 AI 味十足的产物，意味着这项目大概从没被真正做出来，做出来也跑不通。
> **mcculley**：这个太棒了。Apple 该想想怎么把它塞进 16 寸 MacBook Pro。

原文：https://github.com/Koppar-AI/koppar-lte-modem ｜ 讨论：https://news.ycombinator.com/item?id=50317331

---

**已跳过**：意大利农民的老种子、Distributed Proofreaders、动漫词汇覆盖率、Dustin Hoffman 访谈、Casio 80 年代手表、Nordhaus 讣告、塞尔维亚议会学历、The Duty of a Scholar（属政策评论）。

20 条新帖已全部标记已读。
