
**橘鸦AI早报 · 2026-10-28**（第 31 条，共 31 条已读完）

---

### 要闻

**1｜Google DeepMind 发布世界模型 Genie 4，首次实现“边跑边改”**
Genie 4 能实时生成接近照片真实感的可交互场景，并模拟空气动力学、碰撞和人物动作。用户可以用一句文字提示改变天气、切换镜头，或加入新人物；模型会同步生成环境音、音乐和对话，这是 Google 首个原生生成音频的实时世界模型。实际控制靠 Gemini Omni 呈现效果、其他 Gemini 模型维持连贯，Gemini 3.8 Flash 负责把目标拆成步骤并检查画面进度。目前仅向受信任的测试者开放，之后会提供给 Google AI Ultra 订阅者和 Gemini API 合作伙伴。
**影响**：世界模型从“看视频”进入了“可编辑的仿真空间”阶段，游戏预演、机器人训练和影视分镜最直接受益。Google 自己也承认，它只支持几分钟连续交互，运行越久细节和物体漂移越明显，说明它离真正可用的产品还有明显距离。
https://deepmind.google/blog/genie-4-a-new-generation-of-world-simulation

**2｜OpenAI 之后，Claude 也声称推翻了 ETH（指数时间假设）**
OpenAI 于 10 月 26 日宣布其内部 AI 给出了指数时间假设的反证，并公开论文和 Lean 形式化结果，请专家核验。随后 Anthropic 的研究员 Levent Alpöge 披露，公司内部的 Claude 研究模型也找到了相关算法，能以亚指数时间求解 3-SAT 并统计满足条件的解的数量。两家都称结果产生于 10 月 16 日，Anthropic 特别说明这只是渐进时间复杂度层面，不代表实际求解变快。Alpöge 称，Claude 找到核心算法时用了 1400 万输出 token，全程没有人类输入，论文是研究人员后续与它一起改的。
**影响**：这是“AI 做原创数学”第一次出现两家公司同一天撞题的情况，而且都还没通过独立审查。如果核实，AI 自主产出理论计算机科学成果的可信度讨论会彻底变化；如果没核实，就是一次典型的 AI 辅助研究过度宣称。
https://github.com/anthropics/formal-math/tree/16a5ce41304fcdaea4e0be7c132e1c361dc26da5/eth

**3｜Axiom 称用 AI agent 24 天完成有限单群分类定理的完整 Lean 形式化**
有限单群分类定理（CFSG）的原始证明约 15000 页，由约 100 位数学家完成。Axiom 组织数十个 AI agent，由工程师和数学家指挥，24 天生成约 4310 万行 Lean 代码，并通过机器核验。过程中发现 34 处值得关注的偏差，最关键的一处涉及不平衡群定理所用的 Walter 证明：agent 找到了反例，团队被迫改用 Solomon 的极大 2-分量理论重建论证。代码以 Apache-2.0 在 GitHub 公开。
**影响**：这是形式化数学的标志性事件。意义不只是“快”，更在于 AI 在补全证明时真的发现人类文献里的漏洞，形式化验证从此不只是搬运，还承担纠错。
https://cfsg.axiommath.ai/

---

### 模型与开源

**4｜蚂蚁百灵开源 Ling-3.1-flash-1019，连同基座一起放出**
总参数 5600 亿，每个 token 激活 250 亿，支持 100 万 token 上下文，权重已在 Hugging Face。除了发布指令模型，还开放了 Ling-3.1-flash-base 基座，方便他人继续训练。成绩方面，Artificial Analysis 智能指数从上一代 41 升到 44，AutomationBench-AA 从 62% 升到 68%。
**影响**：开源一个 5600 亿参数、激活 250 亿的 MoE，还附带基座，是少见的大厂级开放动作；对想在中文长上下文场景自建模型、又不想从零预训练的团队，直接省掉最贵的一步。
https://huggingface.co/inclusionAI/Ling-3.1-flash-1019

