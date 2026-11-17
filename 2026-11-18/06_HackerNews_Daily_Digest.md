
# HackerNews 日报 · 2026-11-18

昨日 HN 共有 20 条新帖，现按热度抓取前 10 条。OpenAI 在这一天同时发布新模型，抢走了当天的大部分注意力；除模型发布外，安全领域还有两个值得注意的信号：一个是 Java 运行时出现可远程执行代码的漏洞（RCE），另一个是 Phrack 把 AI 写进了目录。

---

## 1. GPT‑6.2 Astra 与 Sol 发布（1003 分 / 619 条评论）

**摘要**：OpenAI 同时推出两端定位：Astra 是面向“最难项目”的前沿模型，Sol 是日常主力，两者的共同卖点是**更少的输出 token 换来更强的结果**。Astra 在 Agents' Last Exam 上比 GPT‑6 Astra 高 5.2 分，而成本还不足后者的三分之一，对外还宣称比 Claude Fable 5.2 高 5.5 分、成本只有其 5%。API 价格：输入 $8、缓存输入 $0.40、输出 $40（每百万 token），比上一代 Astra 便宜 20%。Sol 在 Cognition 的 FrontierCode 2.0 上只比 Astra 低 0.5 分，成本约为其五分之一。

**HN 讨论**（评价两极）：
- 有人从定价角度发问：`charlesabarnes`：“我欣赏 OAI 现在把话题引向‘完成任务的花费’，而不是蛮力堆算力。”
- 实测派则强调两者的分工：`itvision`：“我手上是一个 1.5MB 的 C++ 代码库，Sol 完成的任务里至少三分之一要 Astra 返工，Astra 一次就给出可用结果。”
- 与之相反，`billypilgrim`：“我还没找到 Astra 明显强于 Sol 的应用场景，有人能说说自己具体在做什么吗？”
- 信任问题：`alastairr`：“Sol 6.1 在真实 SWE 工作里远没有 benchmark 上那么惊艳，我怀疑模型内部有一套‘跑分模式’，只在题目长得像跑分时才启动。”
- 另外，发布当天官网被吐槽很卡：`geauxvirtual`：“这网站把我 GPU 顶到 100%，他们是在挖矿吗？”并且 `christianqchung` 指出配套的 system card 当时还没上线。

**为什么值得看**：AI 竞争的评价标准正从“绝对智能”转向“每任务成本”，这直接影响你怎么选模型、怎么估算账单。顺便说一句，评论区里真实的降本经验（用 Sol 干粗活、用 Astra 收拾残局）比官方 benchmark 有用。

🔗 https://openai.com/index/introducing-gpt-6-2-astra-sol/

---

## 2. Java4Shell：OpenJDK 处理 Base64 时的 RCE（320 分）

**摘要**：CVE‑2026‑114938，CVSS 4.0 评分 9.2。OpenJDK 为了加速 Base64 解码，用 AVX‑512 VBMI 手写汇编，这段汇编处理结尾几个字符时存在 bug：输入 64 个 `A` 加一个 `=`，会让函数计算出负的输出长度，进而被当成 64 字节写入，最多越界 62 字节，覆盖相邻的堆对象。后果是既能读内存，类似 Heartbleed，也能远程执行代码。已复现的**免认证 RCE** 目标包括 Keycloak、Jira、Confluence、Artifactory、Jenkins、PingFederate，登录后利用的包括 Kafka、Solr、Elasticsearch、Gerrit、Spinnaker。发现过程由 AI 辅助完成：1 小时定位漏洞，再加 2 小时写出利用，token 花费不到 200 美元。

