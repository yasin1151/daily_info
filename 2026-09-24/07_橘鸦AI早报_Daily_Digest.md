
已抓取并标记已读。以下是 2026-09-23 期摘要：

---

# 橘鸦AI早报 2026-09-23 摘要

来源：https://daily.juya.uk/issues/2026-09-23/

## 1. Anthropic 发布 Claude Opus 5.5，直接降价＋提高订阅额度（要闻）
官方称其在多数工作上已达 Claude Fable 5.1 水平，提升集中在 Agentic 编程、计算机操作、知识工作与长任务。API 输入/输出降至每百万 token **4 美元 / 20 美元**，缓存读取降至 0.20 美元；典型任务整体成本比 Opus 5 低约 40%，输出速度快 30% 以上，另有最高 2.5 倍速的 Fast Mode。Pro、Max、Team 及按席位的 Enterprise 同步提高五小时额度，部分用户还拿到一次可自行择时使用的额度重置。
安全上有两个需要留意的行为变化：这是首个在网络安全、生物、反蒸馏方面采用接近 Fable 5.1 级防护的 Opus 模型，**多数网络安全任务会被转交给 Opus 4.8**，涉及前沿 LLM 开发的部分请求（如机器学习加速器内核）会回退到 Opus 5。Thinking 始终开启，Claude Code 默认 medium effort，官方建议不要再堆"think carefully"式提示，而是直接给全任务、完成标准和何时该停下来问人。
Sonnet 5.5 与 Haiku 5.5 将在未来几周跟进。
链接：https://www.anthropic.com/claude-opus-5-5 ｜ https://claude.com/blog/what-a-task-costs-on-opus-5-5

## 2. OpenAI 发布 GPT-6 Sol 和 GPT-6 Luna，价格降 50%（要闻）
把 GPT-6 Astra 的部分训练方法下放到更快更便宜的档位。**Sol 每百万输入/输出 2 / 10 美元，Luna 为 0.10 / 0.50 美元**，较 GPT-5.6 促销价整体低 50%。内部事实评测中 Sol 的错误约为上一代的一半。
另一半重点是提示缓存：默认缓存命中率提高，缓存输入最高享 90% 折扣，新增缓存监控、诊断、显式断点和预热，开发者可在调整推理强度或工具可用性时尽量保留已有缓存——GitHub 称这让 Copilot 需要重新处理的 prompt token 比此前基线减少一半以上。两款已进入 ChatGPT Work、Codex 和 API，普通 Chat 界面尚未提供，Free/Go 用户可在桌面应用用 Luna。
链接：https://openai.com/index/introducing-gpt-6-sol-and-luna/ ｜ https://openai.com/index/better-prompt-caching-for-gpt-6/

## 3. OpenRouter 推出 Batch API，70 多款模型支持异步批处理（开发生态）
面向不需要即时返回的批量任务：多条请求放进一个 JSON 请求体提交，服务商在 24 小时窗口内安排处理，再查询状态取结果。**输入和输出 Token 通常按标准价五折计费**（折扣因模型和服务商而异，工具调用仍按标准费率）。两周测试期完成超过 23 万个批次，中位完成时间 7 分钟，90% 在一小时内完成。
价值在于省掉自建队列、限流和重试的那层工程——评测、批量标注、内容生成这类非实时任务可以直接半价跑。
链接：https://openrouter.ai/blog/announcements/batch-api/

## 4. 阶跃星辰开源终端编程智能体 Step Code v0.1.0（开发生态）
MIT 许可，支持 macOS、Linux 和 WSL，可在终端内完成代码阅读、编写、修改、调试、执行到交付的闭环。通过上下文管理、工具调用和 subagent 并行执行降低 token 消耗，并提供长任务托管、定时执行、StepPage 静态网站发布、MCP、Agent Skills、插件及多 Agent 编排。
需要注意的取舍：**产品默认只内置 Step provider**，需 Step Plan 订阅或 Step Platform API Key 登录，不是任意模型插拔的框架。
链接：https://github.com/stepfun-ai/Step-Code

## 5. 腾讯混元发布专业级生图模型 Hy Image3.5 preview（模型发布）
支持文生图、图生图、多轮对话编辑，最多 5 张参考图，最高 2K 输出。官方称通过架构简化、高效蒸馏、文本与图像分支解耦部署，对比 Hy Image3.0 综合能力提升约 30%，重点改善**文本渲染与编辑一致性**（生图最长期的两个痛点）。
已上线元宝、WorkRally、OnSolo、Miora、WorkBuddy 和 ima；可通过腾讯云 TokenHub、MPS、云点播调用 API，**2K 图像每张 0.15 元且仅对输出图片收费**——这个计费口径对批量海报/电商图很友好。
链接：https://hy.tencent.com/research/hy-image35-preview

