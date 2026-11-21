
# r/LLM 今日热帖 · 2026-11-22

Reddit 各端点（www/old/redlib）本轮全部返回 000，无法访问；所有请求都超时，GitHub API 仍返回 200，说明是 Reddit 的 IP 段被封。r/LLM 的候选共 251 条，过滤并去重后剩 177 条，我逐个请求评论树探测，177/177 全部成功、没有失败；但今天帖子的评论量极少：评论数达到 3 条以上的新鲜帖子只有 1 条，多数当日新帖为 0 到 2 条评论。因此本次只推送 1 条真实有讨论的内容，不为了凑够条数而补充低质量评论。帖子与评论的赞数都是归档入库时的快照值，可能滞后于线上。

## 1. 「无审查模型真好用」：abliterated 变体的真实需求长什么样

**摘要：** r/LLM 今天最活跃的一条帖子问的是：有人玩过 DeepSeek V4.1 Flash、Qwen 3.8 27B、GLM 5.3 Flash 的 abliterated（去审查）变体吗？楼主说自己最爱的是去审查版 DeepSeek V4.1 Flash，能跑到 200 tok/s 且从不拒绝，用起来不必再琢磨越狱话术，也不会先被说教一顿。评论区没有停留在立场表态，而是很快转向工程细节：有人追问 200 tok/s 是什么硬件跑出来的，有人给出 openuncensored.com（API）和 venice.ai（消费级聊天）两个具体入口，也有人提醒普通版 DeepSeek 在多模态改写上依然有限制、网页版与 App 的策略未必一致。另一条抱怨指出实际问题：聊到十几条就开始无限加载，上下文一长就报错，说明「敢答」和「能稳定用」是两件不同的事。值得留意的是讨论迅速引向越狱与破解（keygen、逆向付费插件），也有人反问「你们到底在问什么」；这本身就是社区信号：对去审查模型的真实需求中，灰色用途占了不小比例。

**高赞评论：**
- u/Crustaceous_Sandwich（赞数 3·归档快照）："I run regular DeepSeek and it does have limitations, especially with image modifications. Is there a separate app for uncensored? Is it uncensored if you use the web site vs the app?" 立场说明：这是全串最实用的一条，指出普通版在多模态改写上的实际边界，并追问网页版与 App 是否两套策略；按入口分级限制是当下厂商的常见做法，用户的困惑正来自这里。
- u/RebelMineCommand（赞数 1·归档快照）："how do I use them without infinite loading screens after like 10 messages or error messages because chat contexts got too long?" 立场说明：反馈很具体。这类模型往往运行在小体量服务上，长对话稳定性差是普遍代价；这条把话题从「能不能答」拉回「能不能连续干活」。
- u/Ontopoftheworld_ay（赞数 1·归档快照，楼主）："openuncensored.com for api and venice.ai for consumer chat" 立场说明：楼主直接给出了分层入口：API 走聚合站，日常聊天走消费级产品，比空谈立场有用；但也说明这类需求目前主要靠第三方灰色供给承接，官方渠道基本不覆盖。

**原帖：** https://www.reddit.com/r/LLM/comments/1y1jewo/
