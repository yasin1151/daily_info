
今日 GitHub Trending 已抓取完成（页面直连 + GitHub API 交叉核对数据），blogwatcher 两个新条目已标记已读。

---

# GitHub 今日热门 · AI 项目精选
2026-10-24 · 榜单 8 个项目，筛出 5 个 AI/Agent 相关

今天榜单几乎被「Agent 基础设施 + Agent 技能库」占满：前五名里有四个都是在给 Agent 加能力或加约束；纯模型项目只有一个 TTS。

---

## 1. Cloudflare 开源「AI 安全审计」技能：让编码 Agent 自己去挖漏洞
**cloudflare/security-audit-skill** · JavaScript · ★42,073（今日 +2,706）· MIT

**是什么**：一个 coding-agent skill，把帮你写代码的 Agent 改造成安全审计员。跑的是六阶段流水线：侦察（产出 `architecture.md` 和覆盖度台账）→ 按台账分配多个隔离的 hunter agent 分头找洞 → 每个候选漏洞交给全新的 verifier agent 专门**试图证伪** → 只把站得住的写进 `findings.json` 并用 JSON schema 校验 → 再由独立 agent 复核源码引用 → 最后生成与目标无关的报告。三种结论严格区分：`confirmed`（有完整源码链路）、`needs_validation`（有未解决的确切事实、不给严重级别）、`rejected`（已被推翻）。同一仓库多次跑是增量叠加的。

**为什么值得关注**：这是 Cloudflare 那套全舰队漏洞挖掘 harness 的"种子版本"，官方博客写明整套系统就是从这一个 skill 长出来的。它最有价值的设计不是"让 AI 找漏洞"（这个大家都在喊），而是**把"证伪"和"独立复核"做成强制流程**——每个发现都要过一个专门唱反调的 agent。这正好是 AI 安全审计最缺的一环：模型太爱顺着你的话编漏洞。注意它明确要求 OS 级沙箱（断网、白名单环境、资源限制），没有沙箱就把结论停在 `needs_validation` 而不执行目标代码。

https://github.com/cloudflare/security-audit-skill

---

## 2. 英伟达 OpenShell：给自主 Agent 用的内核级安全沙箱
**NVIDIA/OpenShell** · Rust · ★18,761（今日 +1,240）· Apache-2.0

**是什么**：面向"成批自主 Agent"的安全运行时。两条腿走路：一是**内核级强制**——每个 Agent 跑在隔离沙箱里，文件访问、系统调用全部受内核控制，每个网络连接出沙箱前都要过策略检查，Agent 永远看不到真实凭据（OpenShell 只在请求发往获批端点时才注入）；二是**形式化验证**——策略改动生效前，先算出"这次放行会新开哪扇门"（比如用凭据访问一个新主机、调用一个新 API 方法），高风险的挂起等人工审批。支持 Linux、Apple Silicon macOS、WSL2，Docker/Podman 起沙箱。

**为什么值得关注**：现在 Agent 安全的主流做法是"提示词里写别乱来"，这是把约束压到内核和凭证层——从"劝它别做"变成"它做不到"。这和上面 Cloudflare 那个 skill 的需求正好对上（那个明确要求 OS 级沙箱）。571 个 open issue 说明还在快速迭代期，0.1.x 刚定了稳定发版节奏，生产用要谨慎。Apache-2.0 + 官方文档齐全，自建 Agent 平台的话值得先读架构文档。

https://github.com/NVIDIA/OpenShell

---

## 3. Anthropic 开源 11 个「岗位插件」：把 Claude 变成销售/法务/财务/数据分析师
**anthropics/knowledge-work-plugins** · Apache-2.0 · ★32,191（今日 +643）

**是什么**：面向 Claude Cowork（也兼容 Claude Code）的插件集，一次放出 11 个职能插件：productivity、sales、customer-support、product-management、marketing、legal、finance、data、enterprise-search、bio-research，外加一个"插件管理"插件用来自己造新插件。每个插件都是纯 markdown + JSON，零代码零构建：`skills/` 放领域知识和流程（Agent 自动按需调用）、`commands/` 放显式斜杠命令（如 `/finance:reconciliation`、`/data:write-query`）、`.mcp.json` 接外部工具（Slack、Notion、Jira、Snowflake、HubSpot、PubMed……）。

