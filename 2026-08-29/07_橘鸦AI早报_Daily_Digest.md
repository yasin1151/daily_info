
# 橘鸦 AI 早报 · 2026-08-28 摘要

本期 22 条，精选 10 条高价值动态（已过滤促销/低价值产品更新）。

## 产业动态

**1. 消息称英伟达同意 129 亿美元收购 Hugging Face**
知情人士向 The Information 透露，英伟达已同意以 129 亿美元收购开源模型托管平台 Hugging Face，借此在开源 AI 领域建立立足点、对抗闭源厂商自研芯片趋势并重返云服务市场。HF 年化收入约 1.5 亿美元，收购价约为远期收入 80 倍；此前 HF 曾拒绝英伟达 50 亿美元投资要约，上轮融资估值 45 亿美元。双方尚未官方回应。
影响：若成真，开源模型分发与社区生态的核心平台将易主，是近年开源 AI 领域最大交易。
链接：https://www.theinformation.com/articles/nvidia-agrees-buy-open-source-model-repository-hugging-face-12-9-billion

**2. 英伟达暂停与 AI 云服务商的收益分成交易**
WSJ 援引知情人士：英伟达暂停了"向 AI 云服务商提供信用支持、换取营收分成"新融资计划的部分交易，内部员工担忧该模式引发反垄断审查及干预客户业务的观感。项目 7 月推出、上周叫停，后续可能调整或并入其他业务；英伟达发言人则回应"该模式仍在正常运作"。
影响：英伟达在云厂商渠道的捆绑式合作正承受监管压力。
链接：https://www.wsj.com/tech/nvidia-pauses-revenue-sharing-deals-with-ai-cloud-companies-9c71454e

## 模型发布

**3. Gemini Omni 1.1 Flash 上线：视频生成可控性大升级**
谷歌推出 Omni 1.1 Flash，核心变化：场景延展可参考最多 10 秒前序内容（此前仅约 1 秒），更易保持人物/场景/叙事连续；新增首尾帧控制与最长 3 秒视频参考；新增 360p 草稿模式（比 720p 快最多 60%、成本约 1/3），成片可输出 1080p 或 4K，累计上限 40 秒。已上线 Gemini API、AI Studio、Flow。
影响：视频生成从"抽卡"走向可控创作，试片成本显著下降。
链接：https://blog.google/innovation-and-ai/technology/developers-tools/build-with-gemini-omni-1-1-flash/

**4. fal 发布 H3 Max：吞吐是 MiniMax H3 官方端点的 35 倍**
fal Research 基于 MiniMax H3 后训练并协同设计推理栈的视频生成模型 H3 Max：生成 5 秒视频耗时不到 3 秒，吞吐约为官方 H3 端点 35 倍；fal 及第三方评估显示其在总体质量、提示词理解、美感维度均排第一。已在 fal Playground、Agent 和 API 上线，首周五折。
影响：开源视频生成在速度与质量上同时拉高标杆。
链接：https://blog.fal.ai/introducing-h3-max-by-fal/

**5. 蚂蚁百灵发布金融增强模型 Ling-3.0-flash-Fin**
基于 Ling-3.0-flash 开发，总参 124B、激活 5.1B，官方称多项金融基准测试表现突出，通用能力评分亦提升。已上线 Vercel AI Gateway（限时免费至 9/25）和 OpenRouter（免费一个月），**下周开源模型权重**。
影响：国产金融垂类模型 + 即将开源，可跟进测试。
链接：https://openrouter.ai/inclusionai/ling-3.0-flash-fin:free#providers

## Agent / 开发工具

**6. Anthropic 推出 Model Hardware Standard（MHS）研究预览**
面向科研实验室的硬件操作标准：通过标准化驱动和 read/write 基础指令，让 Agent 发现和控制显微镜、移液设备、机械臂等，支持 MCP/CLI/API 编排多台设备，官方称可将硬件集成从数周缩短至数小时。已在药物实验、显微成像、机器人协作、量子激光稳定等场景测试；尚未开源，将先完善物理安全评测。
影响：Agent 从操作软件走向操作物理世界的关键一步，值得长期关注。
链接：https://www.anthropic.com/news/model-hardware-standard-research-preview

**7. AISI 开源评估算力优化工具 optstop**
英国 AI 安全研究所推出开源 Python 工具：分层贝叶斯模型追踪可信区间，达到预设精度即停止采样，否则继续并动态要求更多数据；官方测试称可节省 57%–97% 的计划测试量且不影响评分。
影响：长评估任务的算力成本可大幅压缩。
链接：https://github.com/UKGovernmentBEIS/optstop

## 产品与平台

**8. OpenAI：ChatGPT Work/Codex 额度重置 + Luna Reserve 备用额度**
Codex 负责人 Tibo 宣布所有 ChatGPT Work 和 Codex 用户用量已重置（此前 5 小时限制导致用户无法消耗完额度，遭吐槽）。同日 OpenAI 推出 Luna Reserve：常规额度耗尽后提供仅限 GPT-5.6 Luna 的独立备用额度（有上限），当前仅部分个人 Plus/Pro 账户，不含 Business/Enterprise、普通 Chat 与 API。
影响：与你日常查 Codex 配额直接相关——额度用尽后有保底可用，5h 限制已重置。
链接：https://help.openai.com/en/articles/20001499-luna-reserve-in-codex-and-chatgpt-work

**9. Hugging Face 发布开源双足机器人 Microduck**
Pollen Robotics 出品：高约 25cm、重 800g，15 电机 + 摄像头 + LiDAR，出厂自带行走、轮滑等 7 种预训练行为；SDK 与完整强化学习训练栈以 Apache 2.0 开源，支持仿真训练后部署真机。预购 399 美元，联合创始人 Thomas Wolf 称销售额已破 100 万美元。
影响：低成本开源机器人 + 完整训练栈，机器人开发门槛大幅降低。
链接：https://pollen-robotics.com/microduck/

## 技术与洞察

**10. 谷歌 DeepMind 试运行"全球首个"前沿 AI 双盲评估**
利用机密计算创建隔离环境：评估者不可见模型权重、谷歌无法获取外部测试提示词，以防范基准污染。目前对 Gemini Flash Lite 试运行，合作方包括新加坡 AI 安全研究所和 MLCommons。
影响：针对 benchmark 污染争议的直接回应，或推动行业评测范式改变。
链接：https://deepmind.google/blog/piloting-the-worlds-first-double-blind-ai-evaluations/

---
已标记该期已读。来源提示：本早报由 AI 辅助创作，个别细节可能存在偏差，重大事件建议以原文链接为准。
