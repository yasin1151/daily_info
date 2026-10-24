
AI Builders Digest：2026-10-25

## X / 推特

**OpenAI Codex 负责人 Thibault Sottiaux**：Codex CLI 一周内连续更新。新增可复用的 prompt preset、会话内直接切模型和权限、企业版 MCP 登录，修好了长会话恢复失败和 Windows 企业代理认证。更关键的一条是“对话中途改 reasoning 不再让缓存失效”。他说 DevDay 之后 CLI 用量涨了 2 倍。他还有一句话在圈内传得很广：“有工具和成为工具之间区别很微妙，别把自己建造成工具。”
为什么重要：缓存不失效、模型权限行内可切，直接决定 coding agent 能否长时间跑昂贵任务而不烧钱。
https://x.com/thsottiaux/status/2113770862860222611
https://x.com/thsottiaux/status/2113770573994299544
https://x.com/thsottiaux/status/2113838156193894447

**前 Claude Code 团队成员 Thariq**：宣布离开 Anthropic，做了两年多 Claude Code，“看着它长到超出我想象的规模”。他强调自己相信“race to the top”，说同事是他见过最有才华也最 earnest 的一群人，会先休息一阵再开始新的事，并把社区引荐给 addyosmani、bcherny 等人。这条 1 万赞。
为什么重要：Claude Code 的核心早期成员离开，是本周 coding agent 赛道最大的组织变动信号。
https://x.com/trq212/status/2113844051938054167

**Replit CEO Amjad Masad**：收购 Chroma 团队（Jeff 团队）。他的说法是，Chroma“在 RAG 还不叫 RAG 的时候就在做了”，加入 Replit 是为了解决 AI 最难的问题之一：给 agent 足够的 context 和 memory 去干真活，称这是走向“self-driving company”的一大步。同日还宣布 Replit for Government，前 AWS 公共部门负责人 Michael Greenwald 加入。
为什么重要：agent 的瓶颈从“会写代码”转向“记得住、找得到上下文”，向量库团队被应用层公司收编是个明确趋势。
https://x.com/amasad/status/2113736007111827606
https://x.com/amasad/status/2113676717105787192

**Vercel CEO Guillermo Rauch**：点评 OpenAI 发现的 agent 侧信道攻击。他说 agent 能在云端玩“通灵板”：同一个物理机上两个 agent，一个通过 CPU cache 制造噪声，另一个靠给自己计时就能探测到对方。这类共享宿主机的时序攻击 2015 年就知道了，一直没有完整解法。唯一“彻底”的方案是每个 agent 独占硬件，经济上不可行。Vercel Sandbox 已上了所有实际可行的缓解措施，外加持续监控和红队。
为什么重要：agent 沙箱的多租户隔离正在从“工程细节”变成安全底线，做自研引擎跑多 agent 必须正视。
https://x.com/rauchg/status/2113759533801877920

**Box CEO Aaron Levie**：判断“agent swarm 做网络防御”即将成为 AI 最大的品类之一。理由是安全领域“算力投入直接等于价值产出”：agent 可以审代码和基础设施、穷举风险组合、处理海量数据，把人类一直没时间做的测试铺开做。他的原话是安全最适合 swarm，因为“有大量测试是人们永远排不上期的”。
为什么重要：swarm 找到了第一个算力换钱效率极高的落地场景，比通用 agent 更有商业确定性。
https://x.com/levie/status/2113738768645808277

**Claude 官方账号**：放出 Claude Duet 在安全、隐私、防护上的深入说明。
为什么重要：Duet 是本周 Anthropic 的产品新变量，官方主动先讲安全叙事而非能力。
https://x.com/claudeai/status/2113736176737845353

**SPC 普通合伙人 Aditya Agarwal**：提出 AI 最大的进步来自“把很多问题合在一起解”，而不是为每个任务训练专用系统。他引用 Sergey Levine 在机器人上的同一个原则：“把问题做大”。
为什么重要：这是通用模型路线对专用小模型路线的正面表态，和自研引擎该做“一个通用底座还是 N 个专用模块”直接相关。
https://x.com/adityaag/status/2113666947766169868

