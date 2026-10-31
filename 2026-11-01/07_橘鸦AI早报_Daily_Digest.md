
# 橘鸦 AI 早报 2026-10-31 期摘要

**本期主线**：Anthropic 调整订阅层级，并放宽 Ultra 的额度限制；AI 供应链方面出现了一笔千亿美元级的算力合同；苹果的 Apple 智能在中国市场正式接入千问。安全方面则出现一起值得警惕的供应链攻击。

---

## 1. Anthropic 调整 Claude 订阅命名，Ultra 逐步取消 5 小时限制
Claude Max 5x 更名为 **Max**（100 美元/月），Max 20x 更名为 **Ultra**（200 美元/月），价格不变。关键是：已验证的 Ultra 账户将**逐步取消 5 小时窗口限制**，周额度维持 Pro 的 10 倍。未验证账户仍有临时限制，验证为自动进行，暂时无法主动申请。
**影响**：重度用户的主要限制从短期频率转向周总量，更适合长时间运行 agent 或进行大批量编码任务。这相当于 Anthropic 承认：长任务工作流才是高价值场景，按小时限制会造成明显干扰。
https://support.claude.com/en/articles/17728952-what-is-the-ultra-plan

## 2. Cursor 扩展市场出现被篡改的 Claude Code，植入 SSH 后门
Cursor 确认其 VS Code 扩展市场上曾有 **Claude Code 2.1.312 / 2.1.313** 两个恶意版本（Windows 和 macOS），都不是 Anthropic 官方版本；它们会收集主机信息并尝试安装持久化 SSH 后门。Cursor 已下架相关版本，与云服务商合作把攻击服务器下线，并在审计、密钥轮换、重建后恢复市场。
**影响**：危险之处在于，卸载扩展可能清不掉独立运行的持久化脚本。使用过这两个版本的人需要检查设备，而不只是执行卸载。AI 编程工具已经成为供应链攻击的重点目标。
https://cursor.com/blog/claude-code-extension-security-notice

## 3. 苹果 Apple 智能在中国上线，Siri 接入阿里千问
首批功能 11 月 4 日随 iOS 开发者 Beta 开放，12 月随 iOS 27.3 正式推出，包括实时翻译、照片消除、写作工具；现有 Siri、写作工具、视觉智能后端接入**阿里巴巴千问**。支持 iPhone 16 及后续机型、iPhone Air、iPhone 15 Pro/Pro Max 等。
**影响**：这是国内大模型第一次以“默认系统级助手”的身份进入数亿台设备，对国产模型的品牌与调用量影响很大。但这次不含 WWDC 2026 宣布的下一代 Siri AI，说明苹果在中国走的是“旧功能 + 本地模型”的保守过渡路线。
https://www.apple.com.cn/newsroom/2026/10/apple-intelligence-features-are-coming-to-users-in-china/

## 4. Anthropic 被指是 SpaceX 最大单一客户，合同上限 1205 亿美元
SpaceX 申报文件显示，上季度约 **34.5% 营收** 来自 AI 部门（现名 Super Intelligence）的单一客户“客户 B”，知情人士指认是 Anthropic。Anthropic 已签约租用 SpaceX 孟菲斯数据中心算力，合同期至 2029 年，支出上限 1205 亿美元，从今年 12 月起约合**每月 31 亿美元**。
**影响**：这个数字超过多数模型公司全年营收，说明头部实验室正在以“长期锁定算力”的方式竞争。一旦模型收入增速不及预期，这会变成极重的固定成本，这也是 Anthropic IPO 叙事里最关键的风险项。
https://x.com/elonmusk/status/2116036703538606301

## 5. OpenAI 推出 Private Intelligence，企业数据可零留存
面向商业客户的数据保护方案：客户拥有输入输出数据所有权，可决定 agent 能访问什么、执行什么操作、何时需要人工审批；符合条件的 API 工作流可用 **Zero Data Retention**，处理后不留存提示词和回复；Private Inference 目前是预览版。
**影响**：这是针对金融、医疗、法务等“不能把数据交出去”的行业所做的补充完善。企业采购的真正门槛一直在这里，而不在模型能力上。
https://openai.com/business/private-intelligence

