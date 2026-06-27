
**r/UnrealEngine 今日技术向热帖**

**1. Blueprint 继承：子蓝图为什么看不到父类 Event Graph？**  
摘要：一个塔防项目作者把炮塔公共逻辑放进父 Actor，再派生多个子蓝图，却发现子类里看不到父类 Event Graph，以为继承失效。评论区澄清了 UE Blueprint 的继承模型：变量和函数会继承，但父类图不会被复制到子类；子类应通过函数 override、调用父实现、修改默认值来扩展行为。这类问题很适合作为 Blueprint 架构入门提醒，尤其是多人项目里父类、子类、Child Actor 概念很容易混用。  
高赞评论：  
- u/MasterCitrus，16赞：子类会继承变量和函数，但父实现只显示在父类 Event Graph 中。  
- u/nomadgamedev，10赞：类比普通代码继承，子类不是复制逻辑，而是调用或 override 父函数并改默认值。  
- u/SpagettiKonfetti，7赞：可在 Functions 区域选择 override，若要保留原逻辑，需要显式调用 parent 版本。  
原帖：https://www.reddit.com/r/unrealengine/comments/1ug3ud4/

**2. Skeletal Mesh Socket 返回相对坐标：到底是空间没转换还是 socket 没找到？**  
摘要：作者在 Skeletal Mesh Component 上取 socket world transform/location，却得到类似相对坐标的结果；同样逻辑放到 Static Mesh 上又正常。评论给出两个排查方向：一是把 socket 的局部 transform 与组件 transform 做 Compose Transforms，注意顺序；二是确认 Skeletal Mesh 上 socket 名字真实存在，因为 UE 在 socket 不存在时可能静默返回组件 transform。这是典型的“节点看似成功但语义错位”的蓝图调试案例。  
高赞评论：  
- u/duskkazuno，3赞：最直接的修法是把 local transform 和 component transform compose 成 world transform。  
- u/duskkazuno，2赞：Compose Transforms 顺序很重要，先应用 local，再应用组件世界变换。  
- u/SadLevel9017，赞数隐藏：建议先用 DoesSocketExist 检查名字，Skeletal socket 常在 Skeleton Asset 上且命名不如预期。  
原帖：https://www.reddit.com/r/unrealengine/comments/1ug3qnw/

**3. Chaos 破坏物体挂在墙上：常驻 Geometry Collection 不是好方案**  
摘要：作者在做家具破坏游戏，墙上海报、时钟、烘手机等对象需要先固定在墙上，被击碎后再参与 Chaos 破坏；但直接给它们 Geometry Collection 会导致物体掉落、抖动或约束异常。评论建议把“完整状态”和“破坏状态”拆开：平时使用普通 Actor，生命值归零后销毁并生成 Chaos Actor，再施加伤害；另一种思路是用 Anchor Fields 固定，命中后移除锚点。这个讨论对实时破坏系统的状态切换很有参考价值。  
高赞评论：  
- u/JustAUserInTheEnd，赞数隐藏：不要让 Chaos Actor 常驻，先用普通 Actor，归零后 destroy、spawn Chaos actor、apply damage。  
- u/82bladerunner，赞数隐藏：作者说明自己原先让 Chaos Actor 一直存在，再用 onBreakEvent 触发。  
- u/PokeyTradrrr，赞数隐藏：建议使用 anchor fields，并在命中时移除 anchor fields。  
原帖：https://www.reddit.com/r/unrealengine/comments/1uhaybk/

**4. 只在 packaged build 崩溃：日志、DLL 与间接资源引用的排查经验**  
摘要：作者遇到项目编辑器中正常、打包版本 Fatal Error 的问题，并贴出 verbose log 求助。评论先指出应从日志顶部的 DLL 加载失败、error 关键字和相关论坛线索入手；后续作者补充了真正原因：角色 Actor 间接引用了包含关卡内特定 Actor 信息的 Level Sequences，角色随 GameMode 提前加载，导致关卡 Actor 尚未就绪时序列被加载。最终通过移除这些间接关卡资源引用解决。值得关注的是，这不是单纯“读日志”问题，而是 packaged build 中加载顺序和硬引用链的实战坑。  
高赞评论：  
- u/ananbd，赞数隐藏：建议从日志顶部无法加载的 DLL 名称和 error 关键字开始搜索定位。  
- u/ThePointerIsNull，赞数隐藏：给出一个 Unreal 官方论坛相关崩溃讨论作为线索。  
- u/Fefly，赞数隐藏：作者回报根因是角色 BP 间接引用 Level Sequences，导致关卡 Actor 加载顺序出错。  
原帖：https://www.reddit.com/r/unrealengine/comments/1ugy4vv/
