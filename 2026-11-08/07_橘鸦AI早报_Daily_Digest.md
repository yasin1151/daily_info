
橘鸦AI早报（2026-11-07 期）

1. Qwen海报预告新旗舰模型
阿里官方账号发布一张写着「北冥有鱼 其名为_」的海报，配文「The becoming begins」，Qwen 开发者账号随后解释这是《庄子》里名为「鲲」的鱼，读音与 Qwen 相同。社区把这解释为下一代旗舰模型即将登场。官方没有透露任何参数、是否开源、上线时间。由此带来的直接影响是：阿里在自家模型发布方面正采用类似 OpenAI 的悬念式营销，但后续两周内国内模型榜单和企业采购很可能都会等这一款。值得盯的是它和 DeepSeek V4.1 系列的正面竞争。
https://daily.juya.uk/issues/2026-11-07/#1

2. 阿里开源手机端小模型 MNN-Pocket-0.3B
MNN 团队开源了约 3 亿参数的稠密语言模型，支持中英文、32K 上下文、Apache 2.0 授权；INT4 量化的 MNN 版本体积只有 173MB，官方称在 iPhone 18 Pro 上离线运行时平均解码约 350 token/s。意义在于：端侧模型第一次把「可用速度 + 可接受体积」放在一起，且完全开放商用，本地隐私类 App 的模型选型会明显变简单。局限是 0.3B 只能做轻指令类任务，不能代替云端大模型。
https://huggingface.co/taobao-mnn/MNN-Pocket-0.3B

3. DeepSeek V4.1 Flash 周边：降价、加价与提速同时发生
同一天有三条相关动向：OpenDesign 推出 Flash Eco 档，使用与标准版相同的权重、能力不降，只是优先级更低，Go 订阅每月仅 10 美元却给 220 美元额度；Command Code 上线 Flash 1017 Ultrafast，吞吐超 1000 token/s，输入 2.4 美元、输出 9.6 美元每百万 token；同时大量用户反映国内版 WorkBuddy 调用 Flash 的积分消耗明显上涨，但界面标价没变、官方未确认调价。结论是 Flash 正在被拆成「便宜慢速 / 昂贵极速」两个市场，中间商加价风险开始显现，用第三方平台跑批量任务的团队值得自己记一次账，核对成本。
https://x.com/CommandCodeAI/status/2118824521314783243

4. Google Antigravity 连续两天大改：语音 + 云端远程 Agent
负责人 Varun Mohan 为所有用户重置了 Gemini 和 Argon 额度；应用做了重设计，并上线由 Gemini Live 驱动的语音模式和 remote agents。语音模式下可以直接口头派任务、中途改方向、口头批准权限申请，Agent 实时语音回报、可随时打断，9 种音色、0.75–2 倍速。remote agents 面向所有付费个人订阅，任务跑在独立云 VM 里，不用开着自己电脑，单个项目可同时挂 GitHub 仓库和 Drive 文件夹。这是把「编码 Agent 从桌面工具变成常驻云服务」的一步，竞品中 Cursor、Amp 的云端化压力直接上升。
https://antigravity.google/blog/antigravity-voice-mode

5. Anthropic 双更新：手机接管 Claude Code 会话 + 云端环境自动配置
Claude Duet 新增 Claude Code 会话功能，手机上能看正在跑的任务、批准改动、发补充指令，本地和云端会话都支持，新版本正逐步推送。同时 Claude Code 云端会话会自动识别仓库需要哪些依赖、网络访问和 API key，并保存环境复用，API key 加密存储、Claude 自身读不到。影响是「离开工位就断线」这个痛点被消掉，长任务可以真正过夜跑；对做 CI 式自动化的团队，环境自配置省掉的正是最烦的那段初始化脚本。
https://x.com/ClaudeDevs/status/2118795192090386454

6. Cursor 上线与 Agent 的实时语音对话
开发者可以口头提需求、问进度，Agent 干活时播报简短更新，覆盖 Agents Window、IDE、网页和 iOS。语音层用的是 Grok Voice，编码仍走用户自选模型。每天有使用上限，需登录。评价：语音在这里不是噱头而是降低「盯着终端等」的成本，尤其是长任务里追问「现在卡在哪」；但同时说明 Cursor 在语音这类基础能力上开始外采而非自研。
https://cursor.com/changelog/voice-chat

7. Amp 推出 Spaces：一个主 Agent 调度多条线程
每个 Space 是用户与一个主 Agent 的对话，由它拆任务、创建并协调其他 Agent 线程，用户不用手工管多条会话。团队成员可在同一空间提需求、看任务状态、在消息下评论，但只有 @amp 提及时 Amp 才会读评论。任务卡片可点进对应线程看产出继续处理。这是多 Agent 编排从「框架层的概念」落到「产品里的默认交互」，关键设计点在那条「不 @ 就不读」的规则，否则多人空间里的噪音会瞬间淹没 Agent。
https://ampcode.com/news/spaces

8. Meta 给 Muse / Meta AI 换上专用模型，加记忆与抗打断
11 月 6 日起两款产品运行由 Muse Wonder 训练的专用模型，新增 Active Memory 和 Active Focus。前者区分临时与永久信息、跨时间推理并在旧信息重新相关时想起；后者遇到意外继续推进目标，会重试、回滚或换方案。官方数据：Muse 里遗忘关键信息的情况减少 2.4 倍，出现意外问题的日常任务完成度提升 67%；Personal Superintelligence Index 从 38% 升到 47%，Active Memory 评测从 76% 升到 90%。同时 Muse 推出 Spaces，可用对话生成规划器、追踪器、小游戏，连上常用应用后还会在后台更新演出日期、价格等信息。方向很清楚：消费级助手拼的不再是单轮智商，而是长期记忆和任务韧性。
https://research.meta.ai/blog/specialized-models-for-muse-and-metaai

9. Anthropic 介绍 Claude Dreams：后台整理记忆
Dreams 用异步任务整理已有记忆和历史会话，合并重复、更新过时或互相矛盾的条目，并生成互相链接的 wiki 页面方便后续检索。每个任务可输入 1 到 100 个会话，原记忆存储不被改写，新结果由用户审核后采用或丢弃。目前是研究预览，仅部分模型支持，按所选模型标准 API token 计费。这条和上面 Meta 的 Active Memory 指向同一件事：上下文管理正从「塞更多 token」转向「后台做记忆维护」，长跑 Agent 的可靠性会因此明显不同。
https://anthropic.com/research/components-of-agent-memory

10. AI 做科研的两条硬进展，以及一条硬件侧的连锁反应
Anthropic 用隐私保护方法分析了 20.7 万次 Claude / Claude Code 科研会话：数据分析占 Claude 会话约三分之一、占 Claude Code 会话近一半；测算若现有能力被广泛采用，可承担一项新研究所需研究者时间的 27%–52%（中位 38%），统计、计算机等领域产出最多翻倍，约 40% 高频使用 AI 的研究者预计 2030 年前模型能自主完成完整项目。同一时期，Physical Superintelligence 称其内部研究系统用非公开 Anthropic 模型在第 3 天找到量子计算 Aaronson-Ambainis 猜想的完整证明，两次改进后通过 Lean 验证，论文与形式化代码已公开。另有报道称应 NVIDIA 请求，台积电正考虑从 3D DRAM 切入内存业务，与美光、三星、SK 海力士竞争。三件事串起来看：模型能力已经开始反向拉动内存这类上游产能。
https://www.anthropic.com/research/how-researchers-use-claude

已标记该期（#7225）为已读。
