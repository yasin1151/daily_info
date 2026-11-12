
# r/UnrealEngine 今日热帖 · 2026-11-13

说明：直连 Reddit 受限，本篇取自归档快照；部分较新帖子的赞数仍是入库默认值（多为 1），已在每条评论后标注「归档快照」，请按内容而非分数判断。

---

## 1. Fluid Forge 上架 Fab：跟随玩家的实时水体模拟

**摘要：** 一个独立开发者花一年多做的实时水体模拟插件 Fluid Forge 1.0 上架 Fab，起点是市面主流水体插件买不起。核心是一套能在游戏里跑的水面模拟：默认在固定区域内计算倾倒与流动，另有「无限」模式——世界里的河流、湖泊、水坑、海面事先摆好，模拟区域跟随玩家移动，只对玩家附近的水做完整模拟，区域大小可配。室内场景可以排除网格、改用运行时虚拟纹理，或把模拟高度压到屋顶以下做积水；另有海洋模式做海岸拍岸，以及液金、黏液示例。项目需开启 Mesh Distance Fields 与 Niagara 的 Static Mesh DI。评论区关注的全是选型硬问题：和 Fluid Flux、Fluid Ninja 的差别在哪、有没有帧时间对比、能不能当物理体积驱动游泳。对要做水体但预算有限的团队，这条串等于一份免费的需求核对表。

**高赞评论：**
- u/Leonature26（赞数 1·归档快照）：「aside from the price diff, why should i choose this over other water solutions like fluid flux or fluid ninja?」还追问它是不是和 Fluid Flux 一样用 2D heightmap。立场说明：这是买之前最该问的问题，作者答得也实在——确实是高度场方案，但可以排除网格、改用 RVT，或把模拟高度压到屋顶以下处理室内水体。
- u/Vishwah_13（赞数 1·归档快照）：「This looks like implementation of this paper」，并贴出 NVIDIA 浅水模拟论文链接问是不是同一套。立场说明：社区在核对实现来源，作者回说主要基于 Matthias Müller 的论文、只是知道那一篇——对要评估技术债的人有用，至少知道它站在哪条研究线上。
- u/Candescence（赞数 1·归档快照）：「Can water bodies act as a physics volume, for the purposes of character swimming functionality?」立场说明：这条把渲染插件和玩法接上了，作者答复是加 FluidForge_Buoyancy 组件读取水面高度来驱动游泳状态，等于公开了接入点，不必自己从渲染结果里反推高度。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1xtkm7d/

---

## 2. 移动与战斗动画怎么无缝衔接：一份被评论区补全的架构清单

**摘要：** 帖主想做蝙蝠侠 freeflow 那种连招：移动用 GASP，攻击用 montage 编排，但两套动画来自不同资源包，本身不是为彼此设计的，于是卡在怎么接才不突兀。他抛出的问题其实是一份动画架构清单：不同来源的动画怎么过渡、用 Motion Matching 这类自动系统后还剩多少手工调优空间、战斗逻辑怎么和移动解耦、多少能靠混合与姿态匹配解决、多少取决于源动画质量。两条高赞回答给了完整路径：先照 Dynamic Additive Overlay 的思路在 GASP 上层叠加内容；更彻底的是把 GASP 重做一遍，弄清 overlays、additives、curves、linked locomotion layers、gaits 与状态枚举如何组合，先把一把武器的一个状态调到 idle、pivot、cycle 都能无缝切换，再横向扩展武器数量。这类层叠式结构也是多数商业项目处理上下半身分离的通用做法。

**高赞评论：**
- u/analogexplosions（赞数 10）：推荐 Dynamic Additive Overlay 项目，说里面有「some good examples of how to layer on top of GASP’s motion matching setup」。立场说明：最高赞没有空谈，直接指了一个可读的参考实现，等于说明业界做法是分层叠加而不是整套替换，适合当起点文档看。
- u/fullylaced22（赞数 8）：「I would strongly advise REMAKING GASP, as opposed to just using it outright」，并列出 overlays、additives、curves、linked locomotion layers 与 gaits、state enums 是关键，还提到 Inertialization 与 Animation Modifiers 写曲线、Anim Notify 控命中时机。立场说明：全场最完整的一条，把「怎么调」拆到混合类型、过渡规则、骨骼分支过滤的层级，并提醒先做单武器单状态验证再铺开。
- u/TinikTV（赞数 1）：「Build your own locomotion and AnimBP from zero, I always do so. Usually we make lower body independent from upper one in terms of animation in industry」，需要脚部精确落位时再上 root motion 或伪 root motion。立场说明：给出了行业常规的上下半身分离约定，和上面两条不冲突，是更偏工程洁癖的一条路。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1xnrh9a/

