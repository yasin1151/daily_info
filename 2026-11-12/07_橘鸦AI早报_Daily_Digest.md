
# 橘鸦AI早报 2026-11-11 摘要

**本期主线：Gemini 4 Carbon 全面开放，Anthropic 一边推进办公套件、一边准备上市，Agent 基础设施（多 agent 协作、内网 MCP）开始快速完善。**

---

**1. 谷歌正式开放 Gemini 4 Carbon，定位"最强模型"**
本次开放面向网络安全、长周期智能体任务和复杂编程、科研。API 已向付费开发者和企业开放，并陆续推送给 Google AI Ultra 订阅用户，同时已接入 Cursor、GitHub Copilot、OpenRouter。模型统一支持 1048576 token 上下文，并支持文本、图像、视频、音频、PDF 输入和低、中、高三档推理强度。首发价每百万 token 输入 2 美元、输出 10 美元（至 11 月 30 日），之后翻倍到 4/20 美元。
**影响**：这是目前唯一把 1M 上下文、三档推理和安全能力打包销售的旗舰，价格翻倍的时间点值得记住。
https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-carbon-now-available/

**2. Google Antigravity 推出 `/swarm`，一条 prompt 拉起一支 agent 团队**
跑一次命令，当前对话就变成 coordinator，任务会被拆成互不冲突的部分，然后启动多个有命名的 worker 并行开发；通常 2 到 4 个 worker 配 1 个 verifier 负责跑测试、审代码。各成员在共享留言板上沟通，空闲时会挂起、不消耗 token。目前 App 和 CLI 都已上线。
**影响**：这是 "agent 团队" 第一次由 IDE 级产品原生提供，不再是自己拼脚本。但 Google 明确警告，并行多 agent 消耗配额远快于普通聊天。
https://antigravity.google/docs/swarm

**3. Anthropic 把 Claude 推成办公套件：白板、表格、数据看板**
Claude Whiteboards 能把讨论整理成带负责人和日期的计划；Sheets 可按提示生成多标签页、公式和下拉菜单，修改会标注，还能导出 Excel/CSV；Claude Data 可连数据仓库或 CRM，生成仪表盘和"数据故事"。交互式连接器也升级了，能在对话旁边直接打开 Adobe、Atlassian、Box 等应用。
**另**：因近期修复了几个导致额度消耗超预期的问题，Anthropic 向 Pro/Max/Ultra/Team 各发放一次**免费完整额度重置**，Claude Code 同样适用（需在 12 月 10 日前领取，终端和 IDE 内没有按钮，得去网页版 Settings → Usage）。
https://claude.com/resources/articles/sheets-whiteboards-data

**4. MiniMax 发布 H3-Image 并开放权重**
支持文字生图、图像编辑、最多 16 张参考图，输出最高 4096×4096（约 1600 万像素），官网称 4K 出图 10 秒内。权重已在 Hugging Face 放出，同时接入开放平台、MiniMax Code、海螺 AI。首周 1600 万像素及以上请求五折。
**影响**：开源阵营又多了一个可以直接商用的 4K 图像模型，参考图数量是它的差异点。
https://huggingface.co/MiniMaxAI/MiniMax-H3-Image

**5. Gemini Robotics 2.5：真产线上的 96% 成功率**
视觉-语言-动作（VLA）模型，在超过 200 项任务中测试过。与 Apptronik、Mercedes-Benz 合作的概念验证里，Apollo 2 人形机器人在匈牙利和德国的在用汽车产线上分拣金属零件，成功率 96%，比此前基线高 30%~100%，速度快 20%~30%。安全方面内置危险识别和防越狱机制，机器人周围有障碍物时的安全任务完成率提升 33%，人员周边提升 43%。
**影响**：机器人不再只是演示视频，"在用产线"这四个字比任何 benchmark 都有分量。
https://deepmind.google/blog/gemini-robotics-2-5-accelerates-real-world-physical-intelligence/

**6. DeepMind 用 AI 干成了两件安全硬活**
一是 AlphaProof Code 用约四周、Gemini Carbon 驱动的 agent 生成约 650 万行 Lean 证明，对 Signal 协议参考实现 libsignal 完成机器码级形式化验证，约 1% 需人工复核，未发现新漏洞；官方称这是首次把协议级安全保证和广泛部署的未修改代码连起来。二是 AI 辅助密码分析：两个 agent 在不到 4 天内复现了此前需 5 个月的 1024 位 RSA 签名实验，CPU 计算量降约 72%；新的 Fan Factories 算法把后续目标的理论成本降到约 1/30，特定场景可降到约 1/1600。
**影响**：1024 位 RSA 的门槛被重新估低了，2048 位及以上目前不受影响——但这条线的推进速度比预期快得多。
https://deepmind.google/blog/introducing-alphaproof-code

