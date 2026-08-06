
The digest is complete, QA-passed, and verified by read-back. All three entries are technically relevant (plugin/marketplace, packaging/memory, project-data integrity), each has a 150-300 CJK-char summary with background + core + why-it-matters, exactly 3 real high-signal comments with usernames and 赞数 (honestly labeled 隐藏 where reddit hides them), and original post links. I skipped low-information/showcase posts and the honest-1-star complaint noise was filtered.

# r/UnrealEngine 今日热帖 Digest（2026-08-07）

## 1. 免费 UE 插件遭“无声 1 星差评”，开发者谈 Fab 市场生态
**主题：** 插件 / Fab 市场 / 评分机制

**摘要：** 一位独立开发者发布了一款免费的运行时网格绘制（runtime mesh painting）插件，目标是替代同类付费方案，结果上线后接连收到多条“只打 1 星、不写评论、不上报 Bug”的匿名差评。开发者坦言这让他既无法定位问题，也怀疑存在恶意刷差评的同行竞争，并直言如果这种情况持续，他会重新考虑是否继续免费开源更多插件。评论区既有买家对无声评分的不信任，也有技术向的 Fab 安装故障排查经验（清理 Epic Launcher 缓存、等待 Fab 刷新按钮变黄），还有“免费上架是否低估长期维护成本”的尖锐反问。这个帖子切中当前 UE 插件分发渠道 Fab 的评分公平性问题，对正在或准备上架市场的开发者有直接的参考价值。

**高赞评论：**
1. u/MarcusBuer（赞数：隐藏）：Fab 安装失败通常是因为刷新按钮还处于灰色状态——Fab 仍在更新资源列表，只有按钮变成亮黄色后才能安装，而这个过程可能占满你的内存和显存。
2. u/obviouslydeficient（赞数：隐藏）：如果插件确实好用，随着更多人试用迟早会有更好评价。既然是免费发布的，有没有考虑过把它开源自托管？
3. u/penguished（赞数：隐藏）：反问一句——为什么要把免费的东西放到市场里拉低行情？大多数人上架都是靠它赚钱的。也别低估长期支援维护的成本，用户迟早会要更新和补丁。

**原帖：** https://www.reddit.com/r/unrealengine/comments/1vh7ffu/

## 2. UE5 打包内存耗尽陷入“死循环”，实测给出排查与配置思路
**主题：** 打包 / 内存 / Cook 管线

**摘要：** 一位开发者在用 64GB 内存的机器通过 Project Launcher 打包时，发现 UE5.6 在 Cook 阶段反复把内存抽干到约 30% 再重新填满，陷入所谓的“无限循环”，导致原本 5–10 分钟能完成的打包拖到 50 分钟以上甚至卡死。他一度想靠升到 128GB 内存解决，但评论区技术向回复一致指出：问题根源更可能出在损坏的缓存资源或 Cook 配置，而非内存容量。有经验者建议清理 DX Cache 与 Build 目录后重新构建、用命令行方式打包以节省内存，还有人贴出 DefaultEditor.ini 里 CookSettings 相关的 GC 与内存保护开关供对照排查。对经常做大项目打包、遇到内存边界问题的 UE 开发者来说，这套“先查缓存和配置、再考虑加内存”的思路非常实用。

**高赞评论：**
1. u/vexargames（10赞）：你要先修掉导致死循环的根因——很可能是缓存里有损坏的资源，它一直在尝试替换然后就耗尽内存。清掉 DX Cache 和 Build 目录重新开始，加内存并不能解决，只会让它转更久再耗尽。
2. u/botman（3赞）：如果它是在 Cook 阶段内存耗尽，其实只需要等——它会用掉内存、垃圾回收释放、再继续 Cook，并非真正的死循环，只是可能需要好几个小时。另外你说虚拟内存充足，但按项目体积你可能需要 200 或 300GB 的虚拟内存。
3. u/edromrom（1赞）：可以试试两点：一是把 PC 虚拟分页开到 128GB，用磁盘顶内存（慢但通常够用）；二是在 DefaultEditor.ini 的 [CookSettings] 里检查 MemoryMinFreePhysical、MemoryTriggerGCAtPressureLevel、MemoryMaxUsedPhysical 等内存保护开关。

**原帖：** https://www.reddit.com/r/unrealengine/comments/1vga9sm/

## 3. 16GB 优盘竟“装下”33GB 工程：项目数据损坏的警示
**主题：** 项目数据 / 备份 / 工作流

**摘要：** 一位虚拟拍摄新手发现，自己一直在 16GB 优盘上工作的 UE 工程竟然显示有 33GB，且复制粘贴到桌面时报“0x80004005 未指定错误”。评论区指出这多半是假优盘（刷固件假装容量更大）或 FAT32 文件分配表损坏导致的数据截断，属于数据恢复问题而非 UE 本身。经验者强调第一要务是立刻停止使用该盘、避免覆盖写入，可用 robocopy 以不重试方式抢救能拷出的文件；也有开发者建议删掉 Binaries、Build、Intermediate、Saved 等可重建目录来腾空间，或者把资源迁移到空工程。对习惯在移动盘或单点存储上直接编辑 UE 工程的人，这是一次关于“工程备份与存储安全”的及时提醒。

**高赞评论：**
1. u/ComfortableWait9697（赞数：隐藏）：希望你不是网购的这个优盘——市面上有大量刷了假固件、虚标容量的盘，比如 4GB 冒充 64GB，超出部分会循环覆盖旧数据。文件表看似完好，实际读写早坏了，可用 robocopy 的 /R:0 /W:0 强行抢救能读出的文件。
2. u/Pubbebubben（赞数：隐藏）：有些目录是安全可删的，删除后需要重建工程，但能腾出足够空间把项目拷出来。Binaries、Build、Intermediate 和 Saved 都可以安全删除（注意 Saved 里可能含备份）。
3. u/TehBens（赞数：隐藏）：看起来地图文件已经丢了。这个优盘别再用来放任何重要东西，它很可能继续破坏更多文件。建议把最新状态推到 GitHub 备份——虽然不一定用得顺手，但能保证这类悲剧不再发生。

**原帖：** https://www.reddit.com/r/unrealengine/comments/1vh60m9/
