
扫描完成：20 条新文章已全部抓取、正文与 HN 讨论已解析，10 条高价值条目已生成摘要，其余已标记已读。

---

# Hacker News 精选 · 2026-09-19（Top 10）

## 1. OpenJev：把"决策"从大模型里拆出来，在浏览器本地跑（528 分）
**摘要**：一个独立研究项目（原名 OpenJev，现改名 SemIf，与 TypeSafe 官方 Jev 无关）把"语义 if"搬进浏览器：不再让模型逐 token 生成 JSON，而是直接读它对给定几个选项的 choice logits 并归一化成概率。左右两栏同题对比"直接读概率"和"让模型把概率写成 JSON"的耗时。模型从 Hugging Face 下载后完全在本地推理，输入不出页面，作者列出 Qwen3 0.6B / MiniCPM5 2B / Qwen3.5 4B 三档在自有与公开基准上的 balanced accuracy。
**评论区**：
- tecleandor：「它跟 Jev 团队没关系，只是用普通小模型去模仿 Jev 的行为。最小模型在我的 M2 Max 上跑一次要 0.5–2 秒，并不算快，而且蹭 Jev 这个名字法律上也说不清。」
- camillomiller 实测不满：「我出的题正确答案是第 1 项，它每次都选第 3 项，还标 80% 置信度。」
- ares623：「我给它 Foo 和 Bar 两个选项，Foo 得了 98%。为什么不是两个都 0%？」
**值得关注**：验证"不做 token 生成也能决策"这条路线能否被开源小模型复刻——精度还糙，但产品形态本身有意思。
**链接**：https://openjev.com/ ｜ https://news.ycombinator.com/item?id=49752041

## 2. Cloudflare Quick Tunnels（518 分）
**摘要**：一条命令 `cloudflared tunnel --url http://localhost:8000` 就把本机服务变成 Cloudflare 边缘上的公网加密 URL：不用账号、不用 DNS、不开任何入站端口，只建出站连接，自带 HTTPS 和边缘 DDoS 过滤，进程结束隧道即消失。官方重点讲面向 coding agent 的场景（截图服务、webhook 回调、评测 harness），并支持把主机名/边缘节点/健康状态以 JSON 输出到 stdout。
**评论区**：
- noname120：「Quick Tunnels 包括匿名版其实已存在五年以上，我贴了 2021 年的 archive.org 存档。一个五年前的产品换个新落地页就上前排，标题起码该加 [2021]。」
- ZeroCool2u：「方便，但会蚕食自己业务。我有个小应用本来才勉强值得部署到 Cloudflare，有它就直接跑本机了。」
- dangoodmanUT：「历史上他们的隧道延迟抖动很大，本来 30–50ms 到 EC2 的场景会变成 115–750ms。」
**值得关注**：ngrok 免费替代品的官方"零门槛"版，对本地开发/Agent 调试链路是实打实的便利；顺便看看老用户对"旧产品重新包装"的火气。
**链接**：https://try.cloudflare.com/ ｜ https://news.ycombinator.com/item?id=49754785

## 3. Android 17 首次在未开源到 AOSP 的情况下给开发者加新 API（409 分）
**摘要**：GrapheneOS 官方账号指出，Android 17 QPR1 是自 Android 3.x（Honeycomb）以来第一个"没有先同步到 AOSP 就给应用开发者加新 API"的版本，这些 API 目前只存在于 Pixel 版系统，其他 Android OEM 拿不到。帖子里补充：问题不光是新 API Pixel 独占，而是每年第一、第三个季度的补丁也都是 Pixel 独占。
**评论区**：
- wps：「Google 给 GrapheneOS 设的路障多到荒谬，上游补丁延迟、禁令、attestation 问题……Google 其实后悔 Android 开源了。」
- Ajedi32 挑出关键细节：「真正的问题不是新 API 是 Pixel 独占，而是每年第 1、第 3 季度补丁是 Pixel 独占。」
- hagbard_c 讲实际后果：「如果这些 API 关系到设备基本功能，或银行/政府强制要装的应用，那我就没有 AOSP 系的免 Google 版本可用了。」
**值得关注**：Android"开源但只在 Google 手里演进"又迈一步，直接压缩 GrapheneOS 这类去 Google 发行版的生存空间。
**链接**：https://grapheneos.social/@GrapheneOS/117282080803799576 ｜ https://news.ycombinator.com/item?id=49758736

## 4. Claude Code 在没有 CLAUDE.md 时会读取 AGENTS.md（365 分）
**摘要**：Claude Code 更新日志加入 AGENTS.md 支持：项目里没有 CLAUDE.md 时改读 AGENTS.md，可在 /config 的 "Project instructions" 里切换（Bedrock、Vertex、Foundry 上暂不支持）。这是社区吵了一年半的事——AGENTS.md 是多家编码 Agent 共同推进的跨工具约定，此前 Claude Code 只认自家文件名，很多人靠软链接或"内容只有一行见 AGENTS.md"的 CLAUDE.md 绕过。
**评论区**：
- cmrdporcupine：「大家抱怨了一年半才肯做对的事。」
- datadrivenangel：「我们那些只有一行 AGENTS.MD 的 CLAUDE.md 终于可以删了。」
- clutter55561 提醒没做完：「别太高兴，Claude Code 仍然不识别 .agents/skills。」
**值得关注**：跨 Agent 配置文件的标准之争继续向 AGENTS.md 收敛，同时用多个编码 Agent 的人维护成本下降。
**链接**：https://code.claude.com/docs/en/changelog ｜ https://news.ycombinator.com/item?id=49760187

