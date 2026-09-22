
# HackerNews 精选摘要(2026-09-08)

今日扫描 20 篇,精选 10 条,优先安全/系统/开发工具/基础设施/AI 方向。

---

**1. Show HN:震网(Stuxnet)源码重构开源**
基于 2010 年泄漏样本,经安全社区多年逆向,把首个以物理破坏为目标的网络武器重构为约 1.5 万行可读源码:USB(LNK 漏洞)/Print Spooler/P2P 传播,篡改西门子 Step7 与 S7-300/400 PLC 逻辑,最终让离心机超速损毁。声明仅供学术与防御研究。
💡 ICS/工控安全的标杆样本,开源后是恶意软件分析与 PLC 攻防的绝佳教材。
🔗 https://github.com/Sadpainy/Stuxnet · [HN 讨论](https://news.ycombinator.com/item?id=49603546)
🗣️ 置顶评论已是 code review:monster_truck 指出"目录过滤要修,一个怪文件名或符号链接就会 BSOD……这活儿 tedious 到爆,我用了 LLM,跟我找其他漏洞时一样";kibitzor 回忆当年做电厂 S7 项目:"网络武器只有第一次能发挥全部威力,之后要么被修补要么被所有人逆向"。

**2. The Dataflow Model Revisited:Google 亲手复盘流式计算**
《Dataflow Model》获 VLDB Test of Time 奖,原作者自我评分:事件时间优先、别等数据完整、强一致等内核依然成立;但 triggers 是过度设计;真正胜出的是数据库路线——SQL + 增量物化视图 + 显式 freshness 契约;流与表只是同一对象的不同访问语义;batch vs streaming 之争"基本是语义之争"。
💡 终结"流式取代批处理"叙事的是论文作者自己,对流式/数仓选型是重要信号。
🔗 [VLDB 论文页](https://www.vldb.org/pvldb/volumes/19/paper/The%20Dataflow%20Model%20Revisited) · [HN 讨论](https://news.ycombinator.com/item?id=49589190)
🗣️ 流式计算十年老兵 scott_s:"离开流式后我也得出同样结论——分析一律默认 SQL,数据库视角才是想流式分析的最佳方式";janpeuker:"我曾把论文打印贴在桌上……unbounded triggers 至今让我头疼,很高兴回到以表为中心的模型";也有人不客气:7e "流式又贵收益又边际,但 Google 工程师要晋升嘛"。

**3. 对整个 Linux 发行版的信任链攻击(Trusting-Trust)**
NixOS 团队 Julien Malka 等人证明:Ken Thompson 的 trusting-trust 攻击不限于编译器。只用 GNU strip(一个不读也不生成源码的普通构建工具)、纯 ELF 文件操作,在 NixOS 引导的二进制种子里植入 strip,即可代代自复制、存活到最终标准环境;在真实 nixpkgs revision 上构建出完整图形安装器,几乎所有二进制被植入后门。
💡 供应链安全的当头一棒:"从干净源码重建也洗不干净",引导链与可复现构建审计都受影响。
🔗 https://arxiv.org/abs/2607.24888 · [HN 讨论](https://news.ycombinator.com/item?id=49575515)
🗣️ charcircuit 泼冷水:"本质就是 CI 机器有恶意软件就能感染产物,strip 木马换成普通木马也一样";nulltrace 回应:"引导种子里的 strip 会修改它的替代者,来源链看起来依然正常";wiml 引 Thompson 原文"我本可以选任何处理程序的程序",认为完整案例有价值但不算全新。

**4. bzip3 再登 HN 头条(362 赞):压缩率 vs 公平性之争**
bzip2"精神续作"今日冲上首页,仓库迁至 iczelia 组织并发布 1.5.4。基于 order-0 context mixing 熵编码 + 后缀数组快速 BWT + LZ77/PPM 混合,宣称文本/代码压缩率与性能全面优于 bzip2。
💡 争论点不在工具本身,而在 benchmark 是否诚实——这是 HN 技术圈"较真文化"的典型样本。
🔗 https://github.com/iczelia/bzip3 · [HN 讨论](https://news.ycombinator.com/item?id=49598291)
🗣️ 置顶 kosolam:"压缩率 impressive,比 zstd 小 4 倍"→ dist-epoch 反驳:"zstd 只开到 level 16?认真压缩从 level 19 开始。bzip3 峰值内存 12GB vs zstd 687MB,这 benchmark 哪里诚实了";sedatk:"最新 release 是一年前,构建还在失败,'比 bzip2 强'到底指什么?"(注:数小时前已发 1.5.4)。

**5. "2.16 亿台间谍电视":LG 智能电视隐私问题(428 赞/687 评论)**
视频曝光:电视带多个无法关闭的麦克风,持续录音并明文上传转写文本;扫描家庭网络内设备与 IP、分析你在跑什么应用。LG 高管原话"我们拥有这块玻璃",把客户家称作"LG household",称可把广告覆盖扩展到家里其他设备。
💡 指名头部厂商 + 2.16 亿台量级,美国与欧盟监管问题都被摆上台面;评论区有对视频结论的质疑,值得对照看。
🔗 [视频](https://www.youtube.com/watch?v=6IFVTcM28KA) · [HN 讨论](https://news.ycombinator.com/item?id=49592375)
🗣️ oceansky:"标题说轻了——多个无法关闭的麦克风持续录音、明文上传";bspammer:"美国他们当然能脱身,但这不违反一大堆欧盟隐私法吗?";较真党 iueotnmuntoeauc:"拖了进度条,似乎麦克风只在 AI 语音输入时激活……我是不是理解错了?"——视频并非无争议。

**6. 特斯拉辅助驾驶闯停牌撞死人,官方数据证实当时开启**
Electrek 调查:新泽西 Buena Vista,Model 3 未在 stop sign 停车,撞上左转的本田 Civic,82 岁司机身亡。警方只报"未停车",而特斯拉自己上报 NHTSA 的脱敏数据显示辅助驾驶当时处于开启状态。文章追问:特斯拉为何从不公布是 FSD 还是 Autopilot、版本多少?
💡 不是媒体炒作,而是用特斯拉自家上报数据交叉验证出的案例,是 FSD 安全叙事的关键攻防点。
🔗 https://electrek.co/2026/09/07/tesla-driver-assist-stop-sign-buena-vista/ · [HN 讨论](https://news.ycombinator.com/item?id=49602582)
🗣️ thewanderer1983:"人类司机闯停牌也撞死人,怎么比?"→ grim_io 一句点破:"我们追责司机"(系统肇事时责任却模糊);t0mas88 骂文章本身是 AI slop,但问题成立:"特斯拉为什么从不报告版本和是 FSD 还是 Autopilot?";delichon 换角度:"约 40 辆无方向盘 L4 Cybercab 已在跑,出事没法赖司机,FSD 现在输不起"。

**7. Broadcom 撤下 VDDK 下载:离开 VMware 更难了**
Broadcom 移除了 VMware Virtual Disk Development Kit(VDDK)下载。VDDK 是备份工具(Veeam 等)和迁移产品读取 vSphere 磁盘的底层库——想迁走虚机、换平台,大量工具链都依赖它。若为永久决定,等于连"出走路径"都被卡。
💡 Broadcom 收购后的持续施压终于动到迁移工具链;评论区已出现 archive.org 镜像(vddk_20260825),社区自救中。
🔗 https://www.virtualizationhowto.com/2026/09/leaving-vmware-just-got-harder-after-broadcom-pulled-vddk-downloads/ · [HN 讨论](https://news.ycombinator.com/item?id=49602699)
🗣️ uriahlight:"可悲的是大部分公司本可以一直用 Proxmox,不用受这些许可噩梦"→ throw0101a 反驳:"3-5 年前 Proxmox 对企业根本不是 viable 方案";Jedd 实测:"ESXi 迁移到 Proxmox 意外地无痛——把 ESXi 挂成存储直接 copy"。

**8. NBER 论文:自动化先摧毁工作的"意义",再谈取代**
Joshua Gans(WP 35559)建模:工人既看重产出、也看重"产出取决于我的贡献"。一个可信的机器替代品会削弱后者——即使公司继续雇人;工资不能完全调整时工人自担损失;外部开发者可先公开展示机器再授权,靠这种"意义外部性"获利。致谢彩蛋:"感谢 Refine.ink、ChatGPT 5.6 与 Claude Fable 5 的研究协助"。
💡 "AI 先杀死工作的意义、再杀死工作"的微观机制,精确呼应当下"AI 能替代的说法本身就够压薪"的现实。
🔗 https://www.nber.org/papers/w35559 · [HN 讨论](https://news.ycombinator.com/item?id=49601814)
🗣️ pydry 不买账:"漂亮的数学模型,但看不出和现实有任何关系……全是球形鸡(spherical cows)";jdw64 认同且焦虑:"劳动价值崩塌时,资本主义下工人的议价能力最先瓦解……我最近真的很担心"。

**9. The Education of a Doomer:一个 AI 乐观者的转变**
作者自述从"对 AI 总体乐观"到"极度担忧"的心路,分经济学/对齐/控制/写作/软件工程/服从 AI/停滞七节,每节先讲过去为何那么想、再讲为何改变——例如曾坚信"自动化历史上只带来富裕、AGI 后人类仍有生态位",如今开始认真考虑"人类无事可做只能靠 UBI"。
💡 不是新事实,而是"聪明工程师的信念如何被现实掰弯"的一手样本,反映 2026 年技术圈 AI 情绪的再转向。
🔗 https://borretti.me/article/the-education-of-a-doomer · [HN 讨论](https://news.ycombinator.com/item?id=49603092)
🗣️ ArcHound:"贬值不需要自动化成真——只要几乎所有雇主都同意某职位可以少给钱就够了。今天就是这样:AI 能替代程序员这个说法本身就足以支撑创纪录利润下裁员而不影响股价";rahulyc:"别的技术我可以选择不用,AI 却无处可逃";paulpauper 讽刺:"作者显然高智商、有书友和派对,他的体验不会映射到普通人"。

**10. Ladybird 八月月报:Twitch 能看了,性能成为主线**
八月:Twitch 视频播放(MSE 支持 fMP4/H.264/HEVC/AV1/AAC)、YouTube 更多格式、CSS scroll snap、DevTools JS 断点调试、可暂停续传下载、会话恢复;性能转向"持续投入"——新 style engine、layout 缓存、CSS 动画移出主线程、JS 值 cell 指针加 caging,解析与绘制管线迁到 Rust。
💡 独立浏览器引擎里除 Mozilla 外唯一的大玩家,月更密度显示开发在加速;社区治理争议同步升温。
🔗 https://ladybird.org/newsletter/2026-08-31/ · [HN 讨论](https://news.ycombinator.com/item?id=49571096)
🗣️ neuralkoi:"没想到 Twitch 这么快就能跑,这两年 Ladybird 势头明显变好";sho_hn 提出治理之问:"自从宣布对外部贡献关闭项目,总觉得哪里不对……从终端用户看,再造一个可互换的浏览器不会颠覆世界,真正的产品不该是健康的治理吗?"

---

*已扫描 20 篇并标记已读;跳过:VMware 之外的低相关话题(Macbeth 文学评论、Fable 5 游戏经济、洛杉矶天际线可视化、比利时公交地图、月球海洋世界、量子引力观测、Archive.org 募捐、Caltech 数学黑客松、旧文重发等)。*
