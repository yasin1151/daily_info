
HackerNews 今日新帖精选（已扫描 30 条，筛选 10 条技术/产品高价值内容，并已标记已读）

---

**1. JavaScript 的诞生与“死亡”**
- 摘要：Gary Bernhardt 2014 年的经典演讲重新登上 HN，文章/视频以科幻喜剧方式回顾 JavaScript 从 1995 到未来的演化，既承认语言设计的历史包袱，也强调它对整个软件行业的巨大推动。评论区再次拿 `parseInt` 等经典坑调侃 JS 的“美学”。
- 为什么值得关注：适合重新理解 Web 编程语言如何在缺陷、兼容性和生态惯性中成为事实标准。
- 原文链接：https://www.destroyallsoftware.com/talks/the-birth-and-death-of-javascript

---

**2. Paul Graham：如何赚到十亿美元**
- 摘要：Paul Graham 从 YC 经验出发，解释创业公司如何通过极高增长率创造巨大财富，并反驳“十亿美元一定来自剥削”的观点。他强调真正关键是用户热爱产品、公司快速增长以及股权价值上升。评论区争议很大，一方认为他忽略外部性与资本结构，另一方认为批评过度意识形态化。
- 为什么值得关注：创业、财富创造、市场效率与社会分配的典型 PG 式论述，适合产品和创业方向读者。
- 原文链接：https://paulgraham.com/earn.html

---

**3. 并不是所有人都在用 AI 做所有事**
- 摘要：Gabriel Weinberg 反驳“人人都在用 AI”的叙事，指出生成式 AI 的使用更像吃肉：有人高频使用，有人限制使用，也有人完全不用。文中引用 Gen Z、Microsoft 遥测等数据说明 AI 渗透率并没有想象中全面。评论区也提到企业面试、客服流程和工程实践中 AI 使用的分化。
- 为什么值得关注：为 AI 产品增长、企业采用率和“AI 原生工作流”提供了更冷静的数据视角。
- 原文链接：https://gabrielweinberg.com/p/people-are-consuming-ai-like-they

---

**4. Kage：把任意网站保存成可离线浏览的单一二进制/本地副本**
- 摘要：Kage 使用 Headless Chrome 等待网页渲染完成后抓取最终 DOM，再移除 JavaScript，并把 CSS、图片、字体等资源下载到本地路径，目标是生成长期可保存、无追踪、无网络依赖的离线网页副本。评论区将其与 SingleFile 对比，也讨论为什么静态结果仍需要 server 模式。
- 为什么值得关注：面向网页归档、离线阅读、长期资料保存和反 JS 脆弱性的实用开发工具。
- 原文链接：https://github.com/tamnd/kage

---

**5. 里约“自研”LLM 被指是现有模型权重合并**
- 摘要：Nex-AGI 在 GitHub issue 中指称 Rio-3.5-Open-397B 并非真正自研训练，而是约 60% Nex-N2 Pro 与 40% Qwen3.5-397B-A17B 的权重线性合并。证据包括模型在去除系统提示后自称 Nex，以及各层权重张量高度符合固定比例混合。评论区关注模型合并的鲁棒性和归属/署名问题。
- 为什么值得关注：触及开源模型溯源、权重合并检测、模型署名与公共部门 AI 采购透明度。
- 原文链接：https://github.com/nex-agi/Nex-N2/issues/4

---

**6. 用 M1 Max 和本地 ML 索引 669GB GoPro 视频**
- 摘要：作者分享了用本地机器学习模型处理 669GB GoPro 视频的实践，目标是让大量个人视频素材可搜索、可回忆、可组织。虽然原帖主要在 HN 讨论页，评论区延伸到 Apple/Google Photos 式自动回忆、个人影像长期价值，以及本地硬件能否承担隐私友好的多媒体索引。
- 为什么值得关注：本地 AI、多媒体检索、个人数据管理和消费级硬件 ML 能力的交叉案例。
- 原文链接：https://news.ycombinator.com/item?id=48528029

---

**7. Linux 7.1 与旧驱动移除**
- 摘要：Linux 7.1 相关讨论集中在内核版本演进和代码清理。评论中特别提到，由于 AI 辅助 bug 报告大量涌入，一些极少使用的旧网络驱动如 ISDN 被移除，以减少维护噪音。抓取原文时遇到 Anubis 反爬证明页，但 HN 评论提供了关键背景。
- 为什么值得关注：AI 生成 bug report 已经开始影响大型开源项目维护策略，旧代码清理会变得更现实。
- 原文链接：https://lore.kernel.org/lkml/CAHk-=wi4BF4bMhZNZ1tqs+FFV4OuZRe3ZqdWB+LxRLmRweUzQw@mail.gmail.com/T/#u

---

**8. Jane Street：形式化方法与编程未来**
- 摘要：Jane Street 过去长期认为完整形式化方法成本过高，只在硬件综合等特殊场景值得投入；但 agentic coding 改变了成本结构。文章认为，当 AI 能生成大量代码时，人类价值会更多转向规格、验证和证明，形式化方法可能像高级类型系统一样变得普及。评论区则质疑形式化规格是否只是“用另一种方式重写测试/实现”。
- 为什么值得关注：这是 AI 编程浪潮下“代码生成之后如何验证”的重要方向。
- 原文链接：https://blog.janestreet.com/formal-methods-at-jane-street-index/?from_theconsensus=1

---

**9. zeroserve 兼容 Caddyfile：吞吐 3 倍、延迟降低 70%**
- 摘要：zeroserve 新增 Caddyfile 兼容模式，可将 Caddy 配置 JIT 编译成 eBPF，再编译为 x86_64/ARM64 机器码，并运行在 io_uring 事件循环中。作者展示 HTTPS 反向代理场景下的性能提升。评论区一方面认可技术炫技，另一方面质疑 Web server JIT 带来的攻击面和实际瓶颈价值。
- 为什么值得关注：涉及 eBPF、io_uring、配置编译、边缘代理性能优化和安全权衡。
- 原文链接：https://su3.io/posts/zeroserve-caddy-compat

---

**10. Postgres 中唯一可扩展的删除是 DROP TABLE？**
- 摘要：PlanetScale 文章认为，大规模 `DELETE` 在 Postgres 中会制造额外写入、复制压力、MVCC 死元组和 vacuum 成本，真正可扩展的清理策略应围绕分区、整表删除或 `TRUNCATE` 设计。评论区指出标题有些绝对：调优后的 autovacuum 与批量删除在 TB 级也能工作，但当要删除大比例数据时，复制保留数据到新表再 drop 旧表确实是经典方案。
- 为什么值得关注：数据库架构、数据生命周期管理和大规模清理策略的实战话题。
- 原文链接：https://planetscale.com/blog/the-only-scalable-delete
