
# HackerNews 每日精选 · 2026-09-22

来源：HN 首页热度榜（抓取 20 条新帖，去重后取前 10 + 4 条附加）。所有评论为用户原话（英文）+ 中文说明。

---

## 1. Claude Opus 5.5 发布｜1077 分 / 759 评
**摘要**：Anthropic 发布 Claude 5.5 家族首个模型 Opus 5.5，称其在多数工作上达到上一代旗舰 Fable 5.1 的水平，运行成本比 Opus 5 低 40%。输入 $4 / 输出 $20 每百万 token，缓存读取 $0.20（比 Opus 5 便宜 60%），输出速度提升 30% 以上。官方称它拿下了自家对齐审计（自动化行为审计）的历史最高分，更不容易执行"难以撤回"的操作，抗提示注入能力也更强。有测试者用它在一天内完成了 68 万行代码迁移。
**为什么关注**：这是 Anthropic 公开"呼吁放缓前沿"之后的首个发布，也是用"更便宜 + 更安全"双重话术巩固企业客户的典型动作。
**原帖**：https://www.anthropic.com/claude-opus-5-5
**评论原声**：
- `throwaway2027`："After yesterday outage is the new Opus 5.5 load-bearing?"（昨天刚宕机，新的 Opus 5.5 是承重墙吗？）—— 这一问引出了一整串**模仿 AI 话术的玩梗接力**：`handfuloflight`"这值得说明原因，取决于你现在拉的是哪道缝"、`staticman2`"我跟你说实话——我没有证据说它是不是承重墙"、`danw1979`"你说得对，但我要温和地反对一下：这不是宕机，是服务降级"。社区用这种方式吐槽模型输出越来越模板化、过度认同。

---

## 2. GPT-6 Sol 和 Luna 发布，价格直接腰斩｜1040 分 / 547 评
**摘要**：OpenAI 发布 GPT-6 Sol 与 Luna，相对 5.6 代价格直降 50%：Sol 输入 $4→$2、输出 $20→$10；Luna 输入 $0.20→$0.10、输出 $1.20→$0.50。同一天 Anthropic 发 Opus 5.5，两家正面撞车。据评论整理的价格对比，Luna 的单价已经低于 DeepSeek 4.1 flash。
**为什么关注**：头部两家在 24 小时内同时降价，API 单价被打到"便宜到无法计量"的区间，应用层成本假设需要重算。
**原帖**：https://openai.com/index/introducing-gpt-6-sol-and-luna/
**评论原声**：
- `Cu3PO42`："GPT-6 Luna at $0.10/Mio input tokens and $0.50/Mio output is positively insane."（疯狂的价格）但他补了一句：公告完全没提 Azure 或 AWS 上的可用时间。
- `recitedropper`（后被 flag）："This is the most blatantly astroturfed thread I have ever seen on Hacker News."（这是我见过最明显的刷帖）—— 他给出的证据是"发布不到 1 小时、26 分钟内 89 条评论、瞬间顶到第一，且正好在 Opus 5.5 公告后一小时内"。这条内部争议本身值得留意。
- `GodelNumbering`："GPT-6 Luna 比 DeepSeek 4.1 flash 还便宜，今天在智能/价格比上真是疯狂的一天。"
- `m_fayer`："5.6 Sol 是我的甜点区……它是我第一个产生依附感的模型。而这让我在职业上对两个实验室感到非常脆弱。"（对模型换代焦虑的真实原声）

---

## 3. 苹果往 iOS 设置里塞"常驻广告"，用户炸了｜569 分 / 430 评
**摘要**：TechRadar 报道 iOS 设置 App 顶部出现推广位，推销 iCloud+ 存储、Apple Music / Apple TV 免费试用和 AppleCare+。多数横幅没有"关闭"按钮，只能等它自己过期（可能几周甚至几个月），期间设置图标一直挂着通知红点；即使有"关闭"，也有用户反馈点了没用。Maps 插广告的余怒尚未平息，这次反应更激烈。
**为什么关注**：硬件公司用系统级提示位做订阅转化，是"服务收入优先"最直白的体现，也是 App Store 广告生态问题的延伸。
**原帖**：https://www.techradar.com/phones/iphone/i-wish-apple-would-just-stop-that-crap-apple-has-added-persistent-ads-to-ios-and-its-driving-users-crazy
**评论原声**：
- `busymom0`（小开发者）："用户搜我的 App 全名，苹果在上面塞两个全屏广告，有时搜索结果被夹在两个广告中间，用户直接划过去了……而且没有'不再显示此广告'的按钮。"他还说 App 名必须唯一，但搜唯一名也搜不到自己。
- `mikeyouse`："搜'Wordle'都不能保证 Wordle 排第一，这是对整个靠广告支撑的互联网的控诉。"（换成 Claude、Discord 也一样）
- `tensor`："我要的是搜索结果，不是一屏、甚至两屏的广告。简直烂透了。"

