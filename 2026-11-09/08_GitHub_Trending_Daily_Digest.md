
# GitHub Trending 日报 · 2026-11-09

今日上榜 **9 个项目，其中 7 个与 AI、Agent 直接相关**。榜单集中在 Agent 的基础设施方向：浏览器、技能、上下文、本地运行时；只关注“模型有多强”的项目占比已经很少。

---

### 1. OpenMausBot：把“一支 AI 团队”做成聊天软件
**milind-soni/OpenMausBot** · TypeScript · 18.2k stars · **+1,437 today**

开源版 Grok Bot；Electron 桌面端，侧栏里每个“联系人”就是一个真 agent——底层跑本地 Claude 或 Codex，各有独立人格、独立模型、独立云电脑和已连接的 app。可以像跟人聊天一样跟它说话，看它干活，在关键步骤上批准。

**为什么值得关注**：它把“多 agent 协作”从 CLI 编排落到了 IM 式交互上，也就是“你有一支团队”的心智模型，比 pipeline 更接近普通人使用 AI 的方式。同时也是对 Meta Muse、OpenAI dots、Cue by Manus 这类产品的开源替代方案：本地优先、自带模型，不用换订阅。项目 8 月才创建，3 个月冲到 18k，但 open issues 已达 827，功能上得很快、打磨还没跟上。

https://github.com/milind-soni/OpenMausBot

---

### 2. meta/astryx：为“人和 agent 一起写代码”重做的设计系统
**meta/astryx** · TypeScript · 16.6k stars · **+863 today**

Meta 开源的 React 19 + StyleX 设计系统，官方定位是“fully customizable and agent ready”，目前 Beta，MIT 协议。

**为什么值得关注**：设计系统的传统目标用户是设计师和前端；astryx 把它明确扩展到 agent。当 UI 越来越多由模型生成时，组件库需要提供稳定的语义约束和可预期 API，否则 agent 写出的界面样式会走样。这条路线如果成立，以后“组件库好不好”会多一个评测维度：agent 用起来顺不顺。附 Storybook 和沙盒，可直接试。

https://github.com/meta/astryx

---

### 3. vercel-labs/agent-browser：给 agent 一个真正能开的浏览器
**vercel-labs/agent-browser** · Rust · 47.5k stars · **+812 today**

原生 Rust CLI，一条命令一步操作：`snapshot` 把页面返回成紧凑文本，每个可交互元素带 `@e1` 这样的引用，agent 直接按引用点击或输入，不用解析 DOM 和截图。

**为什么值得关注**：浏览器自动化一直是 agent 最费 token、最不稳定的环节。agent-browser 走的是“accessibility tree 加引用”的路子，而不是视觉识别路线，输出小、定位稳、成本低，是目前把这件事做得比较干净的一种设计。Vercel 出品、Apache-2.0，已在 npm 上分发。

https://github.com/vercel-labs/agent-browser

---

### 4. anthropics/skills：Agent Skills 事实标准的官方仓库
**anthropics/skills** · Python · 189.6k stars · **+793 today**

Anthropic 对 Claude Skills 的实现集合：技能就是一组指令、脚本和资源的文件夹，模型按需动态加载。覆盖创意（艺术、音乐、设计）、技术（测试 Web 应用、生成 MCP server）和企业流程。标准本身在 agentskills.io。

**为什么值得关注**：189k stars 和 22k forks 说明它已经不只是一个仓库，而是生态入口。open issues 1,499 反映出大量社区技能在往这里汇集。对开发者来说，这里的实际价值是看别人怎么把一段流程拆成模型能稳定复现的指令，这比读 API 文档更直接。

https://github.com/anthropics/skills

---

### 5. billion-context：把会话拖到“十亿 token”的上下文压缩层
**ranxianglei/billion-context** · TypeScript · 5.1k stars · **+460 today**

夹在 agent 和模型 API 之间，重写 Anthropic/OpenAI 的流式响应并做增量分层压缩。它给模型注入四个工具：`compress` 折叠一段消息为细粒度摘要、`decompress` 需要细节时还原、`search_context` 在摘要里检索、`acp_status` 查看用量。官方宣称单会话可跑数月、token 省 5 倍、100K 窗口够用。

**为什么值得关注**：它和“硬截断”或“主机自带 summarizer”的关键差别是**可逆，并且对 prefix cache 友好**。作者给出 4.5 个月、17.4 万次调用、187 亿输入 token 的长周期数据，还配了第三方 benchmark：ContextBench 第一、LongMemEval-S 比最佳 RAG 高 16.6%。它支持 Claude Code、Codex、OpenCode、pi、kimi、zcode、hermes 等十几个客户端。

需要注意两点：第一，多数客户端的接入方式是 **cert-MITM 代理**，也就是装证书、劫持流量，生产环境要评估；第二，5.1k stars 就堆了 932 个 open issues，说明问题密度不小，尝鲜可以，别急着上主力工作流。

https://github.com/ranxianglei/billion-context

---

### 6. NVKE：在自己机房的裸金属 GPU 上开托管 Kubernetes
**dsx-ai-factory/nvke** · Go · 828 stars · **+345 today**

NVIDIA Kubernetes Engine 的管理面，供平台团队安装后给客户开 K8s 集群；每个工作负载集群自带控制面、etcd 和节点池，客户用 kubectl 访问。Apache-2.0，明确标注 **preview，不建议上生产**。

**为什么值得关注**：自建 AI 工厂的团队一直缺一个“像公有云那样按租户开集群”的方案，NVKE 补的是这一层。但仓库存在 dsx-ai-factory 组织下而非 NVIDIA 官方 org，文档域名指向 nvidia.com，采用前最好核实发布主体和长期维护承诺。文档里提供纯模拟机器的本地 quickstart，没有 GPU 也能先跑通流程。

https://github.com/dsx-ai-factory/nvke

---

### 7–9. 其余上榜
- **sherlock-project/sherlock** · Python · 103.4k stars · **+2,372 today**：今日涨幅第一，但这是老牌 OSINT 工具回到榜单，跨社交网络按用户名反查账号。跟 AI 无关，需求背景大概是账号溯源、尽调、反诈。
- **anthropics/claude-quickstarts** · Python · 19.4k · **+28**：Claude API 的可部署示例集，涨势平淡，属于长尾参考。
- **google-deepmind/mujoco** · C++ · 16.4k · **+26**：物理仿真引擎，机器人、生物力学、RL 训练的底层设施，长期稳定上榜。

---

### 今天的共同点

这九个项目里，做“模型”的一个都没有，七个都在解决 **agent 怎么在真实环境里长时间、可靠地干活**：给它浏览器（agent-browser）、给它技能（skills）、给它记住长历史的能力（billion-context）、给它一张能坐进去的桌子（OpenMausBot）、让它能生成 UI（astryx）、给它算力底座（NVKE）。

其中 OpenMausBot 和 billion-context 都是今年 8 月建仓，三个月冲上万星，说明 agent 周边工具的热度还在加速，而且增长最快的是“把 agent 当员工用”这个想象力的落地件，而不是更聪明的模型封装。

---

*已标记 2 条未读（claude-quickstarts、mujoco）为已读。数据源：GitHub Trending（daily）+ GitHub API。*
