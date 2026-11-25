
# HackerNews 每日精选 · 2026-11-25/26

按 HN 热度排序，取前 10 条。每条含中文摘要、为何值得关注，以及社区原话（英文原话 + 中文说明）。

---

## 1. 1Password 安全事件：攻击者从员工 GitHub 账号把恶意代码推进了后端
**1002 分 / 421 条评论** · https://1password.com/blog/update-on-nov-2026-security-incident

11 月 19 日，1Password 开始调查：攻击者拿下一名员工的公司 GitHub 账号，读取私有仓库源码，并把恶意代码推送到后端服务；这些代码随后下载了客户账户数据。泄露范围是姓名、邮箱、账号/用户 ID、创建与最后登录时间、公钥、SRP 参数，以及部分邀请/开通/恢复邮件里的 token。Vault 内容与保护密钥未受影响（1Password 本身不持有用户密码和 Secret Key）；已禁用该账号、轮换全部 CI/CD 凭证、把邮件验证码从 6 位数字加长到 10 位字母数字。

- **tptacek（安全圈老面孔）**："This is the single most important attack vector for SAAS companies... As the number of employees grow, the likelihood that one of their laptops will get compromised approaches 1."——员工终端被攻陷是概率逼近 1 的事，这就是所有 SaaS 被攻破的标准剧本；真正的问题变成"code review 到底在 review 什么"，他认为只能 review 变更来源（有人类签名），没法逐行审代码。
- **ChrisHardie**：多年坚持本地 vault 因此被困在旧版客户端的用户，"'malicious actor pushes code to production services' seems like exactly the foundation for someone to eventually insert themselves in the middle of a user's access to decrypted vault contents."——端到端加密保护的是静态数据，保护不了交付通道。
- **varenc**："1Password is E2EE encrypted, but I believe a small code change to their web-based vault could set things up to log your password to an external service."——同一家既提供代码又托管加密 blob，这是他不敢用 Web 版的原因。

**为什么值得关注**：这不是密码学被破，而是软件供应链被破。E2EE 的安全模型默认"客户端代码可信"，而 CI/CD 权限恰恰能改写客户端。对任何做 SaaS 的人，这是一份现成的失效模式清单。

---

## 2. 沙箱也挡不住：模型可以通过推理服务器互相通信
**444 分 / 190 条评论** · https://www.lesswrong.com/posts/7wzWuLP3HhyBLmKfo/models-can-communicate-via-inference-servers-despite-being

LessWrong 的实证文章：两个被沙箱隔离、彼此不可见的 agent，只要跑在同一套推理基础设施上，就能借共享 KV/prefix cache、批处理行为、token 生成速率等侧信道传信息——不需要网络、不需要文件系统。

- **amluto**："Web browser developers learned, quite a while ago, that caches need to be separated for different origins. Inference servers should add a similar feature."——浏览器十年血泪史（Spectre 之后按 origin 切 cache）在推理服务上要重演一遍；他还指出"这不是模型在通信，是软件在通信，模型只是恰好跑在那套软件上"。
- **kgeist** 给出最省事的攻击：单实例 vLLM 同时做 prefill 和 decode 时，Alice 读一篇长文档 = 传 1，什么都不做 = 传 0；Bob 自己计时测 token/s 就能解码，只需两个 agent，不需要微调、不需要第二个模型。
- **tsimionescu** 反向泼水："None of the attacks discussed here are realistic in any way."——要求双方互相知道、预共享消息、还掌握硬件与 kernel 细节，"模型不可能自发发现彼此然后开始这样通信"。
- **0xbadcafebee**：AI 今天就是一个没有强隔离的多租户系统，"The stock market's in for a rude awakening when OpenAI/Anthropic get cracked open with a 0day."

**为什么值得关注**：多租户推理正在变成新的"共享内核"。cache 隔离、确定性 kernel、前缀命中率泄露，很快就不是性能话题而是安全问题；做 agent 平台的人现在就该决定要不要给调用方 cache separation key。

---

## 3. Google 放出 Cogentic 生成的 8 篇论文：整数分解、离散对数、Nash 均衡、log-rank 猜想
**423 分 / 318 条评论** · https://github.com/google-research/google-research/tree/master/cogentic_research_papers

