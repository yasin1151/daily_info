
HackerNews 今日未读 20 条，筛选出 10 条高价值内容。已完成标记已读，复查结果为 `No unread articles!`。

1. **Prismata：为 Web Agent 隔离跨站提示注入**
摘要：论文提出 Prismata，用“上下文最小权限”限制 Web Agent 能看到的页面内容和能执行的动作。它把网页结构中的可信/不可信内容动态打标签，并通过内容遮蔽和能力限制降低第三方页面文本劫持 Agent 的风险。  
为什么值得关注：Web Agent 安全正在从“提示词防御”走向浏览器级权限模型，这是 Agent 产品化绕不开的基础问题。  
原文链接：https://arxiv.org/abs/2607.08147

2. **GhostLock：存在 15 年的 Linux 栈 UAF 漏洞**
摘要：Nebula Security 披露 CVE-2026-43499，一个自 2011 年以来影响主流 Linux 发行版的 kernel stack use-after-free。作者称无需特殊内核配置或权限即可触发，并将其做成 97% 稳定的提权和容器逃逸利用。  
为什么值得关注：这是内核安全、容器隔离和发行版补丁响应的高风险案例，尤其影响多租户基础设施。  
原文链接：https://nebusec.ai/research/ionstack-part-2/

3. **LWN：住宅代理与 AI 爬虫正在侵蚀开放 Web**
摘要：LWN 更新了 AI 爬虫问题：大规模抓取流量来自住宅和移动网络代理，单个 IP 只访问少量页面，传统封禁很难奏效。HN 评论分歧集中在两点：应建立更好的公共语料抓取机制，还是会进一步把开放 Web 推向 Cloudflare 式集中控制。  
为什么值得关注：训练数据、Agent 浏览器和反爬基础设施之间的冲突正在变成开放 Web 的结构性成本。  
原文链接：https://lwn.net/SubscriberLink/1080822/990a8a5e2d379085/

4. **GPT-5.6 Sol Ultra 声称证明 Cycle Double Cover 猜想**
摘要：OpenAI 发布 PDF，称 GPT-5.6 Sol Ultra 产出了 Cycle Double Cover Conjecture 的证明。HN 讨论热烈，评论者一方面关注证明本身是否经得起专家验证，另一方面注意到提示词仍大量要求模型“不要只报告进展，要真正解决问题”。  
为什么值得关注：数学证明是 AI 可验证能力的关键战场，但最终价值取决于独立同行审查，而不是发布方声明。  
原文链接：https://cdn.openai.com/pdf/04d1d1e4-bc75-476a-97cf-49055cd98d31/cdc_proof.pdf

5. **QuadRF：用 Raspberry Pi 和 FPGA 看见无线电世界**
摘要：Jeff Geerling 体验 QuadRF，一个围绕 Raspberry Pi 5 和 FPGA 构建的相控阵无线电系统，可做高级信号处理和波束成形，演示中能穿墙观察 WiFi 信号并追踪无人机。创作者在 HN 现身，提到 UI、校准和开放源码方向。  
为什么值得关注：低成本 SDR、FPGA 和可视化工具正在把原本偏军工/专业设备的 RF 感知能力带给开源社区。  
原文链接：https://www.jeffgeerling.com/blog/2026/quadrf-can-spot-drones-and-see-wifi-through-my-wall/

6. **Scarf 运行 7 年后放弃 Haskell**
摘要：Scarf 创始人解释，Haskell 在可靠性、类型系统和性能上兑现了很多承诺，但生产中的编译时间、生态摩擦和 AI Agent 迭代效率成为真实成本。HN 评论焦点是：强类型本应帮助 LLM 写代码，但慢编译会拖垮 Agent 的反馈循环。  
为什么值得关注：这不是简单的语言好坏之争，而是“Agentic development”正在改变工程语言选择的权衡。  
原文链接：https://avi.press/posts/2026-07-10-after-7-years-in-production-scarf-has-reluctantly-moved-away-from-haskell.html

7. **Apple 起诉 OpenAI，指控前员工窃取商业机密**
摘要：Apple 起诉 OpenAI、io Products 及相关前员工，称有人将 Apple 未发布技术、流程和产品信息带给 OpenAI，尤其涉及 OpenAI 与 Jony Ive 相关硬件项目。HN 评论普遍认为若报道属实，证据发现阶段会非常关键。  
为什么值得关注：AI 硬件竞赛已经进入人才、供应链和商业秘密层面的法律冲突，可能影响 OpenAI 硬件路线。  
原文链接：https://9to5mac.com/2026/07/10/apple-sues-openai-trade-secret-theft/

8. **恐怖组织如何使用前沿 AI**
摘要：CASP 报告讨论 Boko Haram 使用 AI 的案例。正文抓取失败，但 HN 讨论显示读者对报告方法和结论强度有明显怀疑：部分引用看起来像“内部传闻”，AI 的实际战术增益可能被标题放大。  
为什么值得关注：AI 安全叙事需要区分“真实能力扩散”和“夸大式风险传播”，这类报告会影响政策与模型管制。  
原文链接：https://casp.ac/reports/ai-enabled-terrorism

9. **SpaceX 申请再发射 10 万颗 Starlink 卫星**
摘要：ZDNET 报道 SpaceX 希望大幅扩张 Starlink 星座，以获得最高 100 倍带宽提升。HN 评论呈现典型分歧：一边看好偏远地区联网和空间基础设施，另一边担心轨道拥堵、夜空污染和企业控制全球接入层。  
为什么值得关注：卫星互联网已从连接服务变成全球网络基础设施竞争，监管和外部性会越来越重要。  
原文链接：https://www.zdnet.com/home-and-office/networking/spacex-wants-to-launch-100000-more-starlink-satellites/

10. **把计算视为宇宙级基础概念**
摘要：Tim Roughgarden 的课程从图灵、停机问题、算法捷径、旅行商问题和 P vs NP 出发，讨论计算为什么不仅是工程工具，也是一种理解自然和复杂系统的基础语言。HN 评论提醒：不要把“计算是有用模型”跳成“宇宙本质就是计算”。  
为什么值得关注：适合从理论计算机科学角度重新理解 AI、复杂系统和可计算性边界。  
原文链接：https://ergo.org/courses/computation-as-a-universal-and-fundamental-concept
