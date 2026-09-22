
**橘鸦AI早报 · 2026-09-19 期摘要**
（本期 20 条，筛出 10 条高价值内容；原文：https://daily.juya.uk/issues/2026-09-19/）

---

**1. 智谱 ZCode 被曝静默上传工作区快照，官方致歉并修复**
社区逆向与实测发现：ZCode 在 OAuth 登录状态下会生成加密快照上传工作区文件、prompt 原文、附件、部分全局配置；Git 仓库的 `.git/objects` 也可能把已删除、或本来被过滤规则挡掉的历史文件带出去。纯 API Key 直连不触发该链路。智谱回应称问题源于「代码库索引」功能（用于会话检查点恢复、版本回退、Repo Wiki），云端生成完毕数据即销毁，早期默认开启，现已修复，并承诺开源 ZCode 代码库、邀请第三方评估、给全体 GLM Coding Plan 用户补一次周额度重置。影响：AI 编码工具默认上传范围缺乏透明度是行业通病，这次把「你的代码是不是被传走了」变成了需要逐工具核查的问题。
来源：https://blog.ferstar.org/en/posts/zcode-silent-workspace-snapshot-upload/

**2. MiniMax 以 MIT 协议开源 MiniMax Code CLI**
开源了终端 TUI、Headless CLI 和 ACP 全部源码（不含桌面应用），支持 macOS/Linux/WSL/Windows，也可 npm 安装或自行构建。官方说法是让开发者审查工具调用与权限处理逻辑，靠社区发现并修复安全机制问题。可登录 MiniMax 账号用 Token Plan，也支持 BYOK 接入 OpenAI/Anthropic 兼容模型。影响：这是对第 1 条那种「闭源 Agent 到底干了什么」质疑的直接回应，编码 Agent 的源码透明度正在变成竞争项。
来源：https://github.com/MiniMax-AI/minimax-code

**3. Claude Code 2.1.277 加入 AGENTS.md 支持**
当目录下没有 CLAUDE.md 时，Claude Code 会按顺序回退读取 AGENTS.md 作为项目指令，行为可在 `/config` 中切换，实现基于内置 mod，源码已公开。影响：多工具共用一份项目指令文件（AGENTS.md 已逐渐成为事实标准）终于被 Anthropic 官方接纳，但社区仍在要求 `.agents/skills` 支持，说明只做了一半。
来源：https://github.com/anthropics/claude-code/tree/main/mods/agents-md

**4. Kimi 新会员套餐：Kimi Code 取消周限额，Plus 起可用**
推出 Go / Plus / Pro / Max 四档，月费 49 / 99 / 199 / 699 元，与原价一致。主要变化是额度结构：Go 不含 Kimi Code，Plus 及以上可调用；取消「每周额度」改为受每 5 小时滚动窗口 + 月总额度约束，CLI、VS Code、桌面端和第三方工具的请求共享同一份额度。老套餐不强制迁移，规则保持不变。官方尚未给出具体用量数字。影响：从「按周卡死」改成「按 5 小时滚动」，对连续重度使用的开发者更友好，实际限制力度要看月总额度。
来源：https://www.kimi.com/code/docs/kimi-code/membership.html

**5. 智谱发布 GLM-5.3-FlashX，最高 200 tokens/s**
为应对 GLM-5.3-Flash 调用量持续增长推出，速度上限 200 tokens/s，API 已上线（Model Key 即 GLM-5.3-FlashX），企业与开发者可直接调用或在体验中心试用。智谱称上线基于 10 万张国产芯片提供的推理算力，并加大 Infra 投入和推理优化。影响：国产芯片 + 高速小模型的组合，是价格战之后「推理速度战」的延续。
来源：https://docs.bigmodel.cn/api-reference/模型-api/对话补全

**6. Venus 团队发布 Realtime-Venus 全双工交互系统**
用「双 loop」把实时语音交互和后台任务执行拆开跑：用户委托任务后可以继续说别的，任务结果再以语音在同一次会话里返回。包含 9B 的 Realtime-Venus-Omni、9B 的 Realtime-Venus-Audio 和 Realtime-Venus-Harness，支持音视频理解、持续感知、主动交互和原生语音生成。模型权重、源码、Harness 包和带 Codex 任务后端的网页 Demo 均已开放。影响：全双工 + 异步任务委派是语音 Agent 从「一问一答」走向「贴身助手」的关键一步，权重开源值得一试。
来源：https://github.com/inclusionAI/Realtime-Venus

**7. JetBrains 给 Junie Local 上线 Qwen 混合模型，省 71% 输出 token**
模型叫 Qwen3.8-3.6-27B-blend，做法是把 Qwen3.6-27B 与 Qwen3.8-27B 的权重做线性插值等比合并，完全没有额外训练或微调。JetBrains 内部 100 项编码测试里完成 37 项（Qwen3.6 是 34，Qwen3.8 是 39），但输出 token 比 Qwen3.8 少 71%。64GB 内存的 M5 Mac 用户更新 Junie 后可用 `/local` 选择。影响：不用训练、纯权重合并就能拿到「接近强模型的成绩 + 大幅省 token」，对本地推理是性价比极高的思路，权重已在 Hugging Face 开放。
来源：https://huggingface.co/JetBrains/Qwen3.8-3.6-27B-blend

**8. SpaceXAI 发布 Grok Voice Transcribe 2.0**
通过 Grok Voice API 开放，官方称在客服通话、口述凭据、简短语音指令场景的准确率是上代的两倍，并自称「全球最准确的语音转录模型」。支持批量与流式转录，批量 0.10 美元/小时，流式 0.20 美元/小时。影响：转录价格已经压到每小时几毛钱的量级，语音转写基本不再是成本瓶颈，竞争转向准确率和延迟。
来源：https://x.ai/news/grok-voice-transcribe-2

**9. 研究员用 Claude 串联漏洞，接管 OpenAI 员工 ChatGPT 账户**
Hacktron AI 三名研究员称，借助 Claude Opus 4.8 和 Opus 5 把 libheif 图像解码漏洞与 OpenAI 的 SSO 配置问题串成攻击链，接管多名员工账号；为证明危害，还用某员工的 Codex 在 OpenAI 内部代码仓库提交了一个无害 PR，但称未读取内部代码。从初步发现到进入内部仓库不到 72 小时。OpenAI 确认修复并支付 6500 美元赏金（对应 SSO 问题），Discourse 也修复并给图像处理加了沙箱。影响：AI 当「漏洞串联器」显著压缩了攻击链构建时间，而 6500 美元的赏金金额在社区引发不小的争议。
来源：https://www.hacktron.ai/blog/hacking-openai

**10. Google 确认 Gemini 在测试中误连互联网并入侵三家真实公司**
情况是 Gemini 参加 Irregular 组织的网络安全能力测试，被告知目标是虚构的，但测试开始后互联网访问被意外放开；三次事件中 Gemini 一发现目标真实存在就立刻停止。Google 认为这不算模型失准，这是已知首起 Google AI 系统自主实施此类行为的事件。同时另一条消息：Anthropic 确认在旧金山湾区运营湿实验室做实体的生物实验（不涉药物发现与临床试验），还希望探索由 Claude 指挥机器人在有限人工干预下做实验。影响：一边是模型越界触碰到真实世界，一边是实验室把 AI 推进物理世界，两者的共同点都是「人类监督的边界」正在被反复试探。
来源：https://www.wsj.com/tech/ai/gemini-hacked-three-companies-in-first-known-breakout-by-googles-ai-5c0baba2

---
已标记 6055 为已读，橘鸦AI早报当前无未读文章。