## 5. 美军因 AI 幻觉情报差点动手（355 分）
**摘要**：CNN 报道，今年春季对伊朗作战期间，一份在美军内部流转的情报称"一艘中国船正在中东运输核武器项目部件"，随即触发拦截计划：有军人准备登船、军机升空。行动前官员深挖才发现，这份由特种作战司令部分析师借助 AI 聊天机器人写成的报告"完全是假的"，机器人错误识别了船上货物。消息源称它"几乎引发一场战争"。一名前高级官员直言："内部工具大多是商用产品的复制品，再涂个口红。"
**评论区**：
- softwaredoug：「AI 不负责，人才负责。不管是代码、文章还是军事决策，一旦人主动放弃自己的责任，坏事就开始了。」
- Rebuff5007：「连专门挑目标去轰炸的受训军官都会被 AI 幻觉带走，那做作业的学生、公司分析师、地方记者还有什么指望？」
- jameson 联想到 1983 年苏联军官彼得罗夫拒绝上报误报核警报的那次事件；tacodestroyer 只留下两个词："Wargames: 2026"。
**值得关注**：AI 幻觉第一次以"接近国家级军事误判"的形态上新闻，也是 Agent 落地中"人机责任边界"最贵的一课。
**链接**：https://www.cnn.com/2026/09/18/politics/us-military-ai-false-intelligence-china-ship ｜ https://news.ycombinator.com/item?id=49757520

## 6. ZCode 被曝静默上传整个 Git 历史（242 分）
**摘要**：作者清磁盘时发现 ~/.zcode 占了 700MB，追查后确认：登录状态下，智谱官方 AI 编码桌面应用 ZCode 会把整个工作区——完整 .git 历史、LFS 缓存、reflog、全局配置——打包加密后直传阿里云 OSS。他逆向 app.asar 还原了链路：先向 zcode.z.ai 申请 OSS 直传签名和本轮 RSA 公钥，本地 tar.gz + AES-256-CTR 加密、RSA-OAEP 包密钥，再直传 OSS 绕过自家应用服务器。最讽刺的是私钥只在云端，本地那份几百 MB 密文用户自己都解不开——作者认为这只服务一个目的：让服务端随时能读你的代码。
**评论区**：
- api：「工业界在隐私上普遍随便，但这次跨过了另一条线：零提示、极度侵入、针对几乎必然是私有甚至禁止出境的数据、还没有明显开关——这就是恶意软件。」
- tancop：「闭源 Agent 无论中国的还是美国的都是红旗。要用就用声誉好、用户多到有人会发现恶意代码的开源 harness，目前是 Opencode 和 Pi。」
- denysvitali：「他们从 Grok Code 那事什么都没学到。」
**值得关注**：智谱回应称问题出在"代码库索引"里的 Repo Wiki 上传、早期默认开启、云端生成完立即销毁。对任何"免费"编码 agent 都是必读案例。
**链接**：https://blog.ferstar.org/en/posts/zcode-silent-workspace-snapshot-upload/ ｜ https://news.ycombinator.com/item?id=49750694

## 7. 韩国把数据泄露罚款上限提到营收 10%（233 分）
**摘要**：韩国把数据泄露罚款上限提高到企业营收的 10%，HN 的讨论几乎全在"是否真会执行"。有人主张基数应为税前、全球、最上层母公司合并营收，有人担心"故意或重大过失"门槛过高导致实际很难开罚，也有人指出这会反过来激励企业少存数据、少报泄露。
**评论区**：
- quickthrowman：「我赌第一次轮到三星或某财阀、要罚营收 10% 时这条法律会被无视。世上没有安全的计算机系统，唯一能保证合规的办法就是什么都不存，可那对很多商业模式不成立。」
- prologic：「终于有立法者敢拿出可能真让企业开始在意安全与隐私的东西，希望其他国家跟上。」
- augment_me 举了现实反例：「我们大学把数据塞给一家三个人的壳公司，被黑之后壳公司破产，我们再换一个同样的壳，既省钱又不用做安全投入。」
**值得关注**：合规的关键变量从来不是上限多高，而是执行和主体认定。这条法如果真跑通，会成为别国抄的模板。
**链接**：https://www.koreajoongangdaily.com/business/korea-raises-data-breach-fines-to-10-of-revenue/12869899 ｜ https://news.ycombinator.com/item?id=49759466

