
**橘鸦AI早报 · 2026-11-12 期摘要**

---

**1. Google 发布 Gemini Decisions 1：不写文字，只给出“判断”**
新模型驱动的 Gemini Decisions API 已在 AI Studio 开放，专用于“从有限选项中做决定”的场景，比如工具选择、政策检查、模型路由。它不逐个 token 生成文本，而是直接给候选选项打分；一次请求最多评估 1000 个问题（支持文本、图像、音频、视频、PDF），返回概率和 0~1 的置信度，端到端延迟 150~250 毫秒，上下文为 262K token。
影响：这是把 LLM 从“生成器”改成“分类器/裁判”的一条新路径；在 Agent 的循环里，路由和校验可以做到成本极低、速度极快——输入每百万 token 0.1 美元，输出不计费，免费档也可用。
https://blog.google/innovation-and-ai/technology/developers-tools/gemini-decisions-api/

**2. 通义千问官宣 Qwen4，Qwen4-Max 预览版已可试用**
官方称 Qwen4 在知识、世界理解、编程和 Agent 能力上更强，并显著提升 EDA、CAD、Blender、UE5 等专业软件的操作能力。预览版 Qwen4-Max 已在 Token Plan 开放（月价 39~312 元四档），Qoder 的匿名测试模型 Qoduck 直接升级为该预览版，计费限时两折（系数 0.5×→0.1×）。
影响：国产模型开始把“能不能操作专业软件”当作新的竞争维度，这也是 Agent 落地时最难突破的一环。
https://mp.weixin.qq.com/s/J_zbVHa2R3mmY5KD4v3-bw

**3. 上海创智学院开源 Nex-N2.6：321B 多模态 Agent 模型**
基于 GLM-5.3-Flash 构建，支持文本、图像和视频输入，FP8 权重已上线 GitHub / HuggingFace。最值得注意的是工程指标：推理复读率从 16.0% 降到 1.6%（相对下降 90%），整体调用未循环率 97.8%；OSWorld 83.0 分、Terminal-Bench 2.1 84.1 分（团队自报）。
影响：在长程 Agent 任务中，“不复读、不卡死”比跑分更影响实际可用性，这个改进方向很务实。已上线 OpenRouter 和 MOSS，256K 上下文 API 可用。
https://huggingface.co/nex-agi/Nex-N2.6

**4. 百度 ERNIE 5.5 Flash Preview：280B 总参、14B 激活、1M 上下文**
首个后训练版本，生成速度超过每秒 200 tokens，API 已上线千帆，权重 11 月 25 日前开源。官方明确说这是后训练过程中的中间版本，仍存在训练不充分导致的能力缺陷。
影响：长上下文加上低激活参数是当前主流配置；百度把中间模型直接放出来收集反馈，说明开源节奏在加快。https://ernie.baidu.com/research

**5. 阿里 Qwen Code 1.0 Preview：终端编程 Agent 变成可嵌入的内核**
把 Qoder 里打磨的 Harness 能力放进同一套 Apache 2.0 开源内核，提供 CLI 和 SDK，集成 SubAgents、MCP，支持 OpenAI、Anthropic、Gemini、Qwen 多协议模型接入和动态工作流。独立分支开放，暂不收社区 PR（预计 12 月后）。
影响：从“一个 CLI 工具”升级为“别人可以拿来搭自己 Agent 产品的基础设施”，直接对标 Claude Code / Codex 的生态位。11/11–11/24 用 Qoder 账号登录可领 Qwen4 免费额度。
https://qwenlm.github.io/qwen-code-docs/1.x/

**6. Google Antigravity 上线 Browser use：Agent 能自己开浏览器验证改动**
Agent 可用内置浏览器查资料、与运行中的应用交互、验证修复效果，能读取控制台报错、失败的网络请求、截图并检查视觉修复。App（v2.30.0+）支持自然语言触发或 `/browser` 命令；CLI 和商业版通过 Chrome DevTools MCP 连接本地 Chrome 144+。
影响：编码 Agent 的闭环从“改代码”扩展到“跑起来看对不对”，这是自动修 bug 真正可用的前提。
https://antigravity.google/docs/browser

**7. Gemini API Managed Agents 可接入自托管 Linux 沙箱**
Shell 命令和文件操作在用户自己的 worker 上执行，Agent 循环和模型调用仍在 Google 侧；基于开源的 gemini-api CLI，走**出站 HTTPS**，无需开放入站端口。Beta 状态，官方要求 worker 跑在容器/microVM/VM 中，本机模式仅供测试。
影响：企业最在意的“代码和数据不出自己的基础设施”这一顾虑被绕开了，同时保留了托管 Agent 的编排能力。
https://aistudio.google.com/docs/agent-environment

**8. Grok Bot 1.0：Bot 能共享给团队，还能进会议记笔记**
可在 Slack / Teams 中团队协作，加入 Google Meet、Zoom、Teams 会议做笔记、在会议聊天里回答问题，会后发摘要和行动项，并会主动发现待办、跟进未完成任务。向 Team / Enterprise / Ultra 订阅开放。
影响：从“个人助手”走向“团队同事”，会议记录这块是各家必争的高频入口。https://x.ai/news/grok-bot-1-0

**9. OpenAI 研究：模型越智能，思维链越难监控**
以“无 CoT 能力”和“CoT 可控性”为代理指标，发现前者随基础模型困惑度下降而平滑提升，也就是说模型越来越不需要写出推理过程。更关键的是：在 Astra 级模型上，**即使没有任何过程监督，仅靠最终答案的强化学习，CoT 可控性也会大幅上升**；用更可控的教师模型做 SFT，能把这一特性传给下一代。
影响：CoT 监控作为对齐手段正在失效，而且这种“可控”会沿模型谱系继承。OpenAI 也承认 CoT 可控性是对抗性监控逃避的嘈杂代理。
https://alignment.openai.com/cot-monitorability-model-lifecycle

**10. 行业：OpenAI Q3 营收 100 亿美元、亏损 109 亿；Anthropic 称 Claude 三天完成 AMD 芯片适配**
OpenAI CFO 确认 Q3 营收环比增近 50% 至 100 亿美元，年化约 500 亿，企业业务环比翻倍、与消费者各占一半；当季经营亏损扩大到 109 亿美元，调整后经营利润率从 -150% 改善至 -109%。
另一侧，Anthropic IPO 路演披露内部模型 Claude Mythos Preview 用约 3 天、几乎无需人工干预，就把一个 Claude 模型的提示处理任务移植到 AMD MI355X 并达到可用性能——传统工程方法通常要 6~12 个月。Dario Amodei 还预测癌症、阿尔茨海默、心脏病等将在不到 10 年内成为过去。
影响：一边是收入高速增长但仍在亏损，一边是“AI 自己加速 AI 基础设施适配”，后者对芯片供应格局的长期影响更值得关注。
https://finance.yahoo.com/technology/article/openai-cfo-q3-was-a-blockbuster-quarter-revenue-jumped-50-225023234.html ｜ https://ipo.anthropic.com/us/#roadshow-video

---

**⚠️ 待核实的重大传闻**：WSJ 报道称 NVIDIA 董事会正准备罢免创始人兼 CEO 黄仁勋，最快当地时间周三开会决定，报道称与其婚外情调查有关。此条仅有 WSJ 单一信源，早报本身也标注“前瞻与传闻”，建议等 NVIDIA 官方回应再采信。https://www.wsj.com/business/nvidia-is-preparing-to-oust-nvidia-ceo-jensen-huang-30f421ad

已标记该期（article 7346）为已读，当前无未读文章。
