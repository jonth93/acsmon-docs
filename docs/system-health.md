# System Health

Infrastructure monitoring and diagnostics

The system health dashboard provides real-time visibility into the platform's own infrastructure health.

### Monitored Services

### Server Metrics

CPU usage, memory usage (with swap), load average, and server uptime. Color-coded status badges (green/amber/red) with progress bars.

### Queue Health

Per-queue job counts (polling, monitors, discovery, alerts, notifications, tools, default). Shows pending, delayed, and reserved jobs. Failed jobs can be retried or flushed.

### Database Health

Active connection count vs. max connections, database size, and the 10 largest tables with row counts.

### Maintenance Actions

Two destructive controls live in the top-right of the System Health page. Each is gated on its own dedicated permission so you can grant the soft service restart without handing out hardware-level reboot rights. Both open a themed confirmation modal explaining the impact before anything happens.

Restart Services
soft

Cycles every container in the ACS Monitor stack — application, queue workers, scheduler, broadcasting service, probe service, database, cache, and time-series store. The page loses connection for 30–60 seconds while services come back up. Any jobs currently running on a worker are killed; queued jobs are preserved.

**When to use:** something is wedged at the application level — workers not picking up jobs, broadcasting silent, probe service unresponsive — and you'd rather not wait for the auto-recovery.

**Permission:** `system.restart-services` — granted to *super-admin* and *admin* by default.

Restart Server
hard

Reboots the entire host machine that ACS Monitor runs on. Page is unreachable until the server boots back up — typically 30 seconds to 2 minutes depending on hardware. Intended for the ISO-installed appliance build, where ACS Monitor owns the whole machine.

**Caveat:** if ACS Monitor shares its host with other workloads, those will *also* be interrupted. Use Restart Services instead unless you specifically need a full hardware-level reset.

**Permission:** `system.restart-host` — granted to *super-admin* only by default. Promote an admin via the Roles UI if appropriate.

Both actions run via a detached helper that survives the calling app being torn down by its own command, so the operation completes even though the process that dispatched it is killed mid-run.
