
# 橘鸦AI早报 · 2026-09-08 摘要

## 要闻

**1. ChatGPT Work 上线「个人写作风格学习」**
OpenAI 宣布 ChatGPT Work 可连接 Gmail、Google Drive、Slack、SharePoint，学习你的措辞偏好、落款方式和大小写习惯，并把风格带入后续所有写作。网页端已对所有 Work 付费订阅开放。
→ 影响：Agent 从「会写」进化到「像你写」，企业办公场景的个性化输出是差异化卖点，也意味着更多隐私边界讨论。
🔗 https://x.com/ChatGPT/status/2097018264048251309

**2. Codex 负责人宣布全量付费订阅用量重置**
Tibo 发文称将对所有付费订阅执行一次用量重置，预计当天约 PST 18:00 落地，理由是用户在 Blender 3D 建模上消耗额度后仍要接着用 Astra。
→ 影响：对重度依赖 Codex 额度的开发者是直接利好；也侧面透露 Codex 生态已延伸到建模等跨领域工作流。
🔗 https://x.com/thsottiaux/status/2097043464538264003

**3. 腾讯混元 Hy4 preview 专项优化全量上线**
混元与 WorkBuddy 联合团队针对 Hy4 preview 在复杂任务下的长思考、过度自我验证问题完成优化，官方称在不损失任务效果的前提下显著降低任务轮次与 token 消耗。
→ 影响：中文大模型在 Agent 场景的「话痨/内耗」是普遍痛点，混元先打补丁，成本敏感型用户可关注实测。
🔗 https://x.com/TencentAI_News 相关推文（via 混元公告）

## 模型发布

**4. OpenBMB 开源 MiniCPM5-2B**
2B 参数小模型，官方称同尺寸 SOTA：34 项基准均分 53.9，Artificial Analysis 智能指数居 4B 以下开源第一；上下文 131072，Apache-2.0，同步开源 UltraData 训练数据与 RL 技术栈，已适配 Intel/Arm/Rockchip 并有 GGUF/MLX/GPTQ 格式。
→ 影响：端侧小模型卷到新高度——不只是权重，训练数据和 RL 全链路开源才是看点，个人开发者可低成本复现。
🔗 https://github.com/OpenBMB/MiniCPM | https://huggingface.co/openbmb/MiniCPM5-2B

## 开发生态

**5. 腾讯 AI 开源内部工具 TeamAI-CLI**
3 月起腾讯内部使用的团队知识管理工具：把技能、规则、文档集中到一个 git 仓库，所有 Agent 基于同一份「手册」工作，变更走 merge request、hook 触发下次会话生效，经验按真实使用累积置信度（强项优先、弱项下沉）。
→ 影响：「用 git 管团队 Agent 知识」是个值得抄的工程实践，直击多 Agent 协作时知识漂移和规则不一致的痛点。
🔗 https://github.com/Tencent-Hunyuan/Hy4-preview

## 产品应用

**6. Qoder 发布数字员工 QoderWake 1.0**
Mac/Windows 可下载、支持云主机部署；数字员工（Waker）可常驻钉钉/飞书/企微群，被 @ 接活或定时/关键词/事件触发，7×24 在岗。特训岗位从 6 个扩到 10 个（新增项目管理员、UI 设计师、DevOps 等），新增 Waker 群组、协作 SOP 与流程复用，高危操作默认拦截。
→ 影响：AI 员工产品从「聊天机器人」走向带权限、可编排的团队协作者，组织级治理（本地存储+拦截）是落地的关键设计。
🔗 http://qoder.com/qoderwake

**7. 千问开放平台上新 10 余个金融智能体**
覆盖证券、基金、期货、保险，入驻方含兴业证券智能投资助手、九方灵犀、众安保险等，用户在千问里 @ 或点角标即可调用。
→ 影响：大厂 Agent 生态开始「平台化拉机构入驻」，金融是第一个成规模的垂直赛道。
🔗 https://mp.weixin.qq.com/s?__biz=MzYzNDE5MDEwMQ==&mid=2247488663

## 行业动态

**8. DeepSeek 社招约 150 人：资深后端 + Agent 弹性计算**
岗位含服务端开发工程师、Agent 弹性计算研发工程师，北京/杭州，2–10 年经验优先。官方人员解释扩招源于数据、容器、训练评测、Agent 环境与请求规模增长带来的后端复杂度上升。
→ 影响：印证 DeepSeek 推理/Agent 业务负载在快速膨胀，弹性计算方向值得关注其技术选型。
🔗 https://x.com/tianyi/status/2096975270578139273

**9. ChatGPT 网站流量份额回升至 55.5%，Gemini 回落至 25.6%**
Similarweb 数据（仅网页端，不含 App/桌面客户端）：ChatGPT 从三个月前 52.7% 回升；Gemini 从 27.8% 回落；同比看 Claude 从 1.9% 涨到 9.3%，Gemini 翻倍，ChatGPT 从 73.3% 明显下滑。
→ 影响：ChatGPT 靠桌面版+Work 稳住了基本盘，但同比份额被蚕食是长期趋势；Claude 是过去一年增速最快的挑战者。
🔗 https://the-decoder.com/chatgpt-claws-back-web-traffic-share-to-55-5-percent-as-geminis-brief-comeback-fades/

---
已跳过：TRAE 高校扶持计划（积分营销活动，低信息量）。最新一期（2026-09-08）已标记已读；另有 8/7–8/15 共 9 期历史积压未读，需要的话可补扫。
