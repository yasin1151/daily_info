
# GitHub Trending 日报｜2026-10-28

今天榜单上 11 个项目里有 10 个与 AI 相关，而且相关项目集中得有点反常：**有三个项目都在解决同一个问题——AI 做出的界面一眼就看出是 AI 做的**。下面是重点。

---

## 1. hallmark：拒绝“AI 味”的设计 skill
**Nutlope/hallmark** ｜ ★38,929 ｜ 今日 +2,859（今日涨幅第一）｜ CSS ｜ MIT

Together AI 出品的设计 skill，供 Claude Code / Codex / Cursor / OpenCode 使用。它从 50 套“材料”（纸感、字体、配色、组件、纹理）里挑三套，先按“访客是来干什么的”搭页面结构，然后在**真实浏览器里 lint** 结果，专门抓那些一眼就能看出的机器痕迹：每个标题上方的小字“eyebrow”、加了字距的全大写标签、标题里只染一个词、整页空框或全是照片、首屏撑不满屏幕、每页底部都挂邮件订阅、表单说“谢谢”其实什么都没发出去。最后还有一个新上下文的 reviewer 复核。

**为什么值得关注**：它把“审美”写成了可执行的 gates（Floor 是绝不能上线的底线、Reflex 是模型容易套用的默认做法、Finish 是可选的工艺细节），属于“用规则文件约束模型输出”的典型做法。想给产品做落地页的话，直接抄它的检查清单就能用。

https://github.com/Nutlope/hallmark

---

## 2. impeccable：62 条检测规则，专门挑 AI 前端的毛病
**pbakaus/impeccable** ｜ ★90,461 ｜ 今日 +1,458 ｜ Rust ｜ Apache-2.0

一个 skill、24 条命令、可在浏览器里实时迭代，外加 62 条确定性检测规则。README 里说得很实在：所有模型都在同一批 SaaS 模板上训练，如果跳过设计指导，每个项目都会犯同样的错误：到处用 Inter 字体、紫到蓝的渐变、卡片里再套卡片、彩色背景上放灰字、每个标题上方放一个圆角方形图标。

**为什么值得关注**：它是在 Anthropic 官方 frontend-design skill 的基础上继续往下做的，安装只要 `npx impeccable install`。和 hallmark 的区别是：hallmark 是“按材料体系搭页面”，impeccable 是“按规则挑错”。而 Rust 实现说明它在代码里也做实时检测，不只是生成 prompt。

https://github.com/pbakaus/impeccable

---

## 3. DeepTutor：港大出品的“终身个性化家教”
**HKUDS/DeepTutor** ｜ ★45,807 ｜ 今日 +1,587 ｜ Python ｜ Apache-2.0

港大 HKUDS 实验室的教育 Agent，带 arXiv 论文和官网，版本迭代很快（10 月 19 日刚发 v1.6.15）。核心是一套持续记忆的学习路径：分组测评、受限的家教记忆、检索方案对比、原生 Gemini 语音、科研工具、学习日志，还有 CLI 形态（agent-native 接口）。

**为什么值得关注**：教育类 AI 从“问答机器人”转向“长期跟踪一个学生的知识状态”，记忆和测评设计是难点；这个仓库的工程完成度（视频阅读、插件管理、索引可恢复）在同赛道里算比较完整的，可以直接当作 RAG + Agent 架构的参考实现。

https://github.com/HKUDS/DeepTutor

---

## 4. cindy：开箱即用的开源 AI Agent，把你的电脑变成服务器
**makecindy/cindy** ｜ ★7,435 ｜ 今日 +1,446 ｜ TypeScript ｜ Apache-2.0

跨 macOS / Windows / iOS / Android 的桌面+手机 Agent。卖点是“所有设备共用一个 Cindy”：换设备打开同一个会话继续干活、能直接调用另一台电脑上配置好的模型供应商（含订阅和本地模型）、手机上内置远程桌面，聊天不够用就接管整台机器。不需要租服务器，也不用自己搭 self-host。

**为什么值得关注**：它直接抢 Claude Code / Codex 的场景——“保留你喜欢的 agent，只是换个更顺的工作方式”。本地优先 + 多设备接续这个产品方向，可能是接下来几个月 agent 桌面端的主战场。

https://github.com/makecindy/cindy

---

