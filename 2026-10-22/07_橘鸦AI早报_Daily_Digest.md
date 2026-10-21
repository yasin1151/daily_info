
**橘鸦AI早报 · 2026-10-21 期**（共 20 条，精选 9 条）

**1｜DeepSeek 开源内部推理框架 DeepInfer ⭐️**
DeepSeek 开源了支撑其线上服务的推理框架 DeepInfer，并同步开源 token 编解码组件 deepseek-recipe。关键数字：V4.1 Flash 单集群每天处理 155 万亿 token，按时段最低价计算，每张卡每小时收入 38 美元，输入缓存平均命中率 96%。技术上支持分布式推理、DSpark 投机解码、SWA Bounded Replay、结构化输出；开源版采用 Apache 2.0，同时支持英伟达 SM100 和**华为昇腾 950 NPU**。这等于公开了“推理怎么做到既快又赚钱”的工程细节，国产算力适配也给了现成路径。
https://github.com/deepseek-ai/DeepInfer

**2｜ChatGPT 上线“锁定聊天”，支持 PIN / 面容访问**
覆盖 Free 到 Enterprise 全档位：对话移出常规历史、置顶和搜索，可设 4 位 PIN 或用 Face ID 解锁。有两个容易被忽略的问题：锁定聊天**不是端到端加密**，不改变聊天保留期限和“改进模型”设置；重置 PIN 会**永久删除**所有锁定聊天、其中文件和仅存于其中的记忆。适合隐私诉求，但企业合规层面别当成保险箱。
https://help.openai.com/en/articles/20001411-using-locked-chats-in-chatgpt

**3｜OpenAI API 新增 12 小时提示词缓存**
Responses API 中 GPT-5.6 及之后模型可选 12 小时缓存，可与默认 30 分钟在同一请求里混用（共享指令/工具走 12h，新对话走 30min）。写入费率为普通输入 2.5 倍 / 1.25 倍，读取费率不变。对“长系统提示 + 调用间隔不规律”的 Agent 是大降本，以前 30 分钟一过就白付全价输入。
https://developers.openai.com/api/docs/guides/prompt-caching

**4｜Google 开源原生 PyTorch 软件栈 TorchTPU**
与 Meta PyTorch 团队共同开发，现有 PyTorch 工作负载少量改代码即可在 TPU 上跑：eager mode 调试、torch.compile 优化利用率，已集成 Hugging Face、vLLM、SGLang、TorchTitan、Ray；Transformers v5 里直接 `device_map="tpu"`。意义在于把 TPU 从“要写 JAX”变成 PyTorch 生态的一等后端，CUDA 的单点锁定被撬开一道口子。
https://github.com/google-pytorch/torch_tpu

**5｜OpenAI 修复约 4 万账户额度错配并补偿**
约 4 万账户的额度计算与实际套餐不符，部分用户额度消耗快于预期。原因之一是 Pro 200 降档用户的旧每周额度未同步调整，10 月 16 日修正后本周剩余用量反而变少。受影响账户获赠价值 500 美元的额度（12,500 credits），与周额度分开计算，2027-01-20 到期。同一天 Codex 28 天改进计划第 15 天以“用量重置”收尾，订阅侧的额度混乱还在消化期。
https://linux.do/t/topic/3051760

**6｜腾讯元宝搜索对外开放，三种接入方式**
通过腾讯云开放 Skill / MCP / API 接入，每月 2000 次免费额度。自述千亿级索引、13 个垂直行业 157 个权威信源、分钟级更新，底层检索平均 8ms、召回 94%。对做国内落地 Agent 的人，这是一个比自建爬虫+向量库更省事的搜索工具层，但免费额度之后的价格没公布。
https://mp.weixin.qq.com/s/DHbVEwhHjiggPI5EQ5LgkQ

**7｜语音模型一天两发：ElevenLabs 与 Mistral 正面撞车**
ElevenLabs 出 Eleven Realtime v1 Mini / Max（Max 在 Big Bench Audio 准确率 98.8%、首音频 0.57s；Mini 75.9% / 0.62s；90+ 语言、17000 种声音；API 兼容 OpenAI Realtime 规范但只支持 WebSocket）。Mistral 发 Voxtral 3 系列 + 语音 Agent SDK：转录 50+ 语言、TTS 35+ 语言 50+ 方言、转录延迟 <500ms、每轮交互 1 秒内完成且支持打断、30 分钟音频克隆音色。语音 Agent 正式进入“实时可打断 + 便宜型号”阶段，选型窗口被打开。
https://mistral.ai/news/voxtral-3 ｜ https://elevenlabs.io/blog/realtime

**8｜Anthropic 用自家模型设计蝎毒结合蛋白，17/211 通过湿实验**
模型在 Claude Science 环境中运行，64 小时生成 30 万+ 设计，最终送检 211 个，17 个达到结合标准（针对 4 种毒素），实验由 Adaptyv Bio 和 Twist Bioscience 完成。别夸大：没有设计能同时结合多种毒素，也未验证细胞内中和能力或动物疗效。但 211 个设计和结合数据全部公开（含 HF 数据集），这是 AI for science 少见的“设计-湿实验-公开数据”完整闭环。
https://www.anthropic.com/research/claude-scorpion-toxin-binder-design

**9｜产业面：融资、IPO 与算力的三角挤压**
OpenAI 正洽谈约 300 亿美元新融资，估值或超 1.4 万亿美元，目的是抢在 Anthropic 预计 11 月中旬上市前锁定资金（软银、MGX 在谈）。Anthropic S-1 草案显示上半年营收 163 亿美元（去年同期 11 亿）、净亏 807 亿其中 720 亿是非现金会计调整，未来算力支出或达 7500 亿美元，且 AWS/谷歌/微软日益视其为竞争者，拿不到足够云容量只能租第三方数据中心。Google 这边 Gemini 4 Argon 上线 72 小时处理近 25 万亿 token ≈ Gemini 3 同期 3 倍，皮查伊承认仍受算力限制，为保前沿 AI 已牺牲部分云业务短期收入。
https://www.reuters.com/world/openai-seeks-accelerate-fundraising-ahead-anthropic-ipo-sources-say-2026-10-19/ ｜ https://www.wsj.com/tech/ai/anthropic-revenue-growth-ipo-accaf0f1

**其余快讯**：ChatGPT 向 Business/Enterprise 推出多人共管“团队任务”，云端定时或事件触发；Gemini 为小企业主做企业落地页 + 品牌风格图像生成（Nano Banana 2.1）+ 账目转财务图表；Gemini Personal Intelligence 上车 Android Auto；千问 App 双 11 上线“陪逛”，共享屏幕语音问商品、算规格价差；X 换新排序模型（预测停留时长）和检索模型（优先推会被读完的帖子），马斯克称用户活跃秒数创新高；OpenAI 收购药物开发平台 Orchestra Bio，并入 Rosalind 生命科学线；Aleksander Madry 重返 OpenAI 抓安全。

已标记该期已读。
