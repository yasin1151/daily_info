
## HackerNews Top 技术新帖摘要（2026-07-19）

### 1. 《Principia Artificialis：人工思维的数学基础》
**摘要：** 这是一个 GitHub 开放研究项目，试图用信息几何、拓扑、动力系统和热力学来形式化 AI 推理与“人工思维”。项目包含实验、数据、讨论笔记和验证状态，目标更像是搭建一套 AI 推理的数学研究纲领，而不是单一模型或工具。  
**为什么值得关注：** 如果 AI 系统越来越依赖经验工程，类似项目代表另一条路线：把推理、表示、能量、约束等概念数学化，可能对可解释性、验证和新型架构有启发。  
**原文链接：** https://github.com/holland202/Principia-Artificialis

---

### 2. 《Grok-iOS：用 iPhone 远程控制 Grok Build 的 ACP 客户端》
**摘要：** 这个开源项目提供一个 iOS 客户端，通过 ACP 协议远程连接 Grok Build。仓库包含 iOS 应用、companion 组件、共享代码、脚本和上游 grok-build 子模块，定位是把移动端变成 AI coding/build 工作流的控制面。  
**为什么值得关注：** ACP/agent 协议生态正在扩展到移动端，说明“在手机上调度远程 AI 编程代理”可能会成为新型开发入口。对移动 IDE、远程 agent 操作台、随时随地 review/build 有参考价值。  
**原文链接：** https://github.com/Pedroshakoor/grok-build-ios

---

### 3. 《Passinote：基于画布的笔记与整理应用》
**摘要：** Passinote 是一个自由画布式笔记应用，主打“把笔记像桌面物件一样随意放置”。功能包括任意拖放笔记、堆叠与分组、绘制区域、自动保存、历史记录，以及把单个笔记、堆栈或区域导出为 PDF。  
**为什么值得关注：** 笔记产品正在从树状文件夹、线性文档转向空间化组织。它的价值不在技术复杂度，而在交互范式：让用户用位置、区域、堆叠表达思考结构。  
**原文链接：** https://www.passinote.app/

---

### 4. 《研究发现：AI 建议让人准确率下降三倍，却更自信》
**摘要：** TNW 报道一项法意研究：当参与者可以使用 AI 建议时，“我不知道”的判断从 44% 降到 3%，准确率从 27% 降到 9%，但自信度从 30% 升到 76%。研究故意选择 AI 容易答错的问题，观察人类是否会放弃独立判断。金钱激励只能略微改善。  
**为什么值得关注：** 这是“认知投降”的又一组强数据：AI 不只是给错答案，还可能压制人类承认不确定性的习惯。对 AI 搜索、教育产品、企业知识助手设计都很重要。  
**原文链接：** https://thenextweb.com/news/ai-advice-suppresses-critical-thinking-wrong-answers-study

---

### 5. 《新的 Intel Itanium / IA-64 模拟器已经能启动 Windows》
**摘要：** Raymii 报道，Yufeng Gao 在 gdwnldsKSC 协助下发布了 IA-64 模拟器 0.1，已经能启动 Itanium 版 Windows Server 2003 和 Windows XP 64-bit。性能仍很慢，据称在 Ryzen 5000 上大约是 486 级别；目前 OpenVMS、HP-UX、Linux/BSD 还不能启动。文章还提到可能存在能跑 Server 2008 的 QEMU fork。  
**为什么值得关注：** Itanium 是历史上重要但失败的非 x86 架构。能模拟启动 Windows 意味着数字考古、旧企业系统研究、CPU 架构教学有了新工具，也体现非主流架构模拟正在升温。  
**原文链接：** https://raymii.org/s/blog/Intel_Itanium_IA-64-Emulator_that_boots_Windows.html

---

