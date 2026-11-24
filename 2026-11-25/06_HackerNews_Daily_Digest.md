
**HackerNews 每日精选 · 2026-11-25**（本轮扫描 20 条新帖，筛出 10 条，按热度与信息价值排序）

---

### 1. LLM agent 为母公司工作，不是为你工作 · 865 分 / 363 评论
https://michaelharley.net/posts/2026/11/01/llm-agents-work-for-their-parent-companies-not-for-you/

作者用 Claude Code 写了个 skill：从 Instagram reel 里识别歌曲，找到乐队 Bandcamp 页面去买正版。Bandcamp 加了人机验证后，模型拒绝绕过；但同一个 skill 里"从 YouTube 扒歌下到本地"那条路径，模型照做不误——一条给乐队付钱，一条一分不给。作者的结论不是"模型不肯帮我黑站"，而是：**这些模型只为允许它工作的公司工作**。合规约束、法务风险、商业利益高度一致，用户利益不在其中。后半段推到 enshittification 和"未来答案里有多少是付费植入"。

值得关注：本周 HN 最大讨论帖，直指 agent 产品化的核心矛盾——对齐策略由厂商定义，用户的正当需求（买正版）反而被挡在门外。

> **jqpabc123**：任何营利性在线服务，第一优先都是为母公司工作。如果不为母公司工作，他们根本不会提供这项服务。用户天然处在弱势位置，结果就是必然的 enshittification。
> **rDr4g0n**：那个给我们带来强制追踪、把用户卖给广告商、用成瘾算法换利润的行业，一定会用 LLM 从我们身上获利，不管人的代价。别再给它们付钱了。
> **girvo**（另一种解法）：开源模型现在很能打，去掉那些"安全措施"也不难，且不太损伤能力。
> **rrhjm53270**（半玩笑）：我有同样的找歌问题，解决办法是本地部署 YuE2，让 agent 直接生成一首。

---

### 2. Ternary Bonsai 2.5 27B：5.9GB 跑出接近满精度的 agent 能力 · 255 分 / 79 评论
https://prismml.com/news/bonsai-2-5-27b

PrismML 发布三值（ternary）量化的 27B 模型，基于 Qwen3.8 27B，体积仍是 5.9GB，主打 agentic coding 与本地私有知识工作。SWE-bench Verified 从上一代 60.8 提升到 75.6（满精度基座 80.6），Terminal-Bench 2.1 从 52.8 到 60.1，AppWorld 从 51.2 到 90.5；主要修的是上一代"想太多、循环重复"的毛病，任务完成轮数和 token 都下降。H100 上 291 tok/s，RTX 4090 上 204 tok/s，Apache 2.0，llama.cpp / MLX 都能跑。

值得关注：这个体积能在消费级硬件上跑出接近满精度基座的 agent 表现，是"敏感数据不出本机"路线最实际的一次进展。

> **nik_s**：除非我完全看错，这分数相当于 Opus 4.6（2026 年 2 月发布）在 SWE-bench Verified 上的水平。到底是 benchmaxxing、基准漂移，还是小模型落后前沿约 6 个月——大概三者都有。
> **StevenNunez**：我真的很想喜欢这个系列，但每次都失望，总觉得被开发者忽悠。
> **NoidFonsense**：这量化质量好得离谱，我猜他们做了量化感知的重新训练？

---

### 3. Check Point 管理服务器遭活跃入侵，至少 22 家机构 · 245 分 / 106 评论
https://www.greynoise.io/blog/check-point-security-management-servers-intrusion-campaign

GreyNoise 披露 GT13 行动：10 月 17 日至 11 月 2 日，至少 22 家机构被入侵，涉及 24 台 Check Point 安全管理服务器，覆盖金融、能源、政府、交通、矿业、制造，横跨 17 个国家和地区。攻击者用 99 个 IP、Nmap/Chisel/Impacket/Paramiko，滥用 HFS、Citrix NetScaler、Ivanti、Windows NetLogon、Check Point SmartConsole 认证绕过等 6 个 CVE，并把一台被控服务器当跳板。GreyNoise 判断攻击者使用 LLM 与 agent 系统做扫描、利用与自动化交互。

