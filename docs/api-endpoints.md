# API Endpoints

Complete endpoint reference for all resources

Authentication
3 endpoints

- **POST** `/api/v1/auth/login` — Authenticate and receive a bearer token
*Permission:* `Public`

- **POST** `/api/v1/auth/logout` — Revoke the current token
*Permission:* `Authenticated`

- **GET** `/api/v1/auth/me` — Get current user info, roles, and permissions
*Permission:* `Authenticated`

SNMP Devices
8 endpoints

- **GET** `/api/v1/devices` — List all devices (filterable, paginated)
*Permission:* `devices.view`

- **POST** `/api/v1/devices` — Create a new SNMP device
*Permission:* `devices.create`

- **GET** `/api/v1/devices/{id}` — Get device details with OIDs
*Permission:* `devices.view`

- **PUT** `/api/v1/devices/{id}` — Update a device
*Permission:* `devices.edit`

- **DELETE** `/api/v1/devices/{id}` — Delete a device
*Permission:* `devices.delete`

- **POST** `/api/v1/devices/{id}/poll` — Trigger an immediate SNMP poll
*Permission:* `devices.edit`

- **POST** `/api/v1/devices/{id}/walk` — Perform an SNMP walk to discover OIDs
*Permission:* `devices.edit`

- **GET** `/api/v1/devices/{id}/metrics` — Get time-series metrics
*Permission:* `devices.view`

Device Groups
5 endpoints

- **GET** `/api/v1/device-groups` — List all device groups
*Permission:* `devices.view`

- **POST** `/api/v1/device-groups` — Create a device group
*Permission:* `device-groups.create`

- **GET** `/api/v1/device-groups/{id}` — Get a device group
*Permission:* `devices.view`

- **PUT** `/api/v1/device-groups/{id}` — Update a device group
*Permission:* `device-groups.edit`

- **DELETE** `/api/v1/device-groups/{id}` — Delete a device group
*Permission:* `device-groups.delete`

OIDs
6 endpoints

- **GET** `/api/v1/devices/{device}/oids` — List OIDs for a device
*Permission:* `devices.view`

- **POST** `/api/v1/devices/{device}/oids` — Create an OID on a device
*Permission:* `devices.edit`

- **GET** `/api/v1/oids/{id}` — Get OID details
*Permission:* `devices.view`

- **PUT** `/api/v1/oids/{id}` — Update an OID
*Permission:* `devices.edit`

- **DELETE** `/api/v1/oids/{id}` — Delete an OID
*Permission:* `devices.delete`

- **POST** `/api/v1/oids/{id}/toggle-monitor` — Toggle monitoring on/off for an OID
*Permission:* `devices.edit`

Device Webhooks
12 endpoints

Webhook CRUD

- **GET** `/api/v1/devices/{device}/webhooks` — List webhooks for a device, including their ingest tokens
*Permission:* `devices.view + webhooks.edit`

- **POST** `/api/v1/devices/{device}/webhooks` — Create a webhook on a device
*Permission:* `devices.create`

- **GET** `/api/v1/devices/{device}/webhooks/{webhook}` — Get webhook details (the ingest token is included only with webhooks.edit)
*Permission:* `devices.view`

- **PUT** `/api/v1/devices/{device}/webhooks/{webhook}` — Update a webhook
*Permission:* `devices.edit`

- **DELETE** `/api/v1/devices/{device}/webhooks/{webhook}` — Delete a webhook
*Permission:* `devices.delete`

- **POST** `/api/v1/devices/{device}/webhooks/{webhook}/toggle` — Toggle webhook active/inactive
*Permission:* `devices.edit`

- **GET** `/api/v1/devices/{device}/webhooks/{webhook}/events` — List webhook ingest events (paginated)
*Permission:* `devices.view`

Webhook Alert Rules

- **GET** `/api/v1/devices/{device}/webhooks/{webhook}/alert-rules` — List alert rules for a webhook
*Permission:* `alerts.view`

- **POST** `/api/v1/devices/{device}/webhooks/{webhook}/alert-rules` — Create a webhook alert rule
*Permission:* `alerts.create`

- **PUT** `/api/v1/devices/{device}/webhooks/{webhook}/alert-rules/{rule}` — Update a webhook alert rule
*Permission:* `alerts.edit`

- **DELETE** `/api/v1/devices/{device}/webhooks/{webhook}/alert-rules/{rule}` — Delete a webhook alert rule
*Permission:* `alerts.delete`

SNMP Traps
4 endpoints

- **GET** `/api/v1/snmp-traps` — List SNMP traps (filter by status, severity, device, search)
*Permission:* `devices.view`

- **GET** `/api/v1/snmp-traps/{id}` — Get trap details with varbinds
*Permission:* `devices.view`

- **POST** `/api/v1/snmp-traps/{id}/acknowledge` — Acknowledge a trap
*Permission:* `alerts.acknowledge`