**HN 讨论**：
- 缓解措施已经公开：`mzs`：“启动参数加 `-XX:-UseBASE64Intrinsics`，或 `-XX:UseAVX=2` 关掉 AVX‑512，只对 x86‑64 有效，ARM 上加了会启动失败。”
- `ievans`（Semgrep）发布了免费检测脚本，列出 5 个命中条件，并指出只有 HotSpot 生成这段 stub，OpenJ9、GCJ 不受影响。
- `Sigmazero60`：“我们去年因为散热问题在所有 JDK 机器上设了 UseAVX=2，结果这次正好躲过。”
- 深层反思：作者称之为“公共资源的悲剧”，即 Base64 优化只有少数应用需要，代码却随 JDK 发给所有人。他们因此提出了“vibe‑uncoding”（用 AI 找出并删除死代码来缩小攻击面）。

**为什么值得看**：凡是采用 JVM 的团队都需要处置。它也是“用 AI 找漏洞、用 AI 删代码”这条新安全产业路线的标志性案例。

🔗 https://calif.io/java4shell/

---

## 3. 微软发布 MAI Code 2 和 Code 2 Flash（246 分）

**摘要**：定位很明确：不做最强的通用模型，只做**性价比最好的企业日常编码模型**，主打多文件改动、跨仓库理解、深度调试和 UI，声称产出的改动是维护者愿意合并的。四个 benchmark 平均下来，MAI Code 2 达到 GPT‑6.1 Sol 的 98% 性能、40% 的价格；达到 Claude Opus 5.5 的 96% 性能、**5% 的价格**。在盲测前端任务中，64% 的评审更喜欢它的结果。官方也承认它尚未针对基础科研和超长程 agent 任务调优。它还衍生出 MAI Work Flash，支撑 M365 的 Excel、PPT、Word。

**HN 讨论**：
- `kennywinker`：“声称只有 20% 的成本，说明模型只有 20% 的大小。这正面挑战了‘代码强必须全能强’的正统观念，明年这套正统可能要倒。”
- `pseudosavant`：“我不想当 OpenAI 或 Anthropic，他们只领先几个月，这是很脆弱的优势，得一直在仓鼠轮上狂奔。”
- 怀疑派：`zf00002` 认为“怀疑，但喜欢他们敢把 benchmark 和最强的模型并排摆出来”；`dude250711` 担心“这会让普通企业停止为真正好用的模型付钱，转而选便宜的”。
- 对品牌问题也有吐槽：`gltwelv`：“微软在一个 Claude vibe‑coded 的网站上发布 MAI Code，这算公开嘲讽我们了。”

**为什么值得看**：如果企业级编码市场真被“够用 + 便宜”的模型打开，订阅价格和 agent 工作流的成本结构都会重新计算。对成本敏感的使用者，这条值得持续跟踪。

🔗 https://microsoft.ai/news/introducing-mai-code-2-and-mai-code-2-flash/

---

## 4. Solid 2.0 正式发布（183 分）

**摘要**：距 1.0 已有五年。核心变化是**把 async 引入 signal 图**：memo 中可以直接返回 Promise 或 async iterator，下游自动理解 pending 与 stale 状态，不需要再让 async 状态散落在各处。同时提供 server RPC、live、broadcast 这类前后端衔接原语，把 Remix 曾试图解决的“中间层”用更自然的方式做出来。官方还提出了“Built to be written by agents”的口号，强调更好的诊断信息、更少的隐式状态。

**HN 讨论**：
- `AlexErrant`：“async graph 很酷，它用已有的 signal 图消解了 async 的‘染色函数’问题；对照 React，hooks 本身才是染色函数。”
- 对“为 agent 而设计”这一点，社区意见分裂：`ale`：“这其实意味着干脆别用框架了，框架本来就是给多人团队补知识鸿沟的，现在这活儿归 agent。”作者 `ryansolid` 亲自回答说正在做 ReactiveScript，把约束下沉到编译器，“agent 写不出坏代码，因为编译不过”。
- `wk_end`：“有趣的是，那些‘为 agent 优化’的东西对手写一样友好，人类的 best practice 就是 agent 的 best practice。”