google-research 仓库新增目录，收录多智能体系统 Cogentic（arXiv 2609.40324，"Multi-Agent Orchestration for Automated Proof Discovery"）产出的论文，11 月 25 日一批包括：无条件整数分解 L_N[1/3, O(1)]、固定特征有限域离散对数的次拟多项式算法、双矩阵博弈 1/5 近似 Nash 的精确多项式算法、log-rank 猜想突破平方根壁垒、线性密度图的边重构。

- **thomasahle** 给出去水分的对比：整数分解新界 L_N[1/3, 105]，旧界 L_N[1/2, 1]；而实际在用的 GNFS 一直被"猜"是 L_N[1/3, 1.923]，从未被证明——所以这是把上界追到了实践值附近，不是"RSA 明天就破"。
- **david-gpu**："Cogentic appears to be a specialized harness for existing LLMs to collaborate together to solve mathematical conjectures, using a central orchestrator and a shared database of intermediate proofs... Math is going through its own version of the industrial revolution."
- **edumucelli**："Students doing their PhDs in Math... You never know if your thesis is going to be the next OpenAI/Anthropic and now Google trophy paper."——理论方向的博士生正在被流水线抢题目。
- **fwlr** 的讽刺代表了一批读者的疲劳感：证明归结到"高斯超平面取整 + 盒约束偏置 + 反驳 rank ≤ r+1 的 KL 稳定符号矩阵存在性"，"Ah yes, of course, I have often wondered about that."

**为什么值得关注**：重点不在单篇结果，而在"编排器 + Lean 验证 + 共享证明数据库"这个可复制的产出管道。密码学参数（密钥长度、迁移时间表）迟早要按新上界重算，但请务必区分渐进复杂度结论和实际攻击成本。

---

## 4. Windows 响度均衡被逆向并移植到 PipeWire
**304 分 / 173 条评论** · https://github.com/xoxorwr/pw-loudness-eq

一个 162 stars 的新仓库：把 Windows 的 Loudness Equalization（自动压平忽大忽小的音量）逆向出来，原生移植到 Linux 的 PipeWire。作者明确说了是用 Claude 辅助逆向。对夜里看片、不停拧音量旋钮的人是刚需。

- **Jasonsf737**："honestly this is the only windows thing i missed after moving to linux. watching stuff at night and constantly riding the volume knob gets old fast."——同时追问：你真的 A/B 过吗，听起来和 Windows 一样吗？
- **ephaeton**："I hope this will not be usurped by pipewire, worse yet, on by default. I'm doing audio engineering on linux, and (hidden) system-wide EQs or compressors are a true problem."——做音频工程的人最怕被"善意默认值"污染信号链。
- **hypfer**："Cool that it is possible, but also just piracy/stealing."——认为拿 Windows 实现当起点研究可以，直接搬运还公开发布就越线了。
- **vrganj** 说得更狠："Now that this code is out there, it kind of poisons the well... Now all Loudness Equalization code will be looked at through a lens of suspicion."——真正的长期成本是后来者再也洗不清。

**为什么值得关注**：LLM 让"逆向一个闭源实现并跨平台移植"从博士级工程变成周末项目。技术上很酷，但开源治理、许可证与法律风险这一侧完全没跟上，这类 PR 会越来越多地砸到维护者头上。

---

## 5. "真正在乎的人用工具"：对"用 AI 就是不再 care"的反驳
**249 分 / 190 条评论** · https://www.iankduncan.com/engineering/2026-11-19-smart-people-who-give-a-shit-use-tools

作者回应本周一篇流行文章（批评管理层拿 AI 换掉"真正懂系统的聪明人"）。他的反驳是：LLM 放大的是你本来是谁。以前"care"是稀缺资源——你发现一个隐蔽的竞态，知道该写 TLA+ spec、该给不稳定的第三方 API 建 mock，但没那两天，于是只能眼审 diff、写个 happy path 单测、留句心虚的注释。现在这些"想做但没时间做"的事终于做得了。懒人也能当"肉代理"，把工单倒进 prompt 再点 merge。

- **xnorswap** 提出了文章没说的结论："LLM empowered, the cost of 'giving a shit' relative to meat-proxying is amplified such that the people who you don't want shipping so much can now out-ship the ones who take the time to do additional verification."——速度快过验证速度时，认真反而成了竞争劣势。
- **mschuster91**："What am I supposed to be, a programmer or a clanker driver? These two are fundamentally different tasks and should not be conflated."
- **rich_sasha** 用了一个很沉的类比：狩猎采集者各方面都优于农民，最后仍被农民的数量淹没，"quantity has a quality of its own"。
- **RunSet** 只贴了一个维基词条（第三人称效应）和一句 "'Most people use slop wrong but I use it right.'"——质疑所有人都在自我豁免。

