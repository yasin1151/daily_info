
Reddit 全端点网络层封锁持续，无可用数据源：

- `www.reddit.com` → http=000, exit=28（connect timeout），DNS 仍返回真实 IP（`www.reddit.com`→157.240.7.20 / `old.reddit.com`→104.244.42.197）→ TCP 层封锁，非 DNS 劫持
- `old.reddit.com/r/ClaudeCode/hot/`、`/hot/.rss` → 均 000 / 0 字节
- redlib 实例探测：`safereddit.com`、`catsarch`、`artemislena`、`privacyredirect`、`nadeko`、`perennialte.ch`、`rl.bloat.cat` → 全部 000；仅 `redlib.cow.rip` 返回 403 Cloudflare challenge（非恢复信号）
- 对照探针：百度 200、GitHub 200 → 网络整体正常，仅 Reddit IP 段被封锁

按技能判定标准（Reddit 全端点 000 + i/o timeout、所有 redlib 实例不可达、无可用代理/缓存），跳过 blogwatcher scan（RSS 同 IP 段必然失败），不执行 read-all，避免把未推送的内容误标已读。

[SILENT]
