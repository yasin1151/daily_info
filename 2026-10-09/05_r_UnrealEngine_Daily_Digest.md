
# r/UnrealEngine 今日热帖（2026-10-09）

Reddit 直连与 redlib 公共实例本轮仍被 IP 层封锁（`www.reddit.com` / `old.reddit.com/r/UnrealEngine/hot/` / `redlib.perennialte.ch/r/unrealengine/hot/` 全部 http=000），按技能既定降级路径改走 arctic-shift 归档通道完成抓取。评论按 comments/tree 默认 best 顺序选取；赞数为归档快照，可能滞后，标 1 的多为入库默认值，不代表真实票数，未按分数排序。

## 1. How to use PCG to make rock walls.

原帖：https://www.reddit.com/r/UnrealEngine/comments/1x0711a/

**摘要：** 有人想用 PCG 自动搭出截图里那种岩石墙，好批量做关卡而不用手动一件件摆。评论区先泼了盆冷水：截图里的墙其实不像实例化网格，更像 landscape 上的 autocliff 表面着色器，用表面法线与噪声做点积来区分石头和泥土；真要在 PCG 里复刻，得靠 Geometry Script 去生成和操作动态网格，而 PCG 的多数几何功能需要通过蓝图函数暴露（引擎自带的 PCG Geometry Script Interop 示例里就有可参考的内容）。另有两条可落地的工程路线：沿 spline 生成点，按受控间距与随机旋转摆 3-4 种岩石模块以获得变化，再按高度或朝上法线筛点，单独生成泥土/草皮格；把顶层封盖放进独立 PCG 分支，材质与密度都更好控制。为什么值得关注：先分清"想要的观感"和"该用的工具"——很多看似 PCG 的效果其实是材质与 landscape 的活，能避免在错的工具链上白耗几天。

**高赞评论：**
- u/amathlog（赞数 1·归档快照）："It's not going to be very easy to have something very generic to create walls like that. It's a combination of mesh generation, mesh manipulation and placement of complex shapes." 并指出这部分"would fall into the Geometry Scripting part"，PCG 的几何能力大多要通过蓝图函数暴露。立场说明：把"通用造墙"这件事的真实复杂度讲清楚，并给出正确工具方向（Geometry Script 而非纯 PCG 节点）。
- u/demonsoswhite（赞数 1·归档快照）："Basically spawn meshes over a spline, randomize mesh placement (so have like 3-4 different variations at least)." 并建议对封闭网格旋转 180 度来增加变化，再采样这些网格在其顶部生成草。立场说明：给出一条能立刻上手的 spline+随机变体流水线，是典型"80% 靠 spline、剩下手工补"的务实做法。
- u/rhoward92（赞数 1·归档快照）："A practical setup is to generate points along a spline or wall volume, then use those points to spawn and orient the rock modules with controlled spacing and randomness." 并补充用高度或朝上法线筛点单独生成泥土/草皮、顶层封盖放独立分支。立场说明：把实现拆成"布点—定向—封顶"三段并强调分支配色，是最接近生产管线的答案。

---

## 2. Do you need a steam app id to test steam sessions with a friend vs local standalone?

原帖：https://www.reddit.com/r/UnrealEngine/comments/1x0yrdv/

**摘要：** 有人用 AI 快速搭了个 Steam 会话原型，本地两个 standalone 能互相找到会话，可打包发给朋友后日志却显示 sessions found:0，于是怀疑是不是必须花 100 美元买 AppID 才能和朋友联机。评论区澄清：480（Spacewar）就是免费测试专用 AppID，在 standalone PIE 和打包 dev build 里都能跑通 P2P 与会话匹配，是注册 Steamworks 之前的官方管线；但 5.8 与 5.2 行为有变化，现在必须显式设置 lobby/游戏名，让搜索只匹配自己的会话，否则会扫到 480 下所有游戏并在第一条结果上报错。也有人警告 480 用久了会莫名失效，付费买了自己的 AppID 后一切恢复正常——这类结论几乎查不到文档。为什么值得关注：联网测试的成本判断很容易被 AI"必须买 AppID"的说法带偏，这条给出了真实可行的低成本路线，以及两个很隐蔽的坑（显式 lobby 名、480 长期失效）。

