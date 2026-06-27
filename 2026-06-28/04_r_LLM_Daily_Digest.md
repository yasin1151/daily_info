
注：redlib 上 `r/LLM` 今日热帖实际是法学硕士申请版块，不是 AI/LLM 讨论区；本次按已知规则改抓 AI 相关的 `r/LocalLLaMA` 今日热帖。

**1. Intel 为什么仍被当作 AI 投资标的？**

摘要：这帖讨论的是“Intel 作为 AI picks and shovels 是否合理”。发帖人质疑 Wall Street 为什么还把 Intel 纳入 AI 基建叙事，因为主流 AI 数据中心并不明显依赖 Intel GPU。评论区的高信号点在于：Intel 的价值可能不在短期 AI 加速卡销量，而在先进制程、High-NA EUV 设备、美国政府持股与未来代工产能。值得关注的是，社区把“AI 基础设施”从 GPU 采购扩展到了半导体供应链与国家产业政策。

高赞评论：
- u/cakemates，330 赞：认为 Intel 拥有高端 ASML 设备，有潜力扰动 AI 硬件行业，但频繁裁员削弱了执行力。
- u/EmperorOfNe，185 赞：强调 Intel 持有多台 High-NA EUV 设备，TSMC 需等待交付，加上美国政府入股，使其成为投资者押注对象。
- u/Gimme_Doi，171 赞：认为 Intel fabs 到 2028 年可能接近先进制程，并可能承接部分未来显卡/AI 芯片产能，因为 TSMC 会被 AI 大客户占满。

原帖：https://www.reddit.com/r/LocalLLaMA/comments/1ugcbqx/why_do_people_keep_investing_in_intel_for_ai/

**2. 96GB 4090/5090 改卡是否是骗局？**

摘要：一位自称经营美国小型 GPU lab、并与中国工厂合作设计 48GB 4090 PCB 的用户发帖提醒：截至 2026 年 6 月，所谓 96GB 4090 和 96GB 5090 很可能是骗局，尤其 5090 改显存目前缺少泄露 VBIOS 和工程条件。这个讨论对本地推理用户很实用，因为高显存消费卡一直是 Local LLM 圈的灰色需求；如果社区判断属实，很多“低价大显存”渠道都需要重新评估风险。

高赞评论：
- u/Silent_Ad_1505，156 赞：指出目前没人能给 5090 加 VRAM，VBIOS 未破解，显存短缺甚至不是最大问题。
- u/Inevitable-Law7964，109 赞：补充称相关卡可能是第三方 PCB 加 4090/5090 核心的拼装方案，更像改装作坊而非正规工厂产品。
- u/computune，98 赞：认为仅显存模组成本就可能接近 RTX 6000 Pro 的价格，所谓便宜方案经济性很可疑。

原帖：https://www.reddit.com/r/LocalLLaMA/comments/1uh1lc7/96gb_4090s_and_5090_are_literally_a_scam_i_mods/

**3. 有硬件之后，不要只跑 benchmark，应该做 post-training**

摘要：发帖人反对 Local LLM 圈常见的“买硬件、下载模型、跑 tokens/s、截图”的玩法，建议把消费级或小型服务器硬件用于 post-training。他结合四年“post-training-as-a-service”经验，指出真实商业任务更看重准确率、延迟、数据质量、训练策略和部署可用性，而不只是推理速度。值得关注的是，这代表社区从“本地跑大模型”走向“用本地资源做可交付模型改造”的成熟方向。

高赞评论：
- u/Xatter，111 赞：半开玩笑地建议直接试 GLM-5.2 并报告体验，代表社区仍很关心新模型实测。
- u/Azazelionide，77 赞：认为 post-training 仍有大量 tribal knowledge，并建议始终使用 AMP、融合 kernel、优化 loss/deembedding 等工程技巧。
- u/kershawbobblehead，64 赞：赞同小模型和本地模型的未来在 bespoke 场景，尤其是科研实验室、隐私数据和非商业许可约束下的模型侧工作。

原帖：https://www.reddit.com/r/LocalLLaMA/comments/1ugg1dm/what_should_i_do_consider_posttraining/

**4. 深圳华强北 96GB 5090 报价与真实性争议**

摘要：发帖人在深圳华强北询问 96GB 5090 改卡，得到的报价是 5090 本体 36000 元人民币，加 20000 元改 96GB VRAM，总价约 8200 美元。这个价格比正规 RTX 6000 便宜有限，但没有保修，且评论区继续质疑 VBIOS 和显存颗粒可行性。值得关注的是，这类线下报价说明大显存本地推理需求已经形成市场，但真实性、可维护性和成本优势都还没有被可靠验证。

高赞评论：
- u/KeepyUpper，95 赞：认为 8000 美元买“拼装卡”风险太高，只比 RTX 6000 便宜三分之一；除非能现场验证和 benchmark。
- u/Fit-Palpitation-7427，69 赞：表示如果欧洲也能这样改，会立刻拿 4090 去尝试，反映高显存消费卡需求很真实。
- u/icepatfork，57 赞：称 48GB/96GB 4090 在中国也能找到，并考虑下月到中国时购买，显示传闻并非完全孤立。

原帖：https://www.reddit.com/r/LocalLLaMA/comments/1ugyqsi/96_gig_5090s_from_shenzhens_huaqiangbei/

**5. 8GB 老 MacBook 能否跑本地 Agent？**

摘要：一位用户想把 8 代 i5、8GB RAM 的旧 MacBook Pro 改成 homelab，用于小模型实验和 agentic tasks。评论区的重点不是推荐“能跑什么最大模型”，而是提醒小模型控制电脑的安全风险，并建议从 Gemma、LFM、Qwen 小模型等低资源方案入手。这个帖子值得关注，因为它代表本地 Agent 从高端多卡玩家下沉到旧设备实验，但安全边界、上下文长度和模型能力会成为核心限制。

高赞评论：
- u/Krowken，116 赞：直接警告不要让 4B 模型控制你的电脑，核心立场是能力不足时 agent 权限很危险。
- u/-p-e-w-，37 赞：认为安全不应依赖模型“足够聪明”，而应靠技术强制约束和权限隔离。
- u/Monad_Maya，19 赞：指出 8GB RAM 会是瓶颈，建议尝试 Liquid AI 的 LFM 模型和 Gemma 小模型。

原帖：https://www.reddit.com/r/LocalLLaMA/comments/1uh0lhc/dear_poor_people_of_this_subreddit/
