# Alert System

Rules, events, notification channels, and escalation

### Alert Rule Types

#### SNMP Alert Rules

Trigger when an OID value matches a condition: greater than, less than, equals, not equals, contains, regex, or percentage thresholds. Supports compare-to-OID for percentage calculations.

Conditions: `gt, lt, eq, ne, contains, regex, pct_gt, pct_lt`

#### Monitor Alert Rules

Trigger when a service monitor condition is met: status down, response time exceeds threshold, SSL certificate expiring soon, or body content mismatch.

Conditions: `status_down, response_time_gt, ssl_expiry_lt, body_mismatch`

#### Webhook Alert Rules

Trigger based on incoming webhook data: status changes, payload field comparisons (equals, contains, greater/less than).

Conditions: `status_down, status_up, payload_eq, payload_ne, payload_contains, payload_gt, payload_lt`

### Common Alert Rule Options

- **Severity** — Info, Warning, or Critical. Determines notification urgency and badge color.

- **Consecutive Failures** — Number of consecutive failures required before triggering (avoids false alarms from transient issues).

- **Cooldown** — Minimum minutes between repeated notifications for the same rule.

- **Escalation** — (SNMP only) Auto-escalate severity after N minutes if not acknowledged.

- **Notify on Recovery** — Send a recovery notification to all channels when the condition clears.

- **Notification Channels** — Select which channels receive notifications for this rule.

### Alert Events

When a rule triggers, an alert event is created with status "open". Events can be acknowledged (by a user) or resolved (manually or automatically when the condition clears). The unified Alert Events page shows all events from SNMP, monitor, and webhook sources with filtering by source, status, severity, and date range. Bulk clear operations are available.

### In-App Notifications

All alert events (SNMP, monitor, webhook) automatically generate in-app bell notifications for admin users, regardless of configured notification channels. The bell icon in the top bar shows unread count with a live-updating dropdown, and plays a configurable sound the moment a new notification arrives — see [Sounds & audio cues](#sounds) for how to pick the sound or mute the bell.
