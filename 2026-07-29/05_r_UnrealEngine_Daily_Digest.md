
# r/UnrealEngine 今日技术热帖

> 抓取说明：redlib 公共实例本次访问失败（curl 35 / 0 字节），已按既定 fallback 使用 old.reddit 抓取 hot 列表与详情页；old.reddit 评论分数隐藏，因此赞数标注为“隐藏”。

## 1. PSA: Your Dynamic Nav Mesh is killing your frame rate.

**摘要：** 这帖讨论 UE5 动态 NavMesh 在大地图或可破坏/可编辑场景里的帧率成本。核心观点不是“禁用动态导航”，而是避免让整张地图持续重建：优先使用 Dynamic Modifiers Only、Nav Modifier Volumes、Navigation Invokers，并限制 tile、半径和并发。它值得关注，是因为很多开放世界、体素或多人项目会把 AI 寻路问题误判成渲染瓶颈；评论区给出了从 20ms/frame 降回可用帧率的实践路径，也提醒 Invoker 只是把全局重建改成局部生成，会引入内存、半径覆盖和远处敌人寻路等新权衡。对任何有大规模 NPC、玩家改造地形或运行时障碍物的项目，这都是应尽早压测的系统。

**高赞评论：**
- u/BronzeProjection（赞数：隐藏）：在大地形项目中踩坑，动态 NavMesh 每帧吃掉约 20ms；改成 Dynamic Modifiers Only，并只给真正移动的对象放 Nav Modifier Volumes 后恢复到 60fps。立场说明：这是最直接的工程经验，强调“只更新变化区域”而不是全局重建。
- u/DemonicArthas（赞数：隐藏）：建议使用 Navigation Invokers，让导航网格只围绕带 invoker component 的 actor 在指定半径内生成。立场说明：适合大地图和局部活动区域，但需要配合半径与生成范围设计。
- u/warpstudio（赞数：隐藏）：其项目在 8x8km 地图、600 AI、130 玩家下仍使用动态 NavMesh；关键是 Invokers、tile limits、radius limits 和 concurrency，不能指望每帧构建全图。立场说明：补充了规模化场景下的参数治理思路，避免把“动态 NavMesh”简单等同于不可用。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1v7rwsa/

## 2. So how are you supposed to disable AI?

**摘要：** 这帖从 State Trees/Behavior Trees 的停止逻辑切入，讨论 UE AI 死亡、停机或失活时到底应该关什么。核心结论是不要只调用一个 Stop Logic 就假设 AI 已停止，而要检查目标 AIController、BrainComponent、StateTree 引用、Pawn 是否正确，以及是否还有 Tick、Gameplay Ability、移动组件或其他代码把逻辑重新拉起。值得关注的是，评论把“停止 AI”拆成状态切换、调试打印、清理 movement/collision/focus/brain 的系统流程，对用 UE5 StateTree 或传统 BT 的项目都很实用。它也提醒团队把死亡、眩晕、暂停等做成统一状态，而不是在蓝图里分散关闭节点。

**高赞评论：**
- u/h20xyg3n（赞数：隐藏）：在 Behavior Tree 场景下，会切换到一个空白 Behavior Tree 来阻止 AI 继续行动。立场说明：这是简单但可控的降级方案，适合快速隔离“AI 是否仍在执行行为树”。
- u/MiniGui98（赞数：隐藏）：提醒确认引用/目标是否是正确的 StateTree，并检查是否有错误或其他代码立即重新激活树。立场说明：把问题从 API 调用转向对象引用与生命周期排查，避免误判 Stop Logic 失效。
- u/lewis-go（赞数：隐藏）：建议把死亡当作状态变化：先设 IsDead，再停止移动、清 focus、停止 Controller 的 BrainComponent/Behavior Tree，并按需禁用 Character Movement 与碰撞。立场说明：这是最完整的工程化处理，把 AI 停止纳入角色状态机而不是单点补丁。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1v8x9h0/

## 3. What's a good solution to fix floating legs off edges in Unreal Engine?

**摘要：** 这帖围绕角色脚部/胶囊体在平台边缘“悬空”展开，问题看似动画细节，实际牵涉 Character Movement、碰撞胶囊、边缘检测和玩法容忍度。核心建议是先定义行为：角色能否小心站在边缘、是否应滑落、视觉准确和物理准确哪个优先；再用 trace 检测 capsule center 或脚部是否越界，必要时让角色滑下。它值得关注，因为 UE 角色移动常把“脚贴地”问题混在动画 IK、碰撞和 CMC 参数里，评论还提到 UE4 的 Perch Radius，可作为 UE5 项目排查边缘站立行为的线索。

**高赞评论：**
- u/Aqua_Dragoon（赞数：隐藏）：认为方案取决于目标行为：是否允许走下边缘、是否有“黏性”边缘、视觉准确还是模拟准确优先；初步做法是用简单 trace 判断胶囊中心/角色脚是否越过边缘，越界则滑落。立场说明：先定设计语义再做技术实现，是最可靠的排查顺序。
- u/EliasWick（赞数：隐藏）：承认不同游戏会按需求处理，倾向在过界时让角色滑下，并追问是否应基于 trace 条件推动角色。立场说明：把讨论具体化到“检测后施加位移/滑落”的实现层面。
- u/honya15（赞数：隐藏）：提到 UE4 的 Character Movement Component 中有 Perch Radius，原本就是处理边缘站立/滑落行为的选项，UE5 中也值得检查。立场说明：提供了可直接搜索的引擎参数入口，适合快速验证是否已有内建解法。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1v8z984/
