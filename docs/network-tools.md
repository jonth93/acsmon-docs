# Network Diagnostic Tools

On-demand diagnostic utilities

Network tools run interactively from the UI. Results stream live via WebSocket and are cached briefly in Redis (5-minute TTL). These are not continuous monitors — they run on demand.

For security, the tools will not target ACS Monitor's own internal network: loopback (`127.0.0.1`, `localhost`), link-local addresses (including the cloud metadata address `169.254.169.254`) and the private container network its own services run on. A web address that redirects there is refused at the redirect. Your own networks (for example `10.x`, `172.16.x`, `192.168.x`) are not affected. The same block applies to service monitors (their host, DNS resolver and web address) and to alert channels (webhook and Slack URLs, custom SMTP hosts), whether they are created in the web interface, through the REST API or by an AI agent over MCP; a channel already pointing there is refused when you send a test. A web monitor's path must start with `/`. Network discovery scans an IPv4 subnet of at most a `/16` (split larger ranges into several scans). To monitor the Docker host that runs ACS Monitor itself, use the host's LAN IP address (for example `192.168.1.20`) — the container network's gateway address is blocked deliberately, as it is part of that internal network. In the rare case this blocks something you need, set `PROBE_ALLOW_INTERNAL_TARGETS=true` and restart; `PROBE_INTERNAL_CIDRS` adds further networks to block (comma-separated CIDRs). Both settings must reach **both** the app and the probe containers (the app checks targets before a run, the probe checks them again when it connects): set them in `.env` and make sure the probe service's `environment:` in `docker-compose.yml` passes them through too, then `docker compose up -d`.

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
