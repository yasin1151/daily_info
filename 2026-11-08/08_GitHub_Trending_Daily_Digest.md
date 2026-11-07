
# GitHub Trending 日报 · 2026-11-08

今天榜单有一个很明确的主题：**Agent Skills 相关项目的大量涌现**。前五名里有四个是「技能包」仓库，也就是别人把 Claude Code 或 coding agent 的能力打包成可复用的模块，发布到 GitHub 上。这说明社区已经从「讨论 agent 能干什么」过渡到「把自己手上的 agent 工作流整理成仓库发布出去」。

---

## 一、Agent Skills 集中涌现（今日主线索）

**google/skills** · Python · 23,374 stars（今日 +449）
Google 官方把自家产品和技术栈的 Agent Skills 开源了。这是大厂第一次系统性地把「怎么让 AI 正确使用我的产品」写成技能包交给社区。值得关注的原因：过去 agent 用 Google API 出问题，只能靠开发者自己摸索文档；现在官方给了一份标准答案，相当于给所有 coding agent 装了 Google 生态的说明书。看这个仓库还能反推 Google 内部认为哪些 API 最容易出错。

**anthropics/skills** · Python · 188,758 stars（今日 +386）
Anthropic 官方的 Agent Skills 公开仓库。它是目前 Skills 事实标准的重要来源之一：SKILL.md 的目录结构、frontmatter 字段、渐进式加载（progressive disclosure）的设计，基本都以此为准。今天又涨了近 400 星，说明生态仍在扩张，而不是短暂热度。

**mattpocock/skills** · Shell · 317,671 stars（今日 +1,111）
作者 Matt Pocock（TypeScript 圈知名教育者）直接把自己 `.agents` 目录里的技能包公开了，项目简介只写了一句 "Skills for Real Engineers. Straight from my .agents directory."。这是今天最能说明问题的一个仓库：**个人开发者开始把自己的 agent 配置当作作品发布**。star 数高得夸张，更多反映的是「大家想知道高手怎么配 agent」这种围观心态，代码本身反而次要。建议看目录结构，而不是逐个读 SKILL.md。

**cloudflare/security-audit-skill** · JavaScript · 65,659 stars（今日 +2,088，今日涨幅第一）
一个面向 coding agent 的多阶段安全审计技能：分阶段扫描，产出**可独立验证、机器可读**的漏洞结论，而不是让模型自由发挥、声称「我发现了漏洞」。今天能冲到第一，是因为它解决了一个真实痛点：AI 做安全审计最怕编造漏洞，而「机器可读、可复核」正好对症。Cloudflare 出品也提供了可信度。

**vercel-labs/agent-browser** · Rust · 46,799 stars（今日 +180）
给 AI agent 用的浏览器自动化 CLI，用 Rust 写成。本质是把「agent 操作网页」这件事做成一个命令行工具，让 agent 通过 shell 调用，而不是塞进多模态输入。Rust 实现意味着启动快、内存占用低，适合高频调用。

---

## 二、今日新上榜（此前未被抓取到的）

**ranxianglei/billion-context** · TypeScript · 4,591 stars（今日 +185）
上下文压缩插件，宣传语是「月级长会话、10 万上下文够用、省 5 倍 token」。今天新上榜里技术含量最高的一个。它附带一篇论文（Model-Driven Incremental Hierarchical Compression，training-free 的多代际上下文管理），还给出了生产级纵向数据：4.5 个月、三台主机、174,327 次模型调用、累计 187.6 亿输入 token、零窗口溢出。对长期运行的 coding agent 来说，这才是真问题：上下文不是「不够长」，而是「越长越贵、越容易失忆」。作者用 prefix-cache 命中率 95-97% 作为健康指标，思路很工程化。

**meta/astryx** · TypeScript · 14,467 stars（今日 +185）
Meta 内部用了八年的设计系统正式开源，React 19 + StyleX，150+ 无障碍组件。特别之处在于它从一开始就把「人和 AI 用同一套工具建 UI」当作设计目标：API、文档、CLI 三者一起设计。目前已 13000+ 应用在用，Beta 阶段。对做 AI 生成前端的人来说，这是一个「AI 能可靠产出 UI 代码」的基础设施候选。

**dsx-ai-factory/nvke** · Go · 545 stars（今日 +125）
NVIDIA Kubernetes Engine，在自有裸金属 GPU 上跑托管 K8s 的管理平面。每个 workload 集群独立控制面、etcd、节点池，你运维管理面，客户用 kubectl 用集群。目前是 preview，官方明说不建议上生产。star 少但信号价值高：GPU 资源调度正在从「抢卡」转向「像云一样卖卡」，这是 MLOps 基础设施层的新形态。

**sherlock-project/sherlock** · Python · 100,391 stars（今日 +1,819）
老牌工具重新上榜：用用户名跨社交网络定位账号。本身与 AI 无关，今天涨得快大概率是某个安全或 OSINT 话题带起来的流量。对做 agent 的人来说有个用法：可作为「人物背景核查」类 agent 的一个工具节点。

**mbillow/localthings** · Python · 1,049 stars（今日 +184）
在 Home Assistant 里通过本地网络控制三星家电，完全不需要云端账号。小项目，但代表了「本地优先、拒绝云依赖」这条线在智能家居里持续有人做。

**tailwindlabs/tailwindcss** · TypeScript · 98,451 stars（今日 +181）
CSS 框架，常规热度波动，无 AI 相关内容。AI 生成前端代码时，Tailwind 仍是模型最熟练的样式方案之一，值得留意它和上面 astryx 那类「AI 友好设计系统」会不会撞车。

---

## 三、其他值得一扫

- **milind-soni/OpenMausBot** · TS · 16,931（+1,986）：开源版 Grok Bot 替代品，带一个 bot 可用的虚拟机。今日涨幅第二，说明「给 agent 一台自己的机器」这个方向很受欢迎。
- **zed-industries/zed** · Rust · 94,256（+1,119）：高性能多人协作编辑器，Atom 原班人马。AI 编辑器赛道的重要变量。
- **astral-sh/ruff** · Rust · 50,967（+350）：Python linter / formatter，速度是核心卖点。AI 写 Python 越多，ruff 越像必备的检查工具。
- **prometheus/prometheus** · Go · 67,441（+325）：监控与时序数据库，常规热度。

---

## 一句话判读

今天真正值得动手试的只有两个：**billion-context**（如果你在跑长时间 coding agent，token 账单会直接受益）和 **cloudflare/security-audit-skill**（如果你让 agent 碰过生产代码，这个能减少「编造漏洞」的幻觉）。其余 skills 仓库建议只读目录结构，不必逐个装。