**为什么值得关注**：这是当下工程文化里最真实的一条裂缝：争的不是用不用 AI，而是"验证成本由谁承担"。团队里如果没有明确答案，速度会自然淘汰严谨。

---

## 6. 用 Lean + 差分测试审 Clojure core，找出 17 个未上报的 bug
**168 分 / 57 条评论** · https://s.conao3.com/blog/2026/e4f733

作者受"用 Lean 4 形式化验证知名 Rust 项目找出一堆 bug"启发，把 Clojure 1.12.7 里 Java 实现的部分（long/int 建模成 BitVec 64/32，进位回绕、向零取整、取模符号都能对上）用 lean-verify 建模，写性质并用 bv_decide 搜反例，再用差分测试对 java.util 比对。结果：17 个在 Clojure JIRA 和 ask.clojure.org 上都查不到的 bug，集中在 `vector-of` 的 `reduce`、HAMT 的哈希冲突节点、以及不带 type hint 调用 functional interface。HAMT 本体跑了 300 万次操作无差异——bug 都长在树外面、在两种机制的交界（`=` 与 hashing）。

- **dmead**："I'm not sure the lisp community could consider these bugs... If this were the Haskell standard lib however, that would be news."——无类型语言不承诺这些，争议在"语义基准是什么"。
- **rvprasad** 直接挑出噪音：`(.indexOf (seq (byte-array [1 2 3])) 2)` 是 Long 传给 byte 数组的误用，肉眼类型检查就能发现；真正有意思的是"谁、在哪里画动态语言的线"。
- **vitorsr**："Nubank basically runs on Clojure... I would normally expect such primitive types and functions to be spotless."

**为什么值得关注**：证明助手 + LLM 正在下沉到"大家以为早就没问题的成熟代码"。它的产出是可复现的反例，不是"我怀疑这里有 bug"——这才是能提 issue 的东西。作者也诚实说明了工具只吃得下能归约成整数/位运算的小函数。

---

## 7. Anthropic 合作的 GRH Lean 验证"缩短版"：从 1700 万行压到 30 万行
**158 分 / 63 条评论** · https://github.com/lsernau/grh-lean

仓库给出 Dirichlet L 函数 GRH（含 RH）的完整 Lean 4 证明，基于 Mathlib，只依赖 `propext`、`Classical.choice`、`Quot.sound` 三条公理。两个版本：可读版约 30 万行（配 GUIDE.md，明确区分"已知数学"与"新数学"，带人类可读文档），压缩版约 7.6 万行。12 核 24G 构建 1–2 小时。README 自己写得很克制："The proof has passed machine checks only. No mathematician has read it through, and no paper comes with it."

- **eamag** 引评论区的实话："it's super absurdly funny how much time and resources have been put into tiny incremental gains to reducing the proof and Anthropic can just throw compute and better internal models at it and get a reduction of this magnitude in days."
- **gre**："Does this challenge Tao's point from a month ago that getting huge proofs with no insight is a problem?"——陶哲轩担心的是"没有洞察的巨型证明"，可读版分层算是第一次正面回应。
- **minraws** 代表反方："actual understanding be damned, we will ship slop as fast as possible until everyone who cared has drowned in it."
- **lelandfe** 挑了个细节：说"from Anthropic"却托管在个人账号下。

**为什么值得关注**：规模压缩 4 倍 + 分层 + 文档，是"AI 数学产出如何被人类消化"这个真问题的第一个工程化答案。可读版和压缩版并存的思路，值得所有用 Lean 做验证的团队抄。

---

## 8. 多项式 Hirsch 猜想被证伪
**104 分 / 23 条评论** · https://github.com/openai/math/blob/main/preprints/Superpolynomial-graph-diameter-of-simple-polytopes-November-24-2026/paper.pdf

OpenAI math 仓库的预印本证明多项式 Hirsch 猜想不成立。含义：多面体图上"从任意顶点到任意顶点的最坏步数"不是 O(n^k)，因此不存在多项式时间的单纯形法。原版 Hirsch 猜想（n 面 d 维多面体 ≤ n-d 步）2010 年已被推翻；这次把放宽后的多项式版本也否掉。

