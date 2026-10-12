
# r/UnrealEngine 今日热帖（2026-10-13）

说明：Reddit 直连与公共 redlib 实例仍被网络层封锁（全端点 000），本轮数据取自 arctic-shift 归档通道。文中赞数为入库快照（多数帖与评论为 1，个别出现 2/3/4 的小梯度），不代表当前真实票数，仅供排序参考；原帖链接可直接打开。

---

## 1. Has anyone tried P4 One? Seems like a free version of perforce geared at artists?

**摘要：** 楼主自建的小型 Perforce 服务难维护，p4ignore 与离线文件冲突频发，于是打听面向美术的 P4 One，并提到 Lore 等替代方案。社区给出的关键结论是：P4 One 只是更友好的客户端，背后仍要跑 P4 服务器，解决不了服务端与权限维护的痛点，甚至可能更麻烦。多位开发者转而推荐 Diversion（简单、迭代快、功能追赶快），但也有人对 Diversion 团队的隐私与自研 IP 风险提出警告。另有回复指出 Lore 本地部署容易、性能明显快于 P4，Epic 官方提供本机部署文档，唯一缺点是每两周更新、维护节奏得跟着走；也有人用 TrueNAS 上的 Gitea+LFS 满足同类需求。对任何要长期协作的 UE 团队，版本控制是地基级决策，这串讨论把 P4、Diversion、Lore、Gitea+LFS 的现实代价（p4ignore 折腾、隐私顾虑、维护频率）摊开讲清楚了。

**高赞评论：**

- u/philsiu02（赞数 1·归档快照）：P4 One 是面向美术的客户端，但你还是得有一台 P4 服务器；如果你现在就被 P4 折磨，它帮不上忙，可能还更糟。我搭过并管过几台 P4，其实很稳、几乎不用维护，不如先把官方文档读一遍确认配置没错。立场说明：把「换客户端」和「换服务端」分开——P4 One 治不了服务端维护痛，先排查配置本身。
- u/matniedoba（赞数 1·归档快照）：既然提到 Lore：本地环境很好搭，AWS 上稍麻烦；性能上 Lore 比 P4 快很多。目前唯一的问题是双周一次更新，维护节奏得跟着走。立场说明：给出一条可评估的替代路径（性能更好、部署有官方文档），同时点明维护频率这一代价。
- u/PolygonMob（赞数 1·归档快照）：我对 Diversion 团队有一些严重的红旗和隐私顾虑，真心建议看重自己 IP 的人别用它。立场说明：在「Diversion 简单好用」的推荐之外补上隐私与知识产权风险，提醒团队别只看易用性。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1x3wuta/

---

## 2. Why do my editor and debug mode have such a vastly different lighting situation?

**摘要：** 楼主在编辑器里看到的光照很满意，但一进入 PIE（他口中的 debug 模式）画面就整体变亮，且光从墙体交接处漏进房间，而编辑器里房间外是纯黑。社区的诊断分两层：一是那个眼睛图标只隐藏了编辑器视口里的灯光，PIE 会重建整个场景，所以隐藏失效——这是新手最容易踩的坑；二是漏光几乎总是几何体太薄导致，墙体低于约 10cm 或只是单面片时 Lumen 处理不好。可操作的修法包括把墙换成有厚度的 Box 而不是平面、在墙角让墙块互相重叠几厘米、提高墙网格的 Distance Field Resolution Scale、并在墙材质上勾选 Shadow Two Sided。至于整体变亮，多半是自动曝光在适应暗环境，用 Post Process Volume 锁住曝光即可。对做室内与建筑可视化的团队，这套编辑器与运行时光照差异、以及 Lumen 薄几何体极限的排查路径很值得存档。

**高赞评论：**

- u/Negative_Strain_5234（赞数 1·归档快照）：如果是漏光，你的墙可能太薄（不到 10cm）。Lumen 对付小而薄的几何体并不好。不想改墙网格、又不需要看到房间外面的话，可以在房间外侧放几个方块把光挡回去。立场说明：先给出「薄墙 + Lumen」这一根因判断，并提供不改模型的权宜解。
- u/GoodXPGames（赞数 1·归档快照）：除了加厚墙体，在拐角处让墙块互相重叠几厘米而不是只挨着，Lumen 在接缝处漏得厉害。也可以提高墙网格的 Distance Field Resolution Scale，让薄的部分被采到。如果之后房间莫名变亮，那是自动曝光在适应黑暗，用 Post Process Volume 锁住。立场说明：把接缝重叠、距离场分辨率、曝光锁定三个具体旋钮一次讲全，可照做。
- u/Spiritual-Movie-5450（赞数 1·归档快照）：眼睛图标是个经典陷阱——它只在编辑器视口里隐藏灯光，PIE 会重建整个场景所以又回来了。至于漏光，几乎总是薄几何体：单面片的墙光直接穿过去，给墙真正的厚度（实体 Box 而不是平面），并在墙材质上勾 Shadow Two Sided。立场说明：解释「编辑器里有效、运行后失效」的机制，并给出材质侧的修法。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1x3oz06/

