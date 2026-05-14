# Network Diagnostic Tools

On-demand diagnostic utilities

Network tools run interactively from the UI. Results stream live via WebSocket and are cached briefly in Redis (5-minute TTL). These are not continuous monitors — they run on demand.

| Tool | Description |
| --- | --- |
| Ping | ICMP echo: min/avg/max RTT, packet loss %, jitter |
| Traceroute | Hop-by-hop route with RTT per hop and hostname resolution (live streaming) |
| Port Scanner | TCP port range scan with service name lookup (live streaming) |
| SSL Check | Full certificate chain, expiry, SANs, issuer, cipher details |
| HTTP Headers | Full request/response headers, redirect chain, timing |
| DNS Lookup | Query A, AAAA, MX, TXT, NS, CNAME, SOA, PTR records |
| WHOIS | Domain and IP registration info lookup |

**Permission required:** `monitors.run_tools`. Tools are rate-limited: max 10 concurrent tool jobs per user session. Results broadcast only to the requesting user's private WebSocket channel.
