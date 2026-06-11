
## V2EX 今日精选

### 1. 苹果 WWDC2026 后的 AI 路线争议
苹果发布会被 V 友认为“功能更新多、AI 交代少”，尤其是 Siri 仍依赖自研模型与 Gemini 补齐，引发对苹果是否在端侧 AI 和全局 Agent 时代掉队的讨论。值得关注的是，评论区分歧集中在“苹果需要追大模型能力”还是“守住终端入口与隐私生态即可”。

💬 热评：
- #2 @xxmym (👍1)：认为发布会没有花哨功能、更多是底层优化，手机 AI 离全局 Agent 还远。
- #8 @maolon (👍0)：苹果坐拥终端入口，端侧硬件与多模态能力才是其核心优势，Gemini 与苹果需求并不完全错位。
- #1 @phrack (👍0)：LLM 更像供应链能力，苹果只要继续用隐私、安全和硬件平台吸引用户即可。

🔗 https://www.v2ex.com/t/1219768

### 2. MiMo API 在 Agent Loop 中提前停止
楼主测试 Xiaomi MiMo-v2.5Pro API 时发现 `tool_choice=auto` 场景下经常提前 `finish_reason=stop`，工具调用为空，导致 SOP 没走完。这个帖子值得关注，因为它暴露了国产模型 API 在 Agent 工作流、工具调用稳定性上的兼容性问题，而不是单纯聊天效果问题。

💬 热评：
- #1 @niubilewodev (👍0)：指出 MiMo 使用 OpenAI Responses 形式时似乎容易出现类似问题。
- #2 @SHF (👍0)：反馈自己写 Agent Loop 暂未遇到，说明问题可能与调用方式或具体接口路径有关。

🔗 https://www.v2ex.com/t/1219736

### 3. MiMo CLI 的终端体验被吐槽
楼主反馈 MiMo CLI 输出异常、页面重叠、不能滚动查看历史内容，怀疑测试不足。评论把问题指向现代 TUI 对终端模拟器能力的依赖，也提到它可能 fork 自 opencode。这个讨论值得关注，因为 AI Coding CLI 的可用性正在从“模型强不强”转向“终端交互、跨平台兼容、工程质量是否可靠”。

💬 热评：
- #4 @bbbblue (👍0)：建议先对比 opencode，并检查 Windows 终端环境，现代终端模拟器和字体配置会影响体验。
- #3 @sommio (👍0)：认为 opencode 需要现代终端模拟器，mimocode 如果 fork 自 opencode，可能没写清终端要求。
- #1 @onecookie (👍0)：吐槽如果是 fork opencode 还能这么难用，说明产品化打磨不足。

🔗 https://www.v2ex.com/t/1219750

### 4. macOS 本地访问带账密住宅代理失败
楼主在量化交易网络调优中遇到同一 HTTP 代理在海外服务器可用、macOS 本地 curl 失败的问题，怀疑 GFW、服务商白名单或 TLS/CONNECT 差异。评论基本指向明文代理被识别阻断，以及用海外机器做链式代理。这个帖子对调试跨境代理、链式代理和本地网络排障有参考价值。

💬 热评：
- #3 @ggyyjy (👍0)：建议用海外机器做跳板，通过 v2fly 或链式代理把国内流量转到海外服务器再出站。
- #4 @nc (👍0)：认为 TUN 或本地 Clash socks5 链式代理应可解决，直连大概率会被阻断。
- #1 @Jianrry (👍0)：明确指出 HTTP/Sock5 代理是明文，容易被 GFW 精准拦截。

🔗 https://www.v2ex.com/t/1219764

已处理并标记 V2EX 本轮 50 条文章为已读。
