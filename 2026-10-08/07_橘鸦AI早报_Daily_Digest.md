
**橘鸦AI早报 · 2026-10-07** — 原文：https://daily.juya.uk/issues/2026-10-07/

**要闻**

**1. Mistral Large 4 上线，月底开放权重**
旗舰模型公开预览版（昵称 Le Chonk）即日通过 API 开放，开源权重计划 10 月 31 日放出。原生多模态细粒度 MoE，总参数 1.05T、每 token 激活 49B，原生支持 160 多种语言。官方评测在 Artificial Analysis Cyber Index 位列全球前五，漏洞复现与修复得分 82% 为所有模型最高；与 Surge AI 的编码盲测排名第二，仅次于 Claude Opus 5；Lakera 攻击测试抵御率 93.3%，欧洲端到端训练。值得关注：又一家把「万亿总参、50B 激活」路线做到开源权重，且主攻网络安全定位，OpenCode 已上线并两周半价。 https://mistral.ai/news/mistral-large-4/

**2. Google 发布 Nano Banana 2.1，图像生成与编辑全面升级**
图像生成/对话式编辑模型 gemini-nano-banana-2.1 在 Gemini API 正式可用，并推送至 Gemini 应用、搜索 AI Mode、AI Studio、Flow 等。支持最多 14 张参考图多图融合、搜索 grounding、可配置 Thinking，输出覆盖 1K/2K/4K，修复超宽画幅拼接瑕疵。第三方 Arena 榜列多图编辑第四、文生图第五、图像编辑第六，较上代提升 38–80 分。Google 的 Logan Kilpatrick 称质量更高、修 bug、价格更低。值得关注：图像编辑赛道迭代明显加速，且官方强调「更便宜」——直接压向竞品定价。 https://blog.google/innovation-and-ai/technology/developers-tools/embeddinggemma-2/

**3. OpenAI 公开一批内部前沿模型产出的数学成果**
722 份手稿按 372 个成果族整理公开在 GitHub，附部分证明的 Lean 形式化、10 份推理摘要与统计，形式化将随取得继续补充。绝大多数成果由同一未发布内部模型以固定流程取得，评测中提出约 4000 个开放研究问题，平均每成果耗约 3 小时 ChatGPT Pro 思考算力。OpenAI 明确：成果处于不同验证阶段，未形式化部分可能有问题。值得关注：这是 lab 首次大规模公开「未发布模型」的科研产出，验证与署名规范成了新问题。 https://openai.com/index/sharing-ai-progress-in-mathematics/

**模型 / 开源发布**

**4. 谷歌开源 EmbeddingGemma 2 多模态嵌入模型**
把上代纯文本能力扩展为原生多模态，文本/代码/图像/视频/音频统一映射到 768 维向量。基于 Gemma 4，740M 参数模块化设计（纯文本仅需 270M，视觉 170M、音频 300M 可选加载），上下文 8192 token 为前代 4 倍，单次可处理约 5.5 分钟音频或 29 张图。MTEB Code 从 68.76 升至 78.68。Pixel 11 Pro 上纯文本权重约占 191MB 运行内存。Apache 2.0，权重已在 Hugging Face 与 Kaggle 开放。值得关注：端侧 RAG 的关键拼图，多模态 + 灵活维度对手机/边缘场景很实用。 https://blog.google/innovation-and-ai/technology/developers-tools/embeddinggemma-2/

**5. 复旦、腾讯混元、浙大开源 Prism，原生 2K 音视频联合生成**
动态稀疏注意力框架，技术报告、训练推理代码与预览权重同步放出，MIT 许可。预览模型支持 720p/1080p/2K 原生音视频联合生成与训练，文生视频、图生视频均可，提示词用 music/sfx/speech 标签分别控制配乐、音效、台词。官方称较全注意力训练提速 2.5 倍且质量更高。720p 推理单张 80GB 显存即可，2K 训练至少需 64 张。值得关注：音视频一体化生成的开源方案，from-scratch 原生训练而非「先视频后配音」的拼接路线。 https://github.com/Tencent-Hunyuan/Prism

**6. 亚马逊 AGI 团队开源扩散语言模型 ALoDLM-8B**
公开 1.7B 与 8B 两档权重及训练推理代码，由 Qwen3-1.7B/8B 直接 SFT 而来。核心改动是在每个去噪步内按 token 难度分配计算：置信度足够的 token 提前提交并作为上下文，其余保留潜在状态继续精炼，最多循环 4 轮。论文评测 11 项基准均分 65.5 / 80.3，均超对应 Qwen3 自回归基线。8B 在 GSM8K 上吞吐约为 vLLM 部署 Qwen3-8B 的 2.7 倍。权重为 CC BY-NC 4.0，非商用。值得关注：「并行生成 + 自适应精炼」开始追上自回归质量，吞吐优势值得跟踪，但非商用许可限制了落地。 https://huggingface.co/amazon/ALoDLM-8B

**开发生态**

**7. OpenAI 免费开放 Auto-review，不占订阅额度**
Codex 负责人 Tibo 宣布，所有通过 ChatGPT 账号登录的用户均可免费使用，且不消耗订阅用量，设置 → 权限 → auto-review 开启。机制是长任务中由第二个 agent 审查主 agent 的每一项操作，拦截高风险动作、防止偏离用户原始意图。Tibo 称其改进了默认沙箱需逐项批准、易造成决策疲劳的问题，并建议用它替代 full-access 权限。值得关注：agent 安全从「人审」转向「agent 审 agent」，且免费化是明显的 adoption 驱动。 https://alignment.openai.com/auto-review/

