
数据齐备（feed 生成于 2026-09-24，17 位 builder / 37 条推文 / 3 篇 Anthropic 工程博客，无播客）。以下是本期摘要。

---

# AI Builders 每日摘要 · 2026-09-25

> 数据源：17 位 builder / 37 条推文 + 3 篇 Anthropic 工程博客（feed 生成于 2026-09-24，约 1 天前，属新鲜数据）。本期无播客更新。

---

## 一、Agent 引擎与工具链（本期重点）

### 1. Anthropic 工程博客：Managed Agents —— 把「大脑」和「手」解耦
**来源**：Anthropic Engineering ｜ https://www.anthropic.com/engineering/managed-agents

把 agent 虚拟化成三个可独立替换的接口：**session**（append-only 事件日志）、**harness**（调用 Claude、路由 tool call 的循环）、**sandbox**（执行环境）。关键动作是把 harness 从容器里搬出来——容器变成「cattle」，挂了就当 tool-call error 抛回给 Claude；要重试就用 `provision({resources})` 重建。接口设计得很克制：`execute(name, input) → string`、`wake(sessionId)`、`getSession(id)`、`emitEvent(id, event)`、`getEvents()`。

**实测收益**：p50 TTFT 降约 60%，p95 降 90% 以上；不再让每个 session 预先付容器启动成本（原话：*"TTFT is the latency the user most acutely feels."*）。

**安全设计值得抄**：凭证（repo token、OAuth）永不进入 sandbox，harness 走代理调 MCP、完全不知道凭证存在。他们点破了原来的攻击面——*"a prompt injection only had to convince Claude to read its own environment."*

**为什么值得关注**：这是目前最完整的「自研 agent 引擎」架构参考。核心判断是：**harness 里编码的是对模型短板的假设，而这些假设会随模型变强而过期**。他们举的例子很具体——Sonnet 4.5 会有「context anxiety」（接近上下文上限就草草收尾），所以 harness 里加了 context reset；换到 Opus 4.5 后这个行为消失了，那些 reset 成了 dead weight。结论就是：**只对接口有主见，不对实现表态**（"meta-harness"）。

### 2. Anthropic：如何给 Claude 做 containment（这篇原话最狠）
**来源**：Anthropic Engineering ｜ https://www.anthropic.com/engineering/how-we-contain-claude

- **人肉监督已失效**：遥测显示用户批准了约 **93% 的权限提示**，越批越不看。Claude Code 的 OS 级 sandbox（macOS Seatbelt / Linux bubblewrap）把权限提示减少了 **84%**；auto mode 在执行前拦下约 83% 的「过度热情」行为。
- **模型层防御的天花板**：Opus 4.7 在 Gray Swan 的 agent 红队基准上，单次提示注入攻击成功率约 0.1%，但 100 次自适应尝试后升到 **5–6%**。原话：*"any probabilistic defense has a non-zero miss rate."*
- **三个他们自己漏掉的风险**：
  1. **trust dialog 之前就执行的代码**——克隆一个有 `.claude/settings.json` hook 的 repo，Claude Code 在弹「Do you trust this folder?」之前就把配置解析并执行了。
  2. **用户本人就是注入向量**——内部红队钓鱼，伪装成「帮我跑一下这个」的 prompt，让 Claude 去读 `~/.aws/credentials` 再 POST 到外部端点。**25 次重试里成功了 24 次**。因为指令来自用户，"there's nothing anomalous for a classifier to catch"。
  3. 多 agent 场景下 HITL 更不可能有效。
- **唯一站得住的防线是环境层**：egress 控制让那个 POST 根本发不出去，文件系统边界让 `~/.aws` 根本够不着。

**为什么值得关注**：如果你在跑无人值守的长时 agent，这篇的威胁模型三分法（用户滥用／模型越界／外部攻击）+「防御必须重叠」的思路可以直接落地。

### 3. Anthropic：Claude Code 质量下降复盘（3 个 bug，已重置所有订阅者用量限额）
**来源**：Anthropic Engineering ｜ https://www.anthropic.com/engineering/april-23-postmortem

三个月里三个独立改动叠加：3 月 4 日把默认 reasoning effort 从 high 改成 medium（想压延迟）；3 月 26 日的缓存优化用 `clear_thinking_20251015` + `keep:1`，本该只清一次 thinking，bug 让它**每个 turn 都清**，表现为「忘事、重复、奇怪的工具选择」，还顺带推高了缓存 miss（这可能就是大家觉得额度掉得快的真实原因）；4 月 16 日为压 verbosity 往 system prompt 加了「tool call 间 ≤25 词、最终回复 ≤100 词」，后来做 ablation 发现让 Opus 4.6/4.7 掉了 **3%** 智力，20 日回滚。