**5｜商汤开源 SenseNova 6.8 Code2Video：写代码生成视频，改代码改片子**
该模型基于 Qwen3.8-27B 微调，支持 512K 上下文，思路不是直接生成像素，而是生成可执行代码来构建场景并渲染视频。成片后用户提修改意见，它在同一项目里改代码并重渲，等于视频有了“源码”这一层。发布包含权重、示例轨迹和一个 code-video Skill，采用 Apache 2.0。商汤自己承认，它在视觉效果和长程稳定性上明显落后于最强闭源模型。
**影响**：可编辑性是这个方向真正的卖点：生成式视频最麻烦的就是改一处崩全片。但“明显落后”的自我评价也说明，它现在更适合当技术路线验证，还不能当生产力工具。
https://github.com/OpenSenseNova/SenseNova-6.8-Code2Video

**6｜两份 OCR 开源同日发布：百度 Unlimited OCR 2 和 OpenBMB MiniCPM-OCR**
百度 Unlimited OCR 2 用 SR-SWA 注意力机制，把文本和图像的交互压缩成固定数量的工作参考，因此在有限上下文窗口里能解析几十到几百页文档，而且每步解码延迟和内存占用近乎恒定；MPDocBench 84.6 分、MarathonDocBench 77.1 分。OpenBMB 则把 OCR 做成一对：1.3B 的 MiniCPM-OCR 1.0 负责解析，2B 的 Jev 负责给 OCR 结果打 0–1 质量分，还能评估 GLM-OCR、PaddleOCR 等别家解析器的输出。
**影响**：长文档解析的成本瓶颈正在被工程化解决。Jev 这种“给 OCR 结果打分”的模型尤其实用，在 RAG 流水线里能自动筛掉烂页，而不是把错字喂给下游。
https://github.com/baidu/Unlimited-OCR ｜ https://huggingface.co/openbmb/MiniCPM-OCR-1.0

**7｜小模型技术继续提升：Liquid AI LFM3 六个 2B 模型、Spark-X2.6-1.7B 强化 coding**
Liquid AI 用同一套 tri-hybrid 骨干一次推出六个约 2B 的开放权重模型（文本、视觉、音频、全模态、决策），其中 LFM3-1.7B 比上一代 2.6B 参数少 35% 但更强，上下文 256K，4-bit 下约 1GB；LFM3-VL-2B 首次支持视频输入。星火 Spark-X2.6-1.7B 保持原架构只改后训练，SWE Verified 从 28.3 跳到 59.8，τ²-bench 从 65.3 到 85.3，提供 none/low/high 三档 thinking。
**影响**：端侧和本地部署的性价比又提高了一档，1.7B 模型的 SWE 分数翻倍说明后训练的红利还远没吃完，这对不打算上大模型的开发者是好消息。
https://liquid.ai/blog/lfm3 ｜ https://huggingface.co/XHToken/Spark-X2.6-1.7B

---

### 开发工具与产品

**8｜Cursor Design Mode 上线 Annotate：在浏览器里圈画，让 agent 改代码**
在 Agents Window 的浏览器里，用户可以点选页面元素、框出区域或直接涂画，每条标注连同元素信息和截图一起发给 agent，agent 改代码的同时用户可以继续标下一处，并能切换屏幕尺寸检查响应式设计。快捷键 Cmd+Shift+D。
**影响**：这是“用自然语言描述 UI 问题”的低效环节被视觉标注取代。对前端来说，沟通成本一直是 agent 编码的主要损耗，标注把“第三栏按钮太挤”这种含糊话变成了可定位的指令。
https://cursor.com/docs/agent/design-mode

**9｜Cognition 发布 FrontierCode 2.0：从“会不会合并”改成“该不该合并”**
旧版只判断“维护者会不会合这个 PR”，新版考察模型能否写出真正值得合的代码：仓库数量多 55%，类别扩展到安全补丁和性能优化，提示词故意写不完整，逼模型自己判断需求。参考解法平均要改 67% 更多文件、89% 更多代码行。榜单上 Claude Opus 5.5 得 45.5%，GPT-6 Astra 42.8%。
**影响**：SWE-bench 那类基准已经饱和，开始在角落里挑刺；FrontierCode 2.0 把评分标准推向“代码品味”和“需求补全”，分数掉到 40% 区间恰恰说明它摸到了更难的地方。
https://cognition.com/blog/frontier-code-2.0

