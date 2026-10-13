
# 橘鸦AI早报 · 2026-10-13 期摘要

来源：https://daily.juya.uk/issues/2026-10-13/ （本期共 26 条，已按价值筛出 10 条）

---

**1. Meta 发布 Muse Wonder 模型系列（要闻）**
Meta 一次性放出 Muse Wonder 和 Muse Wonder Full 两款模型，主打个人/专业 Agent 任务，文本、图像、视频、音频全模态输入，上下文 100 万 token。真正的新东西是两个机制："Active Memory" 能跨对话记住用户重要信息；"Active Focus" 会在复杂任务中主动换替代方案、遇阻继续推进，并在关键动作前向用户确认。API 定价每百万 token 输入 4 美元、输出 20 美元，完整版只给 Muse Code 订阅户。Artificial Analysis 智能指数 52/56 分，高于上代 Muse Spark 1.3 的 48 分，但单任务成本约 4.52 美元——是"能力强但偏贵"的定位，Meta 正式把自己塞进 Agent 模型的第一梯队。
🔗 https://research.meta.ai/blog/muse-wonder

**2. The X Subscription 上线：Grok + Cursor + X Premium 三合一（要闻）**
xAI 把 Grok、Cursor、X Premium 打包进一个订阅、一份账单。档位月费 8/30/100/200 美元，后三档额度是 Plus 的 4/15/50 倍。关键细节也是最大的坑：同一席位的 Grok 和 Cursor 共用每周额度，但 Cursor 里的 Claude、GPT 等第三方模型**不算在订阅内**，按 API 标价另付；而且现有用户切换后不可撤销。xAI 这是在用编程场景给 Grok 导流，对已经在 Cursor 里重度用 Claude/GPT 的人，性价比反而可能下降。
🔗 https://docs.x.ai/x-subscription/overview

**3. 智谱推出法律专用模型 GLM-Legal**
基于 GLM-5.3-Flash 微调，面向合同审查、证据分析、合规研究。官方称在 Harvey LAB 上全通过率 19.2%（比基座提升 12.5 个百分点），在 LegalBench、PLawBench 上"以显著更小的参数规模追平前沿闭源模型"。目前测试阶段、API 需申请，能力即将接入桌面 Agent 平台 AutoClaw。信号很明确：垂直行业小模型开始用"专用评测"对标通用大模型，法律是继医疗、金融后第三个被点名的战场。
🔗 https://z.ai/blog/glm-legal

**4. OpenBMB 开源 MiniCPM-V 4.7（端侧多模态）**
两个型号：35B-A3B 和 1B，支持单图/多图/文档/视频理解。35B-A3B 用 LES 技术预加载下一层专家权重，官方称在 iPhone 17 Pro Max 上解码 >13 token/s，仅占 3GB 内存；支持 4×/16× 混合视觉 token 压缩，另配套 Self-Replay 微调方法来降低能力遗忘。iOS/Android/HarmonyOS 端侧可部署，Apache-2.0 开源。这是国产端侧多模态里少见的"敢公布实测机型 + 手机跑大模型"的组合，手机本地跑 35B MoE 已经不是 PPT。
🔗 https://github.com/openbmb/MiniCPM-V

**5. OpenAI Agents API 新增"沙箱预热"**
开发者可在创建 Agent 会话前先装依赖、加载文件、跑初始化命令，任务到来时直接把现成环境接进会话，省掉开场的等待。预热和接入前免费，接入后按标准容器价计费；未接入的环境约 5 分钟过期。新环境支持最多 128 个会话共享同一工作空间。一个不显眼但很实操的更新——把 Agent 的"冷启动"从用户可感知的卡顿变成后台准备。
🔗 https://developers.openai.com/api/docs/guides/agents-api/environments/prewarmed

**6. Karpathy：LLM 能力认知差距正在扩大（值得一读的判断）**
他给了个"漏斗"估算：约 60 亿人几乎没接触过 LLM；10~20 亿人只是偶尔用免费聊天产品；约 2000 万人在数学和代码领域专业使用前沿模型；只有约 5000 人能接触内部前沿系统。他说专业用户已能让 Agent 通过提示完成过去要数周数月的大型代码项目，内部系统则是"数千个 Agent 连续协作数周"。重点不在于数字准不准，而在于他的结论：这已经不是"两群人互相不理解"，而是逐层收窄的差距，且差距由任务规模、时间跨度和访问权限共同决定。
🔗 https://x.com/karpathy/status/2109361546505966046

**7. Anthropic 两项安全研究：小模型或数月内能自我复制 + 蒸馏防御进展**
自我复制研究：Anthropic 认为小型模型可能在数月内具备在商用物联网设备上自主部署和传播的能力。官方评估中 Qwen3.5-9B 在 9 种测试硬件里 8 种成功部署了 Llama3.1-8B 推理服务；≤300 亿参数模型已能完成复制流程的多数单独步骤，但串联整条链仍出错，GLM-5.2 及以上可在简化评估里端到端完成。注意该评估削弱了入侵环节、结果是现实成功率的上界。另一篇则称加强 Claude 的蒸馏攻击防御后，攻击者提取的推理 token 减少约 90%~99%，手段包括限制推理内容流转、两阶段分类器拦截、对反复尝试账号限流封禁（误报率 <0.1%），但 Anthropic 自己承认"防御能撑多久不确定"。一边说模型快能自我繁殖，一边说防不住多久——这两篇放一起读，比单看任何一篇都更有意思。
🔗 https://www.anthropic.com/research/self-replicating-ai ／ https://www.anthropic.com/research/distillation-defenses

