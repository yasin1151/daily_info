
# GitHub Trending 今日热门（AI / Agent / 开发工具方向）

扫描时间：2026-09-14 07:35 CST｜Trending 页面共 19 个项目，筛出 AI 相关 13 个，其中 6 个为本次新上榜。

---

## 一、AI Agent / 编码助手生态（今日最热赛道）

**1. colibri — 纯 C 写的 MoE 推理引擎（★29,741，今日 +960）**
在自己已有的硬件上跑前沿 MoE 模型：纯 C 实现、零依赖，专家权重直接从磁盘流式加载。"小引擎跑大模型"的思路，主打零环境依赖和低内存占用。
值得关注：零依赖 C 实现意味着可以塞进任何设备（路由器、老机器、嵌入式），绕开 Python/CUDA 生态的部署包袱，是本地推理"轻量化"路线里最激进的一档。
https://github.com/JustVugg/colibri

**2. system_prompts_leaks — 各家大模型系统提示词泄露合集（★66,001，今日 +727）**
持续更新的系统提示词提取库，覆盖 Anthropic（Claude Fable 5.1、Opus 5、Claude Code）、OpenAI（GPT-6-Astra、Codex）、Google（Gemini 3.8 Flash、3.1 Pro、Antigravity）、xAI（Grok）、Cursor、Kimi 等。
值得关注：想看别人怎么"调教"Agent 行为、怎么写工具调用约束和拒答策略，这是最直接的一手材料，比任何 prompt 教程都实在。
https://github.com/asgeirtj/system_prompts_leaks

**3. pentagi — 全自主渗透测试 Agent 系统（★23,949，今日 +613）**
Go 写的自动化 AI Agent 系统，能独立完成复杂渗透测试任务（侦察、漏洞验证、利用链）。
值得关注：攻击性安全是 Agent 自主性最容易被验证的场景之一，红队方向的产品化竞争已经开始了。
https://github.com/vxcontrol/pentagi

**4. Claude-Red — 面向 Claude Skills 的攻防技能库（★4,113，今日 +507）**
一批结构化 SKILL.md，给 Claude 灌注专家级攻击方法论，从 SQL 注入到 shellcode、EDR 绕过、漏洞开发。
值得关注："技能包"正在被同时武器化。防御方应该把这类仓库当作威胁建模的参考清单来看。
https://github.com/SnailSploit/Claude-Red

**5. agent-skills — AI 编码 Agent 的"安全技能注册表"（★5,628，今日 +215）**
经过验证和校验的技能注册中心，可扩展 Antigravity、Claude Code、Cursor、Copilot 等编码 Agent。
值得关注：正好回应上面的风险——技能包分发需要审核机制，这个项目想做的就是这个中间层。
https://github.com/tech-leads-club/agent-skills

**6. OpenMontage — Agentic 视频生产系统（★58,398，今日 +383）**
号称首个开源 Agent 驱动的视频制作系统：12 条生产流水线、100+ 工具、700+ 技能与制作知识文件，把编码助手直接变成视频工作室。
值得关注：Agent 的能力边界从"写代码"扩到"重资产内容生产"，技能文件规模已经超过工具本身，这是新的组织方式。
https://github.com/calesthio/OpenMontage

**7. OpenResearch — 并行研究 Agent 框架（★2,033，今日 +304）**
Rust 实现，可用任意模型并行跑研究型 Agent。
值得关注：小项目但方向明确——把"多 Agent 并行调研"基础设施化，Rust 选型是为了并发和稳定性。
https://github.com/alphaXiv/OpenResearch

**8. MathModelAgent — 专为数学建模设计的 Agent（★5,337，今日 +268）**
自动完成数学建模全流程，并生成可直接提交的完整论文。
值得关注：中国团队项目，明显瞄准数模竞赛场景。"Agent + 垂直场景交付物"这种组合（这里交付物是论文）比通用 Agent 更易落地。
https://github.com/jihe520/MathModelAgent

---

## 二、开发工具 / 代码质量

**9. open-code-review — 阿里开源的混合架构代码审查工具（★23,460，今日 +438）**
确定性流水线 + LLM Agent 混合架构，能给出精确到行的评论，内置多语言规则集（NPE、线程安全、XSS、SQL 注入），兼容 OpenAI 与 Anthropic。
值得关注：阿里内部大规模验证过。用规则引擎兜底、LLM 补语义，是目前工程界对"AI 代码审查幻觉"最务实的回答。
https://github.com/alibaba/open-code-review

---

## 三、多模态生成

**10. VoiceStudio — 完全本地的 ElevenLabs 替代品（★26,694，今日 +2,546，今日涨幅第一）**
本地离线运行：声音克隆、音色设计、视频配音、听写、转录、有声书制作，支持 646 种语言。
值得关注：今日新增 star 最高。语音克隆这块付费 API 最贵、隐私顾虑最大，本地化替代的刚需非常真实。
https://github.com/debpalash/VoiceStudio

**11. YuE2 — 音乐生成（★7,720，今日 +500）**
前沿音乐生成模型：符号化规划、零样本翻唱、Agentic 音乐编辑。
值得关注：生成式音乐从"文生一段音频"走向可结构化编辑，Agentic 编辑是这一版的主要增量。
https://github.com/multimodal-art-projection/YuE

---

## 四、基础设施 / 其他

**12. transformers — HuggingFace 模型定义框架（★165,487，今日 +102）**
文本、视觉、音频、多模态 SOTA 模型的统一定义框架，推理训练通吃。老牌霸主，长期在榜。
https://github.com/huggingface/transformers

**13. DeskcommCRM — 开源 AI 销售 CRM（★2,170，今日 +444）**
自托管 CRM，原生集成 AI Agent 和 WhatsApp（WAHA），兼容 MCP、多租户。面向"靠聊天卖货"的生意，对标 Kommo / Intercom。
值得关注：MCP-ready 已经成为 To B SaaS 的默认卖点，说明协议层的渗透速度比预期快。
https://github.com/melgarafael/DeskcommCRM

---

## 今日新上榜（非 AI，仅供参考）
- **omniget** ★11,608（+547）— 桌面下载器，1800+ 站点（Udemy/YouTube 等），基于 yt-dlp，内置课程播放器和阅读器
- **douyin-downloader** ★11,339（+473）— 抖音批量下载，去水印，支持视频/图集/合集/音乐
- **cool-retro-term** ★26,216（+98）— 模仿老式阴极射线管显示器的终端模拟器
- **ever-gauzy** ★5,027（+58）— 开源企业管理平台（ERP/CRM/HRM/ATS/PM）

---

**观察：** 今日 Trending 被三条线占满——Agent 技能包（agent-skills / Claude-Red / OpenMontage 的技能文件）、本地化推理与生成（colibri / VoiceStudio）、以及 Agent 在垂直场景的落地（pentagi / MathModelAgent / DeskcommCRM）。技能包的分发与安全审核，是这轮里最容易被忽视但涨得最快的一环。

（已标记 6 条未读项目为已读）
