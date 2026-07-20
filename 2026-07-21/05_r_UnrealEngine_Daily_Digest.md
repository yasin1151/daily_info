
# r/UnrealEngine 今日热帖

## 1. Switching from Godot to UE with C++

**摘要：** 这帖讨论一个团队从 Godot 转向 Unreal 后，如何补齐 UE C++ 能力。重点不在“学 C++ 语法”本身，而是 Unreal 的 Actor/GameFramework、UObject 生命周期、宏和反射系统，以及 C++ 与 Blueprint 的分工。评论普遍认为，C++ 适合做稳定系统和可复用基础，Blueprint 更适合迭代和配置；团队迁移还要计算已有语言、工具链和流程成本。值得关注的是，这类迁移决策很容易被引擎功能吸引，但真正决定成败的是工程流程能否重复交付高质量玩法。对已有 Godot 经验的团队来说，这也提示学习顺序应先围绕小型玩法闭环，而不是先追求完整掌握引擎源码。

**高赞评论：**
- u/obviouslydeficient（5赞）：well then I would honestly start with that and combine it with learning UE c++. I'm going to list some things you will need to think about in no particular order. * In UE the combination of c++ and blueprints is key to development. And especially le… 立场说明：这条强调工具链和日常流程影响，比单点功能更接近团队落地问题。
- u/lewis-go（6赞）：Coming from GDScript, I’d learn Unreal C++ in two layers: general C++ fundamentals and Unreal’s object framework. A practical order: References, pointers, const, containers, classes, and basic templates. Create a small Actor and Actor Component; exp… 立场说明：这条提供了工程实现角度，能帮助判断是否需要深入到引擎或 C++ 层。
- u/pantong51（5赞）：The most important thing is to find processes that allow for high quality, repeatable, games. Then optimize that. If it's an engine change that can facilitate that, the that's when you make that decision. If an existing company that mostly uses Unit… 立场说明：这条把讨论拉回性能和迁移成本，适合用来评估方案是否值得投入。

原帖：https://www.reddit.com/r/unrealengine/comments/1v0vq2w/switching_from_godot_to_ue_with_c/

## 2. Root motion animation problem

**摘要：** 这帖是一个 root motion 动画排障讨论，主题集中在动画来源、骨骼层级和 AnimBP 设置。虽然主帖信息有限，但评论给出了比较具体的检查路径：先确认 root bone 是否真实移动，再区分 montage 与 AnimBP 播放方式，并检查是否启用了从所有来源提取 root motion。还有人指出 Mixamo 动画常缺 root bone，需要在 Blender 或插件中修正。值得关注的是，root motion 问题经常看起来像 UE 设置错误，实际可能是 DCC 导出、骨骼命名、动画资源和引擎提取规则共同造成的。对动画管线而言，这类帖子能提醒团队把导入规范、骨架检查和 AnimBP 默认值纳入排障清单。

**高赞评论：**
- u/dave_sullivan（1赞）：How did you setup the animation? With blender? In blender to get root motion to work, you need to exit pose mode and key the movement to the rig object itself. Then when you export it, UE should detect it correctly (with root motion turned on). I re… 立场说明：这条强调工具链和日常流程影响，比单点功能更接近团队落地问题。
- u/diabolik-god（隐藏赞）：Don't waste time with ai plugins. Autorig pro can fix these kinds of issues if you use mixami animations, it's a three clicks job. 立场说明：这条强调工具链和日常流程影响，比单点功能更接近团队落地问题。
- u/Will_X_Intent（1赞）：Did you get the animation from mixamo? If the animation doesn't have a root bone, you can fix it or have AI fix it in blender. There is a plugin that helps. 立场说明：这条强调工具链和日常流程影响，比单点功能更接近团队落地问题。

原帖：https://www.reddit.com/r/unrealengine/comments/1v0i8h3/root_motion_animation_problem/

## 3. Last Week In Unreal: 789 on ue6-main, 48 on ue5-main |

**摘要：** 这期 Last Week In Unreal 汇总了 ue6-main 与 ue5-main 的提交动态，评论焦点转向 Epic 正在建设的 Unreal AI/agent 工作流，以及它和现有通用代码代理的差异。主帖本身显示 UE5 维护分支更多是构建系统和底层管线工作，UE6 主线活动更密集；评论则关心 AI 是否能可靠处理 Blueprint、材质、网络和构建优化。值得关注的是，AI 辅助 Unreal 开发的瓶颈不只是“能否生成代码”，还包括节点图可审计性、资产编辑安全性和团队能否接受自动化改动。它也说明 UE6 相关变更正在从底层工程和编辑器自动化两个方向同时推进。

**高赞评论：**
- u/bieker（隐藏赞）：I have had Claude, GLM and gpt-5.5 work on existing blueprints and they handle it fine. They make a mess of the node graph though so it’s hard to audit or work on them manually after. The built in mcp has an auto-reorganizer tool the llm can call bu… 立场说明：这条强调工具链和日常流程影响，比单点功能更接近团队落地问题。
- u/ZeusAllMighty11（隐藏赞）：I am curious what this AI agent they're building has to offer over other popular agents. Although they can't do Blueprints right now, the top agents are all more than capable of doing quite a bit in Unreal including networking, materials/shaders, bu… 立场说明：这条把讨论拉回性能和迁移成本，适合用来评估方案是否值得投入。
- u/bieker（隐藏赞）：Well I am a professional developer in my day job and while I don’t have a ton of C++ experience I am very familiar with it and am very experienced in systems design and software design patterns. We also use a lot of AI assist tools at work so I am v… 立场说明：这条强调工具链和日常流程影响，比单点功能更接近团队落地问题。

原帖：https://www.reddit.com/r/unrealengine/comments/1v1h34t/last_week_in_unreal_789_on_ue6main_48_on_ue5main/
