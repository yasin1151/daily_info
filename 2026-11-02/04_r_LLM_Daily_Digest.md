
今日 r/LLM 观察完成。Reddit 直连与 redlib 全实例仍不可达（`www.reddit.com` / `old.reddit.com` / `redlib.perennialte.ch` 均 http=000），走 arctic-shift 归档 + feed2json 详情 RSS 通道；今日新帖仅 7 条，按「每条 3 条真实评论」硬门控筛完只剩 2 条可推，未凑数。

r/LLM 今日观察（2026-11-02）

今日 r/LLM 新帖只有 7 条，其中 4 条评论数为 0-2。按「每条必须有 3 条真实评论」的口径筛完，只剩 2 条可推。另有两条题材不错但确实零评论，只在这里提一句备查：一条是用同一个长任务对比 GPT-6.1 Terra 与 DeepSeek V4.1 Flash 的 agent 表现（14 步 vs 73 步、从缓存读取的输入占比 91% vs 96%、总成本 0.44 美元 vs 0.28 美元），另一条是有人把一条 DeepSeek 对话连跑六天、742 轮、约 56 万字直到撞上限。两条都无人回帖，不单独成条。

赞数说明：Reddit 直连与 redlib 全不可达，本稿正文与评论来自 arctic-shift 归档与该帖 RSS。归档里的赞数是入库时的快照，标 1、2 的多半还没长起来，不代表真实热度；RSS 来源不提供赞数，直接标注。

## 1. 免费档到底选谁：8GB 显存下的本地模型与现实里的免费额度

**摘要：** 楼主问的是非 agent 场景的日常问答，包括通用问题、技术问题、游戏问题和偶尔的提示词求助，想让社区直接点名两三个免费档模型。他的判断是 GPT 勉强够用，Gemini 在那次更新之后明显退步。评论区很快把话题拉到硬件：楼主补充只有 8GB 显存，答案就从「哪家额度大方」变成「这显存能跑什么」——Gemma4 的 E2B、E4B 塞得进去，想上 12B 并按 Q4_K_M 开到 192K 上下文就得多加一张 8GB 卡。另一条线来自一位有 5090、Ultra 9 和 64GB 内存的用户，他用 Gemini 批量生成练习题，撞到上传上限但任务还能继续，用 ChatGPT 做更难的乘法游戏扩展时也会耗尽上下文，最后靠人工接力做完，而本地模型至今没接上出 PDF 这一环。值得关注的是这轮讨论暴露的路线：免费额度和本地小模型混着用，而不是押注某一家。

**高赞评论：**
- u/ChillingChasuble（赞数 2·归档快照）：One of the Gemma models running at home on llama.cpp —— 立场说明：把答案从云端免费额度直接引向本地推理，用 llama.cpp 跑 Gemma 是他自己的日常方案，也是这轮讨论里最省事的一条路。
- u/ttkciar（赞数 1·归档快照）：Get a second 8GB card and you can use Gemma-4-12B-it quantized to Q4_K_M at up to 192K of context. —— 立场说明：给的是量化的硬边界，12B 加长上下文不是软件调参能解决的，显存不够就是不够，这条比「换个模型试试」有用得多。
- u/ACTSATGuyonReddit（赞数 1·归档快照）：It ends up running out of uploads, but it can still make the worksheets. —— 立场说明：他的用法最接近普通用户，撞到上传上限但没撞到任务死线，同时点出真正的断点是本地模型接不上 PDF 和成品输出，硬件再好也还差一层工具链。

**原帖：** https://www.reddit.com/r/LLM/comments/1xkz938/

## 2. 七万条销售语料微调的小模型，能不能追上 Claude：一次盲评的方法论争议

**摘要：** 楼主用 7 万条销售对话样本微调了一个小尺寸开源权重模型，输入里带上卖家的报价、理想客户画像和对每个潜在客户的备注，让它和 Claude Haiku 比两项任务：给回复分类排序，以及写销售邮件，评判方式是隐藏模型名的成对盲评。分歧正好在这里：有人肯定盲评已比只贴排行榜截图严谨，随即有人指出盲评证明不了微调更好，因为两个模型看到同一份报价、同一套客户语气和同一批备注，这些材料本身会主导草稿，最后两家写出来的是近似稿，盲评实际只在比文字顺不顺。他给的解法是按整个客户账号而不是随机邮件留出，排序用双方认可的标签，邮件看论点是否与备注一致，读起来漂亮但编造痛点的必须判负。这帖把垂直微调最常见的评估漏洞摊开了：按邮件随机切分时，同账号上下文会泄漏进测试集，指标虚高。

**高赞评论：**
- u/thethornypolling（赞数：RSS 未提供）：Wait, you actually did blind judging? That's more rigor than half the leaderboard posts around here —— 立场说明：肯定的是流程而不是结论，成对盲评加上隐藏模型名在这个版块确实少见，这条也顺手批评了只发截图不发方法的评测风气。
- u/Fit-Corner2382（赞数：RSS 未提供）：Blind judging will not tell you whether the fine-tune is better if both models see the same offer, voice, and prospect notes. —— 立场说明：全场最有价值的一条，指出输入材料主导输出会让两家草稿趋同，并给出按账号留出、按标签算排序、按论点是否忠于备注判邮件这三条可执行改法。
- u/Outbindai（赞数：RSS 未提供）：split by account score claims against the notes and fail any email that invents something however good it reads —— 立场说明：楼主本人的回应，确认他们确实按账号切分并对编造内容的邮件零容忍，还提到有一百多项测试要过，算是把质疑接住而不是绕开。

**原帖：** https://www.reddit.com/r/LLM/comments/1xlfhqc/

（本 job 无 blogwatcher 依赖：三个 DB 只登记了 r/ClaudeCode / GitHub Trending / HackerNews，未执行 scan/read-all。）
