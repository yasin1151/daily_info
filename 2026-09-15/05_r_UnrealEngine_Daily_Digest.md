
All Reddit access paths are down at the network layer — verified across every documented fallback:

**Reddit direct (all exit 28, `dial tcp … i/o timeout`, http=000):** `www.reddit.com`, `old.reddit.com/r/unrealengine/hot/`, `www.reddit.com/r/unrealengine/hot/.rss`, `old.reddit.com/…/.rss`. DNS resolves fine (69.171.235.22 / 104.244.42.197), so this is an IP-layer TCP block, not DNS failure. Direct connects to Reddit's Fastly IPs (151.101.1.140 / .65.140 / .129.140 / .193.140 via `--resolve`) all timed out too (rc=28), confirming the block is at the IP layer.

**redlib instances (14 probed):** `safereddit.com`, `catsarch`, `artemislena`, `privacyredirect`, `nadeko`, `privadency`, `ducks.party`, `rl.bloat.cat`, `privacydev`, `l.opnxng.com`, `tux.pizza`, `kittywi.re`, `baczek.me`, `perennialte.ch` → all 000 (rc=28/35/6). `redlib.cow.rip` returns 403 Cloudflare "Just a moment..." challenge — not a recovery signal. `freedit.eu` returns an error page.

**Third-party proxies:** rsshub.app 000, r.jina.ai 000, api.allorigins.win 500, DoH (cloudflare-dns.com, 1.1.1.1) 000.

**Control probes:** github.com 200, api.github.com 200, baidu.com 200 → network overall healthy; only Reddit's IP range is blocked.

**Recovery probe:** `www.reddit.com` still 000 and `redlib.cow.rip` still 403 → not recovered. Per skill discipline I'm skipping the blogwatcher scan (same blocked IP range would just fail) and making no read-all marking.

This matches the documented判定标准 (Reddit all endpoints 000 + i/o timeout, all redlib instances unreachable, no usable proxy or cache), so there is no valid r/UnrealEngine data to report this round.

[SILENT]
