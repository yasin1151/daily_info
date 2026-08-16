
最新一期内容已抓取完成（2026-08-16，该期共 4 条新闻），已标记已读。重要发现：**橘鸦AI早报的 RSS 已迁移域名** —— 原 `imjuya.github.io/juya-ai-daily/rss.xml` 自 6 月起失效（GitHub 用户/仓库已删除），现已更新 blogwatcher 配置指向新地址 `https://daily.juya.uk/rss.xml`，以后每日推送恢复正常。

---

# 橘鸦AI早报 2026-08-16 摘要

## 🔥 要闻

**1. DeepSeek 团队成员亲推 dsh 极简模式 + V4 Pro 正式版**
据博主爆料聊天记录，DeepSeek 成员在群里推荐在 DeepSeek Harness (dsh) 中用极简模式跑 DeepSeek V4 Pro 正式版，称该模式"和 RL 训练对齐得比较好"；并明确答复运行环境"至少不能 Windows PowerShell"。还提到查看 dsh 的 commit 可见相关配置正是为对齐训练而加入。这等于官方认证了 V4 Pro 的最佳运行姿势——追求正确性和聪明度、不做前端等美学任务时，极简模式是首选。
🔗 https://x.com/xhyctf/status/2088445310557360203

**2. Codex Multi-agents v2：主 Agent 可调用 Luna 等模型**
OpenAI 团队集中宣传 Codex 的 Multi-agents v2 更新：主 Agent 现在可以把子任务交给包括 Luna 在内的不同受支持模型，部分模型可作为"只执行、不继续调度"的 sub-agent。改动其实此前已上线但关注度不高，8/15 Eric Provencher 发帖后 Greg Brockman 等多人转发造势。实质是 Codex 从"单模型多智能体"走向"多模型编排"。
🔗 https://x.com/pvncher/status/2088641056237580632

## 🎙️ 模型发布

**3. 小红书 FireRedTTS3 开源：21 种中文方言零样本克隆**
FireRed Team 发布统一语音生成与编辑模型 FireRedTTS3（Apache-2.0）：
- **Base 版**：支持 24 种语言 + 21 种中文方言零样本克隆，Seed-TTS-eval 平均 WER 3.04%、说话人相似度 78.8%，官方称对比模型最佳；
- **Instruct 版**：支持自然语言语音设计 + 语义/声学两类语音编辑。
方言 TTS 覆盖度是目前开源梯队里最高的之一，代码和权重均已放出，值得本地试玩。
🔗 https://huggingface.co/FireRedTeam/FireRedTTS3

## 🛠️ 开发生态

**4. Devin 免费开放 SWE-1.7 与 GLM-5.2 一个月**
Devin 宣布 Pro、Max、Teams 订阅用户即日起一个月内免费使用 SWE-1.7 和 GLM-5.2 两个模型，Devin Desktop 和 Devin CLI 均可。本质是借订阅用户扩大模型组合的测试面，但对用户来说等于白嫖一个月多模型切换能力。
🔗 https://x.com/devindesktop/status/2088383979997241794

---

📌 **运营提示**：feed 迁移后 blogwatcher 已自动补抓最近 10 期（8/7–8/16），本次仅摘要最新一期；如需补看之前某期可随时告诉我。
