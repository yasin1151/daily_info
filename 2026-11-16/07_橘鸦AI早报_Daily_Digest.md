
**橘鸦AI早报 · 2026-11-15 期摘要**
本期 8 条，核心看点是「成本与安全」：谷歌免费额度缩水、Anthropic 用量成本数据、两起安全事故通报。

---

**一、开发生态**

**1. Grok Bot 上线多项 harness 优化，订阅用量提升约 7%**
团队本周完成多轮 harness 优化，官方称订阅方案可用量预计增加约 7%，日常运行场景最多可提升约 15%，后续还有更多优化在路上。有用户已能感知提升，也有用户反映自己账号上没变化——实际增益可能因使用形态而异。
影响：对重度用户是直接降本；但官方口径是「预计」，落地程度待观察。
https://x.com/mattyp/status/2121624592326480311

**2. Claude Code 桌面版支持 mods 自定义主题**
可通过 mods 调整配色、加动画背景，也能直接告诉 Claude 想要什么外观让它生成，官方另提供 theme-examples 插件快速上手。目前仅在桌面端本地会话生效，云端会话支持待上线。
影响：纯体验层功能，对工作流无实质改变，但说明 Anthropic 开始认真做桌面端产品化。
https://code.claude.com/docs/en/plugins/mods/interface

**3. 谷歌 300 美元赠金不再覆盖 Gemini 调用费用（11/16 起注册生效）**
2026 年 11 月 16 日或之后注册免费试用 / 升级付费结算账号的用户，300 美元迎新赠金无法再支付 Gemini Platform（含 Vertex AI）、AI Studio 中的 Gemini API 以及生成式 AI 合作伙伴的 MaaS 费用，只能用于其他 GCP 产品。赠金 90 天有效。社区指出「排除 Gemini Platform」是本次新增条款。
影响：这是本期最有实操价值的一条——**今天正好是规则生效日**。靠赠金白嫖 Gemini 试点的路基本封死，评估阶段建议改用 AI Studio 免费层或竞争对手额度。
https://docs.cloud.google.com/free/docs/free-cloud-features

**4. Cloudflare 开源 Kitesurf 浏览器，Apache 2.0**
专为 AI agent 设计的浏览器，agent 用它加载和操作网页，支持 CDP 协议可接 Puppeteer，Cloudflare 测试称截图与内容提取的 CPU / 内存消耗低于 Chromium。可本地改代码，也可部署到自己账户（自行部署需 Workers Paid）。
影响：agent 浏览层出现了一个「轻量 + 可自托管」选项，对标 Playwright/Chromium 的资源开销痛点，值得在抓取类 agent 上试。
https://blog.cloudflare.com/kitesurf-open-source/ ｜ https://github.com/cloudflare/kitesurf

---

**二、技术与洞察**

**5. Claude 发布 always-on agents 搭建指南（五模块架构）**
架构拆为 event inbox、timers、memory、permissions、outbox 五块：agent 大部分时间休眠，收到事件后跑一次 run 并落盘状态。官方给的关键数据是——在长周期编码基准上，**Opus 5.5 每个已解决任务的成本比 Opus 5 低 78%，典型负载低 40%**，这是他们主张「常驻 agent 现在才划算」的依据。
影响：这是目前关于「后台常驻 agent」最工程化的一份公开设计参考，做定时/事件驱动 agent 的可以直接对照检查自己的缺项（尤其是 permissions 和 outbox 这两块多数人没做）。
https://claude.com/resources/articles/building-always-on-agents

**6. Anthropic 发布 10 项安全评测建议**
核心观点：衡量安全不能只看拒绝率，要看「恰当回应率」——整段对话全程恰当才算通过；在自杀自残等场景，单纯拒绝本身就是失败。方法上要求评测在断网沙箱内运行并实时监控，多轮复杂评测样本量 ≥100 例、单轮简单评测 ≥1000 例，并写明模型版本、提示词、评分器以便复现。文中举例：Claude Fable 5.1 在 API 与 claude.ai 两种配置下，多轮安全评测恰当回应率**最高相差 34 个百分点**。
影响：34 个百分点这个数字很有杀伤力——它说明「同一模型同一评测」的结论可能被部署配置完全改写，引用任何安全 benchmark 时都必须看配置。
https://anthropic.com/research/building-strong-safety-evaluations

---

**三、行业动态**

**7. FBI 警告：开源 AI 渗透工具 ARTEX 已被武器化**
框架自今年 8 月起被多方用于自动化入侵金融、政府、国防、能源等行业，部分案例**从锁定目标到取得云端高权限不到 3 小时**。韩国一家金融机构约 6.7 万人个人信息被窃；攻击者还用 ConnectWise 云备份的被盗凭据向 2250+ 个 Microsoft 365 租户尝试登录。作者 Autumn-27 已于 7 月发布后下架并转闭源，但截至 11 月初仍有 **1600+ 个可公开访问的控制界面**在跑，另有商业版 ARTEX PRO 在流传。
影响：AI 自动化攻击的「时间成本」已经被压缩到小时级，防守方的检测窗口同步缩短；开源下架对已扩散的衍生版本几乎无效。
（原文未附外链，建议直接检索 FBI 官方 alert 获取 IOCs）

**8. Cursor 披露安全事件：Fireworks 密钥泄露导致部分数据外泄**
攻击者用泄露的 Fireworks 访问密钥复制了部分 agent 链路追踪数据，少量含未脱敏凭据，API 凭证受影响的客户不到 0.01%。同时借机入侵 Cursor 使用的部分 SaaS 工具。10 月 29 日，恶意的 Anthropic.claude-code 2.1.312 / 2.1.313 版本被注入扩展市场分发缓存，**最多 5,000 名用户**可能收到恶意构建，约 11 小时后下架。最后一次攻击活动 11 月 1 日被拦截，凭证已全部轮换、市场已重建。
影响：这是典型的供应链（SaaS 工具 + 扩展市场）双重失守。近期装过 Claude Code 扩展的，值得核对一下版本号。
https://cursor.com/blog/security-incident-update

---

**一句话结论**：本期没有模型发布，全是「钱」和「安全」——谷歌收紧免费额度、Anthropic 用 78% 成本降幅论证常驻 agent 的经济性、两起安全事故显示 AI 工具链正在成为主攻面。已标记本期为已读。
