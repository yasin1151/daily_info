
# 🍊 橘鸦AI早报 · 2026-08-17

共 8 条要闻，按栏目整理如下。

## 要闻

**1. Codex 官方教程：开启 1M token 上下文，但定价争议未了**
Codex 负责人 Tibo 公布为 GPT-5.6 Sol 开启 100 万 token 上下文的配置方法（config.toml 设 `model_context_window = 1000000`、`model_auto_compact_token_limit = 900000`，重启生效）。但 OpenAI 另一员工 Vaibhav Srivastav 提醒：超出默认窗口的 token 按 **2 倍计入用量限额**，不用时应关闭——Tibo 此前否认过此说法。对重度用户是利好，但"2 倍计费"是否属实直接影响成本。
🔗 https://x.com/thsottiaux/status/2089082893804896524

**2. Codex 确认未来将接入下一代模型 Astra**
Tibo 在 X 上列出 Codex 特性清单（近 100% 可靠、偶尔重置、开源），末尾括号注明 "will have Astra"。官方未公布上线时间。暗示 Codex 后续将绑定 OpenAI 新一代旗舰模型，路线图信号明确。
🔗 https://x.com/thsottiaux/status/2089149255382438340

## 开发生态

**3. DeepSeek API 正式涨价，并启用峰谷定价**
新定价体系今日零时生效：deepseek-v4-flash 与 v4-pro 由统一定价改为**峰谷定价且整体大幅上涨**。高峰时段 9:00–12:00、14:00–18:00；空闲时段价格为高峰的一半。对国内开发者是把成本敏感度从"按月"拉低到"按小时"，用量调度策略将直接影响账单。
🔗 https://api-docs.deepseek.com/zh-cn/quick_start/pricing/

**4. OpenCode Go 跟随 DeepSeek 涨价缩水额度**
DeepSeek 官方涨价后，OpenCode Go 额度同步更新：v4 flash 额度从 **60 美元降至 15 美元**，每月预估请求从 158,150 次降至 18,900 次（约 -88%），并出现忙时加价。创始人 dax 称本周在测试多种部署方案，力争以接近原价托管；同时吐槽"数十家声称对齐旧价的供应商实际都没做到"。
🔗 https://x.com/opencode/status/2089032195100774534

**5. SuperGrok Heavy 用户可免费使用 Cursor Ultra（订阅存续期间）**
订阅 SuperGrok Heavy 的用户在 Grok Bot 中关联账户后即可免费使用 Cursor Ultra，只要订阅保持活跃就持续有效。此前帮助页写的"1 个月"已被 Cursor 官方论坛澄清为过时信息。限制：一个 Grok 账户只对应一个 Cursor 账户，已订阅 Ultra 或团队账户不适用。
🔗 https://forum.cursor.com/t/free-cursor-ultra-with-grok/168286

## 技术与洞察

**6. Dario Amodei 回应"AI 言论过于负面"批评**
Amodei 否认个人沟通"不成比例地负面"，认为公众负面看法源于长期形成的信任危机；他承认对 AI 公司"最准确的批评"是**尚未兑现改善世界的承诺**，为此 Anthropic 正加速生物学与医学研究，预计未来数月公布早期成果。监管上反对"集中监管 vs 广泛分发"的二元对立，支持前置测试路线。安全派与加速派之争的代表性表态。
🔗 https://x.com/DarioAmodei/status/2088758819304443967

## 前瞻与传闻

**7. 传 Stripe 以超 70 亿美元收购 OpenRouter**
彭博援引知情人士：支付巨头 Stripe 已敲定以逾 70 亿美元收购 AI 路由聚合平台 OpenRouter，尚未官方确认。几个月前 OpenRouter 融资估值约 13 亿美元——若属实，涨幅超 5 倍，也意味着 AI API 分发层被支付巨头整合。
🔗 https://www.bloomberg.com/news/articles/2026-08-16/stripe-nears-deal-to-buy-ai-firm-openrouter-for-over-7-billion

**8. 曝 OpenAI 解散 Preparedness 团队**
据 FT 援引内部人士：OpenAI 已于 7 月底解散评估模型灾难性风险的 Preparedness 团队，生物/网络风险工作拆分并入现有团队，近期多名安全人员离职。Brockman 称安全工作已更紧密融入模型开发；原负责人 Dylan Scandinaro 现专注"递归自我改进"AI 的安全风险。安全团队独立性的又一次收缩，值得关注后续动向。
🔗 https://www.ft.com/content/53082739-7714-4aae-9816-e55ab423cbee

---

**本期看点**：DeepSeek 峰谷涨价 + OpenCode 额度缩水直接冲击开发者成本（第 3、4 条联动）；Codex 两个信号（1M 上下文、Astra）；两笔/两起大事件均来自传闻（Stripe×OpenRouter、OpenAI 解散 Preparedness），以官方确认为准。

已标记 2026-08-17 期为已读。
