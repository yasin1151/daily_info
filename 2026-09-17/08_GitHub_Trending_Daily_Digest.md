
扫描完成，已标记 7 条为已读。以下是本次产出：

---

# GitHub Trending 每日速递 · 2026-09-17

今日 trending 榜共 21 个项目，筛出 **AI / Agent / LLM / 开发工具 / 数据工程** 相关 15 项，按今日新增 star 排序。stars 为抓取时快照。

## 一、代码审查与 Agent 工程（今日最热）

**1. alibaba/open-code-review** ★31,718（+3,215）· Go
简介：阿里开源的代码审查工具，混合架构——确定性流水线负责精准定位问题，LLM Agent 负责解释与修复建议；支持行级精确评论，内置多语言规则集（空指针、线程安全、XSS、SQL 注入），兼容 OpenAI / Anthropic 接口。仓库简介明确写着"在阿里规模上久经考验"。
为什么值得关注：+3,215 是今日全站第一增幅。大厂把内部审查工具开源，通常意味着它已在真实脏代码和高压 CI 上跑过一轮；"规则引擎定位置 + LLM 写解释"的分工，恰好绕开了纯 LLM 审查常见的漏报与幻觉，自建审查链路的团队可以直接对标。
https://github.com/alibaba/open-code-review

**2. affaan-m/ECC** ★260,243（+1,046）· JavaScript
简介：号称"agent harness 性能优化系统"——用 Skills、instincts、记忆、安全策略和 research-first 开发流程，给 Claude Code、Codex、Opencode、Cursor 等做外围增强。
为什么值得关注：260k stars 量级在整个 Trending 里都很扎眼，说明"给各家 coding agent 套一层统一增强壳"是当前最拥挤也最被需要的赛道。值得关注它到底用什么机制做跨 harness 抽象。
https://github.com/affaan-m/ECC

**3. addyosmani/agent-skills** ★95,420（+656）· JavaScript
简介：面向 AI coding agent 的"生产级工程技能"合集（Addy Osmani 出品）。
为什么值得关注：和上一条同属"agent 技能包"方向，但署名是 Google 工程圈的知名实践者，内容更偏工程规范而非性能 hack。这类仓库正在事实上成为 agent 写代码的质量基线，可以直接抄它的 skill 结构。
https://github.com/addyosmani/agent-skills

**4. cline/cline** ★68,350（+102）· TypeScript
简介：自主编程 agent，支持 SDK、IDE 扩展、CLI 三种形态。
为什么值得关注：老牌项目，今日仍在榜说明热度稳定。它的"同一内核、多形态分发"是 agent 产品化的成熟样本。
https://github.com/cline/cline

**5. anthropics/claude-code** ★145,479（+155）· TypeScript
简介：Claude 官方的终端 agentic 编程工具，能理解代码库、执行日常任务、解释复杂代码、处理 git 工作流。
为什么值得关注：榜单常客。今日增幅平缓，属于"基础设施型"存在。
https://github.com/anthropics/claude-code

**6. rlaope/oh-my-hermes** ★2,537（+74）· Python
简介：Hermes Agent 的一体化插件包——长期记忆系统 + 编码智能 + 模型优化工作流。
为什么值得关注：**你正在用的就是 Hermes**，这是社区为它做的增强插件。虽然体量小（2.5k stars），但同类插件生态刚起步，值得看一眼它的记忆实现思路。
https://github.com/rlaope/oh-my-hermes

## 二、模型推理与生成

**7. JustVugg/colibri** ★35,007（+1,532）· C
简介：纯 C、零依赖的推理引擎，把专家权重从磁盘流式加载，以在普通自有硬件上跑前沿 MoE 大模型。
为什么值得关注：今日增幅第二（+1,532）。"零依赖 + 磁盘流式加载专家"直接绕开了显存墙，是本地跑大 MoE 的一条硬核路线。名字下的标语很狂：Tiny engine, immense model。如果你关心消费级硬件上跑大模型，这是今天最值得读代码的一个。
https://github.com/JustVugg/colibri

**8. multimodal-art-projection/YuE** ★9,353（+370）· Python
简介：YuE2 —— 前沿音乐生成模型，支持符号化规划、零样本翻唱（covers）和 agentic 音乐编辑。
为什么值得关注：音乐生成里少数把"符号规划 + agent 化编辑"做进流程的项目，不再只是"输一段话出一段音频"，而是可迭代编辑。
https://github.com/multimodal-art-projection/YuE

