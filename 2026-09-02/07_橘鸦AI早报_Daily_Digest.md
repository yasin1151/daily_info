
# 📰 橘鸦AI早报 · 2026-09-01 摘要

## 模型发布

**1. DeepSeek 开源首个视觉多模态模型 V4-Flash-Vision-Exp（305B, MIT 协议）**
DeepSeek 发布 V4 系列首个引入视觉模块的实验模型：305B 参数，在 V4-Flash 基础上加视觉能力，纯文本能力基本持平，视觉 Agent 能力显著增强，权重已在 Hugging Face 开源。MIT 许可意味着可自由商用，多模态赛道竞争进一步加剧。
🔗 https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp

**2. Runway 发布首个「界面世界模型」Solaris**
基于 Gen-4.5 视频模型改造，能逐帧实时生成免代码的可交互界面——用户在交互过程中画面持续合成，由语言模型推理、世界模型渲染，支持 720p 实时交互和长会话一致性。官方承认文本渲染稳定性、长会话一致性仍是难题，尚未公开发布，仅开放早期访问申请。
🔗 https://runway.com/news/research/introducing-solaris

**3. 谷歌开源 TimesFM-3：零样本多变量时间序列预测**
3.3 亿参数，在超 1 万亿时间点语料上预训练，原生支持多变量联合预测，无需微调即可零样本预测多条协同演化的序列，单次前向传播生成完整预测区间，支持多目标、协变量和分位数预测。代码与权重均已开放。
🔗 https://research.google/blog/timesfm-3-a-zero-shot-foundation-model-for-multivariate-forecasting/

## Agent 与开发工具

**4. OpenClaw 2.0 发布：史上最大更新，1.6 万个 PR 合入**
933 位贡献者完成，覆盖安装、浏览器、消息、记忆、技能、模型、自动化、插件等几乎所有模块。安装流程简化，可直接复用本机 ChatGPT/Claude 订阅、API key 和本地模型；新增跨设备共享云会话，支持换设备继续工作、团队接手会话。
🔗 https://openclaw.ai/blog/openclaw-2-accidentally

**5. Meta Muse Code 正式 GA：每月 5 美元起，主打 subagent 编排**
结束 beta 并推出订阅（5 美元/月起），新增 Workflow（编排大规模 subagent 团队并行处理复杂工程任务并返回单一结果）、会话间消息（本地 Unix socket 互传，不走网络）和 Rewind 功能；SDK 以 TypeScript 库形式开放，全本地运行。
🔗 https://developer.meta.com/ai/resources/blog/muse-code-new-plans-and-features/

**6. 微信支付 AI 专属卡接入 DeepSeek Harness 和 OpenClaw**
继 WorkBuddy、QClaw 后，AI 专属卡可在更多 Agent 中使用：消费与主账户完全隔离，余额由用户设定，每笔支付需用户确认授权。一条命令 `npx -y @tenpay/weixinpay-ai-installer` 即可完成插件安装配置。Agent 原生支付基础设施在快速扩张。
🔗 https://mp.weixin.qq.com/s/qGS_3y9ZXVuLgRZ8_Nc9Iw

## 舆论与争议

**7. Claude 200 美元套餐「20x 用量」被指仅限 5 小时窗口**
用户指出 Anthropic 宣传的 Max 套餐「20x」实际指相对 Pro 的每 5 小时会话额度，周限额仅约为 100 美元套餐的 2 倍。Codex 负责人 Tibo 转发并强调「Codex 的 20x 直接适用于每周额度」，形成对比。Anthropic 尚未正式回应，定价透明度争议仍在发酵。
🔗 https://x.com/thsottiaux/status/2094254532020818191

## 商业与产业

**8. OpenAI：ChatGPT Ads 上线不到 200 天，ARR 达 10 亿美元**
广告已覆盖 40+ 国家，数万广告主投放；Ads Manager 自助投放扩展到印度、欧洲、中东和北非。官方称广告与回答分离、广告主无法访问用户私人对话。AI 原生广告的商业化速度相当惊人。
🔗 https://openai.com/index/expanding-access-to-ai-with-chatgpt-ads/

**9. ChatGPT 被欧盟认定为「超大型在线搜索引擎」**
欧盟委员会依据 DSA 将 ChatGPT 认定为超大型在线搜索引擎（VLOSE），Reddit、Roblox 认定为超大型在线平台，三者须在 2027 年 1 月前完成额外合规义务，包括评估和缓解非法内容、未成年人影响等系统性风险。AI 产品正式进入欧盟最严格监管轨道。
🔗 https://ec.europa.eu/commission/presscorner/detail/en/ip_26_1772

**10. Nvidia 35 亿美元投资 MediaTek，共建边缘到云的 AI 平台**
Nvidia 购买 MediaTek 可转换债券深化合作，覆盖 AI 基础设施、本地 AI 计算和汽车三大领域：MediaTek 将采用 NVLink Fusion 平台开发定制 XPU，接入 Nvidia 机架级 AI 工厂；双方还继续合作多代 RTX Spark / DGX Spark PC 芯片及 AI 软件定义汽车平台。
🔗 https://nvidianews.nvidia.com/news/nvidia-and-mediatek-deepen-long-standing-partnership-to-build-ai-edge-to-cloud-computing-platforms

---
*跳过：ZCode 1.5 倍配额延长（促销）、WorkBuddy Hy4 扩容（排队公告）。另有关注点未列入正文：Anthropic 发布对齐整改措施（reward hacking 实验结论）、智谱下一代大模型走「大基座」路线、OpenAI 向部分大客户推按结果付费、五角大楼 GenAI.mil 上线 ChatGPT Mil 与 Grok for Government，需要详情可随时查。*
