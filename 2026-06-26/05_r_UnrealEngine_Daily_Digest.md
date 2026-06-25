
---

## 🔥 r/UnrealEngine 今日热帖推送 (2026.06.26)

---

### 1️⃣ 未来 C++ 在 UE 中的定位：UE6 是否强制 Verse？(31⬆ | 91 评论)

**背景：** 有用户发帖询问，随着 UE6 将用 Verse 取代 Blueprint 作为主要游戏逻辑语言（Epic 官方已透露的方向），是否会进一步要求开发者完全转向 Verse，而无法再用纯 C++ 开发游戏。

**核心：** 这是自 Epic 宣布 Verse 路线图以来社区最激烈争论的集中爆发——C++ 是否只是"暂时保留"、Verse 的泛用性是否真的优越、以及独立/中小开发者是否能承受被迫学习新语言+新工具链的成本。

**为什么值得关注：** 虽然高赞回答（57⬆ /u/Baazar）明确指出 C++ 不会被移除——引擎插件、渲染、核心系统仍然是 C++——但 Verse 将接管新框架中的顶层场景图（Scene Graph）逻辑。这意味着 **UE6 的双轨制已成定局**：如果你写引擎/渲染层，C++ 不变；但如果你做 gameplay 编程，必须使用 Verse 对接新 Scene Graph。多位开发者指出，此举可能迫使中小工作室在 UE5 上停留更久，成为 UE6 采用率的隐形障碍。

**评论精选：**

> [57⬆] u/Baazar：*"C++ 不会被从 UE 移除，但它将被移除作为 gameplay 编程的主要语言。如果你写引擎插件、渲染代码或核心系统，C++ 不会变。如果你用新框架构建顶层 gameplay 逻辑，那就是 Verse。"* → 作为最高赞回答，清晰分化了引擎层和应用层的语言策略，是理解 Epic 整体路线的最关键信号。

> [21⬆] u/shableep：*"我理解 Verse 的理想，但我觉得它没有合理权衡实际游戏开发者的真实痛点。组合式设计很好，但这完全可以在 C++ 里做到。"* → 代表了对 Epic 方向持保留态度的独立开发者声音，核心质疑是"引进新语言解决什么问题？"

> [16⬆] u/phoenixflare599：*"大量谣言来自独立/爱好者开发者。C++ 不会消失，你仍然可以用 C++ 开发 UE6。"* → 反映了社区内对信息误传的焦虑，以及 Epic 沟通不够透明的问题。

🔗 https://www.reddit.com/r/unrealengine/comments/1ue4a97/future_of_c/

---

### 2️⃣ UE5 游戏模组化的可行性：如何实现类似 Creation Kit 的 Modkit？(32⬆ | 17 评论)

**背景：** 随着众多大工作室转向 UE5，玩家对游戏模组化的需求日益增长。发帖者询问，游戏工作室能否（以及多难）为社区制作独立的 Modkit 工具（类似 Bethesda 的 Creation Kit）。

**核心：** 讨论揭示了一个关键矛盾——UE5 的 Game Features / Modular Gameplay 系统并未默认设计为可导出 mod 的架构。要让模组化成为现实，必须在项目架构初期就有意识地进行依赖注入设计，且要么自研完整的 Devkit，要么像 Ark 的 Wildcard 工作室那样向 Epic 授权精简版引擎。

**为什么值得关注：** 这是关于 UE5 模组化上限的深度讨论。几个具体的架构建议（依赖注入、Game Features 的灰色地带、打包 Plugin 分发）直接给出了**可落地的工程方案**，对任何需要在 UE5 中支持社区 mod 的工作室都有直接参考价值。

**评论精选：**

> [21⬆] u/yamsyamsya：*"可行，但难度取决于项目复杂度。你必须从一开始就设计为易于添加 mod —— 这完全取决于你如何构建游戏。"* → 设定了讨论基调：模组化不是"加个开关"，而是贯穿整个架构的约束条件。

> [21⬆] u/MarcusBuer：*"要么自研 Devkit，要么从 Epic 授权精简版引擎（像 Ark 那样）——输出为打包好的 Plugin，利用 Unreal 的 Game Features 系统加载。"* → 给出了两条经过验证的实践路径，是目前最成熟的参考方案。

> [17⬆] u/Plane_Reveal_8868：*"你必须明确围绕依赖注入设计。经典场景：支持多配方组的 Crafting Station——通过数据驱动注册配方，而不是硬编码。"* → 提供了一段具体的 DI 设计思路，工程细节扎实。

🔗 https://www.reddit.com/r/unrealengine/comments/1uei8q0/moddability_of_unrealengine/

---

### 3️⃣ 开源免费 UE5 C++ 插件：将臃肿 PCG 节点链压缩为单一编译节点 (18⬆ | 6 评论)

**背景：** 开发者 James-Joslin 因个人项目中的 PCG 图形过于混乱，将大量逻辑用 C++ 重写为编译节点，并开源了 **PCGExtensionsPlugin**（GitHub），涵盖了岩石生成、地形嵌入/法线计算、高密度地表散布（空间网格方案）、分层植被（噪声聚类+生物群落混合）、基于磁盘分布散布+地形射线投射+坡度过滤等核心节点。

**核心：** 这是一个直接对标 PCGEx/PCGExtendedToolkit 的开源方案，全部 C++ 源码公开。核心卖点是将巨量的 PCG 蓝图节点链"压缩"成少量 C++ 编译节点，性能提升显著，且完全免费。

**为什么值得关注：** 对 UE5 PCG 工作流重度用户而言，这是**直接节省数小时重构时间的资源**。六条评论虽然不多，但包括命名建议、与 PCGEx 的关系澄清、"是否 AI 生成"的质疑及其回应——项目有可见的社区真实互动，不是自卖自夸。需要 UE 5.7+。

**评论精选：**

> [Hidden] u/hellomistershifty：*"看起来很不错，但建议改个名字避免与 PCGEx/PCGExtendedToolkit 混淆。"* → 实用的命名建议，反映出同类工具生态的命名冲突问题。

> [Hidden] u/obviouslydeficient：*"这是 vibe coded 的吗？"* → 对开源 UE 插件质量的社区信任度担忧，是当前 AI 生成代码泛滥背景下的合理质疑。

> [Hidden] u/ConnectionThis8333（OP）：*"不是。README 是 AI 生成的因为我懒，但代码是从另一个项目迁移过来的。"* → OP 的坦诚回应反而增加了项目的可信度。

🔗 https://www.reddit.com/r/unrealengine/comments/1uf57kb/open_source_free_ue5_c_plugin_that_squashes/
