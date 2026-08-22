
已抓取最新一期（2026-08-22）全文，共 22 条，筛选出 10 条高价值内容：

---

# 🍊 橘鸦AI早报 2026-08-22 精选

## 要闻

**1. DeepSeek 发布多模态模型 V4-Flash-Vision-Exp**
DeepSeek API 正式上线视觉理解模型：纯文本能力持平 V4-Flash，多模态 Agent 能力接近 Opus-4.8，上下文 1M、最大输出 384K，单张图片最多占 384 tokens、单请求最多 600 图，定价与 V4-Flash 一致。同时上线**免费的 Files API**（先传图再引用，省带宽），支持 Chat Completions/Messages/Responses 三种格式。意味着 DeepSeek 补齐了多模态短板，且延续低价策略，视觉 Agent 的 API 成本门槛被拉低。
🔗 https://mp.weixin.qq.com/s/UGMfvPMwBIB4oFYZZejekA

**2. Codex 额度异常有说法了：sub2api 转订阅共享会被标记**
Codex 负责人 Tibo 回应近期大量用户反馈的额度消耗异常：与其交谈的受影响用户多在使用 sub2api（把订阅转成 API 流量供多人共享），这类用法会被防欺诈系统标记；用"ChatGPT 登录"的官方客户端及 Pi、OpenCode 等 OSS 客户端没问题。但多名用户反驳称**从未用 sub2api、仅用官方应用也遇到异常**，调查仍在进行。用共享/转售渠道的要注意了。
🔗 https://x.com/thsottiaux/status/2090675027670978569

**3. Codex 活跃用户达 2000 万，给付费用户发了一次性 banked reset**
Tibo 宣布 Codex 活跃用户本周破 2000 万，向所有 Codex 和 ChatGPT Work 付费用户发放一次 banked reset（额度重置，可自行择时使用），目前已发放完成。结合上条，官方仍称未发现额度消耗异常——用户端的抱怨和官方口径存在明显张力。
🔗 https://x.com/thsottiaux/status/2090947196107764189

## 开发生态

**4. OpenAI 将 GPT-5.6 Sol API 价格下调超 20%**
降价持续 3 个月，已对 API 用户和按量计费的 Codex Credits 生效（同样额度能跑更多调用）；Pro/Plus/Business 订阅内含用量不变。成本敏感型团队未来三个月是加大 Sol 用量/迁移的好窗口。
🔗 https://x.com/OpenAI/status/2090885187634905500

**5. OpenAI 推出按 API 密钥追踪用量与支出 + 硬性限额**
用量仪表盘现可按 API 密钥查看具体应用/工作负载的费用，并可设置月度支出限额——含**达到限额直接停止流量的硬性限额**，可防失控的 token 账单（尤其是 Agent 类负载）。API 成本治理能力一次性补齐。
🔗 https://x.com/OpenAIDevs/status/2090903221636338057

**6. DeepSeek Harness 三连更至 v0.1.1-rc.1，支持官方多模态**
自预览版发布以来连续三次更新：新增 V4-Flash-Vision-Exp 多模态选项，/goal、/plan 可接收图文输入，@ 菜单可引用文件和会话；Codex 与 Claude Code subagent 接入 Job Panel 可按需安装，支持非交互权限模式和多个命名实例；并修复长会话、终端兼容等社区反馈问题。DeepSeek 官方 Agent 框架迭代速度很快。
🔗 https://mp.weixin.qq.com/s/xw-hxtHMcxxSGqbSbp98RQ

**7. Claude Security 代码扫描上线 Claude Mythos 5（Enterprise 公开测试）**
在 claude.ai/security 指定 GitHub 仓库后由 Mythos 5 扫漏洞，每条发现附 CWE 分类、置信度、严重程度和建议修复；按订阅标准 token 用量计费。同步设立 **3500 万美元 Defender Advantage Fund** 并扩展 Cyber Verification Program。企业安全扫描直接绑定旗舰模型，模型即安全能力。
🔗 https://claude.com/blog/bringing-claude-mythos-5-to-more-defenders

## 模型发布

**8. Thinking Machines 在 OpenRouter 免费开放 Inkling（限 agentic 调用）**
Inkling 与 Inkling-Small 即日起在 OpenRouter 免费开放数周，**仅限 agentic harnesses 调用**，官方用收集的使用数据改进 agentic 表现（数据与账户脱钩）。免费窗口期是低成本实测该模型 Agent 能力的时机。
🔗 https://x.com/thinkymachines/status/2090888586849878374

## 产品应用

**9. Kimi Code 飞书 AI 同事「Mira」开启 Beta**
Mira 驻扎在飞书：群聊中当团队 AI 员工接任务、跟进度，私聊中当个人助理；支持主动学习，消息整理、复盘、定时巡查后台持续运行。Beta 仅支持飞书，需申请审核，只能用 Kimi Code 会员额度（建议 K3），**暂不支持自己的 API Key**，且后台自动消耗额度、总体消耗可能较大。用飞书办公的团队可以关注。
🔗 https://www.kimi.com/code/beta

## 技术与洞察

**10. NVIDIA AVO Agent 在 ARC-AGI-3 公开集拿下 100 分满分**
NVIDIA 通用编码 Agent AVO（基于 Claude Opus 5）在 ARC-AGI-3 公开集取得 100.00 RHAE，完成全部 25 个环境 183 关（环境不提供说明/规则/目标），共 6,624 次动作。官方明确仅覆盖公开集、不含半私有与完全私有集。长时程自主 Agent 的基准表现又上一个台阶。
🔗 https://developer.nvidia.com/blog/nvidia-avo-reaches-100-on-arc-agi-3-demonstrating-a-frontier-level-general-purpose-architecture-for-long-horizon-autonomous-agents/

---

**本期看点小结**：DeepSeek 多模态补齐 + Harness 快速迭代；Codex 2000 万用户背后的额度争议（sub2api 被标记 vs 官方称无异常）；OpenAI 降价 + 成本治理工具双双落地；两家巨头（Claude/Google）同日推 Remote Control 远程控制也是值得注意的趋势信号。

来源：https://daily.juya.uk/issues/2026-08-22/（文章已标记已读）
