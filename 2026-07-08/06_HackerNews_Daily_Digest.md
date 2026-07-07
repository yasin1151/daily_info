
HackerNews 新帖技术精选（已标记 20 条为已读）

1. **AI 审计发现 Cloudflare CIRCL 七个真实密码学漏洞**  
摘要：zkSecurity 将 AI 审计管线用于 Cloudflare 的 CIRCL 实验密码学库，确认了 7 个已修复漏洞，包括 threshold RSA 精度损失、BLS 聚合验证问题、HPKE PSK 校验绕过和 CP-ABE 访问控制破坏。文章也强调 AI 产出的是候选发现，严重性判断仍需人工复核。  
为什么值得关注：这是 AI agent 用于真实安全审计的高质量案例，尤其适合关注 LLM+安全、密码学库审计和自动化漏洞发现的人。  
原文：https://blog.zksecurity.xyz/posts/circl-bugs/

2. **Rowboat：开源、本地优先的 AI coworker**  
摘要：Rowboat 是一个开源 AI coworker 项目，定位为带记忆能力的本地优先 Claude Desktop 替代品。GitHub 页面显示项目已有 15k+ stars，近期仍活跃开发，包含 agent 应用、工具集成、记忆和桌面工作流相关能力。  
为什么值得关注：AI 桌面助手正在从聊天窗口走向本地工作流编排，Rowboat 代表了开源路线的一类产品形态。  
原文：https://github.com/rowboatlabs/rowboat

3. **PgDog：为什么还要做一个 Postgres 连接池**  
摘要：PgDog 认为传统连接池容易泄漏抽象，迫使应用放弃 `SET`、RLS session state、LISTEN/NOTIFY 等 Postgres 特性。它内置 SQL parser 跟踪连接状态，用 pipelining 同步服务端状态，并基于 Tokio 多线程提升连接利用率。  
为什么值得关注：这不是简单复刻 PgBouncer，而是围绕“尽量不改变 Postgres 语义”的基础设施设计，适合数据库和后端架构关注者。  
原文：https://pgdog.dev/blog/why-yet-another-connection-pooler

4. **Halo：面向 AI agent 的可篡改检测运行记录**  
摘要：Halo 提供 append-only、hash-chained 的 agent runtime records，把工具调用、模型调用、数据访问、审批等动作写入可验证日志。目标是让客户或安全团队能验证 agent 对数据做了什么，而不只依赖供应商文字承诺。  
为什么值得关注：AI agent 进入企业场景后，可审计性和供应商信任会成为核心问题；Halo 把这个问题具体化成开放记录格式和参考实现。  
原文：https://github.com/bkuan001/halo-record

5. **Kokoro：本地 CPU 友好的高质量 TTS**  
摘要：文章演示了 Kokoro 82M 参数 TTS 模型在本地 CPU 上生成较高质量语音，可通过 Kokoro-FastAPI 容器部署，并兼容 OpenAI speech API。作者给出性能数据：M2 Pro 约 4.5 秒、Ryzen 8745HS 约 1.5 秒生成测试段落。  
为什么值得关注：本地语音合成正在变得足够实用，对隐私敏感 AI 助手、本地 LLM 语音交互和低成本部署都有价值。  
原文：https://ariya.io/2026/03/local-cpu-friendly-high-quality-tts-text-to-speech-with-kokoro/

6. **Docx-CLI：让 AI agent 读写 Word 文档的命令行工具**  
摘要：Docx-CLI 面向 Claude、Codex 等 agent，提供读取、编辑、评论 `.docx` 文件并保持格式保真的 CLI。项目还包含 Claude/Codex 插件或 skill 相关目录，目标是减少 agent 处理 Word 文件时的时间和 token 消耗。  
为什么值得关注：办公文档仍是企业自动化的硬骨头；能可靠编辑 Word 且保留格式的工具，对 agent 落地非常实用。  
原文：https://github.com/kklimuk/docx-cli

7. **l：面向 k/q/qSQL 的新运行时**  
摘要：l 是一个新的 k4、q、qSQL 运行时，主打不修改现有代码即可获得透明压缩向量、SIMD 和自动并行。项目强调现代硬件常受内存带宽限制，因此让 primitives 直接在压缩结构上运行可以减少数据搬运。  
为什么值得关注：数组语言和时序数据库生态相对小众但技术密度高，l 展示了“兼容旧语言、替换执行引擎”的性能优化路线。  
原文：https://lv1.sh/

8. **30papers.com：Ilya 给 John Carmack 的 30 篇 ML 论文清单**  
摘要：该站把 Ilya Sutskever 曾给 John Carmack 的 30 篇关键 ML 阅读材料做成更易浏览的列表，包含 CNN、RNN、LSTM、ResNet、Attention、Transformer、Scaling Laws、GPipe、Kolmogorov Complexity 等主题。  
为什么值得关注：这是一份紧凑的机器学习基础阅读路线，适合用来回看深度学习发展脉络，而不是追逐碎片化新论文。  
原文：https://30papers.com/

9. **Davit：Apple Containers 的原生 macOS UI**  
摘要：Davit 是一个面向 Apple container 平台的原生 macOS 应用，可在 Apple silicon 上运行 Linux 容器，不依赖 Docker Desktop。它提供容器、镜像、卷、网络、终端、编辑重建和平台安装等功能，要求 macOS 15+。  
为什么值得关注：Apple 官方容器平台还在早期生态阶段，Davit 这类原生 UI 工具可能降低开发者尝试成本。  
原文：https://davit.app

10. **Automating AI Away：把 AI 易错部分替换成确定性工具**  
摘要：作者批评 AI agent 即使被明确要求不要手写解析逻辑，仍会尝试手工解析；他的做法是用 Ragel 等确定性工具生成 parser，并周期性扫描代码库移除 agent 写出的坏模式。核心观点是：应该自动化掉 AI 不擅长的部分。  
为什么值得关注：这篇短文抓住了 agent 工程中的一个现实问题：LLM 不是所有任务都该亲自做，确定性工具、生成器和静态检查仍然是提高可靠性的关键。  
原文：https://replicated.live/blog/away
