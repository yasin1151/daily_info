
**橘鸦AI早报 2026-11-21 摘要**

共 24 条，筛出 10 条真正有信息量的。

---

**1. 数学家称与 Claude 合作证明黎曼猜想**
Levent Alpöge 在自己网站发文，称与 Claude 一起找到了黎曼猜想的证明，方法还能推到广义黎曼猜想。他没有放论文，只放了无假设的 Lean 形式化代码（14 个文件），手写证明稿超过 25 万页，说等自己彻底理解并简化后再写常规论文。**影响**：如果成立这是世纪级事件，但目前零独立验证，社区普遍持怀疑态度，值得盯后续。
https://alpo.ge/remark.pdf

**2. Thinking Machines 开源 Inkling 2 Mini**
总参数 26.4B、激活 3.4B，looped transformer 架构（中段 12 层对每个 token 跑三遍），Apache 2.0 开放权重。官方称 DeepSWE v1.1 拿到 48.2%，领先所有 100B 以下开源模型。内存占用约 20GB，32GB 内存的 Mac 和 DGX Spark 都能跑 Ollama，已上 Tinker 可微调。**影响**：小体量本地可跑 + 代码能力对标大模型，是本周最实用的一次开源。
https://thinkingmachines.ai/news/inkling-2-mini/

**3. 腾讯混元开源旗舰 Hy4，770B 总参**
原生多模态 MoE，770B 总参 / 49B 激活，1M 上下文，文本图像视频通吃。权重 + GGUF 在 HF、ModelScope、GitCode 都能下，同时发了 System Card 安全评估报告，本周五在 r/LocalLLaMA 办 AMA。**影响**：国产开源第一次把旗舰级参数规模放出来，49B 激活意味着单机多卡可推理，对做私有化部署的团队影响直接。
https://huggingface.co/tencent/Hy4

**4. 微信开源全模态系列 WeMM-Video**
Apache 2.0，含 2B/4B/9B 稠密和 35B-A3B MoE，能同时吃文本、图像、音频、视频，处理视频时画面和原声轨一起用。35B-A3B 在全模态视频理解上刷新开源最好成绩，官方称超过 Qwen3.5-Omni-Flash 等闭源模型。提供 Instruct/Thinking 双模式和 FP8/AWQ/GGUF/NVFP4 量化。**影响**：音轨+画面联合理解是视频理解的真痛点，开源阵营补上了这块。
https://github.com/Tencent/WeMM-Video

**5. Codex 两项性能更新**
①对话线程重构，减少冗余记录，冷启动加载提速 60–70%，状态切换更顺；②模型请求 WebSocket 上限从 16MB 提到 128MB，大轮次不再回退 HTTP，整体回退率降约 20%，超限时服务器立即告知而非等传完再拒，处理速度提升约 5 倍。**影响**：长上下文、大工具输出的 Agent 场景体感会明显变好。
https://x.com/charliermarsh/status/2123849871480463669

**6. OpenAI API 为 GPT-6.2 启用跨轮推理复用**
Responses API 里 GPT-6.2 的 Agent 可跨轮复用推理，降 token 消耗、提缓存命中。但机制是刚性的：推理与前置对话绑定，一旦缩短工具输出、改写提示词或改请求参数导致前缀变化，后续推理直接丢弃，成本和延迟反而上升。新增 input_transformations 对象和 Reasoning removals 面板帮排查。**影响**：提示词工程要改成"只追加不改前缀"，这是个容易踩的坑。
https://developers.openai.com/api/docs/guides/keep-prefix-unchanged

**7. OpenAI 新防御把推理窃取成功率打到 0.2%**
针对"受保护推理"（模型作答时的内部中间步骤）做防护，自适应攻击成功率从 GPT-6 Astra 原防护下的 54.0% 降到 0.2%。研究还证实：用精确推理痕迹训练的学生模型，比只用推理摘要学到的网络安全能力多得多——蒸馏确实能绕过原始安全对齐。OpenAI 称今年每周处置的蒸馏滥用账号从数千到数万。**影响**：闭源模型的护城河从"权重不外泄"转向"推理不外泄"。
https://openai.com/index/combatting-adversarial-distillation/

**8. 数千 Agent 32 分钟做完几个月的生物数据分析**
OpenAI 联合 PerturbAI 和 Scripps Research，用数千个 GPT-Rosalind agent 并行分析小鼠全脑 CRISPR 图谱（基因扰动如何影响数百万脑细胞），人工估计要数月到一年。Agent 还发现扰动 Dctn1 会提高胆固醇合成基因表达，提出"恢复胆固醇分布或能保护神经元"的待验证假设。推理图谱已在 GitHub 开源。**影响**：这是"分布式生物推理"的样板，比单纯刷榜更能说明 Agent 集群的实际产出。
https://openai.com/index/scaling-ai-research-for-complex-biological-data

**9. 美众议院报告：Cursor 考虑逐步停用中国模型**
报告称 SpaceX 旗下 Cursor 已告知国会，因"地缘政治风险"正考虑逐步停用中国开发的开放权重模型。Cursor 的 Composer 2 正是基于月之暗面 Kimi K2.5 构建的。报告还建议推美国国家级开放权重计划，并在联邦系统及联邦合同履行中禁用中国 AI 模型。**影响**：开源模型"可商用"的地缘风险从纸面变成采购现实，出海团队的模型选型要开始算政治成本。
https://homeland.house.gov/wp-content/uploads/2026/11/2026.11.20-Joint-Report-PRC-AI-Models.pdf

**10. 传智谱将推 3 万亿参数 GLM-5.5**
流传的摩根大通研报称，智谱管理层预计 2026 Q4 推出约 3 万亿参数旗舰 GLM-5.5，是现有 7450 亿基座的 4 倍，目标重回全球第一梯队。另有一款 7000 亿参数模型正作为验证平台做后训练，性能已超 GLM-5.3，发不发未定。智谱重申年底 30 亿美元 ARR 目标，算力大部分在国内，受美芯片新规短期影响有限。**影响**：属未证实传闻，但参数竞赛重回 3T 量级这个信号值得记。
https://news.futunn.com/post/1004821534/navigating-through-noise-advancing-steadily-key-takeaways-from-the-tig

---

已跳过：Google 黑五订阅五折（促销）、Gemini GIF 生成、Claude App 移动端改版、CarPlay 呼叫 Dot、小米 MiMo 套餐上线（低价值产品更新）。文章已标记已读。