**9. jamiepine/voicebox** ★54,356（+409）· TypeScript
简介：开源 AI 语音工作室，主打声音克隆、听写、创作三件事合一。
为什么值得关注：语音方向少见的"工作室级"完整产品而非单点模型，stars 已经到 54k。适合想看 AI 语音产品化落地形态的人。
https://github.com/jamiepine/voicebox

## 三、知识与 RAG / 研究 Agent

**10. Tencent/WeKnora** ★25,248（+1,201）· Go
简介：腾讯开源 LLM 知识平台——把原始文档变成可查询的 RAG、自主推理 agent，以及一个能自我维护的 Wiki。
为什么值得关注：+1,201 排今日第四。关键词是"self-maintaining Wiki"，即知识库自己维护自己，而不是每次问答都临时检索。企业知识库方向上这是目前最完整的开源组合拳之一。
https://github.com/Tencent/WeKnora

**11. alphaXiv/OpenResearch** ★4,380（+1,036）· Rust
简介：把 coding agent 变成 research agent。
为什么值得关注：+1,036 增幅，方向切得很准——利用已成熟的编码 agent 做科研检索与实验。Rust 实现，说明在追求速度/稳定性。小项目但增速猛，值得早期关注。
https://github.com/alphaXiv/OpenResearch

**12. anthropics/knowledge-work-plugins** ★24,271（+96）· Python
简介：Anthropic 官方的插件仓库，面向知识工作者在 Claude Cowork 里使用。
为什么值得关注：官方出品，"知识工作者插件"这个定位意味着 agent 正在从程序员工具向通用办公场景铺开，可以看 Anthropic 认为哪些办公能力该被插件化。
https://github.com/anthropics/knowledge-work-plugins

## 四、安全与视觉

**13. cloudflare/security-audit-skill** ★7,102（+1,249）· JavaScript
简介：给 coding agent 用的多阶段安全审计技能，产出"可独立验证、机器可读"的漏洞结论。
为什么值得关注：+1,249 排今日第三，且名字里 "independently verified / machine-readable" 是关键——它在解决 AI 安全审计最大的信任问题：怎么让人相信 agent 报的漏洞是真的。Cloudflare 出品，落地价值高。
https://github.com/cloudflare/security-audit-skill

**14. SnailSploit/Claude-Red** ★5,755（+383）· Python
简介：为 Claude skills 系统准备的攻击性安全技能库，每个技能是一个结构化 SKILL.md，覆盖从 SQLi 到 shellcode、EDR 绕过、漏洞利用开发的方法论。
为什么值得关注：和白帽审计是一对镜像——同一套 skill 机制被用来武装攻击面。它同时暴露了一个现实问题：SKILL.md 这种纯文本技能格式几乎无法做能力管控。
https://github.com/SnailSploit/Claude-Red

**15. roboflow/supervision** ★50,582（+292）· Python
简介：Roboflow 出品的可复用计算机视觉工具库。
为什么值得关注：稳定增长的老项目，CV 流水线的默认选择之一。
https://github.com/roboflow/supervision

## 五、其他入榜（非 AI 主线，一笔带过）

- **NationalSecurityAgency/ghidra** ★77,750（+1,059）· Java —— NSA 的逆向工程框架，今日增幅不低，可能受安全话题带动。
- **supabase/supabase** ★109,693（+352）· TypeScript —— Postgres 开发平台，简介里明确提"构建 AI 应用"。
- **ankitects/anki** ★30,840（+50）· Rust —— 间隔重复记忆软件。
- **ever-co/ever-gauzy**（+771）、**abue-ammar/tinycast**（+1,136，macOS 启动器）、**Lakr233/vphone-cli**（+444，无简介）—— 与 AI 主线无关。

---

**一句话总结**：今天的主线是 **"给 coding agent 装技能与记忆"**（ECC / agent-skills / security-audit-skill / oh-my-hermes / Claude-Red 五席），配合 **本地大模型推理突围**（colibri）和 **企业知识库自动化**（WeKnora）两条支线。最值得先看的是 alibaba/open-code-review 与 cloudflare/security-audit-skill——都是大厂把内部能力外放，且都直面"AI 结论如何可信"这个核心问题。

（已标记 blogwatcher 7 条为已读；本次产出将按 job 83667c76356d 归入 08:30 的 GitHub 每日入库流程。）
