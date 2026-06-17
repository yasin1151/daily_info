
## r/UnrealEngine 今日技术热帖

### 1) Epic 开源面向 Unreal 的版本控制系统 Lore
摘要：Epic 在 Unreal Fest 宣布 Lore：一个已在 UEFN / Unreal Revision Control 中使用、现在开放给社区的版本控制系统。它主打二进制资产友好：内容寻址、分块上传、跨仓库去重、多租户隔离，并强调 API-first。值得关注的是，它直接瞄准 Unreal 项目长期依赖 Perforce、Git 又不擅长大资产的痛点，可能改变中小团队的资产协作、CI/CD 和编辑器集成工作流。  
高赞评论：
- u/EliasWick（赞数隐藏）：关注 Perforce 与 Epic 长期合作关系，立场是“这会冲击既有生态”。
- u/hyperdynesystems（赞数隐藏）：认为 Perforce 成本高、集成体验老旧，Epic 自研 Unreal 专用 VCS 是合理演进。
- u/bastardlessword（赞数隐藏）：认为 Plastic、Diversion 等竞品压力更大，但大型公司不会立刻迁出 Perforce。
原帖：https://www.reddit.com/r/unrealengine/comments/1u8excv/

### 2) UE6 之后 Blueprint 可能被弃用：视觉脚本工作流争议升温
摘要：帖子讨论 State of Unreal 2026 中关于 UE6 未来路线的信息：Blueprint 将在更长期阶段被 deprecated，而 Epic 似乎会把“无代码/视觉化编程”能力转向 Verse 或新的视觉脚本层。这个话题值得关注，因为 Blueprint 不只是新手工具，也深度嵌入技术美术、动画、关卡逻辑和快速原型流程；若迁移方向处理不好，会影响团队分工、版本控制、调试和艺术管线。  
高赞评论：
- u/IAmTiiX（赞数隐藏）：主用 Blueprint，认为弃用令人遗憾，但可能还有 2-3 年缓冲。
- u/Rabbitical（赞数隐藏）：支持向文本/Verse 迁移，认为 Blueprint 在合并、调试、变量和接口维护上工作流糟糕。
- u/Shail666（赞数隐藏）：从技术动画角度担心 AAA 美术管线学习曲线陡增。
原帖：https://www.reddit.com/r/unrealengine/comments/1u8dm2w/

### 3) UE6 可能弱化 Actor / Blueprint，转向 Scene Graph 与实体组件模型
摘要：另一条高热讨论聚焦“Deprecating Actors and Blueprints in UE6?!”。楼主引用 Marcus Wassmer 与 Epic 的 UE6 路线文章，询问 UEFN 的 Scene Graph 是否代表 UE6 的核心架构方向。它值得关注的点不只是 Blueprint，而是 Unreal 传统 Actor-centric 架构是否会逐步迁移到更数据化、实体组件化的模型；这会影响 gameplay framework、编辑器对象模型、序列化、多人协作与大型世界组织方式。  
高赞评论：
- u/gnatinator（赞数隐藏）：认为弃用很奇怪，因为动画图、材质图等大量系统依赖图编辑器。
- u/namrog84（赞数隐藏）：区分 Blueprint 与 graph editor，认为可能是先迁到 Verse，再构建生成 Verse 的图系统。
- u/PuzzledBridge（赞数隐藏）：认为 Scene Graph entity/component 会替代 Actor/Blueprint，并对 UEFN 经验持正面态度。
原帖：https://www.reddit.com/r/unrealengine/comments/1u8dkx1/

### 4) Unreal Engine 5.8.0 已在 Launcher 可用，轻量 Lumen 与修复更受关注
摘要：UE 5.8.0 上线 Launcher。帖子本身信息较短，但评论把焦点放在 release notes、Blueprint 修复、轻量 Lumen 与 Linux 支持上。值得关注的是，社区对版本更新的评价越来越偏向“能否改善真实项目性能与稳定性”，而不是只看宣传功能。轻量 Lumen 如果能降低 UE5 游戏常见的 GI 成本，可能对主机、移动端或性能敏感项目更有实际价值。  
高赞评论：
- u/SoonAmuck（赞数隐藏）：认为 release notes 和性能修复比营销功能更值得看。
- u/WonderFactory（赞数隐藏）：最期待 lightweight Lumen，认为 UE5 最大痛点之一是性能。
- u/TLable（赞数隐藏）：补充 Linux Mint 可从源码构建，且有 Win/Mac/Linux 二进制。
原帖：https://www.reddit.com/r/unrealengine/comments/1u8a5ad/

### 5) 开源 UE5 C++ 车辆物理系统：Async Physics、轮胎与悬挂细节丰富
摘要：作者发布一个开源 UE5 车辆物理系统，C++ 实现并运行在 Async Physics 上，包含 Pacejka 风格轮胎 slip-friction、combined slip、非线性载荷敏感度、多种悬挂结构、实时悬挂几何求解、传动轴扭转刚度、发动机/离合/变速箱等 1D 物理模拟。相比展示帖，这条信息量较高，适合关注 Chaos Vehicles 替代方案、赛车/载具手感调校、物理线程与 Blueprint 暴露接口的开发者跟进。  
高赞评论：
- u/Ok-Art-2255（赞数隐藏）：认为项目正好解决自己不想购买并学习 R-Tune 的需求，已 star/fork。
- u/extrapower99（赞数隐藏）：建议移除旧 AsyncTickPhysics 插件，改用引擎内置 async physics 能力。
- u/L_Mcqueen（赞数隐藏）：解释保留插件是因为需要把 wheel component 的物理计算接口暴露给 Blueprint。
原帖：https://www.reddit.com/r/unrealengine/comments/1u87sxa/
