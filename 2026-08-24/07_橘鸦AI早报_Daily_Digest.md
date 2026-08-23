
📰 **橘鸦AI早报 2026-08-23**（共 6 条，全部高价值）

---

**1. DeepSeek API 计费调整：周末全天统一按低谷价收费**
自 8 月 23 日 00:00 起，周末（周六、周日）不再区分峰谷时段，统一按低谷价计费；工作日维持原峰谷分段计费。官方称此举让用户周末灵活调度业务、避免高峰成本，同时平衡全网算力负载。规则生效前费用按原规则结算，不同意可退出并申请退费。
💡 **影响**：对周末跑批、训练、批量调用的开发者是实打实的成本利好，可把重任务挪到周末。
🔗 https://daily.juya.uk/issues/2026-08-23/

**2. Firecrawl 上线编程 Agent 专用检索索引 Developer Index**
覆盖超 7000 万个一手来源（仓库、文档、issue、已合并 PR、README），供 Agent 自行回答代码行为、API 契约、报错信息和已知 bug。官方基准：1179 条真实开发者查询上 recall@10 达 63%，比次优外部服务商高约 10%。
💡 **影响**：编程 Agent 的"查资料"能力直接决定任务成功率，这是对现有检索方案（如 grep.app、Sourcegraph）的正面竞争。
🔗 https://firecrawl.dev/developer-index

**3. Codex 用量异常更新：部分用户缓存命中率下滑，团队正调查**
Codex 负责人 Tibo 发帖称部分用户本周缓存命中率低于此前稳定水平，可能解释额度消耗加快的原因，团队正在查日志和监控面板，稍后会有更新。评论区多名用户反馈额度异常快速消耗，也有人反驳称无使用时额度仍在下降，原因未定。
💡 **影响**：如果你近期感觉 Codex 额度掉得快，属于已知问题，官方在排查，别急着续费。
🔗 https://x.com/thsottiaux/status/2091033630147854385

**4. uv 作者重做 Codex CLI 启动流程，提速约 25 倍**
已加入 OpenAI 的 Python 工具 uv 作者 Charlie Marsh 在最新版 Codex CLI 中重写启动生命周期，codex 启动近乎即时、可立即响应，已随新版发布，升级即可体验。
💡 **影响**：CLI 工具启动延迟是日常开发的高频痛点，25 倍提升感知明显，值得立即升级。
🔗 https://x.com/charliermarsh/status/2090924566923067490

**5. Cursor 权益变动：SuperGrok Heavy 不再附赠 Cursor Ultra**
Cursor 官方文档已删除"关联 SuperGrok Heavy 附赠 Cursor Ultra"的说法，现明确关联 SuperGrok Plus/Heavy 仅获得 Grok Bot 用量授权。工作人员回应：已付费并成功激活免费 Ultra 的老账号不受影响。
💡 **影响**：新用户薅不到 Ultra 了，老用户权益保留；续费前先确认当前绑定关系。
🔗 https://forum.cursor.com/t/free-cursor-ultra-with-grok/168286/37

**6. Anthropic 回应 Claude Code "降智"质疑：配置测试导致数值映射差异**
用户发现 Claude Code 2.1.237 起 "high" 推理档显示数值为 10（与旧版 "low" 相同），质疑降智。Anthropic 成员 Thariq 回应：团队正在测试新的 API 服务配置，对数值型努力等级的映射方式不同导致显示差异；该刻度不是 0-100，数字无独立意义，所选努力等级就是实际获得的等级，内部深度评估确认不影响性能。他还承认 Opus 5 是"尖峰化（spiky）"模型，提升一致性是团队高优先级事项；遇到明显回退可发 /feedback 提交 ID，会补偿 credits。
💡 **影响**：显示数字≠真实档位，属误会；但官方亲口承认 Opus 5 表现不稳定，长任务表现波动可能确实存在。
🔗 https://x.com/trq212/status/2091247114869432543

---

**备注**：blogwatcher 里还积压了 08-07 ~ 08-15 共 9 期未读旧刊（此前 cron 中断所致），本次仅处理并标记了最新一期（5359）。如需补读旧刊或批量标记已读，下个任务说一声即可。
