
# r/UnrealEngine 今日热帖 · 2026-11-23

今天 r/UnrealEngine 的讨论几乎被同一件事占满：Epic 确认 UE6 不再包含 Blueprint，Actor/Component 框架也要换成 Verse + Scene Graph。以下三条是从 669 个归档候选帖、80 个评论树里筛出的技术向讨论，跳过展示帖、招聘帖和 Fab 促销帖。所有赞数来自 Reddit 归档快照（新帖多为入库默认值 1），仅作参考，不代表真实高赞。

---

## 1. 到底有没有人真心期待 UE6？——51 条评论里的架构正反辩论

**摘要：** 楼主在 Epic 公布 UE6 路线后发问：Blueprint 要被 Verse 取代、Actor 框架要换成类似 Unity 的 Scene Graph，社区里到底有没有人真的期待这件事。他举了《光与影：33 号远征队》、Granny Escape Together 等几乎全 Blueprint 完成的项目，认为 Blueprint 已被证明够用，而 Verse 太新、AI 对它的掌握也不牢。评论区没有停留在情绪，而是转向架构层面：Blueprint 图无法 diff、简单数学就能塞满视口，长期维护成本高；Actor/Component 模型和 Blueprint 一起被视为 UE5 性能问题的根源，ECS 更适合大规模场景；UE 的 C++ 因为 UPROPERTY/UFUNCTION 宏而像另一门语言。反方则强调 Epic 已把 Fortnite/Meta 相关部分插件化拆开，不用 AI 可以不启用。对正在规划 2027 年后项目的团队，这是一次关于"继续押 UE5.8/5.9 还是提前吃 Verse/ECS 技术债"的公开权衡记录。

**高赞评论：**
- u/nvec（赞数 1·归档快照）："the graph for a fairly simple maths equation can easily fill the viewport, and it's horrible to handle with Git" 立场说明：这位用户从工程可维护性切入——Blueprint 不是"能不能做出来"的问题，而是代码评审、合并、diff 全部失效；他还指出 UE 的 C++ 带 UPROPERTY/UFUNCTION 宏，实际更像内存受管语言，所以"改用文本语言"并不等于回到标准 C++。
- u/HunterIV4（赞数 1·归档快照）："They would need to significantly alter how BPs function to work with Verse. The design of the language is different from C++ and so it's not just a matter of swapping out nodes to the Verse implementation." 立场说明：直接反驳楼主"Epic 说做过可视化 Verse 但失败了是借口"的猜测，指出 Verse 的语言设计与 C++ 不同，节点图不能一对一映射，所以可视化层需要重新设计而不是替换后端。
- u/BARDLER（赞数 1·归档快照）："Blueprints and the Actor/Component framework are the primary root for performance issues in UE5. I think their decision to remove them are correct so they can have a more performant base architecture." 立场说明：少见的"支持移除"技术判断，把 Blueprint 和 Actor 模型一起认定为 UE5 性能天花板；同时认为可视化脚本可以在 Verse 之上后补，这与 Epic 的官方说法一致。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1y2nb7n/

---

## 2. "以前大家不是最讨厌 Blueprint 吗？"——用户认知与工作流的翻转

**摘要：** 楼主提出一个尖锐的观察：几年前社区还在骂 Blueprint、转 C++、盼 AngelScript 和 Verse 早点来，如今 Epic 真要移除 Blueprint，同一批社区却集体反对。他自认当年"躲开 Blueprint"才是主流。评论区给出两类解释。第一类是社会性的：这是两拨不同的人，写 C++ 的人本来就不发声，网上只吐槽不表扬，算法还会加固各自立场。第二类更有价值，是对 Blueprint 能力边界的复盘：它适合状态机图、动画图、材质图这类数据流场景，不适合顺序式命令逻辑；它长期是 UE 里唯一"一等公民"，工具链都围着它建；真正缺的是在同一个引擎里自由混写图和代码，而不是二选一。也有人认为 Verse 对命令式逻辑是更正确的解，只是可视化入口被砍得太急。这条串适合用来判断：Blueprint 留下的能力空白，究竟该由文本语言、可视化数据流，还是 AI 生成来填。

