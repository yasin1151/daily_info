
# GitHub Trending 日报 · 2026-11-01

今日榜单 14 个项目里有 11 个跟 AI Agent 直接相关，而且集中在同一层：**给 coding agent 装记忆、装技能、装控制台**。模型和框架本身反而没有出现。今天的竞争已经从“谁的模型强”转移到“谁能把 agent 真正用起来”。

---

## 一、Agent 记忆与技能（今日最热）

**1. claude-mem：给所有 coding agent 装一个跨会话记忆**
自动记录 agent 在会话里做的每次工具调用，用 AI 压缩成语义摘要，下次开新会话时把相关上下文注入回去。支持 Claude Code、Codex、Gemini、Hermes、Copilot、OpenCode 等十几家。
为什么值得关注：agent 最大的痛点不是智商而是失忆，每次重开都要重新讲一遍项目背景。这是目前最直接的解法，也解释了它 3 个月冲到 10 万星。
Stars：107,810（今日 +1,723，榜首）
https://github.com/thedotmack/claude-mem

**2. mattpocock/skills：反对“vibe coding”的工程师技能包**
TypeScript 圈知名作者 Matt Pocock 放出了自己每天在用的 `.agents` 目录。他在 README 里明确批评 GSD、BMAD、Spec-Kit 这类方案：它们帮你接管流程，但也夺走了控制权，流程出错时你没法修。他的技能刻意做小、可拆、可改，不绑定任何模型。
为什么值得关注：这是当前 skills 热潮里少见的“反框架”立场，值得对照自己的 agent 工作流看一遍。
Stars：308,337（今日 +882）
https://github.com/mattpocock/skills

**3. superpowers：agentic skills 框架与开发方法论**
把 skills 当成一套完整 SDLC 方法论来组织，包含头脑风暴、子 agent 驱动开发等环节。
为什么值得关注：和上一条正好是两种路线，一个是“小而散”，一个是“成套方法论”，可以对比看哪种更适合团队。
Stars：310,037（今日 +663）
https://github.com/obra/superpowers

**4. impeccable：教 agent 什么叫“设计感”，专治 AI 味的界面**
给 coding agent 一套设计词汇：用 `polish`、`bolder` 调整风格，用 `critique`、`audit` 做评审。官网给了同一模型、同一需求的两版对比，无它时是“米色背景+细衬线+胶囊按钮”的典型 AI 模板，有它时整页围绕一张夜景图构建。
为什么值得关注：AI 生成界面的同质化已经是公开的丑，这是第一个系统性对付“AI slop”的项目。
Stars：98,235（今日 +1,339，今日增幅第一）
https://github.com/pbakaus/impeccable

---

## 二、Agent 控制台与多 agent 团队

**5. t3code：把所有 agent 收进一个遥控器**
Theo（t3.gg）团队做的“agent harness 控制面”，手机 App、网页、Electron 桌面三端控制本机的 Claude Code、Codex、Cursor、Grok Build、OpenCode、Antigravity。README 里直接回答“你们卖什么”——什么都不卖，嫌现有方案（Codex 桌面版、Conductor、Cursor Glass）没达到标准才自己写。
为什么值得关注：agent 从终端走向“随身可控”，远程派活、手机审批是下一个形态。也说明这块还没有公认赢家。
Stars：35,452（今日 +1,148）
https://github.com/pingdotgg/t3code

**6. Orkas：桌面上的本地 AI 团队**
MIT 协议、local-first。一个 Commander 把目标拆成 to-do，调度 16 个内置专家 agent，同时能拉 Claude Code、Codex、OpenCode、OpenClaw、Hermes 一起干。项目维度保存目标、规则、记忆、文件，支持自动推进和定时任务，数据不出本机。
为什么值得关注：把“多 agent 协作”从 demo 做成有项目记忆和排期的产品形态，送的 500 credits 让它开箱可用。
Stars：6,111（今日 +1,118，今日增幅榜前列）
https://github.com/Orkas-AI/Orkas

