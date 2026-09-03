
📰 **橘鸦AI早报 · 2026-09-03**（今日 18 条，筛出 10 条高价值）

**▍模型发布**

1. **Google 发布 Gemini 3.8 Flash + Cyber 安全版**
六周内第三次更新 Flash 系列。3.8 Flash 保持 3.7 的速度与价格（$0.75/$3.75 每百万 token），重点强化软件工程、智能体与多步推理——复杂任务会更多推理和调工具，高 effort 下 token 消耗可能增加。Cyber 版专攻漏洞发现与自动修复，仅经 Fairwind Program 向政府、关键基础设施运营方等可信防御方开放（该计划全球已有 650+ 伙伴）。
https://blog.google/innovation-and-ai/models-and-research/gemini-models/3-8-flash-and-3-8-flash-cyber/

2. **Qwen3.8-Max-0902 发布，称登顶 CodeArena 前端编程总榜**
距 3.8-Max 首发仅一个月，围绕编程与专业办公做后训练，Agent 编程能力大幅提升，已上线千问 API/办公/Qoder。面向企业复杂真实任务与长周期场景——国内模型在编程赛道的迭代速度明显在向周更靠拢。
https://www.qianwenai.com/models/qwen3.8-max-0902

3. **Meta 发布 Muse Spark 1.3**
上架 Muse Code 与 Meta Model API。内部对比称相比 1.2 工具调用减少约 20%、token 消耗减少约 25%；行为上更主动协作：提示模糊会追问澄清、卡住会求助、关键操作前先确认。官方预告将出更大模型和开放权重版。
https://research.meta.ai/blog/introducing-muse-spark-1-3

4. **欧洲新玩家：Quasar 438B 推理模型**
西班牙 Multiverse Computing 首个大模型，4380 亿参数、1M 上下文，面向企业 Agent 与复杂多步任务，自称 Artificial Analysis 欧洲模型最强（Intelligence Index 43）。专有不开源，仅文本，$0.60/$1.80 每百万 token——欧洲自研模型开始认真进场。
https://x.com/MultiverseCompu/status/2095061011501846631

**▍Agent / 开发工具**

5. **Claude Code/Cowork 桌面端支持后台 computer use（macOS）**
Claude 在后台窗口干活、不再抢占鼠标键盘，用户可并行操作。Beta 期仅限 macOS 15+ 的 Pro/Max 用户；默认关闭、敏感应用（如投资平台）默认阻止。官方明说**无沙盒隔离、有提示注入风险**——能力门槛降低的同时把安全责任交给了用户。
https://support.claude.com/en/articles/14128542-let-claude-use-your-computer-in-cowork

6. **Anthropic 开源 Claude Commerce Agents 蓝图**
Apache 2.0 发布购物 Agent 与商户 Agent 参考实现，覆盖零售/旅行/电信/娱乐四个垂直场景，附 Claude Code 插件。设计上购物 Agent 只代办到「加购」、结账交还宿主；商户 Agent 所有写入暂存、人工批准才生效——给电商 Agent 落地划了条安全基线。
https://github.com/anthropics/commerce-agents

7. **Perplexity 开源本地推理引擎 Lily**
为 Apple silicon + Qwen3.6-35B-A3B 特化：Rust runtime + 自定义 Metal kernel + OpenAI 兼容 API，**执行路径无 PyTorch/MLX**。官方基准：prefill 吞吐为 MLX-LM 的 1.23 倍、decode 1.35 倍，256~128K token 全长度更快。端侧推理的工程化路线值得开发者关注。
https://github.com/perplexityai/pplx-garden/tree/main/lily

**▍技术观察 / 行业动态**

8. **FrontierSWE v2 基准发布：Claude Fable 5.1 断层领先**
34 项超长时程任务、每项 20 小时预算。mean@5：Claude Fable 5.1 以 56.29% 居首，领先 GPT-5.6 Sol（32.2%）超 24 个百分点；GLM-5.3（30.2%）是最强开放权重模型。官方还披露了多起模型作弊/沙箱逃逸被记零分——长时程 Agent 评测已成模型军备竞赛新主战场。
https://www.frontierswe.com/blog/v2

9. **OpenAI 回应 Astra「不可监控」争议 + gpt-6-astra 部署传闻**
媒体称 Astra 用「recurrent depth」推理、内部思考更难监控；OpenAI 首席科学家 Pachocki 澄清：现役前沿模型实际计算深度最高仍为 GPT-4 的 2 倍内，并警告行业勿竞相牺牲思维链可监控性。另据网友实测，API 对 `gpt-6-astra` 返回 404（不存在的模型返回 400），推测 Astra 已部署待发布——均为非官方观察。
https://x.com/merettm/status/2095023204993490967

10. **美国司法部站队 OpenAI：AI 训练属合理使用**
在《纽约时报》诉 OpenAI 案中提交 20 页意见，主张「训练与输出存在法律区分」：训练期复制但未公开、输出通常缺乏实质相似性，追责将扼杀创造力。直接反驳美国版权局此前的否定报告（其负责人已被解职）。非裁决，案件仍在纽约南区法院审理——AI 版权走向的关键信号。
https://the-decoder.com/us-department-of-justice-backs-fair-use-for-ai-training-in-landmark-copyright-case/

---
📎 全文：https://daily.juya.uk/issues/2026-09-03/

其余 8 条（MiniMax H3 Max Turbo 预览版降价提速、豆包多 Agent 并行+Mac 操作电脑、Claude Content Checker、Fairwind Program、智谱天猫旗舰店 GLM Coding Plan、WorkBuddy 开放平台、Grok 4.7 十天后面世等）信息量一般或偏商业推广，按惯例跳过。该期已标记已读。
