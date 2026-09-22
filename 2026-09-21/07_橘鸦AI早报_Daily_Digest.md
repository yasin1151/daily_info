
**橘鸦AI早报 · 2026-09-20 期摘要**（共 14 条，筛出 10 条）

---

**模型发布**

**1. 阶跃星辰 Step 5 Preview 现身 Artificial Analysis** —— 第三方榜单已收录并完成独立评测，智能指数 44，支持 1M 上下文与视觉输入，百万 input/output token 分别 1 美元和 2.7 美元；部分 Step Plan 用户称已能调用，但官方尚未正式发布，页面仍标注为闭源。
看点：国产模型第一次在货架榜单上把「百万级上下文」和「个位数美元/百万 token」绑在一起，指向的是长文档/长代码场景的成本结构变化。
https://artificialanalysis.ai/models/step-5

**2. 千问发布同传模型 Qwen3.8-LiveTranslate** —— 支持 60 种语言实时互译，采用 Interleave 架构（音频文本交织单流，缓存复用已听音频和已输出译文），Thinker-Talker 双模块设计，字均延迟从上一代 2.8 秒降至 2.3 秒；新增实时说话人分离、原文译文同帧输出、长上下文消歧。在线体验与 API 均已上线。
影响：0.5 秒的延迟削减 + 说话人分离，直接对现有同传 SaaS/字幕工具构成替代压力。
https://mp.weixin.qq.com/s/Rc3CKdHAtA_NdVRN2RLuAg

**3. 达摩院开源腹部 CT 诊断视觉语言模型 RADAR，论文发表于 Science** —— 在 424,911 例增强腹部 CT、1500 万解剖级图文对上训练，直接从临床报告学习、无需人工标注；覆盖 18 个解剖结构和 146 项影像发现，内部真实队列 AUC 0.913，八家外部中心 0.874–0.912；26 名放射科医生参与的阅读研究中，协作使用使诊断敏感度提升约 10%。代码同步存档 Zenodo，权重在 HuggingFace，Apache 2.0。
看点：不是刷分模型，而是走向「可外部复现的通用诊断基线」，医疗 AI 的评测门槛被抬高了一档。
https://github.com/alibaba-damo-academy/damo-radar

**4. Cua 开源表单填写微模型 cua-s1-forms** —— 仅有 706,048 个可训练参数、检查点约 2.8 MB，通过单次前向为界面元素的候选值及「勾选/点击/跳过」打分，再由 Cua Driver 排序执行。模型卡称合成测试准确率 99.95%、小规模真实演示 100%。作者自陈仍是早期研究，未在演示集以外任意真实表单上验证，也未被任何推理服务商部署。
看点：用 0.7M 参数替代大模型来做具体 UI 动作，是「Agent 能力下沉到小模型」的一次明确示范。
https://huggingface.co/cua-ai/cua-s1-forms

**5. 中国电信开源 Xing4.0-29B-A4B** —— 星辰语义大模型，29B 总参 / 4B 激活，采用 mHC、MLA、MTP 架构，原生支持 256K 上下文并可扩至 512K，面向多步骤规划、工具调用与复杂推理链路。完全基于国产算力训练（昇腾 910C 集群 + MindSpore/MindFormers），官方称整体训练吞吐较开箱性能提升约 96%。基础版、FP8 版、GGUF 版均已放出。
看点：模型本身中规中矩，真正有信息量的是「国产算力 + 国产框架跑通 MoE 训练并全量开源」这条链路。
https://github.com/XingChen-AGI/Xing4.0-29B-A4B

---

**开发生态 / 开发工具**

**6. DeepSeek API 明确计费口径：调休周末和法定节假日全天按空闲时段计费** —— 平台公告横幅明确，即使周末因调休成为工作日，也适用空闲时段规则，面向官方 API 用户。
影响：对把批处理、评测、数据清洗放在国内非工作时段跑的团队是实打实的账单下降；也是国内厂商继续打价格战的一个信号。
https://platform.deepseek.com/

