# SNMP Traps

Receive and manage SNMP trap notifications

The SNMP trap receiver listens for incoming trap notifications from network devices. Traps are logged with full varbind data and can be acknowledged, archived, or deleted.

### Trap Settings

Configure the listening port and community string from the trap settings panel. The probe service handles trap reception and forwards them to the application backend via internal API.

### Trap List

View all received traps with source IP, OID, timestamp, severity, and varbind data. Auto-matches traps to known devices by IP address. Filter, search, and perform bulk operations (delete, archive, acknowledge).
