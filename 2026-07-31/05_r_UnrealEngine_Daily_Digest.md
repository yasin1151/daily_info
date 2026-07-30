
# r/UnrealEngine 今日技术热帖

## 1. Security heads-up: Untrusted compiled Blueprints are not safe, not sandboxable, and should always be treated as arbitrary code execution hazards due to type confusion vulnerabilities in the Blueprint interpreter.

摘要：这帖提醒不要把来自玩家或第三方的已编译 Blueprint 当作安全内容处理，核心问题是蓝图解释器存在类型混淆一类风险，导入后可能接近任意代码执行。它值得关注，不是因为某个单点漏洞，而是因为 UE 生态常把 Marketplace、Mod、Workshop、编辑器导入流程混在一起使用；一旦团队允许外部资产进入项目，就需要把审核、隔离和打包策略当成安全边界，而不能只依赖编辑器看似可打开。评论区进一步讨论 cooked blueprint、Steam/Fab 审核和分发链路，适合给做 UGC、Mod 或插件平台的人做风险清单。

高赞评论：
- u/ParsingError（隐藏赞）：So, I took another look at this, and the documentation suggests there is a way to import cooked blueprints into a project if you enable cooked content in the editor. I haven't had any luck actually getting it to output a cooked blueprint asset file though (vs just pulling it straight from the content directory when packaging), and disabling the "use pak files" option is broken, so I'm not really… 立场说明：这条评论把问题放到 cooked content 与编辑器导入链路上，提醒外部内容进入项目时不能只看编辑器是否能加载。
- u/Gunhorin（隐藏赞）：There is a difference in hacking games or placing marlware on website and using the gaming infrastructure like Steam Workshop to distribute viruses. You are right that games were always not vette proparly. I bet a lot of the multiplayer games will have some form of vurnability… 立场说明：这条评论把风险扩展到 Steam Workshop 等分发基础设施，强调 UGC/Mod 平台需要按供应链安全来处理。
- u/vexargames（隐藏赞）：I understand the barrier of entry seems lower to people but it's always been low, and people always had the ability to use someone other persons tools to create chaos even before AI. 立场说明：这条评论提供了现实反例：AI 只是降低门槛，不改变“外部工具和外部资产本来就可能被滥用”的底层安全判断。

原帖链接：https://www.reddit.com/r/UnrealEngine/comments/1v9lmka/

## 2. A new way to design levels in UE5. Draw, pull, carve, reshape. Fully non destructive. Built into Dungeon Architect

摘要：这帖介绍 Dungeon Architect 新的 Room Designer：在 UE5 中通过绘制、拉伸、切割体块来生成房间，底层保持 add/subtract volumes，因此墙体和平台可以继续非破坏编辑。它值得关注，因为这类工具把传统 BSP/BoxCutter 式的快速白盒流程重新包装成可进入程序化生成管线的编辑器功能；对关卡团队来说，关键不只是建模更快，而是能否把格子、遍历、装饰规则和预制房间缝合起来，减少从 blockout 到最终资产的返工。评论区也在讨论随机化、可通行性和 Markov/rewrite 规则，技术含量高于普通展示。

高赞评论：
- u/coderespawn（3赞）：Thanks. The workflow is inspired by BoxCutter in Blender, where you draw shapes and cut them into geometry. It manages the boolean volumes for you and the mesh is just the result, same as what happens here. I wanted that speed for level design, but constrained to a grid so everything stays stable and snaps together properly… 立场说明：这条评论解释了工具的核心取舍：借鉴 BoxCutter 的速度，但用 grid 与 boolean volumes 保持关卡稳定和可编辑。
- u/msew（隐藏赞）：Driving the volumes themselves procedurally needs more exploration. something like randomizing the volumes with a spatial traversal graph inside the room to make sure the space stays traversible. That would give random good looking rooms… 立场说明：这条评论把问题推进到程序化生成层面，指出随机房间不只是摆体块，还要保证空间遍历和可通行性。
- u/coderespawn（隐藏赞）：Dungeon Architect already has a few procedural systems that define the dungeon layout, then stitches pre-made rooms together, like the one designed in this video. The room designer lets you rapidly build rooms with a human touch… 立场说明：这条评论说明该功能不是孤立编辑器玩具，而是与 Dungeon Architect 现有 layout、Flow framework、预制房间缝合流程结合。

原帖链接：https://www.reddit.com/r/UnrealEngine/comments/1va2dl8/

## 3. Free HLSL Gradient Material Function for Unreal Engine (UV-independent + Path Tracing fix)

摘要：这帖分享了一个不依赖 UV 的 HLSL Gradient Material Function，用对象空间/包围盒思路在整个 mesh 上生成渐变，并特别处理 Path Tracing 下的兼容问题。它值得关注，因为很多材质小工具看似只是节点复用，但真正进入项目后会遇到旋转、缩放、UV 缺失、Nanite/Path Tracing 或美术资产规范不一致的问题；作者把函数开放出来后，评论区重点质疑为什么需要 HLSL、已有节点方案是否足够、以及 path tracing 破坏点在哪里，这些反馈能帮助技术美术判断该函数是生产级工具还是学习示例。

高赞评论：
- u/Thatguyintokyo（隐藏赞）：So this is an object space gradient using the object bounds. This is cool but why did it need to be HLSL? This already exists in nodes made by many people over the years, even back in ue4. The desaturate shouldn’t be nessesary either… 立场说明：这条评论直接审视实现必要性，提醒技术美术先确认节点方案、saturate/clamp 等基础做法是否已经足够。
- u/pereladov（隐藏赞）：The answer is presented in post. When I was newbie to UE and looking how to create object space gradient, I faced two problems: no info how to rotate it if I need something else… and recently I found an issue with PathTracing… 立场说明：这条评论补充作者动机：HLSL 方案主要为了解决旋转控制和 Path Tracing 下 Lerp 颜色异常，而不是单纯重写已有节点。
- u/Thatguyintokyo（隐藏赞）：I’ll get back to you, I’ve not had any need to play with path tracing so i’m not aware of what it impacts, i cant imagine why it’d break this though, so long as the values are clamped it should be ok… 立场说明：这条评论给出生产经验视角：Path Tracing 兼容问题需要进一步验证，且 UE 更新频繁，材质函数最好保留可调试空间。

原帖链接：https://www.reddit.com/r/UnrealEngine/comments/1vavffq/