**7. Codex「banked reset」争议** —— 有用户因 OpenAI 本周未推出预期更新，向 Codex 负责人 Tibo 喊话「you owe us a banked reset sorry i don't make the rules」，Tibo 回：「OK fine. But it's also still coming in Tuesday」。
社区随即分裂成两派：一派认为「OK fine」就是答应补发额度；另一派指出这句话里根本没出现 banked reset 三个字，唯一明确的信息只是「周二有东西」。典型的官方不表态、用户自行解读并放大预期。
https://x.com/thsottiaux/status/2101352781219258527

**8. Android Developers 推出 Android Bench 2.0** —— 把 AI 评测扩展到真实、多日的 Android 工程任务：从零构建应用、开发新功能、把跨平台代码库迁移到 Android；以完成率、视觉保真度、回归问题和每个模型/任务的平均成本连续评分。新版首次评估常用 Agent 与模型的组合，并新增 Gemini 3.8 Flash、Gemini 3.7 Flash、GPT-6 Astra、Fable 5.1、Kimi K3、Qwen 3.8 Max。
看点：评测范式从「单模型跑分」转向「Agent + 模型组合 + 单位成本」，这才是真实开发场景的比较方式。
https://developer.android.com/bench

---

**产业动态**

**9. OpenAI、Anthropic、SpaceXAI、Google 遭付费用户集体反垄断诉讼** —— 一批付费订阅用户在加州北区联邦法院起诉四家，指控其高管公开赞同一篇「呼吁协调限制未经约束的 AI 发展速度」的文章，构成《谢尔曼反托拉斯法》第 1 条的合谋，导致订阅者「以同样价格获得改进更慢的产品」。原告寻求集体诉讼认证、针对四家的禁令，以及确认违反联邦反垄断法的宣告性判决；四家公司尚未回应，材料也未说明相关服务可用性实际发生变化。
看点：AI 安全话语第一次被当作「价格—创新合谋」的证据送进法庭，无论成败都会改变厂商公开谈「放慢」的措辞成本。
https://news.bloomberglaw.com/litigation/openai-anthropic-google-spacexai-hit-with-antitrust-lawsuit

---

**前瞻与传闻（均未官宣，谨慎对待）**

**10. 五条发布传闻**
- OpenAI 或下周推出 GPT-6 系列：Sam Altman 称最期待的内容推迟到下周，Tibo 称筹备内容「可能够办 3 个 DevDay」，用户点名要 GPT-6 Sol 和 Luna 时他回「What else do you want」——这两款成为主要猜测对象。DevDay 定于当地时间 9 月 29 日。
- Gemini 4 Pro 疑似在 Arena 隐藏测试：多名用户称 gemini-3.8-flash 会随机路由至疑似 Gemini 4 Pro 的 Argon checkpoint，在 SVG、3D 场景、网页和游戏生成上表现优异；同期流传的一张基准图已被鉴定为 GPT-Image 生成。Google 未确认型号、代号、价格与开放时间。
- MiniMax-M3.1：官方开源的 MiniMax Code CLI 多个文件出现该标识，覆盖历史模型字段恢复、managed catalog、模型列表、参数解析与队列持久化；测试配置含 45 万 / 51.2 万 / 100 万上下文与 8192 / 16000 / 128000 输出、多档 thinking effort。尚未内置。
- Kimi K3.1：Kimi 知乎认证机构号发了一串从「4159」开始、恰好少了开头「3.1」的圆周率数字，被解读为暗示 K3.1 即将发布；帖文未直接提及，目前已删除。
- Anthropic：路透援引三名消息人士称其正考虑推新模型，以应对 GPT-6 Astra 在企业市场获得的关注，但安全评估仍在进行、尚未确定是否及何时发布；讨论发生在利率上升、竞争加剧与预期 IPO 之前。另有爆料博主称新版 Fable / Opus / Sonnet 正在部分账号隐蔽测试，未获官方确认。
https://x.com/thsottiaux/status/2101157729037586694

---

已标记 2026-09-20 期（id 6082）为已读，当前无未读文章。
