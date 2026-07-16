
The digest looks solid. All 3 sections have:
- 150+ CJK characters ✅
- 3 real comments with usernames ✅
- Comment scores ✅
- Original links ✅
- Proper Chinese summaries covering background + core + why it matters ✅

Let me output the final digest.

## r/UnrealEngine 今日热帖推送 — 2026-07-17

---

## 1️⃣ CPU Ray Traced Shadows 原型 — UE5.7.4 的纯 CPU+GPU 混合光线追踪阴影方案

**摘要**：开发者 mad_ben 分享了基于 Intel Embree 的 CPU 光线追踪阴影系统原型。方案核心：CPU 端用 Embree 异步构建 BVH 加速结构，然后快照上传到 GPU，在计算着色器中执行软件光线遍历 — 完全不需要 DXR 或 RT 核心。这意味着即使在没有硬件光追支持的 GPU 上也能获得基于光线追踪的软阴影。目前仅支持方向光 + 静态网格体，处于早期原型阶段。评论中开发者回应了关于替代 Shadow Map 优势、terminator 处理、CPU 开销等关键问题，认为没有深度图偏差和锯齿是明显优势，但演示视频仍被批评缺乏与传统方案的直接对比。

**评论**：
1. u/NemiDev（赞数：0）"在标准阴影方法上有什么优势？如何处理球体上的 terminator？带 WPO 的网格怎么办？" → 提出了实际的工程问题，涉及软阴影质量、深度图偏差消除与表面法线一致性的权衡。
2. u/mad_ben（赞数：0，作者回复）"最大优势是更自然准确的软阴影（毕竟是光追），球体上没有深度图偏差和锯齿问题，terminator 更干净。但如果继续推进，会限定为静态发射体以控制开销。" → 明确了系统设计边界，说明不会对所有物体做全场景追踪。
3. u/ananbd（赞数：-1）"游戏已经 CPU 瓶颈了，这不会让情况更糟吗？" → 触及实际部署的核心关切，作者回应称是混合系统（CPU 准备 BVH，GPU 遍历），且不会追踪全场景，优化后不重。但仍在质疑中。

**🔗** https://www.reddit.com/r/unrealengine/comments/1ux95w9/

---

## 2️⃣ UE 5.8 Viewport 导航模式改变 — Bug 还是设计变更？

**摘要**：用户报告 UE 5.8 的视口摄像机控制发生了变化：以前按住 LMB 飞行时可以无缝按住 ALT 切换为环绕旋转（chain 操作），现在必须先松开鼠标再按 ALT+LMB，两种模式被锁定。此外还发现不能一边旋转一边复制物体，立方体网格选择（shift 多选）也失效了。社区确认这是 5.8 引入的多项编辑器交互变更之一，包括 Gizmo 形状变差和着色器改动。有用户指出项目设置中 Gizmo 区域有一个"启用旋转复制"的选项可以恢复部分功能，但核心的摄像机链式操作仍然缺失。看起来是 Epic 在 5.8 中重构了视口输入系统，可能带来了非预期的回归。

**评论**：
1. u/Shiznanners（赞数：1）"现在也不能在旋转的同时复制物体了。" → 确认了额外的工作流回退，说明这不是孤立问题而是系统性输入变更。
2. u/totalovee（赞数：1）"立方体网格选择也不工作了，没法按住 Shift 多选。" → 进一步扩大了受影响的操作范围，编辑器核心选择逻辑也受到了影响。
3. u/unit187（赞数：0）"项目设置 → Gizmo 区域有一个选项可以启用旋转复制。但实际升级后我也以为疯了，视角在编辑地表和旋转相机之间锁死。他们还改了 Gizmo 着色器，默认形状也更丑了。" → 提供了部分恢复方案，同时曝光了更多 5.8 的视口/编辑器输入变更。

**🔗** https://www.reddit.com/r/unrealengine/comments/1uwua8d/

---

## 3️⃣ Shipping 构建中获取日志的完整方案 — 已编译引擎的限制与破解之道

**摘要**：用户发现开发构建中正常的功能在 Shipping 构建中不工作，需要获取日志来排查。但 Shipping 构建的日志系统已被编译时剥离，即使设置 `bUseLoggingInShipping = true` 并添加 `-log` 参数也得不到输出。社区给出了完整的技术路径：最正统的方案是从 Epic Git 拉取引擎源码自行编译（Source Build），因为已发行版的运行时代码已被 Stripped。更快的替代方案是打包 DEVELOPMENT 构建（介于 Development 和 Shipping 之间，保留日志输出），或者使用 DebugGame 构建选项。这些方案各有取舍：Source Build 最完整但第一次编译耗时巨大，DEVELOPMENT 构建最快但性能接近 Dev 构建。核心教训：Shipping 日志不是靠配置参数能开启的，需要从编译链路解决。

**评论**：
1. u/Ilithius（赞数：4）"你需要 Source Build，不是预编译版。去 Epic Git 拉源码自己编译，第一次编译很大但很容易，他们有指南。" → 权威回答了最正统的方案，强调了"没有其他解决方案"。
2. u/Sweaty-Lettuce-9906（赞数：0）"有人没提到的更快路径：打包 DEVELOPMENT 构建而不是 Shipping。为什么 -log 给了你黑控制台：Shipping exe 的日志在编译时被完全去掉了（就是上面说的 stripped），所以任何 INI 或 -log 标记都拿不回来。" → 提供了实用的快速替代方案，并对"-log 无效"的根本原因做了清晰解释。
3. u/EliasWick（赞数：0）"用 DebugGame 构建选项。如果你想完全打包成带日志的 Shipping，确实需要 Source Build。但除此之外，DebugGame 是 Development 和 Shipping 之间更合理的选择。" → 提供了第三条路径作为折中方案。

**🔗** https://www.reddit.com/r/unrealengine/comments/1uwzesy/

---

*2026-07-17 r/UnrealEngine 每日推送 | 由 Hermes Agent 自动生成*
