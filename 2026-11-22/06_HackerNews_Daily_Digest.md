
**HackerNews 每日精选 · 2026-11-22**
（扫描 20 条，新增 17 条，筛选出 10 条技术价值较高的内容）

---

### 1. Lean 社区正式认证：黎曼猜想的机器验证证明成立
🔗 https://leanprover-community.github.io/blog/posts/riemann-hypothesis/ ｜741 分 / 592 评论

11 月 20 日，Levent Alpöge 以 Lean 库的形式发布了黎曼猜想的证明，代码规模 1700 万行。Lean 与 Mathlib 社区当天联合发表声明，逐项确认了四件事：命题本身即 Mathlib 中经过专家审定的 `RiemannHypothesis`；“证明的确实是这个命题”，这一点用 comparator 与 con-leche 两个独立工具比对过；代码能够无错编译，并有多人复现出相同的 raw proof 导出；导出的原始证明被 Lean 官方 kernel、con-leche、con-ron 以及多个用不同语言实现的第三方检查器分别验证通过，而且是在与源码隔离的惰性导出上运行的，以防恶意代码干扰。最值得注意的是，con-leche 和 con-ron 自带基于集合论的元证明，说明“它们不会接受假证明”。

**为什么值得关注**：这是形式化数学第一次以社区可复现的方式处理“世纪难题”级别的成果，从此“证明”的可信度不再只依赖同行评审。

**HN 上的真实反应**（评论区明显分为激动与怀疑两类）：
- **dathinab**（11 条回复）：“but is it useful?? because a million+ lives of code without any understanding how the proof works or any methodic to advance the field of mathematics seems to be rather not so useful” —— 意思是：代码量达到百万行级别，却没有人真正理解这个证明是怎么运作的，这算不算有用？
- **1970-01-01**：“Isn't this the equivalent of aliens coming to Earth and saying 'Hello, human, your Riemann question is true, here's a book on it's proof, we didn't bother with translation'” —— 他给的比喻很刻薄：这就像外星人降临之后说“你的问题为真，书在这里，我们懒得翻译”。
- **iandanforth**：真正有趣的，是把 Alpöge 与 Masullo 两人的思路结合起来之后会带来哪些简化。**alexey-salmin** 则调侃：万一 Lean 自己有 bug，而 Claude 靠蛮力挖出了漏洞，用它证出了错命题（那就搞笑了）。
- 也有 **pera** 追问：con-leche 凭什么能“绝对无 bug”？

---

### 2. Inkling-2-Mini 压缩到 5.4GB：一种新的“量化编译器”
🔗 https://github.com/ShinMegamiBoson/lookatmyquant ｜310 分 / 79 评论

LookAtMyQuant 的思路与常规量化不同：它先衡量“每一块被存储的权重在压缩时对最终输出的伤害有多大”，再以此为每块权重挑选编码方式，从而在文件大小预算下把总损失压到最低。作者给出的数据是：同尺寸下，Gemma 4 E2B 的 GGUF 相比 Q4_K_M，KL 散度低 12 倍；Qwen3.5-4B 被压到 1.23GB（2.3 bit/weight），540 道精确答案数学题解出 330 道，而 Prism ML 的 Bonsai 2 Ternary 4B 解出 328 道（该模型原版解出 359 道）；Qwen3.8-27B 从 53.7GB 降到 7.2GB，数学成绩与原版打平（401/540），而 Unsloth 同尺寸的 UD-IQ2_XXS 为 348 道，并且在 HumanEval、MMLU、GSM8K 三项上都领先。整个配方在蒸馏环节只花了约 34 美元 GPU 时间。

**为什么值得关注**：这是“在本地跑大模型”的一条实际可行路线——把 26B 的 MoE 模型塞进 5.4GB，并且在 Apple Silicon 上还能配一个 drafter 来加速解码。

**评论里的质疑同样尖锐**：**woadwarrior01** 直接贴出模型卡：“The model is distributed as a single checkpoint of about 20GB, in mixed NVFP4 and MXFP8 precisions. What's the point in quantizing a QAT model? Just for social media karma?” —— 既然原模型本身就是量化训练过的，再量化一遍有什么意义，难道只是为了社交媒体上的点赞？**Dwedit** 问这套方法与传统 importance matrix 相比如何；**IronWolve** 追问是否只有 MLX 版本。

---

### 3. 我的显示器把下载速度砍掉 75%
🔗 https://blog.tymscar.com/posts/studiodisplayethernet/ ｜436 分 / 216 评论