**高赞评论：**
- u/ananbd（赞数 1·归档快照）："Blueprints are a bad solution to a difficult problem." 以及 "Visual interfaces are great for dataflow paradigms like shaders, but they don't work well for sequential, imperative programming." 立场说明：用数据流 vs 命令式的区分解释"为什么大家又爱又恨"，并认为 Verse 才是这类问题的正解；他的另一条评论还提到工作室里 AI 辅助已经在替代"美术找程序帮忙"的环节，这是本轮最直接的一线观察。
- u/LockYaw（赞数 1·归档快照）："it was very much the only first class citizen of Unreal, most of the tooling was built around being used with Blueprints primarily" 以及 "They're absolutely GREAT for things like State Machine Graphs, Animation Graphs, Shader Graphs" 立场说明：把抱怨定位到"工具链只服务 Blueprint"而不是 Blueprint 本身，同时明确它在图式数据流上的优势，属于少见的可执行结论——按场景选范式，而不是按阵营选。
- u/yamsyamsya（赞数 1·归档快照）："Blueprints are meant for prototyping, they are literally the blueprint to building C++ code off of them" 立场说明：一位主要写 C++ 的用户给出的中间立场：Blueprint 的定位是原型与结构草图，最终是否下沉到 C++ 取决于项目，不必互相否定；这跟"移除"的激进程度形成对照。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1y2st2t/

---

## 3. Blueprint 退场后的第一个"外流样本"：把节点图搬到 Godot 的插件

**摘要：** 一位长期使用 Unreal 的开发者，因为不满 Blueprint 被移除，做了一个 Godot 插件：把 Blueprint 风格的节点图实时转成 GDScript，也能把已有脚本反向转成节点，输出是不依赖插件的纯 GDScript，因此随时可以脱离工具继续维护。他在评论里补充了实现边界：节点到脚本是实时的，脚本到节点需要点一次"转换"，但支持批量；插件还带了一批调试工具，方便在引擎里来回切换。评论区追问最多的是三点——它与已有的可视化脚本方案（如 Orchestrator）差别在哪、手改脚本能否回写节点图、以及能否覆盖 shader 图。也有用户说，当年留在 UE 的真正原因正是"图与代码能在同一引擎里自由混写"，这条插件正好击中那个痛点。对团队来说，这是 Blueprint 退场后最具体的迁移成本信号：决定迁移难度的不是语言本身，而是"图↔文本"是否双向无损。

**高赞评论：**
- u/VertexMachine（赞数 1·归档快照）："Oh, that's even cooler. Having a mapping to/from gdscript is super useful!" 立场说明：他先拿已有的 Orchestrator 方案做横向比较，确认差异后才认可；真正看重的是双向映射——这恰好说明同类工具的评价标准已经从"能不能可视化"变成"能不能无损回到文本"。
- u/Riustuue（赞数 1·归档快照）："does it convert it into a script live as you place and connect nodes? And any manual script changes are propagated back to the node system?" 立场说明：问的是工程上最关键的同步语义——单向导出和双向同步是完全不同的维护模型；作者回答节点→脚本实时、脚本→节点需一次转换但可批量，这个限制决定了它能否进生产流程。
- u/StereoCatPicture（赞数 1·归档快照）："My main complaint about Blueprints in Unreal was that it didn't allow you to do some parts in code and some parts in Blueprints right in the engine." 立场说明：把痛点说得最清楚的一位：不是讨厌 Blueprint，而是讨厌"只能在图和代码之间二选一"；这类需求在 UE6 方案里仍未被正面回答，迁移讨论因此有了实际抓手。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1y2raqb/