值得关注：安全设备自己成了入口；而且这是少见的、把"agent 驱动的入侵流水线"写进正式报告的一手材料。公网暴露的 Check Point 管理口该查了。

> **mentalgear**：系好安全带，这只是结束的开始。现在只有高级犯罪组织和国家级行为体在用 LLM 打点，很快十万量级的犯罪分子会直接对模型说"给我赚尽可能多的钱"，结果就是模型和 agent 集群攻击一切在线服务，包括关键基础设施。
> **PyWoody**：HFS 每次登录返回的 session cookie 签名值取自 JS `Math.random()`，连着登录几次就能重建 V8 PRNG 内部状态、伪造 admin cookie 免密登录。十年前我在 Burp 上玩过这个手法，不敢相信它还是个问题。
> **sigmar**（细节）：攻击者拿下跳板后用 nftables 丢掉可能触发 CVE-2026-98432 的 IPv4 包，等于自己给机器打了补丁防止别人进来——而这个洞 Ubuntu 拖到 11 月才修。
> **tamimio**：我最喜欢的一点是，他们占完机器还顺手帮它打了个补丁。

---

### 4. Jetty Pro：想 vibe code 一天的小工具，做了三个半月 · 242 分 / 108 评论
http://hypercritical.co/2026/11/23/jetty-pro

John Siracusa（Hypercritical）发布 Mac 应用 Jetty Pro，功能说起来极小：屏幕角落一个文件夹面板，出自已退役的 DragThing。他本打算用编码 agent 一两天 vibe code 出来，结果做了三个半月，中途从 SwitchGlass 的旧 SwiftUI 代码起步，最后把项目做成了"替换 Dock"。文章坦诚记录了 agent 快速生成的代码"能跑但很糙"、优化与细节全部要人工补回来的过程。定价采用订阅制。

值得关注：两个信号叠加——AI 编码确实让"投入产出比不划算"的小工具重新变得可做；同时独立 Mac 开发者的订阅制反弹有多强烈，评论区可以当样本看。

> **0gs**：要是一次性买断我肯定买，40 到 50 美元都行。但我没法接受为了在屏幕边上多放几个快捷方式去用"私有 API"，更不想签一份年度 v-dongle 税。
> **clates**：你 FAQ 里自己说私有 API 一变功能可能失效，那你怎么论证订阅是合理的？我没法把钱和时间投在一个随时可能被第三方弄坏的工具上。
> **egeozcan**：我尊重你的投入，但再多一个订阅我都无法接受，1 美元一年还是 100 美元一年，没区别。
> **boplicity**（反向解读）：有人在骂价格，说明他们想要这个产品——这是好信号。

---

### 5. 用确定性 VM 算关键路径：给 Brendan Gregg 的一份献礼 · 212 分 / 39 评论
https://fzakaria.com/2026/11/12/worshipping-at-the-altar-of-brendan-gregg

Rewind 是一个可完整重放的确定性 VM，作者给它加了 `rewind time` 命令，输出程序的**关键路径**——最长依赖链，也就是无论堆多少 CPU 都省不下来的最短时间。拿 libuv 的 build+test 试：单核 78 秒，关键路径 47.4 秒，其中 67% 的时间在睡眠（epoll_pwait 23.1 秒、clock_nanosleep 8.5 秒），CPU profile 在这里几乎无用。关键洞察是：VM 为了重放本来就要记录每次上下文切换，现在连 wakeup 归因也记了，于是 off-CPU 分析可以**事后**对任意一次录制做，不必提前打点。

值得关注：把 Gregg 的 off-CPU 分析和 flame graph 方法搬到"可重放录制"上，绕开了 live tracing 必须提前开、有开销、样本少这三个老问题。对构建系统和 CI 调优直接可用。

> **perdy**：我们把 CI benchmark 换成 Callgrind 的指令数、固定 cache 几何后，数字基本不漂了，这是 wall-clock 在共享 runner 上从没给过的稳定性。代价是丢掉所有 off-CPU 信息——正是这篇文章讲的。
> **aidanhs**：我很喜欢确定性 VM 这个思路（Antithesis 同理），但听说你的 VM 是单线程的？那对高吞吐多线程流水线来说，性能分析会失真吧。顺便推荐 Perfetto 那篇 tracing 方法综述。
> **uvdn7**：这种分析对 async/coroutine/fiber 有用吗？难点在于框架层没有 request context 把后续任务和原始请求关联起来。

