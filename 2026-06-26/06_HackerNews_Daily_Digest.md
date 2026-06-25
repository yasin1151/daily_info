
📡 **HackerNews 每日简报**｜2026-06-25（周四）

---

**1. IBM 发布全球首款亚纳米芯片技术**
IBM 宣布 0.7nm（7 埃米）制程突破，采用革命性三维"nanostack"架构，单芯片集成近 1000 亿晶体管（是 2nm 芯片的近两倍）。相比 2nm 节点，性能提升 50% 或能效提升 70%。这是半导体行业在逼近原子尺度极限后又一次实质性跨越。
🔗 https://newsroom.ibm.com/2026-06-25-ibm-debuts-worlds-first-sub-1-nanometer-chip-technology

---

**2. 从 Proxmox 迁移到 NixOS + Incus：一篇关于声明式基础设施的深度实践**
作者用亲身经历展示了从 GUI 驱动的 Proxmox 迁移到全声明式 NixOS + Incus 的过程。亮点在于：他论证了当 AI Agent 介入运维时，声明式配置从"可选优雅"变为"必修课"——一个在 YOLO 模式下运行几百条命令的 Agent 可以把系统推到不可复现的混乱状态。文中附有 vzdump→Incus 的完整迁移脚本。
🔗 https://www.nijho.lt/post/proxmox-to-nixos/

---

**3. Zig 编译器重大更新：全新 @bitCast 语义 + LLVM 后端优化**
Zig 核心贡献者 Matthew Lugg 实现了 LLVM 后端对任意位宽整型（u4/i13/u40）的内存表示优化——不再直接用 LLVM bit-int 类型（这些路径因 Clang 从不 emit 而测试不足、bug 频出），改为 SSA 内用 bit-int、落内存时零扩展至 ABI 对齐类型。修复了长期存在的 miscompilation 问题，并重新定义了 @bitCast 的语义。
🔗 https://ziglang.org/devlog/2026/#2026-06-25

---

**4. Un-0：用耦合振荡器生成图像——物理计算的全新范式**
Unconventional AI 发布了一个完全由耦合振荡器物理系统驱动的图像生成器，在 ImageNet 64×64 上达到 FID 6.74，追赶早期传统扩散模型水平。其核心理念是：未来 AI 计算需要 1000x 能效提升，必须抛弃 GPU，直接用物理定律做计算。所有权重和代码开源。
🔗 https://unconv.ai/blog/introducing-un-0-generating-images-with-coupled-oscillators/

---

**5. OpenKnowledge：开源的 AI-first 笔记/知识库替代品（Show HN）**
一个本地优先的 Markdown 编辑器 + LLM Wiki，对标 Obsidian/Notion 但主打 AI 集成：内置 MCP 协议、agentic search、skill 系统，原生支持 Claude/Cursor/Codex 协作编辑。底层由 git/GitHub 驱动，支持团队同步。GPL-3.0 开源。
🔗 https://github.com/inkeep/open-knowledge

---

**6. AI 模型的政见地图——谁左谁右？**
Trakkr.ai 发布了一份系统性测量报告：对 6 个主流模型（ChatGPT、Claude、Gemini、Grok、Llama、DeepSeek）在政治、经济、言论、社会议题上的立场做盲测（关闭搜索引擎）。结果显示：6 个模型中 4 个偏左。Grok 最右，Gemini 最中立且最稳定。所有原始数据开源可查。
🔗 https://trakkr.ai/bias

---

**7. Hacker News Trends：18 年评论索引的趋势工具（Show HN）**
基于 Upstash Redis Search 构建，支持查询任意主题/工具/人物在 HN 18 年间的讨论热度走势，可叠加对比（如 Vercel vs Cloudflare、Scala vs Swift vs Kotlin、AMD vs Nvidia）。每个数据点都链接到原始讨论，附带 Who is Hiring 专版趋势图表。
🔗 https://hackernewstrends.com

---

**8. OpenAI 倾向于推迟到明年再 IPO**
据 NYT 报道，OpenAI 考虑将上市计划推迟至 2027 年，原因是需要更多时间稳定业务模型、应对监管审查并在组织架构从非营利转型方面做足准备。
🔗 https://www.nytimes.com/2026/06/25/technology/openai-ipo-artificial-intelligence.html

---

**9. An Oral History of Bank Python——投资银行的 Python 暗面**
一篇 2021 年的经典重读：大型投行的 Python 其实是整个生态的私有 fork，核心是一个名叫 Barbara 的全局 Python 对象 KV 存储（基于 pickle+zip），没有文件系统、金融建模用 float 而非高精度数、Excel 内嵌交易执行。读完让你理解为什么说"金融是一个异国"。
🔗 https://calpaterson.com/bank-python.html

---

**10. "请出示证件"时代的互联网正在摧毁你的隐私**
作者以澳大利亚 2025 年实施的 16 岁以下社交媒体禁令为引，论述全球范围内的年龄验证（Age Verification）实为身份验证——你将被迫上传护照/人脸来参与公共讨论。核心警示：当批评政要、讨论成瘾经历或敏感健康问题时，这个"papers, please"体制的代价远不止于不便。
🔗 https://expression.fire.org/p/the-papers-please-era-of-the-internet

---

**已跳过：** 军事流感疫苗、Om Malik 逝世讣告、Apple 涨价（价格变动、无新洞察）、GE-Proton 更新

**已标记全部 20 篇为已读 ✅**
