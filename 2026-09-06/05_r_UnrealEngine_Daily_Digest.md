
探针结果与 skill 中 2026-08-17 记录的"IP 层 TCP 封锁"场景完全一致：

- **Reddit 全端点**（www.reddit.com / old.reddit.com / RSS）：`000` + TCP 连接超时（非 SSL exit 35，是 connect 阶段 i/o timeout）
- **redlib/libreddit 全部实例**：perennialte / safereddit / nadeko / bloat.cat → 000 超时；artemislena → connection reset；cow.rip → 403 challenge
- **对照站点正常**：GitHub 200、百度 200 —— 确认是 Reddit 定向封锁而非代理断网
- **无可用缓存**：/tmp 下 digest 文件均属其他管线（总参谋部/HN，非 r/UnrealEngine 内容），无本轮 UE 有效缓存

按 skill 判定标准（Reddit 全端点 000+i/o timeout 且所有 redlib 实例不可达 → 直接 `[SILENT]`，RSS 同 IP 段必然失败），恢复探针（www.reddit.com 返回 200 / redlib.cow.rip 非 403）均未命中，无任何可行抓取路径，且无可用缓存可兜底。

[SILENT]
