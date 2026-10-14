
# 橘鸦AI早报 2026-10-14 摘要

**本期共 27 条，以下为 10 条高价值信息。**

---

**1. Google 全球开放 Gemini 4 Argon（要闻）**
Gemini 4 Argon 向全球开放，AI Pro 用户在 Gemini App 和搜索 AI Mode 可用，Ultra 用户额度更高、还能用 Antigravity 桌面 App/CLI 与 AI Studio。开发者必须开付费层级，免费档和 Pro 档都不含。
**值得关注**：API 优惠价每百万 token 输入 2 美元、输出 10 美元，**12 月 1 日起翻倍**——想批量跑任务的应在此之前压测成本。macOS 版 Gemini App 还内置了 Antigravity 编码界面，等于把编码 Agent 直接塞进消费端应用。
https://deepmind.google/blog/introducing-gemini-4-argon/

**2. Anthropic 弃用 Git，自建版本控制系统 Scion（技术与洞察）**
Anthropic 用 5 个月自建版本控制系统，把超大单一代码库从 Git 完全迁走，原因是 Claude 大量写代码后，面向人类开发者设计的 Git 基础设施成了瓶颈：**每日合并的代码变更从 5 月的约 2500 次涨到 9 月的 30000+ 次**。
**值得关注**：Scion 假设客户端永远在线，把提交/合并/历史查询挪到服务端，CPU 和内存需求降到旧 Git 镜像的约 1/200，CI 取代码从分钟级到秒级。官方明确说这**不是通用 Git 替代品**——但它揭示了一个信号：AI 生成代码的量级正在倒逼开发基础设施重做。
https://www.anthropic.com/engineering/redesigning-source-control

**3. Character.ai 申请破产保护（行业动态）**
AI 角色聊天平台 Character.ai 已申请美国破产法第 11 章保护，将在法院监督下出售全部或绝大部分资产。法院文件显示，**2026 年 1–8 月算力支出 5610 万美元，到 8 月仍每月亏损 800–900 万美元**。迪士尼已达成协议，以 2000 万美元换部分 IP 的非独占永久许可。
**值得关注**：这是"AI 应用层经济学不成立"最直白的一次公开暴露——用户量不等于收入，算力账单才是。平台服务与订阅计费暂时不变，但若无买家接手将逐步关闭。
https://blog.character.ai/an-update-on-character-ai/

**4. Artificial Analysis 新增缓存命中率与每任务成本榜单（技术与洞察）**
AA 公开了所有追踪端点的缓存命中率，并给开放权重模型加了按供应商划分的 Cost per Task 数据。
**值得关注**：同一款 **GLM-5.3 (max) 在不同供应商间任务成本从 0.92 美元到 8.68 美元，差约 9 倍**；21 家供应商 25 个端点上缓存命中率跨度 41%–100%。即使命中率接近，缓存输入是否打折也直接影响成本——选供应商前值得先查这张表。
https://artificialanalysis.ai/models/glm-5-3/providers

**5. Arena 推出 Agent 版 Max 模型路由器（产品应用）**
基于超 250 万次真实 Agent Arena 会话，按任务复杂度/类型/成本动态选模型，覆盖聊天、工作、编程。Arena 称 Max 实测期间位列 Agent Arena 第 1，**每任务成本中位数 3.27 美元，比当时第 1 的 Fable 5.1 (Max) 表现高 0.3%、成本低 37.5%**。
**值得关注**：路由层正在从"省钱小技巧"变成有独立排行榜的竞争赛道。
https://arena.ai/blog/max-router-tops-agent-arena

**6. Fish Audio 发布开放权重 TTS 模型 Drama 3（模型发布）**
支持自然语言控制情绪、节奏和声音，可把耳语、强调等表达限定到单个词，支持 83 种语言，已上线网页/iOS/Android/API，权重可下载自部署。**API 价格到 11 月 12 日从每百万字符 50 美元降到 10 美元**。
**值得关注**：授权是门槛——研究和非商业免费，年收入低于 50 万美元可免费商用，但对外提供 TTS/语音克隆/推理 API 仍需单独许可。
https://huggingface.co/fishaudio/drama-3

**7. Liquid AI 发布端侧开放权重模型 LFM2.5-24B-A2B（模型发布）**
总量 240 亿参数、每 token 仅激活 20 亿，面向端侧 Agent 的工具调用和多步任务。**上下文窗口从前代 32,768 扩到 131,072**，回答前会输出显式推理过程。权重已在 HF 开放，支持 llama.cpp / MLX / vLLM，已上 OpenRouter。API 定价极低：输入 0.10 美元、缓存输入 0.05、输出 1 美元（每百万 token）。
**值得关注**：笔记本/PC 本地跑 Agent 的工具调用能力，正在被这类稀疏激活模型快速拉平。
https://huggingface.co/LiquidAI/LFM2.5-24B-A2B

**8. IDC：英伟达中国 AI 芯片份额降至 34%（行业动态）**
据路透社援引 IDC，2026 上半年英伟达在中国数据中心 AI 芯片市场份额降至 **34%**，AI 加速器出货量同比降 44% 至 67.8 万颗；同期华为从 30 万+ 增至 **57.2 万颗，份额 28%**。
**值得关注**：国产替代已经不是趋势判断，而是出货量数据。
https://www.reuters.com/business/retail-consumer/nvidias-china-ai-chip-share-falls-huawei-closes-gap-report-finds-2026-10-13/

**9. 阿里千问连发 Agent 与硬件（产品应用）**
个人 Agent「千问 Go」内嵌千问 App、限时邀测（专业会员优先）；同时**现货开售 AI 眼镜 N1 / N1 Pro 和 AI 耳夹式耳机**——N1 Pro 支持心率血氧皮温监测、眼动交互、虹膜核身支付；耳机由 Bose SoundDesign 调音，支持 89 种语言翻译、可唤起 Qoder 全双工语音推进任务。
**值得关注**：国内大厂开始把 Agent 从 App 推入口延伸到眼镜/耳机等全天候入口。
https://mp.weixin.qq.com/s/MhlweW9-Ia6jizS3zf7OMQ

**10. 两条安全与情报类动向（技术与洞察 / 行业动态）**
- **AISI 开源 Transect**：把复杂 Agent 评估记录转成交互式时间线（活动分类、token 用量、人工干预、子 Agent 活动），可跳回原始记录核查，而不是只看最终得分；基于 Inspect Scout 构建。https://github.com/AI-Safety-Institute/transect
- **OpenAI 工程师因在旧金山办公室高管会议室暗藏录音设备被捕**，被控截获口头通信，OpenAI 已解雇该员工并移交 FBI；官方称无迹象表明模型权重、源代码或客户数据被外传。https://www.justice.gov/opa/pr/saudi-national-arrested-installing-surreptitious-audio-recording-device-openai

---

其余略过项（低价值/常规更新）：Command Code GOAT 限时额度、MiniMax 入驻天猫、Antigravity 科研免费申请、Cursor Origin 集成、Google Play 私人应用、Llama Windows 桌面应用、阶跃 STEPX Neo 先行版手机、Manus × OPPO ColorOS 17、Exa 年化收入破亿、NVIDIA 法国生态、Anthropic 大阪数据中心、字节 Seed 安全与对齐部门。

已标记该期（2026-10-14）为已读，无剩余未读文章。