**7. Anthropic 启动 IPO 路演，拟发 8.25 亿股**
预期发行价 70~78 美元/股，Anthropic 自己发售约 8.01 亿股，其余由现有股东出售，申请以 "ANT" 为代码在 Nasdaq Global Select Market 上市。注册声明已提交但尚未生效。
**影响**：按区间中值粗算，这是千亿美元量级的发行。AI 实验室的估值锚点要从一级市场移到二级市场了。
（本期暂无官方链接，以 SEC 文件为准）

**8. OpenRouter 正式并入 Stripe**
8 月公布的收购完成。Stripe CEO Patrick Collison 称 OpenRouter 每周 token 用量比宣布收购时增长约 125%，OpenRouter 自称有超 1000 万开发者和公司在用，并入后"中立承诺不变，模型按质量、可靠性和价格竞争"。
**影响**：模型的"支付+路由"层被 Stripe 吃下，token 计费等于接进了 Stripe 的账单体系——这对做 agent 产品的团队是基础设施级别的变化。
https://x.com/stripe/status/2120240651778355306

**9. 安全公司发现 3.5 万个 Grok 应用无需登录就能打开**
Claroc Research 收集到 43,551 个 Grok Build 模式生成的应用地址，37,571 个仍在线，其中 35,578 个无需登录即可访问，估计约 650~800 个含隐私数据——研究人员看到的实例包括重症患者化验单和明文密码工时表。测试发现付费账户的发布面板默认选中"任何拿到链接的人"。SpaceXSI 撤下了自家员工创建的 24 个应用，其他用户和组织的公开应用未移除。
**影响**：AI 一句话建站把"默认公开"的成本降到了零。任何人用 Build 模式做过东西，都该去查一遍分享设置。
https://blog.claroc.io/ghostshares-grok-build-apps/

**10. ChatGPT Business 订阅可以在第三方工具里用了（含 Hermes）**
通过 Sign in with ChatGPT，可在 Notion、v0、ampcode、kilocode、Warp、Nous Research 的 Hermes、openclaw、opencode 等工具中直接使用 Business 订阅。管理员可在后台按工具开关权限、按成员额度百分比设限额。用量计入原有订阅限额，连接应用不新增额度，也不会让应用访问你的对话和记忆。
**影响**：企业版订阅的使用范围从"chatgpt.com"扩展到整个 agent 工具生态，对已经在用 Hermes 的团队来说，报销路径变简单了。
https://x.com/OpenAIDevs/status/2120212596850663712

---

**其他值得一提（未展开）**
- **Grok 4.8 完成预训练**：马斯克称 SpaceXSI 已弃用 JAX/SGLang，用 C/C++（含少量汇编）从零重写整个 RL 和推理堆栈，衍生自 Starlink 的工程成果；Grok 4.8 正处 RL 阶段，本周向 Bot 用户软发布，"与 4.7 毫无相似之处"。
- **Tailscale OAuth apps 正式可用**：agent 以授权用户身份加入私有 tailnet，Grok Bot 已接入，可访问内网私有 MCP 服务器，无需暴露公网。这是 agent 接触内部系统的正确做法。
- **Modern Web Guidance 1.0**：Chrome、Firefox、Edge、MDN 四方共维护，203 条指南覆盖 250 项 Web 能力并嵌 Baseline 数据，专门给 AI 编程 agent 用；附带 legacy-scan 工具扫旧模式。
- **ElevenLabs Scribe v3 / v3 Live**：102 种语言词错误率比 v2 降 27%，实时版首次支持区分说话人（语义词错误率降 43%），轮次检测改为看整段对话而不只是静音。
- **Amazon 开源 Mitra-v2**：纯合成数据预训练的表格基础模型，TabArena 单模型排名第一，Apache-2.0。
- **Hugging Face 开发者破 2000 万**，Hub 托管资源达 300PB，上周单周新增 9PB；10 月 DAU/MAU/收入均创历史新高。
- **澳大利亚接受 OpenAI 事件审查全部 18 条建议**，6 项强制安全义务将写入 AI 标准立法，拟设可高额处罚的 AI 安全监管机构。

---
已标记本期为已读（article 7321），该源暂无未读。
