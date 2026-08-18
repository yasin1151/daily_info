
# 🍊 橘鸦AI早报 · 2026-08-18

> 本期共 16 条，精选 10 条高价值内容（已跳过 GitHub 故障复盘、OpenAI 政策资助等低行动性新闻）。

---

## 要闻

**1. OpenAI 拿下 PORTS-Pike 数据中心大单，初始 4.25 吉瓦**
OpenAI 与 SB Energy、NVIDIA、美国能源部达成协议，租用俄亥俄州 PORTS-Pike 园区建 AI 工厂，初始部署 4.25 吉瓦（全园 8 吉瓦，NVIDIA 可能扩至余下 3.75 吉瓦）。OpenAI 为租户并支付租约，采用 NVIDIA 全栈 DSX 平台；NVIDIA 仅为租约和电费特定部分担保，2028-2030 年分阶段投用。算力军备竞赛再上量级，三巨头绑定加深。
🔗 https://x.com/OpenAINewsroom/status/2089364481478721572

**2. Claude Code 上线 /design 功能**
研究预览版，把 Claude Design 的画板工作流带进 CLI 和桌面端：运行 /design 生成可编辑 UI 画板，Claude 会读代码库、匹配现有 UI 风格、产出可分享 mock，挑选后直接交给 Claude 实现。面向 Pro/Max/Team/Enterprise，更新到最新版即可用。UI 原型 → 代码落地链路进一步缩短。
🔗 https://x.com/ClaudeDevs/status/2089471692762673408

## 模型与成本

**3. OpenCode「Operation Cheepseek」：10 美元换 30 美元 DeepSeek-V4-Flash 额度**
第一阶段完成，Go 订阅用户付 10 美元即可获得 30 美元 DeepSeek-V4-Flash 用量，第二阶段已启动（细节未披露）。对 DeepSeek 重度用户是实打实的羊毛，也说明推理成本战还在继续。
🔗 https://x.com/opencode/status/2089428008268402786

**4. GPT-5.6 Sol 半价一个月**
OpenRouter 与 Vercel AI Gateway 同步五折，均持续至 9 月 18 日。OpenRouter 覆盖 batch/flex/priority 档，仅限 OpenAI provider、不含 BYOK；Vercel 的 standard 和 fast 均适用。降本窗口一个月，依赖该模型的应用可以趁机压测。
🔗 https://openrouter.ai/openai/gpt-5.6-sol

**5. Qwen-Audio-3.0 系列语音模型正式上线**
包含 ASR（识别）、TTS（合成）、Realtime（实时对话）三款模型，千问平台开放 API 调用，也可订阅 Token Plan（限时优惠），已落地千问 App、千问办公、Qoder。语音交互全家桶就位，开发者可直接对标 Whisper/实时语音方案。
🔗 https://mp.weixin.qq.com/s/yb4-PDno5NaacES9RfxIEA

## 开发工具与 Agent

**6. Cursor 上线 Origin 代码托管平台**
早期测试版向所有付费用户开放：仓库、PR、代码浏览、GitHub 双向同步（推送仍发到 GitHub），Agent 原生功能即将推出；Vercel、Depot、Buildkite 已集成。Cursor 从编辑器向托管平台延伸，直接叫板 GitHub——「AI 原生的代码托管」开始成型。
🔗 https://cursor.com/changelog/origin-code-hosting

**7. yetone 开源 Cumora：AI Agent 成为团队正式成员**
跨平台团队聊天应用，Agent 与人类共用名单、私聊、群聊、看板和日历，拥有人设、记忆和状态，可主动发起对话、认领任务、收发真实邮件。两种模式：Cumora Cloud（托管独立 Pod + OpenAI Responses API）或 BYOA（本地 Claude Code/Codex CLI 当大脑，密钥不经过服务器）。完整开源，需 Postgres + Redis。Agent 协作从"工具"走向"同事"的代表作。
🔗 https://github.com/yetone/cumora

## 行业与安全

**8. Groq 完成 3.5 亿美元融资，转型 neocloud**
Disruptive 领投、NVIDIA 计划参投，估值 35 亿美元。Groq 正从 AI 芯片商转型为推理云服务商：运营 13 个数据中心、服务 600 万+ 开发者，计划 2027 年算力从 54MW 扩至 200MW+。芯片公司集体"下场卖云"，推理层竞争格局生变。
🔗 https://groq.com/newsroom/groq-closes-usd350-million-series-a-building-the-world-s-leading-ai-inference-cloud

**9. OpenAI 披露安全防御四大支柱，暗示 8 月底发开放权重模型**
继 OpenAI/Hugging Face 入侵事件后发文：① Codex 部署前验证代码并修漏洞；② 安全告警先 AI 分诊再人工；③ 前沿模型持续枚举攻击路径；④ 纵深防御+最小权限。建议安全团队申请 Trusted Access for Cyber 用 GPT-Daybreak-Blue。文中还透露：最新一款带网络能力的开放权重模型计划 8 月底发布，很可能显著加速威胁格局——值得紧盯。
🔗 https://openai.com/index/the-defenders-window/

**10. 字节跳动与美国电影协会签版权协议**
据路透社，协议覆盖 Seedance（视频）和 Seedream（图像）两款生成模型。此前 MPA 曾发停止侵权函，迪士尼等担心 AI 生成受版权角色和名人肖像；字节称新版模型已内置更强的知识产权保护。好莱坞与 AI 公司从对抗走向契约，版权合规成出海模型标配。
🔗 https://www.reuters.com/legal/litigation/bytedance-signs-ai-copyright-pact-with-hollywood-trade-group-2026-08-17/

---

**本期看点**：算力基建（OpenAI 8GW 大单、Groq 转型）、AI 原生开发工具加速（Claude Code /design、Cursor Origin、Cumora）、以及 8 月底可能出现的"带网络能力的开放权重模型"——安全与开源的交汇点值得持续跟踪。