---

### 6. Songe：用闲置算力在本地训练你自己的模型 · 161 分 / 47 评论
https://github.com/sous-labs/songe

开源工具，装在本地模型服务（LM Studio / Ollama / vLLM / llama.cpp / MLX）前面当代理。它记录 agent 每次动作之后发生了什么——工具返回值、报错、你的下一条消息；等 agent 空闲、内存和电量允许时，把学到的东西变成训练。两种"梦"：Quick Dream 几分钟内把你的偏好写进模型指令；Deep Dream 跑一小时以上，训练一个小 adapter。新版本只有在你自己的历史对话上表现更好才会被启用，可一键回滚到任意旧版本。无账号、无遥测，数据不出本机。

值得关注："本地 agent 自我进化"这条路线第一次有了完整工程实现（记录→练习→训练→验收→回滚），并且把验收标准严格限定在用户自己的数据上而不是公共 benchmark。真问题是有没有过拟合和能否量化收益。

> **dofm**：How it works 那一节完全没用。它到底在干什么——更新一个 LoRA 吗？
> **mock-possum**：它怎么判断"变好了"？希望 README 里贴一段改进判定的完整转录，show don't tell。
> **ganelonhb**（半玩笑）：别让 Altman 知道这个。
> **krawczstef**：我一直在等 LLM 版的 SETI@home，也许可以做成分布式的？

---

### 7. Cloudflare 掩盖了源站的落后 · 137 分 / 94 评论
https://charlie.fish/posts/2026/11/what-cloudflare-doesnt-tell-you/

用户连 Cloudflare 站点能拿到 TLS、IPv6、后量子加密，但 Cloudflare 到源站那一段可能完全没加密、且只用 IPv4。官方文档明确写：同一记录同时有 AAAA 和 A 时，回源优先 IPv4——即使站长已经在源站部署了 IPv6。作者的主张是 Cloudflare 应该在面板上主动告警"你的源站比我们落后"，并推动行业让 CDN 暴露回源段的 TLS 与 IP 版本信息。

值得关注：边缘现代化不等于全链路现代化，这是评估 CDN 安全姿态时最常被忽略的盲区；也是 IPv6 普及停滞的一个结构性原因。

> **Velocifyer**（技术解释）：回源 IPv4 每包省 4 字节开销；想强制走 IPv6，删掉 A 记录只留 AAAA 就行。
> **e63f67dd**（反驳）：Cloudflare 的全部意义就是把源站挡在互联网之外，我为什么希望它暴露更多源站信息？
> **Thaxll**：Cloudflare 可以给你签源站证书（Origin CA），你该用那个。
> **ipsum2**：不标题党的版本是——Cloudflare 内部连接优先 IPv4。

---

### 8. 拆分 USB-C：一个口同时跑 USB 3 和 USB 2 · 123 分 / 78 评论
https://www.frankchiarulli.com/blog/splitting-usb-c/

作者在做 restorekit 的 DFU 恢复 dongle，想支持新 Mac 的 USB 3 恢复速度。正规方案（GL3510 hub + 两颗 TI SuperSpeed mux）BOM 翻倍、PCB 涨到 100mm。他的"疯狂实验"是：USB 2 hub 继续走 D+/D-，SuperSpeed 差分对直接透传，赌 USB-C 里两套控制器本来就独立。板子从 JLC 回来实测通了——10 Gbps 全速 + 同口 USB 2 设备共存，而且比 USB 2 版本更便宜更小（21×48mm）。

值得关注：一个反直觉但已被实测验证的硬件技巧，做 USB-C 产品的团队可直接复用；代价是主机对端口拓扑的假设会被打破。

