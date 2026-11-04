
**橘鸦AI早报 2026-11-04 期摘要**

本期共 19 条，核心信号是：可验证推理从论文走向工程原型；开源模型继续从“通用对话”转向专用能力，如视觉、协作协议；OpenAI 一边扩张产品线，一边补强政策与安全团队。

---

**1. Anthropic 开源 FlashProve：能证明“回复来自哪个模型”**
发布可验证推理系统，提供方先对模型权重发布“承诺”，即不公开权重的加密指纹，再为每条回复生成证明，用户用自己的 CPU 即可验证回复是否符合该权重计算结果，无需拿到权重。实测在 Llama 4 Maverick 4bit 上，单张 H100 约 110 token/s，1024 token 请求的证明约 19MB、24 核验证约 17 秒。代价是生成证明耗 GPU 时间约为普通推理的 70–95 倍，且当前仅支持 1024 token 上下文。意义在于模型替换、回复篡改、评测模型与实际服务不一致这三类问题第一次有了可查的数学手段，但成本决定它短期只能用于审计和高价值场景。
https://anthropic.com/research/provable-inference

**2. 隐身模型 Crouton Alpha 上线 OpenRouter / OpenCode，免费一周**
1M 上下文、多模态、输入输出均 0 美元，OpenCode 宣布免费一周、数据不用于训练、限特定地区。社区从屏蔽国家列表、日文词汇报错、effort 设置等特征推断其与 Meta 模型高度一致，但身份未确认。这类“隐身测试”通常是大厂正式发布前收集真实流量反馈，免费窗口值得白嫖，但不要把生产数据放进去。
https://openrouter.ai/stealth/crouton-alpha

**3. 微信视觉团队开源 WeVisOne-VL（2B / 4B）**
基于 Qwen3-VL，用 structured next-token prediction 把检测、指代定位、计数、指点、OCR 等物体级任务与分割、抠图等像素级任务统一进一个模型，配 9.6M 参数像素解码器，推理时不再需要外挂 SAM。目标不存在时支持返回 None，官方称 30 多个基准领先。权重、推理包、Cookbooks 全开源（自研代码 Apache 2.0）。对小团队做图像编辑、标注流水线是直接可用的替代方案。
https://github.com/Tencent/WeVisOne-VL

**4. MiniMax 开源 BYOB：把“多 agent 同桌”做成协议**
发布协议规范 + TypeScript 参考实现（MIT），场景是一张共享桌子，每人带自己的 agent 入座，可以是 MiniMax Code、Grok Bot、任意 MCP agent 或脚本。关键设计是记忆、身份、权限、账号始终归各自主人，桌子不拥有任何 agent；跨主人操作走“提议 → 受影响方批准 → 本方执行 → 另一席位核验”四步。这是把 A2A 从概念推进到可运行的最小协作单元，值得关注其能否成为跨厂商 agent 互操作的事实标准。
https://github.com/MiniMax-AI/mcode-agent-table

**5. Claude 团队版/企业版上线插件自动连接**
管理员为整个组织授权一次后，员工首次登录即自动连上公司开通的插件，不必逐个登录确认。支持两条路径：通过身份提供商统一管理（已正式可用，目前支持 Okta），或由 Claude 作为可信签发方直接签发（测试版，支持 Notion、Figma、Datadog、Amplitude 等 14 款）。这是企业采购的实际摩擦点——插件授权的运维成本往往比模型能力更影响落地速度。
https://support.claude.com/en/articles/15537633-auto-connect-your-organization-s-apps-to-claude

**6. OpenAI 披露：ChatGPT 搜索量约为 Google 的 20%，周活达 12 亿**
消费产品负责人 Adam Fry 称，按“每次提问触发联网搜索计一次”口径，ChatGPT 搜索查询量约为 Google 的 1/5 且增长较快；周活跃用户近两个月从 10 亿增至 12 亿，语音周活 2.5 亿，每周生成约 15 亿张图片。另透露计划合并 Chat 与 Work 两种模式，由单一界面自动判断意图。20% 这个数字口径宽松、不宜直接对比，但“搜索入口正在被对话入口侵蚀”的方向已经明确。
https://x.com/adamhfry/status/2117714179209723951

**7. AI 推理服务商 fal 融资 16.5 亿美元，估值翻倍至 160 亿**
E 轮 3.5 亿由 Sequoia 领投，F 轮 13 亿由 Bessemer 领投，NVIDIA 战略投资，T. Rowe Price、Sound Ventures 等参与。估值较今年 4 月的 80 亿翻倍。信号很明确：资本正在从“训模型”转向“卖推理算力”，多模态生成（图像/视频）的推理需求是当前最确定的现金流之一。
https://fal.ai/blog/series-e-f

**8. 上海宣判盗用大模型算力案：伪造签名转售，获刑三年**
被告用 AI 工具伪造签名绕过平台防护，自建网站转售图片和视频生成服务。涉案平台短时间内涌入 400 多万个同一 IP 注册的用户，非法调用接口 29 万余次，违法所得 3.4 万余元。法院以非法获取计算机信息系统数据罪判处有期徒刑三年、缓刑三年，罚金 4 万元。违法所得不高但刑期实打实，对“薅 API 转售”灰产是一次明确的司法定性。
https://www.thepaper.cn/newsDetail_forward_34389477

**9. 产业链消息：DeepSeek V5 计划基于华为昇腾预训练**
据《科创板日报》引述多名产业链人士，DeepSeek 下一代大模型 V5 将用昇腾芯片做预训练，而此前昇腾主要承担 DeepSeek 的推理任务。官方未确认。如果成立，这是国产算力从“能跑推理”跨到“能训前沿模型”的关键一步，也意味着训练侧的软件栈（算子、并行、稳定性）已经过一轮实战验证；但预训练对集群规模和互联的要求远高于推理，仍需观望实际规模。
https://mp.weixin.qq.com/s/R-1u2exLwZMOu7AITyU5kg

**10. 两条人事与组织动向**
Claude Code 产品负责人 Cat Wu 宣布离职，她回顾两年间 Claude Code 从内部小工具变成“默认信任模型判断、自动批准权限”的行业定义级产品，并参与 Cowork。同期 OpenAI 聘请 Uber 总裁 Jill Hazelbaker 任首席企业事务官、美国前陆军部长 Dan Driscoll 任国家安全现代化高级顾问，并与 Cathedral Systems 开展安全冲刺，关键漏洞赏金提至四倍以上、单项最高 17.2 万美元。一边是产品线核心人物流出，一边是政策、安全、政府关系密集补强，两家的组织重心差异越来越明显。
https://x.com/_catwu/status/2117731934340337676

---

*已标记该期（ID 7142）为已读。*