作者拥有 2.5G 对称宽带，某天却发现下载只有 600Mbps，上传仍为 2.4Gbps。排查后发现，问题出在他为了“一根线搞定”把 USB-C 2.5G 网卡插到 Studio Display XDR 上：直插 Mac 时能跑到 2.3Gbps，而经显示器连接就只有 600Mbps。pcap 和系统日志里都没有掉帧错误的记录，说明是网卡自己先把包丢了、没上报。换成 Realtek 官方驱动后，速度提升到 1.1Gbps；打开流控（pause frame）后升到约 2Gbps，但作者不想让它一直开着。他的最终解释是：经显示器连接时，Mac 侧的 ACK 回得慢，USB 网卡缓冲被打满后只能丢包；而他换的 RTL8157 网卡每次 burst 从 4 个 1KB 包变成 8 个，链路速度也翻倍，等效带宽超过 4.5Gbps，于是缓冲不再溢出。看 USB 描述符（`wMaxPacketSize` 与 `bMaxBurst`）就能验证这两种网卡的差异。

**为什么值得关注**：一次教科书式的底层排查——从“谁在丢包”的假设出发，一路查到 USB 的 burst 描述符，中途并不需要拆机或更换 ISP。

**HN 上讨论得很热闹**（其中不乏指出原文理解有误的）：**fancyfredbot** 替作者澄清：“lots of comments misunderstood the article, the extra latency from going through the monitor meant his laptop couldn't acknowledge the packets quickly enough. That led a buffer on the ethernet adapter to fill and that led it to drop packets.” **TacticalCoder** 总结成一句经验：“it's always some weird USB thing”（它总是某种奇怪的 USB 问题）。**candl** 站在运维立场吐槽：“I hate this attitude: 'I wasn't getting three quarters of the speed I was paying for'. No, you were. It was not the ISPs fault.” —— 速度没给满并不是 ISP 的问题，问题出在用户自己加装的设备上。**entrope** 则批评标题党的成分。

---

### 4. GnuPG 严重漏洞：一行超长 user id 触发 double free，可能导致 RCE
🔗 https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html ｜221 分 / 88 评论

Werner Koch 宣布 GPGME 2.3.1，修复一个存在于此前所有版本中的严重漏洞（CVE-2026-129975，内部编号 T8557）。触发条件是：OpenPGP 密钥的 user id 极长，从而导致 GPGME 内部读取 gpg 状态行和密钥列表的两个函数在 realloc 之后、指针写回 context 之前提前 return，于是 context 里留下的仍是已经释放的旧指针，造成 double free。这个漏洞可以用来从应用中泄露数据（例如在对方发送带签名的数据时），并且“不能排除”升级为远程代码执行的可能。该漏洞由 Johan Carlsson 发现，GitLab 于 11 月 12 日通知，原定 11 月 25 日协同披露，但因为 Ruby2Shell 的缘故提前到今天。Gpg4win、GnuPG Desktop 等版本已同步更新。

**为什么值得关注**：GPG 是软件供应链签名的底层依赖，凡是经由 GPGME 处理签名的地方（GitLab 签名提交就是一条路径），都需要立刻升级。

**评论区的实用信息**：
- **uptrails**（3 条回复）指出一个尴尬事实：“Reportedly fixed by Red Hat 5 years ago based on the output from conventional tools, but missed by upstream.” —— Red Hat 五年前就修过这一类问题，但上游没有合并。
- **usr1106** 追问实际攻击面：普通开发者大多没有 GPG key、也不验证签名，但发行版的包是用 GPG 验证的；“Is the vulnerable component involved or not?”（这个易受攻击的组件到底有没有被涉及？）
- **miduil** 补充了 GitLab Omnibus 的对应补丁链接，并说明这次提前披露的压力来源。

---

### 5. Show HN: Zero C#：没有 runtime、没有 GC 的 C#
🔗 https://onurgumus.github.io/zero-csharp/index.html ｜115 分 / 92 评论

基于 bflat 的一个分支直接把 C# 编译成很小的原生程序：没有 .NET runtime，没有垃圾回收，目标机上什么都不用安装。语言层面保留的类型检查和泛型都在（C# 15 的 unions、真实泛型按类型特化、默认接口方法、records、lambda 与 Where/Select），内存改为从 arena 分配、由你一次性整体释放；去掉的是 GC、异常捕获（`throw` 会直接终止程序，改用 union 返回错误）、反射和 async。Hello world 在 Windows 上为 11KB、Linux 上 40KB。同一份源码可以在 Linux、macOS、Windows、WASM 以及 DOS 的 386 上运行。

**为什么值得关注**：它把“C# 的语法 + C 的运行模型”做成了一条真实可达的路径，对小体积、可嵌入、复古平台的场景很有吸引力。