## 6. 蚂蚁百灵开源 Ming-Image-0.1-Design 系列（模型发布）
两款 **60 亿参数** 图像模型（含 Layer 版）加两项 Agent Skill：Ming-Image-0.1-Design 可根据提示生成界面、信息图、海报并输出透明背景图；Design-Layer 能把扁平设计图**拆成 2 至 9 个可独立编辑的 RGBA 图层**。两个 Skill 分别面向"设计稿转网页代码"和"幻灯片图片转可编辑 PowerPoint"。
MIT 许可，权重已开放下载，官方称在 Artificial Analysis 的 UI/UX Design 榜单上位列开放权重模型第一。60 亿这个量级意味着消费级显卡可以本地跑。
链接：https://github.com/inclusionAI/Ming-Image

## 7. Kimi Browser Extension 上线，可把网页操作录成 skill（产品应用）
原名 Kimi WebBridge，现已上官网和 Chrome 商店。用户点工具栏图标，在侧边栏登录后通过对话让 Kimi 导航网页、填表单、完成任务；**重复性操作可录制一次步骤并保存为 skill，供下次直接执行**。扩展也可配合本地 Agent 使用，通过本地服务操作现有的 Chrome 或 Edge。
这条的价值不在"能点网页"，而在把浏览器 Agent 从每次重新推理改成录制-回放：重复流程的成功率和成本都会明显改善。
链接：https://www.kimi.ai/products/kimi-browser-extension

## 8. 火山引擎推出 Seedance 2.5 Draft 样片模式（产品应用）
先用 480P 生成样片确认构图、动作，再用样片 ID 生成 1080P 成片，成片复用样片的生成条件，镜头结构和运动表现尽量保持一致（局部细节可能变）。企业可在 API 创建任务时把 `draft` 设为 true，C 端可在即梦选"Seedance 2.5（样片模式）"。
官方算例：不含输入视频、生成 5 秒 1080P、尝试 4 次才选定片段的情况下，**可节约 57% 成本，生成速度提升近一倍**。AI 视频最大的痛点就是试错成本，"低清试稿＋高清定稿"很可能成为标准工作流。
链接：https://mp.weixin.qq.com/s/Cq42y7dJgy92LtXevulXlA

## 9. 阿里三线推进 Agent 入口：Qwen Intelligence / Qwen4 路线图 / QwenBook
- **Qwen Intelligence**：面向手机场景的全栈方案，提供 Mobile Planner Agent（规划）、Mobile-Use Agent（操作）、Mobile Creative Agent（影像创作）三类 Agent，不参与硬件生产，已与荣耀 Magic OS 结合落地。
- **Qwen4 路线图**（云栖大会披露）：Qwen4-Max、Flash、Plus、27B 四款标注"即将推出"，已基于新一代架构进入训练；后续 Qwen4.5 与 Qwen5 计划把参数规模扩展到 **5—10T**。
- **QwenBook**：无影团队展示定位"原生智能体电脑"的演示真机，平板＋键盘触摸板形态，圆形小背屏和千问专属键，基于安卓，多指滑动切换 AI 智能体界面与传统桌面。官网招募 100 名"Day One"体验官（10 月 31 日截止），完整产品预计 2026 年底或 2027 年初发布。现场版本主要用于展示理念，非最新完整版本。
链接：https://www.qwenintelligence.com/ ｜ https://www.qianwenai.com/product/qwenbook

## 10. 两条行业侧信号
**OpenAI 提出第三方安全评估的重点与原则**：承诺让独立机构深度访问模型训练、评估、部署环节，核查安全论证的证据并判断防护是否有效；面向私营和非营利机构长期开展（数周至数月），可并行进行，部分工作可在部署前完成但不绑定单次产品发布。这是把"安全承诺"往可核查方向推的一步。
**TypeSafe AI 因需求激增暂停 Jev 新用户注册**：已注册用户不受影响，恢复时间未公布。AI 编码工具的需求端已经热到供应商要靠限流保服务质量。
另有 **阿里云成为 Omacom 基金会创始企业赞助人**：承诺连续三年每年 100 万美元、合计 300 万美元支持 Omarchy，并共建 Omarchy China（本地 CDN、托管、社区支持），双方还计划让 Omarchy 适配即将推出的 Qwen Book。
链接：https://openai.com/index/priorities-principles-third-party-assessments/ ｜ https://x.com/typesafeai/status/2102281508950307159 ｜ https://zh.omarchy.org/news/2026/09/alibaba-cloud-joins-as-founding-corporate-patron/

---

本期略过：智谱 GLM Coding Plan 双节促销（纯营销活动）、PixVerse R2 实时世界模型（目前仅有两条推文，无技术细节）、Artificial Analysis 九语种 TTS 榜（榜单更新，普通话榜 Inworld Realtime TTS-2 以 1185 Elo 居首）。

已标记第 6154 篇文章为已读。
