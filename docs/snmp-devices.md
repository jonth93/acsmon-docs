# SNMP Devices

SNMP polling, OIDs, and metric collection

SNMP devices are polled on a configurable interval to collect metric data from OIDs. Supports SNMP v1, v2c, and v3 (with full auth/priv options).

### Adding a Device

- Navigate to **SNMP Devices** and click **"+ Add Device"**

- Enter device name, IP address, and SNMP version

- For v1/v2c: enter community string. For v3: configure username, auth/priv protocols and passwords

- Optionally assign a device group, type, location, and custom poll interval

- Save and trigger an initial SNMP Walk to discover available OIDs

### OID Management

After performing an SNMP Walk, discovered OIDs are listed on the device detail page. Toggle monitoring on specific OIDs to include them in regular polls. Monitored OIDs have their values stored for time-series graphing. OIDs are grouped by category (system, interfaces, storage, CPU, etc.) for organized viewing.

### Manual Poll & Live Data

Trigger an on-demand poll of any device to get fresh data immediately. The device detail page shows live metric values that update in real-time via WebSocket when auto-refresh is enabled.

### Bulk Operations

Select multiple devices via checkboxes on the list page to perform bulk poll or bulk delete operations.