**为什么值得看**：前端框架正在以“模型好不好写”为第一性重新设计；如果你还在手写前端，这是观察下一代框架形态的窗口。

🔗 https://www.solidjs.com/blog/solid-2-0-the-long-hold/

---

## 5. Phrack 第 73 期发布（227 分）

**摘要**：老牌安全电子杂志出刊，距上期一年多。目录里最值得注意的是 **“Reflections on Trusting AI: A Virus Inside an LLM”**，此外还有从 vDSO 逃逸 Docker 容器、TCC 绕过的密码学思路、Windows 的 “Word Machines”、QNX 用户态 shellcode、Sheaves 时代的 UAF（释放后使用）利用、以及 PhrackCTF 衍生出的两个 WinFsp 0‑day。另有 “Phrack World History” 栏目，记录社区口述史。

**HN 讨论**：以怀旧情绪为主。
- `ChrisArchitect`：“薪火还在传，尤其是那些 World History 栏目，把被遗忘的故事留下来很重要。”
- `myth_drannon`：“什么都比不过 1996 年的第 49 期，*Smashing The Stack For Fun And Profit*。”
- `neuromancer` 类评论怀念 300 波特调制解调器合成音和 ASCII art。

**为什么值得看**：想看第一手的攻击技术原帖，而不只是二手转述，这里是源头；LLM 作为攻击载体那篇尤其值得读。

🔗 https://phrack.org/issues/73/introduction_md

---

## 6. jQuery 4.1.0 与 3.8.0 同时发布（213 分）

**摘要**：4.x 首个 minor 版本，同时发布 3.8.0。官方明说 3.8.0 是“送别版，不是复兴”：把 3.x 分支积压多年的修复一次放出，此后只收关键安全与 bug 修复，鼓励所有人升级到 4.x。两者共有改动包括：selector 标识符匹配修复 ReDoS（一长串 hex 转义加非法字符就能挂死页面）；AJAX transport 回调改成单对象参数；4.1.0 新增 `jqXHR.responseURL`；核心用 `querySelectorAll` 替换 `getElementsByTagName` 等老接口。仓库还新增了**机器生成贡献的规范**和商业支持厂商 TuxCare。

**HN 讨论**：
- `gosen`：“有点惊讶（是好的那种）它还在维护，而且还在支撑半个互联网。”
- `maxpert`：“在 AI 和 React 的时代，大家已经体会不到当年在 IE6 上用 jQuery 有多爽。”
- `frabjoused` 开玩笑：“既然维护这么容易，不如把 MooTools 也复活？”

**为什么值得看**：一个 20 年老库仍在给“半个互联网”打安全补丁。这次修掉的 ReDoS 值得排查自己项目里是否有可被外部触发的老 selector。

🔗 https://github.com/jquery/jquery/releases/tag/4.1.0

---

## 7. Quad9 退出法国：煤矿里的金丝雀（118 分）

**摘要**：瑞士非营利基金会 Quad9 上个月宣布撤回其在法国的免费公共 DNS 解析器。起因是法国法院认定它未按要求屏蔽涉嫌侵权的域名，并对它施加每日罚款，而 Quad9 只能在“承受巨额罚金”和“破坏用户隐私与安全、污染解析结果”之间二选一，最终选择退出。Cloudflare 撰文指出这不是孤立事件（此前 Cisco 也退过），并警告：一旦在 DNS 这层做强制屏蔽，用户会“毫无解释地断网”，而受影响方包括法国政府部门、学校、医院和公共事业机构。

**HN 讨论**：
- `slopinthebag`：“我们大概在目睹自由全球互联网终结的开始，正在走向按国划分的‘网中之网’。”
- `robinpie`：“对互联网的过度监管既可怕又短视。”
- 也有人把矛头指向版权与 AI 公司的利益交换（`lifestyleguru`）；另有一条评论则把问题直接归因于“欧洲只会产出更多管制”（`tsss`）。