---

## 3. Issues with Landscape Materials

**摘要：** 楼主搞不定 Landscape 的 Layer Info 排序，Painter 里图层只剩黑球，自己新建又变成棋盘格，跟着三份教程都走不通；同时困惑于很多地表贴图只有 albedo 和 normal，缺第三张。回复给出的路径很一致：在景观材质里用 Landscape Layer Blend 节点，图层名必须与 Layer Info 完全同名；然后在 Landscape 模式的 Paint 面板点加号新建 Layer Info，选 Weight-Blended Layer (normal) 会自动创建。黑球只代表还没分配 Layer Info，棋盘格通常是材质或图层配置不对，而不是贴图缺失。只有 albedo 的贴图需要把 RGB 通道分别拆出来接到输出，或把 AO、Roughness、Metallic 打包进通道；实在不行就换一张通道齐全的贴图。三条回答互相补位，基本覆盖了新手在景观图层上卡住的常见形态。

**高赞评论：**

- u/Engage69（赞数 1·归档快照）：你要找的是 Landscape Layer Blend 节点，把材质接进去。至于只有 albedo 的贴图，是因为你需要把 R G B 分别拆到各自输出；如果那样也不行，就换一张贴图或查清楚它们该接到哪里。立场说明：点出节点名和通道拆分这两个最常见的卡点，直接可执行。
- u/DanielFost（赞数 1·归档快照）：黑球和棋盘格通常说明 Layer Info 或材质设置不对，而不是贴图缺失。确认景观材质里的图层名正确，然后在 Landscape Paint 面板为每层创建 weight-blended 或 non-weight-blended 的 Layer Info，名字要和材质里的图层一致。立场说明：纠正「以为是贴图缺失」的误判，指向命名一致这个真正原因。
- u/Spiritual-Movie-5450（赞数 1·归档快照）：黑球只表示还没分配 Landscape Layer Info。真正能用的流程是：在景观材质里用 Landscape Layer Blend，图层名拼写完全一致，然后进 Landscape 模式、Paint 面板点加号创建 layer info，选 Weight-Blended Layer (normal) 会自动建好。立场说明：给出完整的、可复现的建层流程，与另外两条互补。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1x3k40m/

---

## 4. I got tired of constantly switching to File Explorer for reference files and docs, so I built a plugin that displays them directly in the Content Browser. Now live on Fab!

**摘要：** 开发者把自己做的 Project File Browser 插件上架 Fab：它让 .png、.jpg、.svg、.json、.txt、.md 等原始文件直接出现在 Content Browser 的目录层级里，带实时缩略图和磁盘刷新，省去反复切到文件管理器看参考图与设计文档的麻烦。评论区的分歧很有价值：有人建议增加指向项目目录之外文件夹的选项，别把项目塞满非资产文件，作者回应可在 Content 下建一个 RawFiles 目录；也有开发者直接批评这个思路会把资产浏览器搞乱，推荐用免费的 PureRef 看图；还有人表示这正是自己每天 alt-tab 的痛点。对 UE 团队来说，参考图与设计文档在资产浏览器里不可见是真实的日常摩擦，这串讨论把「污染 Content 目录」与「外部工具分工」两种取舍摆了出来。

**高赞评论：**

- u/Rossilaz（赞数 3·归档快照）：有意思。如果能加一个指向项目目录之外文件夹的选项会更好，这样项目就不会被非项目文件塞满。立场说明：指出插件最大副作用（Content 目录被非资产文件污染），并给出可行改法。
- u/OfficialDuelist（赞数 4·归档快照）：这看起来会很乱。你要把参考图淹进资产浏览器？直接用 PureRef 就行了，免费的。立场说明：代表「不要污染资产浏览器、外部工具分工」的一派，提醒团队评估工作流代价。
- u/USURPATIO（赞数 0·归档快照）：这真是救命。不停 alt-tab 去另一块屏看参考图，是我目前最烦的事。很妙的想法，我去 Fab 上看看。立场说明：在反方观点之外提供真实刚需反馈，说明「在资产浏览器里看参考」确实有用户。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1x1x0yg/

---

## 5. Bet you can build an entire city, with 100% enterable buildings before GTA VI!?

**摘要：** 作者在 CitySamplePCG 演示里挖到一个几乎没文档的调试用特性，并据此搭了一套 PCG 城市生成系统：用可随意编辑的主干道（红）与支路（绿）样条，配合基于网格的切分，几秒钟生成带道路、人行道和广场的整座城市网格。评论区一半是技术、一半是争论：有人直言本来想喜欢，直到它变成了一条 Claude AI 广告，因为作者随方案分享了 Blender 文件和喂给 AI 的记忆文件与提示词；也有人质疑 AI 生成资产的来源，作者反驳说 AI 只负责重活、你仍得知道自己在要什么，并回应了关于路口怎么做的技术提问——主要靠 polygon2d 运算和样条偏移，自己做了少量自定义节点。这条同时提供了少见的 UE 城市生成技巧，和一份 UE 社区对 AI 进入资产管线的真实态度切片。

