
**橘鸦AI早报 · 2026-11-20 摘要**

今天这期信息密度很高：Anthropic 上市、DeepSeek 千亿融资、腾讯公开承认元宝没做起来，三条行业消息集中到一起；产品侧则是 Gemini 和 OpenAI 同时朝着 agent 的方向推进。

---

**1. Anthropic 上市首日收涨 17%，成为史上最大 IPO**
Anthropic 11 月 19 日在 Nasdaq 挂牌，代码 ANT。发行价 83 美元已经高于最初 70–78 美元的指导区间；一共发行 9.8 亿股，募资 813 亿美元，超过 SpaceX 的 750 亿美元，成为史上规模最大的 IPO。开盘 111.50 美元，比发行价高出 34%，收盘 97.17 美元。按收盘价计算，市值约 1.27–1.3 万亿美元；按完全稀释口径计算，接近 1.8 万亿美元。
意义：AI 公司第一次进入“万亿市值”这一量级，后面所有 AI 创业公司的融资和定价都会参考这个数值。
https://x.com/AnthropicAI/status/2123461658890686863

**2. DeepSeek 千亿融资得到确认，31 家机构入局**
工商变更显示，杭州深度求索的注册资本从 1644.75 万元增至 1991.87 万元，新增股东杭州程砚持股 17.27%。这个持股平台新增的 31 家合伙人包括腾讯、宁德时代、中国移动、中信证券投资、小红书等，出资额从 0.6 万元增加到约 34.39 亿元。梁文锋退出直接合伙人名单，但仍通过杭州程策担任执行事务合伙人。财新称第二轮外部融资已完成，DeepSeek 官方尚未回应。
意义：腾讯、宁德、中移动同时入股同一家模型公司，说明资金已经不只是财务投资，还带有算力和渠道的绑定。
https://companies.caixin.com/2026-11-19/102506636.html

**3. 腾讯刘炽平：元宝没达到预期，已大幅削减投入**
在三季度业绩会上，刘炽平直接说，AI 助手元宝“没有达到预期那样的成功”。现在的策略是不再把用户规模当作唯一目标，重心回到模型能力上，并补充了 AI 搜索功能，同时大幅削减了相关投入。财报里提到的 AI 产品线包括混元、元宝、CodeBuddy、WorkBuddy、小微。
意义：这是大厂高层少有的公开认输。国内 AI 助手的“先抢用户、再谈变现”这一套打法，在元宝这个项目上基本被判定为失败。
https://news.bjd.com.cn/2026/11/18/12035795.shtml

**4. OpenAI 公开 Performance Factory：用 Codex 自动修复 ChatGPT 性能回退**
整套流程是：性能告警触发后派出 agent 调查根因并提出修复方案，由工程师审核代码后合并，再由第二个 agent 验证性能是否恢复。三个多月里一共追踪了 1700 多次调查，定位了 600 多个案例的根因。最终上线的修复中，约 50 个受 agent 建议影响，约 15 个直接采用了 Codex 提交的代码。有意思的是官方的结论：让 agent 提出“可靠修复”仍然比定位原因要难。
意义：这是目前公开得最详细的“AI 参与自身基础设施维护”的生产案例，15 这个数字也比较诚实，没有夸大。
https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast

**5. Gemini API 预览 Tool Retrieval：工具定义可以按需加载**
agent 不必每次请求都把完整工具库塞进 prompt，只要加上 tool_search 工具并把工具标记为“暂缓加载”，模型就先只看到工具名和描述，需要时再拉取完整的参数结构。支持接入数百种工具，远程 MCP 服务器同样适用，只兼容 Interactions API 和 Gemini 3.6 及之后的模型，不单独收费。
意义：这是 agent 规模化的主要瓶颈之一。工具上百个之后，token 成本会直接失控，按需加载是必需的基础设施。
https://blog.google/innovation-and-ai/technology/developers-tools/gemini-api-tool-retrieval/

**6. Antigravity 桌面版支持 SSH 远程开发**
可以从侧边栏或命令面板连接远程的 64 位 Linux 机器，Antigravity 会通过 OpenSSH 自动在远端安装服务端。项目、Git worktree、agent 和终端全部在远程主机上运行，关掉本地窗口后进程也不会中断。要求 glibc 2.26+，macOS、Windows、Alpine 这类 musl 系统都不支持。另外还加了 GitHub PR 集成。
意义：coding agent 开始从“本地 IDE 插件”转成“远程常驻执行体”，对关掉笔记本就断掉的那套模式来说，是一种替代。
https://antigravity.google/docs/ssh

**7. Mac 版 Gemini 上线 computer use**
AI 在隔离的后台窗口里操作本地文件、桌面应用和网页，聊天界面会给出实时预览，主屏幕和光标不会被占用。用户可以随时暂停，也可以在关键操作执行前批准，还能指定允许访问哪些应用。目前只在美国英语地区向 Google AI Plus、Pro、Ultra 订阅用户开放。
意义：Google 把 desktop agent 直接内置进消费级 App 里，而不是做成一个开发者工具，铺开速度会比 OpenAI 的 Operator 路线更快。
https://blog.google/innovation-and-ai/products/gemini-app/computer-use-mac/

**8. Genie 4 上线 Gemini API 和 AI Studio，按秒计费**
可以用文字或图片生成可交互的世界，输出 720p、24fps 的画面，同时带 48kHz 立体声，支持 WASD、方向键和文字实时控制。通过 WebRTC 或 WebSocket 传输，约 0.10 美元/秒。有一点需要留意：**关掉浏览器页面并不会停止服务端生成，也不会停止计费**，必须显式结束会话。
意义：世界模型开始按“流媒体”的方式定价，但要小心忘记结束会话带来的成本。
https://blog.google/innovation-and-ai/technology/developers-tools/genie-4-in-gemini-api/

**9. 火山引擎上线豆包 SeedRealtime 1.0，端到端音视频通话**
把声音、画面、时序、表达统一进一个端到端模型，支持一边看、一边听、一边说，并且能在理解场景之后主动开口。官方给出的对比是：相比 ASR、VLM、TTS 级联的旧方案，音视频对话的节奏问题减少了一半。可用于语音助手、智能硬件、陪伴应用、实时客服。
意义：级联方案的延迟叠加是实时音视频助手的长期痛点，端到端是必然方向，国内已经率先走向商用。
https://mp.weixin.qq.com/s/fyNH7Y6o32kxc4GeK8Qb3A

**10. Ideogram 4.6：原生 4K + 精准编辑**
在 Rapidata 多步图像编辑基准上拿到 1892 分（上一代 4.5 是 1866），精确改色从 46% 提升到 83%，编辑区域之外的像素漂移明显减少。已经上线 App、API 以及 Leonardo、Runway、fal，API 价格每张 0.008 美元起。
意义：图像编辑真正的问题，不是画不画得好，而是改一处、坏一片；漂移这个指标终于被当成核心 KPI 来做了。
https://ideogram.ai/models/4.6

---

**几条边角但值得记的**：阿里吴泳铭说千问已在平头哥芯片上训练下一代模型，并判断 2027–2028 是中国算力最紧的两年；OpenCode 称自有 GPU 已承接当天 44% 的 token（16 万亿），手里有 1000 块 GB300/B300，而且全部是短租；Cloudflare 开源了 Clairic（27B）/Clairic-flash（9B）两个信息抽取模型权重，12 月 1 日前 Workers AI 上 0.10 美元/百万 token。

已标记 2026-11-20 期已读。
