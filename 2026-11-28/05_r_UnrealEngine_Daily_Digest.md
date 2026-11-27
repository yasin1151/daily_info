
**抓取状态**：Reddit 三个端点和 redlib 公共实例全部返回 `http=000`，本机 IP 段仍被 TCP 层封锁；GitHub API 返回 200，说明网络本身正常。按技能文档中的降级流程改用 arctic-shift 归档通道：9 个时间窗口全部返回 200，去重后得到 393 个候选，并逐帖拉取评论树，筛选出信息量充足的帖子，共 66 个候选。`blogwatcher scan` 照例因 `i/o timeout` 失败，`read-all --yes` 返回无可标记内容，可以接受。

---

# r/UnrealEngine 今日热帖

赞数说明：本轮 Reddit 正文与评论经归档通道读取，score 多为归档快照值（新帖普遍显示为 1），不代表真实热度排序；评论区按 best 顺序取信息量最高的三条。

---

## 1. Noisy shadow trail despite disabling almost everything

**摘要：** 楼主放出视频：近景里阴影拖着尾巴、还有噪点，他已经把 Lumen、TAA、虚拟阴影贴图、光追反射全部关掉，伪影依然在，而网上能搜到的答案全都指向这几个已经排除的开关。评论区把方向定到环境光遮蔽这一系：Distance Field AO、GTAO、SSAO 都会在物体或镜头移动时留下滞后痕迹，所以"关掉 Lumen 没用"是正常现象。可核对的检查点是天空光的阴影投射、方向光阴影配置、后处理体积是否把 AO 设置覆盖掉，以及是否开启了 MegaLights。值得关注的原因在于排查顺序：这类"明明关了却还在"的伪影，先走 AO 分支能省掉一整轮开关试验，也解释了为什么默认把锅甩给 TAA 会白忙。

**高赞评论：**

- u/slydex44（赞数 1·归档快照）："Distance Field AO can cause this. Untick the shadow casting in your skylight, that should help." 立场说明：给出高频根因加一步可验证的开关，关掉 SkyLight 的阴影投射就能确认是不是 DFAO 在留残影，是本帖最具操作性的建议。
- u/iku_19（赞数 1·归档快照）："Most of the trailing issues are not TAA but GTAO, try tweaking ambient occlusion settings." 立场说明：纠正社区习惯性归因，指出拖尾来自 AO 的时间性滤波而非 TAA，直接解释了楼主关掉 TAA 仍然无效。
- u/monnotorium（赞数 1·归档快照）："Check how shadows are configured in the directional light and do you have screen space AO turned on in a post-processing volume, actually, do you have a post-processing volume just overwriting your settings? Is the light static? Is megalights on?" 立场说明：把单点猜测扩成排查清单——后处理体积覆盖、光源是否 static、有没有开 MegaLights，适合照单核对而不是逐个试开关。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1y6qlsg/

---

## 2. Why your Epic Games Store build might secretly be trying to open Steam

**摘要：** 双平台发行的经典坑：按教程把 DefaultPlatformService=Steam 写进 DefaultEngine.ini，打包上传 Epic 商店后，游戏启动仍去初始化 Steamworks，找不到 Steam 客户端就静默失败或弹出 Steam 登录框，Epic 认证会直接判失败。作者的方案是单包自适应而不用打两套包：在 OnlineSubsystem 初始化之前读命令行，检测 Epic 启动器带的隐藏标志 -EpicPortal，命中就在内存里把平台服务切成 EOS 并接 Epic Account Services，未命中则让 Steam 接管；Build.cs 里对 Steamworks 做延迟加载，避免 Epic 玩家机器上加载到 Steam DLL；成就节点统一封装一层，玩法代码里不再写平台分支。评论区集中拆这套方案的地基，值得看的也是这部分。注意正文末尾带 Fab 插件推广。

**高赞评论：**

