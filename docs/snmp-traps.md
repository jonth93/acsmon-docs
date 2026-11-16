# SNMP Traps

Receive and manage SNMP trap notifications

The SNMP trap receiver listens for incoming trap notifications from network devices. Traps are logged with full varbind data and can be acknowledged, archived, or deleted.

### Trap Settings

Configure the listening port and community string from the trap settings panel. The probe service handles trap reception and forwards them to the application backend via internal API.

The receiver accepts a trap only when its community is one it knows: the trap community set here, the default SNMP community (Settings → SNMP), or the community of any active SNMPv1/v2c device. The saved trap community is never shown; leave the field blank to keep it, or tick **Remove saved community** to clear it. With no community known at all, no traps are accepted — unless **Accept traps with any community** is ticked. That switch is off by default and not recommended (anyone who can reach the trap port could inject traps); installs that were already receiving traps with no community configured are switched to it on upgrade so traps keep arriving — list your communities and switch it off.

### Trap List

View all received traps with source IP, OID, timestamp, severity, and varbind data. Auto-matches traps to known devices by IP address. Filter, search, and perform bulk operations (delete, archive, acknowledge).
