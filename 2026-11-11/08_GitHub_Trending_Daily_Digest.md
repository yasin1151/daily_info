
# GitHub Trending 日报 · 2026-11-11

**今日榜单主线：Agent Skills 生态正占据榜首。** 12 个热榜项目中有 4 个是“给 AI 编码 Agent 用的技能包”，今日合计新增 4,925 stars；Meta 的“面向 agent 的设计系统”Astryx 单日涨幅 3,111，位列涨幅第一。榜单重心已从“做 Agent 的框架”转向“给 Agent 装经验”。

---

## 一、Skills 生态（今日主场）

**1. mattpocock/skills — ★320,872（+1,223）**
Matt Pocock（TypeScript 教育领域知名作者）把自家 `.agents` 目录里的技能原样开源，定位是“给真工程师的技能包”，并非玩具 demo。
值得关注：它在技能类仓库中 star 数最高，说明社区已将其视为“可直接导入工作流的生产资料”，而非仅仅阅读的参考。
https://github.com/mattpocock/skills

**2. anthropics/skills — ★192,273（+1,676）**
Anthropic 官方 Agent Skills 仓库，采用 Apache 2.0 许可，并且把 Claude 文档能力底层的 `docx / pdf / pptx / xlsx` 技能源码也一并开源。
值得关注：这是事实标准。如果想了解“技能”这一形态怎么组织（每个技能一个文件夹加 SKILL.md），或者想直接获取官方文档处理技能，这个仓库是源头。
https://github.com/anthropics/skills

**3. addyosmani/agent-skills — ★115,125（+465）**
Addy Osmani（Google Chrome 团队）发布的“生产级工程技能”，把资深工程师的工作流拆成 9 个 slash 命令：`/spec → /plan → /build → /test → /constraints → /review → /webperf → /code-simplify → /ship`。
值得关注：它是当前在把“软件工程纪律”固化进 Agent 方面做得最完整的一套。`/build auto` 允许先批准一次计划，然后自动跑完全部任务，但每个任务仍然测试驱动、单独提交，遇到失败或高风险步骤就暂停；它去掉的是人工一步一步推动的过程，并未去掉验证环节。
https://github.com/addyosmani/agent-skills

---

## 二、Agent 基础设施

**4. meta/astryx — ★22,695（+3,111，今日涨幅第一）**
Meta 开源的设计系统，在内部已发展八年，支撑 13,000+ 应用；包含 150+ 无障碍组件、主题、暗色模式、模板和 CLI，技术栈是 React 19 + StyleX，目前 Beta。
值得关注：它的核心卖点是“人和 AI 助手使用同一套工具链构建 UI”：组件可在任意层级组合，`swizzle` 能把组件源码整个导出到你的项目里。这是大厂第一次把“agent 可直接消费的 UI 基建”作为设计系统的首要目标；它正在抢占“Agent 做前端”的默认组件库位置。
https://github.com/meta/astryx

**5. vercel-labs/agent-browser — ★49,171（+775）**
Vercel Labs 的 Rust 原生浏览器自动化 CLI：`snapshot` 把页面转成紧凑的无障碍树，每个元素带 `@e1` 引用，Agent 点一下、再快照、确认结果；后台 daemon 使用 CDP 保持浏览器常驻，每条命令只是一次短 shell 调用。
值得关注：它专门解决了“Agent 操作浏览器时，每一步都返回大段 HTML，从而耗尽上下文”的问题。点击目标被遮挡或不可见时，它会直接报失败，而不会假装成功；这个细节比功能列表更有价值。
https://github.com/vercel-labs/agent-browser

**6. ranxianglei/billion-context — ★6,285（+374）**
上下文压缩插件，面向“月级超长单会话”：宣称 100K 窗口就够用、节省 5 倍 token，并随代码一起开源了一篇论文（MIT），数据为 4.5 个月、3 台机器、174,327 次模型调用、累计 18.76B 输入 token，零窗口越界。
值得关注：它是当前少见的“以长期真实使用数据说话”的长上下文方案，并附有第三方 1500 条评测（LongMemEval-S / ContextBench / MemoryAgentBench），与三种 RAG 方案进行了对比。中文项目，社区活跃度（QQ 群已加满三个）也值得留意。
https://github.com/ranxianglei/billion-context

**7. homeassistant-ai/ha-mcp — ★6,612（+792）**
用 Claude / ChatGPT 直接配置和自动化 Home Assistant 的 MCP 服务。v9 起改为 HACS / Marketplace 集成，在 HA 进程内运行，覆盖 HA OS、Supervised、Container、Core 全部安装形态。
值得关注：MCP 从“开发者玩具”进入消费级智能家居，它是本周最典型的落地案例；单日 +792 说明需求真实存在。
https://github.com/homeassistant-ai/ha-mcp

**8. anthropics/claude-quickstarts — ★20,473（+530）**
官方 Claude API 快速上手项目集，定位是“能直接部署的示例”，并非只能用来看的 notebook。
值得关注：想上手 Claude API 时，可把它与其他项目的 README 一起对照，比读文档更快。
https://github.com/anthropics/claude-quickstarts

---

## 三、其他上榜（非 AI，但值得一提）

- **sherlock-project/sherlock** ★108,906（+2,387）：跨社交网络按用户名查找账号，安全、取证老牌工具今天意外回榜。
- **google-deepmind/mujoco** ★17,333（+453）：通用物理仿真器，机器人、强化学习研究的常用基础工具。
- **tokio-rs/topcoat** ★6,779（+192）：Tokio 团队新出的 Rust 全栈 Web 框架，主打“电池内置、少配置”，仍标注 early-stage，会出现破坏性变更。今天是新进入榜单的项目。
- **we-promise/sure** ★11,893（+184）：开源个人财务 App（Ruby）。今天同样是新进入榜单的项目。

---

**一句话观察：** 今天最明显的信号是“技能”正在成为继 prompt、MCP 之后的第三个可分发单元：Anthropic 定义标准、Addy 和 Matt 这类一线工程师提供工程实践、Astryx 这类基础设施方开始主动适配“agent 消费”。如果只挑一个方向跟进，就去看 agent-skills 的 `/spec → /ship` 流程如何组织，因为那是目前最接近“可复用工程方法论”的东西。

已抓取 12 个项目、标记 2 条新增为已读，blogwatcher 队列已清空。
