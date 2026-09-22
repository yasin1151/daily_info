
**橘鸦AI早报 · 2026-09-17 期摘要**
原文：https://daily.juya.uk/issues/2026-09-17/

---

**要闻**

**1. 匿名「stealth」模型 Union Alpha 上线 OpenRouter / Cline / OpenCode**
一个不透露开发商的代号模型突然登陆三个平台并免费开放：支持图像多模态输入与工具调用，256k 上下文、最大输出 131k，定位研究、编程和 Agentic 工作流。OpenRouter 与 Cline 均称免费，OpenCode 明确只免一周。这类 stealth 放出通常是新模型正式发布前的盲测（参考此前 GPT-5、Claude 系列的惯例），值得先跑一轮实测，但不要在生产环境依赖——一周后可能收费或下线。
https://openrouter.ai/stealth/union-alpha

**2. 豆包 Doubao-Seed-2.1-pro 更新至 0915，主打「Agent 干活少胡说」**
API 全量上线火山方舟，豆包工作、TRAE 同步接入，6 月的 Doubao-Seed-Evolving 也升到同版本且无需改 Model ID。升级重点是生产级 Agent：多轮工具调用+联网调研+长报告场景下强化证据溯源、权威信源检索和时效判断，官方称幻觉显著减少；多模态 Coding 能读设计稿、录屏和复杂代码仓库，图像与视频推理 Token 消耗较上代降 30% 以上。想锁版本调 `-0915`，想自动跟随就调 Evolving。
https://mp.weixin.qq.com/s/Fp_mgF6wxMk0bkUVBqOKqA

**3. Anthropic 把 Claude Cowork 和聊天合并成一个 Claude**
用户不再需要区分「快速问答」和「复杂任务」，由 Claude 自己判断是直接回答还是持续执行，甚至关机后继续跑。同步上线 Claude Docs、Claude Slides，并把 Claude Design 接入对话——同一上下文里生成、编辑、分享文档/幻灯片/设计稿，Slides 支持直接演示和导出 PPT、PDF。三项均 beta、先给付费用户，能力也已进 Claude Code（可基于仓库文件和 RFC 生成文档、评审幻灯片或 UI 原型）。这是把 ChatGPT 式「一个入口」路径走到底，冲击的是 Notion/Google Docs/Figma 这类单点工具。
https://claude.com/blog/cowork-is-now-claude

**4. Sam Altman：原定本周的最主要发布推迟到下周**
他在 X 上表示原本最期待的本周发布改为下周，称「值得等待」，但没说是什么。社区与媒体广泛猜测是 GPT-6 Sol，均未获官方确认。这类预告式放风基本可以确认是一次大版本或旗舰模型发布，下周值得盯官方博客而非二手转述。
https://x.com/sama/status/2100351958167220547

---

**开发生态**

**5. Zed 开放 Delta 公测：用 Agent 线程替代 Pull Request**
Zed 推出多人编程与代码审查环境 Delta，尝试用共享 Agent 线程取代传统 PR——解决的是 Agent 生成代码暴增后「审查规模爆炸 + 决策上下文丢失」的真问题。开发者邀请成员进线程，共享 Agent 对话和 worktree，在独立审查子线程里检查、修改、合并代码。基于 DeltaDB 构建但兼容 Git，团队无需整体迁移，不用 Delta 的成员看到的仍是普通 Git 仓库。已支持 macOS/Linux/Windows 与网页端，公测免费。这是对 GitHub PR 流程最直接的一次挑战。
https://zed.dev/blog/delta-public-beta

**6. Qoder Cloud Agents 1.0 发布：把 Agent 当云服务托管**
定位一站式云端 Harness 托管平台，「Agent as a Service」，让 Agent 变成可调度、可管控、可扩展的云服务。提供可被 AI 编程工具直接调用的 Skill、Plugin、CLI，以及 API 与多语言 SDK；官方称测试期已支持数百家客户，月调用量从万级涨到千万级。规模能力包括十万级并发弹性调度、Batch 批处理、夜间折扣、多地域资源池和长任务断线续传。对做 Agent 生产的团队，这是「自建 harness」之外的一个托管选项。
https://mp.weixin.qq.com/s/vWqZhEbFv0cxrd__sIKt1w