---

## 3. 距离场软件 GI 插件上架：技术路线清楚，定价被质疑

**摘要：** 这是一个基于 Unreal 全局距离场的软件全局光照插件：用 DDGI 式探针体积加 surfel 辐亮度缓存，可选逐像素 final gather，不依赖硬件光追就能做动态间接光，探针密度可配，支持动态与烘焙两种模式、自发光表面产生间接光，蓝图与 C++ 都能运行时控制，并放出与 Lumen Lite 的对比视频。并入整套工具后还包括增强版 SMAA、RCAS 锐化、屏幕空间阴影与着色器预编译。评论区的反应值得一看：有人直接说这是把 GDC 演讲里的实现拼凑后转卖；也有人态度转变，认为作者确实懂图形、也肯答疑，但整套定价偏高，指出有订阅的人可以自己复现；还有人对展示场景的可信度提出质疑。对没法上硬件光追、又嫌 Lumen 成本高的项目，这条串能同时看到方案边界和社区口碑。

**高赞评论：**
- u/horizikaul（赞数 1·归档快照）：「he has a good understanding of the plugins hes putting out, and of graphics in general」，但认为定价过高，原话是「anyone with a $200 sub can reproduce that whole suite」。立场说明：从黑转中立的长评，把争议从抄不抄转到值不值这个价，这正是买插件前该算的账。
- u/ShrikeGFX（赞数 1·归档快照）：「This showcase is very unrepresentative, do you have no better testing?」立场说明：GI 这类效果最怕 demo 场景选得偏，一句质疑就说明单看宣传片不成立；作者回说有可下载 demo，含丛林、室内多光源精神病院和室外区域，还带与 Lumen Lite 对比的开发者菜单。
- u/oxygen_addiction（赞数 0·归档快照）：「This is that guy that takes GDC talks and slops shitty implementations together and then resells them.」立场说明：0 分但代表社区对把论文和 GDC 实现打包出售的敌意，读的时候要配上面那条平衡，别把它当技术评测。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1xrppna/

---

## 4. 「UE6 没有 C++ 也没有蓝图」的截图帖，评论区把范围说清楚了

**摘要：** 一张「UE6 没有 C++、也没有蓝图」的截图把社区点着了，但真正有价值的是评论里的辨析：官方要动的是 C++ gameplay library 这一层，也就是引擎代码的一个子集，而不是把 C++ 整个从 UE6 里拿掉。这条纠正拿到 11 赞，比情绪化标题更接近事实。另一条高赞认为砍掉蓝图会是极其错误的决定，因为蓝图在原型阶段的迭代速度没有替代品；也有人对让 AI 写游戏的方向表达疲惫，觉得最后留下的是没人愿意维护的成品。对团队来说，这条串值得看的原因不是传闻本身，而是它暴露了 UE6 迁移时的真实担忧：现有蓝图工程、C++ gameplay 层的存量代码、以及原型工作流会被怎么影响。任何「某版本要砍掉 X」的消息，都该先落到具体模块名上再判断影响面。

**高赞评论：**
- u/NewInflation2121（赞数 11）：「They aren't deprecating c++... They are deprecating the c++ gameplay library, which is a subset of the engine code.」立场说明：全帖最有用的一条事实纠正，把恐慌收敛到具体范围，也解释了为什么引擎层 C++ 不受影响。
- u/-LaughingMan-0D（赞数 7）：「Killing blueprint will turn out to be a horribly misguided idea」立场说明：代表大量蓝图工作者的判断，原型迭代成本是蓝图最难被替代的部分，这条情绪背后是实打实的迁移风险。
- u/Pileisto（赞数 6）：「No more developers either. Let them have AI make the games itself and also play that slop then.」立场说明：说法带情绪，但反映一部分人对引擎方押注 AI 的不信任，做技术选型时该知道社区情绪已经分化到这一步。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1xnxzkc/

---

## 5. 六个状态的状态机就乱成一团，三条回答对应三个层次

**摘要：** 一个只有 6 个状态的动画状态机，transition 连线已经多到看不清，作者问有没有整理办法。三条回答分别对应三个层次：把逻辑收进 function 或 component，用统一接口把乱线关在一个地方；如果确实是动画状态机，先看 conduit，用共享的过渡条件替代每条状态之间的重复连线；如果项目还早，换 StateTree 配 UAF，回答者认为它会在 UE6 转出实验状态。这类问题看着基础，但状态机的可维护性直接决定后期加状态、加武器的成本——状态一多，连线复杂度接近平方级增长，早点分层比后期重构便宜得多。评论区没有长篇大论，三条都给了可立刻动手的改法，适合正在被 transition 淹没的项目直接照做。