---

## 4. GPT-6 Astra 自主破解了 2005 年以来无人破的 Enigma 密电｜530 分 / 353 评
**摘要**：Crypto Cellar 公布，研究者 Carter Leffer 只让 GPT-6 Astra"看看能不能破未解密的 Enigma 密文"。模型自己选出 1941 年 7 月 10 日的 MVUEH 电报，怀疑它与已破解的 173 号电报正文相关，用重复地名 ROSENOW 作 crib，自行编写 Python/C++ 的 Enigma 模拟器和 Bombe 开始系统性穷举，最终得到正确密钥与明文。它还自己去查了德国联邦档案馆的档案目录线索（RS 3-3/20a、RS 3-3/63b）。原文称"它在两天内做到的，人类要花很久"。
**为什么关注**：第一个公开的"模型自主完成完整密码分析工作流"案例——找目标、找关联、写工具、跑穷举、验证，全程无人工引导。
**原帖**：https://www.cryptocellar.org/bgac/the-mvueh-break.html
**评论原声**：
- `saberience`："这类的'新闻'还要来多少？它不需要技巧、不需要想象力，看起来就是碰运气。我们进入了一个无名之辈指挥模型去做被遗忘的任务、然后收获 15 分钟不应得关注的时代。"
- `mossTechnician`："人靠运气发明东西仍然有趣；一台机器用未公开的时长和费用跑循环，去解决一个没人关心的问题，那更像公关。"
- `pixl97` 反驳："现在有一台机器能解决那些'因为没有足够多懂行的人'而一直没解决的问题，我们只要供电就能拿到答案——非理性的恨让人盲目。"

---

## 5. 五角大楼：对 AI 的过度依赖导致了伊朗学校被导弹击中｜334 分 / 173 评
**摘要**：彭博一项未公开的调查报告（原文标注"unreleased Pentagon probe"）指出，美军对 AI 辅助目标决策的过度依赖，是伊朗一所学校遭导弹打击的成因之一。HN 讨论几乎全部集中在责任归属上，而非技术细节。
**为什么关注**："AI 参与致命决策"从假设题变成了追责案例，而这正是各家 AI 公司安全叙事里最难回答的一块。
**原帖**：https://www.bloomberg.com/graphics/2026-iran-school-attack/
**评论原声**：
- `colingauvin`："AI can't be tried in a court. There has to be a responsible human for every one of its actions, especially when it's killing children. I cannot believe this has come to pass."（AI 不能上法庭，它每个动作背后必须有一个负责的人，尤其是杀害儿童的时候。我不敢相信事情已经到了这一步。）
- `derektank`："反对'扣扳机的人负责'。在空袭/导弹/炮击中，操作员可能根本看不到目标，只是输入指挥中心给的目标信息。这些是分布式责任的社会性决策。而讽刺的是，正是识别并预防这类灾难的 Civilian Protection Center of Excellence 被本届政府关掉且没有替代。"
- `esseph`："扣扳机的人往往不是做目标选择的人，尤其在'战斧'这类战略武器上，他们拿到的只是预先编程的目标数据包。"

---

