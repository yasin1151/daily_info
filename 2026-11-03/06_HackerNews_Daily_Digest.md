
# HackerNews 今日十帖 · 2026-11-03

**1. LLM 能原生读写神经网络权重：Astra 手改 0.016% 权重，把 Qwen 的数学从 7.9% 拉到 48.1%**
MIT CSAIL 团队发现前沿模型可以直接读、写权重、不靠梯度下降。GPT-6 Astra 只看 17,253 个数字就能认出网络是打哪个游戏的；不给环境反馈也能从零写出打赢 PPO 一亿步的小网络；在 Python 里改掉 Qwen3.5-0.8B 的 0.016% 权重，修掉官方 model card 自己警告的推理死循环，MATH-500 从 7.9% 升到 48.1%，IFEval 顺带涨 3 倍。作者称之为 Weight-Space Programming。
社区："I'll chalk up never even having thought of this being an option as yet another instance my human hubris"（连"这事能干"都没想到，又是人类傲慢）；"Slightly terrifying."；也有人类比 CRISPR——给模型做基因编辑。
为什么值得关注：优化器这一层可能被推理模型吃掉一部分，alignment 的前提也被动摇。
https://rikiyat.github.io/blog/weight-space-programming/ ｜ https://news.ycombinator.com/item?id=50341174

**2. Ubuntu LTS 内核三周没修一个 CVSS 9.8 的 0day RCE**
CVE-2026-98432 打分 9.8，22.04 / 24.04 / 26.04 三个 LTS 至今没有官方修复内核，也没给 ETA 和缓解方案。管理员只能在原地硬扛、上 iptables/nftables 规则，或者迁到已带补丁的发行版。
社区有人提醒该站是"2026 年的 freenode.net"，与老 Freenode 无关；实用派给了过滤规则示例：`iptables -A INPUT -p tcp -m u32 --u32 "0>>24&0xF=6:15" -j DROP`；也有人反驳说"没有观察到在野利用，风险被夸大了"，并指出 RHEL 也是前一天才发补丁。
为什么值得关注：LTS 的隐含承诺是"有洞就快修"，这次是承诺兑现率的压力测试。
https://freenode.net/article/ubuntu-lts-kernels-still-unfixed-for-critical-cve-2026-98432 ｜ https://news.ycombinator.com/item?id=50341462

**3. Oracle 发股发债募 200 亿美元，给 AI 数据中心续命**
CNBC 报道 Oracle 申请增发股票与债券共 200 亿美元用于 AI 基建。按其市值粗算股票部分约 2.5% 稀释，但股价当天跌 8%——市场担心的不是稀释，是它本身杠杆已经很高还要继续加。
社区："I hope nothing but the worst for Oracle as a corporation...though nothing against the technical talent there."；更硬的一条是"Oracle 并没有 OpenAI 离不开的专有 IP，它在卖大宗商品服务"，一旦 GPU 世代换代，按老卡设计融资的机房可能在回本前就被超越。还有人说"读成 to finance AI bailout 了"。
为什么值得关注：这是 AI 资本开支从"讲故事"转向"加杠杆"的典型样本，也是 neocloud 连锁反应的源头。
https://www.cnbc.com/2026/11/02/oracle-files-to-sell-20-billion-in-new-stock-bonds-to-finance-ai-buildout.html ｜ https://news.ycombinator.com/item?id=50342284

**4. 陶哲轩博客发文《AI 时代的无我数学》**
这是 Karthik C. S.、Amit Sahai、Jie Xue 三位学者的客座文章（用 AI 转换格式），核心论点是：数学发现的价值不该绑在"谁先做出来"上，若把学科价值等同于产出结果和个人能力展示，AI 一来就会失重；应该回到柏拉图式的"发现独立于我们的真理"。
社区吵得很实在："I fear for what mathematics will become if that becomes the majority viewpoint."（如果这变成主流观点，我为数学的未来担心）；"在 publish or perish 时代，学术界除了荣誉几乎没别的可图"；还有人对文末致谢"感谢 GPT Astra 6.0 和 6.1 Sol 协助撰写"感到不适，认为像在念祷词。
为什么值得关注：AI 对学术共同体价值观的冲击，比工具替代争论更早发生。
https://terrytao.wordpress.com/2026/11/02/egoless-mathematics-in-the-ai-era/ ｜ https://news.ycombinator.com/item?id=50341736

**5. 预训练投毒可以给 Agent 植入 RCE 后门**
arXiv 论文（作者含 Nicholas Carlini 等）：从零预训练 Qwen3 0.6B/1.7B/4B，再走干净流程 post-train 成 CLI Agent。只污染 0.1% 预训练语料，4B 模型攻击成功率约 92%；污染率降到 0.0005% 仍有效，且干净输入下行为完全正常。
社区有人叫它"context bombs"，担心未来"免费送模型"就是送货上门；也有人说这是 Anthropic 作者在给闭源站台，"真正在意安全的人早就把 Agent 沙箱化了"；反方紧跟着回：闭源模型你连审计的机会都没有。
为什么值得关注：和上一条 Astra 权重编辑放在一起看，开源模型供应链的信任模型要重写了。
https://arxiv.org/abs/2610.37741 ｜ https://news.ycombinator.com/item?id=50341334