- **DELETE** `/api/v1/snmp-traps/{id}` — Delete a trap
*Permission:* `devices.delete`

Service Monitors
8 endpoints

- **GET** `/api/v1/monitors` — List monitors (filter by status, type, group, search)
*Permission:* `monitors.view`

- **POST** `/api/v1/monitors` — Create a new service monitor
*Permission:* `monitors.create`

- **GET** `/api/v1/monitors/{id}` — Get monitor details with group and recent results
*Permission:* `monitors.view`

- **PUT** `/api/v1/monitors/{id}` — Update a monitor
*Permission:* `monitors.edit`

- **DELETE** `/api/v1/monitors/{id}` — Delete a monitor
*Permission:* `monitors.delete`

- **POST** `/api/v1/monitors/{id}/check` — Trigger an immediate manual check
*Permission:* `monitors.edit`

- **GET** `/api/v1/monitors/{id}/results` — Get recent check results
*Permission:* `monitors.view`

- **GET** `/api/v1/monitors/{id}/uptime` — Get uptime statistics (7d, 30d)
*Permission:* `monitors.view`

Monitor Groups
5 endpoints

- **GET** `/api/v1/monitor-groups` — List all monitor groups
*Permission:* `monitors.view`

- **POST** `/api/v1/monitor-groups` — Create a monitor group
*Permission:* `monitor-groups.create`

- **GET** `/api/v1/monitor-groups/{id}` — Get a monitor group
*Permission:* `monitors.view`

- **PUT** `/api/v1/monitor-groups/{id}` — Update a monitor group
*Permission:* `monitor-groups.edit`

- **DELETE** `/api/v1/monitor-groups/{id}` — Delete a monitor group
*Permission:* `monitor-groups.delete`

SNMP Alert Rules
5 endpoints

- **GET** `/api/v1/alert-rules` — List SNMP alert rules (filter by device, severity, active)
*Permission:* `alerts.view`

- **POST** `/api/v1/alert-rules` — Create an SNMP alert rule with channels
*Permission:* `alerts.create`

- **GET** `/api/v1/alert-rules/{id}` — Get rule with device, OID, channels, recent events
*Permission:* `alerts.view`

- **PUT** `/api/v1/alert-rules/{id}` — Update rule and sync channels
*Permission:* `alerts.edit`

- **DELETE** `/api/v1/alert-rules/{id}` — Delete rule and detach channels
*Permission:* `alerts.delete`

SNMP Alert Events
4 endpoints

- **GET** `/api/v1/alert-events` — List SNMP alert events (paginated)
*Permission:* `alerts.view`

- **GET** `/api/v1/alert-events/{id}` — Get alert event details
*Permission:* `alerts.view`

- **POST** `/api/v1/alert-events/{id}/acknowledge` — Acknowledge an open alert
*Permission:* `alerts.acknowledge`

- **POST** `/api/v1/alert-events/{id}/resolve` — Manually resolve an alert
*Permission:* `alerts.acknowledge`

Monitor Alert Rules
5 endpoints

- **GET** `/api/v1/monitor-alert-rules` — List monitor alert rules
*Permission:* `alerts.view`

- **POST** `/api/v1/monitor-alert-rules` — Create a monitor alert rule
*Permission:* `alerts.create`

- **GET** `/api/v1/monitor-alert-rules/{id}` — Get monitor alert rule details
*Permission:* `alerts.view`

- **PUT** `/api/v1/monitor-alert-rules/{id}` — Update a monitor alert rule
*Permission:* `alerts.edit`

- **DELETE** `/api/v1/monitor-alert-rules/{id}` — Delete a monitor alert rule
*Permission:* `alerts.delete`

Monitor Events
4 endpoints

- **GET** `/api/v1/monitor-events` — List monitor alert events
*Permission:* `alerts.view`

- **GET** `/api/v1/monitor-events/{id}` — Get monitor event details
*Permission:* `alerts.view`

- **POST** `/api/v1/monitor-events/{id}/acknowledge` — Acknowledge a monitor event
*Permission:* `alerts.acknowledge`

- **POST** `/api/v1/monitor-events/{id}/resolve` — Resolve a monitor event
*Permission:* `alerts.acknowledge`

Alert Channels
6 endpoints

- **GET** `/api/v1/alert-channels` — List notification channels
*Permission:* `channels.view`

- **POST** `/api/v1/alert-channels` — Create a channel (email, sms, webhook, slack)
*Permission:* `channels.create`

- **GET** `/api/v1/alert-channels/{id}` — Get channel details
*Permission:* `channels.view`

- **PUT** `/api/v1/alert-channels/{id}` — Update a channel
*Permission:* `channels.edit`

- **DELETE** `/api/v1/alert-channels/{id}` — Delete a channel
*Permission:* `channels.delete`

- **POST** `/api/v1/alert-channels/{id}/test` — Send a test notification
*Permission:* `channels.edit`

MIBs
4 endpoints

