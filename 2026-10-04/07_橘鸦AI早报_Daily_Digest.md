
【橘鸦AI早报 · 2026-10-03】共 19 条，筛选 10 条高价值摘要

**要闻**

1. **付费 ChatGPT 额度全局重置** — Codex 负责人 Tibo 表示，面向所有付费 ChatGPT 账户的全局重置已全部生效；此前 GPT-6.1 Sol 发布后头两天因负载激增运行缓慢，现该模型已恢复预期速度。对你的影响：Plus/Pro 的 5 小时与周额度回到满格。
https://x.com/thsottiaux/status/2106131810921136451

2. **Gemini 免费用户自 10/9 起只能用 Flash-Lite** — Google 帮助文档更新：未订阅 AI 方案的个人账号仅剩 Flash-Lite；Flash 需 AI Plus，Pro 需 AI Pro/Ultra。免费版额度被实质性压缩，明显是在推免费用户转订阅。
https://support.google.com/gemini/answer/17004136

3. **Karpathy 分享"读懂模型输出"的技巧** — 他认为随着模型自主完成的工作变多，人的重心会从写转向监督与理解，建议让模型用 ASD-STE100 受控语言（原用于航空维修手册，限制词汇+短句）解释，或生成图表/交互网页/按主题定制的讲解视频。这套提示词思路对做 agent 监督的人可直接借鉴。
https://x.com/karpathy/status/2105819303471976479

**开发生态**

4. **Claude Code 新增 "You should Know" 插件** — 以 mod 形式派生一个 sideagent 观察 Claude 的输出，提示用户可能漏看的重要信息，长任务里减少"跑完才发现跑偏"。启用命令：`/plugin enable cc-plugin-you-should-know@builtin`。
https://x.com/ClaudeDevs/status/2106118517447876618

5. **Cua Spaces 上线 macOS：给 AI agent 用的沙箱桌面** — 免费且源码可用，创建名为 Space 的沙箱虚拟电脑供 agent 直接操作；权限预授权、工具预装，Teleport 可把本地应用会话迁入（免重新登录），敏感项目需 Touch ID，数据默认锁在本机 Keyvault；用户与 agent 共享桌面、各有独立光标，可随时接管。可跑在本机 Mac、自备 Mac mini/Linux 或自有云。
https://github.com/trycua/cua/tree/main/apps/cua-spaces

6. **llama.cpp 支持"决策模型"，新增 `v1/systemone` 端点** — 发送状态（文本/JSON/截图）加若干问题，模型单次前向传播即返回各选项概率（choice/score/noul 三类）；接口沿用 System One 格式，现有客户端只需换 base URL。官方配 Julia-1、Laya、Kev-4B、lev、OpenJev 五款 GGUF（OpenJev 支持图像输入）。
https://huggingface.co/blog/ggml-org/decision-models-in-llamacpp

7. **Meta 开源 Muse Gadgets 硬件项目** — 以 Apache 2.0 开放 ESP32 固件与 Linux 设备 SDK，开发者可把现成开发板或树莓派做成接入 AI 助手 Muse 的自制设备；需在官网申请 SDK token 后在 App 开发者模式配对。同步公布 USB-C 供电的 Home Link（首批 5000 台，订阅者免费领）。个人 AI 硬件多了个开放入口。
https://github.com/facebookincubator/muse-gadget-sdk

**产品应用**

8. **ChatGPT Finances 向美国 Free/Go 用户推出** — 可通过 Plaid、Experian 连接账户，让 ChatGPT 基于本人财务数据回答问题：找回仍在扣费的遗忘订阅、发现陌生扣款或重复付款、看哪些循环账单涨价、生成每周财务更新与支出结构，并支持预算、信用分追踪、还债与应急基金测算。财务助手从付费下放到免费层。
https://x.com/ChatGPT/status/2106083592522932320

**技术与洞察**

9. **剑桥 CASP 发布"智能爆炸"研究，Hinton/Bengio 等署名** — 文章称 AI 系统现在已编写构建这些系统公司内部的大部分代码，几年内或自动化大部分甚至全部 AI 研发，进展可能被压缩为数月；初步证据显示这有可能发生。建议政策制定者紧急掌握自动化研发情况、开发约束手段。Hinton 同日发帖称递归自我改进"此前不像迫近，现在可能很快发生"。顶级研究者对 AGI 风险时点的一次公开背书。
https://x.com/geoffreyhinton/status/2106122709285368061

10. **苹果将收紧 macOS 完全磁盘访问权限** — 官方通告称将引入额外管控，需非常明确的操作才能授权；理由是部分开发者滥用该权限（可绕过系统隐私控制，访问文件、邮件、信息、浏览历史）。苹果特别点名"随着 AI 智能体能力与自主性增强，这类高权限风险将大幅增长"。涉及 macOS 27 等系统，具体形式与时间未公布。对 agent 类桌面应用是明确的收紧信号。
https://developer.apple.com/news/?id=p6zjojqw

**其他一句话看点**
- Anthropic 投 1 亿美元办 Claude Frontier Academy，2027 年底前培养 1 万名前沿部署工程师，首批来自埃森哲、德勤、麦肯锡、摩根士丹利等。
- arXiv 限额：10/1 起每位提交者每自然月最多两篇，应对 AI 生成低价值论文涌入（9 月投稿 4.04 万篇，两年翻倍）。
- 博通为 Anthropic 等安排 600 亿美元 AI 芯片融资（含 420 亿美元 A 类高级担保份额），尚未正式公布 — 传闻。
- OpenRouter 上线模型路由基准页，Jev Router 与 Pareto 并列 9.1，仍低于单模型 GPT-6-Sol 的 9.4；提醒路由并非总更优。

已标记 2026-10-03 期（ID 6401）为已读，当前无未读文章。
