
# 橘鸦AI早报 2026-08-25 摘要

## 开发生态 / Agent

**1. 字节整合 TRAE 与扣子进豆包体系，本周或推"豆包工作"**
TRAE 与扣子团队整体并入豆包体系：TRAE Work 与扣子并入豆包工作场景能力，TRAE IDE/CLI 保留为独立编程产品线。据称最快本周推出统一 AI 办公产品"豆包工作"，并与飞书深度整合。这是字节在 AI 办公/Agent 赛道的一次大整合，此前分散的编程、工作流、办公产品线将统一入口，对使用 TRAE/扣子的开发者影响直接（官方称现有用户权益不受影响）。
https://mp.weixin.qq.com/s/ZgA2HZIgkNsE5HQkC40Sgw

**2. NVIDIA Vera Rubin NVL72 实测：Agent 负载吞吐最高提升 30 倍、token 成本降 35 倍**
NVIDIA 官方博客公布 Vera Rubin NVL72 实测数据：运行 Agent 工作负载（SemiAnalysis AgentX 真实编码轨迹，DeepSeek V4 Pro 模型）时，较 GB300 NVL72 每兆瓦吞吐量最高提升 30 倍、每百万 token 成本最高下降 35 倍。已进入全面量产。注意：官方自述为早期数据、尚待 SemiAnalysis 审查，且未计入 Vera CPU 工具调用性能——数据本身有营销成分，但方向性信号明确：Agent 推理负载的硬件代际跃迁已经来了。
https://blogs.nvidia.com/blog/vera-rubin-nvl72-efficiency-ai-agents/

**3. NVIDIA Groq 3 LPX 全面投产，主打 Agent 超快推理**
作为 Vera Rubin 平台的扩展，Groq 3 LPX 交互式推理加速器全面投产：官方基准显示运行 Gemma 4 31B（10 万 token 上下文）时输出达 3400 token/秒，为最接近替代品的 4 倍；Nebius 成为首个采用的 AI 云服务商。
https://blogs.nvidia.com/news/nvidia-groq-3-lpx-now-in-full-production-with-world-class-speed-for-agentic-ai

## 模型发布

**4. Agnes AI 开源 Agnes 2.5 Pro Alpha：Qwen3.5-397B 后训练，Apache 2.0**
397B 参数多模态推理模型开源，支持 1M token 上下文、65536 输出 token、图像理解、扩展推理与工具调用。官方称在 Artificial Analysis 八项评测中六项优于基座 Qwen3.5-397B。开源可商用，适合长上下文/工具调用场景自部署。
https://huggingface.co/Agnes-AI/Agnes-2.5-Pro-Alpha

**5. 阿里 Wan3.0 视频模型正式上线，支持文档输入、API 限时 7 折**
结束公测正式上线：单次生成最长 30 秒视频，首次支持输入 doc/xls/ppt/pdf/md 文档，指令遵循与跨镜头一致性提升。已在阿里云百炼、万相官网、千问等 8 个平台开放，API 按分辨率定价 0.3-1.2 元/秒，部分平台限时 7 折；井英科技、美图 RoboNeo 等已接入。
https://mp.weixin.qq.com/s/peeeU6cBz4AaROvFe1zqQQ

**6. MiniMax M3/M2.7 等模型 14 天免费无限制访问（8/24-9/6）**
MiniMax 与 GMI Cloud 联合推出：M3、M2.7 模型及 Speech 2.8、Music 3.0 功能 14 天免费无限调用（有反滥用与速率限制），用 GMI API 密钥即可。开发者在 9 月 6 日前可低成本实测 M3 效果。
https://www.gmicloud.ai/minimax-week

## 产品应用

**7. Anthropic 重写 Claude 流式渲染器：长回答平滑度提升约 4 倍**
Web/桌面端流式渲染器重构，只渲染仍在变化的内容：慢速笔记本长回复卡顿减少 9 倍、最长冻结时间缩短 4.5 倍，120Hz MacBook 上可全程维持 120fps。对长输出场景的体感改善明显。
https://x.com/ClaudeDevs/status/2092006814804214163

## 行业动态

**8. 小米发布玄戒三款自研芯片，展出 AI Cube 原型机**
O3（AI 旗舰 SoC，安兔兔 522 万、首发 LPDDR6）已规模量产，9 月搭载小米 18 Fold 与小米平板 9 Pro Max 上市；O100（行业首颗 6nm 3D 晶圆级堆叠 AI 加速芯片，1.22TB/s 近存带宽）与 D100（国内首款 3nm 智驾芯片，最高 160GB 统一内存）明年商用。现场展出集成三芯、150W 性能释放的 AI Cube 原型主机（未定价）。
https://www.ithome.com/0/993/587.htm

**9. 传 Nvidia 拟数十亿美元投资 Perplexity，估值超 300 亿美元**
双方还在磋商技术授权协议。Perplexity 年化营收已从年初不到 2.5 亿美元增至 7.5 亿美元以上。若成行，Nvidia 将同时握有 AI 搜索流量入口与推理硬件需求，补齐其在消费端 AI 的布局。
https://www.reuters.com/technology/nvidia-discusses-perplexity-investment-30-billion-plus-valuation-information-2026-08-24/

**10. Mistral AI × 沙特 PIF 子公司 HUMAIN：中东主权 AI 基建，规模数亿欧元**
双方将部署 AI 基础设施、本地化先进模型（初期聚焦网络安全与语音），并开发阿拉伯语表现强劲的前沿模型，探索使用 HUMAIN 数据中心。欧洲模型厂商继续向主权 AI 资本靠拢，与中东资金绑定成为重要融资路径。
https://mistral.ai/news/mistral-x-humain/

---
另：SpaceXAI 宣布部署 NVIDIA Vera CPU 并计划明年 Q4 发射"太空版"Vera Rubin NVL72（Starmind 卫星，2028 年扩规）；Thinking Machines Lab 推出 Tinker 资助计划，为开源权重模型安全研究提供最高 5 万美元算力额度。均为远期/小众动向，供参考。

已跳过：OpenAI 美国大学生 4 个月免费 Plus、阿里云高校学生 Qoder 福利（营销活动，低价值）。

（已标记 2026-08-25 期为已读）
