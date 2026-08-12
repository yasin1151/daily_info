
# r/UnrealEngine 今日技术热帖

Redlib 公共实例本轮未通过语义检查，已回退 old.reddit hot 列表与详情页；评论赞数在 old.reddit 详情页中隐藏，以下按“赞数：隐藏”标注。

## 1. 嵌套 Blueprint 里的 line trace 本地空间转换失效

**摘要：** 作者想做一个可交互控制面板：玩家看向控件并点击后，根据 trace 命中位置移动滑块。逻辑在直接放进关卡的 Blueprint 中正常，但把控件作为 Child Actor Component 放进另一个 Blueprint 后，World to Local 结果看起来没有生效。讨论的核心是 transform 参照系：相对变换只相对父对象，嵌套后不再等同世界变换。这个帖子值得关注，因为它是 UE 组件层级、交互命中点和本地坐标转换的典型坑，很多 Editor 工具、机关面板和嵌套 Actor 交互都会遇到；修正点也很小，适合直接迁移到类似蓝图。

**高赞评论：**
1. u/TheCoCe（赞数：隐藏）：问题在于使用了 relative transform；放在世界中时 relative 与 world 基本一致，但作为 child actor 后 relative transform 只是相对父 Actor 的偏移，应使用组件的 inverse world transform 转到本地空间。立场说明：这是最关键的定位，直接指出 bug 来自参照系变化，而不是 line trace 本身。
2. u/DMEGames（赞数：隐藏）：猜测 child Blueprint 场景下 trace 可能先打到 Owner；即使勾选 Ignore Self，也可能需要把 owner 加入 Ignore Actors 数组。立场说明：这个建议没有命中最终答案，但提醒了嵌套 Actor 交互里碰撞过滤也要显式检查。
3. u/goodwarrior12345（赞数：隐藏）：作者反馈把 Get Relative Transform 换成 Get World Transform 后问题解决。立场说明：这是可复现的最终修正，说明该场景下应先拿世界变换，再进行本地空间计算。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1vm8zdy/converting_line_trace_to_local_space_seems_to_not/

## 2. 缩放 Landscape 来获得更细地形细节是否可靠

**摘要：** 作者在做驾驶原型，默认 Landscape 网格间距导致地形过粗，平滑山丘变成尖锐顶点；把 Landscape scale 从 100 调到 50 后细节满足需求，但担心后期出现 LOD、光照或工具链问题。讨论没有给出绝对禁令，而是把问题落到 Landscape 分辨率、刷子、LOD 与 UE 5.8 mesh terrain 方向上。它值得关注，是因为很多开放地形原型会在“提高顶点密度”和“保持引擎预期尺度”之间摇摆，早期尺度选择会影响驾驶手感、性能预算和后续重做成本；这类决定越晚返工代价越高。

**高赞评论：**
1. u/grandmaMax（赞数：隐藏）：作者追问希望看到具体失败案例，而不是泛泛地说不能改 scale；他查到的主要是 2014 年旧光照问题，且自己有多年手工地形经验，当前痛点只是标准 Landscape 细节不够。立场说明：这条把讨论从原则争论拉回实际风险证据，适合评估是否值得在原型期尝试。
2. u/Northwest_Radio（赞数：隐藏）：认为 Landscape 尺寸和网格设置很重要，建议遵守一些规则，让引擎的 LOD 和地形刷子正常工作，并去看 landscape brushes、LOD 相关教程。立场说明：建议偏保守，但提醒 scale 不是单一参数，后续还会牵动 LOD 与工具行为。
3. u/Jaxelino（赞数：隐藏）：提到 UE 5.8 mesh terrain 仍偏实验性，但相关技术讲座可能能解释其工作方式，或许适合这类更细地形需求。立场说明：这是替代路线提示，说明如果标准 Landscape 达不到需求，可以关注新地形系统而不是只压缩 scale。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1vmp1xf/scaling_landscape_to_get_more_detail/

## 3. FAB 角色重定向后材质变青色的根因

**摘要：** 作者从 FAB 买了一个 UE5 skeleton 角色，需要转到 UE4 skeleton，于是用 Accurig 重新 rig 并导入新 mesh。动画与骨架看似正常，但腿部材质变成青色；两套 mesh 使用同一个材质，作者一开始排除了缺材质、shader 错误和 vertex color。后续排查发现 Material Instance 里存在 Vertex Color mask 开关，只是最初没注意到。这个帖子值得关注，因为资产迁移、重定向和外部工具重导入经常会保留材质引用却改变顶点色/遮罩输入，视觉异常不一定来自 shader 编译或贴图丢失；排查时要把 MI 参数也纳入清单。

**高赞评论：**
1. u/Gojira_Wins（赞数：隐藏）：提到自己集成 shader 到现有材质时也遇到类似青色问题，颜色默认值从 white 改成 black 后才恢复。立场说明：这说明青色常来自材质参数或 mask 默认值，而不一定是引擎级错误。
2. u/ApeirogonGames（赞数：隐藏）：作者补充原模型没有青色问题，两者使用同一材质；截图链接一度不可见，后来改成公开链接，并说明普通纹理显示正常。立场说明：这条缩小了排查范围，排除了“材质资源完全丢失”的简单解释。
3. u/ApeirogonGames（赞数：隐藏）：作者最终确认材质里确实有 Vertex Color mask，只是最初没发现，Material Instance 中的 bool 暴露了线索。立场说明：最终结论可操作，迁移资产时应检查 MI 参数、vertex color 通道和 mask 开关。

原帖链接：https://www.reddit.com/r/unrealengine/comments/1vlyn6p/why_is_my_material_turning_cyan/
