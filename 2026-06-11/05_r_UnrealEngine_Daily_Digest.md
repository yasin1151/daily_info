
Every single domain resolves to a `198.18.x.x` IP. The router is running a transparent proxy (likely Surge/Clash in enhanced mode) that hijacks ALL DNS and routes through `198.18.x.x` virtual network interfaces. The proxy itself seems to be failing/offline today — TLS cannot complete for any external HTTPS service.

This is a router-level infrastructure issue. I cannot circumvent it from the command line in this cron session. The proxy/VPN on the router/gateway `192.168.88.229` needs to be restarted.

Given the situation — **all HTTPS is blocked** — I cannot fetch any Reddit/redlib content today. This is a genuine network infrastructure failure, not something I can work around. I'll report [SILENT] since no content can be gathered.

[SILENT]
