
GitHub Trending 日榜已抓取完成：15 个项目，13 个与 AI、Agent、开发工具相关，2 个不相关（lz4 压缩库、DiscImageStudio 光盘刻录），后者剔除。

---

# GitHub Trending 日报 · 2026-11-06

**今日最明显的信号：15 个上榜项目里有 5 个是 “agent skills” 仓库。** mattpocock、Google、ConardLi、scenario-labs、garrytan 各怀一套技能包同时上榜，Star 增量从 199 到 2053 不等。这说明生态重心已从“造 Agent 框架”转向“为 Agent 编写可复用的技能与规程”：模型能力本身不再是瓶颈，如何给它一套可靠、可组装的工作方法才是。第二个信号是 Vercel Labs 同时占据两个位置（agent-desktop、agent-browser），瞄准的都是同一件事：让 Agent 操作界面，不再靠截屏和像素匹配。

---

## 重点

**1. NVIDIA/auto-ontology — 给 Agent 的“数据语义层”**
Python · 7,248 stars · 今日 +2,707（今日增量第一）

NVIDIA 开源的库，从企业元数据中自动生成本体（ontology），把分散在不同系统里的指标定义对齐，再通过 MCP、CLI、API 提供给任意 Agent 使用。官方 README 提出的问题很实在：“revnue 指标答得再快，数字错了就一文不值”——Agent 能查数据库不等于查得对，缺的是“数据在哪、什么含义、能不能用、从哪来”这层上下文。它同时做校验：生成的查询要对照认证过的定义和血缘检查，每个答案都带出处。

值得关注的原因：这是把“语义层/知识图谱”这类老概念重新包装成 Agent 基础设施，而且出手的是 NVIDIA，配套的是 MCP 而非自研协议。做数据平台和内部 BI Agent 的人，这套思路可以直接借鉴。

https://github.com/NVIDIA/auto-ontology

**2. vercel-labs/agent-desktop — 不靠截图操作桌面**
Rust · 16,786 stars · 今日 +2,173

通过操作系统的 accessibility tree（无障碍树）读写桌面应用，跨 macOS/Windows/Linux，不使用截图和像素匹配。已有 npm 包。

值得关注的原因：computer use 的老大难是分辨率和主题一变，视觉定位就失效；读无障碍树等于拿到了结构化的 UI DOM，稳定性高一个量级。对做 RPA、桌面自动化的团队来说，这是比视觉方案更靠谱的路径。

https://github.com/vercel-labs/agent-desktop

**3. mattpocock/skills — 今日 Star 总量最高**
Shell · 315,163 stars · 今日 +2,053

TypeScript 圈知名教育者 Matt Pocock 的日常技能集，标题是 “Skills for Real Engineers”，副标题直接开火：不是 vibe coding。README 里点名批评 GSD、BMAD、Spec-Kit 这类流程框架——“它们靠接管整个流程来帮忙，代价是你失去控制权，流程里的 bug 也变得难以排查”。他的方案是技能保持小而可组合、任何模型都能用，并鼓励用户改进或改成自己的版本。

值得关注的原因：这是对“重型 Agent 工作流框架”的一次公开反驳，也是当前 skills 生态里讨论度最高的一种立场：不要大而全的流程引擎，要能被你随手修改的零件。

https://github.com/mattpocock/skills

**4. D4Vinci/Scrapling — 抓取框架**
Python · 97,921 stars · 今日 +1,661

自称处理“从单个请求到全站爬取”全部场景的 Web 抓取框架，自适应选择器是它的核心卖点。

值得关注的原因：AI 数据管线里最脏的一环永远是采集。这个项目的 Star 体量说明它已经是事实标准之一，配合前面的 skills 生态，等于给 Agent 接上了“能读任意网页”的能力。

https://github.com/D4Vinci/Scrapling

**5. floci-io/floci — 本地云模拟器，主打免费**
Java · 30,376 stars · 今日 +784

“Any Cloud. Locally.” 不用账号、不用 auth token、没有功能门槛，`docker compose up` 就能跑，定位是 LocalStack 这类 AWS 本地模拟器的免费替代。

值得关注的原因：LocalStack 把核心功能收进付费版后，这块一直有怨气。Agent 要跑集成测试就得有本地云环境，免费替代出现后，CI 成本能降一截。

https://github.com/floci-io/floci

**6. max-sixty/worktrunk — 为并行 Agent 管理 git worktree**
Rust · 11,495 stars · 今日 +546

专门给 git worktree 做的 CLI，设计目标就是“并行 AI Agent 工作流”。

值得关注的原因：同时开三五个 Agent 改同一个仓库，合并冲突和分支混乱是必然的。这是很典型的“Agent 用多了以后才暴露出来的工具需求”——不是 AI 项目，但是 AI 工作流的基础设施。同类需求可以参考我们自己的多 Agent 隔离做法。

https://github.com/max-sixty/worktrunk

**7. Usagi-org/ai-goofish-monitor — 闲鱼监控与智能分析**
Python · 17,502 stars · 今日 +242

基于 Playwright 加 AI 的多任务实时/定时闲鱼监控系统，带完整后台管理 UI，从海量商品里筛出符合预期的货。

值得关注的原因：中文项目里少见的“AI 落到具体交易场景”的完整产品，不是 demo。技术上没什么新东西，但产品完成度高，适合当成 AI 应用层的参考案例看。

https://github.com/Usagi-org/ai-goofish-monitor

---

## 其余上榜（简列）

- **google/skills** — 22,350 stars，+199 — Google 官方为自家产品和技术写的 Agent Skills，大厂开始把“教 Agent 用我的产品”当成官方交付物。https://github.com/google/skills
- **scenario-labs/skills** — 3,027 stars，+674 — 通过 Scenario MCP 让任意 Agent 生成图/视频/音频/3D，先报价再花钱，并保持角色与品牌一致。https://github.com/scenario-labs/skills
- **garrytan/gstack** — 139,924 stars，+608 — 把 Garry Tan 的 Claude Code 配置整套开源：23 个带观点的工具，分别扮演 CEO、设计师、工程经理、发布经理、文档工程师和 QA。https://github.com/garrytan/gstack
- **ConardLi/garden-skills** — 14,111 stars，+241 — 中文社区的 Skills 合集，涵盖网页设计、知识检索、图像生成。https://github.com/ConardLi/garden-skills
- **microsoft/VibeVoice** — 55,878 stars，+214 — 微软开源的前沿语音 AI。https://github.com/microsoft/VibeVoice
- **vercel-labs/agent-browser** — 45,854 stars，+181 — 给 AI Agent 用的浏览器自动化 CLI，今天 blogwatcher 也单独报了这一条。https://github.com/vercel-labs/agent-browser

---

**一句话总结**：今天没有新的模型或框架，全是“给 Agent 配套的工具层”——语义层、桌面操控、技能包、worktree 管理、本地云。基础设施正在围绕 Agent 重排一遍。

已标记 2 条未读为已读，blogwatcher 队列清空。
