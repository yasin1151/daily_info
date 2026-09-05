
Full picture confirmed — this matches the documented network-block scenario exactly:

- **Reddit direct** (`www`/`old`/`api.reddit.com`, both DNS-default and forced real IPs 104.244.42.x, 185.45.5.x): all `000` TCP timeouts → IP-level block
- **Redlib instances** (perennialte, catsarch, privacyredirect, artemislena, safereddit, nadeko, privadency, tux.pizza, bloat.cat, privacydev): all `000`; only **cow.rip** responds, with a Cloudflare "Just a moment..." challenge (403)
- **Fallback proxies** (r.jina.ai, web.archive.org, Reddit RSS): all `000`
- Network itself is up (GitHub 200, Baidu 200, gstatic reachable) → selective blocking of Reddit/Google
- Recovery probe fails: `www.reddit.com` not 200, `redlib.cow.rip` still 403/challenge
- Forbidden in unattended cron: router proxy ports (security-scan hang), browser_exec (auth popup)

All documented recovery criteria for [SILENT] are met — no content source for r/LLM is reachable, and there is no legitimate cached data to fall back on.

[SILENT]
