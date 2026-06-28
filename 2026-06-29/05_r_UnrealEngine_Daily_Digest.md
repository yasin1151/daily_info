
r/UnrealEngine 今日技术热帖

1. Is quitting Unreal because of UE6 AI and blueprints removal an extreme reaction?

摘要：这条帖子的背景是 UE6 公布后，部分 UE5 用户担心 AI 功能会进入引擎核心，同时传闻 Blueprints 可能被移除或被新系统替代。核心讨论不是单纯“要不要抵制”，而是项目是否应该因为未来版本路线而提前迁移。值得关注的是，评论区普遍把问题拉回工程现实：UE5 仍可长期使用，UE6 尚未发布，Blueprints 的实际命运也未定，团队不应基于不完整信息做高成本切换。

高赞评论：
- u/Due_Mastodon_7052（Hidden赞）：立场是务实保守。评论要点：可以继续使用 UE5.8，就像很多开发者仍在使用 UE4.27，没有人强制迁移到 UE6。
- u/FriendlyInElektro（Hidden赞）：立场是反对情绪化迁移。评论要点：如果专业或业余项目仍受益于 Unreal，就没有必要为了未落地的 UE6 变化惩罚自己的工作流。
- u/maku_89（Hidden赞）：立场是长期版本锁定可行。评论要点：UE5 完全可以继续用很多年，AI 目前还远不足以稳定产出高质量、连贯、有新意的玩法。

原帖：https://www.reddit.com/r/unrealengine/comments/1ui9vd9/is_quitting_unreal_because_of_ue6_ai_and/

2. How to make an attack “attach” and deal multiple ticks of damage to an enemy

摘要：楼主想在 UE5.4 里复刻《怪物猎人》铳枪类连招：输入序列、组合按键、命中后附着到敌人并持续造成多段伤害。这个问题值得关注，因为它把很多动作游戏系统的基础难点放在一起：输入缓冲、连招状态机、持续伤害、Actor/Component 附着，以及是否引入 GAS。评论区给出的方向很工程化：DoT 可由 Gameplay Effects 处理，但连招系统通常需要自己设计清晰状态结构。

高赞评论：
- u/Accomplished_Rock695（Hidden赞）：立场是建议使用 GAS。评论要点：持续伤害很容易，可以看 Gameplay Ability System 里的 Gameplay Effects，设置 duration 即可；连招系统则大概率需要自己实现。
- u/JDSherbert（Hidden赞）：立场是拆成输入栈和附着对象。评论要点：把玩家输入存进数组/栈，在超时后清空，循环检查输入序列；“刺入敌人”的部分可以做成 Actor 或 Scene Component。
- u/MattOpara（Hidden赞）：立场是用状态机建模。评论要点：连招可视作 state machine；组合输入可用 chorded actions，触发后把 tag 或状态传给 advance state function。

原帖：https://www.reddit.com/r/unrealengine/comments/1ui4s79/how_to_make_an_attack_attach_and_deal_multiple/

3. Did 5.8 fix any issues on Linux or Wayland?

摘要：楼主想知道 UE 5.8 是否改善了 Linux/Wayland 稳定性，因为他希望摆脱 Windows，但过去 UE 在 Linux 上仍有不少阻碍。这个话题值得关注，因为它直接关系到开发环境迁移成本：不是“能不能运行”这么简单，而是源代码编译、Vulkan/驱动、发行版更新节奏、GPU 组合和项目加载稳定性共同决定体验。评论显示，Linux 上 UE 已有人稳定使用，但仍高度依赖本机驱动栈和发行版维护质量。

高赞评论：
- u/tukaram92（Hidden赞）：立场是原生编译更可靠。评论要点：如果从源码本地编译，基本可以工作，UI 有些小问题；他在最新 CachyOS 上使用体验较稳定。
- u/luden_dev（Hidden赞）：立场是仍有真实崩溃风险。评论要点：自己本机原生编译后，项目加载时能看到 3D viewport 和异常光照，随后会直接崩溃。
- u/tukaram92（Hidden赞）：立场是问题常在驱动和 Vulkan 交互。评论要点：不同系统处理 Vulkan 与驱动版本的方式会影响稳定性；CachyOS 的驱动交付目前对他较稳，Fedora 更新后曾停止正常工作。

原帖：https://www.reddit.com/r/unrealengine/comments/1uhu9su/did_58_fix_any_issues_on_linux_or_wayland/
