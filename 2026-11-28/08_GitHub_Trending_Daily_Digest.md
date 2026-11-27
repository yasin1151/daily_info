
# GitHub Trending 日报 · 2026-11-28

今日榜单 16 个项目，AI / Agent / 开发工具占了 12 个。核心信号：**竞争焦点从"模型能力"移到了"技能包 + agent 工作流"**——前十里 6 个是给 Claude Code / Codex / Cursor 用的 skills 或方法论仓库。

---

## 1. Claude-BugHunter —— 把 Claude Code 变成红队操作员
`elementalsouls/Claude-BugHunter` · Python · **26,035 ★（今日 +1,615，全榜第一）**
https://github.com/elementalsouls/Claude-BugHunter

**是什么**：一个开箱即用的 Claude Code 技能包，85 个技能、16 个 slash 命令、681 条已披露漏洞报告模式（其中 433 条单独标注可审计），覆盖 24 类核心漏洞，外加企业身份与基础设施攻击矩阵，集成 Burp MCP，并自带"约定范围"约束，防止 agent 越界。

**为什么值得关注**：这是"技能包"这条路走到极端安全场景的样本——不再让模型泛泛地"帮我找漏洞"，而是把方法论、payload 链模板、VRT 映射、报告规范全部预置。今日单日涨星超过 1600，说明安全从业者对"agent 落地到具体岗位"的需求是真实且急迫的。

---

## 2. superpowers —— 给编码 agent 装一套开发方法论
`obra/superpowers` · Shell · **328,286 ★（今日 +916）**
https://github.com/obra/superpowers

**是什么**：不是工具，是一套"软件工程纪律"。agent 一启动不会直接写代码，而是先追问你真正要做什么 → 提炼出 spec → 分块给你确认 → 出实施计划（标准是"给一个没品味、没判断力、没有项目上下文、还讨厌写测试的初级工程师也能照着做"）→ 强制红绿 TDD、YAGNI、DRY。

**为什么值得关注**：README 里支持列表几乎覆盖了所有主流 agent 宿主：Claude Code、Codex CLI、Cursor、Gemini CLI、GitHub Copilot CLI、Kimi Code、Qwen Code、OpenCode、Factory Droid，连 Hermes Agent 都单独列了一节。32 万星和这种"跨宿主中立"的姿态说明：大家已经不指望换模型解决问题，开始卷**流程约束**了。

---

## 3. CLI-Anything —— 让所有软件对 agent 可用
`HKUDS/CLI-Anything` · Python · **66,981 ★（今日 +668）**
https://github.com/HKUDS/CLI-Anything

**是什么**：港大数据智能实验室的项目，一句话：把任意软件包装成 agent 能调用的 CLI，然后由 agent 驱动去做真东西——CAD 建模、3D 场景、图表、字幕、游戏。配套 CLI-Hub 注册表（`pip install cli-anything-hub`）统一分发社区产出的 CLI。

**为什么值得关注**：它跟 MCP 是两条路线之争。MCP 是"让软件作者提供协议接口"，CLI-Anything 是"我帮你生成一个 CLI 壳，软件不用改"。对存量软件（尤其桌面软件）来说后者成本低得多。README 里已经在讨论给 Hermes 做编排技能，社区驱动明显。

---

## 4. MiniMind —— 3 块钱、2 小时，从零训出 64M 小模型
`jingyaogong/minimind` · Python · **72,199 ★（今日 +667）**
https://github.com/jingyaogong/minimind

**是什么**：全部用 PyTorch 原生实现，不调任何高层抽象库，覆盖 Pretrain → SFT → LoRA → RLHF(DPO) → RLAIF(PPO/GRPO/CISPO) → Tool Use → Agentic RL → 蒸馏 → MoE 的完整链路，还有视觉版 MiniMind-V、全模态版 MiniMind-O、扩散语言模型和线性模型分支。

**为什么值得关注**：README 老实交代了数字口径——"2 小时"指单张 3090 跑完 SFT 一个 epoch，"3 块钱"是那段时间的租卡成本。这种不吹的口径反而让它在中文社区长期霸榜。想真正搞懂 LLM 训练而不是调 API 的人，这是目前最完整的教学级代码库。

---

## 5. last30days —— 用真人投票排序，不用编辑排序
`mvanhorn/last30days-skill` · Python · **76,345 ★（今日 +664）**
https://github.com/mvanhorn/last30days-skill

**是什么**：一个 agent 技能。给一个话题，并行扫 Reddit 上票、X 点赞、YouTube 转录、TikTok 互动、HN、Polymarket 真金白银赔率、arXiv、专利、招聘页，按真实互动量排序，再由 agent 裁判综合成一份简报。零配置，Reddit/HN/Polymarket/GitHub 开箱即用。

**为什么值得关注**：作者原话很锋利——"Google 聚合的是编辑，last30days 聚合的是人"。对做信息聚合的人来说，这是把"排序权"从编辑换成注意力+资金的完整实现，方法论比代码更值钱。50+ Agent Skills 宿主都能装。

