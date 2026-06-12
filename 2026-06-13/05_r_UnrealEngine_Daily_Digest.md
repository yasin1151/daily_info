
今日 r/UnrealEngine 技术热帖筛选到 2 条，其余多为纯展示、低信息求助，或详情页/评论不足以支撑推送。

## 1. GPU FFT 海面系统 2.0：复制、船只、浮力与 Compute Shader 泡沫

摘要：作者更新了 UE 插件 Dynamic Real Water 2.0，把原有 GPU 加速 FFT 水面系统几乎重写了一遍。核心变化包括：多人复制支持、可驾驶船只系统、更稳定的异步 CPU 浮力、交互泡沫、重做视觉层，以及更好的开发体验。值得关注的是评论中补充了实现细节：船只泡沫不是简单贴图，而是基于 Compute Shader 的层，使用以相机为中心的 Render Target 覆盖较远距离。这类案例对 UE5 水体、网络同步、渲染效果与性能权衡都有参考价值。

高赞评论：
- u/klawd11 · 0 赞：追问船只泡沫实现方式，关心它是跟随 actor 还是 camera 的 Render Target；立场是从渲染管线角度验证方案可扩展性。
- u/boranoztrk · 0 赞：作者解释泡沫是一层 Compute Shader，RT 始终以相机为中心，并可叠加船只交互；立场是强调实现不是局部特效，而是系统化水面交互层。
- u/Illustrious-Site1955 · 0 赞：询问性能和优化情况；立场是认可视觉效果，但把重点拉回真实项目中的运行成本。

原帖：https://www.reddit.com/r/unrealengine/comments/1u3uxax/i_have_updated_my_gpuaccelerated_fft_water/

## 2. UE5.7 + VS2026 Live Coding 编译过慢：冷编译、头文件与工作流问题

摘要：一名新 UE C++ 用户反馈：刚建项目、只添加 landscape、sublevel 和一个简单 Actor，在 BeginPlay 打一行 log，用 Live Coding 编译却非常慢。讨论重点不是“电脑配置够不够”，而是 UE C++ 的编译模型：改动 `.h` 文件会触发更大范围编译，首次编译/清理后的冷启动也会慢，Live Coding 并不适合所有 C++ 结构变更。这个帖子适合作为 UE C++ 入门工作流提醒：区分冷编译与增量编译、看编译输出、必要时关闭编辑器重新生成项目文件。

高赞评论：
- u/kaalins · 0 赞：指出如果改了 `.h` 文件，不推荐继续依赖 Live Coding，应退出项目、重新生成项目文件并完整编译；立场是把问题定位到 UE 头文件和构建系统机制。
- u/JmacTheGreat · 0 赞：认为当前环境配置可能有问题，并提到社区常推荐 Rider；立场是从 IDE/工具链角度排查，而不是单纯怪 UE。
- u/bieker · 0 赞：建议确认是否第一次编译、是否只是改一行后再次编译，并查看输出中实际编译了多少文件/步骤；立场是先区分冷编译、增量编译和异常配置。

原帖：https://www.reddit.com/r/unrealengine/comments/1u3s8h8/long_compilation_time/