## 5. thinkrail：JetBrains 亲自下场做 agentic IDE
**JetBrains/thinkrail** ｜ ★3,951 ｜ 今日 +1,211 ｜ TypeScript ｜ Apache-2.0

围绕 `pi` 编码 agent 做了一层较重的界面：每个任务开一个独立的 git worktree 作为 workspace，agent 之间并行互不干扰，好的分支合并、差的分支删掉；空闲的 workspace 会自动归到项目下的 shelf，PR 合并或关闭后自动清理，需要时再调回来。项目知识靠 “living specs” 和可复用 skills 持久化，下一步要做完整插件体系，让 IDE 按你的使用习惯自己长出新工具。

**为什么值得关注**：worktree 隔离 + spec 持久化，是目前对“agent 并行改代码”最工整的工程解法之一，而且有 JetBrains 的资源支撑。值得观望它和 Cursor 的路线差异。

https://github.com/JetBrains/thinkrail

---

## 6. ECC：给 agent harness 做性能优化（29 万星）
**affaan-m/ECC** ｜ ★290,850 ｜ 今日 +1,183 ｜ JavaScript ｜ MIT

涵盖 skills、instincts、memory、security 和 research-first development，支持 Claude Code、Codex、Opencode、Cursor。定位偏底层：它不生产 agent，而是调整 agent 的行为方式。

**为什么值得关注**：29 万星说明 “agent harness 调优” 已经是个庞大的细分生态——大家不再纠结选哪个模型，而是纠结上下文怎么管、记忆放在哪、怎么防止它乱改。这类项目的实际价值，得看它提出的方法能不能迁移到自己的工具链上。

https://github.com/affaan-m/ECC

---

## 7. ai-design-skills：把设计 skill 当 npm 包来发
**elayadesign/ai-design-skills** ｜ ★9,247 ｜ 今日 +1,395（新上榜）｜ MIT

一个还在增长的设计 skill 合集（landing-page-design 等），每个 skill 是一个独立文件夹，安装方式就是 clone 后 `cp -r skills/ .claude/skills/`，Cursor 就 curl 一个 SKILL.md 到 `.cursor/rules/`。设计取向（字体、颜色、间距、动效）集中在文件底部一小节，fork 改那里，整个 skill 的行为就跟着变。

**为什么值得关注**：它体现了一个正在成型的共识——**skill 是新的分发单位**，一个 markdown 文件就能改掉 AI 的输出风格，不需要 SDK、不需要 API key。这对做工具的人来说是低成本获客渠道。

https://github.com/elayadesign/ai-design-skills

---

## 8. openbot：给每个 agent 一个独立工位的本地桌面
**nightly-labs/openbot** ｜ ★2,384 ｜ 今日 +794（新上榜）｜ TypeScript

本地优先的桌面工作台，支持 Codex App Server、Claude Code、Grok CLI，以及通过 ACP 接 OpenCode / Gemini / Cursor / Cline。每个 agent 有自己的 workspace、会话、FIFO 消息队列、文件传输、内嵌浏览器，还能 agent 之间互相发消息；上下文快撑满时自动压缩，并自动探测本地 Ollama / LM Studio。

**为什么值得关注**：结构设计很完整，但 README 里明确警告这是开发预览版，agent 以 `danger-full-access` + `approvalPolicy: never` 运行，首次同意后可以随意读写文件、跑命令、控制浏览器。想尝试的话，建议单独开一台机器。

https://github.com/nightly-labs/openbot

---

## 其他值得知道的

- **togg53192-cmd/jailbreaks** ★5,469（+890，新上榜）— 纯 jailbreak 清单合集，无人维护的纯文本仓库能冲上趋势，说明红队测试的关注度在上升。https://github.com/togg53192-cmd/jailbreaks
- **obra/superpowers** ★306,403（+608）— agentic skills 框架 + 开发方法论，已被大量 skill 生态引用，属于基建型项目。https://github.com/obra/superpowers
- **gitroomhq/postiz-app** ★39,332（+953）— 开源社媒排期工具，正在往 “agentic” 方向改，AGPL 授权。https://github.com/gitroomhq/postiz-app

---

**一句话总结**：今天的榜单在说明一件事——竞争焦点已经从“哪个模型更强”转到“**怎么用一堆 markdown 文件把模型约束成靠谱的工程师**”。前八里有五个（hallmark、impeccable、ai-design-skills、ECC、superpowers）本质都是规则文件加检测器，设计和代码正在被同一套方法论吃掉。
