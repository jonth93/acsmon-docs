# Service Monitors

Multi-protocol endpoint monitoring

Service monitors check the availability and performance of network services at configurable intervals. Each check records response time, status, and protocol-specific metadata.

### Supported Monitor Types

| Type | Default Port | Description |
| --- | --- | --- |
| ping | ICMP | ICMP echo with RTT, jitter, and packet loss |
| tcp | — | TCP port open/close check with optional send/expect strings |
| http | 80 | HTTP check: status code, body regex, redirect following |
| https | 443 | HTTPS check + SSL certificate validation and expiry tracking |
| ssh | 22 | SSH banner check with optional auth and command execution |
| smtp | 25/587 | SMTP banner and optional auth check |
| ftp | 21 | FTP banner check |
| pop3 | 110 | POP3 banner check |
| imap | 143 | IMAP banner check |
| dns | 53 | DNS query check (A, AAAA, MX, CNAME, TXT, NS, SOA) |
| mysql | 3306 | MySQL/MariaDB connection check |

### Monitor Detail Page

Each monitor's detail page shows current status, response time chart (time-series), uptime percentage (7-day and 30-day), recent check results, SSL certificate details (for HTTPS), and linked alert rules. Live data updates via WebSocket.

### Monitor Groups

Organize monitors into groups with custom names and colors. Groups can be used to filter the monitor list and organize status views.

### Tags

Add tags to monitors for flexible categorisation beyond groups. Tags are displayed as clickable badges in the monitors table — click one to filter by that tag. When adding or editing a monitor, the tag input suggests existing tags as you type for consistency. Tags are also searchable from both the monitor list search bar and the global search (Ctrl+K). Use tags for cross-cutting labels like "production", "customer-facing", "legacy", or customer names.

### Uptime Tracking

Uptime percentages are calculated from stored check results. 7-day and 30-day windows are computed and cached for quick display. The uptime timeline widget visualizes this data on dashboards.