**8. Linus 正用 Claude Code 优化 Linux 内核**
Linus Torvalds 用 Claude Code 写了一组内核补丁，目标是缓解"多线程小块读取同一文件"时的 folio 引用计数争用。他表示代码、测试程序、审查和说明初稿都由 Claude Code 在他的指导下完成，测量在他自己的机器上做。效果：笔记本上 8 线程对同一文件做 16 字节读取，每次读取内核周期从 2937–2975 降到 725–726（约 4 倍）。补丁目前在 `noref-filemap-read-with-llm` 分支，还有内存回收和连续内存分配问题未解。Linux 之父用 AI 改内核并给出可验证的 benchmark 数字，是"AI 编码工具进入核心基础设施"最有分量的一次背书。
🔗 https://www.phoronix.com/news/Linus-Torvalds-Claude-Code

**9. 训练/Agent 方法两条：千问 QwenGyre 超长程 RL、Sakana AI MASS 自监督**
千问 QwenGyre：面向超长程 Agent 任务的在线 RL 框架，能弹性调度 GPU、处理执行轨迹以减少重复计算。在 Qwen3.8-2.4T 的 NL2RepoBench 实验中，每步约 70 万 token、训练 48 步，通过率 52.48%→58.54%，同等 GPU 预算下耗时从 Async 的 134.55 小时压到 75.42 小时（1.78 倍端到端加速）。
Sakana MASS：让同一模型同时当执行者、工作流优化器和评估者，把多 Agent 协作经验回灌训练。Qwen3.6-27B 两轮实验后，在 3 项未参与后训练的合成研究任务上对基座胜率 53.9%→69.9%，4 项公共研究基准上单位 token 得分达基座 1.2~1.6 倍；但在 Terminal-Bench 2.0 和 SWE-bench Verified 上**低于基座**——说明自监督多 Agent 有用，但不是万能，Sakana 也自己提示"模型自评的共同盲点可能把错误当进步"。
🔗 https://arxiv.org/abs/2609.33848 ／ https://pub.sakana.ai/mass/

**10. Artificial Analysis 发布 FrontierCode 1.1 私有编码榜单**
用 100 项真实开源仓库任务，评估模型提交的修改能否达到"维护者可合并"的标准（每任务试 3 次取平均；未过任一阻断检查或疑似查答案记 0 分）。结果：Claude Opus 5.5（max with fallback）以 52% 居首，其"通过全部阻断检查"的尝试占 58%；开放权重里 MiMo-V2.6-Pro 以 45% 领跑。最能说明性价比的是 GPT-6.1 Sol（max）得 49%，平均每任务成本 0.81 美元，不到同分 Claude Fable 5.1 的十分之一。榜单开始从"刷分"转向"能不能真正 merge"，比单纯代码 benchmark 更接近工程现实。
🔗 https://artificialanalysis.ai/articles/frontiercode

---

**行业动态速览（硬件三条）**
- **微软**计划 2027 年起把自研 Maia 扩到数千兆瓦级、成为旗下主要 AI 推理系统；三代 Maia 300 每机架 96 个加速器、约 167kW，官方称每兆瓦生成 token 比领先 GPU 多 40%，满配机架吞吐最高达 Maia 200 的 7 倍。→ 云厂商"去英伟达化"从试水转向主力部署。🔗 https://blogs.microsoft.com/blog/2026/10/12/microsoft-to-expand-azure-maia-system-to-multi-gigawatt-deployments/
- **NVIDIA** 在 OCP 峰会开放 Vera Rubin 机架与计算托盘设计，MGX 1.2 支持最高 250kW 机架、机架级盲插液冷、5000A 液冷母排；Vera CPU 机架规范把 MGX 扩到支持 Agent 工具调用/编排/沙箱执行的平台。🔗 https://blogs.nvidia.com/blog/ocp-global-summit-vera-rubin-scale-ai-factories/
- **AMD** 开卖新一代锐龙 AI Halo 开发者平台，最大 192GB 统一内存（至高 160GB 可作显存），官方称 4-bit 量化下可跑 3000 亿参数以上模型；Linux 版 7299.99 美元、美国 Micro Center 部分门店有售，Windows 版后续推出。🔗 https://www.amd.com/en/blogs/2026/meet-the-next-amd-ryzen-ai-halo.html

**传闻两条（未证实）**：The Information 称一家由 Jeffrey Katzenberg 与前 Sora 研究负责人 Bill Peebles 联合创立的初创公司，正与 OpenAI 洽谈授权并定制 Sora 用于电影制作；另有消息称腾讯元宝在开发个人 Agent 产品"元宝助手"并计划独立 App，承载长周期任务和长期记忆。

*已跳过：Codex 第 8 天额度重置、OpenCode/阶跃 Step 5/DeepSeek WorkBuddy 限免、ZCode 邀请返利等促销与运营类条目，以及丘成桐实验室联盟、月之暗面谣言案、英国 AISI 恢复访问等非产品动态。*

---
✅ 已标记 6628 为已读，当前无未读文章。