- u/jhartikainen（赞数 1·归档快照）："Do you think it's actually a good idea to rely on the command line flag to detect this? Is it guaranteed that in the future, Epic Store will keep passing the flag in? Feels like packaging twice is going to give a more reliable result." 立场说明：质疑方案的隐式契约——依赖未文档化的 -EpicPortal 标志等于赌 Epic 内部实现不变，一旦改动整条链路失效。
- u/FreshProduce7473（赞数 1·归档快照）："you know you can launch the package with your own command instead of relying on theirs. that way if their changes your game doesnt break" 以及 "i have shipped a game to steam and egs and its one build"。立场说明：给出实战替代：上传 EGS 时用上传工具自定义 launch param，参数自己掌控，不必赌默认值；他自称已用单包发行过双平台。
- u/Dave-Face（赞数 1·归档快照）："As others have said, I wouldn't rely on this kind of solution, especially given Epic's recent vibe-coding - it's likely to change or break in future." 立场说明：从维护成本出发否决，宁可走保守路线甚至暂时不上 EGS，代表了对这类"聪明 hack"最典型的反对意见。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1y6vm15/

---

## 3. Everything New In Unreal Engine 5.9!

**摘要：** 一条汇总 UE 5.9 新特性的视频帖，评论区几乎没在聊新功能本身，而是集中吐槽 Epic 长期把功能挂在 beta 与 experimental 状态：水体插件到现在仍是 experimental，EQS 实验了将近十年，转成 Production Ready 时也几乎没改动什么；另一条高赞则断言动画工具与 Mover 2.0 级别的更新被故意留给 UE6，用来逼团队迁移。值得关注的是它反映了版本升级决策的真实用户情绪：新特性可以慢慢等，把未打磨的 beta 插件放进生产管线才是真正的风险，尤其对要跨版本维护项目的团队，这条讨论比特性清单更有参考价值。

**高赞评论：**

- u/DaDarkDragon（赞数 1·归档快照）："Water plugin is STILL experimental" 立场说明：一句话点出最刺眼的历史遗留，水体插件多年仍挂 experimental，实际使用等于自己承担兼容风险。
- u/oxygen_addiction（赞数 1·归档快照）："EQS was experimental for like 10 years and they didn't change anything when they switched it over to Production Ready..." 立场说明：用 EQS 的例子说明"转正"标签本身不可信，实验状态和实际稳定性已经脱钩，选型应看代码历史而不是标签。
- u/mxhunterzzz（赞数 1·归档快照）："No Mover 2.0 or improved animation tools for you UE5 plebs. They're gonna hoard it all to UE6 to force you to make a choice that you will have to live with, forever" 立场说明：把未完成的 beta 和 UE6 迁移策略连起来讲，是社区对 5.x 尾段版本最典型的负面预期。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1y5u8mi/

---

## 4. Reinstalling a version takes less disk space... (?)

**摘要：** 从 Preview 一路热修升上来的引擎会越吃越多磁盘，楼主实测 5.5.4 删掉重装能省将近 20GB，于是问两件事：为什么会这样，以及重装会不会伤到项目。评论区的解释是：下载下来的是"裸"引擎，真正打开后 Binary、Intermediate、Saved 与各插件的二进制才开始堆积，热修只覆盖 Epic 分发的文件，不会清理引擎自己生成的缓存；安装选项里的 debug symbols 与额外目标平台也占很大一块。结论是重装安全，项目只通过 .uproject 里的 EngineAssociation 指向版本，中间文件和 DDC 都在项目目录；但装进引擎的 Fab 与 Marketplace 插件需要重装，共享 DDC 与 Zen 缓存则可以随时删。对磁盘吃紧的团队，这是每月都能省下几十 GB 的低风险操作。

**高赞评论：**

- u/Beautiful_Vacation_7（赞数 1·归档快照）："The disc usage grows over time. You download "bare" unreal, once you open it, Binary, Intermediate and Saved folders are being populated. For each plugin used." 立场说明：点明膨胀来源是首次打开后为每个插件生成的二进制与中间目录，属于使用痕迹而不是安装包本身变大。
- u/GustavoTheFish（赞数 1·归档快照）："Safe to do, your projects don't care. A project only points at an engine version (EngineAssociation in the .uproject)" 立场说明：给出可执行判断：删引擎重装不影响项目，并提醒装进引擎的 Fab 插件要重装、共享 DDC 与 Zen 才是真正的大头，可以放心清。
- u/botman（赞数 1·归档快照）："Building things over time will use up space." 立场说明：最短的一句补充确认——空间是用出来的，所以主动删掉重装比等热修补清理更实际。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1y438cr/