**高赞评论：**
- u/two_three_five_eigth（赞数 1·归档快照）：「Make them a function or component so all the mess is in one place with a standard interface」立场说明：最工程化的解法，用一层封装牺牲一点直观性，换来调用方不被内部连线污染，长期最省心。
- u/Informal_Cookie_132（赞数 1·归档快照）：「look into conduits」立场说明：动画状态机专属优化，conduit 把共享过渡条件收成一处，能一口气砍掉大量重复连线，是成本最低的即时改进。
- u/JournalistMiddle527（赞数 1·归档快照）：「switch to UAF and use state tree instead, it's way easier, I think they'll move it out of experimental in ue6」立场说明：给的是迁移建议，越早换成本越低；但要接受 StateTree 与 UAF 仍在演进，适合新项目而非半途重写。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1xumxhn/

---

## 6. 做影视化镜头很慢：问题多半不在教程，而在分镜和后处理默认值

**摘要：** 作者在做影视化镜头，坦白自己很慢，怀疑那些「两小时做出整个场景」的课程是不是骗钱，想知道有没有偏电影感而非游戏开发的免费教程。回答先反问卡点在哪：概念还是界面。接着给出一条常被忽略的路径：Unreal 的默认后处理是有主见的，颜色分级和一堆默认选项会把人带偏，先把自动曝光关掉，用黑白灰立方体摆一摆把灯光校准；镜头语言方面，先把分镜定下来，只做摄影机真正看得到的东西，森林地面这种入不了画的部分不要花时间。还有人给了时间参照：一开始十秒镜头要三小时，靠练才降下来，建议先用一两分钟的小项目带着学。这条串对刚进 Sequencer 的人比大多数付费课更省时间。

**高赞评论：**
- u/HongPong（赞数 1·归档快照）：「it is better to disable auto exposure and use little stacks of black white gray cubes to work out the lights」立场说明：把画面平归因到默认后处理与自动曝光，这是很多人第一步就该改的设置，比换素材更能立刻看到差别。
- u/Dopafiending（赞数 1·归档快照）：「you first of all need to work out your shots, from there you focus on what is actually going to be seen by the camera」，并说自己十秒镜头从三小时练到明显更快。立场说明：分镜先行、只做入画内容，是对堆场景路线最实用的反驳，也解释了为什么慢往往不是软件不熟。
- u/InfluencePlus2963（赞数 1·归档快照）：「Unreal sensei also updated his free intro to unreal, 5 hours of video.」立场说明：先给免费且系统的入门，再谈付费课，避免被「两小时成片」的广告带节奏；同帖还推荐了 Josh Toonen 的免费内容。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1xugqnv/

---

## 7. 贴图在 Z 轴被拉长：world aligned 救不了错误的 UV

**摘要：** 从 FBX 导入模型后贴图在 Z 方向被拉长，作者已经用 World Aligned 节点试图绕开，但侧面依旧拉伸，于是把视口和材质图都贴出来求助。三条回答指向不同层次：先检查静态网格的缩放是不是三轴一致，只要某个轴被单独拉过，贴图就会跟着变形，用 1,1,1 缩放测一遍就能排除；材质侧建议搭 Master Material，用 TexCoord 接 Append 再乘参数来控制平铺，让所有贴图通道走同一套 UV；最直接的一条反问是——既然要正确结果，为什么不干脆做对 UV，而要拿 world aligned 去补。这个帖的价值在于把「绕过 UV」和「修好 UV」的取舍摆清楚了：世界对齐适合地形、岩石这类无接缝表面，拿它去救一个本该有正确 UV 的硬表面模型，斜面与侧面一定会露馅。

**高赞评论：**
- u/korhart（赞数 1·归档快照）：「Why do you need to fix the stretching with a world aligned node? Just create correct uv maps.」立场说明：最短也最根本的一条，world aligned 是给无接缝表面用的，硬表面模型该回到 UV 本身，否则问题只是被推到别的视角。
- u/MarkLikesCatsNThings（赞数 1·归档快照）：「Make sure your static meshes scale is the same on X, Y and Z」立场说明：先在 1,1,1 缩放下复测，能快速区分是模型缩放问题还是 UV 问题，是最省时间的一步排查。
- u/Gojira_Wins（赞数 1·归档快照）：「plug that multiply into the UV slot of all the Texture Samples with your textures」立场说明：给的是可复用的 Master Material 结构，用参数统一控制平铺，顺手把贴图参数化的习惯建立起来，比逐个材质改更耐用。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1xqvvon/