**为什么值得看**：内容屏蔽与版权执法正从应用层下探到 DNS、TLS 这类基础设施层。这类退出会以“某个网站突然打不开”的形式，落在普通人和小团队头上。

🔗 https://blog.cloudflare.com/quad9-withdrawal-from-france/

---

## 8. Web Browser Engineering 教材（770 分 / 2021）

**摘要**：Pavel Panchekha 与 Chris Harrelson 写的书，用两千多行 Python 从零实现一个“基本但完整”的浏览器：网络、URL/HTTP、字符排版、HTML 解析、布局、CSS 应用、表单、JS 与 DOM、Cookie 与 XSS/CSRF、合成与动画、无障碍、内嵌内容。牛津大学出版社出版，在线版免费，已出韩文、日文译本。

**HN 讨论**：几乎全是推荐。
- `CrayKhoi`：“我一直在补浏览器内部原理，这本书特别有用，它能在不读几百万行 Chrome 代码的前提下建立直觉。”
- `bberrry`：“感谢作者，你们是我们中最好的。”
- `andai` 补充了作者解释为何选 Python 的博文，以及把 Python 编译成 JS 让示例能在书页里直接跑的做法。

**为什么值得看**：agent 时代“能不能从零造东西”的理解力反而更值钱。这是最省时间的浏览器原理路径，适合周末动手。

🔗 https://browser.engineering/

---

## 9. Not Everything Needs an LLM（65 分，PostHog 工程博客）

**摘要**：PostHog 的 Jina Yoon 写他们用“decision model”（如 Jev）处理简单任务：问结构化的窄问题，返回带概率的类型化答案（0.99 表示“是”的概率为 99%），而不是几百字的“it depends”。在已校准的模型里，0.8 的答案约有八成是对的，不确定性是显式的。核心用法是**用便宜模型给昂贵的 LLM 调用设置前置判断**：例如在 Replay Vision 里用两个判断题来筛出 PII，命中 0.4 以上才叫 Gemini 重写。文中称这类模型比前沿 LLM 便宜最多 444 倍、快 193 倍。

**HN 讨论**：
- `jakeydus` 质疑：“‘别什么都用 LLM，用 decision model’——那 decision model 到底是什么？一个被限制回答的 LLM？嗯。”
- `aabdi` 唱反调：“我反而认为，除非你会做 eval，否则就该用最贵的模型。我见过太多人自己写的 eval 完全不对应真实世界，然后产品直接坏在 p90 用户上。”
- `dzink` 一句立场：“PostHog 就是不该拿用户数据做这个。”

**为什么值得看**：这是“成本和复杂度分层”的工程实践样本：不是所有判断都值得用大模型，也不是所有省法都安全。评论区对 eval 的争论，比正文更值得看。

🔗 https://newsletter.posthog.com/p/decision-models

---

## 10. Apple 服务大面积宕机（592 分，简报）

**摘要**：Apple 系统状态页一度显示多项服务 partial outage，波及账户登录、商店订单与设备激活。HN 上先有大量“这是真的吗”的怀疑，随后被现场经历确认。

**HN 讨论**：
- `cjbconnor`：“刚从 Apple Store 回来，他们确认全线挂了，没法下单也没法退货，新 iPhone 都激活不了。”
- `adamsiem`：“是真的，日历登录失败，然后任何设备都登不上 account.apple.com。”
- `frenchie4111` 提供了有用的推理：“Apple 几乎全跑在自家硬件上，本来没理由和其他云厂商的故障相关联。”

**为什么值得看**：纯运维事件，价值不高，但对“自建基础设施能否避免连带故障”是一次现场样本。

🔗 https://developer.apple.com/system-status/

---

**本期观察**：三条主线交叉——模型价格战把“每任务成本”变成新指标（1、3），AI 同时成为漏洞的发现者和修复工具（2、5），以及框架开始按“被 agent 读写”重新设计（4、8）。10 条已全部标记为已读，下期继续。
