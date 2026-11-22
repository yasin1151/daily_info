
**橘鸦AI早报 2026-11-22**（最新一期；11-23 尚未发布，共 12 条，提炼 10 条）

---

**1. Google Antigravity 重置全部用户 Gemini 配额，缓存改进后产出提升 22%**
核心变化：负责人 Varun Mohan 宣布重置所有用户的 Gemini 配额，此前承诺的缓存改进已经实现，同样配额下能完成的工作量提升 22%。同时 `/btw` 命令升级：原本只能在主任务运行时插嘴提问，现在可以另开支线探索，还能把支线提升为主线，全程不丢失进度。
影响：Antigravity 正用“配额宽松”和“长任务可观察性”这两方面来争取 agent 用户，直接针对 Codex、Claude Code 的痛点，也就是长任务进行到一半时不敢随意提问。竞争重点从模型能力转到了工作流体验。
链接：https://x.com/_mohansolo/status/2124070033534161407 ｜ https://x.com/antigravity/status/2123921833883840650

**2. 博主称 Cursor 即将更名为 Grok Build**
核心变化：博主 Puck 称 Cursor 将改名为 Grok Build，图标保留，名字不保留；Grok Build CLI 2.0 已进入 alpha-unified 渠道，运行在 Cursor 的 agent 引擎上，支持以 Grok 或 Cursor 身份登录。推测更名绑定统一订阅，把 Grok 与 Cursor 装进同一个套餐，公告还承诺更轻快的桌面与网页版、多 agent 协作的 Projects、一个应用接入多家模型。
影响：如果情况属实，这就是 xAI 借 Cursor 的工程能力补齐编码入口的一步。但 Cursor 官方尚未确认，更名、订阅合并和模型中立这三件事互有矛盾，值得先当作传闻看待，等官方公告。
链接：https://x.com/GrokInsider/status/2123867269553938671

**3. OpenCode 宣布 GLM 5.3 与 DeepSeek V4.1 Flash 降价 60%**
核心变化：按量计费（pay by token）模式改为新官方定价，不是限时活动。开发者 dax 称模型跑在自有 GPU 上，价格比 Fireworks、Baseten 低 60%，处理量还更高；直接 API 调用同样按新价，Go 订阅超额后按 token 付费也享受新价。他强调服务不只面向 coding agent。
影响：推理托管层正在走向价格竞争。对成本敏感的团队来说，同一个模型在不同供应商之间的差价已经达到 1.5 倍以上，可以开始考虑把预算切换到更便宜的供应商。
链接：https://x.com/thdxr/status/2124265777217802707

**4. Gemini 网页版被曝隐藏「元素周期表」模型切换器**
核心变化：用户 Lumina 演示长按 Gemini 网页版模型选择器，出现 “The Periodic Table of Gemini” 界面，列出 Gemini 4 Hydrogen、Argon、Carbon、Neon，Nano Banana 排在钾元素位置。有 Plus 账号看不到，猜测仅对 Pro 和 Ultra 开放。
影响：这是目前关于 Gemini 4 产品线划分最具体的线索，也就是按元素分档、多个变体并存。虽然只是泄露，但这类隐藏 UI 通常出现在正式发布之前数周。
链接：https://x.com/LuminaBench/status/2124084959459873080

**5. OpenAI 把 Business Agent 开放给美国境外企业**
核心变化：总部在美国之外的电商和在线服务企业，现在可以在 ChatGPT 里认领业务并发布 Business Agent。流程是经 Business Hub 验证后创建 agent、更新业务信息、挂接带实时价格与库存的产品信息流，并能看到提及量、网站点击、常见话题的汇总洞察。此前仅限美国企业测试。
影响：ChatGPT 正在变成一个电商与客服的分发渠道，把商户侧经营工具直接嵌进对话入口。对跨境卖家和 SaaS 客服厂商是明确的机会，也是对传统客服机器人市场的一次挤压。OpenAI 明确不会把用户对话分享给企业。
链接：https://openai.com/business/businesses-in-chatgpt/

