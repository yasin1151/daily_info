
# GitHub Trending 日报 · 2026-11-04

今日 Trending 13 个项目里，AI / Agent 相关占 12 个。榜单整体偏向「Agent 基建」：桌面控制、长期记忆、并行工作流、技能库——不是新模型，而是给 Agent 装手脚和记忆的工程层。

---

## 一、Agent 能力层（今日热度第一梯队）

**1. vercel-labs/agent-desktop** — Rust · ★12,630 · 今日 +3,792（榜首）
Vercel Labs 出的「给 AI 用电脑」CLI。关键做法：不靠截图和像素匹配，而是直接读桌面应用的无障碍树（accessibility tree），把每个可操作元素转成带 ref 的 JSON，Agent 点 ref、再读 UI 校验结果，循环在自己代码里跑。macOS / Windows / Linux 三平台。
为什么值得看：computer-use 一直是「截图 + VLM 猜坐标」的脏活，这条路线把视觉问题降级成结构化 API 调用，稳定性和成本都会好一个量级。榜单第一说明这是真痛点。

**2. thedotmack/claude-mem** — TypeScript · ★111,853 · 今日 +1,138
给 Agent 做跨会话的持久记忆：录制会话全过程，用 AI 压缩，再把相关片段注入下一次会话。README 明写兼容 Claude Code、OpenClaw、Codex、Gemini、Hermes、Copilot、OpenCode。
为什么值得看：上下文管理已经从「模型能力」变成「外挂工程」。它做的是会话级的 RAG，属于所有 Agent 工具都会需要的一层。

**3. mattpocock/skills** — Shell · ★311,403 · 今日 +1,164
Matt Pocock 直接开源了自己 `.agents` 目录下的技能集，「给真工程师用的 Skills」。
为什么值得看：Skills 生态开始出现「个人最佳实践仓库」这种形态——不是框架，是别人调教好的提示词/流程资产。对已经在用 Hermes / Claude Code 的人，这是最省事的抄作业入口。

**4. Donchitos/Claude-Code-Game-Studios** — Shell · ★34,625 · 今日 +1,181
把 Claude Code 改造成一整套游戏开发工作室：49 个 AI agent、72 个 workflow skill，外加模拟真实工作室层级的协调系统（制作人 / 主程 / 美术 / QA 分工）。
为什么值得看：多 agent 编排的「组织架构」玩法样本。热闹归热闹，但它是目前最完整的角色分工落地案例，值得拆它的协调逻辑。

**5. spotify/portal-ai-plugins** — TypeScript · ★3,029 · 今日 +94（blogwatcher 新收录）
Spotify 官方开源：把内部 Portal（软件目录 + 服务诊断 + 事故信息）接进 Claude Code / Codex / Cursor / pi。还带一个叫 shunt 的插件，把 I/O 密集的活（批量读文件、样板代码）路由给更便宜的 worker 模型跑，省 token。
为什么值得看：大厂开始把内部平台包装成 Agent 插件，而不是做聊天机器人。「贵模型做决策、便宜模型干粗活」的分流思路，是今年成本优化最实用的一招。

---

## 二、推理与模型改造

**6. JustVugg/colibri** — C · ★47,227 · 今日 +803
「小引擎，大模型」。纯 C 写的 MoE 分层推理引擎：热专家放 GPU（CUDA / Vulkan），温的放内存，冷的从 NVMe 流式读。已支持 GLM-5.2/5.3、Mistral-Large-4 等十来个引擎，官方口号是「不需要 GPU 也能跑千亿参数」。
为什么值得看：把显存墙变成磁盘带宽问题，是本地跑大 MoE 最现实的路径。C 实现、单文件一族模型，适合嵌进边缘设备。

**7. p-e-w/heretic** — Python · ★38,756 · 今日 +699
免训练的模型改造工具：去审查、压「slop」、降低谄媚倾向（abliteration 路线的工程化封装）。
为什么值得看：不用微调就能改模型行为，成本极低。争议也大——它同时也是「越狱即服务」，社区讨论热度一半来自伦理争论。

**8. shiyu-coder/Kronos** — Python · ★46,502 · 今日 +503
面向金融市场的 foundation model，把 K 线/行情当「语言」来建模。
为什么值得看：垂直领域 foundation model 的典型样本。金融时序做预训练一直难，如果这套 tokenization 思路站得住，量化圈会很快跟进复现。

---

## 三、开发工具 / 数据工程

**9. D4Vinci/Scrapling** — Python · ★94,748 · 今日 +1,658（第二热）
自适应网页抓取框架，从单次请求到全站爬取一套接口搞定，自带反爬对抗。
为什么值得看：Agent 要吃数据，抓取是刚需。它的「自适应选择器」（页面改版后自动重新定位元素）正好解决爬虫维护成本这个老大难。做 RAG 数据管道的人应该看一眼。

**10. max-sixty/worktrunk** — Rust · ★10,464 · 今日 +437
管理 git worktree 的 CLI，专门为「多个 AI agent 并行改同一个仓库」设计。
为什么值得看：并行 agent 最大的坑是工作区互相踩。worktree 隔离是干净解法，这类工具会随着「一人开五个 agent」变成标配。

**11. anomalyco/hex** — Rust · ★4,555 · 今日 +410
本地语音听写：按住快捷键说话，松手自动粘贴，全程离线（首次下载模型后不出本机）。Mac / Windows / Linux 全平台。
为什么值得看：端侧 ASR 已经好用到可以替代云服务，隐私和延迟双赢。Rust 写的跨平台壳，值得当桌面端 AI 应用模板研究。

**12. floci-io/floci** — Java · ★28,727 · 今日 +679（blogwatcher 新收录）
「轻、软、永远免费」的 AWS 本地模拟器，LocalStack 的替代品。
为什么值得看：非 AI，但属于 Agent 开发的基础设施——本地跑通 S3/SQS/Lambda 才能让 agent 安全试错。免费这个定位直接打在 LocalStack 的收费痛点上。

**13. Usagi-org/ai-goofish-monitor** — Python · ★16,334 · 今日 +204（blogwatcher 新收录）
基于 Playwright + AI 的闲鱼多任务实时/定时监控与智能分析，带完整后台管理 UI，帮用户从海量商品里筛出心仪货。
为什么值得看：中文社区的「AI 应用落地」典型——不高大上，但需求真实。它的做法（定时抓 + LLM 判价值 + 通知）可以直接迁移到任何二手/票务/房源场景。

---

## 一句话总结

今天的榜单没有新模型，全是「让 Agent 更能干」的配套：**眼睛（agent-desktop）、记忆（claude-mem）、手脚（worktrunk）、经验（skills）、省钱（shunt）**。基建期特征非常明显——谁先把这些层拼稳，谁的 agent 才真能干活。

已标记 3 条 blogwatcher 新条目为已读。