**高赞评论：**

- u/ConsistentAd3434（赞数 3·归档快照）：我本来很想喜欢它，直到它变成了一条 Claude AI 广告。我希望大家去做自己的资产，或者付钱给美术。给 AI 公司付钱，等于在为训练数据里被偷的资产买单。立场说明：代表社区对「AI 生成资产＋作者顺势推 AI 工具」最集中的反弹，是这条帖争论的核心。
- u/slystudio（赞数 1·归档快照）：这类东西的问题是，AI 得把 GTA 剩下的部分也建出来。我是说，你得到一个城市之后呢？如果自己不会做，其实也做不了太多。立场说明：从「工具能生成、但项目不能靠它完成」的角度泼冷水，指出能力依赖性。
- u/Agile_Pressure_7430（赞数 2·归档快照）：你是怎么做出那些漂亮的道路交叉口的？立场说明：技术侧的高价值提问，作者答「主要是 polygon2d 运算和样条偏移，少量自定义节点」，把城市生成的关键做法带出来。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1wxadqc/

---

## 6. Cross Engine: Blender ↔ Unreal Bridge

**摘要：** 这是一个跨引擎资产桥工具，把 Blender 里的资产直接送进 Unreal，定位在「可用的游戏资产」上。评论里的实用信息比展示本身更值得看：有人问能不能在 Blender 侧排除特定内容不参与传输；有人提醒演示里 FPS 偏低、场景相对真实游戏关卡太轻，并指出 Maya 的桥接也有同样现象，所以更适合单个资产而非整关；还有人建议补上针对身体的 LiveLink 同步，因为动画师觉得那样更顺手，并提到已有 Maya 版本可以参照。对在 Blender 与 UE 之间来回倒资产的团队，这串讨论把三个关键前提摆了出来：排除粒度、性能与场景规模、以及动画是否走 LiveLink 而不是静态导出。

**高赞评论：**

- u/vexargames（赞数 1·归档快照）：看起来 FPS 挺低——如果目标是做游戏资产，这更适合单个资产。那个场景和真实游戏关卡比太轻了。Maya 的桥接也有同样现象。立场说明：指出适用边界（单资产而非整关）与跨引擎桥接的共性性能问题。
- u/korhart（赞数 1·归档快照）：看起来不错，有没有简单的办法把 Blender 里特定内容排除、不参与传输？立场说明：问出团队落地时最实际的「排除粒度」需求。
- u/Hawaiian_spawn（赞数 1·归档快照）：不错，别忘了给身体加 LiveLink 同步，动画师用起来更顺手。我这边有个 Maya 版本可以参考。立场说明：补充动画工作流建议——动画走 LiveLink 而不是静态导出。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1wvu05w/

---

## 7. Any good ue5 courses that are c++ coding based without blueprint

**摘要：** 楼主想找完全以 C++ 为主、不依赖蓝图的 UE5 课程。高赞回答给出的是被反复验证的清单：Stephen Ulibarri 与 Tom Looman 这对经典组合；其中有人补充 Tom 最近把课程从 OOP 重构为更偏 DOD（数据导向设计）的结构，值得重看；也有人指出真正做纯 UE C++ 教程的只有 Tom Looman 和 Vince Petrelli，其余多数课程仍要靠蓝图兜底，并给了获取渠道（官网与 Udemy）。另有一条提醒很实在：即便写 C++，你还是需要少量蓝图来做「胶水」逻辑。对准备从蓝图转向 C++ 的开发者，这不只是资源清单，也透露出社区对架构取向（DOD 而非纯 OOP）正在变化的判断。

**高赞评论：**

- u/Justaniceman（赞数 9·归档快照）：经典组合：Stephen Ulibarri 和 Tom Looman。立场说明：最高赞回答，给出社区公认的两个人选，是本帖最直接的结论。
- u/VR_Robotica（赞数 6·归档快照）：而且 Tom 刚把课程更新成更偏 DOD 结构、而不是 OOP，很高兴看到它在演进。立场说明：补充课程取向变化，对关心架构的开发者是关键信息。
- u/Blissextus（赞数 3·归档快照）：就我所知，真正做 UE C++ 教程的只有 Tom Looman 和 Vince Petrelli。其他人也出 C++ 课程，但大多仍要依赖蓝图。Tom 的在官网，Vince 的 Udemy 上找。立场说明：把纯 C++ 课程的稀缺性与获取渠道讲清楚，可直接照单去找。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1wwa2f2/