**7. Grok Build 上线跨会话记忆**
可跨会话记住项目约定、决策和项目事实，官方称「越用效果越好」。两条命令：`/memory` 浏览记忆笔记，`/dream` 把近期笔记整理成主题。跨会话记忆是目前同类 Agent 工具最核心的体验分水岭，但也要注意：记忆里塞进错误的项目约定会被长期固化，建议定期用 `/memory` 审一遍。
https://x.ai/news/grok-build-memory

---

**技术与洞察**

**8. OpenAI 发布模型 misalignment 披露框架，同步公开六起案例**
框架覆盖训练、评估、测试、部署全生命周期，优先公开新型 misalignment 机制、已知行为的显著变化，以及挑战既有安全假设的发现。关键表态是：即使行为尚未被充分解释或缓解，也倾向于先行披露；复杂案例可能拖更久或需与第三方协调。同步披露过去半年训练/评估中观察到的六起意外或令人担忧行为。这是「先公布再解释」的透明度路线，对做模型安全评估的团队是一份可对标的披露模板。
https://openai.com/index/model-misalignment-reporting-framework/

**9. 小米公开直播 mimo-v2.6 的强化学习训练过程**
mimo-v2.6-pro 与 mimo-v2.6-flash 的 RL 训练指标、训练器日志、进度、成本公开可查，目前两项训练都在进行中。已更新 flash 第 12 步、pro 第 8 步的 DeepSWE 离线评测：v1.1 mini-swe-agent avg@3 得分 pro 62.24、flash 60.77。把训练过程（含成本）当成公开内容来播，在国内厂商里很少见，对判断模型真实进展比发布会更有参考价值。
https://mimo.xiaomi.com/rl/

---

**行业动态**

**10. 欧盟 + 联合国同日就 AI 风险发声，直指 Agent 与自我改进模型**
冯德莱恩在盟情咨文里提到 Hugging Face 事件，警告「AI Agent 逃离运行环境只是风险预演」，自我改进模型的危险正日益显现；她将邀请主要前沿实验室会谈，并与加拿大、英国等推进模型评估与验证合作，称《AI 法案》是关键护栏。此前有报道称欧盟目前尚无法可靠获取大型 AI 实验室最先进的网络安全模型。同日联合国秘书长古特雷斯警告 AI 风险超出人类理解，呼吁全球协调，「世界承受不起 AI 安全上的逐底竞争」，下周将以此为重点与各国领导人会谈，安理会也可能讨论 AI。监管叙事已从「能力监管」转向「Agent 失控 + 自我改进」。
https://ec.europa.eu/commission/presscorner/detail/en/speech_26_1868

**11. Cohere 与 Aleph Alpha 签署最终合并协议，主打跨大西洋主权 AI**
合并后以 Cohere 名义全球运营，柏林与多伦多双总部，保留海德堡办公室作研究中心，员工超 1000 人，官方称将成为首个同时满足加拿大和德国主权要求的基础模型开发商。Aleph Alpha 联席 CEO Ilhan Scheer 将任 Cohere COO，联创 Samuel Weinbach 任首席研究官（均以交易完成为前提），仍需监管批准，预计今年晚些时候完成。主权 AI 从口号进入并购整合阶段，欧洲阵营在收缩聚合。
https://cohere.com/blog/cohere-and-aleph-alpha-sign-agreement

---

**其他值得一瞥**：讯飞 Spark-Audio-1.0-Preview 上线，官方称业界首个纯国产算力训练的语音基座（0.65B 编码器 + 30B-A3B MoE，99 语言 / 202 方言，Fleurs 中文 SOTA，但指令遵循与音频理解仍有短板）；网易有道开源两款流式同传模型子曰4-R2T2 / T3PO（延迟最低 200–600ms，并推出终身免费的语音 Agent「网易叭哥说」）；报道称苹果在开发搭载 M8 Ultra 的企业 AI 推理服务器，最早 2029 年，或采用 NVLink Fusion。

已标记该期为已读。