**Every CEO Dan Shipper**：AI 团队最好的配置只有两种人，pirates 和 architects。海盗负责破局，架构师负责把它搭成能长期运转的东西。
https://x.com/danshipper/status/2113693510629281895

## 播客

**No Priors：Democratizing Security for the Agentic Web，嘉宾 Cloudflare CTO Dane Knecht**
（该 feed 只提供频道链接，无单集地址）
https://www.youtube.com/@NoPriorsPodcast

这期信息密度很高，核心是“AI 既是安全灾难的制造者，也是唯一能追上它的工具”。

- **漏洞从“一年一次 Log4j”变成“一周一次”**。他说过去 3 到 6 个月，被上报的漏洞数量指数级上升，严重程度和 Log4j 同级，但频率完全不是一回事。很多没公开。他预计未来 18 个月内，超过 50% 的工程时间会花在安全上。
- **攻击者不再是国家行为体**。最近几个大漏洞是高中生干的，他把这类人叫 agent kitties：以前打 CTF，现在把 agent 指向一个目标猛挖，还有 bug bounty 现金回报。等于把国家级能力下放给了所有人。
- **最吓人的一个例子**：保护整个 TLS / WebPKI 的一把密钥，种子是数字 4。他顺带提到上周 OpenAI 找到了 2000 年发布的 NIST 曲线的种子。他的判断是模型本身只是一半，“harness 和人类怎么用 frontier model 找 exploit”才是另一半进步。
- **他不认同 air gap 末日论**。理由是过去 5 到 10 年从“城堡护城河”转向 zero trust，让很多公司处在更好的位置。但代价是安全预算要在 18 个月内全部前置，之后生产力才会回补。
- **AI 目前没有让软件更安全**。原话是“早期 AI 非常 verbose，它喜欢制造复杂度”，而减少攻击面恰恰要求做减法。所以人类判断力还在关键路径上。
- **Cloudflare 的做法可以抄**：内部有一份叫 Codex 的文档，把一堆 RFC 沉淀成“在 Cloudflare 怎么写安全软件”的十条戒律，agent 在 review 每个环节都能读到并执行。上面 agent 大量写代码，下游 human 做性能和安全对抗性 review。红队从 1 个扩到 4 到 5 个，逻辑是“别指望流程先变好，先让漏洞发现量爆炸，工程师自然会去自动化”。
- **互联网要分成人和机器两张网**。现在是 messy middle：agent 在爬为人设计的网页，翻译层白烧 token。网站其实知道自己内容的 CPM 是多少，理想状态是 agent 判断值不值得读、按 CPM 付费。Cloudflare 已上线 content monetization gateway（带 agent 钱包和稳定币）、支持 Stripe 的 x402 协议，以及和 OpenAI 合作的 signals 项目，让 agent 主动发现新内容而不是全站重爬。他也提到 Amazon 已经直接禁止 agent 代购，这是各方在抢谈判筹码。
- **Cloudflare OS**：内部 AI 平台，定位是 reference architecture，让非工程部门自己搭工具，安全默认内建。实际用得最多的是 GTM 和 G&A，不是工程团队。
- **token 预算哲学值得直接借鉴**：不要排行榜，不考核用量，只考核产出。但设三档提醒：一天 300 次发邮件提醒本人，500 次抄送经理，1000 次上报 VP。他说绝大多数人根本不知道自己用了这么多，收到提醒反而高兴。真正的方向是模型智能路由，“让人来决定每个任务用哪个模型是件蠢事”。典型编排是：规划和评审用 frontier model，执行段落交给开源模型。
- **组织上最反直觉的一招**：5000 人的公司今年招了 1000 个实习生，因为上一批 200 个实习生是第一批 AI native，带他们的经理反而更快接受 AI。早期还有个 agents@ 邮箱，员工把 job to be done 发过去就回一份 skill file，他一度以为是全自动 AI，其实是一群实习生在写。

为什么重要：这期几乎是“agent 时代基础设施该怎么搭”的一手清单，涉及安全预算前置、agent review 流水线、agent 专属支付轨道、token 治理和模型路由，跟自研引擎和 Agent 工具链的每一项都正面对上。

Generated through the Follow Builders skill: https://github.com/zarazhangrui/follow-builders
