
r/UnrealEngine 今日技术热帖

1. Verse is single threaded... so why is Epic deleting Blueprints again?

摘要：这帖围绕 Epic 长期推进 Verse、削弱 Blueprint/Actor 体系的争议展开。核心不是“Verse 现在是否单线程”这么简单，而是 UE 未来 gameplay 编程模型、事务系统、ECS 化和多线程能力如何演进。值得关注的是，评论区把讨论从情绪化的“删蓝图”拉回到运行时开销、节点调度、C++ 边界和 UE7 可能的架构迁移。对团队来说，这会影响脚本层写法、性能热点归属、工具培训成本，以及未来是否要提前为 Verse/数据导向架构预留迁移空间，因此比普通路线图争论更有技术含量。

高赞评论：
- u/Nextil（隐藏赞）：As far as I know, Blueprints are also single-threaded, aside from some of the animation blueprint stuff. It really shouldn't matter for gameplay code. If need to do something really heavy it should be in C++. 中文立场说明：这条评论把 Verse 与 Blueprint 都放在 gameplay 代码的线程模型里比较，提醒重负载逻辑仍应下沉到 C++，避免把脚本层当成万能性能解法。
- u/Polysiens（隐藏赞）：This mindset is because of blueprints and their single threaded nature and overhead that they add to each node. Verse is meant to be more performant and they have solutions like transaction system to make it multithreaded. 中文立场说明：这条评论指出 Blueprint 节点开销和事务系统的差异，提供了理解 Epic 推 Verse 的技术动机。
- u/tcpukl（隐藏赞）：Verse is all transactional. So even if not currently multi threaded is the correct frame work to make it multi threaded. People thinking blue prints is single threaded is hilarious. BP nodes are really slow as well. 中文立场说明：这条评论强调“当前单线程”和“未来可并行化框架”不是一回事，适合用来评估 Verse 的长期架构价值。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1v6odft/

2. How to handle uneven ground/terrain for paired animations (i.e assassinations, takedowns, finishers)?

摘要：这帖讨论在不平地形上处理双人同步动画，例如处决、背刺、终结技。问题本质是动画资产、角色 Z 轴基准、IK、Motion Warping 和失败回退逻辑之间的取舍。它值得关注，因为许多 UE 项目在平地 Demo 中动作成立，但到了坡地、台阶和复杂碰撞环境就会穿模或漂浮；评论区给出了从高制作规格多套动画到低成本运行时校正的完整方案谱系。对动作游戏、潜行动画和近战交互来说，这类细节直接决定镜头可信度、打击反馈和关卡可用范围。

高赞评论：
- u/darthbator（6赞）：It depends on the desired fidelity level of the game. In general you need to validate sync animations before you fire them. If the game has a high production value I'll request assets for various slope grades and for the 2 elevation cases. 中文立场说明：这条评论把问题先拆成制作规格和预校验，说明高品质项目不能只靠运行时补丁，需要资产层面覆盖坡度与高度差。
- u/prototypeByDesign（4赞）：Lots of different options of varying complexity: move both, split the difference, let one of them float, make multiple animations and pick the closest, make multiple animations and use a blend space, ik height adjustment on one or both. 中文立场说明：这条评论快速列出复杂度阶梯，适合团队按预算选择“多动画”“Blend Space”或“IK 修正”的组合。
- u/JDSherbert（3赞）：I've dealt with this situation before. In first person games we use an enemy proxy to sort of clip through the slope to make it less jarring for the player, and replace with the dead ragdoll. 中文立场说明：这条评论提供了生产经验：第一人称可用代理对象隐藏穿坡问题，第三人称则更依赖接触 socket、IK 和前置检查。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1v637tz/

3. Fatal warning that Unreal Engine content is not in repository

摘要：这帖表面是一个“Unreal Engine content is not in repository”的 fatal warning，实际触及 UE 项目如何组织 Git 仓库、哪些目录应提交、哪些生成物和引擎内容必须排除。它值得关注，因为 UE 工程常见问题不是代码本身，而是仓库根目录、插件、Content、Config、Source、DerivedDataCache、Intermediate、Saved、Binaries 的边界不清。评论区给出了可直接套用的版本控制经验，能帮助小团队避免把安装版引擎内容、缓存或构建产物误纳入仓库，减少同步体积、冲突和 CI 误报。对多人协作和自动化构建而言，这类基础规范往往比单次报错本身更重要。

高赞评论：
- u/EliasWick（3赞）：You should not ignore that. What are you trying to do? Have you setup source control for the entire engine + project or just project? 中文立场说明：这条评论先确认仓库范围，抓住了 UE 版本控制排错的第一步：区分“项目仓库”和“引擎源码/安装目录仓库”。
- u/botman（3赞）：You should never be commiting Unreal Engine content to source control (it isn't needed and you should never be changing it). You only need to commit your game's Content folder to source control. 中文立场说明：这条评论给出明确边界：不要提交安装版 Engine/Content，只提交项目自身内容，能避免仓库膨胀和错误依赖。
- u/lewis-go（3赞）：Don’t add the installed Engine/Content directory to your project repo. Your repo root should be the folder containing the .uproject, and your ignore rules should exclude DerivedDataCache, Intermediate, Saved, and Binaries. 中文立场说明：这条评论最具可操作性，直接列出 repo root 与忽略目录，适合作为 UE Git 模板检查清单。

原帖：https://www.reddit.com/r/UnrealEngine/comments/1v659rx/
