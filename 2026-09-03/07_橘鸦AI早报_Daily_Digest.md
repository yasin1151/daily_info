
**橘鸦AI早报 · 2026-09-02（周三）要点摘要**

---

**1. Anthropic 发布 Claude Fable 5.1 / Mythos 5.1**
同一模型、安全限制不同：Fable 5.1 全面开放（编程/知识工作/计算机操作/长时 Agent 强化），Mythos 5.1 仅限验证过的网络安全与生命科学机构。Terminal-Bench 4.0 从 42.0% 涨到 55.8%；输入输出单价不变，缓存读取降价 75%（$0.25/M token），典型工作负载省约 25%。同步调整安全机制：Claude Code 网络安全干预减少约 60%，生物/医疗正常请求误触发减约 85%，并引入企业 EFS、反蒸馏和不可见文本水印，发布当天重置所有用户 5 小时/周额度。
https://www.anthropic.com/claude-fable-and-mythos-5-1

**2. OpenAI 宣布 Astra 即将发布（网络安全 Critical 级）**
OpenAI 称 Astra 是首个达到其安全框架网络安全 "Critical" 门槛的模型：ExploitBench 拿到 100%，内部测试发现并利用了 2 个零日漏洞，专家测试完成浏览器沙箱逃逸和普通用户→root 提权链。官方为此推迟了部分开发、强化拒答与跨会话监控；近期开放但最强攻防能力只给部分测试者，后续经 Daybreak Blue 扩大防御性使用。
https://openai.com/index/path-to-astra/

**3. Gemini 3.7 Flash 等三款模型上线 Agentic 视频理解**
模型可自主决定看哪些片段、按什么速度/模态（视觉帧、音频、字幕）处理视频，替代固定 1FPS 整体读入。官方数据：长视频 token 最高省 88%、成本降 66%、准确度最高 +7%。在 Gemini API 配置 processing=agentic 即可启用，按标准 token 计费无附加费，将支撑未来 YouTube "Ask YouTube" 功能。
https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-agentic-video-in-gemini/

**4. World Labs 发布世界模型 Atlas**
多模态自回归扩散 Transformer，原生处理文本/图像/视频/3D：1-6 张图生成最长 1 分钟 1440p 视频（精确相机控制），2-3 张图即可重建真实场景输出点云或 3D Gaussian splats，还支持 Real-to-Sim 机器人仿真。官方称相机控制生成和稀疏视角 3D 重建均超多个专用模型，未来几周开放早期访问，将驱动 Marble 产品。
https://www.worldlabs.ai/blog/atlas

**5. Meta 发布实时音频感知模型 Muse Voice Transcribe**
超级智能实验室首个音频感知模型：单模型内原生做实时流式 ASR + 20+ 说话人分离 + 端点检测，支持多语言和句内语码转换。官方称在 Artificial Analysis 流式语音转写榜和公开说话人分离基准均列第一；已上 Meta Model API（含零数据保留层级），并驱动 Meta AI for Mac 和 Muse Code 语音听写。
https://research.meta.ai/blog/introducing-muse-voice-transcribe

**6. 讯飞星火开源星火 X2.5 端侧模型（4B/1.7B）**
号称端侧首个原生支持 100 万 token 上下文的模型，混合注意力架构，围绕 Agent/代码/数学优化；基于全国产算力平台训练，兼容英伟达/华为/海光等硬件及 vLLM、Ollama、llama.cpp。Apache 2.0，权重已在 Hugging Face/GitHub 开放，API 上线星辰 MaaS 限时免费。
https://github.com/XHToken/Spark-X2.5

**7. 腾讯混元发布 Hy4 preview 量化轻量版（GGUF 开源）**
用自研 Sherry 稀疏三值量化把约 1.5TB 权重压到约 214GB（-86%），长文理解、长上下文检索基本持平原版，多数评测与 BF16 差距 1-2 分内。GGUF 已在 Hugging Face AngelSlim 仓库开源三个版本；注意需先打仓库补丁，llama.cpp 原生跑不了，STQ1_0 版显存约需 214GB。
https://huggingface.co/AngelSlim/Hy4-preview-GGUF

**8. Ollama 订阅改按 token 计费**
Pro $20/月含 $60 用量，Max $100/月含 $300 用量，Team $500/月共享 $1000 用量；无服务费、无 5 小时/周限制，用完按相同 token 价续用，还预告了错峰定价。老用户原方案继续有效可随时升级。对重度本地+云端混用用户，成本更可预测了。
https://ollama.com/pricing

**9. 传 Anthropic 与 Lambda 签 350 亿美元云协议**
据路透/彭博，Anthropic 与英伟达投资的云商 Lambda 签约，租用德州约 350MW（Hut 8 开发）数据中心算力，由 Lambda 部署英伟达芯片供 Claude 使用，应对需求增长。Anthropic 算力军备仍在加码。
https://www.reuters.com/technology/anthropic-signs-35-billion-cloud-deal-with-nvidia-backed-lambda-source-says-2026-08-31/

**10. Manus 正式恢复独立运营**
创始团队继续领导，作为独立 agent lab 运营，将更深嵌入用户工作流、更主动代表用户与世界交互。此前过渡期出现访问中断的用户可经恢复门户找回数据，无截止期限。
https://manus.im/blog/manus-resumes-independent-operations

---
已跳过：GLM Coding Plan 周年重置卡（营销）、ChatGPT 礼品卡（仅限美国）、Celeris-1 Magnus、Abliteration GLM-5.3 去拒绝版等低价值/小众条目。最新一期（2026-09-02）已标记已读。
