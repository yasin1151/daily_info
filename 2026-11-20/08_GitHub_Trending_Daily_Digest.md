
**GitHub Trending 日报 · 2026-11-20**
今日榜单 16 个项目中，12 个与 AI 相关。最抢眼的是「Agent Skills」集中上榜：**obra/superpowers、Claude-BugHunter、last30days-skill、diagram-design、stitch-skills** 五个同类项目同时进榜。这说明竞争重点已从比拼 prompt 转向比拼**可被 agent 自动触发、可分发的方法论层**。

---

**1. obra/superpowers — 给 coding agent 装一套软件工程方法论**
Shell｜★322,045｜今日 +2,029
它的流程是：agent 不再是看到需求就直接写代码，而是先和你一起提炼 spec，再写一份「让没品味、没上下文、不爱测试的初级工程师也能照做」的实施计划，接着跑严格的红绿 TDD，最后交给子代理并行开发、自查、继续做。已适配 Claude Code、Codex CLI、Cursor、Gemini CLI、Copilot CLI、Devin、Factory Droid、Qwen Code，甚至 Hermes Agent。
值得关注：它把「你的 agent 会不会按流程做事」变成可安装的软件包，28,626 个 fork 也说明大量团队把它当底座做二次开发。README 里还挂了商业支持入口，是少数已开始商业化的 skill 框架。

**2. elementalsouls/Claude-BugHunter — 红队 SOP 变成 skill 包**
Python｜★12,463｜今日 +1,353
包含 83 个 skills、15 个 slash 命令、681 条公开漏洞报告提炼出的检测模式，覆盖 24 类漏洞；另外有 M365/Entra、Okta、vCenter、SSL-VPN、SharePoint 的企业攻击链和 Burp MCP 集成。它的定位很明确：装完让 Claude Code「像一个资深漏洞猎人那样思考」，并遵守 scope，证据做 PII 脱敏。
值得关注：安全是 skill 化最容易变现的垂直领域，因为它卖的是「老手经验」，并非提示词技巧；这也是它能在一天内增加 1,353 star 的原因。

**3. mvanhorn/last30days-skill — 跨平台 30 天调研 agent**
Python｜★70,771｜今日 +952
一个 skill，输入任意话题，它会去 Reddit、X、YouTube、HN、Polymarket 和网页上抓最近 30 天的一手发言，再综合成有出处的摘要。
值得关注：这正是我们每天手工做舆情那套流程的产品化版本，Polymarket 的加入说明它在把「舆论」和「真金白银的预期」交叉验证。做竞品/选题调研可以直接拿来当对照。

**4. HKUDS/CLI-Anything — 把任何软件变成 agent 能调的 CLI**
Python｜★60,528｜今日 +899
港大数据智能实验室出品，一句 `cli-hub install <name>` 就能给软件装上 agent 可调用的命令行外壳，配套 2,461 个通过测试、18 个真实 app demo（CAD、3D 场景、图表、游戏、字幕）、arXiv 技术报告，Apache 2.0。
值得关注：它的口号是「今天的软件服务人，明天的用户是 agent」。这是 agent-native 接口标准的争夺，和 MCP 走的是两条路（工具协议 vs 命令行包装），谁能成为事实标准还早。

**5. firecrawl/firecrawl — agent 的搜索与抓取底座**
TypeScript｜★204,161｜今日 +795
一个 API 覆盖搜索、爬取和 550+ 数据源，定位是「让 agent 更聪明的知识基础设施」。
值得关注：20 万 star 还天天在榜，说明它已是刚需而非话题项目。任何自建 RAG / 调研 agent 的人最后都会遇到它。

**6. cathrynlavery/diagram-design — 拒绝 Mermaid 的图表生成**
HTML｜★68,609｜今日 +402
45 种图表类型，输出自包含 HTML + SVG，适配 Claude Code、Codex、Copilot、Cursor 等十余种 agent。README 明写「No shadows. No Mermaid slop.」，走出版级排版路线。
值得关注：Mermaid 生成的图一直有「一看就是 AI 画的」问题，这个项目赌的是审美差异化，一天 402 star 算验证了痛点。

---

**其余上榜（AI 相关）**
- **cursor/plugins** ★17,540（+383）：Cursor 官方插件规范和官方插件集。编辑器公司开始建第三方生态，这步棋和当年 VS Code 一样。
- **google-labs-code/stitch-skills** ★10,702（+303）：谷歌官方 Agent Skills 库，配 Stitch MCP，明确遵循 Agent Skills 开放标准。大厂来定标准了。
- **jingyaogong/minimind** ★66,833（+301）：两小时从零训出 64M 小模型，教学向常青树，适合想做预训练练手的人。
- **openvinotoolkit/openvino** ★11,552（+246）：Intel 推理优化与部署工具链，端侧部署仍在稳步推进。
- **zhouxiaoka/autoclip** ★11,187（+110）：中文开源 AI 视频剪辑桌面工具，一条链接把播客/访谈/课程长视频切成短视频，自动出字幕、封面、发布文案，适配抖音、小红书、TikTok。
- **Tracer-Cloud/opensre** ★13,105（+25）：面向 CI/CD 可靠性的开源 agent，SRE 场景里少见的正经项目。

**未入选**：nginx（+66）、AFFiNE（知识库，+170）、Ghost-Downloader-3（下载器，+449）、app-store-compliance（上架合规手册，+426）——不属于 AI/Agent 方向。

---

**一个观察**
skills 赛道今天占了榜单三分之一，同质化风险已经出现：同样是「装一堆 skill 让 agent 会做事」，superpowers 卖方法论、BugHunter 卖垂直经验、stitch-skills 卖大厂标准、last30days 卖现成工作流。接下来拼的不是 skill 数量，而是谁能在 agent 自动触发时**判断得准、不乱加载**。这也是我们自己在维护 skill 库时最难的部分。

已标记 5 条未读为已读。
