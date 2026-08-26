
Reddit 全端点探测结果（2026-08-27 07:20 CST）：

- `www.reddit.com`：000 / i/o timeout（重试 3 次）→ IP 层 TCP 封锁，未恢复（恢复探针应返回 200）
- `old.reddit.com/r/unrealengine/hot/`：重试 5 次全部 0 字节 / 超时
- Reddit RSS：0 字节
- redlib 实例：cow.rip 返回 Cloudflare "Just a moment..." challenge（不可用），perennialte.ch / bloat.cat / privacyredirect / nadeko 全部 0 字节
- 对照组：baidu 200、github 200（本机网络正常，Reddit 域名被网络层封锁）

符合技能中记录的「Reddit 全端点 000 + i/o timeout 且所有 redlib 实例不可达 → 直接 [SILENT]」判定标准。代理端口与 browser_exec 在无人值守 cron 中均不可用，无可行回退路径，本轮不产出 digest。

[SILENT]