**6. 微信内测桌面端 AI Agent「做个小工具」，一句话做个应用**
核心变化：微信把小微里的「小工具」能力单独做成桌面客户端，提供 macOS 与 Windows Beta 版，官网有报名入口。实测显示开发任务由云端 subagent 完成，代码在云端生成、本机不留文件、写完直接部署，成品可经微信推送到 PC 和手机端使用。客户端用微信自研 WeLM，实测版本为 welm-v4.6-flash。报道称小微内测日活已超 3000 万。
影响：这是国内最接近“对话即应用”的分发实验，而且明确免注册、免备案、免认证、免审核，把发布门槛降到了零。对独立开发者是新的分发渠道，对合规体系则是一个明显的空白地带。
链接：https://mp.weixin.qq.com/wiki/minitool

**7. Lean 与 Mathlib 社区正式认证黎曼假设证明正确**
核心变化：Anthropic 数学家 Levent Alpöge 发布 1700 万行 Lean 代码的黎曼假设证明，称与 Claude 协作完成。Lean 与 Mathlib 社区随后发表联合声明，认证陈述与证明均正确：数十人复现编译且导出文件一致；陈述经 comparator 与 con-leche 两个独立工具比对，与 Mathlib 定义一致；证明导出文件经 Lean 官方内核和多个独立核查器检验。
影响：这是 AI 辅助数学第一次拿出形式化验证级别的成果，而且验证链条完全由第三方社区提供，不依赖 Anthropic 自证。意义不在“AI 证明了黎曼假设”这个标题，而在形式化验证这套机制被证明可以承载机器产出的巨型证明。
链接：https://leanprover-community.github.io/blog/posts/riemann-hypothesis/

**8. Novita AI 承认部分 MiniMax 请求被转发至 MiniMax 官方 API**
核心变化：隐私通知确认，5 月 28 日至 11 月 11 日期间，部分经 Novita 及经 OpenRouter 转入的 MiniMax 请求被转发至 MiniMax 官方 API，内容可能被第三方访问或留存。原因是路由配置错误，某个特定客户的转发路径被更广泛地套用；收到独立安全研究员报告后已暂停受影响模型。Novita 称自己不留提示词与输出、不用于训练，正与 MiniMax 核实数据留存与删除。
影响：持续近半年的静默泄露，波及所有经 OpenRouter 中转的链路，说明多级转售的推理链路在隐私上基本不可审计。如果这段时间通过这两个渠道传过 API 密钥或机密内容，应该立即轮换。
链接：https://novita.ai/blog/minimax-requests-privacy-notice/

**9. 台积电暂停中国企业 16nm 及以下先进制程订单**
核心变化：台积电已通知客户暂停中国企业的 16nm 及以下订单。按收紧后的管制规则，中国企业须事先取得美方许可或符合豁免资格，订单获批后才能恢复；此前台积电可自行评估设计能否豁免，现在必须由客户提前申请。获批名单含 Apple、AMD、Nvidia，无中国公司。受影响企业只能退到 28nm/40nm 等老工艺，且拿不到 AI 数据中心用的 HBM。
影响：管制节点从 7nm 一路下压到 16nm，覆盖范围从先进 AI 芯片扩到通用逻辑芯片。对国内芯片设计公司来说，这是产能与工艺的双重收紧，28nm 以上的成熟制程会变得更拥挤。
链接：https://appleinsider.com/articles/26/11/20/apple-supplier-tsmc-cuts-off-china-chip-orders-amid-tighter-export-controls

**10. 腾讯混元：下一代 Hy 将大幅扩大规模，Hy4-mini 已列入路线图**
核心变化：混元团队在 Reddit AMA 表示，下一代 Hy 模型将进一步大幅扩大参数规模，并继续投入大规模强化学习；确认 Hy4-mini 已进路线图，一款 Flash-Lite 在规划中。架构上首次披露 Hy4 曾在 GQA 与 MLA 之间反复权衡，最终因 DSA 降低了 MLA 在解码阶段的计算强度而选择 MLA。此前刚开放 Hy4 权重、发布 Hy4 flash。
影响：国内头部实验室明确走“更大参数 + 大 RL”的路线，与 DeepSeek 的效率路线形成对照。选择 MLA 的理由由官方自己给出，属于比较少见的技术透明度，对做推理优化的人有参考价值。
链接：https://mp.weixin.qq.com/s/LHZxKjzVkEpnsCDcNlaMXw

---

已跳过：Dots 通话转录（产品小更新）。已标记 7581 为已读。
