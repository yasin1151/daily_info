
# 橘鸦AI早报 · 2026-08-21 摘要

共 23 条新闻，筛选出 10 条高价值信息：

---

## 🔥 要闻

**1. OpenRouter + OpenCode 上线免费 stealth 模型 Ox Alpha**
两家平台联手推出不公开供应商的推理模型，面向编程、持续 Agentic 工作与生产负载，**上下文 1M token，支持文本/图像/视频输入**。OpenCode 承诺一周内免费；OpenRouter 侧提示词由提供方保留但不用于训练，OpenCode 侧则宣称零数据保留。免费窗口内值得直接拿去跑长上下文 agent 任务试试。
https://openrouter.ai/stealth/ox-alpha

**2. Claude Platform 正式 GA：computer use + Skills API + Files API**
Anthropic 宣布 computer use 正式可用，并新增 browser use 工具；Skills API 与 Files API 同步上线 Microsoft Foundry，Vertex AI 即将跟进。**说明这套 Agent 能力栈已从 beta 转正为可依赖的正式产品**，企业用户选型时的确定性更高了。
https://claude.com/blog/computer-use-skills-api-files-api

---

## 📦 模型发布

**3. 阿里千问发布 GUI 智能体基座模型 Qwen-UI-Agent**
覆盖移动端、电脑端、网页端及深度搜索环境。官方数据显示在 **MobileWorld、OSWorld-Verified、WebArena 等基准上超越 GPT-5.6 Sol 和 Claude Opus 4.8**。GUI 操作类 agent 是当前竞争最激烈的方向，国产模型首次在多基准上同时压过两家旗舰，值得关注后续实测。
https://github.com/Tongyi-MAI/MAI-UI

**4. 商汤开源 SenseNova-U1.5-8B-MoT 多模态模型**
基于 NEO-unify 架构，**Apache 2.0 许可**，主打图像生成、中英文文本渲染、原生 4K 生成、图像编辑等六项提升，技术报告与 SFT/RL 到 MOPD 的完整训练流程后续开源。8B 规模 + 全流程开源，自部署做多模态生成的门槛又低了一档。
https://huggingface.co/sensenova/SenseNova-U1.5-8B-MoT

**5. Liquid AI 发布 LFM2.5 DSpark draft models**
为 1.2B/2.6B/8B 三款模型提供投机解码草稿模型：**GPU 吞吐最高提升 3.18 倍，设备端最高 2.87 倍，2.6B 函数调用延迟平均降 57%**，且不改变输出质量、内存增量极小。对端侧部署和 agent 函数调用场景是实打实的免费加速。
https://huggingface.co/blog/LiquidAI/lfm25-dspark

---

## 🛠 开发工具

**6. Google 推出 Antigravity IDE 扩展**
覆盖 **VS Code、Visual Studio、JetBrains 全系和 Zed** 四款 IDE，个人开发者任意订阅方案（含免费层）登录即可用，提供会话、自定义及共享上下文的多 Agent 编排。Google 在编码 agent 的 IDE 入口争夺上正式下场。
https://antigravity.google/blog/introducing-google-antigravity-2

**7. Exa 推出 Codex 与 ChatGPT 插件**
可让 ChatGPT Work 和 Codex 访问**超 1000 亿个网站、论文、文档**。公告未提定价与用量限制，评论区多名用户追问是否免费，官方暂未回复。搜索型工具与编码 agent 结合，是补齐 agent 实时信息获取能力的关键拼图。
https://x.com/OpenAIDevs/status/2090480484107141493

---

## 🚀 产品应用

**8. Grok Build 模式向所有 SuperGrok / X Premium 用户开放**
一条提示词即可生成带独立域名的可发布产品，底层运行完整编码 Agent（支持 subagents、浏览器使用、数据库与 secrets），可发布到 grok.me 或自有域名，也可导出源码。**「提示词 → 上线产品」的产品化程度又进了一步**。
https://x.ai/news/grok-build-for-everyone

---

## 🏭 行业动态

**9. 报道称 MiniMax 研发负责人阿岛离职**
原工程研发负责人阿岛（缪宇航）已离职，此前负责 **M3.x、Code、Agent、Audio 和海螺 AI** 等多条核心研发线。飞书状态已显示离职，下一站去向与接替人选均未公开。核心模型负责人变动，对 MiniMax 后续模型节奏是个不确定性信号。
https://mp.weixin.qq.com/s/Mjs8jLuyGQn0ah4yJmGO9w

**10. 消息称 Anthropic 最快 8 月底递交 IPO 申请**
彭博援引知情人士：Anthropic **预期 IPO 规模追平甚至超越 SpaceX 创纪录的发行**，最快 8 月底公开递交申请；近期投资者简报会回避了估值问题。未获官方确认。若属实，这将是 2026 年最受关注的科技 IPO 之一。
https://www.bloomberg.com/news/articles/2026-08-20/anthropic-expects-to-match-spacex-s-record-ipo-size-or-top-it

---

**本日主线**：Agent 基础设施全面转正（Claude Platform GA、Qwen-UI-Agent、Grok Build 全量开放）+ 模型免费化竞争（Ox Alpha、Muse Spark 1.2）+ 国内头部公司人事与资本动向。

*略过未收录：Claude Academy 学习平台、Ollama Kimi K3、ChatGPT Messages 插件/只读分享、GPT-Image-2 透明背景、FLUX Upscale、Meta WildArtifactBench、Anthropic 数据留存调整等（价值或时效性较低）。*

来源：[橘鸦AI早报 2026-08-21](https://daily.juya.uk/issues/2026-08-21/)（内容由 AI 辅助创作，可能存在错误）
