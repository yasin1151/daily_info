
**橘鸦AI早报 · 2026-11-24 期摘要**

---

**1. 智谱发布 GLM-5.4：首个 Loop Transformer 旗舰，瞄准"泛 Coding"**
这是智谱第一款不用"堆参数"换智能的旗舰。它把 750B 基座里 28 层做两轮循环，官方称效果相当于 2–3 万亿参数级模型，代价是推理更慢（官方自己也提示模型容易进入长时间的"雷霆大思考"模式）。在 200 个真实编程场景的评测中，视觉 Coding、界面复刻、长程任务表现突出，还能向外扩展到视频生成、完整游戏构建、3D 建模、机械工程设计。
已向 GLM Coding Plan 全量开放，V2、V3、团队版额度升到 1.5 倍，但 V1 老用户没加，这点在社区被吐槽。API 待安全评估后开放，权重计划开源。
https://mp.weixin.qq.com/s/D-IZr-QaT1or_chminK8IQ

**2. OpenAI 在 ChatGPT 上线日常对话版 GPT-6.2 Sol**
注意不是全线替换，只在 Chat 模式、面向 Plus/Pro/Business/Enterprise。核心提升在"日常琐事"：图像理解 71.7%（旧版 47.4%）、高难度指令遵循 78.1%（旧版 62.5%），更擅长按价格和位置帮人缩小选项、主动追问。方向很明确——把模型从"答题工具"做成"帮你做决定的人"。
https://help.openai.com/en/articles/6825453-chatgpt-release-notes

**3. Antigravity 重置全部用户配额，Carbon 向付费 Pro 开放**
负责人 Varun Mohan 直接宣布重置所有人 Gemini 配额（因各层级模型升级）。付费 Pro 可拿到 Carbon 权限，Hydrogen 按承诺向全体开放。关键变化是：Pro 用户原有的独立 Argon 配额池被取消、并入通用池，好处是能自由分配在 Argon、Carbon、Neon 上。有用户反馈重置后没看到 Carbon，官方回复"正在推送"。
https://x.com/_mohansolo/status/2124971131312734707

**4. Claude Ship 测试版：让 Claude 审查、修复、甚至批准 PR**
把代码评审自动化推到了"批准"这一步，分三块：Code Review（已通用）、PR Steward（处理 CI 失败、合并冲突、审查反馈，但设计上不批准也不合并）、Claude Approvals（按仓库政策文件检查，政策允许时可自行批准例行改动）。面 Team/Enterprise，按 token 额外计费，用 `/ship` 命令体验。值得关注的是"AI 自己批 PR"的边界怎么划。
https://code.claude.com/docs/en/claude-ship

**5. Gemini API 上线文件切片控制，只为实际处理的部分付费**
以前传一个 200 页 PDF 就按 200 页计费，现在可以指定页码、工作表、单元格区域、时间段，甚至内容层（页面图像 / 提取文本 / 公式 / 视频转录）。对做长文档 RAG、长视频分析的成本影响很直接。已覆盖 Google AI Studio 和 Vertex AI。
https://blog.google/innovation-and-ai/technology/developers-tools/file-slicing-controls/

**6. OpenAI 与 Cisco 开源 AI 安全运行时 Shirudo**
面向 Linux 的 eBPF runtime，让 AI agent 现场写动态防护规则——在打补丁之前拦住漏洞利用、放行正常请求，为部署补丁争取时间。防护规则要经加密签名验证 + 运维批准才加载。测试中 Codex 生成的防护成功拦下针对运行中 Elasticsearch 的 Java4Shell 攻击。BSD 2-Clause，OpenAI 称之为"自防御基础设施的第一步"。这条比大多数模型新闻更有长期意义。
https://github.com/shirudo-dev/shirudo

**7. Google DeepMind 用多组 Gemini 4 agents 优化量子算法，成果降本 10 倍**
玩法值得学：多个 agent 团队并行独立找优化方案，每个方案必须过 Lean 形式化证明（量子线路没法在经典机上验证，只能用数学证明保证正确），结果汇入共享笔记，每 4 小时开"虚拟会议"互相对比。成果：惯性约束聚变计算成本降 11.8 倍、常见光敏分子模拟降 8 倍、药物代谢关键酶 CYP450 降 2.5 倍。方案与 Lean 库已开源。这是"多 agent + 形式化验证"跑通科学发现的完整闭环样板。
https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/

**8. Claude 的 Connectors 与 Skills 合并为 plugins，1 万多个可浏览**
原来"连工具"和"教技能"是两套入口，现在统一成 plugins，侧边栏 Customize 改名 Plugins，三页合并为一。Free/Pro/Max/Ultra 已上线，Team 从 11/30 起、Enterprise 随后几周。已安装内容保留。生态开始收口，对做 Claude 插件的人是窗口期。
https://support.claude.com/en/articles/13837440-use-plugins-in-claude

**9. OpenRouter：上周用户花在 Google 模型上的钱超过了 OpenAI**
占比破 50%，推手是 Gemini 4 Neon、Carbon 等口碑不错的新模型。但 OpenRouter 洞察负责人 Peter Walker 明确说：按 token 用量算 Neon 并没超过 OpenAI，这次反超只体现在支出上——也就是说 Google 单 token 更贵、但用户愿意买单。这种反超年初常见，自 6 月 8 日那周后就没再出现过。
https://x.com/PeterJ_Walker/status/2124924320459989032

**10. 需要动作的两条下线/收紧通知**
- ChatGPT 将于 12 月 23 日下线 GPT-5.6 Sol（Chat 服务），Work 和 Codex 里 Sol 与 Terra 一起下线，有依赖的趁早迁。
- Mistral Vibe API 被社区曝出不再允许用于非 Mistral 产品，下月 Vibe 额度只能在 Vibe CLI 用，付费用户记得取消订阅。
https://x.com/ChatGPT/status/2124981905380569283

---

**一句话总结**：今天最值得看的是三条结构性变化——智谱用循环架构绕开参数堆叠、Claude Ship 把 AI 推到"批准 PR"这一步、OpenAI 和 Cisco 用 agent 写 eBPF 防护规则。其余多为配额、计费和入口整合类调整。

（已标记 2026-11-24 期已读，源内无其他未读文章）