**7. OpenMausBot：开源的 Grok Bot 替代，bot 有自己的虚拟机**
聊天软件形态，侧栏每个 bot 都是真 agent（本地跑 Claude 或 Codex），各有性格、模型、云电脑和连接的 App。可以对它像联系人一样说话，看它干活，只在关键处审批。自称对标 Grok Bot、Meta Muse、OpenAI dots、Cue by Manus。
为什么值得关注：把 computer-use 封装成“同事”而不是“工具”，是今年产品化最激进的一条路。
Stars：9,572（今日 +1,304）
https://github.com/milind-soni/OpenMausBot

**8. Claude-Code-Game-Studios：把 Claude Code 变成一间游戏工作室**
49 个 AI agent + 72 个 workflow skill，模拟真实工作室层级（制作人、主程、美术、QA 分工协作），覆盖 Unity、Unreal、Godot。
为什么值得关注：这是“岗位化多 agent”目前最具体的样本，游戏开发流程长、角色多，正好是压力测试场。对你关注的 UE 方向也有直接参考价值。
Stars：31,130（今日 +724）
https://github.com/Donchitos/Claude-Code-Game-Studios

**9. OpenMAIC：清华 MAIC 的一键多 agent 互动课堂**
一句话生成沉浸式多 agent 教学场景，学生和多个 AI 角色在同一课堂里互动。
为什么值得关注：教育是多 agent 少见的、有真实需求的落地方向，清华团队背书，适合观察“课堂”这种强结构场景怎么设计 agent 分工。
Stars：42,169（今日 +115）
https://github.com/THU-MAIC/OpenMAIC

---

## 三、基础设施与工具

**10. lightpanda：为 AI 和自动化重写的无头浏览器**
用 Zig 从零写的 headless browser，不是 Chromium 套壳，主打低内存和快启动，兼容 CDP，可直接顶替 Playwright、Puppeteer。
为什么值得关注：agent 抓网页的瓶颈一直是浏览器太重，一个实例几百 MB。这是少数从引擎层解决的方案，跑大批量 agent 爬取时成本差别很大。
Stars：39,212（今日 +929）
https://github.com/lightpanda-io/browser

**11. DeepTutor：港大数据智能实验室的“终身个性化家教”**
多 agent + RAG 架构的 AI 导师，带 CLI（agent-native 接口），有 arXiv 论文和 Discord、飞书、微信群，配套 EduHub 技能社区。
为什么值得关注：学术团队做的教育 agent，工程完整度罕见；CLI-first 的设计说明它想被别的 agent 调用，而不是只做聊天窗口。
Stars：52,770（今日 +1,035）
https://github.com/HKUDS/DeepTutor

**12. devops-exercises：85k 星的 DevOps 面试题库**
Linux、K8s、Terraform、Prometheus、AWS、SRE、Python 等全覆盖的练习题与答案库，2019 年至今仍在更新。
为什么值得关注：老项目重回榜单，通常是有人在拿它喂 agent 做训练或评测。非 AI 项目里最值得收藏的一个。
Stars：85,957（今日 +341）
https://github.com/bregman-arie/devops-exercises

---

## 四、非 AI 但值得一扫

- **ziwei-doushu**（12,244，+1,093）：紫微斗数开源排盘引擎，基于倪海厦《天纪》体系，含四化系统、格局知识库、古籍原文。中文项目今日增幅第二。
- **vorssaint-utils**（31,876，+499）：免费开源的 macOS 菜单栏工具箱，Alt-Tab、卸载器、防休眠。

---

**一句话结论**：今天攒星星的不是模型，是“让 agent 记得住、会审美、能远程管”的这几层外壳。claude-mem 和 impeccable 分别解决了 agent 的两个真实短板，如果你只用一条时间看，看这两个。
