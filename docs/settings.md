# Settings

Global application configuration

The settings page is organised into tabs covering all aspects of system configuration. Accessible to admins via **Administration &rarr; Settings**.

- **General** — Domain and SSL configuration (with automatic certificate provisioning), email/SMTP settings with test send, and other general options.

- **SNMP** — Default SNMP poll intervals, timeout settings, and protocol defaults.

- **Monitors** — Default check interval, timeout, and service monitor behaviour settings.

- **Alerts & Notifications** — Alert evaluation settings, default severity, cooldown periods, and notification preferences.

- **Network Tools** — Configuration for on-demand diagnostic tools (ping, traceroute, port scan, etc.).

- **Workers & Performance** — Queue worker scaling, worker counts, and performance tuning.

- **Data Retention** — Retention periods for alert events, monitor results, notification logs, SNMP traps, and webhook events. Time-series metrics retention is also shown (read-only). A cleanup job runs daily at 02:00 to enforce these settings.

- **White Labelling** — Customise system name, logo, favicon, accent colour, and notification footer text. Changes apply across the entire application including the sidebar, browser title, emails, and the maintenance page.

- **Sounds** — Pick which sound plays for each notification type, browse 20 built-in tones, and upload your own WAV / MP3 files. See [Sounds & audio cues](#sounds) for details.

- **License** — View license status, connection to ACS Monitor Cloud, tier, usage against cap, license key, and expiry. See [Licensing](#licensing) for details.

- **Updates** — Current version, available updates with changelog, and one-click update button. See [Updates](#updates) for details.