**8. OpenAI 向所有开发者开放 Decisions API 公测**
让应用在近实时条件下选择合适的模型、工具或动作，由 GPT-6 Luna 驱动，支持文本与图像输入。三类输出：Predicates 估概率、Choices 从预定义选项选择并给置信度、Scores 按数值区间评估。官方称比通过 Responses API 调用 GPT-6 Luna 最快快 10 倍，仅收输入 token，每百万 0.1 美元，无缓存/输出费用。典型用途：请求路由、大规模标注与评分、截图决定动作、标记高风险工具调用。值得关注：把「路由/判定」抽成独立廉价 API，是 agent 编排降本的关键一步。 https://developers.openai.com/api/docs/guides/decisions

**产品应用**

**9. Claude 上线 Google Workspace 插件，并悄然支持简繁中文界面**
Claude for Google Workspace 公开测试版面向所有付费方案：在 Docs/Sheets/Slides 侧栏读取当前文件与选中内容并直接编辑，默认每次修改需批准，可切换自动应用；表格可写公式、建透视表与原生图表，幻灯片按现有版式生成新页。同批推出 Docs/Sheets/Slides 连接器，可在 Claude 对话中创建编辑 Google 文件。另外多名用户发现网页版与桌面端新增简繁中文界面，可在设置切换；另有用户发现部分地区订阅页显示支持银联国际卡，但尝试支付订单被拒。值得关注：办公套件正成为 agent 主战场；中文界面 + 银联入口透露出对中文市场的试探，但支付环节仍不通。 https://claude.com/resources/articles/claude-now-works-in-google-docs-sheets-and-slides

**技术与洞察**

**10. GitHub 重建 Git 基础设施，面向 Agent 规模开发**
为支撑开发者与大量 AI Agent 并发读写仓库，改造在平台持续运行中推进，用户无需改变构建方式。过去一年 GitHub 月度 Git 事件从 2182 亿增至 4733 亿；9 月单月提交 73.8 亿次（一年前五倍多），推送量同比增 4.9 倍至每月 33.5 亿次。旧 Spokes 架构把持久化与读扩展耦合，加读副本会拖慢写入；新架构把协调范围缩小到真正需要一致性的引用更新，维护工作移出服务路径，权威数据存入 Azure Blob Storage，读容量改由轻量缓存节点提供。内部基准写入吞吐最高达原来 35 倍。值得关注：agent 流量已经在重塑最底层代码基础设施的架构设计。 https://github.blog/engineering/architecture-optimization/building-git-infrastructure-for-agent-scale-development/

**简讯**

- **SemiAnalysis 实测：Anthropic 订阅价值约为 OpenAI 五倍** — Claude 订阅跑 Opus 5.5 的 API 等值价值约为 OpenAI 跑 GPT-6.1 Sol 的 5 倍；200 美元 Claude 方案用掉约 2485 美元仍剩一半额度，OpenAI 同档约 2897 美元即耗尽。报告估算订阅约占 Anthropic 收入 10%，却占用超 40% 推理算力。 https://newsletter.semianalysis.com/p/anthropic-subscriptions-offer-5x
- **Nous Research 发布 Hermes Index 智能体模型榜** — 用 Hermes Bench、Terminal-Bench 4.0、Terminal-Bench Science、SkillsBench 四套件均分与平均每任务成本评测。Claude Opus 5.5 以 63.31 分、约 4.99 美元/任务居首，GPT-6 Astra 以 56.25 分、11.61 美元列第二。 https://portal.nousresearch.com/bench
- **五角大楼确认停用 Anthropic 全部产品** — 美防部今年 2 月将 Anthropic 列为国家安全供应链风险，要求 8 月底前停用，但知情人称直到上周 Claude 仍被用于情报分析和对伊朗的军事行动；冲突起因是五角大楼要求移除安全护栏遭拒，Anthropic 已起诉特朗普政府。 https://www.bbc.com/news/articles/c5j9x9pr0240o
- **Opus 5.5 Agent 三天找出两种室温磁性半导体** — 90 多个 Agent 三天内运行数百次量子力学模拟，找出两种 Luttinger 补偿磁体候选，其中一个 KV[Cr(CN)₆] 早在 1999 年就合成过；Vals AI 强调带隙与自旋分选均未被测量，计算数据已公开在 GitHub。 https://x.com/ValsAI/status/2107204457738256749
- **谷歌 Docs 与云盘原生支持 .md 文件** — 点开即可见渲染好的链接与表格，支持实时编辑与评论，自 10 月 5 日起推送（部分用户需等最多 15 天）。谷歌员工称「Markdown 已成为人类与 AI 智能体之间的通用语言」。 https://workspaceupdates.googleblog.com/2026/10/preview-edit-and-collaborate-on-Markdown-files-natively-across-Drive-and-Docs.html
- **融资/IPO 潮** — OpenAI 洽谈至少 300 亿美元新融资（阿联酋基金或出资最高 100 亿，投前估值约 1.4 万亿美元）；DeepSeek 新一轮至少 800 亿元人民币、腾讯与宁德时代领投，总额或近千亿；月之暗面完成上市前融资、估值约 500 亿美元、拟明年 Q1 赴港上市；快手可灵 AI 选定中金/高盛/瑞银筹备赴港 IPO，拟募资至少 10 亿美元。 https://www.bloomberg.com/news/articles/2026-10-06/deepseek-to-raise-at-least-12-billion-in-tencent-backed-funding

已标记该期（#6493）为已读。
