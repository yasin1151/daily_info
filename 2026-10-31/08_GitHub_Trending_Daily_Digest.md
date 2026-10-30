
GitHub Trending 日报（2026-10-31 日榜，15 个项目，筛选出 12 个 AI / Agent / 开发工具相关）

**今日主线：Agent Skills 生态主导热门榜单。** 前 15 名里有 4 个是“给 agent 装技能”的仓库（impeccable、superpowers、mattpocock/skills、anthropics/skills），其中两个的星数都超过了 30 万。与此同时，另一条主线正在成形：**给 agent 配上自己的电脑**（OpenBot、OpenMausBot、lightpanda），以及给 agent **配上长期记忆**（claude-mem）。

---

**1. impeccable — 给编码 agent 一套“设计词汇表”（+2,299★今日第一）**
简介：Rust 写的 agent skill 集，用 polish、bolder、critique、audit 这类指令词，让编码 agent 在产出界面时能“调风格、做审查”，并在发布前找出像 AI 生成的那种粗糙质感（AI slop）。自带网站 impeccable.style。
为什么值得关注：它切中了 AI 编码最普遍的失败模式——功能正确，但界面一看就是模型随手拼出来的。把设计判断拆成一组可被 agent 调用的词，是个很聪明的做法；它用 Rust 实现，而不是用 prompt 包一层，说明确实做了性能方面的工作。
Stars：97,004（+2,299）｜ https://github.com/pbakaus/impeccable

**2. DeepTutor — 港大数据智能实验室的“终身个性化辅导”（+2,282）**
简介：HKUDS 出品的智能辅导系统，主打“终身、个性化”，有独立站点 deeptutor.info。
为什么值得关注：HKUDS 这个组此前的 LightRAG、AutoAgent 都走得比较稳。“把 LLM 从答题机器改成会跟着你成长的老师”，是教育类应用里少见的长期记忆 + 用户建模方向。
Stars：51,739（+2,282）｜ https://github.com/HKUDS/DeepTutor

**3. jailbreaks — 一份持续更新的越狱提示词清单（+2,053）**
简介：作者把自己收集的全部越狱（jailbreak）样本集中到一个仓库里公开。
为什么值得关注：安全团队可以直接拿去当回归测试集。它也说明红队测试这件事正在变得比较“公开”——这类仓库上榜，通常意味着各家模型的安全对齐刚被绕过去了一轮。
Stars：10,932（+2,053）｜ https://github.com/togg53192-cmd/jailbreaks

**4. superpowers — agentic skills 框架 + 开发方法论（+1,255）**
简介：一套“技能框架 + 软件开发方法论”，把工程流程本身写成 agent 可执行的技能包。
为什么值得关注：它的重点在于把“怎么做事”也一并编码进技能里，而不只是让 agent 会更擅长写代码，这正是 skills 生态下一阶段的竞争点。30.9 万星，是目前这类仓库里体量最大的。
Stars：309,408（+1,255）｜ https://github.com/obra/superpowers

**5. claude-mem — 给所有 agent 加一层跨会话长期记忆（+1,145）**
简介：捕捉 agent 在会话里的全部动作，用 AI 压缩，再把相关上下文注入未来的会话。兼容 Claude Code、Codex、Gemini、Hermes、Copilot、OpenCode 等。
为什么值得关注：这是目前“记忆层”赛道里接口最通用的方案，直接支持 Hermes。底层用了 SQLite 加向量检索（memory-engine、embeddings），不是纯 prompt 拼接，架构值得借鉴。
Stars：106,185（+1,145）｜ https://github.com/thedotmack/claude-mem