---

## 6. firecrawl —— agent 的投喂层
`firecrawl/firecrawl` · TypeScript · **211,662 ★（今日 +833）**
https://github.com/firecrawl/firecrawl

**是什么**：一个 API 打通搜索、抓取、解析，接 550+ 数据源，定位是"让 agent 更聪明的知识基础设施"。

**为什么值得关注**：21 万星基本坐实了它的品类地位——**agent 再强，没有干净输入也是空转**。今日 +833 说明这块需求仍在膨胀，没有随 agent 框架成熟而萎缩。

---

## 7. diagram-design —— 技能的竞争卷到了"审美"
`cathrynlavery/diagram-design` · HTML · **74,440 ★（今日 +731）**
https://github.com/cathrynlavery/diagram-design

**是什么**：一套"编辑部级"图表设计技能，52 种图表类型，适配 Claude Code、Codex、GitHub Copilot、Cursor、Factory Droid、Qoder、Pi。

**为什么值得关注**：纯 HTML 项目能冲到 7.4 万星很反常，说明痛点不在功能而在**输出难看**。agent 能写代码之后，瓶颈转移到"做出来的东西能不能直接给人看"。这是技能包里少见的"设计/排版"方向。

---

## 8. stitch-skills —— 大厂开始押注 Agent Skills 标准
`google-labs-code/stitch-skills` · TypeScript · **13,583 ★（今日 +311）**
https://github.com/google-labs-code/stitch-skills

**是什么**：Google Labs 出的 Agent Skills 库，配合 Stitch MCP server 使用，每个技能都遵循 Agent Skills 开放标准。

**为什么值得关注**：MCP 解决了"工具怎么接"，Skills 在解决"经验和流程怎么打包复用"。Google 官方下场做技能库，且明确站开放标准，意味着这层可能形成事实标准，第三方技能市场（前面几个项目）会跟着受益或被迫对齐。

---

## 9. OpenSRE —— 专门修 CI 的开源 agent
`Tracer-Cloud/opensre` · Python · **16,117 ★（今日 +326）**
https://github.com/Tracer-Cloud/opensre

**是什么**：一个 CLI agent，读失败的 CI 运行、追根因、直接推一个修复 PR 给你审。完全自托管，可接你自己的模型。目前是 public alpha，API 和集成还会变。

**为什么值得关注**：README 第一句就是痛点——"你的 CI 告诉你它挂了，但不说为什么、怎么修"。代码被 AI 写得越多，构建失败越频繁，"谁修 build"从杂活变成瓶颈。这是 SRE/DevOps 场景里少见的、边界清晰（只做一件事）的 agent 落地样本。

---

## 10. autoclip —— 开源版 OpusClip
`zhouxiaoka/autoclip` · Python · **17,572 ★（今日 +733）**
https://github.com/zhouxiaoka/autoclip

**是什么**：本地优先的 AI 切片工具，一个链接一键出片，自带 MCP server，零订阅。

**为什么值得关注**：把"长视频转短视频"的边际成本压到接近零，而且数据不出本地。对做内容分发的人，这是替代按分钟计费的 SaaS 的直接方案。

---

## 11. cursor/plugins —— 编辑器厂商开始定义插件规范
`cursor/plugins` · TypeScript · **20,010 ★（今日 +242）**
https://github.com/cursor/plugins

**是什么**：Cursor 的插件规范与官方插件集。

**为什么值得关注**：星数不高但信号明确——编辑器厂商不再满足于"支持 skills 目录"，而是开始收口自己的插件生态。早期规范往往就是后来的兼容性债，值得提前看一眼它怎么定义扩展点。

---

## 12. OpenVINO —— 端侧推理的老牌选项
`openvinotoolkit/openvino` · C++ · **12,945 ★（今日 +152）**
https://github.com/openvinotoolkit/openvino

**是什么**：Intel 的开源 AI 推理优化与部署工具包，重点在 CPU / 集成显卡 / NPU 上把模型跑起来。

**为什么值得关注**：榜单里唯一偏"部署落地"的项目。企业私有化和端侧部署绕不开它，涨幅平稳说明是刚需而非炒作。

---

## 其他值得一提

- **mjmirza/app-store-compliance**（7,877 ★，+531）：App Store / Google Play 上架被拒的开放 playbook，收录 125 个真实拒绝案例。跟 AI 无关但今天涨得很猛，做移动端的可以直接抄。
- **toeverything/AFFiNE**（79,436 ★，+469）：Notion + Miro 的开源合体，知识库赛道的常青树，本地优先。
- **nginx/nginx**（33,661 ★，+148）：官方源码仓库罕见上榜，可能是版本发布带来的关注。

---

**一句话总结**：今天榜单最值得看的是第 2 和第 3 个项目——它们代表两种截然不同但都在被验证的答案：一个是**用方法论约束 agent**（superpowers），一个是**改造世界去适配 agent**（CLI-Anything）。技能包生态已经卷到安全审计、图表排版、舆情检索这种垂直岗位了。
