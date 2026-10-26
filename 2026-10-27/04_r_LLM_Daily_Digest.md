
今日 r/LLM 热帖精选（2026-10-27）。说明：Reddit 直连与 redlib 实例仍被网络层封锁（`000/rc=28`），本轮通过归档通道取数；帖子评论赞数为归档快照，多数尚未成熟，仅作参考，不代表真实热度排序。

---

## 1. 自己写了一个 SKILL 之后，我才明白它不是 token 垃圾

**摘要：** 作者原本认定 agent 的 SKILL 是烧 token 的噱头——一次挂一堆技能，订阅额度早上就见底。自己动手写了一个之后改口。关键差别在上下文成本：MCP 连接会把工具定义全量塞进上下文，而 SKILL 起初只放名字和一句话描述，一两百 token 的量级，真正需要时由 agent 自己加载正文，所以同时挂三十个也不痛。第二个价值是补模型的知识盲区：自研或冷门工具在网上根本没有文档，写一个 SKILL.md 说清怎么用就行。第三是把公司特有的发布流程固化成流程而不是技术，比如跑测试、更新 CHANGELOG、提版本号、打包、打 tag、发布。第四是 SKILL 目录里能放脚本、参考文档和模板，且不会自动进上下文，agent 可以直接执行现成脚本，不必现写代码。评论区没有停在工具层面，而是吵到了隐私：把个人经验写成技能交出去，算不算免费给厂商贡献训练素材。

**高赞评论：**

- u/PopularPhoneChair333（赞数 1·归档快照）："Skills are also you handing over your knowledge and training the LLM, while you pay for the privilege." 立场说明：质疑派的核心一句——技能是把你的经验无偿交给模型，还要你自己掏订阅费，读者该想清楚这是不是本意。
- u/PopularPhoneChair333（赞数 1·归档快照）："They see your data, skills, code, prompts, how you steer, and correct the model" 立场说明：同一位继续加码，认为厂商能看到数据、技能、代码、提示词以及你怎么纠偏，长期看等于你在替对方训练下一代模型，最后连自己的软件都不再被需要。
- u/ievkz（赞数 2·归档快照，楼主）："I use Tiel-Coder-35B-A3B-MTP for coding and Cyber-Tiel-Coder-35B-A3B-MTP for pentesting, both quantized to Q2_K_XL, with a 65K context window in the Pi coding agent." 立场说明：楼主用具体配置反驳——全部跑在自己的 4070 Ti Super 16GB 上，代码、提示词和工作流都没出本机，谈不上被拿去训练；这也顺带说明 Q2 量化加 65K 上下文在单卡上的现实边界。

**原帖：** https://www.reddit.com/r/LLM/comments/1xf80iv/

---

## 2. Kimi K3.1 Pro 便宜五倍，社区先问准确率再问价格

**摘要：** Moonshot 公布 Kimi K3.1 Pro：号称 100 万 token 上下文，另有 Highspeed 版本输出速度快 2 到 3 倍，价格约为 OpenAI GPT 6 Astra 的五分之一。发帖人算的是日常账——跑几小时代码 agent、读一堆财报、调研几十个竞品，API 费用涨得很快，五分之一价差确实诱人。但他自己先泼了冷水：便宜模型如果错得多、要重试、样样都得复核，省下的钱会被人工时间吃掉；而且上下文长不等于能在超长文档里准确捞到那一条信息。评论区基本认同先看准确率：有人说便宜模型只会让自己变成保姆；也有人指出更隐蔽的成本是用量——思考更久、卡住更多、返工更多，单价低不代表总价低。还有人认为同价位它不如 Opus，真要便宜不如用 DeepSeek。

**高赞评论：**

- u/MajorGlucose373（赞数 1·归档快照）："accuracy first, always. a cheap model that hallucinates or misses details in a 1M context window just means I'm spending my time babysitting it instead of saving money" 立场说明：把账算回人力成本的典型观点——只要它幻觉或漏细节，省下的钱立刻变成盯梢时间，除非能证明在真实大文档里检索可靠。
- u/Upper-Philosophy2376（赞数 2·归档快照）："even a cheaper model can use way more tokens, if it thinks more, takes longer, gets stuck more often" 立场说明：指出单价陷阱——按 token 计费时，思考冗长和反复卡住会吃掉价差；他补充窄任务（把某个函数改成这样）适合便宜模型，而 Kimi 目前只适合当规划阶段的第二意见，还替不掉 Claude 和 Codex。
- u/OddDesigner9784（赞数 1·归档快照）："Sure it's cheaper that astra but it's also worse than opus at a similar price point." 立场说明：直接给否定结论——同价位不如 Opus，就没有切换理由，要更便宜还不如用 DeepSeek，属于对"便宜五倍"这个卖点的祛魅。

**原帖：** https://www.reddit.com/r/LLM/comments/1xfpc3w/

---

## 3. 免费与低价模型替代清单：本地 Ollama 还是 OpenRouter

**摘要：** 一个研究生手里有年付 Claude Pro，却发现学习场景几乎没用上、额度在白白过期；试过 Gemini 免费版不喜欢，于是问大家用什么便宜甚至免费的模型来做课程和讲义相关的事。评论区给出两条路。第一条本地跑：装 Ollama，Qwen 的 7B 和 14B 在小笔记本上就能跑，效果对得起零成本。发帖人回说自己内存不够，打算 Qwen、Kimi 加 Claude 混着用。第二条走托管：OpenRouter 按量付费比 Claude Pro 便宜，还能按任务随时换模型；有人把当前免费模型清单直接列了出来，包括 Gemma 4 26B A4B 与 31B、Nemotron 3 系列、Laguna、Inkling 等。还有人给出成品方案：Mac Mini M6 上用 LM Studio 把 Gemma 4 26B 起成服务，再从笔记本和另一台机器访问，速度够快。对预算敏感的学生，这套组合比继续囤订阅更实际。

**高赞评论：**

- u/modern_foothold（赞数 1·归档快照）："a grad student just get ollama running locally and call it a day" 立场说明：主张先榨干本地算力——Qwen 7B/14B 在普通笔记本上就够用，真需要托管再用 OpenRouter 按量付费，比 Claude Pro 订阅便宜且能按任务切模型。
- u/ixid（赞数 1·归档快照）："Google: Gemma 4 26B A4B (free)" 立场说明：直接贴出 OpenRouter 上的免费模型清单，从 Gemma 4 26B/31B 到 Nemotron 3 全系、Laguna、Inkling、Llama 3.1 8B，是这条帖里最可操作的信息。
- u/AttitudeMedium5623（赞数 1·归档快照）："I have a Mac Mini M6 running Gemma 4 26b e4b qat in LM Studio as a server." 立场说明：给出一套可复制的低预算方案——一台 Mac Mini 当推理服务，其他设备通过 Askimo 接入，兼顾免费与跨机器可用，属于本地部署派的实证。

**原帖：** https://www.reddit.com/r/LLM/comments/1xfv7gh/
