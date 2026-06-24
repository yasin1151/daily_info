
**r/LLM 今日热帖**

**1. Overfitted a 900KB LLM to compress a 100MB csv into 7MB**

摘要：作者展示了一个很有实验味的 neural compression 项目：不是用通用压缩器，而是把一个小 Transformer 专门过拟合到单个 100MB CSV 的字节分布，再结合 arithmetic coding 输出 7MB 压缩文件。值得关注的点不只是“LLM 能压缩文件”，而是模型大小必须计入总成本后，才有公平比较意义。这类方法像是在探索“模型作为文件特化概率表”的边界，对数据压缩、memorization、推理成本和小模型用途都有启发。

高赞评论：
- u/cbrincoveanu，5 赞：指出真正关键指标应是“模型文件 + 压缩文件”相对原文件的总压缩率，并希望看到与 ZIP 等标准压缩器的 benchmark。立场：支持实验，但要求公平基准。
- u/sabbath_loophole，4 赞：认为这个想法很酷。立场：偏正面，认可创意价值。
- u/westsunset，4 赞：确认复现文件是否需要同时保存 900KB 模型和 7MB 压缩包。立场：关注实际可用性和总交付成本。

原帖：https://www.reddit.com/r/LLM/comments/1udarnp/

**2. Gemma4-12B-QAT Uncensored Balanced is out with MTP (~60% speed boost)!**

摘要：帖子发布了一个 Gemma4-12B-QAT 的 uncensored balanced 版本，声称通过 MTP 获得约 60% 速度提升，并在拒答测试中表现激进。技术看点是小/中型开源模型在量化、推理速度和安全策略移除上的持续分化；但评论区焦点很快转向许可证与代码来源争议。这条值得关注，不是因为营销指标本身，而是因为它同时反映了开源模型社区在速度优化、uncensored 需求、AGPL 合规和模型发布信任上的摩擦。

高赞评论：
- u/Party_9001，3 赞：指控相关代码是 AGPL 3，若使用则必须署名、开源且许可证传染，但发布者改了许可证并拒绝公开方法。立场：强烈质疑合规性。
- u/UntimelyAlchemist，2 赞：认为这是针对发布者的骚扰活动，称模型质量确实好且免费，争议可能来自竞争和付费化压力。立场：维护发布者，强调实际模型效果。
- u/Party_9001，1 赞：继续表示问题在于“偷了所有东西”。立场：延续许可证/来源质疑。

原帖：https://www.reddit.com/r/LLM/comments/1ucn9kr/
