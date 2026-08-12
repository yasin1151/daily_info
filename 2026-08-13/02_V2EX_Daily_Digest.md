
State updated successfully — 116 total IDs recorded (67 prior + 49 new). All new topics from this batch are marked read so they won't resend next run.

Now let me compose the final digest. I have two strong items to push:

1. **DeepSeek V4 Pro 0813 正式发布** — the major news event. From 1233961 (and corroborated by 1233960/1233959/1233963). Key detail from reply #3: supports responses API and can connect to Codex.
2. **Moeka Markdown 编辑器 (Rust/GPUI)** — self-promo from creator, but 18 replies with substantive technical critique (#11 challenges the "丝滑" performance claim — 2万行滚动卡顿, bug报错要金币; #18 detailed feature wishlist; #17 reply about export). Per rubric, this clears because commenters engage technically and the critical performance reply has real engineering value.

The rest were skipped: self-promo tools with thin/no replies (CalculatorQueen 1233980, Everything skill 1233975, 45M agent plugin 1233947, various 推广), recruitment posts, low-value life chatter, and the Baidu infra report which only had 1 reply (couldn't clear the 2-comment bar).

Let me write the digest in Chinese.

---

# V2EX 摘要推送 — 2026-08-13

## 1. DeepSeek V4 Pro（0813）正式版发布，已支持 Responses API / Codex

**摘要**：DeepSeek 官方定价文档中悄然上线了 `DeepSeek-V4-Pro-0813` 型号，多个 V2EX 帖同时确认模型已发布。社区反馈：模型已支持 Responses API，可直接接入 Codex；能力有所提升，但部分用户实测感觉"比上一代 Pro 慢"，价格暂未上调。对国内开发者而言，这是 V4 系列一次重要的正式版本落地，值得关注其多模态/长任务表现。

**评论摘选**：
- 〔3楼〕是的，的确更新了，试了下已经支持 responses api 了，可以接入 codex 蹬了。
- 〔8楼〕还没涨价呢，等涨价了再滑动（提醒当前定价可能随时变动）。
- 〔1楼/1233963〕跑了几个 WebGL demo，能力不错，就是感觉比以前的 Pro 要慢。

**链接**：https://www.v2ex.com/t/1233961

---

## 2. 「Moeka」—— Rust + GPUI 自研的本地优先 Markdown 编辑器

**摘要**：作者时隔八年携成品回归 V2EX，介绍自己用 Rust 与 GPUI 耗时 6 个月自研的所见即所得 Markdown 编辑器 Moeka，完全不用 Web 技术，主打高密度记录、GPU 渲染低开销，并集成 AI Agent。帖子的价值不止于产品本身——回复区围绕"本地优先编辑器性能与生态"展开了有营养的讨论，甚至包含对"丝滑"宣传的硬核打脸，对关注编辑器/桌面应用开发的人有参考意义。

**评论摘选**：
- 〔11楼〕2万行 js 滚动就会卡，resize 重建缓存后继续卡……我寻思起码比 sublime 流畅才值得宣称丝滑吧，报 bug 还要花金币，不测了。（对"丝滑"宣传的直接质疑，是测试 PR 的典型反例）
- 〔18楼〕不错的点赞。建议：1. Terminal 可选手体与大小（显示特殊字符）；2. 支持切换查看高亮源码（源码才有掌控感）；3. light 主题下左侧两栏未同步变化。谢谢用爱发电。（落地的功能改进清单）
- 〔9楼〕一行超长的部分直接隐藏了，移动不过去，没有底部滚动条。（真实可用性 bug 反馈）

**链接**：https://www.v2ex.com/t/1233953

---

已处理 49 条新帖，其余（推广帖、招聘、低价值生活闲聊、回复数不足的帖子）均已跳过并标记为已读。

This is my final report.
