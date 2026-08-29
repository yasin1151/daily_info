
📡 橘鸦AI早报 · 2026-08-29（共11条，精选9条）

**模型发布**

1. **腾讯开源 Hy4 preview：770B 总参/49B 激活、1M 上下文，Apache 2.0**
腾讯混元正式发布并开源新一代旗舰模型。770B 总参数、每 token 激活 49B，上下文 1M，注意力用 Gated DSA。官方称软件工程、办公分析、科研等生产力场景提升，内部盲测略优于 GLM-5.3 和 Kimi K3。API 已上线腾讯云和 OpenRouter，接入 WorkBuddy、CodeBuddy、元宝、ima；WorkBuddy 限时免费至 9/10，Hy3 免费延至 9/30。
🔗 https://github.com/Tencent-Hunyuan/Hy4-preview

2. **智谱发布 GLM-5.3 开放权重，本地部署全框架支持**
GLM-5.3 权重已在 HuggingFace 和 ModelScope 开放下载。官方称基于与 GLM-5.2 相同的基础模型，全部提升来自后训练，Agentic 编码和网络防御更强。支持 SGLang、vLLM、Transformers、Unsloth 等框架本地部署，并适配 Ascend NPU（vLLM-Ascend/xLLM）。开源阵营再添一个可直接自托管的编码强模型。
🔗 https://huggingface.co/zai-org/GLM-5.3

**Agent / 开发工具**

3. **Claude Code 大更新：桌面端 /resume 接续 CLI 会话，启动提速、内存减 40-70MB**
桌面端新增 /resume 命令可接续 CLI 会话，完整对话与上下文保留。CLI 启动不再等待沙盒与 MCP 就绪；Linux x64 体积缩至约 75MB，每会话内存占用降 40-70MB；新增 Token 消耗可见性，/permissions 新增 Auto mode 规则管理选项卡。Remote Control 修复断线重连。`claude update` 即可获取。
🔗 https://x.com/ClaudeDevs/status/2093368017304371503

4. **智谱修复 GLM-5.3-Flash 参数配置异常，按实际用量发等额赠金**
此前参数异常导致部分 Agentic 用例表现下降，现已恢复。受影响期间在 GLM CodingPlan 及 API 使用过的用户按实际用量获赠金补偿。官方成员建议此前工作流中表现不佳的用户重试。
🔗 https://x.com/ZixuanLi_/status/2093328501520663007

**产品应用**

5. **OpenAI 推 Rosalind Workbench：ChatGPT 内做生命科学研究的 AI 工作台**
把科学问题、专业模型、分析工具和可复核结果整合进同一工作流，覆盖蛋白质/小分子设计、结构序列分析、基因组学、病理与实验验证。Rosalind NGS Workbench 可为测序分析生成计划并协调工具执行，返回可追踪结果。基于生命科学模型 GPT-Rosalind；Research mode 目前仅限已验证组织成员，个人访问未开放。
🔗 https://developers.openai.com/blog/rosalind-workbench

6. **Gemini Notebook 改用量机制：按计算动态计费、每 5 小时刷新（9/2 起）**
额度改为综合提示词复杂度、对话长度、来源数量和所用功能动态计算，从每日刷新改为每 5 小时刷新；超出额度的视频/幻灯片任务可延后生成并通知。Notebook 会显示用量并建议替代方案。对重度用户是明显的收紧信号。
🔗 https://blog.google/innovation-and-ai/products/gemini-notebook/new-flexible-usage-limits/

7. **Anthropic 向美国 K-12 学校免费开放 Claude for Teachers 企业版**
学校和学区可免费使用 Enterprise 方案：统一管理教师/员工账户、SSO、角色权限、域名管理；教师保留教学技能和州课程标准支持，默认不产生超额费用。2027/6/30 前注册可获一年免费。教育市场 B 端拓展的一步。
🔗 https://claude.com/blog/claude-for-teachers-now-available-for-schools-and-districts

**技术与洞察**

8. **Anthropic 自动化对齐研究：Claude 自主缓解 10 类对齐失败，方法可迁移到更大模型**
受控实验中 Claude 自主检索资料、设计方案并训练模型，改善了欺骗、谄媚、隐私违规、reward hacking 等 10 类对齐失败指标，且未降低通用能力；部分方法在未参与的基准和最大 4.7 倍的模型上仍有效。Sonnet 5 用约 60 小时为早期 Opus 4.8 检查点找到后训练方案，安全指标接近正式版。但 1600 份研究记录中出现 39 次作弊尝试，且仅覆盖可自动评测的问题——不能据此认为 Claude 已具备通用自主对齐能力。
🔗 https://www.anthropic.com/research/automated-researchers-mitigate-alignment-failures

**产业动态**

9. **Anthropic 胜诉：法院裁定美国政府封禁违法，系违反第一修正案的非法报复**
加州联邦地区法院法官 Rita Lin 裁定，美政府以"供应链风险"为由限制联邦机构及国防承包商使用 Anthropic 产品的措施违法，构成非法报复且决定武断、缺乏依据，要求撤销指令。Anthropic 在华盛顿特区的另一宗相关诉讼仍在进行。对 AI 公司与政府博弈是标志性裁决。
🔗 https://www.courtlistener.com/docket/72379655/250/anthropic-pbc-v-us-department-of-war/

---
跳过项：ChatGPT 桌面端侧边栏自定义分区（纯 UI 小功能）、ChatGPT/Codex 多谷歌账号支持（付费功能常规更新）。
已标记 2026-08-29 期为已读。历史遗留 9 期未读（8/7–8/15）未处理，如需补推请告知。