## 6. 黑客称拿到 FBI 全员数据：PeopleSoft 零日 + AWS GovCloud｜290 分 / 198 评
**摘要**：ShinyHunters 向 404 Media 声称利用 Oracle PeopleSoft 的零日漏洞进入 AWS GovCloud 服务器，窃取 2–3 TB 数据，覆盖"所有 FBI 在职、离职员工和申请人"，并展示了 5000 人样本（姓名、住址、电话、出生日期，部分含配偶信息）。404 Media 用 OSINT 工具交叉验证部分电话确实对应同名人员，且关联到司法部人员。FBI 招聘网站被挂上"已被 ShinyHunters 接管"，官方回应称"已知悉并正在调查"。该组织称这不是为了钱，"或许叫胁迫更合适"。
**为什么关注**：政府承包商软件栈的纵深风险，加上数据经纪人时代的身份泄露放大效应——同一份数据在别处也许只是"公开信息"，在这里却能威胁执法人员和其家人的安全。
**原帖**：https://www.404media.co/we-hacked-the-fbi-hackers-say-they-have-data-on-all-fbi-employees/
**评论原声**：
- `smalltorch`："如果攻击者还在网内、你又谁都不能信，这种协调该怎么做？"
- `lenerdenator`反问："如果目标只是让 FBI 员工感到脆弱——泄露样本就是这意思——那用社交媒体和数据经纪商的数据大概也能做到差不多的事。" `smalltorch` 回：公开数据经纪商可不会给你一份探员的完整名册，泄露身份会危及整个卧底调查。
- `nateb2022`："大公司都有无能的地方，PeopleSoft 也不是以现代化或安全著称的东西。以后减少依赖这类第三方软件是好事。"

---

## 7. 《OpenAI 很可能会抄掉 Jev 的午饭》｜247 分 / 182 评
**摘要**：Arcturus Labs 的分析认为，TypeSafe 的 Jev 本质上仍是 LLM：给出一个输入和一组问题，取下一步 token 的概率分布，把 logprobs 归一化成 true/false 概率或选项分布。而 OpenAI 从 tool calling 时代起就在把 LLM 当隐式分类器用（`to=function` 本身就是一次分类），因此它完全有能力快速跟进，还能把"通用分类"直接折进自家模型和 agent 里，用于模型选择、更高效的思考、安全护栏。作者判断真正的护城河在 TypeSafe 的训练数据与流程。
**为什么关注**：一个拆得很细的"模型公司会不会顺手吃掉应用层"样本，对做 AI 应用的人是直接的策略输入。
**原帖**：https://arcturus-labs.com/blog/2026/09/21/will-openai-eat-jevs-lunch/
**评论原声**：
- `HarHarVeryFunny`归纳 Jev 的三个优势："便宜快，一次输入带多个候选分类、输入计算被共享；原生结构化输出；概率经过校准、真正有意义。" 最后一句是重点："AI 公司得决定自己是在卖智能/token，还是在做应用、跟自己的客户竞争。"
- `alex_sf`泼冷水："纠正一下——它保证的是'格式'固定，不是'答案正确'。用语法约束（grammars）在任何 LLM 上都能做到类似效果，大家似乎都忘了 grammars 的存在。"
- 另有一条十余层的长串，是两人为"训练数据到底重不重要"吵架（`danielmarkbruce` vs `verdverm`），最后升级到"你根本没跑过这两个训练步骤，你在挥手瞎说"。

---

## 8. 2027 年很可能有预装 GrapheneOS 的手机开卖｜241 分 / 103 评
**摘要**：GrapheneOS 官方账号称，2027 年出现预装该系统的在售设备"可能性很高"。HN 讨论的落点是摩托罗拉即将在骁龙峰会上发布的 Signature 27——硬件几乎全面胜过 Pixel 11 Pro XL，价格在 1300 美元级别，且摩托罗拉美国社交账号已有预热。
**为什么关注**：隐私增强系统长期被"只有 Pixel 支持"锁死，这是第一次出现真正的 OEM 意愿信号，会直接影响隐私手机的可及性。
**原帖**：https://grapheneos.social/@GrapheneOS/117299954135808210
**评论原声**：
- `Cider9986`："2026 款 Signature 英国卖 1460 美元、巴西 1230 美元，Pixel 11 Pro XL 官网 1300 美元——如果 Motorola 真在美国卖并支持 GrapheneOS，这事很有看头。"
- `drnick1`："Pixel a 系列就是那个中端甜点，而且目前只有 Pixel 被 GrapheneOS 支持。"
- `armadyl`："这更多取决于高通。悲观一点看，他们为了利润最大化会把安全特性锁在高端芯片上。"

---

