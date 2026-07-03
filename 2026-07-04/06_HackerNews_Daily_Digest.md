
## HackerNews 技术精选 Top 10（已标记本轮 20 篇为已读）

### 1. Leanstral 1.5：开源 Lean 4 证明模型
**摘要：** Mistral 发布 Apache-2.0 许可的 Leanstral 1.5，119B 总参数、6B 激活参数，面向 Lean 4 形式化证明。官方称其 miniF2F 达到 100%，PutnamBench 解出 587/672，并能在真实代码库中生成性质、尝试证明并发现 bug。  
**为什么值得关注：** 形式化验证正在从“专家工具”走向 AI 代理可执行工作流，尤其对高可靠系统、编译器、密码学库和基础设施代码有现实意义。HN 评论关注其 bug-finding 示例是否足够有说服力。  
**原文：** https://mistral.ai/news/leanstral-1-5/

### 2. AMD MI355X 上跑 GLM5.2：推理性价比挑战 Blackwell
**摘要：** Wafer 报告称在 AMD MI355X 上服务 GLM5.2，达到 2626 tok/s/node、单流 213 tok/s，并宣称成本低于 Blackwell 两倍以上。文章重点讨论 MXFP4 量化、ROCm 栈优化和新模型 day-0 支持难题。  
**为什么值得关注：** 如果 AMD 推理栈持续缩小软件差距，AI 基础设施成本结构会发生变化。HN 评论希望看到 performance-per-watt，并质疑供应商毛利、利用率等真实经济账。  
**原文：** https://www.wafer.ai/blog/glm52-amd

### 3. 小语言模型中的 embedding condensation 与 dispersion loss
**摘要：** ICML 2026 工作观察到小模型 Transformer 层中的 token embedding 更容易塌缩到狭窄锥形子空间，称为 embedding condensation。作者提出 dispersion loss，在训练中鼓励表示分散，以改善小模型泛化。  
**为什么值得关注：** 这提供了一个解释“小模型为什么弱”的几何视角，也可能给小模型训练、蒸馏和高效模型设计带来新正则化方向。作者也坦诚增益较小，需谨慎复现。  
**原文：** https://chenliu-1996.github.io/projects/LM-Dispersion/

### 4. Claude Mythos 发布后，高危 CVE 披露量激增
**摘要：** Epoch AI 统计称，Claude Mythos Preview 宣布具备自主漏洞发现能力后，2026 年 6 月约有 1500 个高危/严重 CVE 被重要组织披露，是此前月度纪录的 3.5 倍以上。文章关联 Anthropic Project Glasswing 和 OpenAI Daybreak。  
**为什么值得关注：** AI 辅助漏洞发现可能显著改变安全行业的披露节奏、修复压力和攻防窗口。HN 评论关心披露有效性、是否存在 AI 幻觉，以及责任披露期结束后是否还有更大规模释放。  
**原文：** https://epoch.ai/data-insights/cve-severity-spike

### 5. Firefox 到 Android Root 的完整提权链
**摘要：** IonStack 页面宣称展示 Android 17 上首个 browser-to-kernel full-chain RCE，从 Firefox 入口一路提权到 Android root；源码倒计时后公开。目前公开正文信息很少，HN 讨论也主要围绕标题与演示安全性。  
**为什么值得关注：** 浏览器到内核的完整链条对移动安全极具信号价值，尤其涉及 Android 沙箱、浏览器隔离和内核攻击面。需等待技术细节公开后再判断漏洞质量。  
**原文：** https://rootme.nebusec.ai/

### 6. ContextCodeCache：为 AI Agent 生成代码库结构缓存
**摘要：** Show HN 项目 ContextCodeCache 是 Rust 工具，可扫描项目并生成 `.ccc` 目录，记录源文件常量、函数、返回类型、文档摘要、文件内调用图和 TODO/FIXME 标记，并支持 CI 检查缓存是否过期。  
**为什么值得关注：** 这类“代码库索引层”是 AI 编程代理的重要基础设施：相比每次全量读仓库，结构化、可更新、可提交的上下文缓存更便宜，也更适合长任务代理。  
**原文：** https://github.com/colwill/ccc

### 7. Steam Controller Auto-Charge：用视觉和 WebHID 自动“开”进充电座
**摘要：** 这是一个开源 Web 应用，用 OpenCV.js 光流追踪、WebHID 遥测和 Steam Controller 的 LRA 震动反馈，让手柄在桌面上自动移动到磁吸充电 puck。项目还包含 Rust/WASM 的视觉处理模块。  
**为什么值得关注：** 虽然像极客玩具，但它展示了浏览器 API、计算机视觉、HID 控制和 WASM 的有趣组合，也说明现代 Web 平台已能承载不少本地硬件自动化实验。  
**原文：** https://github.com/FossPrime/Steam-Controller-Auto-Charge

### 8. Software, from First Principles：从物理到软件的长篇心智模型
**摘要：** 这篇 54 分钟长文试图从第一性原理解释软件：从物理开关、逻辑门、通用计算机、操作系统、内存共享到网络通信，降低非专业读者理解计算系统的门槛。  
**为什么值得关注：** 对工程师也有价值：它把复杂系统拆成层层抽象，适合作为技术写作、入门教育和“重新校准基础概念”的参考。HN 当前评论不多，但文章本身结构完整。  
**原文：** https://fazamhd.com/mental-models/software/

### 9. Applied Category Theory Course：应用范畴论课程网页
**摘要：** John Baez 基于 Fong 与 Spivak 的《Seven Sketches in Compositionality》整理的应用范畴论课程，覆盖偏序、资源理论、数据库、协作设计、Kan 扩张等内容，并以网页形式组织。  
**为什么值得关注：** 范畴论在数据库、组合系统、类型论、资源建模和程序语义中都有应用。对想建立“组合性”抽象思维的工程师，这是较系统的学习入口。  
**原文：** https://math.ucr.edu/home/baez/act_course/index.html

### 10. 欧洲议会议员手机遭 Pegasus 间谍软件感染
**摘要：** Citizen Lab 报告称，对希腊欧洲议会议员 Thanasis Kouloglou 的 iPhone 取证后，高置信度确认其设备在 2022 与 2023 年多次感染 Pegasus。HN 讨论集中在欧洲政界间谍软件滥用、设备隔离和反情报能力薄弱。  
**为什么值得关注：** 虽偏安全/政治交叉，但对移动端高价值目标防护、商业间谍软件监管和组织安全策略有直接启发。评论中特别提到工作/私人设备混用带来的风险。  
**原文：** https://citizenlab.ca/research/member-of-committee-investigating-spyware-hacked-with-pegasus/