## 6. OpenAI、Google、Microsoft、Anthropic 共同支持 robots.txt 训练偏好标记
四家支持一种基于 IETF 草案的通用 policy token，网站可以在 robots.txt 里一次性向多家厂商声明内容是否可用于训练。落地节奏不同：Anthropic 已开始实施，OpenAI 未来数月，Google 目标 2027 年，Microsoft 2027 年 2 月 1 日起生效，3 月 1 日后旧的 NoArchive/NoCache 不再被视为训练偏好。
**影响**：这是把“AI 抓取授权”从各家私有的爬虫协议统一成一个标准化入口。对内容站是利好，但也意味着 2027 年前会有一段规则混乱的过渡期：旧标签失效，新标签尚未全面生效。
https://openai.com/index/helping-websites-express-ai-training-preferences/

## 7. 商汤开源 SenseNova-Loop-9B-Preview：9B 参数做到 27B 级表现
约 90 亿参数的多模态模型，支持图文输入、文档与编码任务，训练序列最长 262,144 token。核心设计是**循环复用部分解码器参数**来增加计算深度，而不是提高参数规模。商汤称在 WorkBuddy Bench 等测试中优于 Qwen3.5-27B，达到 27B 级别性能。
**影响**：这条技术路线值得关注：用深度换宽度，主打端侧和 agent 工作流的低成本推理。如果“循环层”能在真实任务里稳定，对小参数量模型社区会是一次明显的方法变化。
https://huggingface.co/sensenova/SenseNova-Loop-9B-Preview

## 8. OpenCode Go 给 DeepSeek V4.1 Flash 每月 100 美元额度
OpenCode 发布 Operation Cheepseek 第四阶段：Go 订阅用户可获得 DeepSeek V4.1 Flash 每月 **100 美元** 使用额度，订阅本身 10 美元/月起，额度另受 5 小时（月度 20%）与每周（50%）限额约束。该模型分峰谷计价：每百万 token 输入/输出，非高峰 0.15/0.60 美元，高峰 0.30/1.20 美元。
**影响**：10 美元订阅撬动 100 美元模型额度，是典型的“用补贴换编码场景留存”的打法，对成本敏感的开发者吸引力很强。峰谷差价一倍，也提示批处理任务应尽量错峰。
https://opencode.ai/v2/docs/console/go

## 9. OpenAI Agents API 五项更新：命令预审、后台压缩、时间感知
新增 **Auto Review**（命令执行前检查潜在不当行为）、异步压缩（压缩在后台进行不阻塞会话）、实验性时间感知（模型能感知时间流逝）、会话中随时更新工具、系统提示跨会话自动缓存。OpenAI 称缓存可省时间和费用。
**影响**：Auto Review 是 agent 安全从“事后拦截”转向“执行前审批”的信号；时间感知则直接针对长期运行 agent 的老问题：模型不知道自己已经跑了多久。
https://x.com/stevendcoffey/status/2116303789649236048

## 10. Qoder 支持局域网内多设备互联、直接分派任务
同一局域网内的桌面端可互相配对，在常用客户端里给笔记本、台式机、手机派任务，**无需配置 SSH 或切换远程桌面**。执行中可看进度、补要求，远端生成的 PPT、Excel 可在当前电脑直接预览；终端、文件、浏览器操作都在目标设备执行，模型选择遵循该设备的可用目录。
**影响**：把“远程开发环境”做成了消费级体验，直接面向“一台机器算力不够、又想随处开工”的个人开发者。相比云端沙箱，本地设备的隐私与文件访问优势更明显。
https://mp.weixin.qq.com/s/4hFWL1RkQ4wWeUzWlddYKg

---

## 其他值得留意（简讯）
- **Google 星载 TPU 回传首个 AI 回复**：Project Suncatcher 原型卫星上的 TPU 跑通 Gemma 4 并生成俳句回传，计划 2027 年发射两颗卫星测试跨卫星分布式计算。象征意义大于实用价值，但“太空数据中心”从 PPT 走到了在轨验证。https://blog.google/innovation-and-ai/models-and-research/google-research/project-suncatcher-satellite-response/
- **Grok 4.8 推迟**：马斯克承认耗时超预期，称未针对基准优化、“不在意跑分，只在意实用性”，未给发布时间。https://x.com/elonmusk/status/2116036703538606301
- **Claude Code 加入“禁止重制他人游戏”规则**：提示词层面限制 Opus 5.5 复刻特定现有游戏，原创与同类型游戏仍可做。属于 IP 合规的预防性收紧。https://x.com/addyosmani/status/2116213240363729013
- **OpenAI 社区安全报告**：承诺 2027 年初发首期（覆盖 2026 下半年），此后半年一更；未来几周 ChatGPT 将限制向青少年提供可用于暴力的武器/安防实用信息，并在出现暴力执着迹象时终止对话。

*已标记本期为已读。*
