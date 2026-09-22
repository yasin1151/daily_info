
All access paths to Reddit are down again this round, matching the documented IP-layer block:

- **Reddit endpoints**: `www.reddit.com`, `old.reddit.com`, `api.reddit.com`, `.rss` → all `000` with `curl (28) connect timeout` (i/o timeout, ~12s). No HTML/RSS retrieved.
- **redlib instances** (perennialte, bloat.cat, safereddit, catsarch, artemislena, privacyredirect, nadeko): all `000`/timeout; only `redlib.cow.rip` responds, and it returns `403 "Just a moment..."` (Cloudflare challenge, no content).
- **Third-party routes**: rsshub.app `000`, r.jina.ai `000`, web.archive.org `000`, api.allorigins.win `522` — no bypass.
- **blogwatcher scan**: `failed to fetch feed: ... dial tcp 104.244.42.197:443: i/o timeout` → no candidates.
- **Control probes**: github.com `200`, baidu `200` → network stack is fine; this is a Reddit-specific IP/TCP block, not a local outage.
- **Cache check**: `/tmp` holds no fresh Reddit content (only the 5631-byte Cloudflare challenge page from the prior round) — nothing valid to reuse.

No candidates could be fetched, so no digest was produced and `read-all` was intentionally **not** run (per skill discipline: never mark unread items read when no push succeeded).

[SILENT]