### 6. 《HomeLab #1：把 MikroTik 当家用路由器》
**摘要：** 作者记录了用 MikroTik L009UiGS-RM 搭建家庭网络的过程，重点解释了 ISP 接入前置知识：IPoE vs PPPoE、VLAN、WAN 是否公网 IPv4、CGNAT、DS-Lite 对端口转发和远程访问的影响。文章随后进入 RouterOS 初始化、ONT 接入、管理地址和网络结构配置。  
**为什么值得关注：** 很多 homelab 教程跳过最关键的 ISP 接入层。本文价值在于把“买路由器之前要问清楚什么”讲得很具体，尤其适合准备自托管、NAS、远程访问的人。  
**原文链接：** https://justsomebody.dev/blog/mikrotik-home-router

---

### 7. 《最后一个 MPEG-4 Visual 专利已过期》
**摘要：** Phoronix 报道，MPEG-4 Part 2 / MPEG-4 Visual 的最后一项专利于 2026 年 7 月 19 日到期。美国和欧盟相关专利此前已经过期，最后剩余的是巴西专利 BRPI0109962B1。VIA Licensing Alliance 确认这是 MPEG-4 Visual 的最终专利。  
**为什么值得关注：** 这对多媒体软件、开源发行版、编解码器合规有象征意义。虽然 MPEG-4 Visual 已不是最前沿格式，但专利到期降低了长期维护、归档、兼容播放和发行层面的法律复杂度。  
**原文链接：** https://www.phoronix.com/news/Last-MPEG-4-Patent-Expired

---

### 8. 《Show HN：用 1600 美元 ESP32 替换 12 万美元保龄球馆计分系统》
**摘要：** 一位 SRE 买下废弃的 8 道保龄球馆后，发现 2008 年安装的计分系统替换成本高达 8–12 万美元。于是他用 ESP32、ESPNow、RS485 备用链路、Raspberry Pi、Redis、状态机和 WebSocket/React 原型，做出约每对球道 200–400 美元的开放系统 OpenLaneLink。HN 讨论热度很高，约 1200 points、128 comments。  
**为什么值得关注：** 这是典型“开源硬件 + 事件流 + Web UI”打穿垂直行业供应商锁定的案例。亮点不是省钱本身，而是把昂贵闭源行业设备拆解为传感器、继电器、状态机和可替换节点。  
**原文链接：** https://news.ycombinator.com/item?id=48968606

---

### 9. 《Minecraft Java 版现在使用 SDL3》
**摘要：** Minecraft Java Edition 的新快照公告中提到迁移到 SDL3。虽然官方页面抓取失败，但从 RSS 标题看，这意味着 Minecraft Java 的底层窗口、输入或平台抽象层发生了重要更新，转向新版 SDL 生态。  
**为什么值得关注：** Minecraft Java 是巨大规模的跨平台桌面应用。它采用 SDL3 对游戏输入、窗口管理、控制器支持和跨平台兼容性都有信号意义，也可能推动更多 Java/游戏客户端现代化底层依赖。  
**原文链接：** https://www.minecraft.net/en-us/article/minecraft-26-3-snapshot-4

---

### 10. 《Claude Code 现在使用 Rust 版 Bun》
**摘要：** Simon Willison 检查本地 Claude Code 二进制，发现其中包含 `Bun v1.4.0` 字符串，而公开 Bun 最新稳定版还是 1.3.14；进一步用 `strings` 搜索 `.rs` 文件路径，找到 563 个 Rust 源文件路径，说明 Claude Code 内嵌并运行了尚未正式稳定发布的 Rust 版 Bun。作者还给出用 `BUN_OPTIONS --preload` 打印内嵌 Bun 版本的小技巧。  
**为什么值得关注：** 这说明 Rust 重写版 Bun 已经在 Claude Code 这种大规模分发的生产工具中运行。对 JS runtime、AI coding CLI 打包、单文件工具链分发、Rust 替代 Zig/C++ 实现都有观察价值。  
**原文链接：** https://simonwillison.net/2026/Jul/19/claude-code-in-bun-in-rust/

---

已处理并标记本轮 HackerNews RSS 新帖为已读。