**高赞评论：**
- u/Sinaz20（赞数 1·归档快照）："You use id 480, Spacewar for testing without a sku of your own." 并确认"I have definitely set up sessions and p2p matchmaking via steam in both Standalone PIE, and in packaged dev builds using ID 480." 立场说明：来自有大量实战经验者的直接背书，是判断"不必先付费"的关键证据。
- u/Skyroor（赞数 1·归档快照）："Make sure to set the actual game/lobby names so it searches for your game explicitly. Or else it will try to find any games/matches with appid 480 then error out on the first result." 并指出从 5.2 到 5.8 行为变了。立场说明：给出最容易踩的 5.8 新坑，解释了"本地能连、发包后找不到"的典型症状。
- u/Aakburns（赞数 1·归档快照）："You can use 480 but it will eventually stop working. True story."，并说"Once I paid for an AppID for Steam for the project, everything started working again." 立场说明：提醒 480 并非永久方案，为长期项目留出购买付费 AppID 的预算与预期。

---

## 3. Can't install UE on my Macbok Pro M5 with 500Gb free. Getting "There is not enough space at/" with the error code "SU-DS01".

原帖：https://www.reddit.com/r/UnrealEngine/comments/1wx3vnj/

**摘要：** 有人在 M5 MacBook Pro、500GB 可用空间的情况下装 UE，却被报 "There is not enough space at /"（错误码 SU-DS01），反复删 Cache、Application Support 等 Epic 目录也无解。评论区的判断是：这多半不是容量问题，而是 launcher 在抱怨安装路径或卷。新版 macOS 的 "/" 是只读密封系统卷，真实可用空间在独立的 Data 卷上，launcher 查错卷或用错临时路径时就会误报"空间不足"；建议换一个全新安装目录并确认它存在、位于 APFS 卷且当前用户可写，或把安装指向 home 目录下的文件夹，再用 df -h /System/Volumes/Data 核对真实剩余空间与写权限。有人用 AI 逐条排查后按其中一条成功解决；也有少数人怀疑是 SSD 损坏。为什么值得关注：macOS 上的这类"磁盘空间"报错往往指向路径与卷而非容量，认清机制能省下大量无意义的清理。

**高赞评论：**
- u/XSM909（赞数 3·归档快照）："that error is usually the launcher complaining about the install location, not the actual free space." 并建议在 launcher 里另选一个全新安装目录、确认它在 APFS 卷上且用户可写。立场说明：本楼最高赞，直接点破报错语义，给出的动作最小、最容易验证。
- u/redwolf1430（赞数 1·归档快照）："That message is almost always misleading on a Mac." 并解释现代 macOS 的"/"是只读密封系统卷、真实空间在分开的 Data 卷。立场说明：从卷结构层面解释 macOS 旧容量的错位，是理解这个跨平台陷阱的关键背景。
- u/Agitated_Maize_4796（赞数 0·归档快照）："often means the launcher is checking the wrong volume or temp path, not that the Data volume is full." 并建议先把安装指到 home 目录下的路径，再核对 Data 卷空间与写权限。立场说明：给出可复现的自查步骤，把"看起来是 Epic launcher 路径/权限 bug，而非 M5 硬件问题"这一判断落实。

---

## 4. Issues with a spritesheet sylized face controled by bone transform

原帖：https://www.reddit.com/r/UnrealEngine/comments/1wz2w7x/

**摘要：** 有人用 Blender 做了个靠骨骼变换驱动精灵图切换表情的脸部绑定，导进 UE 后发现在动画插值时会"顺路"经过中间所有精灵帧，而不是从第 2 张直接跳到第 6 张，于是问能不能只对特定骨骼关掉插值。评论给出两条可行路线：把脸部控制值当作离散索引，在动画里把这些骨骼的关键帧插值模式改成常量/阶跃（stepped），就能直接跳帧；如果最终选择发生在材质里，则把连续的骨骼值量化成整数精灵索引，观感更干净。有人证实阶跃关键帧是更省事、更彻底的做法，并分享自己在"嘴巴循环贴图"项目里用材质量化时遇到过一直调不掉的延迟感；也有人追问导入的动画能不能直接改成阶跃关键帧。为什么值得关注：把骨骼当索引用的精灵图表情是省算力的常见做法，插值语义一旦处理错就会全程穿帮。