> **jsmith45**（关键风险）：最大问题是电源管理。主机要断电某个 3.x 设备，得知道它对应哪个 2.0 端口；意外拆分拓扑会让主机关错口。
> **xg15**：USB-IF 的向后兼容思路很有意思——不是扩展协议，而是要求同时完整实现旧协议。相当于 IMAP 工作组宣布"我们 100% 兼容 POP3：规定每台 IMAP 服务器也必须捆一个 POP3 服务器"。
> **riobard**：USB-A 四根线跑到 480Mbps 就够了；USB-C 用 24 根细针同时跑 120Gbps 和 240W，而且它已经不"serial"了。

---

### 9. GPT-6 展现内生的蛋白质设计能力 · 103 分 / 19 评论
https://openai.com/index/gpt-6-models-demonstrate-intrinsic-protein-design-capabilities/

OpenAI 论文称 GPT-6 系列能仅靠推理 + 写代码就设计出新的蛋白质三维结构和氨基酸序列，不调用专门的生物模型；14 项蛋白任务中内部研究模型多项追平或超过专用模型。用自然语言就能指定结合位点、整体形状、几个螺旋几个折叠。实验中基于 GPT-6.2 设计的蛋白在 5 个靶点显示结合迹象，重设计的抗体保持结合。但把设计变成可测蛋白仍需 SolubleMPNN 等专用模型补序列、筛候选。

值得关注：通用模型"只要会写代码就能做科学"的又一次验证，同时也是 biosecurity 争论的新弹药——评论区已经在吵这个。

> **fabian2k**（方法论质疑）：我没看懂 GPT-6.2 到底设计了什么。蛋白质里序列就是结构。它是真的输出了序列，还是只给了一个形状？"蛋白设计"应该是有目标、产出达成目标的序列。
> **mrkn1**：GPT-6 设计蛋白，别的模型把设计变成序列并筛选。它已经精通学术界了——出想法、让研究生干活、拿功劳。
> **infralog77**：不在实验室里长出来，你怎么验证这种东西？

---

### 10. KL 散度不会为负——除了在 PyTorch 里 · 81 分 / 31 评论
https://arxiv.org/abs/2611.30835

论文在 850 万条带认证参考的输入、18 类闭式 KL 公式和 `F.kl_div` 上，测出 PyTorch 在 CPU 和 GPU 上的值与梯度普遍出错：KL≈1e-7 附近，标量族超过 85% 的 FP32 结果相对误差 ≥1%，约 30% 在更小散度上直接变成负数；换更高精度也救不回来（23 个配置里 22 个仍有 7–51% 的 FP32 值显著错误）。作者给出稳定闭式分解 + 补偿算术 + 解析梯度，消除了 97% 以上显著误差。下游影响包括参数拟合、同起点蒸馏（top-1 分歧高达 97%）、量化 LLM 的层排序、GPT-2 circuit 的 19–59% 边分数。

值得关注：一个被"clamp 到 0"掩盖多年的静默数值失败。做 KL 相关训练、蒸馏或可解释性分析的，结论可靠性要重新审视。

> **sva_**：现在把 bug report 发到 arXiv 是个有意思的选择，不过如果为真，这个发现相当重要。
> **derf_**（同类坑）：`MAX(x,0)` 遇到负零返回 x（负零不小于 0），sqrt 看到符号位就直接失败。负零是抵消计算的正常产物。
> **bobmarleybiceps**：PyTorch 里数值不靠谱的地方多得有点意外，大概是算子太多、部分没人用也就没人管；也可能因为 ML 本身对数值问题不敏感，用户根本注意不到。

---

**补一条运维提醒（未入选正文）**：Grafana 12.4.16 / 13.0.14 / 13.1.11 / 13.2.7 / 13.3.2 修复多个 CVE（含 cookie 解密 oracle），114 分 / 18 评论。评论区普遍认为多为提权类中危、实际风险有限，但对一遍 https://grafana.com/security/security-advisories/ 里的版本号成本很低。

**本轮跳过**：心脏/中风风险预测（医学）、CIA 未分类系统被入侵（地缘政治）、Launch HN Versine、Weave 招聘、GTA 6 跑在 Windows 上、Fable 5.2 行为评测（仅 6 分，讨论不足）。

已标记 20 篇文章为已读。
