
All Reddit access paths are down this round — verified across every documented route:

- **Reddit endpoints** (`www.reddit.com`, `old.reddit.com`, RSS `.rss`, `hot/`): all `000` / `rc=28` (i/o timeout), 0 bytes — IP-layer TCP block, DNS still resolves (104.244.42.197).
- **redlib instances** (perennialte, safereddit, catsarch, artemislena, nadeko, bloat.cat, privacyredirect, privacydev): all `000` (timeout/exit 35).
- **redlib.cow.rip**: only `403` Cloudflare "Just a moment…" challenge.
- **Proxies** (rsshub, allorigins, r.jina.ai): `000` or empty upstream body.
- **Control probes**: baidu `200`, github `200`, google `000` — so the block is Reddit/redlib-specific, not a total network outage.
- **No usable cache**: only a stale 2-day-old unrelated HTML in `/tmp/rllm_digest/`; nothing from today.

This matches the documented Reddit IP-layer blockade criterion (Reddit 全端点 000 + 所有 redlib 实例不可达). No candidates could be retrieved, so no digest can be produced without fabricating content. Skipping blogwatcher scan (same IP range, would fail identically).

[SILENT]