**评论直接开火**：**OnceMoreUntoThe**：“this is just a bunch of AI slop... I really don't get all the CLR GC hate?” 并举例说，自己的 .NET 10 工业相机监控系统连续跑了三个月没出问题。**bob1029** 站在相反的立场为 GC 辩护：“The GC is a feature. Not a bug to be eliminated. GC is not surrendering control.” **amelius** 担心“没有 GC”意味着把垃圾攒起来、很久才清一次；**dosshell** 认为引用计数更符合 C# 哲学（像 Swift）；**kvuj** 和 **raincole** 则指出，C# 早已有 unsafe 指针、Marshal、Span 和 NativeAOT，质疑“是否真的需要 fork”。andyfilms1 只留了一句：“Finally, C--”。

---

### 6. 用 Go 写 PostgreSQL 扩展：gopgext
🔗 https://jespino.github.io/gopgext/ ｜105 分 / 14 评论

借助 TinyGo，把普通的 Go 代码编译成 PostgreSQL 扩展：标上 `//gopgext:function` 就是一个 SQL 函数，C 胶水、install 脚本、control 文件全部自动生成。标准库可用（fmt、regexp、encoding/json、crypto/*、maps、泛型、iterator、defer/recover），类型可映射到 SQL，自定义类型和复合类型也能写；通过 SPI 执行 SQL、返回带 SQLSTATE 的错误、响应查询取消。不止函数，还能写触发器、聚合、GiST/GIN/SP-GiST/BRIN 算子类、索引访问方法、FDW 和 query hook，并且已经移植了 pgcrypto、hstore、pg_stat_statements 等 contrib 模块作为可行性证明。作者明确标注 experimental：生成代码或 Go runtime 里的 bug 是跑在服务器进程内的，可能直接导致崩溃或数据损坏，别上生产。

**为什么值得关注**：PostgreSQL 扩展长期是 C 的天下（踩内存错误就整个数据库挂掉），用带边界检查和 GC 的语言写扩展，是能显著降低事故率的路线。

**评论**：**ltbarcly3**（4 条回复）贡献了最直接的反方意见：“LLMs make 'I need to shoehorn a language I already know well into an environment where it doesn't really belong' an unnecessary extravagance. Just have an AI write plpgsql.” —— 直接让 AI 写 plpgsql 就好，不必强行把语言塞进不属于它的环境。**Wicher** 提到另一个同类项目 plgo；另外还有两条评论在聊 Go 的 gopher 吉祥物，以及暗色模式下看不见括号的文档问题。

---

### 7. Upload2Shell（CVE-2026-125396）：Ghostscript 沙箱逃逸
🔗 https://pwn.ai/upload2shell ｜60 分 / 20 评论

Ghostscript 的 Type 1 字体加载器存在一个 use-after-free：精心构造的文档可以越过 `-dSAFER` 沙箱，篡改原生路径控制，并以渲染进程的身份执行攻击者指定的命令。pwn.ai 给出的时间线是：7 月 27 日发现可利用的逃逸路径；7 月 30 日在 Google 的文档渲染器上完成生产环境验证，即一个未登录请求居然能命中攻击者托管的文件并最终触达 Ghostscript，随后报告给 Google；8 月 12 日 WordPress Core 修复（CVE-2026-65640，Author 及以上角色、以及任何被授予 upload_files 的 Contributor 都能触及上传路径，多个插件的公开上传字段甚至不需要登录）；9 月 8 日 Ghostscript 10.08.0 上游修复。

**为什么值得关注**：Ghostscript 藏在打印、邮件附件、图片上传的预览链路下面，一个 .png 文件就能走到它。Web 应用只要存在“上传后由服务端转换图片”的功能，就处在攻击面上。

**评论**：**baggy_trough** 一句话总结：“If you want to use Ghostscript in a secure manner, you're going to have a bad time.” **philipwhiuk** 批评命名和披露流程：“Weird title. Feels like it should be GhostScript2Shell.” 还有不止一人吐槽这页根本读不下去，**dabinat** 说：“This seems like important information but this page is completely unreadable.”

---

### 8. 给接下来 100 个 Rust GUI 的建议（Raph Levien）
🔗 https://linebender.org/blog/next-100-guis/ ｜25 分 / 1 评论

这是 4.5 年前那篇《给接下来十几个 Rust GUI 的建议》的续篇。核心判断是：Rust GUI 的动机依然成立（Electron 的臃肿、平台官方 toolkit 停滞、RAM 昂贵且注意力转向移动端），而过去几年先后冒出约 20 个 toolkit，真正落地的旗舰只有 Zed 的 GPUI；GPUI 正在成为 AI 驱动重写时的热门选择（最典型的是 Discord），但它 2D 渲染器缺少渐变、混合、滤镜，未必适合通用应用。作者认为“采用慢”的最大原因——Rust 难写、同时懂 Rust 和 UI 的人少——正在被 AI 消解：有证据表明用 LLM 写 Rust 的成本并不比写其他语言高多少，而在大代码库里 Rust 的类型系统更有利于长期维护。结论是 UI 层还没有共识，未来会有一轮“各种方案都试一遍”的爆发；移动端则应使用平台原生 toolkit 做 UI、把业务逻辑用 Rust 写。

**为什么值得关注**：这是少数既讲技术判断、又讲清楚生态策略的行业观察，对选型（GPUI vs. Vello/Skia 这一代的 toolkit）有直接参考价值。

---

### 9. PcapAnalyzer：自托管的 pcap 分析器，27 个问题检测器
🔗 https://github.com/sebaandrada-cell/PcapAnalyzer ｜21 分 / 2 评论

上传 .pcap/.pcapng（支持 gzip），它会告诉你哪个环节出了问题、为什么、下一步该查什么。27 个检测器覆盖：TCP 层（防火墙丢 SYN 导致的 RST、重传、重复 ACK、丢包与乱序、零窗口/满窗口、握手后的 RST、慢握手）；路径层（PMTUD 黑洞、低 MSS、IP 分片、ICMP 错误、路由环路）；名字与地址服务（DNS 无应答/慢应答、SERVFAIL、NXDOMAIN 突增、DHCP NAK、IP 冲突、ARP 风暴）；应用层（HTTP 4xx/5xx、TLS alert、SSL3.0/TLS1.0）；隧道（IPsec、WireGuard、OpenVPN、GRE、L2TP 单向不通）；安全（端口扫描、明文登录、Telnet/SMBv1/SNMPv1-2c、ARP 欺骗）。它还会先提示抓包质量本身带来的限制（镜像口重复帧、只有单向流量、截断包）。带 Wireshark 风格的包列表、真实 display filter、CSV 导出、流图，以及可选的 AI 调查（用你自己的 Anthropic key，会引用支撑结论的包）。Apache 2.0，beta。

**为什么值得关注**：网络排障中“先看包”的人不少，但能把抓包结果直接翻译成“下一步查什么”的工具很少，而且它完全本地运行，抓包数据不出内网。

**评论里的经验补充**：**tuckerpo** 说 CableLabs 团队做过高度类似的东西（PNM + 反应式自修复），还给全球最大的宽带公司的 CEO/CTO 演示过，最后没能推广起来；**tonyarkles** 分享了一个更通用的思路：“I've had pretty great success using LLMs to write 'doctor' scripts... instead of repeatedly giving LLMs raw data files and having it find the same issues over and over, I've started driving the lessons learned into automated test scripts.” —— 把每次踩到的坑固化成脚本，而不是每次都让 LLM 重新读一遍原始数据。

---

### 10. Pandex：把欧洲法律做成一个 API + MCP server
🔗 https://www.pandex.io ｜11 分 / 1 评论

覆盖 EU、德国、法国、荷兰、英国、奥地利、瑞士、卢森堡和 ECHR 判例，280 万份官方文件，410 份机构刊物中 33 家完整，3700 万条引用链接回原文。能力包括：关键词/语义/混合检索（可以用英文查询找到法文判决里的那一段）、时间点版本（每一条法律的每个历史版本以及生效日期）、完整引用图谱、精确查找、只使用官方来源。既可以当 REST API 用，也可以当 MCP server 用（Claude、Cursor、Copilot、Windsurf、Zed、Gemini 都能接），每晚更新。

**为什么值得关注**：它解决的问题很具体——LLM 讲欧洲法时会引用旧版本或者干脆编造条文；这里给模型的是官方原文加历史版本，而且 MCP 接法一条命令就能装上，是“给 agent 提供可靠数据源”这一类产品里比较典型的形态。

**作者自述（vasie）**：“AI models often get European law wrong, quoting old versions or making up text. Pandex gives them the official text instead. ... Works as an MCP server, no key needed.”，并在评论里直接问 HN：下一个该加哪个国家。

---

**今日观察**：今天 HN 被两条“信任”主线占据——一条是“我们能不能相信一个 1700 万行的机器证明”（黎曼猜想帖 592 条评论），另一条是“我们能不能相信渲染管道和签名库”（Ghostscript、GPGME 两个 CVE 同时在榜）。与之形成对照的，是量化压缩和 Zero C# 这类“把重量级运行时从栈里拿掉”的项目：AI 降低了写底层代码的成本之后，本周冒头的方向明显偏向“用更少的东西做同样的事”。

已标记 17 篇为已读。