**6. Anthropic 增长"真的"平了：Q3 环比 +45%，Q2 是 +141%**
Henry Blodget 拆解：Q1 48 亿、Q2 116 亿、Q3 168 亿美元，Q3 绝对增量比 Q2 少；结合 7 月 650 亿年化这个点倒推月收入，8、9 月几乎是平的，而且投资者会上没敢报 9 月年化数字。作者认为这可能是季节性、产能跟不上，或需求端真的在减速（部分流向中国便宜模型）。
社区："I think all numbers coming out of Anthropic are utterly meaningless until we can answer the question of just how subsidized are those subscriptions?"；也有人把锅甩给产品代际："Opus 5.5 太强，大多数人不需要 Fable 了"。还有一句很典型："我希望它们成功，但更希望估值现实一点。"
为什么值得关注：这是"AI 泡沫何时破"从情绪争论变成数字争论的第一手材料。
https://www.regenerator1.com/p/anthropics-growth-just-flattened ｜ https://news.ycombinator.com/item?id=50344958

**7. Launch HN：Momentic 的 Agent 靠"真用你的 App"找 bug**
YC W24 团队发布 Mo：不是跑用例，而是像用户一样操作应用做探索式测试。他们同时开源了 qa-bench，并直接公布不利数字——Mo 每个 bug 2.67 美元、Codex 0.80 美元；查全 84% 对 86% 精确。
社区最扎心的问题："Is the takeaway from that not just that Codex is better for cheaper?"；也有人质疑护城河："过去三年一堆 custom harness 都被下一代前沿模型吞了，Opus 6.0 五个月后吃掉你的优势时你卖什么？"创始人现场回应并开放第三方 Agent 上榜。
为什么值得关注：Agent 产品的竞争已经从"能不能做"落到"每个 bug 多少钱"。
https://momentic.ai/ ｜ https://news.ycombinator.com/item?id=50339913

**8. 有人主张 SEC 应该拦下 Anthropic 的 IPO**
TechPolicy 评论文章认为，Anthropic 上市后会被动进入指数基金和养老金组合，普通人的钱在没得选的情况下承接高风险 AI 资产，监管应提前拦截。
社区多数不买账但分歧有意思："Let the market figure it out. If it goes public and crashes, we get a valuable answer."；反驳方指出被动基金本身就是市场扭曲，"强制买入发生在崩盘之后"；另有一条角度更刁：真正该问的是"为什么拖到现在才上市，之前的万亿美元收益全被内部人拿走了"。
为什么值得关注：AI 公司上市会第一次把行业风险传导到普通人的退休账户，这是接下来半年最现实的政策争点。
https://www.techpolicy.press/the-sec-should-block-anthropics-ipo-to-protect-the-public/ ｜ https://news.ycombinator.com/item?id=50344919

**9. 网线穿不动？用"隐形"光纤**
一位房主 CAT6 只跑到 100 Mbps，穿管失败后改用 0.9mm 的隐形光纤沿踢脚线和门框走线，肉眼几乎看不见，配双向光模块一根线搞定。
评论区几乎全是实操经验：20 年网络工程师指出"先重压水晶头，十有八九是一对线没压好"；用 MoCA 的人提醒"入口一定要装滤波器，别把数据送到邻居家"；也有人吐槽 Powerline 到不了千兆、MoCA 又贵又不是全双工。还有德国读者跑题讲起埋在地下的军用光纤。
为什么值得关注：家庭/小办公室 10G 组网的最优解正在从铜缆转向光纤，成本门槛已经降到几百美元熔接机。
https://momandpop.network/2026/11/02/cant-fish-ethernet-use-invisible-fiber-instead/ ｜ https://news.ycombinator.com/item?id=50344222

**10. Polyend 开源 Tracker 固件源码**
硬件音乐设备厂商 Polyend 把 Tracker 固件源代码公开，这是本轮"合成器固件开源潮"里最新一例（Erika Synths 的 LXR-02 刚跟上）。官方明确：刷第三方固件不保，但出问题可走付费保修外维修。
社区："The avalanche of reverse engineered/custom firmwares is definitely changing the synth landscape."，并指出社区早就用 LLM 辅助逆向、自己写固件，厂商开源其实是承认既成事实；也有音乐人担心"很多人不喜欢 AI，但确实想要新功能和修 bug"。顺带有人吐槽官网视频要"接受营销 cookie"。
为什么值得关注：硬件厂商开始把固件开放当成竞争手段，硬件 + 社区固件的模式可能复制到更多嵌入式产品。
https://polyend.com/whats-up/tracker-the-biggest-update-yet/ ｜ https://news.ycombinator.com/item?id=50340159

---
今天 HN 的能量高度集中在两件事上：模型开始"理解并改写权重"（1600+ 赞），以及 AI 资本故事出现第一道裂缝（Oracle 加杠杆、Anthropic 增速走平）。BYD 销量、苹果财报虽然分数更高，但与技术读者关系不大，未纳入。
