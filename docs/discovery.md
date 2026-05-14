# Network Discovery

Automated subnet scanning and device import

Network discovery scans an entire subnet to find all devices and services. It goes beyond simple SNMP scanning — every live host is detected regardless of whether it supports SNMP.

### How Discovery Works

Discovery runs in three stages:

- **Ping sweep** — sends ICMP pings to every IP in the subnet to find all live hosts, whether or not they support SNMP.

- **SNMP probing** — queries live hosts for system information (hostname, sysDescr, sysObjectID, device type) using the SNMP version and credentials you configure. Hosts without SNMP are still kept as discovered devices.

- **Service detection** — probes each live host for common services: SSH (22), HTTP (80), HTTPS (443), SMTP (25), FTP (21), DNS (53), MySQL (3306), POP3 (110), IMAP (143), and RDP (3389). All probes run concurrently for speed.

### Running a Scan

- Create a discovery job with a subnet in CIDR notation (e.g. `192.168.1.0/24`)

- Specify SNMP version and credentials for the subnet

- Click **Run Now** to start the scan, or configure a cron schedule for periodic scans

- Progress updates live — shows IPs scanned and devices found in real-time

- Review results: each discovered IP shows hostname, system description, device type, and detected services

- Import individual devices or use **Import All** for bulk creation

### Auto-Import & Service Monitors

When importing a discovered device, service monitors are automatically created for every service that was detected on that host. For example, if a host responds on ports 22 (SSH) and 443 (HTTPS), both an SSH monitor and an HTTPS monitor are created alongside the device — ready to start checking immediately.

### Scheduled Discovery

Jobs can be configured with a cron schedule for periodic re-scanning. This is useful for detecting new devices added to the network. Combined with auto-import, new devices can be discovered, imported, and monitored without manual intervention.
