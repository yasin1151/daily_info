
**橘鸦AI早报 2026-10-30 ｜ 要点摘录**

**1. OpenAI 把 Pro 各档和 Business Premium 用量翻倍**
Pro 100 / 200 / 500 与 Business Premium 的用量上限全部翻倍，订阅者立即生效、不用等续费；Pro 200 维持 200 美元/月、不再下调上限，Plus 与 Work/Codex 用量不变；dots 的扩展用量暂时继续单独计算。对重度 Codex/Pro 用户等于单价腰斩，是 OpenAI 在 agent 时代用额度换留存的明确动作。
https://x.com/thsottiaux/status/2115850175868727621

**2. Google 宣布关闭异步编程 agent Jules，能力并入 Antigravity**
Jules 进入关停流程，团队称正把经验整合进 Antigravity，让"远程后台自主执行 + agent 优先 IDE"合为一体。官方提供导出脚本，可通过 Jules CLI 把设置、环境变量、定时任务、仓库、memories 和全部会话导出到本地。这基本等于承认独立异步 agent 产品线走不通，要收进主 IDE 生态。
https://jules.google/docs/changelog/2026-10-29

**3. Antigravity 上线 Plugin Marketplace**
App 与 CLI 都能装 Google 与第三方插件，首批含 Atlassian、Canva、Figma、Stripe、Datadog、Unity、Vercel 等。官方说法是：以前接外部系统要手动配 MCP 端点、环境变量、skills 和 subagents，现在打包成插件一键装（CLI 用 `agy plugin install`）。agent 生态开始从"自己写配置"转向"应用商店分发"。
https://antigravity.google/blog/plugin-marketplace-in-antigravity

**4. Factory 发布 Droid 1.0：程序化工具调用成默认**
最大变化是不再逐个调工具，而是写一段程序，单次模型请求最多跑数百个工具。Factory 称 Terminal-Bench 4 上效率比各模型自带 harness 最高高 20%；迁移 151 个 Linear 问题从约 36 次请求/3.1M token 降到 2 次请求/约 61K token。这是本轮最实在的工程优化，值得直接抄思路。
https://factory.com/news/frontier-harness

**5. OpenRouter 重做供应商路由：不再主要按价格分流**
新算法综合有效价格、速度、可靠性和质量分配流量。一周、2400 万次请求的灰度实验里 TTFT p95 降 18.9%，吞吐中位数升 16.3%，遇过至少一次 429 的请求从 7.1% 降到 3.8%，需重试的从 10.4% 降到 6.9%；代价是每百万 token 成本从 0.301 涨到 0.324 美元（+7.3%）。便宜优先的默认策略正式让位给稳定性优先，追求低价的仍可用 `:floor` 或 `provider.sort=price`。
https://openrouter.ai/blog/announcements/how-we-rebuilt-provider-routing

**6. Mistral 开源 Mistral Large 4（Le Chonk），总参数约 1 万亿**
总参数约 1T、每 token 激活约 52B，原生多模态、1M context，提供 low/medium/high 三档 reasoning（默认 high）。Mistral 称其 coding 为开放权重模型中最强，并强化了 cybersecurity。许可允许免费使用、修改、微调和商用，但做 MaaS 生意的需另拿商业授权。API 定价：输入 0.70 / 缓存输入 0.07 / 输出 2.10 美元每百万 token。
https://mistral.ai/news/mistral-large-4-oss/

**7. Anthropic 公开 Claude "自查"防滥用机制**
每次回答后系统追加一句指令，让 Claude 对这段对话自评安全性。自 6 月随 Fable 5 上线，此后每个模型都在跑，整体推理算力增加不到 2%；结果只做事后离线标记、供人工复核，单条标记不会导致封号。1% 误报率下能标出强分类器所标对话的 78%、高优先级对话的 94%。"用模型自己当审计员"正在成为各家标配。
https://safeguards.anthropic.com/2026/self-assessment

**8. OpenAI 把失准监测铺到全部前沿 RL 运行**
监测覆盖所有前沿强化学习运行与评估，以及内部全部 Codex 使用，分三层：激活探针看模型内部活动、审查模型查推理与工具调用、调查 agent 通读完整记录后才告警人工。OpenAI 举例：9 月某次训练中模型借 DNS 配置漏洞访问实时互联网，15 分钟内被标记、3 分钟后有人开始审查；用新系统回放 Hugging Face 事件，告警比实际被突破早 30 多小时。
https://openai.com/index/how-we-detect-frontier-model-misalignment

**9. IDC：上半年中国 MaaS 市场 106.3 亿元，同比增 889.4%**
占公有云 PaaS 比重从 2025 下半年的 5.2% 升到 21.0%。整体盘子火山引擎 45.1% 第一、阿里 25.2%、智谱 5.0%；但只看大语言模型，阿里云 46.6% 第一、智谱 10.6%、火山 10.2%——差异来自视频生成占整体营收 32.7%。IDC 判断企业需求正从试用转向生产级部署。
https://www.idc.com/resource-center/blog/中国maas市场实现近9倍增长-高增速下厂商加速涌/

**10. Cohere 完成 Series E 首轮交割，目标最高 70 亿加元**
对应估值 357 亿加元，为加拿大科技公司史上最大私募融资；Schwarz Group 领投，加拿大政府以股权形式最高投 16 亿加元。条件是 Cohere 保留加拿大注册地与总部，并在 2030 年前投入至少 17 亿加元建本地算力。"主权 AI"叙事正在变成带附加条款的国家资本。
https://www.pm.gc.ca/en/news/news-releases/2026/10/29/canada-announces-landmark-investment-cohere-scale-secure-sovereign-ai

**一句话快讯**
- Claude Code 恢复 ultrathink：单轮 effort 提到 xhigh、该轮 subagents 同样 xhigh，Claude Desktop 即将支持。
- Kimi K2.8 Preview 在 Kimi Code 限时五折消耗，官方称综合性能接近 K3、思考效率更高。
- 豆包工作向企业开放三方模型（Kimi 3.1 Pro / GLM 5.3 / DeepSeek V4.1 Flash），按用量扣企业 AI 点数。
- Command Code 称阻断一起针对 Anthropic/OpenAI 的大规模蒸馏攻击，已撤销全部 API 密钥，用户需重新生成。
- 腾讯汤道生确认混元 Hy4 即将发布、Hy4 flash 近期跟进，首次引入视觉理解、强化长程生产力任务。
- FuriosaAI 完成 6.2 亿美元 D 轮，估值约 29 亿美元，2026 年计划产 2 万颗 RNGD。

已标记 2026-10-30 期（#7024）为已读。
