
## GitHub Trending 日报 · 今日热门 AI 项目

今日 Trending 共 16 个仓库，筛出 10 个与 AI / Agent / LLM / 开发工具相关，按今日新增 Stars 排序。

---

**1. God's Eye View —— 浏览器里的"间谍卫星"模拟器**
把公开数据源（航班、船舶、卫星、地震、交通、公共摄像头）实时叠在一张照片级 3D 地球上，内置实时 AI 语音 Agent 支持免手操作。作者称八月曾登顶 GitHub Trending 日榜+周榜，YouTube 系列 500 万+ 播放。
为什么值得关注：它把"公开数据 + 实时 AI 语音交互"做到了消费级体验，是 OSINT 类工具产品化的样板。
Stars：29.8k（今日 +2,265，今日第一）
https://github.com/bilawalsidhu/gods-eye-view

**2. DeskcommCRM —— 开源的 AI 销售 CRM（WhatsApp 原生）**
自托管 CRM，内置 AI agent 负责接待、筛选、成交，走 WhatsApp（WAHA 网关），MCP-ready、多租户。对标的 Kommo / Octadesk / Intercom 全是付费 SaaS。
为什么值得关注：巴西团队做的开源替代品，把"AI agent 卖东西"落进具体行业流程，对做对话式 Agent 落地的人有直接参考价值。
Stars：1,789（今日 +505）
https://github.com/melgarafael/DeskcommCRM

**3. CloddsBot —— 跑在自己电脑上的 AI 交易终端**
基于 Claude 的自主交易 agent，118+ 交易策略、鲸鱼跟踪、套利检测，覆盖 10 个预测市场 + 7 个期货所，以及 Solana（Jupiter/Pump.fun/Raydium）和 EVM 链（Uniswap V3/1inch），可通过 21 个消息平台对话下单。自称 12 天黑客松产物。
为什么值得关注：agent 直接管钱是最激进的应用形态，值得看它的风控与权限设计；也提醒一句，这类项目风险极高，仅适合研究。
Stars：2,487（今日 +377）
https://github.com/alsk1992/CloddsBot

**4. system_prompts_leaks —— 各家大模型系统提示词泄露合集**
逐字收录 ChatGPT、Claude、Gemini、Grok 等产品的系统提示词并持续更新：最新包括 Claude Code headless（Fable 5.1）、Codex GPT-6-Astra、Grok 4.6、Gemini 3.7 Flash、Meta 的 Muse Code 等。《华盛顿邮报》曾基于此仓库做交互式报道。
为什么值得关注：想知道前沿模型"被怎么要求"、各家产品策略差异，这是最直接的原始材料。
Stars：65.4k（今日 +357）
https://github.com/asgeirtj/system_prompts_leaks

**5. MathModelAgent —— 自动打数学建模比赛的 Agent**
中文项目。多 agent 分工（建模手 / 代码手 / 论文手）+ 多模型各司其职，自动分析题目、建模、写代码跑结果、自我纠错，最后产出一份排版完整、可直接提交的论文；支持 local Jupyter / E2B / Daytona code interpreter。已有签名公证的 macOS 桌面版，内置 Claude Code 与全套 skills。
为什么值得关注：美赛/国赛级别的刚需场景，完整演示了"多 agent + code interpreter + 论文级输出"的链路。
Stars：5,122（今日 +264）
https://github.com/jihe520/MathModelAgent

**6. awesome-llm-apps —— 100+ 开源 AI Agent / RAG 应用合集**
每个模板都能直接 clone 跑：AI 旅行助手、保险理赔 agent 团队、欺诈调查 agent，以及 "Project Graveyard" 这类可直接 `npx skills add` 装进 coding agent 的 skills。Apache-2.0 可商用，兼容 Claude/GPT/Gemini/DeepSeek/Qwen 等。
为什么值得关注：想快速搭 demo 或找 skill 模板，这是最省事的起点（每周更新）。
Stars：137.6k（今日 +237）
https://github.com/Shubhamsaboo/awesome-llm-apps

**7. YuE2 —— 先"写谱"再唱歌的音乐生成模型**
符号 + 音频统一：先产出旋律与和弦规划，再渲染成带人声和伴奏的完整歌曲，因此谱面可被人或 agent 读取和修改，支持 zero-shot 翻唱与"边聊边改歌"。作者称在 WildSongBench 上对标 Suno v5/v6（best-of-8 拿到 6.9632 SongBench Avg）。
为什么值得关注：开源音乐生成第一次把"可编辑 / white-box"当卖点，对 agent 编排音乐更友好。
Stars：7,270（今日 +193）
https://github.com/multimodal-art-projection/YuE

**8. PentAGI —— 全自主渗透测试 AI Agent**
在隔离 Docker 沙箱内运行，自带 nmap / metasploit / sqlmap 等 20+ 专业工具，具备长期记忆、可选 Neo4j 知识图谱、Grafana/Prometheus 监控，最终输出带利用步骤的漏洞报告。模型侧支持 Ollama/OpenAI/Anthropic/Gemini/DeepSeek/GLM/Kimi/Qwen 等一大票 provider。
为什么值得关注：安全是 agent 自主性最容易翻车的场景，它的沙箱隔离、任务规划与人工监督设计值得借鉴。
Stars：23.4k（今日 +193）
https://github.com/vxcontrol/pentagi

**9. Worktrunk —— 为并行跑 AI Agent 而生的 Git worktree CLI**
把 worktree 当分支一样管理：三条核心命令搞定新建/切换/清理，按分支名寻址、自动计算路径，还有 hooks 自动化本地流程。作者称它已是"最流行的 git worktree 管理器"。
为什么值得关注：同时跑 5-10 个 Claude Code / Codex 最大的痛点就是目录和分支互相踩，这是对口的基建工具。
Stars：7,222（今日 +137）
https://github.com/max-sixty/worktrunk

**10. Claude-Red —— 给 Claude 用的进攻性安全 skills 库**
一套结构化 SKILL.md，把 SQLi、shellcode、EDR 绕过、ADCS 滥用等攻击面方法论按会话触发按需加载进 Claude Skills 系统，声明用于授权红队、漏洞赏金、CTF 与安全研究。
为什么值得关注：它示范了 skills 机制如何沉淀"专家方法论"，同时也提醒 skill 生态的滥用风险。
Stars：3,583（今日 +99）
https://github.com/SnailSploit/Claude-Red

---

其余 trending 为非 AI 项目：OpenFlux（TCP 隧道，1.4k）、Armorpaint（4.9k）、Sonarr（15.9k）、SmartTube（33.2k）、zapret-discord-youtube（33.2k）、iloader（3.1k）。

（已标记 7 条 blogwatcher 未读项为已读；今日 GitHub 网络可达，trending 页面直连抓取成功。）
