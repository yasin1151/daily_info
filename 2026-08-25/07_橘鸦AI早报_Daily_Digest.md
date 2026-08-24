
# 🍊 橘鸦AI早报 · 2026-08-24

来源：[daily.juya.uk/issues/2026-08-24](https://daily.juya.uk/issues/2026-08-24/)

---

## 开发生态

**1. Codex 用量异常修复即将上线，付费用户用量全面重置**
Codex 负责人 Tibo 称已定位多个导致用量消耗过快的问题：长会话多次 compaction 后使用图片的低效、Computer History 在 p95 以上的高用量、以及对话标题生成功能的异常消耗。修复上线后全部付费订阅用户用量将重置，plus 用户已陆续生效，business/pro 暂未重置。Tibo 还明确回应："We don't support sub2api"——订阅额度不能转 API 调用。
**影响**：用量被"偷走"的 Codex 用户将获补偿性重置，订阅/API 边界被官方再次划清。
🔗 https://x.com/thsottiaux/status/2091407991736332689

**2. Claude Code 回应 Opus 5 批评：上线简洁输出配置过渡**
Claude Code 主创 Boris Cherny 承认 Opus 5 不完美、输出冗长，修复是团队优先事项。过渡方案已上线：运行 `claude /config outputStyle=concise` 即可切换简洁输出风格，无需等长期修复。
**影响**：被 Opus 5 废话输出困扰的用户现在有立即可用的缓解手段，同时释放了"修复中"的官方信号。
🔗 https://x.com/bcherny/status/2091591570982371454

## 前瞻与传闻

**3. 智谱 glm-5.3-turbo 疑似即将上线**
zcode 预览版 3.9.1 新增 computer use 与模型输入模态选择功能（官方曾称 computer use 将随多模态模型上线）；有用户在 GLM Coding Plan 中调用 glm-5.3-t 报错为"无权访问"而非"模型不存在"——该报错模式此前只出现在智谱未开放的内测模型上。
**影响**：多模态 + computer use 组合意味着智谱可能在终端 Agent 赛道对标 Claude/OpenAI，值得关注官方发布。
🔗 https://daily.juya.uk/issues/2026-08-24/

**4. Anthropic 两个新 Claude 模型标识曝光**
爆料称出现 `claude-marshmallow-eap` 和 `claude-melon-eap` 两个新标识（EAP 即早期访问计划）。爆料人判断非 fable 级别但表现尚可，猜测下周更可能看到 Opus 或 Sonnet 更新。均为个人推测，官方未确认。
**影响**：与 Opus 5 刚遭批评的时点叠加，Anthropic 可能正加速迭代修复口碑。
🔗 https://x.com/notjazii/status/2091578924639871451

## 产业动态

**5. Hugging Face 探索出售，估值或达 130 亿美元**
Business Insider 报道 HF 正与银行合作评估潜在收购方兴趣，估值 130 亿美元以上，尚未达成任何交易，官方未确认。
**影响**：AI 开源生态核心平台若易主，模型托管与开源分发格局可能生变。
🔗 https://www.businessinsider.com/hugging-face-could-be-acquired-13-billion-2026-8

**6. 阿里巴巴拟配售 800 亿港元新股，净额 100% 投 AI**
阿里拟配售 800 亿港元新股（2019 年港股上市以来首次），款项净额全部投向全栈 AI 能力和 AI 基础设施。这将是港交所史上最大增发、史上最大 Regulation S 发行，今年全球第三大股权发行（仅次于 Alphabet 和英特尔）。目前仍为拟议计划。
**影响**：国内 AI 军备竞赛再添重磅弹药，阿里算力/模型投入规模将显著加码。
🔗 https://www.zaobao.com.sg/news/china/story20260823-9560754

**7. 英伟达 AI 服务器明年初涨价超 15%（HBM 成本飙升）**
彭博社：因内存成本飙升，英伟达已通知核心客户，搭载其 AI 芯片的服务器多数涨价超 15%，自明年初出货的 Grace Blackwell 与 Vera Rubin 系统起生效，涨幅取决于芯片代际与内存配置。官方未确认。
**影响**：HBM 涨价沿供应链传导，明年 AI 算力采购成本将明显上升，可能波及云厂商定价。
🔗 https://www.bloomberg.com/news/articles/2026-08-22/nvidia-customers-notified-about-ai-related-price-hikes-above-15

---

*已标记已读。其余 9 篇为 8/15 及更早旧刊，如需补读可告知。*