**为什么值得关注**：harness 层每一个「小优化」（默认 effort、system prompt 里的一行、缓存策略）都会真实改变模型表现，而且极难复现——他们自己花了一周多才定位，还有两个无关的内部实验把 bug 掩盖了。后续做法：system prompt 改动一律跑全套 per-model evals + soak period + 灰度。

### 4. Guillermo Rauch（Vercel CEO）发布 Drives：agent 三件套 + 存储解耦
**来源**：@rauchg ｜ https://x.com/rauchg/status/2102820148629614685（1453 赞）

原话框架：*"All successful agents have 3 key components: 🧠 Brain → model, harness (logic)｜👐 Hands → tools, computer, browser｜🗃️ Files → memories, skills, repos."* 单机版就是「把 `claude` 或 `fx` 挂在 Mac Mini 上跑一整天」；云上要拆——harness 跑 Fluid compute，用 Workflow 把 event log 做持久化以扛重启/滚动发布/崩溃；hands 用 Browserbase/Kernel 浏览器舰队、Sandbox、乃至 just-bash 这类轻量工具。新发的 **Drives** 补上最后一环：把存储也解耦，比如「dreaming」这种每晚跑的记忆整理 cron job，可以直接读写文件而**不用把整个 agent 电脑 boot 起来**。他还强调拆开不只是省成本，*"it also massively improves security and auditability. I'd argue you can't even run a secure agent otherwise!"*

**另**：他另一条说让 Opus 5.5 去优化 `.zshrc` 等 shell 启动时间，*"found a lot of really great optimizations other models missed."*

**为什么值得关注**：这和 Anthropic 的 Managed Agents 是同一思路的两家独立实现（brain/hands 解耦 + session/存储外置），云上跑 agent 的成本模型和安全模型都建立在这个拆法上。

### 5. Boris Cherny（Anthropic，Claude Code）：Claude 在做形式化方法 + 客户端提速
**来源**：@bcherny ｜ https://x.com/bcherny/status/2102898067133595992 ／ https://x.com/bcherny/status/2102854267782705648

他给「formal methods 圈的人」补了细节，Claude 实际做的是四步：**1)** 给程序（尤其是棘手的状态机／有竞态的部分）建模型 → **2)** 在模型里找反例（这些就是疑似 bug）→ **3)** 复现 → **4)** 在代码里修。他明确说：*"It's not that the whole codebase is formally verified (yet!..), more that the hairiest parts of the code are modeled, checked for counter-examples, and fixed."*

另一条（3292 赞）：Claude Code 和 Desktop 最近几周明显变快，他们发了讲实现细节的 blog，*"Lots of juicy learnings & techniques in the blog post for engineers working on speeding up your own apps."*

**为什么值得关注**：「用模型给状态机找反例」是当前最实在的 agent 辅助正确性路径，比笼统的"AI 写测试"具体得多。

---

## 二、模型与产品动向

### 6. Opus 5.5 已成 builder 圈的事实默认，且「最好的模型和最好的 harness 分属两家」
**来源**：Swyx ｜ https://x.com/swyx/status/2102650014552182920（205 赞）｜ Peter Yang ｜ https://x.com/petergyang/status/2102952201350254667

Swyx（smol.ai / AI News）原话：*"can confirm. ran @latentspacepod AINews side by side with 6 Sol and the difference was night and day… 5.5 Opus is the new default model for AINews going forward. so much more concise and tasteful reporting, with much less slopese than even 5 Opus."*

Peter Yang（309 赞）的清单：*"Opus 5.5 is: Smart / Fast / Fun to talk to / Good at writing / Friendly on rate limits / Constantly surprising at just how much it is capable of."* 更关键的是他另一条：*"Right now one lab has the best model and another has the best harness."*

**为什么值得关注**：最优组合现在是跨厂商的——模型选一家的，harness 可能是另一家的。这直接决定自研引擎的底座选型和 harness 独立演进的必要性。

### 7. OpenAI：DevDay 下周二，Thibault Sottiaux 称「我们最野心的一轮 sprint」，并把新东西归功于 Astra
**来源**：@thsottiaux（Codex & ChatGPT @OpenAI）｜ https://x.com/thsottiaux/status/2102996313780736363（3159 赞）

原话：*"Can't wait for DevDay next Tuesday. Some really fun stuff, but also many many things that should change the way you work. It's been our most ambitious sprint and Astra has really made new things possible in such short amounts of time."*

另一条（4009 赞）讲语音：*"I've gotten so used to just call ChatGPT and talk about all the work, check on emails, do some coding, manage my calendar and it works across the full ecosystem of plugins, including 3P developed plugins."*

Peter Steinberger（OpenClaw）追加一句：*"Astra is crushing it."*

**为什么值得关注**：「Astra」在一个内部人口中反复出现但尚未正式命名，DevDay 值得盯。

