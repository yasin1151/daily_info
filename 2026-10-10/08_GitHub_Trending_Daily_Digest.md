
# GitHub Trending 每日推送｜2026-10-10

今天 Trending 上扫到 3 个新项目，全部与 AI 应用开发直接相关：一个是 LLM 网关的底层重写，一个是 3D 重建的基础模型，一个是给 AI 编程助手用的 SwiftUI 技能包。

---

## 一、新增项目（3 条）

### 1. BerriAI/litellm — LLM 网关正在用 Rust 重写内核

**简介**：最主流的开源 AI Gateway 之一，一个接口统一调用 100+ LLM（OpenAI/Anthropic/Gemini/Bedrock/Azure/Vertex/vLLM 等），提供虚拟密钥、花费追踪、护栏、负载均衡和管理面板。最新版本定位已改为「Rust core with Python SDK」——核心网关用 Rust 重写，Python SDK 拆成独立的 `litellm-core` 包。

**为什么值得关注**：这是 AI 基础设施层的事实标准之一，Netflix 等公司在用。把热路径换成 Rust，说明这个领域已经进入「拼延迟和吞吐」的阶段（官方称 1k RPS 下 P95 仅 8ms）。如果你在生产环境做过 LLM 代理层选型，这次架构切换值得跟一下迁移成本。另外仓库 open issues 高达 5,418，社区体量大但也反映出维护压力。

**Stars**：60,643（今日 +95）｜Python / Rust｜Apache 系（NOASSERTION）
**链接**：https://github.com/BerriAI/litellm

---

### 2. Robbyant/lingbot-map — 流式 3D 重建的基础模型

**简介**：Robbyant 团队出的前馈式 3D 基础模型，做**流式**三维重建。核心是「Geometric Context Transformer」，把坐标锚定、稠密几何线索、长程漂移校正统一进一个流式框架里；配合分页 KV cache 注意力，在 518×378 分辨率下能稳定跑到约 20 FPS，序列超过 10,000 帧仍不崩。

**为什么值得关注**：标注是 ECCV 2026 最佳论文候选。它对标的是「流式方案 vs 传统迭代优化」两条路线，且直接开源了模型权重（HuggingFace + ModelScope，Apache-2.0）。对做机器人、AR/VR、自动驾驶感知里 SLAM/重建的人来说，这是一个能直接跑起来的候选替代方案——重点不在精度单点，而在**长序列不漂移 + 实时帧率**这个工程组合。

**Stars**：17,682（今日 +109）｜Python｜Apache-2.0
**链接**：https://github.com/Robbyant/lingbot-map

---

### 3. twostraws/SwiftUI-Agent-Skill — 专治 LLM 写 SwiftUI 的坏习惯

**简介**：Paul Hudson（Hacking with Swift 作者）做的 Agent Skill，教 AI 编程助手写更现代、更简洁的 SwiftUI，覆盖导航、布局、动画、状态管理、VoiceOver 无障碍和已废弃 API。明确点出「以 LLM 实际会犯的错误为靶子」，基于他多年的 `AGENTS.md` 积累，采用 agentskills.io 的通用 Agent Skills 格式。

**为什么值得关注**：这是「技能包/Agent Skill 化」趋势的一个好样本——把资深开发者的经验固化成 agent 可直接调用的资产，而不是塞进 prompt。装一行命令（`npx skills add ...`）就能进 Claude Code、Codex、Gemini、Cursor；Claude Code 还能走 plugin marketplace。同一作者还有 SwiftData、Swift Concurrency、Swift Testing 三个姊妹包。

**Stars**：5,410（今日 +88）｜MIT
**链接**：https://github.com/twostraws/SwiftUI-Agent-Skill

---

## 二、Trending 榜上其他 AI 相关项目（已追踪，附今日数据）

- **morluto/rea**（TypeScript，44,998 ⭐，今日 **+15,335**）— 用 agent 反编译/逆向，从 App 行为一路挖到原生二进制。今日涨幅榜第一，安全+Agent 交叉方向，值得单独盯一下。
- **storytold/artcraft**（Rust，11,364 ⭐，今日 +3,723）— 面向艺术家/设计师/影视的「有意图的创作引擎」。
- **cathrynlavery/diagram-design**（HTML，47,824 ⭐，今日 +1,744）— Claude Code / Codex / Copilot 用的编辑级图表设计技能，42 种图表类型，自包含 HTML+SVG，作者原话「No Mermaid slop」。
- **mattpocock/skills**（Shell，282,623 ⭐，今日 +1,696）— 「Skills for Real Engineers」，作者 `.agents` 目录直接开源。
- **anthropics/knowledge-work-plugins**（Python，28,229 ⭐，今日 +714）— Anthropic 官方开源的知识工作者插件库，主要给 Claude Cowork 用。
- **addyosmani/agent-skills**（JavaScript，103,964 ⭐，今日 +523）— Addy Osmani 的生产级 AI 编码 agent 技能集。
- **alibaba/open-code-review**（Go，45,175 ⭐，今日 +323）— 阿里规模化验证过的代码审查工具：确定性流水线 + LLM Agent 混合架构，行级精确定位，内置 NPE/线程安全/XSS/SQL 注入多语言规则集。

（榜单另有 boykopovar/AnyPS5 等非 AI 项目，未收录。）

---

## 三、一句话总结

今天的信号集中在两点：**一是 Agent Skills / 技能包这一层正在快速被标准化和商品化**（今天榜上至少 5 个是技能包，从 SwiftUI 到图表设计到通用工程技能）；**二是 AI 基础设施开始拼底层性能**（litellm 换 Rust 内核）。昨天已在榜的 litellm、lingbot-map、SwiftUI-Agent-Skill 三个新项目均已完成入库并标记已读。