## 9. Artificial Analysis 的 Opus 5.5 评测：每任务成本约减半｜212 分 / 61 评
**摘要**：第三方评测机构 Artificial Analysis 给出 Opus 5.5 的智能/性能/价格分析。在与 Opus 5 同为 high reasoning effort 的设置下，每个任务的成本约为一半，完成时间也约为一半。
**为什么关注**：模型之间原始能力的差距已经小到必须看"每任务成本 + 耗时"这类综合指标才有决策意义；这也是企业换模型的真实依据。
**原帖**：https://artificialanalysis.ai/models/claude-opus-5-5
**评论原声**：
- `breckenedge`（最值得注意的一条）："这些评测会在几周后重跑吗？我在自己的数据集上重测，发现 Sol 已经退化到和 Luna 一样。只是一次运行，但我越来越担心模型方先证明自己最强、用户切换、然后收网。"
- `echelon`回："这些测试需要持续采样。而且测试应该随机化，确保模型没有背答案。" `mnicky` 补充了 Margin Labs 的退化追踪器。
- `user43928`："Astra High 每任务 $1.73，Opus 5.5 是 $1.82，很接近。"
- `makeavish`："AA 默认只显示 max effort，我差点以为它是烧 token 机器，切到 high 才正常。"

---

## 10. AMD Ryzen 两年快了 50%，靠的是什么？｜175 分 / 56 评
**摘要**：Daniel Lemire 注意到两代 Ryzen 之间单核成绩提升约 50%（跨度两年），但最高加速频率只涨了约 15%，于是追问"为什么"。读者给出的答案集中在三点：基础频率提升与散热改善（X3D 系列把缓存从一侧移到另一侧，让主要热源更贴近散热器，减少降频）、更小制程带来电压/功耗余量、以及对 Geekbench 分数本身是否被 AVX/加密扩展拉高的怀疑。
**为什么关注**：一条务实的"性能到底从哪来"复盘——也提醒不要用单一 benchmark 的增量去估算代际收益。
**原帖**：https://lemire.me/blog/2026/09/18/how-did-amd-ryzen-get-50-faster-in-two-years/
**评论原声**：
- `nly`："最高加速只涨 15%，基础频率却涨了 38%——更好的散热？更少降频？"
- `kasabali`："制程更小，全核负载时频率空间更大。另外要小心 Geekbench——随着版本号增长它越来越偏袒 AVX、加密扩展这类专用指令集。"
- `kristianp`修正了前提："两年听着很快，其实是因为两代的 3D 缓存型号发布时间错开。Zen 3 桌面首发 2020 年 11 月，Zen 5 桌面首发 2024 年 8 月，实际差约 4 年。"

---

## 附加短讯（同样在榜，价值偏窄或偏技术）

- **WordPress 未授权路径穿越可致条件性 RCE**（146 分）— 需要 pearcmd.php 存在且 register_argc_argv 开启（官方 PHP Docker 镜像默认如此），再叠加部分主题里未净化的 `get_page_template`。有意思的是讨论焦点变成 CVSS 本身：`tptacek`"这些 CVSS 分数没有任何意义，最好别再出现在标题里" vs `vntok`"你不该把 base score 当终端结论，业界就是不读规范"。链接：https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-7hp8-65ch-5whp
- **SAML: A fractal of bad design**（124 分）— Trail of Bits 的新一篇经典批评。企业侧的反驳非常现实，`ocdtrekkie`："如果不支持 SAML，我就去找支持的产品。"另一位 SaaS 侧的人吐槽，对接方常常是被摊派这个活、且离决策层四级远。链接：https://blog.trailofbits.com/2026/09/21/saml-a-fractal-of-bad-design/
- **微软 2007 年砍掉 FoxPro，现在有人把它复活了**（121 分）— 作者用 Rust 写了个 WASM 运行时，对照真的 `vfp9.exe` 校验，表突破 2GB 限制、老 32 位 `.fll` 插件仍可加载，顺带加了 lambda/JSON/HTTP server。作者自述动机："客户想把他 20 年的生意继续做下去。"链接：https://foxscript.org/
- **Unreal Agent**（107 分）— 把 agent 工具调用做成异步的 harness，声称减少等待期间的 token 浪费。作者在评论里承认标题图的对比口径不一致、会改。有用户顺手给出 Codex 的 `~/.codex/config.toml` 配置来抑制无意义轮询。链接：https://unreallabs.ai/blog/unreal-agent/

---

**一句话观察**：今天 HN 的叙事被两家实验室的发布会彻底占满（前两名合计 2117 分），但最有信息量的并不是模型参数，而是三条与能力无关的声音——用户对模型换代"依附感破裂"的焦虑、对 thread 是否被刷的公开质疑、以及对评测跑完就退化的追踪诉求。这三条合起来，是这轮"能力+降价"竞速里真正的信任缺口。
