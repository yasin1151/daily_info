
# 橘鸦AI早报 2026-08-26 摘要

## 🔥 要闻

**1. 阿里千问预告今晚 23:00 开源 Qwen3.8-Flash-Next**
基于下一代 Qwen4 架构的多模态 MoE 模型，权重尚未放出，官方称提前发布是为社区迎接完整 Qwen4 家族做准备。影响：Qwen4 架构首次公开亮相，多模态 MoE 路线值得关注。
🔗 https://huggingface.co/Qwen/Qwen3.8-Flash-Next

**2. OpenAI 公布自研推理芯片 Jalapeño 实测数据**
专为语言模型与交互式 Agent 设计：InferenceX 基准上峰值每瓦性能达对比系统 1.5–1.9 倍，端到端延迟降低 1.7–3.6 倍（在 GPT-OSS 120B、DeepSeek R1 670B、Kimi K2.5 1T 上实测）。计划年底内部署，第二代已深入开发。影响：OpenAI 算力自主化提速，推理成本结构可能生变。
🔗 https://openai.com/index/jalapeno-first-results/

**3. Codex 重置付费用户用量，恢复 Plus/Business 5 小时限额**
官方为平滑算力负载恢复 5 小时限额（Pro 不受影响），并重置了 Plus/Team/Pro 用户额度；桌面端开始原生显示第三方模型、会话不再按 provider 隔离（CLI 仍隔离）。影响：用 Codex 的同学注意周额度重新计起。
🔗 https://x.com/thsottiaux/status/2092058556707344708

## 🛠 开发生态

**4. ChatGPT Work 新增代用户登录网站能力**
网页端+移动端可用 computer/browser 代为登录，全程看不到用户名密码；今日起向 Plus/Pro/Business 逐步开放。影响：Agent 自主执行网页任务的关键一环（登录墙）被打通。
🔗 https://x.com/ChatGPT/status/2092366554965107164

**5. OpenAI 推出 WebMCP 支持 + 黑客松**
ChatGPT 桌面内置浏览器与 ChatGPT Sites 支持 WebMCP 实验性开放标准——网站可直接向 Agent 暴露结构化工具；联合 Google Chrome、Cloudflare、Shopify、Vercel、Render、Netlify 启动 10 天挑战赛。影响：Web 层 Agent 工具互操作标准在快速推进。
🔗 https://openai.com/webmcp-challenge/

**6. ChatGPT 定时任务支持事件触发**
Plus/Pro 用户可让任务在 Slack、Gmail、GitHub 出现变化时自动响应，不再只限固定时间表；免费用户陆续开放（最多 3 个），支持分享任务模板。
🔗 https://x.com/ChatGPT/status/2092335329110004140

**7. Cursor 调整计费：Auto 改为按路由模型计费**
Auto 从统一价改为按实际路由模型计费，多数请求价格将上涨；同步上调自有模型套餐额度，并再次永久提高 Grok 4.6 包含额度。影响：Cursor 重度用户成本可能上升。
🔗 https://x.com/cursor_ai/status/2092281297271996712

## 🤖 产品与 Agent

**8. 豆包工作正式发布（可领 30 天订阅）**
面向生产力场景的 Agent 产品：自主拆解任务、调用工具完成写文档/表格/PPT，可操作电脑与浏览器、过程全程可见可接管，与飞书深度打通。即日起下载电脑版领 30 天订阅权益。
🔗 https://www.doubao.com/work

**9. Anthropic 统一 Claude 对话与 Cowork 记忆**
聊天与 Claude Cowork 共用同一份记忆，云端任务可直接沿用对话背景；自动记录新话题，可逐条查看/编辑/重置，Free/Pro/Max 默认开启。影响：Claude 系 Agent 任务连续性大幅增强。
🔗 https://claude.com/blog/claudes-memory-works-everywhere-and-you-decide-whats-in-it

**10. Perplexity 发布本地 Agent「Portable Computer」**
首发支持 NVIDIA DGX Spark，内置自研 PPLX 27B（也支持 Qwen 3.8 27B），敏感文档本地处理，必要时授权调用云端模型；向拥有 DGX Spark 的 Pro/Max 用户开放。
🔗 https://x.com/Perplexity_AI（原文见橘鸦早报 #19）

## 📦 模型与行业（简讯）

- **IBM 开源 Granite 4.2**：3B/8B/30B，面向企业 Agentic AI，512K 上下文，Apache 2.0，支持思考/不思考/低努力三模式；同推 Granite Speech 5.0 Turbo（470M）。
- **腾讯开源 WeMM-Embedding**：2B/4B/9B 多模态嵌入，基于 Qwen3.5，支持文本/图像/视频/交错输入，Apache 2.0。
- **Claude Code 争议**：Shopify CEO Tobi Lütke 称考虑禁用 Claude Code——只认 CLAUDE.md 会造成团队"split brain"；Anthropic 员工回应将支持 AGENTS.md 等通用配置，并承认维护成本不低。
- **苹果发布新款 Mac mini（M6）与 Mac Studio（M5 Ultra）**，强调设备端 AI 推理与雷雳 5 集群能力。

---
已跳过：ChatGPT Stickers、Command Code 支付宝、商汤生图 Token Plan、OpenCode 5 美元优惠下架、Stability AI 融资等低优先级/广告类条目。最新一期（8-26）已标记已读。