**为什么值得关注**：这是 Anthropic 亲自给的"插件该怎么写"的参考实现——**用文件结构代替框架**，没有 SDK、没有运行时依赖，fork 下来改 markdown 就能改成自己公司的版本。对做企业 Agent 落地的人来说，这 11 个目录基本就是一张"岗位 × 工具 × 工作流"的对照表，比自己从零设计 schema 快得多。注意它是通用起点而非成品，官方自己说"真正有用的部分是你把公司术语、组织结构和流程塞进去之后"。

https://github.com/anthropics/knowledge-work-plugins

---

## 4. Claude-Red：78 个红队 SKILL.md，按对话触发自动加载
**SnailSploit/Claude-Red** · Python · ★8,448（今日 +209）· MIT

**是什么**：面向 Claude Skills 系统的攻击性安全技能库，78 个 skill 分 23 类，覆盖从 SQL 注入到 shellcode、从 EDR 规避到 ADCS 滥用的具体攻击面。每个就是一个结构化 `SKILL.md`，把 Claude 预设成该领域的专家：知道手法、工具链、边界情况和提权路径。装法就是 clone 到 `~/.claude/skills/`，之后按对话触发词自动加载（提到 SQL 注入就加载 `offensive-sqli`），不用的技能不占上下文。

**为什么值得关注**：和 Cloudflare 那个"防守型"技能正好是一对——同一套 Skill 机制，一边做审计一边做攻击。它印证了今年一个明显趋势：**安全能力的交付单位从"工具/脚本"变成了"给 Agent 的方法论文档"**。可用于授权红队、赏金初筛、CTF 备赛。红线很清楚：必须授权环境，这类技能库本身不提供任何隔离，跑起来就是在你机器上执行攻击代码。

https://github.com/SnailSploit/Claude-Red

---

## 5. VoxCPM2：2B 无 tokenizer TTS，30 语言 + 一句话造声音
**OpenBMB/VoxCPM** · Python · ★40,236（今日 +144）· Apache-2.0

**是什么**：面壁智能的 tokenizer-free TTS，用端到端 diffusion autoregressive 架构直接生成连续语音表示，跳过离散 token 化这一步。VoxCPM2 是最新大版本：2B 参数、200 万小时以上多语种语音训练、30 种语言（输入不用打语言标签）、48kHz 录音棚级输出，底座是 MiniCPM-4。亮点功能有两个：**Voice Design**——只给一句自然语言描述（性别、年龄、音色、情绪、语速）就能凭空造一个全新声音，不需要参考音频；**Controllable Cloning**——一段短参考音频克隆音色，还能额外给风格指令调情绪语速而不破音色。4090 上 RTF 约 0.3，接 vLLM-Omni 可到约 0.13，有 OpenAI 兼容 API。权重和代码 Apache-2.0，明确可商用。

**为什么值得关注**：这是今天榜单里唯一的模型项目，也是国产开源里少见的"能直接商用"的 TTS——许可证干净、有 vLLM 官方多模态服务支持、有 OpenAI 兼容接口，工程落地门槛比多数研究型 TTS 低。"无 tokenizer + 48kHz 内置超分"意味着不用外挂上采样器，链路更短。Voice Design 那个能力值得单独试：它把"配音"从"找演员/找素材"变成了"写描述"。

https://github.com/OpenBMB/VoxCPM

---

## 其他上榜（非 AI 向）
- **Renhuai123/ziwei-doushu** ★6,842（+547）— 紫微斗数开源排盘引擎，基于倪海厦《天纪》体系，含完整排盘算法、四化系统、格局知识库和古籍原文数据。国产小众垂类一天涨五百多星，算今日榜单里的意外项。
- **php/php-src** ★41,553（+722）、**nodejs/node** ★122,849（+93）— 老牌运行时常规上榜，无新事件。

---

**一句话盘面**：今天的高星不是"新模型"，而是"Agent 的护栏和技能包"——Cloudflare 教 Agent 怎么审、Claude-Red 教它怎么攻、英伟达给它造牢房、Anthropic 给它排岗位。基础设施层正在围着 Agent 重组。