**高赞评论：**
- u/DanielFost（赞数 1·归档快照）："you probably don't want to disable interpolation on the whole animation, just make the face-control values step instead of interpolate" 并给出"set the relevant keys to stepped/constant interpolation so it jumps from sprite 2 to sprite 6 instead of passing through 3, 4, and 5"，以及在材质里量化骨骼值的备选方案。立场说明：把问题精确归因到"离散数据不该被插值"，并同时给了动画层与材质层两条修法。
- u/Turbulent_Chance_722（赞数 1·归档快照）："stepped keys in the animation is def the cleaner route, just set the interpolation mode to constant on those specific face bones and boom, jumps straight from frame to frame no in-between nonsense" 并补充自己在材质量化方案上的延迟踩坑。立场说明：用亲身项目经验背书阶跃关键帧路线，并提示材质量化存在难以调掉的延迟副作用。
- u/TvHeadDev（赞数 1·归档快照）："Is it possible to set the keys to stepped on an imported animation?" 立场说明：把方案落到"导入动画能否直接改插值"这一实操边界上，是这条修法能否直接复用的关键追问。

---

## 5. Distance Fields in shaders don't seem to stay after use

原帖：https://www.reddit.com/r/UnrealEngine/comments/1wp5by1/

**摘要：** 有人做基于距离场的材质效果，编辑材质实例时一切正常，一旦停止编辑改动就不再显示，连最简单的"到最近距离→颜色渐变"节点也留不住；已排除距离场分辨率、bound scale、自相交、以及没开距离场等常见原因。评论区按排查顺序给出三个最可能的方向：一是该网格是否真的允许距离场（有人确认已禁用仍复现）；二是这个对象是不是蓝图、被 construction script 在拖动时重置了材质（楼主说明这是直接拖进场景的普通立方体、并非蓝图）；三是 PIE 里是否也一样（楼主确认一样，排除了编辑器与运行时不一致）。为什么值得关注：距离场材质"编辑可见、退出即失效"是经典陷阱，这三条正好覆盖网格距离场设置、construction 重置、运行时一致性三个层面，值得按序自查。

**高赞评论：**
- u/neuropope（赞数 2·归档快照）："Are you sure the construction script doesn't reset the material? By default construction runs on drag" 立场说明：指向最常见的一类"改了又弹回去"根因——construction script 在拖动时重跑并覆盖材质，排查时优先级很高。
- u/DaDarkDragon（赞数 2·归档快照）："are distance feilds disabled on the cube?" 立场说明：一句话点中距离场材质的前提条件（网格需允许距离场），是这类问题最廉价的第一个检查项。
- u/GenderJuicy（赞数 1·归档快照）："Is that the case in PIE as well?" 立场说明：用最小对照把问题在"编辑器 vs 运行时"之间定位，能快速排除是编辑器显示问题还是材质本身失效。

---

## 6. PS5 Gamepad Thumbstick Value Bug

原帖：https://www.reddit.com/r/UnrealEngine/comments/1x01u4f/

**摘要：** 有人用 PS5 手柄时摇杆即使把死区设到 1 仍会漂移，用 Get Key Analog 读到的正向值是 3.5、负向是 -1，而 Xbox 手柄是正常的 ±1。评论判断 3.5 这种越界值说明 DualSense 没走 XInput，被当成通用 raw HID 设备且轴映射不对：建议先关掉 Steam Input / DS4Windows 之类的半翻译层（把 Steam 完全退出）再测，检查 Windows RawInput 插件是否启用并重映射或归一化轴，或干脆让它以 XInput 手柄身份出现。另一条建议是先看原始输入值、确认两个手柄是否用同一套输入映射，并尝试把值归一化/钳制到期望区间来验证推断。楼主最终确认是 GameInput 与 Fabulous DualSense 两个插件同时启用产生冲突，关掉后者即解决。为什么值得关注：跨平台手柄的模拟量范围差异是隐性漂移的常见来源，答案往往在插件冲突而不在死区设置上。

**高赞评论：**
- u/loulo88（赞数 1·归档快照）："That 3.5 value usually means the DualSense isn't going through XInput, so Unreal is reading it as a generic raw HID device with the wrong axis mapping." 并建议让它以 XInput 手柄身份出现。立场说明：给出异常数值背后的机制（没走 XInput、轴映射错），比单纯调死区更接近根因。
- u/EthanMerce（赞数 1·归档快照）："sounds like the ps5 controller is reporting a different analog range rather than the stick actually drifting." 并建议"i'd normalize/clamp the value to the expected range as a test"。立场说明：用"量程差异而非真漂移"的假设解释现象，并给出可快速验证的归一化实验。
- u/shiny0suicune（赞数 1·归档快照·楼主）："Deactivating Fabulous DualSense got rid of the problem." 立场说明：楼主回填的最终解法——GameInput 与 Fabulous DualSense 插件冲突，直接给出可复现的修复动作。
