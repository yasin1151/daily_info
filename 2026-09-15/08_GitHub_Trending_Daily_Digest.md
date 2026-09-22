
# GitHub Trending 今日热门｜2026-09-15

## 新上榜（本次新增 3 个）

**1. oh-my-hermes — Hermes Agent 的一站式插件包**
简介：为 Hermes Agent 打造的 all-in-one 插件，整合编码智能、长期记忆系统和针对模型调优的工作流包。Python，于 2026-06-03 创建。
为什么值得关注：Hermes Agent 生态第一批社区插件里star涨得最快的之一，说明这套 agent 框架开始被外部开发者主动扩展；做记忆系统和 agent 工作流的人可以直接参考它的插件组织方式。
Stars：2,016（今日 +52）｜Python｜🔗 https://github.com/rlaope/oh-my-hermes

**2. localsend — 开源的跨平台 AirDrop 替代**
简介：跨平台局域网文件互传工具，Dart/Flutter 写的，Mac、Windows、Linux、iOS、Android 之间都能传。
为什么值得关注：Windows 和 Android 都收不到 AirDrop，这是实际痛点；项目创建于 2022 年，至今仍在活跃更新（最近提交 2026-09-14），9.1 万 star 说明已是成熟方案而非玩具。
Stars：91,291（今日 +311）｜Dart｜🔗 https://github.com/localsend/localsend

**3. opendisplay — 把 iPhone/iPad 变成 Mac 真正的第二屏**
简介：免费开源的 Sidecar/Duet 替代品，通过 USB 或 WiFi 把 iPhone/iPad 当 Mac 扩展显示器，支持 H.264 低延迟、Retina HiDPI 和触控输入。
为什么值得关注：苹果官方 Sidecar 限制多（不支持老机型、不稳定），Duet 要付费；这个 2026 年 6 月才出的新项目 3 个月做到 3.5k star，说明需求很硬。用 ScreenCaptureKit + VideoToolbox 实现，参考价值高。
Stars：3,544（今日 +258）｜Swift｜🔗 https://github.com/peetzweg/opendisplay

## AI / Agent / LLM 重点

**JustVugg/colibri — 纯 C 跑前沿 MoE 大模型** ★32,002（今日 +2,233，全榜第一）
零依赖纯 C 实现，把专家权重放磁盘上流式加载，让消费级硬件也能跑 frontier MoE 模型。今日涨星最猛，本地推理这条路线又被点燃了。
🔗 https://github.com/JustVugg/colibri

**alibaba/open-code-review — 阿里内部的代码审查工具开源** ★25,601（今日 +1,796）
混合架构：确定性流水线 + LLM Agent，做精确到行的评论，内置多语言规则集（NPE、线程安全、XSS、SQL 注入），兼容 OpenAI 与 Anthropic 接口。"在阿里规模上久经考验"是它最硬的卖点。
🔗 https://github.com/alibaba/open-code-review

**debpalash/VoiceStudio — 完全本地的 ElevenLabs 替代品** ★29,101（今日 +2,774）
语音克隆、音色设计、视频配音、听写、转录、有声书制作，支持 646 种语言，全程本地运行。商业 TTS 的高价与隐私问题在这类项目面前越来越难站住。
🔗 https://github.com/debpalash/VoiceStudio

**Panniantong/Agent-Reach — 给 agent 装上"看全网"的眼睛** ★81,210（今日 +640）
一个 CLI 读取和搜索 Twitter、Reddit、YouTube、GitHub、Bilibili、小红书，零 API 费用。agent 的数据获取一直是卡点，这个把常见信息源一次性打通。
🔗 https://github.com/Panniantong/Agent-Reach

**asgeirtj/system_prompts_leaks — 各家大模型系统提示词合集** ★66,738（今日 +770）
整理 Anthropic（Claude Fable 5.1、Opus 5、Claude Code）、OpenAI（GPT-6-Astra、Codex）、Google（Gemini 3.8 Flash、3.1 Pro、Antigravity）、xAI 等的系统提示词，持续更新。想学 prompt 工程，这是最直接的实战素材。
🔗 https://github.com/asgeirtj/system_prompts_leaks

**tech-leads-club/agent-skills — 安全校验过的 agent 技能注册表** ★6,042（今日 +506）
面向 Claude Code、Cursor、Copilot、Antigravity 的技能市场，主打"经过安全校验"。技能生态一旦铺开，供应链安全就会成为真问题，这个切入角度很准。
🔗 https://github.com/tech-leads-club/agent-skills

**SnailSploit/Claude-Red — Claude 技能形式的渗透测试武器库** ★4,700（今日 +606）
用 SKILL.md 打包的攻击方法论，覆盖 SQLi 到 shellcode、EDR 绕过到漏洞利用开发。同一套技能机制既能做防御也能做攻击，值得安全团队关注。
🔗 https://github.com/SnailSploit/Claude-Red

**multimodal-art-projection/YuE — YuE2 音乐生成** ★8,304（今日 +578）
主打符号化规划、零样本翻唱和 agentic 音乐编辑，生成质量路线从"能听"转向"可控"。
🔗 https://github.com/multimodal-art-projection/YuE

**OpenBMB/VoxCPM — 无分词器的多语言 TTS** ★37,352（今日 +204）
VoxCPM2 去掉 tokenizer，做多语言语音生成、创意音色设计和逼真克隆。TTS 架构层面的一次路线尝试。
🔗 https://github.com/OpenBMB/VoxCPM

**TauricResearch/TradingAgents — 多 Agent 金融交易框架** ★106,084（今日 +756）
用多个 LLM agent 分工做金融交易决策，10.6 万 star 说明"多 agent 协作"在金融场景已经是最热的应用范式之一。
🔗 https://github.com/TauricResearch/TradingAgents

## 开发工具 / 数据工程 / 其他

- **huggingface/transformers** ★165,955（+528）—— 模型定义框架，仍是整个 ML 生态的地基。🔗 https://github.com/huggingface/transformers
- **666ghj/MiroFish** ★73,114（+524）—— 通用群体智能引擎，声称"预测万物"，中文项目里少数做通用预测范式的。🔗 https://github.com/666ghj/MiroFish
- **reconurge/flowsint** ★8,330（+279）—— 面向网络安全分析师的图式调查平台。🔗 https://github.com/reconurge/flowsint
- **Crosstalk-Solutions/project-nomad** ★36,891（+26）—— 离线优先的知识教育服务器，可自带本地 AI、无需联网。🔗 https://github.com/Crosstalk-Solutions/project-nomad
- **dani-garcia/vaultwarden** ★67,520（+110）—— Rust 写的 Bitwarden 兼容服务端。🔗 https://github.com/dani-garcia/vaultwarden

---

**今日观察**：榜单上半区几乎被"本地/开源自托管"占据——本地跑前沿模型（colibri）、本地语音克隆（VoiceStudio）、本地知识库（project-nomad）、自建密码服务（vaultwarden）。同时 agent 生态正从"框架"下沉到"技能与数据接入"层（agent-skills、Claude-Red、Agent-Reach），说明竞争焦点已经从模型能力转向工具链与供应链安全。

已标记 3 条为已读，blogwatcher 队列为空。
