# Users & Access Control

Role-based permissions, 2FA, and user management

### Default Roles

| Role | Access Level |
| --- | --- |
| Super Admin | Full unrestricted access — bypasses all permission checks. Includes system settings, role management, system health, and all other features. |
| Admin | All features including system health, documentation, user management, channels, and settings view — except role management and settings editing. |
| Operator | View devices, monitors, alerts, traps, MIBs, discovery, channels, notification log, and documentation. Can acknowledge/resolve alerts and traps, run network tools, and manage own dashboards. No access to settings, system health, users, or roles. |
| Viewer | Read-only access to devices, monitors, alerts, traps, MIBs, discovery, channels, notification log, and documentation. No access to settings, system health, users, or roles. |

### Permissions

Granular permission slugs control access to every resource. Custom roles can be created with any combination of these permissions.

| Category | Permission Slugs |
| --- | --- |
| SNMP Devices | `devices.view` `devices.create` `devices.edit` `devices.delete` |
| Device Groups | `device-groups.view` `device-groups.create` `device-groups.edit` `device-groups.delete` |
| Service Monitors | `monitors.view` `monitors.create` `monitors.edit` `monitors.delete` `monitors.run_tools` |
| Monitor Groups | `monitor-groups.view` `monitor-groups.create` `monitor-groups.edit` `monitor-groups.delete` |
| Alert Rules | `alert-rules.view` `alert-rules.create` `alert-rules.edit` `alert-rules.delete` |
| Alert Events | `alerts.view` `alerts.create` `alerts.edit` `alerts.delete` `alerts.acknowledge` |
| Notification Log | `notifications.view` |
| MIBs | `mibs.view` `mibs.upload` `mibs.delete` |
| Discovery | `discovery.view` `discovery.create` `discovery.run` |
| SNMP Traps | `traps.view` `traps.acknowledge` `traps.delete` |
| Dashboards | `dashboards.view` `dashboards.create` `dashboards.edit` `dashboards.delete` `dashboards.share` |
| Webhooks | `webhooks.view` `webhooks.create` `webhooks.edit` `webhooks.delete` |
| Users | `users.view` `users.create` `users.edit` `users.delete` `roles.manage` |
| Channels | `channels.view` `channels.create` `channels.edit` `channels.delete` |
| Settings | `settings.view` `settings.edit` |
| System | `system-health.view` `documentation.view` |
| System Maintenance | `system.restart-services` `system.restart-host` (host reboot is super-admin-only by default) |

### Two-Factor Authentication (2FA)

TOTP-based 2FA via Google Authenticator or similar apps. Enable from your profile page — scan the QR code, enter the verification code, and store your recovery codes securely. Recovery codes provide backup access if you lose your authenticator.

### Profile & API Tokens

Users can update their profile (name, email, avatar), change password, and manage API tokens from the profile page. API tokens are used for REST API authentication via Bearer tokens.
