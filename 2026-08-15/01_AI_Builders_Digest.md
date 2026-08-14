
I have everything I need. Let me compose the final Chinese digest, focused on the user's interests (AI agents, coding agents, LLM infrastructure, model/tooling/product shifts, 自研引擎/Agent 工具链). I'll keep it concise and scannable, with all links present.

---

# AI Builders Digest — 2026-08-15

今日有 19 位 builder 的新动态 + 1 期播客。以下按主题高信号内容整理。

## 🤖 Agent / 编码 Agent 实战

**Boris Cherny（Anthropic，Claude Code 团队）** — 披露了一场数周的实验：让 Claude 在 Slack 频道里独立接管应用的日常维护。它每天跑例行任务（崩溃模糊测试修复、死代码清理、去重抽象、泄漏检查），覆盖 iOS/Android/Desktop/Web/CLI 与 Agent SDK，数周开出 388 个 PR、其中 180 个经 Claude Code Review + 人工审核后合并。Claude 通常一次就能做对，不对时会自动调优第二天的任务。这是「Agent 长期维护代码库」可直接复用的工作流范本。
https://x.com/bcherny/status/2088014489438621990

**Swyx（AI Engineer 社区）** — 改进 /align-me（Claude Code 对齐提示词工具），借鉴「spec decoding」思路支持并行批量提问、向前看 2-10 步。核心洞察：**人类的 I/O 昂贵，减少往返次数是提升 Agent 效率的关键**，批量提问在设计探索类任务上效果出奇地好。
https://x.com/swyx/status/2088073777779515615

**Amjad Masad（Replit CEO）** — 仅靠给 LLM 加一个「编码 harness（代码执行框架）」就近乎解决了 ARC-AGI-3 基准，印证他此前的判断：**编码能力正在泛化扩展 LLM 的通用能力**。他断言 Replit 内部确实如此，并预测到明年「用电脑将变成可选」。
https://x.com/amasad/status/2088124774824521786
https://x.com/amasad/status/2088110851681386864

**Guillermo Rauch（Vercel CEO）** — 推广「一条命令管理所有 token」的编码 AI 网关，可统一配置 Claude Code、Codex 等现有 harness，兼顾模型选择、成本、可观测性与零数据保留（ZDR），预测这将是规模化使用编码 AI 的默认方式。另在 v0 上免费提供 GLM 5.2（最高 500 TPS）。
https://x.com/rauchg/status/2088020529039180204
https://x.com/rauchg/status/2087982033499042205

**Nikunj Kothari（fpvventures 合伙人）** — 抛出高价值之问：用户到底想要掌握全部上下文的「超级 Agent」，还是按部门/目标分工的多个子 Agent？他认为若把 Agent 类比「人」，Grok Bot「按目标隔离工具与上下文」的设计逻辑讲得通。
https://x.com/nikunj/status/2088029329624371544

## 🧠 模型与产品迭代

**Josh Woodward（Google Gemini/Studio 副总裁）** — 发布 **Gemini 3.7 Flash**：更快、成本便宜 50%，整个迭代仅约三周，体现 Google 在速度与成本上的推进节奏。
https://x.com/joshwoodward/status/2088016871710957587

**Thibault Sottiaux（OpenAI，Codex & ChatGPT）** — ChatGPT 新增 **Computer History 插件**，可点评你一天的操作（如 Slack 占 48% 活动量）；并支持直接在 ChatGPT 内处理 Google Docs/Sheets/Slides，边聊边改。
https://x.com/thsottiaux/status/2088133823619895712
https://x.com/thsottiaux/status/2088103609477238858

**Sam Altman（OpenAI CEO）** — 只发极简一条「/ultrafast」，配图，1638 赞、205 回复，社区猜测 OpenAI 将推出的「超快」能力。
https://x.com/sama/status/2088101491802243121

## 💭 对 AI 行业的冷峻观察

**Madhu Guru（Meta AI 高级总监）** — 犀利观点：**「Prompt debt」就是新的技术债**。模型出错加规则、调用失败加示例、输出不对加约束，三个月后系统提示词变成一本小说，把更聪明的模型逼成「只会执行规则」。主张每次模型更新至少应削减 50% 提示词。顺便吐槽 AI 产品命名全是「Studio」。
https://x.com/realmadhuguru/status/2087916590964851172

**Aaron Levie（Box CEO）** — 反驳「工程师将被消灭」：AI 给工程师的是加速一切的强力工具，工程价值不降反升——模型越强、越需要领域专家善用。「这是个做专家的好时代。」
https://x.com/levie/status/2088105350201270529

**Zara Zhang（产品/增长 Builder）** — 反直觉印证：最热门的岗位全带「工程师」字样（forward-deployed engineer、design engineer、growth engineer）——AI 没有取代工程，而是催生了更多元的新型工程岗。
https://x.com/zarazhangrui/status/2088087765267386564

**Matt Turck（FirstMark 合伙人）** — 针砭 AI 生态两极分化和你死我活的估值军备竞赛现状。
https://x.com/mattturck/status/2087978386195103916

## 🎙️ 本期播客

**No Priors — 《What Chess.com Teaches Us About Superhuman Capabilities》**，嘉宾 Chess.com CEO Erik Allebest

**核心启示**：当机器早已超越人类（深蓝击败卡斯帕罗夫三十余年），人类反而前所未有地更爱这项活动——AI 没有终结人类技能，反而逼人更强、让游戏更好玩。Erik 2005 年从破产拍卖以 5.6 万美元买下 chess.com 域名，不融资、不追热点，以「现金增长的速度」经营二十多年，做成 2.5 亿用户、年营收超 2 亿美元。反直觉洞察：神经网络引擎（Leela Chess Zero）让棋更精彩、棋手更强；技能无捷径、工具才有捷径；他要用「评级」重做扑克——「输一百美元我不太在乎，但扑克评级掉一百分真的很难受」。他认为超人类智能的关键「更多是文化问题而非技术问题」。
https://www.youtube.com/@NoPriorsPodcast

---

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
