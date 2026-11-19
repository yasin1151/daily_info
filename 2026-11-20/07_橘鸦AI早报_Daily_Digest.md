
**橘鸦 AI 早报 · 2026-11-19**（26 条，精选 9 条）

---

**1. Google 发布 Gemini 4 Neon：卡在 Carbon 和 Hydrogen 之间的“主力干活型”模型**
定位复杂软件工程与科学工作流，支持四档思维调节、100 万 token 上下文。官方称它在 Artificial Analysis Coding Agent Index 排第一，默认 high 档单任务成本比 Carbon 低 32%。API 定价为每百万输入 3 美元、输出 15 美元（缓存输入 0.15 美元），已在 AI Studio 付费层、Gemini API、Pro/Ultra 订阅的 Gemini 应用和 Antigravity 上线。
*值得注意：模型线已经密到用元素名排队了，Neon 的关键卖点不是分数而是“便宜 32% 还能打”，明显是冲着日常编码主力位来的。*
🔗 https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/

**2. Google Genie 4 开放：世界里能实时改天气、加角色，还能对话配音**
AI Ultra 订阅者可玩，Pro 会员排队。首次带环境音效和角色对话，支持输入文字实时编辑环境，单次探索从 60 秒延长到 3 分钟，可串联多个世界。所有产出带 SynthID 水印，体验期内不消耗点数但有日限额和高峰排队。
🔗 https://deepmind.google/blog/genie-4-is-now-available

**3. DeepSeek 改搜索计费：模型自己决定联网，不再单独收钱**
11 月 18 日 12:00 起，模型调用触发的服务端搜索和网页抓取不再单独计费，只按 token 计。客户端直接调 Search/Fetch API 则 5 元/1000 次成功请求，失败、无结果、超时不计费。
*这是很实在的一步：把“要不要联网”变成模型内部的决策成本，而不是用户的心算题。*
🔗 https://api-docs.deepseek.com/zh-cn/guides/search/

**4. 腾讯混元开源 Hy4 flash：224B 总参、每 token 只激活 12B、1M 上下文**
指令版、FP8 量化版、预训练基座版三个权重全放，GitHub / HuggingFace / ModelScope / GitCode 都能下。支持文本加图像输入。官方顺带说 Hy4 完整版开源“正在加速推进”。
🔗 https://huggingface.co/tencent/Hy4-flash

**5. OpenAI 详解 Codex 沙箱：默认断网、按域放行、不用容器**
直接用系统机制在用户本机限制命令的文件和网络权限：macOS 走 Seatbelt，Linux 用 bubblewrap + seccomp，Windows 正迁到微软的 MXC 库。默认允许改工作区源码但 .git 和 .codex 只读，网络默认关闭，需要时走代理规则配白名单域名，命中的请求不用逐次审批。
*对天天让 Agent 在自己机器上跑的人来说，这篇比任何 benchmark 都更值得读。*
🔗 https://openai.com/index/inside-the-codex-sandbox/

**6. OpenAI 拿模型设计芯片：Jalapeño 流片验证通过，AMD GPU 电路 PPA 最高改善 14%**
模型提的电路优化方案在 OpenAI 首款定制推理芯片 Jalapeño 上通过实际芯片验证，向量单元和矩阵单元标准单元面积分别减约 13% 和 10%。与 AMD 合作中，旗舰 GPU 部分电路在功耗性能面积上最高改善 14%，耗时不到 5 个月，部分改动已送厂。另与 Synopsys 合作训练 GPT-Synopsys 学习用 EDA 工具。
🔗 https://openai.com/index/advancing-chip-design-with-our-models

**7. Arena 上线 Agent Arena Index：1090 万真实会话，Claude Fable 5.2 Max 以 1463 分登顶**
同步推出 Work、Coding、Chat 等六个细分指数，并引入可跨时间比较的新分数缩放（称不影响排名）。Claude Fable 5.2 (Max) 领先第二名 134 分，拿下五个细分指数第一；Tool Use 指数第一是 Claude Sonnet 5。
🔗 https://arena.ai/blog/introducing-the-agent-arena-index

**8. Anthropic 上市前被“背刺”：AI 安全圈联署质疑其安全形象**
Center for AI Safety 联合多方发布 MisAnthropic 声明，指责其一边警告递归自我改进 AI 的风险、一边竞相开发这种技术，并借安全形象扩张权力、削弱安全承诺、游说有利于自己的监管。签署者包括图灵奖得主 Judea Pearl、HuggingFace 联创 Thomas Wolf。CAIS 执行主任 Dan Hendrycks 称多个安全团体私下认同但怕影响人脉和经费不敢署名。
🔗 https://safe.ai/news/anthropic-is-not-a-safe-ai-company

**9. 国内 AI 应用数据齐发：微信小微 DAU 3000 万、WorkBuddy 日活破千万、豆包工作 3 个月 DAU 800 万**
腾讯 Q3 财报披露小微测试范围扩大、DAU 达 3000 万，用定制 WeLM 模型、推理成本极低，未来部分推理要下放到设备端；WorkBuddy 日活超 1000 万，日消耗 token 超 100 万亿，马化腾称按 token 口径已是国内最大 AI 应用。豆包工作上线三个月 DAU 破 800 万、企业 ARR 破 20 亿元。
🔗 腾讯财报 PDF / 豆包工作公众号

---

**另外三条值得一提的**
- **GPT-6.2 口碑翻车后续**：多位博主差评同时发布被质疑串通，博主 Matt Shumer 解释是解禁时间撞车、“模型本身不行”；OpenAI 员工 Tibo 直接回“我确实认为他们在一个 Slack 频道里协调过”。Tibo 另解释博主与普通用户观感差异：视频拍于上周，模型最后 3-4 天改动很多且没重测。
- **白宫拟要求美企在自家网站披露使用中国 AI 模型**（路透独家），思路是用公众压力替代新限制，Airbnb（用 Qwen 驱动客服）、Anysphere、DoorDash 已被国会问询。
- **两个运维雷**：NVIDIA 621.24 驱动闲置时 NVDisplay.Container.exe 每小时写约 30GB 日志（因整体重写而非追加），会显著折损 SSD 寿命，官方未承认；Nginx 修 10 处漏洞，其中两处 HTTP/2 漏洞可未授权 RCE，1.31.9 / 1.30.7 已修。

已标记该期（#7516）为已读。
