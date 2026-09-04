
复核确认：www/old.reddit.com 全部 TCP 超时（000），redlib 公共实例要么超时要么 403 bot challenge，而 GitHub/百度正常——与 skill 中 2026-08-17 记录的「Reddit IP 层 TCP 封锁」状态完全一致。恢复探针（`curl -sI https://www.reddit.com/`）未返回 200，redlib.cow.rip 仍为 403 challenge，无可用缓存，RSS 同 IP 段必然失败，blogwatcher scan 亦跳过。

[SILENT]
