# Unified Device Hub

Single pane of glass for all device data

The Device Hub is the primary device management interface. It combines SNMP data, service monitors, webhooks, alert events, and traps into a single unified view per device.

### Device List

The device list shows all devices across all types with real-time status indicators (up/down/unknown), last poll time, and IP address. You can filter by group, status, and search by name or IP. Bulk delete is available via checkboxes.

### Device Detail Tabs

#### Overview

SNMP system info (sysName, sysDescr, uptime), device details (IP, type, group, location), status badge, and live metric charts. Tabbed OID groups for organized viewing.

#### Service Monitors

All service monitors linked to this device. Auto-discover services to create monitors automatically. Link existing monitors or create new ones directly.

#### Webhooks

Create webhook endpoints per device. Each webhook gets a unique ingest URL. Configure alert rules on webhook payloads with conditions like payload_contains, payload_gt, status_down, etc.

#### Alerts & Traps

Combined view of all SNMP alert events, monitor events, and webhook events for this device. Also shows SNMP traps received from this device's IP.

### Auto-Discovery of Services

Click "Discover Services" on any device to automatically probe common ports (HTTP, HTTPS, SSH, SMTP, FTP, DNS, MySQL, etc.) and detect which services are running. One-click creation of monitors for all discovered services.

### Auto Alert Rules

Generate recommended alert rules based on the device's monitored OIDs. Automatically creates sensible thresholds for CPU, memory, disk, interface utilization, and other common metrics.
