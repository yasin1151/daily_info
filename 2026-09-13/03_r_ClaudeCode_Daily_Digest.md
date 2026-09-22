
All Reddit endpoints and every redlib instance are unreachable, while the control probes (GitHub 200, Baidu 200) work — this is the IP-layer block condition, not a local outage:

- `www.reddit.com`, `old.reddit.com` (hot HTML + `.rss`) → `000` / 0 bytes across 3 retry rounds each
- 6 redlib instances (perennialte, bloat.cat, safereddit, catsarch, nadeko, artemislena) → all `000`
- `blogwatcher-cli scan "r/ClaudeCode"` → `dial tcp 104.244.42.197:443: i/o timeout`
- `blogwatcher-cli articles --blog "r/ClaudeCode"` → `No unread articles!`

Per the redlib skill's判定标准 (Reddit 全端点 `000`+i/o timeout, all redlib instances down, and control hosts fine), there is no reachable source and no cached unread content to work from.

[SILENT]
