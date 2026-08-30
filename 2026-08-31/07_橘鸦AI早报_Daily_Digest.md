
# 📰 橘鸦AI早报 2026-08-30

## 头条：OpenAI 与 Cursor 决裂

**1. OpenAI 终止与 Cursor 合作，11月12日起切断模型访问**
SpaceX 以约 600 亿美元收购 Cursor 母公司 Anysphere 后，OpenAI 宣布 11 月 12 日终止向 Cursor 提供模型接入，不再开放新模型。理由：收购触发合同「控制权变更」条款 + 马斯克旗下公司有违反服务条款（如蒸馏）前科。用户仍可自带 API Key 或通过 Codex 插件调用 OpenAI，终止的是平台级供应合作。Cursor CEO Truell 回应：OpenAI 模型仅占平台流量约 5%；Anthropic 表示将加大对 Cursor 的 Claude 算力支持。马斯克则在 X 上公开攻击 Altman 和 Brockman。**影响**：AI 编程工具阵营加速两极分化（OpenAI vs Anthropic），Cursor 基本盘转向 Claude。
🔗 https://openai.com/index/our-decision-on-cursor-following-its-acquisition-by-spacex/

**2. Codex 重置付费用户额度 + 修复消耗 Bug（与你直接相关）**
8月29日 Codex 负责人 Tibo 为所有 Codex/ChatGPT Work 付费用户重置使用额度，并公布一轮额度异常消耗修复：涉及图片压缩、Memory、/goal、Automation、子代理、历史摘要、MCP。异常 /goal 个别案例曾吞掉周额度 15%~70%，旧版 Computer History 每周最多耗约 1/5 额度。修复后同样额度预计可多撑 10%~50% 使用量，官方将提供应用内额度消耗明细。Tibo 称「庆祝」顺延至次日，社区猜测可能还有后续重置。
🔗 https://x.com/thsottiaux/status/2093801758665715784

**3. Anthropic 调整 Claude Code 每周限额（9月14日生效）**
Pro/Max/Team/Enterprise 标准周额度永久提高 25%；但当前临时 50% 加成在 9 月 14 日前仍有效，届时新标准比现在实际额度**下降约 17%**。官方承认该变化，称将推出额度可见性/控制的新体验。
🔗 https://x.com/ClaudeDevs/status/2093742321473065266

## 行业动态

**4. 索尼音乐 + Warner Chappell 起诉 Anthropic 及创始人**
指控其用 BitTorrent 非法下载盗版书籍（创始人 Mann 被指下载超 500 万本）、从 Pirate Library Mirror 抓取至少 200 万本、爬取付费许可网站歌词训练 Claude。索赔每部作品最高 15 万美元，总金额或达数十亿美元。Anthropic 暂未回应。
🔗 https://techcrunch.com/2026/08/29/sony-music-warner-sue-anthropic-alleging-a-brazen-campaign-of-intellectual-property-theft/

## 开发生态

**5. 官方确认：CPA 在 Cursor 用 Codex 订阅仍被支持**
网友 Max Katz 提出用 CLIProxyAPI（CPA）在 Cursor 里继续用 Codex 订阅，Tibo 本人回复「确实继续支持」。但有用户质疑这和此前被禁的 sub2api 没区别，Tibo 未进一步解释。*注意：此做法处于灰色地带，官方态度可能变化。*
🔗 https://x.com/thsottiaux/status/2093573575869698091

**6. Warp 推出 /skill-doctor，自动诊断改进 skill**
评估并改进其他 skill 的工具：爬取历史 CC/Codex/Warp 对话 → 拆成 subagent 批次 → 按效率与代码质量 0~1 打分 → 筛出「失败」案例找可修补模式 → 生成改进报告。
🔗 https://github.com/warpdotdev/common-skills/blob/main/.agents/skills/skill-doctor/SKILL.md

## 一句话带过

- **Grok Bot X 插件上线**：付费用户连账号可获免费 X API 额度，支持搜帖/读时间线/看提及（🔗 https://x.ai/news/grok-bot-and-x）
- **豆包开学季活动**：学生认证免费领 3 个月标准套餐（营销活动，仅电脑版参与）

---
**今日信号**：OpenAI–Cursor 断供是本周最重大结构性变化，Codex 用户群（包括你我）正受益于额度修复；Anthropic 借机抢 Cursor 生态，但同时面临数十亿美元版权诉讼。已标记本期已读。
