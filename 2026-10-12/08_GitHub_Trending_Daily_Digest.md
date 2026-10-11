
**GitHub Trending 日报 · 2026-10-12**
数据源：github.com/trending?since=daily（今日榜单共 8 个项目，其中 AI/Agent/LLM/开发工具相关 5 个）

---

**1. rea — 让 Agent 干逆向工程（今日榜首）**
- 项目：`morluto/rea` | 今日 **+25,585** stars | 总 102,840 | TypeScript | MIT | https://github.com/morluto/rea
- 简介：把逆向工程封装成一个 MCP 服务。装好后让你的 agent（Claude Code、Codex 等）去分析原生二进制、JavaScript/Electron 应用、.NET 程序集和网站，从 app 表面行为一路追到二进制层。分析全程本地跑，每条结论会附上证据和"我哪里不确定"；逆向部分可对接已有的 Hopper / Ghidra / IDA。作者的原话场景很直白："看到某个 app 里有个想要的功能，让 agent 用 REA 查清楚它怎么实现的，然后给你的项目做一个"。
- 为什么值得关注：agent + 逆向 是比较少见的组合，正好落在"扒竞品功能实现"这个真实需求上，而不是又一轮 CRUD 生成。它同时挂着 `agent-skills` / `mcp` / `claude-code` / `codex` 标签，是 MCP 生态从"代码助手"往"系统级工具"延伸的一个样本。日增 2.5 万星、创建于今年 4 月就到 10 万星，属于爆发级别，值得蹲一下它的实际效果和争议。

**2. diagram-design — 给 Agent 用的"不丑"图表技能**
- 项目：`cathrynlavery/diagram-design` | 今日 **+1,083** | 总 50,280 | HTML/SVG | MIT | https://github.com/cathrynlavery/diagram-design
- 简介：一个 agent skill，支持 Claude Code、Codex、GitHub Copilot、Cursor、Factory Droid 等。内置 44 种图表类型，输出是单文件自包含 HTML + SVG（双击就能打开），可再导出 PNG/SVG。支持"入职"你的网站——抓取配色和字体，让之后每张图都跟你品牌一致。slogan 是 "No shadows. No Mermaid slop."
- 为什么值得关注：agent skills 生态里目前大多是代码/流程类工具，这个是少见的"审美向"工具，直接解决 Mermaid 出图一眼 AI 味的问题。对要写文档、写周报、做技术方案的人，属于装了就立刻能用、且能交差的那类技能。

**3. artcraft — AI 图像/视频的"IDE"**
- 项目：`storytold/artcraft` | 今日 **+2,956** | 总 17,769 | Rust | Apache-2.0 | https://github.com/storytold/artcraft
- 简介：定位是 "The IDE for interactive AI image and video creation"（给艺术家的 IDE）。核心思路是**先搭场景再生成**：2D 图层合成、3D 场景搭建（背景/前景/道具分层、kitbashing）、角色姿态和相机位预先摆好、角色身份一致性迁移、图生 3D mesh，然后选适合的模型出图。桌面端 Rust 实现，Apache-2.0 开源。
- 为什么值得关注：AI 视频/图像生成正在从"抽卡式 prompt"转向"可控、可重复的工程流程"，这个项目是这条路线里做得比较完整的一个开源实现。你关心的模型可以自己换，而不是被云端工作流锁死。

**4. airllm — 单张 4GB 显存跑 70B**
- 项目：`lyogavin/airllm` | 今日 **+541** | 总 36,448 | Apache-2.0 | https://github.com/lyogavin/airllm
- 简介：分层加载思路，让 70B 级别模型在单张 4GB 显存的消费级卡上跑推理，主打低成本本地部署。
- 为什么值得关注：这是 2023 年的老项目今天重新回榜。老项目回榜通常不是巧合——多半是又有人在找"省显存跑大模型"的土办法。对成本敏感、又不想把数据发出去的个人开发者，仍是门槛最低的入口之一。注意它牺牲的是速度，不是免费午餐。

**5. pytorch/pytorch — 基线信号**
- 项目：`pytorch/pytorch` | 今日 **+314** | 总 104,468 | Python | https://github.com/pytorch/pytorch
- 简介：主流深度学习框架本体，Tensors + 动态神经网络 + GPU 加速。
- 为什么值得关注：常态在榜的项目，单看日增没意义，价值在于当基线——今天 314，说明生态活跃度平稳，没有大版本事件。仓库几小时前还有提交。

---

**其他上榜（非 AI，仅备注）**：`boykopovar/AnyPS5` 今日 +3,977（PS5 可执行文件自动移植到 Linux/Windows）、`bilawalsidhu/gods-eye-view` +872（浏览器里的真实数据卫星侦察模拟器）、`chrislgarry/Apollo-11` +581（阿波罗 11 制导计算机原始源码）。

**一句话总结**：今天榜单的主线是 **"agent 开始接管专业工具"** —— 逆向工程（rea）、图表设计（diagram-design）都被做成 agent skill/MCP 直接调用；另一条线是 **AI 创作往工程化可控走**（artcraft）。两条线都指向同一个方向：agent 的竞争点正从"能不能写代码"转成"能不能操作真实工具链"。

（已标记 blogwatcher 中 2 条未读为已读）