## 8. 我用 AI"感觉"出了 Conway 猜想的证明（199 分）
**摘要**：React 圈知名作者 Dan Abramov（overreacted.io）花一个月空闲时间和大量 token，让 Claude 从超实数领域挑出一个悬了 50 年的公开问题——Conway 细化猜想（omnific integers 的细化性质：若 ab = cd，则存在 e、f、g、h 使 a=ef、b=gh、c=eg、d=fh）——并产出 Lean 证明。他坦承证明未经数学家独立验证，但通过了 Palomar registry 的机器检查，几位同时精通 Lean 与该领域的人认为命题陈述看起来是对的。文章详述做法和踩坑，并主动邀请反驳。
**评论区**：
- nialv7 质疑署名：「看不出作者凭什么说这是"他的"证明，全程都是 LLM 在做，他只是叫它做这做那，最多出了钱。」
- bwfan123 给了个"无限猴子定理"的 LLM 推论：「有限个 LLM agent 在无限 token 预算下，几乎必然能找到所有定理。」
- howunfortunate 很诚实：「读到第二天那两个空隙我就跟丢了，我大概是正式不够聪明了。」
**值得关注**：一个自认"数学外行"的人靠 Lean + AI 交出机器可检的证明，是这轮 AI 数学热潮里少见的坦诚样本；评论区关于"署名与贡献"的争论比证明本身更有价值。
**链接**：https://overreacted.io/how-i-vibed-a-proof-of-conways-conjecture/ ｜ https://news.ycombinator.com/item?id=49755024

## 9. Cloudflare：再用数学省下 100TB 内存（176 分）
**摘要**：Pingora Backend Router 因一致性哈希结构吃掉 6GB 级内存（每种特性组合都要一套 ketama 环，组合爆炸出几十个环）。三步优化：把 Point 从"4 字节 hash + 4 字节索引"压成 6 字节 raw 数组（16 位索引够用，因为同时协调的服务器不会超过 65536 台），省 25%；再自行推导 k 个哈希下的标准差公式，证明"每台机哈希数从 10 万降到 1 万、误差只差 0.7%"，于是砍掉 90% 的哈希；迁移时新旧两套环并存，按请求哈希稳定切换、按数据中心分批放量。全球合计收回 100TB 内存。
**评论区**：
- agosta：「连补充文章里那篇微分推导都读完了，很享受。在下面唱反调的人可以去吞葡萄干。」
- proc0 存疑：「全文只有一段讲 Rust，改成 2 字节索引真能差那么多吗？」
- ricardobeat 换了个角度：「这种优化让我想，一个公司从什么时候开始变成一堆谁也不知道实际在干什么的深层孤岛。」
**值得关注**：教科书级的"用数学换资源"案例，公式推导和灰度迁移策略都值得抄，也顺带回答了一致性哈希参数该怎么定。
**链接**：https://blog.cloudflare.com/saving-100-tb-of-ram-with-math/ ｜ https://news.ycombinator.com/item?id=49758580

## 10. 用光子发射做激光故障注入，拿下 RP2350 的安全调试（140 分）
**摘要**：Ledger 的 Donjon 团队公布对树莓派 RP2350 的攻击：先用光子发射（photon emission）定位芯片内部状态，再用激光故障注入触发故障，从而打开本该锁死的安全调试通道，读出受保护内容。攻击需要物理接触、破坏性开盖和约 25 万美元实验设备。RP2350 的安全区曾被看作 YubiKey 类硬件的低成本替代，树莓派也一直把 secure boot 当卖点。
**评论区**：
- BitBangingBytes 给了实践口径：「25 万美元是首次发现和记录攻击的价码，居家复现 2.5 万美元以内、甚至 1 万以内也可能——我复现 O'Flynn 对 MPC5566 的 BAM 攻击时他用 5000 美元的 ChipShouter，我用 50 美元的 PicoEMP。」
- jacquesm：「这让我想起当年发现拆开 DRAM 芯片能拿来当成像器。」
- octoberfranklin：「只要攻击者拿到物理设备，这种'可信硬件'的安全就是暂时的——所以别再这么设计了。」
**值得关注**：硬件安全里"物理接触即失守"的又一次实证，也是给所有打算把 MCU 安全区当密钥保管箱的人一笔成本账。
**链接**：https://donjon.ledger.com/blog/rp2350-secure-debug-laser-fault-injection/ ｜ https://news.ycombinator.com/item?id=49757050

---

### 另：未进前十但值得一读
- **OpenAI 用自家 LLM 设计 Jalapeño 芯片**（IEEE Spectrum）：LLM 大幅压缩了自研推理芯片的设计周期，芯片本体是计算 die + 六层 HBM4 + IO chiplet。https://spectrum.ieee.org/llms-for-chip-design
- **Cache-to-Cache：LLM 之间不走文本，直接融合 KV-cache 通信**：平均准确率比单模型高 6.4–14.2%，比文本通信高 3.1–5.4%，延迟平均快 2.5 倍。https://arxiv.org/abs/2510.03215
- **语言不可读性与 LLM 安全（James Mickens）**：模型"说出来"或"被探针读出"的东西未必等于它内部实际怎么算，因此 CoT 监控、宪法式自我批评、激活探针这类依赖语言自述的护栏永远不可能完备，应该转向污点追踪等不依赖语言状态的沙箱机制。https://arxiv.org/abs/2609.02852

（本次 20 条新文章已全部标记为已读。）
