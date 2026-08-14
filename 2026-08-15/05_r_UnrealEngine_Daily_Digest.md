
## 1. [open source] umg design system

**摘要：**
这个帖子讲的是一个面向 Unreal Engine UMG 的开源设计系统。核心不是单个控件，而是把 design token、主题色、间距、字号、图标和 C++ widget 封装成一套可直接落地的组件语言，做到启用插件后就能在 UMG Designer 里快速拼界面。它值得关注的点在于，它把 UI 统一性从“每个项目手工约定”变成“框架层默认提供”，对中大型项目尤其有价值。对团队来说，这类方案能减少界面风格漂移、降低重复实现成本，也更容易把暗色/亮色主题、图标集和基础交互一起收口。对于正在做工具界面、游戏内菜单或复杂 HUD 的团队，它很像一个能直接拿来改造项目 UI 基础设施的起点。

**高赞评论：**
- u/MyNameIsDjole（3赞）：当年做过假操作系统 UI，这种系统会很省事。立场说明：这条说明它的适用场景很明确，尤其适合做桌面风格、工具壳或模拟器界面，不是纯展示型夸赞。
- u/Dire_Venom（隐藏）：这套架构看起来干净，问题定义也清楚，还问到了 widget class bloat。立场说明：这条抓住了真正的工程点，关注的是架构收敛和类膨胀控制，而不是表面视觉。
- u/WartedKiller（隐藏）：为什么从 SButton 而不是 CommonUI 起步。立场说明：这是很实在的实现追问，能直接引出控件基类选择、可扩展性和与 CommonUI 的取舍。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1vnn2uj/open_source_umg_design_system/

## 2. Turns out Lumen had been doing nothing in our project for months

**摘要：**
这条是很典型的 UE5 渲染排障帖，价值在于把“看起来像 Lumen 的问题”拆成了配置和渲染路径两层。楼主原本以为是 Planar Reflection 和 Lumen 交互导致的崩溃，结果真正暴露问题的是把硬件光追打开后，才发现项目里长期保留着从 UE4 继承来的旧 ini：距离场关闭、RayTracing 关闭、一些旧 cvar 还在，但 UE5 并不会明确报错，只会悄悄退化成屏幕追踪。这个帖子值得看，是因为它说明了 UE5 迁移项目里最容易踩的坑不是某个单独功能，而是“配置还能跑，但渲染已经退化”。评论里还进一步把皮毛、皮肤缓存、Lumen、VSM、Nanite 之间的依赖关系讲清楚，对做性能优化、迁移旧项目、排查渲染假死特别有参考价值。

**高赞评论：**
- u/Strong_Ant3431（5赞）：先别急着重建 binding，先把 skin cache 编译和运行状态弄对。立场说明：这条直接指出了故障层级，区分了 shader 编译问题和绑定问题，排障顺序很专业。
- u/vexargames（3赞）：建议新建一个 ray traced 项目对比 ini，再把 Nanite、HW RT、Lumen 的成本单独算清。立场说明：它把“先修配置”提升成了“把渲染预算和团队成本显式化”，很适合项目治理。
- u/Zvyaginsky（隐藏）：原来 r.SkinCache.CompileShaders 是编译期开关，不是运行时切换。立场说明：这条是很好的结论回收，说明问题根源和修复步骤都已经落到可执行层面。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1vn3qhr/turns_out_lumen_had_been_doing_nothing_in_our/

## 3. How to correctly handle replicated shooting?

**摘要：**
这是一个很适合 UE 多人项目的射击复制讨论。楼主现在做法是客户端先做线性检测，再把命中位置、命中 Actor、骨骼命中通过 RPC 发给服务器，担心自动武器会在高射速下产生 RPC 压力。这个问题的核心其实不只是“带宽省不省”，而是权威逻辑应该放在哪里：是客户端先算命中再上报，还是只上报开火输入，由服务器自己重算命中并做回溯。评论里把竞争性 PvP 和 coop 的需求区分得很清楚，也提醒了 full auto 一般按按下/松开发 RPC、不要复制 projectile、以及要结合 lag compensation 和 server-side rewind。它值得关注的原因在于，这类设计会直接决定后续的作弊风险、手感、网络成本和代码复杂度，属于射击项目早期必须做对的基础架构问题。

**高赞评论：**
- u/MartinMakingGames（6赞）：如果是竞技游戏，就别把问题当成简单 RPC 复制来看。立场说明：这条把场景边界讲清楚了，告诉你不同游戏类型需要完全不同的命中模型。
- u/Rev0verDrive（3赞）：服务器只需要知道你开枪了，自动武器用 burst counting，不要复制 projectile。立场说明：这是可执行的工程建议，直接落到输入、命中和网络对象建模上。
- u/riley_sc（9赞）：全自动一般在按下和松开扳机时各发一次 RPC，但这取决于你的联网模型和是否做反作弊。立场说明：这条给出了比较稳的默认做法，也明确提醒了实现前提，不会误导成万能答案。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1vnm1c6/how_to_correctly_handle_replicated_shooting/
