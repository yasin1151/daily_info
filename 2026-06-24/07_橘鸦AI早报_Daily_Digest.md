
橘鸦 AI 早报最新一期：**2026-06-23**  
原文：https://daily.juya.uk/issues/2026-06-23/

注：`blogwatcher-cli scan "橘鸦AI早报"` 返回 404，原因是本地配置的旧 RSS `https://imjuya.github.io/juya-ai-daily/rss.xml` 已失效；我从新官网 RSS `https://daily.juya.uk/rss.xml` 抓取了最新一期。`read-all` 已执行，本地无未读可标记。

1. **OpenAI 推出完整版 GPT-5.5-Cyber，面向受信任防御者开放**  
   OpenAI 扩展 Daybreak 计划，发布 Codex Security 更新、GPT-5.5-Cyber，并联合 Trail of Bits、HackerOne 等启动 Patch the Planet。核心变化是把安全漏洞发现推进到“验证、补丁、人工审查”闭环；影响是开源维护者和安全团队会获得更强的 AI 辅助修复能力，但模型访问仍被严格限制。  
   https://openai.com/index/daybreak-securing-the-world/

2. **Sakana AI 发布多 Agent 编排系统 Fugu，但透明度引发质疑**  
   Fugu 通过 OpenAI 兼容 API 动态调用多个闭源模型，宣称在编程和推理基准上接近顶级模型。它代表“模型编排器即产品”的路线，但社区质疑其成本、token 消耗、底层模型选择都不透明，企业采用时需要重点评估可控性和合规风险。  
   https://sakana.ai/fugu/

3. **京东开源实时视觉交互模型 JoyAI-VL-Interaction**  
   这是一个 8B 视觉语言交互模型，能持续观察视频流，并在 1 秒内决定回应、沉默或委托后台 Agent。它的价值在于把多模态从“问答”推向“实时陪伴式交互”，适合视频助手、直播客服、具身智能前端等场景；同时开源了权重、400 万条训练数据和 vLLM 部署系统。  
   https://github.com/jd-opensource/JoyAI-VL-Interaction

4. **百度发布 Unlimited-OCR，主打长篇文档一次性解析**  
   3B 参数模型支持单图和多页 PDF 长文档 OCR，代码与权重已开放。影响是文档智能的门槛继续下降，尤其对合同、报告、扫描件批处理有直接价值；若部署成本可控，可能替代一部分传统 OCR 加版面分析流水线。  
   https://github.com/baidu/Unlimited-OCR

5. **Ai2 发布 TMax 开源终端 Agent 训练方案**  
   TMax 提供 14,600 个 RL 环境数据集、DPPO 训练配方，以及 2B 到 27B 的终端 Agent 模型。TMax-9B 在 Terminal Bench 2.0 达到 27.2%，接近 Claude Haiku 4.5；这对开源 coding/terminal agent 很关键，因为它公开了数据、权重、rollout 和训练方法。  
   https://wai-org.com/blog/tmax

6. **Google Interactions API GA，成为 Gemini 模型与 Agent 默认接口**  
   新 API 面向模型与自主 Agent 编排，支持 Managed Agents、远程 Linux 沙盒、后台执行、结构化步骤，以及 Maps、多模态生成等工具生态。影响是 Gemini 的前沿 Agent 能力会逐步集中到新接口，开发者需要开始从旧的 `generateContent` 迁移心智模型。  
   https://blog.google/innovation-and-ai/technology/developers-tools/interactions-api-general-availability/

7. **SpaceXAI 推出 Grok Build `/goal` 模式，强化长周期自主执行**  
   `/goal` 允许用户输入一个目标后，由系统规划、维护任务清单、调用多轮 subagent，并执行验证。它反映 coding agent 产品竞争正在从“单次补全/聊天”转向“长期任务执行与自检”；但目前需要 SuperGrok 或 X Premium Plus。  
   https://x.ai/news/introducing-goal

8. **Micron 与 Anthropic 达成战略合作，AI 基建继续向存储侧扩展**  
   双方将在 HBM、DRAM、SSD 供应，以及训练/推理存储架构优化上合作，Micron 还投资 Anthropic H 轮融资。影响是大模型竞争不只在 GPU，也在内存带宽、存储子系统和能效优化，Claude 规模化部署会进一步绑定上游硬件供应链。  
   https://investors.micron.com/news-releases/news-release-details/micron-and-anthropic-announce-strategic-agreement-scale-next

9. **微软得州 2GW 数据中心绑定 Chevron 20 年供电协议**  
   Microsoft 将在得州 Pecos 建设约 2GW 数据中心，Chevron 配套约 2.67GW 天然气电厂并脱离公共电网供电。影响是 AI 数据中心进入“算力、电力、能源项目一体化”阶段，未来模型能力扩张越来越取决于电力获取速度和能源合同。  
   https://blogs.microsoft.com/blog/2026/06/22/powering-the-next-wave-of-ai-expanding-capacity-with-our-new-datacenter-in-pecos/

10. **Groq 完成 6.5 亿美元融资，继续押注推理云**  
   Groq 称每周处理数万亿 tokens，新融资将用于扩展全球推理基础设施，目标到 2027 年底达到 200MW。影响是推理侧专用基础设施竞争加速，低延迟、高吞吐推理云仍是 AI 应用规模化的关键战场。  
   https://groq.com/newsroom/groq-raises-usd650m-to-scale-its-ai-inference-cloud-business
