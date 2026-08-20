
已抓取 2026-08-20 期全文并完成提炼。文章已标记已读。以下为推送内容：

---

# 橘鸦AI早报 · 2026-08-20 摘要

## 行业动态

**1. Stripe 收购 OpenRouter**
Stripe 宣布签署协议收购 AI 模型网关与路由平台 OpenRouter。其 CEO Alex Atallah 表示名称、产品、路线图不变，照常运营。Stripe 意在帮企业同时管好 AI 的收入与成本两端——智能路由请求、高效使用 token 以提升盈利能力。
影响：模型 API 分发基础设施被支付巨头收编，OpenRouter 的聚合路由能力有望与 Stripe 计费体系打通，影响开发者调用模型的方式。
🔗 https://stripe.com/newsroom/news/stripe-agrees-to-acquire-openrouter

**2. Anthropic 二季度收入首次超过 OpenAI**
据 WSJ，Anthropic 截至 6 月的二季度收入达 116 亿美元（环比翻倍）并实现小额营业利润；OpenAI 同期收入 67 亿美元，环比仅增 18%，营业利润率进一步下滑，IPO 前仍未盈利。
影响：商业化格局生变——Anthropic 单季反超 OpenAI，后者在上市前的盈利压力加大。
🔗 https://www.wsj.com/tech/ai/openais-second-quarter-sales-show-tepid-growth-compared-with-anthropic-5cb42998

**3. 字节 Seed 基础模型成立四个一级部门**
据晚点，字节大模型部门 Seed 完成新一轮组织调整，新设四个一级部门，负责人均向吴永辉汇报，另任命 AI 安全与前沿探索方向负责人。意在合并相似工作、减少团队重叠；背景是字节此前讨论训练 5 万亿参数模型，并希望下一代模型直接走向全模态。
影响：国内大厂模型团队进一步资源集中，全模态 + 超大参数是 Seed 明确方向。
🔗 https://mp.weixin.qq.com/s/F83lvCWxJE8GkjrVGb18AA

**4. OpenAI 继续提供 Zero Data Retention，推出 Private Safety Processing**
OpenAI 宣布继续为符合条件的 API 客户提供前沿模型 ZDR（零数据留存），并推出新安全机制 Private Safety Processing：自动化系统可跨相关交互识别滥用模式，只返回有限安全信号，底层提示词和响应不暴露给 OpenAI 人员。部分功能正与早期客户测试，9 月开始推出并发布技术白皮书。
影响：企业客户最关心的数据隐私条款延续，安全审查从"逐条评估"升级为"跨交互关联分析"。
🔗 https://openai.com/index/offering-zero-data-retention-for-frontier-models/

## Agent 与开发工具

**5. Codex 上线多层防护，降低误删文件风险**
Codex 团队回顾过去几周改动：明确指示删除前检查目标、不复用系统环境变量、强化高风险删除命令检查并升级送审、提高 Full access 意外开启难度、更新 Auto-review，另构建回放评估并过滤训练数据中的破坏性操作。团队建议保持应用更新，使用 Ask for approval 或沙箱模式。
影响：针对此前 GPT-5.6 误删用户文件的舆论事件给出系统性修复，回放评估显示相关行为已大幅减少。
🔗 https://x.com/thsottiaux/status/2089891927659585918

**6. Claude Managed Agents 三项更新上线**
① Self-Hosted Sandbox 中完成的工作可保存到记忆；② web_search / web_fetch 新增 allowed_domains 与 blocked_domains 参数，控制 Agent 可搜索和读取的内容；③ Console 多 Agent 会话查看器改版。已上线 platform.claude.com。
影响：域名白名单是 Agent 安全治理的重要补丁，企业可控性明显增强。
🔗 https://x.com/ClaudeDevs/status/2090218983962390950

**7. Replit 上线 Free Mode，由 GPT-5.6 Luna 驱动**
Replit 推出 Free Mode：Core 订阅用户（$20/月）日常任务不再消耗额度，创造量最高提升 30 倍，每月最多 30 小时聊天；用量上限每 5 小时重置，Pro 用户限额更高。
影响：低成本模型 Luna 直接改变了 Replit 的定价模式——"低价模型 + 无限额度"正成为新一轮竞争手段。
🔗 https://replit.com/blog/replit-introduces-free-mode

## 模型发布

**8. Ornith-1.5 开源：397B MoE 全系 MIT 许可**
Ornith-1.5 系列含 397B MoE、35B MoE、9B dense 三档，全部模型及 FP8/GGUF/MLX/NVFP4 量化版均以 MIT 发布。把 self-scaffolding 扩展为端到端自我改进循环：模型自己提任务、生成任务专属脚手架、产出 rollout 用于强化学习。官方称 397B 版在相关基准上与 Opus 4.8 相当。
影响：超大开源模型以宽松许可放出，自我改进式训练路线值得跟进。
🔗 https://ornith.ai/ornith_1_5.html

**9. Unsloth 发布 Qwen3.8-27B Dynamic v3.0 量化，1-bit 版 8GB 内存可跑**
Unsloth 发布 Qwen3.8-27B Dynamic v3.0 GGUF 量化，兼容 llama.cpp 与 Unsloth Desktop 等主流推理引擎；同步推出的 1-bit 量化可在 8GB 内存运行，相对 BF16 保留约 77% 准确率。官方称同等体积下 top-1% 准确率比其他提供方高 10%+。
影响：本地部署门槛进一步下探，8GB 内存设备也能跑 27B 级模型。
🔗 https://unsloth.ai/docs/basics/dynamic-3.0-ggufs

## 技术与洞察

**10. 唐杰：GLM-5.3 是后训练对照实验**
智谱创始人唐杰发文阐述 Scaling Law：参数量必须与数据量、算力投入方向一起衡量。GLM-5.3 与 5.2 同基座、同架构、同参数量，仅经过一个月长程环境与 RL 扩展，提升"并非边际性"，验证了后训练扩展的价值。总参数达到容纳知识的阈值后，能力增长主要来自有效深度与后训练；下一步计划可能是 mid-training、pre-training。
影响：为"Scaling 已死"之争提供新角度——后训练本身也是 Scaling 的一个旋钮。
🔗 https://x.com/jietang/status/2089941544581403107

---
**已跳过**：谷歌学生优惠、ChatGPT Ads 欧洲扩展（营销/广告类）、Meta AI Mac 测试版、Google Search 学习工具、Daybreak Blue 验证问题（低价值）、OpenCode/ZCode 额度更新（同质化产品更新）。

*原文：https://daily.juya.uk/issues/2026-08-20/ （内容由 AI 辅助整理，可能有误，重要信息建议点链接核对）*