### 8. Claude Marketplace 上线
**来源**：@claudeai ｜ https://x.com/claudeai/status/2102840851538080172（4249 赞）

Claude 内可直接发现 tools / agents / expert partners：加 Slack、Notion 这类 connector；从 Cursor、CrowdStrike 买 agent 和产品；通过 Accenture、Deloitte 这类服务伙伴扩展。开发者可把自己的 tool / agent / service 挂上去：https://x.com/claudeai/status/2102840855258452037

**为什么值得关注**：模型厂商开始抢 agent/tool 的分发渠道，而不只是卖 token。

### 9. Google：更多 app 接入 Gemini
**来源**：Josh Woodward（VP @Google / GeminiApp）｜ https://x.com/joshwoodward/status/2102800209894056351（366 赞）——*"More of your favorite apps are coming to Gemini! Which ones do you want next?"*

---

## 三、builder 观点：社区在讨论什么

### 10. Garry Tan（YC 总裁）：startup 获客的两个新趋势同时发生
**来源**：@garrytan ｜ https://x.com/garrytan/status/2102955139875397806（434 赞）
原话极简：*"Make software agents want｜Use agents to make people want software"*——即「让软件被 agent 想要」和「用 agent 让人想要软件」两条路。他另一条称 *"Muse is very impressive"*。

### 11. Madhu Guru（Meta AI Sr Director，前 Google Gemini/Veo 负责人）公开反驳 Ben Thompson
**来源**：@realmadhuguru ｜ https://x.com/realmadhuguru/status/2102777931764498536
原话：*"Consumers don't have one relationship with 'doing things'… Browsing clothes can be entertainment (for some). But hiring a roofer is miserable (for most)."* 他把「agent 会消灭浏览式消费」的论断类比成 2000 年代初的 *"Why would I buy clothes online? I need to try them on."* 结论：*"The latent demand for agents that remove this friction for consumers is immense."*

### 12. Ryo Lu（Cursor 设计师）的反生产力崇拜长文 —— 本期社区共鸣最强的一条
**来源**：@ryolu_ ｜ https://x.com/ryolu_/status/2102933485795369213（1087 赞 / 165 转发）
原话节选：*"ship faster, merge more, manage more agents, compress every loop… but what is the point of endless production if there is no time left to think deeply?"*；*"the danger is not that ai makes us lazy — the danger is that ai makes us endlessly busy. that it gives us infinite production before we have found intention, infinite execution before we have developed taste, infinite motion before we have learned how to be still."* 落点：*"maybe the real frontier is not more speed, maybe it is discernment — knowing what not to make."*

**为什么值得关注**：1087 赞 + 165 转发说明这种「做得更多 ≠ 更值钱」的情绪在 builder 圈已经是主流声音，不只是圈外批评。

### 13. Aaron Levie（Box CEO）转引电影业判断：AI 降低门槛是扩张而非替代
**来源**：@levie ｜ https://x.com/levie/status/2102934874470617303
引用的原话：*"As the barriers and the costs come down, more films will get made, not fewer… Every time storytelling has met a genuine technological shift, from synchronized sound to color to computer animation, it has redefined the boundaries of the medium and grown larger in the process."* 他的补充是：媒介和技术会变，但**对 creative skills 和 taste 的底层需求不会消失**，只是更多人能用上这些能力。

### 14. Thariq（Claude Code）：开始公开「我们怎么干活」的可复现细节
**来源**：@trq212 ｜ https://x.com/trq212/status/2102857025206255902（2289 赞）／ https://x.com/trq212/status/2102870353781641416（1265 赞）
他们在试一种新 post 类型：把具体 prompt 和技术细节公开到别人能复现。另一条自嘲很实：*"the post: 'Claude one-shot this' ｜ the prompt: 10k characters with good takes plus skills, examples and API keys"*——所谓「一次成型」背后是一万字符的 prompt 加技能、示例和 API key。

### 15. Dan Shipper（Every CEO）：让 agent 策划一整个线下活动
**来源**：@danshipper ｜ https://x.com/danshipper/status/2102826854357016793
Every 的 agent 包办了 9 月 meetup 的全流程——从餐饮菜单到来宾名单，然后在布鲁克林的 brownstone 现场让人打分。*"tomorrow at 6pm we find out if an ai agent can throw a good party."*

---

**本期一句话**：Agent 工程侧出现了清晰的收敛信号——**Anthropic 和 Vercel 在同一天从两个方向给出同一答案：把 harness / hands / session 与存储彻底解耦**，Anthropic 还顺手把「人肉审批已经失效、唯一可靠防线是环境隔离」讲透了；产品侧 Opus 5.5 成为 builder 事实默认，而「最好的模型和最好的 harness 分属两家」这一点，正在把 harness 独立演进从选项变成必需。
