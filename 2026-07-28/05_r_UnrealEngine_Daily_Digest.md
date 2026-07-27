
## r/UnrealEngine 今日技术热帖

### 1. Verse is single threaded... so why is Epic deleting Blueprints again?

**摘要：** 这条讨论聚焦 UE6 路线图中 Verse 与 Blueprints 的关系：主帖质疑 Verse 目前仍偏单线程，为什么 Epic 还要推动替代蓝图。核心分歧不在“节点编辑器会不会消失”，而在 gameplay 脚本、Actor 体系、事务模型和未来 ECS/并发能力如何迁移。它值得关注，因为很多团队把 Blueprint 当作原型、设计师脚本和生产 glue code；如果 Verse 逐步接管，性能收益、学习成本、插件兼容、调试体验和现有项目维护都会受影响。对已有大量蓝图资产的项目来说，这也关系到长期升级路径、团队培训节奏和工具生态稳定性。

**高赞/高信号评论：**
- u/Nextil（62 赞）：As far as I know, Blueprints are also single-threaded, aside from some of the animation blueprint stuff. It really shouldn't matter for gameplay code. If need to do something really heavy it should be in C++. 立场说明：给出工程 workflow 或工具链角度的取舍，落地价值较高。
- u/dicygames（37 赞）：What I really don't get is that the blueprint-style interface is used across a lot of different tools within unreal. Blueprints, materials, metasounds, PCG, etc. all use very similar node-based systems that integrate extremely well with eachother. On… 立场说明：补充了渲染管线层面的判断，可帮助区分视觉问题与引擎限制。
- u/AlFlakky（28 赞）：Node editor != Blueprints. If they say they are gonna get rid of Blueprints, it does not mean they are gonna remove all node tools. So, materials, metasounds, and others, are basically node editors for data. While Blueprints is a scripting tool (incl… 立场说明：补充了渲染管线层面的判断，可帮助区分视觉问题与引擎限制。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1v6odft/verse_is_single_threaded_so_why_is_epic_deleting/

### 2. How do I secure my games against malicious custom content?

**摘要：** 这条帖子讨论 UE 游戏开放自定义内容/Mod 时的安全边界。发帖者想让玩家导入地图、Actor 等内容，但担心蓝图或未限制的引擎接口带来远程执行、文件访问或作弊风险。核心建议是把 Blueprint Mod 当作“代码”而非普通资源处理，尽量限制为数据和资产，白名单可调用 API，并用 DLC/content-only plugin 等机制隔离。它值得关注，因为 UGC 能提升生命周期，但一旦边界设计错误，安全、平台审核、存档污染和线上信任成本会迅速超过玩法收益。

**高赞/高信号评论：**
- u/randomperson189_（12 赞）：From my knowledge, Mecca Chameleon had exposed certain engine C++ functionality to Blueprint that wasn't sanitised, thus creating a RCE vulnerability, the best thing I can say is to do all your workshop code within native C++ and don't expose ANYTHIN… 立场说明：给出工程 workflow 或工具链角度的取舍，落地价值较高。
- u/ImportantDetail6260（5 赞）：Treat Blueprint mods as code, not content! For the portfolio version, make the boundary boring: load data/assets only, whitelist callable functions, no console/CVar/process/file/network wrappers, and test with a fake malicious mod. Singleplayer doesn… 立场说明：给出工程 workflow 或工具链角度的取舍，落地价值较高。
- u/randomperson189_（2 赞）：Unreal actually has a built-in away to load custom content and it's via using the DLC system (which uses content only plugins), and Epic has this plugin called SimpleUGC that shows how it works, I've also made my own WorkshopUploader plugin that make… 立场说明：给出工程 workflow 或工具链角度的取舍，落地价值较高。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1v6u0bp/how_do_i_secure_my_games_against_malicious_custom/

### 3. Perforce and Horde on a shoestring budget

**摘要：** 这条帖子分享一个低预算搭建 Perforce 与 Horde 的团队工作流：小团队跨时区协作，希望用约每月 20 美元覆盖版本库、备份、源码编译和构建分发。核心价值不在省钱本身，而是把 UE 项目常见的 P4、BuildGraph/Horde、备份和 Steam 上传串成可复用流水线。它值得关注，因为很多独立团队从 Git/LFS 迁移到 Perforce 时，真正卡住的是运维复杂度、权限管理、夜间备份和构建交付，而这类经验能帮助判断自托管、云服务和替代版本管理工具的边界。

**高赞/高信号评论：**
- u/DGoodayle（隐藏 赞）：Given we're on a timeline, we don't really have the time to be trying out new workflows. I've also never heard of it and I'm not sure if it's even supported by Epic. Maybe in the future, though Lore is looking more likely to be our next bet down the line. 立场说明：给出工程 workflow 或工具链角度的取舍，落地价值较高。
- u/Sk00terb00（隐藏 赞）：Clever. I was doing Google Cloud services, but now I host my P4 server at home with backups running nightly. I would like to know more about doing builds on my server and deploying them (Steam) 立场说明：提供了可操作经验或反例，不只是情绪反馈。
- u/Vulltrax（隐藏 赞）：Diversion is excellent and has a super easy plugin for Unreal. Took me less than 10 minutes to get a repo stood up and first submit. Def check it out on your next project! 立场说明：给出工程 workflow 或工具链角度的取舍，落地价值较高。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1v7rwgm/perforce_and_horde_on_a_shoestring_budget/