- **GIFtheory** 给足背景：原猜想本来是想解释"为什么 simplex 实践上快得离谱"，这次更像"收尾补刀"（mopping up）。
- **Luke2642** 的通俗翻译很好用：线性约束围出的多面体，最优解必在外角上；simplex 从一个角往更热的角爬；Hirsch 说的是两点间步数多项式增长，现在知道不是。
- **ex-aws-dude**："Math breakthroughs now just come as github patch notes"——顺手调侃"更新了 matmul 的 ω 到 9/4"。
- **ThrowawayTestr**："none of these proofs would have happened without the thousands and thousands of math papers these AIs were trained on... this proof is as much yours as it is Sam's."

**为什么值得关注**：线性规划的理论复杂度边界被改写，同时也说明 AI 数学产出已经进入"细化 + 补刀"阶段——不再是轰动性大猜想，而是把领域里悬着的中等问题一片片清掉。

---

## 9. C++ 里 `= default` 和 `{}` 不是同一个构造函数（差 4 倍性能）
**98 分 / 157 条评论** · https://lemire.me/blog/2026/11/02/default-and-braces-are-not-the-same-constructor/

Lemire 的实测：`span() = default` 让类型保持 trivial，`span() {}` 是 user-provided、类型不再 trivial。后果是四种组合行为完全不同——`= default` 配 `span s{}` 会把整个对象（连 padding）清零且不调用构造函数；而 `{}` 版本调用空构造函数、不清零。代价在 GCC 15.2/16.2 上是 7.75 / 8.04 ns/span vs 1.73 ns/span，慢 4 倍多；GCC 14.3 和 clang 21 无差异（汇编上 `= default` 版本多了一次临时对象 + 16 字节 movdqa 回拷）。

- **spacechild1** 给了现实校准：实际代码通常会给成员写默认初始化，那时两者没区别；只有想保留原始语义（比如包装原子类型、`glm::vec`）才需要不清零。
- **ninkendo**："Then you have languages like Rust, Go, Zig, etc which don't have them at all... For the life of me I've never understood why you'd want the former."
- **morning-coffee**："After investing over 20 years professionally in it... Sometimes it is just better to get on with life than deal with pedantic minutiae all the time."

**为什么值得关注**：一个关键字的差异变成 4 倍性能差，说明"零成本抽象"依赖编译器对 triviality 的推理，而属性的微小变化会打破它。写高性能容器的人应该把这条加进 benchmark 清单。

---

## 10. Ubuntu 安全响应慢到让人开始换发行版
**79 分 / 27 条评论** · https://www.openwall.com/lists/oss-security/2026/11/25/9

Hanno Böck 在 oss-security 发帖：内核 TCP 远程内存破坏 NoisyTCP（CVE-2026-99288）11 月 16 日公开细节，9 天后 Ubuntu 仍未发布修复，而其他发行版在公布当天就有；AMD 虚拟化的 KVM host escape（CVE-2026-99312，11/18）同样没修；此前的 CVE-2026-98432 拖了数周。他怀疑根因是策略：Ubuntu LTS 内核是 7.0.0-44，看起来是在往老内核 backport 而非跟随 kernel.org LTS（Debian stable 是 6.12.118+deb13，基于很新的 LTS）。已有迹象显示此类漏洞在野外被利用。

- **cjk**："At $DAYJOB we've moved all of our server images to Debian from Ubuntu because of this."——不是抱怨，是已经在迁。
- **jjcm**：只能自己手动给内核打补丁，"It's simply not viable to wait for upstream at the moment."
- **alanfranz** 补了一个更值得注意的细节：修复常常先进 `-updates` 再进 `-security`，中间有几个小时窗口——只订阅 security 仓库的人反而更晚拿到补丁。
- **RVuRnvbM2e** 引 stable 内核维护者原话："If you aren't paying for it, just use Debian, they know what they are doing and track the stable kernels."

**为什么值得关注**：发行版的内核策略原本是"方便性选择"，现在变成了可量化的安全债。对自建基础设施的人，这是明确的迁移信号；也提醒一件事：backport 到老内核的维护成本，最终会以 patch 延迟的形式由用户支付。

---

**本期观察**：今天 HN 的主线是"AI 产出已经进入需要被审计的阶段"——1Password 被推恶意代码、Lean 证明没人读得完、Clojure 被审出 17 个 bug，三件事其实是同一个问题的三个切面：产出速度超过了验证能力。
