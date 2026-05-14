# Notification Channels

Email, SMS, Slack, and webhook notification delivery

Notification channels define how alert notifications are delivered. Multiple channels can be attached to each alert rule.

#### Email

SMTP-based email delivery. Supports any SMTP server, Mailgun, or Amazon SES. Rich HTML templates with device info, severity badges, and metric details. Configure per-channel recipients.

#### SMS (Twilio)

SMS via Twilio. Configure account SID, auth token, from number, and to number. Short text messages with device name, alert name, and current value.

#### Slack

Slack incoming webhook integration. Rich attachment format with color-coded severity. Provide your Slack webhook URL and optional channel override.

#### Webhook

Custom HTTP POST to any URL. JSON payload with full event details. HMAC-SHA256 signature via `X-ACS-Signature` header. 3 retries with exponential backoff (1m, 5m, 15m).

### Testing Channels

Each channel has a "Send Test" button that dispatches a test notification to verify configuration before attaching it to alert rules.

### Notification Log

All sent notifications are logged with delivery status (sent/failed), error messages, recipient, and timestamp. Access via **Notification Log** in the sidebar.