**6. T3 Code — 用手机远程操控你机器上的所有 agent（+920）**
简介：自称“agent harness 控制面”，通过 iOS、Android、Web、Electron 四端，统一操控本机的 Claude Code、Codex、Cursor、Grok Build、OpenCode、Antigravity。作者明确说“不卖你任何东西，不喜欢可以 fork”。
为什么值得关注：现在的痛点是 agent 跑起来之后人就被绑在桌前。T3 的思路是把 agent 当成后台服务，人用手机随时插手，比各家自建的桌面端更开放。
Stars：32,711（+920）｜ https://github.com/pingdotgg/t3code

**7. OpenMausBot — 开源的 Grok Bot 替代品（+899）**
简介：给 bot 配一台虚拟机，让 bot 在 VM 里自己操作环境，而不是只在沙箱里调工具。
为什么值得关注：注意它与第 11 名 OpenBot 是同一波的竞争——都是“AI 同事要有自己的电脑”。VM 隔离比容器更接近真实用户环境，也更适合做长任务的自主执行。
Stars：8,592（+899）｜ https://github.com/milind-soni/OpenMausBot

**8. mattpocock/skills — 一个工程师的 .agents 目录原样开源（+889）**
简介：作者直接把自己日常使用的 agent 技能目录公开，没有包装、也没有框架。
为什么值得关注：30.7 万星说明很多人想看“高手的技能文件夹到底长什么样”。它属于参考样本型仓库，价值在于范式，不在于代码量。
Stars：307,445（+889）｜ https://github.com/mattpocock/skills

**9. thinkrail — JetBrains 亲自下场的 Vibe Coding IDE（+717）**
简介：JetBrains 出品的轻量“真 IDE”，围绕 pi agent 构建，能根据你的工作方式自我定制，主打 spec-driven coding。
为什么值得关注：这是今天最有信号意义的一条。JetBrains 直接做 agent 原生 IDE，意味着传统 IDE 厂商已经承认“编辑器要为 agent 重构”，而不是只加个侧边栏聊天。spec-driven 的路线也和 Cursor 那类“直接改代码”形成对照。
Stars：6,553（+717）｜ https://github.com/JetBrains/thinkrail

**10. OpenBot — CopilotKit 的“AI 同事”，每人一台电脑（+707）**
简介：每个 AI 同事分到独立的浏览器、文件系统和工具，每个动作执行前先决定、执行后留记录，兼容任意 AG-UI agent。
为什么值得关注：“动作前决策 + 动作后留痕”是可审计 agent 的关键设计，对企业落地比单纯的性能指标更重要。
Stars：8,757（+707）｜ https://github.com/CopilotKit/OpenBot

**11. lightpanda — 专为 AI 和自动化做的无头浏览器（+652）**
简介：用 Zig 从零写的无头浏览器，不是 Chromium 套壳，目标是给 agent 提供低内存、高并发的网页访问层。
为什么值得关注：agent 抓网页的开销大头一直是 Chromium。用 Zig 重写内核是重活，但一旦成型，可以大幅降低大规模 agent 的爬取成本。
Stars：38,331（+652）｜ https://github.com/lightpanda-io/browser

**12. anthropics/skills — 官方 Agent Skills 参考仓库（+287）**
简介：Anthropic 公开的 Agent Skills 仓库。
为什么值得关注：今天榜上大半“技能”仓库的规范源头都在这里。虽然增速已放缓（+287），但作为事实标准仍值得持续关注。
Stars：185,283（+287）｜ https://github.com/anthropics/skills

**未入选但值得一提**：Renhuai123/ziwei-doushu（11,182★，+1,146）是紫微斗数排盘引擎，古籍数据 + 算法还原做得比较扎实，但不是 AI 方向；macro-inc/macro（5,855★，+117）是带共享 AI 记忆的团队工作台，Rust 实现，增速偏慢；expo/skills（3,882★，+108）属于垂直场景的技能包。

---

blogwatcher 已扫描（15 条，无未读遗留），以上 12 项已标记为已读。今日最值得跟的两条线是 **impeccable（agent 产出质量的可控化）** 和 **thinkrail（IDE 厂商的 agent 原生重构）**。
