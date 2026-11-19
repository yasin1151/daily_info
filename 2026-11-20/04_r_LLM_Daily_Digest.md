
# r/LLM 热帖 · 2026-11-20

说明：Reddit 的三个端点与 redlib 公共实例在本机仍然全部不可达（`000`），本期继续走归档接口逐帖取数。r/LLM 这两天相当安静——最近 24 小时全版只检索到 6 条评论、48 小时 23 条，今天新发的帖子几乎全是 0 到 3 条回复，且多为自推项目。下面三条是归档里尚未推送过、讨论质量最高的帖子，均为旧帖补读，按实际回复数如实呈现（每帖 2 条真实发言，部分为楼主本人），不为凑格式补写第三条。赞数是归档快照，可能滞后，不代表真实热度。

---

## 1. 16 GB Mac 上跑完整 Gemma 4 26B：靠逐层「专家热力图」把 80 个专家钉在 GPU 上（10-26 发布，补读）

**摘要：** 有人在 16 GB 的 Mac mini M4 上，用 llama.cpp 插件 Kraits 直接加载 Google 官方的 Gemma 4 26B-A4B 量化文件（QAT Q4_0，14.4 GB），完全不裁剪模型。做法是先测出每一层 128 个专家里哪些在 TypeScript 任务上最常被路由，把最热的 80 个常驻 GPU，其余留在内存，写入过程中完全不读 SSD；换一张热力图，同一个文件就能服务另一类工作。评测是 5 个 TypeScript 任务、每题 8 分，判分只看严格编译是否通过、Jest 测试是否真的跑过，没有人工打分：Gemma 总分 33/40，唯独 Jest 那项只有 2 分，而 GPT-5.4 mini 与 5.5 都是满分，生成速度约 31 tok/s 且全程离线。真正值得看的是路线本身——MoE 的显存墙可以用路由统计去换，而不是一刀切压量化位宽。

**高赞评论：**

- u/Mission-Sir-1614（1赞·归档快照，楼主）："the 122B we tried fails the same task the same way" … "One wrong expectation fails the suite on the correct code" 立场说明：楼主主动拆穿自己的分数，说 2/8 不是模型不会写测试，而是测试夹具里 4 个期望值算错了（例如「保留两位小数」却期望 11.665），连 122B 也栽在同一处；这种把跑分还原成具体失败原因的复盘，比总分更有参考价值。
- u/Tough_Produce1612（1赞·归档快照）："That 2/8 on the Jest suite but perfect everywhere else is such a weird gap" 立场说明：指出「只有 Jest 一项崩、其它全满」的断层很反常，怀疑是提示方式的问题或模型对 mocking 写法有偏好，属于典型的社区质疑顺序——先怀疑评测设计，再怀疑模型能力。

原帖：https://www.reddit.com/r/LLM/comments/1xfuh5e/

---

## 2. 给 agent 划「会话意图」和「读取预算」：静态白名单为什么拦不住合规范围内的滥用（10-12 发布，补读）

**摘要：** 一个做 agent 运行时的人提出，真正的滥用发生在白名单内部：agent 反复扫敏感读接口直到把预算耗尽，或者读完敏感状态立刻发一个外呼请求，每一次单看都合法，静态 allowlist 因为「逐个调用都有效」而完全拦不住。他在本地运行时里试了两层控制：一是会话级意图信封，把 allowed_tools 与 denied_tools 在 /session 时由宿主声明，网关在执行前逐次校验；二是读取预算，对敏感工具设量级和速率阈值，越线后决策从放行自动升级为需人工批准或直接阻断。作者自己划了边界：这不是提示词过滤，也不是企业级安全方案，只是启发式阈值，绕过方式肯定存在。对做 agent 平台的人来说，「边界 + 预算 + 升级审批」这套组合比单点权限更接近可落地形态。

**高赞评论：**

- u/rainy_contentment（2赞·归档快照）："Static allowlists are like checking someone's ID at the door and then never looking at them again." … "Agents will happily spin in circles if nothing stops them, and a hard cap with a human tap on the shoulder beats discovering a drained budget three hours later." 立场说明：用门卫比喻点出静态白名单的盲区，并认为把读取预算接到人工审批才是实战里最有用的一环，因为 agent 没有刹车就会一直转圈，事后才发现预算被打空已经太晚。
- u/GameChacking（1赞·归档快照，楼主）："Session intent is declared upfront by the host on /session, not inferred. Verify is server-side and ignores client intent" 立场说明：楼主回答最关键的设计问题——意图信封必须由宿主声明而不是模型自述，校验在服务端完成并忽略客户端上报，否则等于让 agent 自己写规则再自己遵守，约束力为零。

原帖：https://www.reddit.com/r/LLM/comments/1x3e4uz/

---

## 3. 本地 coding agent 真正的失败不是写错代码，而是发现问题后绕着它转圈（10-19 发布，补读）

**摘要：** 一个在做 macOS 本地 AI 应用的人复盘自家 9B 模型的表现：模型能正确指出错误，却不动手修，而是继续反复跑检查；他想知道别人用 Ollama 跑 coding agent 时最常见的失败长什么样，并且明确说更想听真实故障，不要理论上的改进。回帖把这种状态描述得很到位：agent 先写一个修复，紧接着写一个证明这个修复是错的测试，然后盯着两边不动；更常见的是第三次用 bash 列目录结构，而不是改那两行真正要改的代码。楼主的判断是，harness 最该改的不是模型能力，而是从发现问题到真的动手修这一段转换，并且要在不增加模型调用次数的前提下变可靠。这条讨论的价值在于把「agent 不行」拆成了可工程化的环节：检查循环、验证与修复的次序、以及长时间无进展时的强制收敛。

**高赞评论：**

- u/SolemnlySmelly（1赞·归档快照）："mine will sometimes write a fix, then immediately write a test that proves the fix is wrong, and then just stare at both like they're abstract art" … "it'll start writing bash commands to check the file structure for the third time instead of actually changing the two lines it needs to change" 立场说明：真实使用者的吐槽，把「检查循环」描述成写修复、写反证测试、然后对着两边发呆，说明失败模式更像流程设计问题，而不是单纯的模型太弱。
- u/dedly_project（1赞·归档快照，楼主）："the biggest opportunities for agent harnesses is improving the transition from identifying a problem to actually fixing it, instead of wasting time on repeated inspections" 立场说明：楼主把问题定位到 harness 的识别到修复这一跳，并强调不能靠增加模型调用次数解决，这与回帖里「第三次去列目录」的观察正好对上。

原帖：https://www.reddit.com/r/LLM/comments/1x9s3fy/

---

## 附：今日新增但尚无讨论（不计入推送）

- 本地 27B 模型同时操控 MMO 里五个角色，并上 Twitch 让观众投票覆盖它的决定（29 小时，14 分，1 条评论）：https://www.reddit.com/r/LLM/comments/1xzlxft/
- 从零用 Rust 写字节级 BPE tokenizer，自测比 o200k_base 少 26.6% token（38 小时，2 分，1 条评论）：https://www.reddit.com/r/LLM/comments/1xzawav/
- Ling-3.2-flash 标称 1M 上下文，但 Messages API 里输出 token 另有独立预算（105 小时，4 分，暂无评论）：https://www.reddit.com/r/LLM/comments/1xwwz74/
