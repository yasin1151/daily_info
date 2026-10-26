
**橘鸦AI早报 · 2026-10-26 期**
来源：daily.juya.uk ｜ 7 条，栏目：要闻 / 产品应用 / 开发生态 / 模型发布 / 技术与洞察 / 行业动态

---

**1. Kimi 为 K3.1 Pro 限流致歉，给所有订阅用户重置用量（最多补 25% 月额度）**
Kimi 承认 K3.1 Pro 订阅方案存在限流和不必要的额度消耗，“问题由自身造成，本应更早修复”。补偿方式：所有档位一次性重置用量，最多恢复相当于月度额度 25%（约一周用量），已用量低于 25% 的直接归零。同时调整配置，减少 Kimi Code CLI 和桌面端里不必要的 subagent 调用与输出长度。
值得注意：官方把“subagent 乱调用”明确列为额度消耗元凶，这和下面第 6 条 Anthropic 的判断是同一个病。
→ https://x.com/Kimi_Moonshot/status/2114450610724708492

**2. OpenAI「28 天计划」第 20 天全量重置 Codex / ChatGPT Work 用量**
Codex 团队 Tibo 确认第 20 天是 reset 日，改动已全量传播完成。该计划每天要么上线一项改进，要么对所有人全量重置用量。他预告“接下来一周会有有趣进展”。
实用点：现在是用量重置窗口，适合跑重任务。→ https://x.com/thsottiaux/status/2114237083652882932

**3. CapCut 插件将接入 ChatGPT，11 月开放测试**
剪映海外版 CapCut 的视频编辑/生成插件要进 ChatGPT，11 月在移动端、桌面端、网页端开测。用法：在对话里用自然语言生成素材、调草稿时间线，做出可编辑草稿后转进 CapCut 网页编辑器精修、发布；也能上传已有草稿继续改。官方把这套流程叫 "CapCut × Codex"。
影响：视频剪辑开始被拉进对话式工作流，OpenAI 生态在往“生产力插件平台”走。→ https://www.capcut.com/tools/capcut-x-codex

**4. OpenCode 公开自建 DeepSeek 推理机架的真实数据：24 小时 6.77 万亿 token**
团队成员 dax 披露：p50 首 token 延迟 1.16 秒，p50 吞吐 143 token/s。被问是否量化，他答“与 DeepSeek 官方 API 完全一致”，即未做量化降级。机架里有一个托盘不稳定，拖累了 p95 长尾。他此前称这套配置的价格性能优于他找到的其他供应商。
影响：第三方推理商开始公开硬指标卷透明度，6.77T/天这个量级说明开源模型自托管已是真生意。→ https://x.com/thdxr/status/2114211145615626433

**5. BOSS 直聘 Nanbeige 开源 33B dense 模型，主打智能体编程**
Nanbeige4.3-33B：33B dense、512K 上下文、Apache-2.0。官方称在 ~30B 级开源模型里 agent 表现 SOTA，Terminal-Bench 2.1 得 80.9，高于 Qwen3.8-27B 的 73.0。后续会拿它当教师模型蒸馏小模型，首个是 Nanbeige4.3-3B。社区已放出基于原 BF16 权重的 GGUF，13.7GB–35.2GB。
影响：本地/私有化跑 agentic coding 多了一个够格的开源选项，量化后单机可承载。→ https://huggingface.co/Nanbeige/Nanbeige4.3-33B

**6. Anthropic 反水：建议企业把 subagent 合并回主 agent 循环**
Anthropic 在 Claude 博客发文，建议已建多个 subagent 的企业把路由、规划、领域 subagent 整合进主 agent 循环，改用 Skills + 工具搜索按需加载上下文和工具。依据是多家企业部署对比：“配备 Skills 的单 agent 方案质量常优于 subagent 方案”，单任务成本和延迟更低；有一家客户评估发现单 agent 循环速度约为多 agent 框架的 2 倍。配套发了 migration kit（可在模拟系统上试跑）和一组 Claude API Skills。
但也没全否：上下文膨胀导致性能下降、需并行处理的场景，subagent 仍有价值。
影响：这是今年多 agent 架构退潮最权威的一脚，正在设计 agent 系统的人值得直接改方案。→ https://github.com/anthropics/single-agent-loop-kit

**7. 猫王歌曲权利方起诉 Anthropic，索赔约 4100 万美元**
Authentic Brands Group 旗下实体联合猫王权利实体起诉，指控 Anthropic 未经授权用 274 首歌训练 Claude，并要求每首 15 万美元赔偿（合计约 4100 万）。诉讼还称 Claude 生成了未授权的衍生内容。
影响：AI 训练版权诉讼正从“作者集体诉讼”转向“版权方单点、按首计价的高额索赔”，单曲 15 万美元这个锚点会外溢到整个行业。→ https://www.billboard.com/pro/elvis-presley-estate-sues-suno-anthropic/

---

**本期一条主线**：Kimi 因 subagent 乱调用于额度（第 1 条），Anthropic 直接发文劝企业砍掉 subagent（第 6 条），同一天两件事指向同一个结论：多层 agent 编排的隐性成本（token、延迟、额度）已经高于它带来的质量增益。第 4、5 条则是另一头——推理侧成本在被打下来（6.77T/天、33B 开源 SOTA），两头夹击下，“少编排、单循环、靠 Skills 加载上下文”会变成默认架构。

已标记该期为已读，当前无未读文章。
