# Website Monitoring

HTTP, HTTPS, and SSL certificate monitoring for websites

Monitor the availability, performance, and SSL certificate health of your websites and web applications using HTTP, HTTPS, and SSL service monitors.

### Recommended Setup

For each website you want to monitor, create the following service monitors:

- **HTTPS Monitor** — the primary check. Set the host to your domain (e.g. `www.example.com`), configure the expected HTTP status code (usually `200`), and optionally add a body regex to verify the page content is correct (e.g. a keyword that should always appear on the page). Enable **Follow Redirects** if the site redirects HTTP to HTTPS. Set the **SSL expiry alert** threshold (default 14 days) to be notified before the certificate expires.

- **SSL Certificate Monitor** — a dedicated SSL check for more detailed certificate monitoring. Set warning and critical thresholds (e.g. 30 days warning, 14 days critical). The monitor tracks the full certificate chain, issuer, SANs, and cipher details. Use this when you need separate alert rules for certificate issues vs site availability.

- **Ping Monitor** — checks basic network reachability of the web server. If ping fails but HTTPS succeeds, this can indicate intermittent network issues. If both fail, the server is likely unreachable.

### HTTP vs HTTPS

Use an **HTTPS** monitor for any site with an SSL certificate — it validates the certificate as part of the check and can alert on upcoming expiry. Use an **HTTP** monitor only for sites that don't use SSL, or for specifically checking the non-SSL version of a site (e.g. verifying it redirects to HTTPS).

### Configuration

| Setting | Guidance |
| --- | --- |
| Expected Status | `200` for standard pages. `301`/`302` if checking a redirect endpoint with Follow Redirects off. |
| Body Regex | A keyword that always appears on the page (e.g. company name, footer text). Catches cases where the server returns 200 but serves an error page or blank content. |
| Follow Redirects | Enable for sites that redirect (e.g. HTTP → HTTPS, www → non-www). Disable if you want to specifically verify the redirect itself. |
| SSL Verify | Keep enabled for production sites. Disable only for self-signed certificates on internal/staging sites. |
| Custom Headers | Add `Host` for virtual hosts, `Authorization` for basic auth sites, or any headers the site requires. |
| Check Interval | 60s for most sites. 30s for critical customer-facing sites. 300s for lower-priority internal sites. |
| Timeout | 5000ms default. Increase for sites on slower connections. If the site consistently exceeds the timeout, the check reports as down. |
| SSL Expiry Alert | 14 days default on HTTPS monitors. Set higher (e.g. 30 days) for critical sites to allow more time to renew. |

### Alert Rules for Websites

Create alert rules on your website monitors to be notified immediately when issues occur:

- **Status Down** — triggers when the site is unreachable or returns an unexpected status code. Set consecutive failures to 2-3 to avoid false alarms from transient network blips.

- **Response Time** — triggers when the site becomes slow (e.g. response time > 3000ms). Useful for catching performance degradation before users notice.

- **SSL Expiry** — triggers when the certificate is close to expiry. Set to 14-30 days so you have time to renew.

- **Body Mismatch** — triggers when the expected content is missing from the page. Catches defacement, broken deployments, or CDN issues serving stale content.

### Monitoring Multiple Sites

When monitoring many websites, use **tags** (e.g. "websites", "customer-sites", "staging") and **monitor groups** to keep them organised. Add a **Status Grid** widget to your dashboard filtered to your website group for an at-a-glance overview of all monitored sites. The **SSL Expiry List** widget shows all HTTPS monitors with their certificate expiry dates, colour-coded by urgency.

**Tip:** For customer websites, combine website monitoring with [Scoped User Views](#scoped-views) — give each customer a dashboard showing only their website monitors, with notification channels routing alerts directly to their team.