- **GET** `/api/v1/mibs` — List uploaded MIBs
*Permission:* `mibs.view`

- **POST** `/api/v1/mibs` — Upload a MIB file (multipart)
*Permission:* `mibs.upload`

- **GET** `/api/v1/mibs/{id}` — Get MIB details and parsed OIDs
*Permission:* `mibs.view`

- **DELETE** `/api/v1/mibs/{id}` — Delete a MIB
*Permission:* `mibs.delete`

Discovery
6 endpoints

- **GET** `/api/v1/discovery` — List discovery jobs
*Permission:* `discovery.view`

- **POST** `/api/v1/discovery` — Create a discovery job (subnet CIDR)
*Permission:* `discovery.create`

- **GET** `/api/v1/discovery/{id}` — Get job details with results
*Permission:* `discovery.view`

- **DELETE** `/api/v1/discovery/{id}` — Delete a discovery job
*Permission:* `discovery.create`

- **POST** `/api/v1/discovery/{id}/run` — Trigger a discovery scan
*Permission:* `discovery.run`

- **POST** `/api/v1/discovery-results/{id}/import` — Import a discovered device
*Permission:* `discovery.run`

Dashboards & Widgets
10 endpoints

- **GET** `/api/v1/dashboards` — List user dashboards
*Permission:* `dashboards.view`

- **POST** `/api/v1/dashboards` — Create a dashboard
*Permission:* `dashboards.create`

- **GET** `/api/v1/dashboards/{id}` — Get dashboard with widgets
*Permission:* `dashboards.view`

- **PUT** `/api/v1/dashboards/{id}` — Update dashboard settings (own dashboards; admins any)
*Permission:* `dashboards.edit`

- **DELETE** `/api/v1/dashboards/{id}` — Delete dashboard and all widgets (own dashboards; admins any)
*Permission:* `dashboards.delete`

- **GET** `/api/v1/dashboards/{id}/widgets` — List widgets on a dashboard
*Permission:* `dashboards.view`

- **POST** `/api/v1/dashboards/{id}/widgets` — Add a widget to a dashboard (own dashboards; admins any)
*Permission:* `dashboards.edit`

- **PUT** `/api/v1/widgets/{id}` — Update a widget's config (own dashboards; admins any)
*Permission:* `dashboards.edit`

- **DELETE** `/api/v1/widgets/{id}` — Remove a widget (own dashboards; admins any)
*Permission:* `dashboards.edit`

- **POST** `/api/v1/widgets/positions` — Batch update widget positions (every widget must be on a dashboard you may edit)
*Permission:* `dashboards.edit`

Users & Roles
8 endpoints

- **GET** `/api/v1/users` — List all users
*Permission:* `users.view`

- **POST** `/api/v1/users` — Create a user
*Permission:* `users.create`

- **GET** `/api/v1/users/{id}` — Get user details
*Permission:* `users.view`

- **PUT** `/api/v1/users/{id}` — Update a user
*Permission:* `users.edit`

- **DELETE** `/api/v1/users/{id}` — Delete a user
*Permission:* `users.delete`

- **GET** `/api/v1/roles` — List all roles with permissions
*Permission:* `roles.manage`

- **GET** `/api/v1/roles/{id}` — Get role details
*Permission:* `roles.manage`

- **PUT** `/api/v1/roles/{id}` — Update role permissions
*Permission:* `roles.manage`

Network Tools
7 endpoints

- **POST** `/api/v1/tools/ping` — Run a ping test (host, count)
*Permission:* `monitors.run_tools`

- **POST** `/api/v1/tools/traceroute` — Run a traceroute (host, max_hops)
*Permission:* `monitors.run_tools`

- **POST** `/api/v1/tools/port-scan` — Scan TCP port range (host, port_start, port_end)
*Permission:* `monitors.run_tools`

- **POST** `/api/v1/tools/ssl-check` — Check SSL certificate (host, port)
*Permission:* `monitors.run_tools`

- **POST** `/api/v1/tools/http-headers` — Inspect HTTP headers (url, follow_redirects)
*Permission:* `monitors.run_tools`

- **POST** `/api/v1/tools/dns-lookup` — DNS query (host, record_type, resolver)
*Permission:* `monitors.run_tools`

- **POST** `/api/v1/tools/whois` — WHOIS lookup (query)
*Permission:* `monitors.run_tools`

Webhook Ingest
1 endpoint

- **GET|POST** `/api/v1/webhook-ingest/{token}` — Receive webhook data (no auth, token-based)
*Permission:* `Public`

Notes:

- Accepts any JSON body — stored as the webhook event payload

- Query parameters are also captured

- Token is generated when creating a webhook on a device

- Source IP is logged for each ingest event

System
2 endpoints

- **GET** `/api/v1/system/health` — System health metrics (services, queues, DB)
*Permission:* `settings.view`

- **GET** `/api/v1/system/stats` — Application statistics (device/monitor counts)
*Permission:* `settings.view`