**10｜其他值得一看的产品动作**
- **ChatGPT 接入 iCloud 邮件和日历**：可查邮件、整理收件箱、看下一项日程、更新日历事件，覆盖所有订阅方案和 Web/桌面/iOS，连接需 Apple 专用密码。这是 OpenAI 把助理往个人数据纵深推的一步。
- **Arena Agent Mode 上线 Connectors**：可连 GitHub、Google Drive、Notion、Linear、Gmail、Supabase、Vercel、Dropbox，免费开放。
- **微信输入法 4.0.0 新增 AI 录音笔**：边录边转写，AI 总结后生成可分享、可交互的网页，iOS、Android、Windows 全平台。
https://x.com/ChatGPT/status/2115139248458191070

---

### 产业与算力

**11｜Anthropic 一天三件事：买公司、进政府、租 630 亿美元芯片**
它宣布与 BigHat、BMS、Generate Biomedicines 等六家药企合作并启动自有药物发现项目；收购一人公司 Mithril Medicine——创始人靠 Claude 协调 11 家外部实验室的合同、物流和实验，不到 18 个月把一款罕见肌营养不良疗法从构想推到小鼠实验并取得积极结果，若顺利最早 2028 年底进人体临床。同时与美国总务管理局签 OneGov 协议，向各级政府提供 Claude，全产品线 40% 折扣，无最低消费承诺。算力侧，美银、Blackstone、花旗、摩根士丹利安排 630 亿美元融资，购买 Broadcom XPU 加速器和网络设备租给 Anthropic，2027 年起交付。
**影响**：这是“AI 公司开始自己做科研”的最具体样本，一人公司加 Claude 顶掉一个实验室的协调工作量。而 630 亿美元的 SPV 租赁结构，说明前沿实验室的算力扩张已经彻底金融化，风险被转移到资本市场。
https://anthropic.com/research/early-progress-drug-development

**12｜TPU 第一次走出 Google 云：Oracle 将从 2027 年起提供 Google TPU**
Oracle 与 Google 在 Oracle AI World 宣布，OCI 将提供 Google TPU，这是 TPU 首次在 Google 以外的超大规模云平台上可用。OCI 负责电力、冷却和数据中心网络，客户可在同一云内混用 TPU 和 GPU，按负载挑加速器。
**影响**：TPU 从“自用芯片”变成“对外商品”，直接冲的是 NVIDIA 在云端的默认地位。虽然 2027 年才可用，但对多云架构和议价能力的影响现在就开始计价。
https://cloud.google.com/blog/products/infrastructure/bringing-google-tpus-to-oracle-cloud-infrastructure

**13｜行业侧记两则**
- **Anthropic 招聘经理公开宣布取消传统编码面试**：Felix Rieseberg 称 Claude 在 React 小题和汇编问答上已经比人强，这类测试不再有信号；团队里最高效的开发者也和刷题成绩无关。他的建议是初级工程师围绕业务影响选题、用一个周末做出可运行原型。
- **Cloudflare 披露 GLM-5.3 数据泄露**：Workers AI 上该模型因缓存配置和 SGLang 请求拒绝路径缺陷，把其他用户的请求数据返回给了部分用户，155 条响应受影响。触发条件是提示词超过 681,280 tokens（模型配置 1M 上下文，但 KV cache 池更小）。已修复，未发现蓄意利用。
- **梁文锋首次上胡润百富榜**：以 2800 亿元列第七，也是今年新上榜第一。胡润称去年未纳入是因为他曾提“不商业化”，今年 DeepSeek 估值升至 500 多亿美元。
https://blog.cloudflare.com/kv-cache-exposure-remediation/

---

**一句话总结**：这一天的主线是“AI 开始产出可核验的硬成果”：Genie 4 让仿真可编辑、Claude 和 OpenAI 同日撞上数学反证、Axiom 24 天啃完 15000 页定理；另一条线是 Anthropic 用资本和芯片把算力规模推到 630 亿美元级别，开源侧则被 2B 小模型和 OCR、视频这类“可落地工具链”占领。
