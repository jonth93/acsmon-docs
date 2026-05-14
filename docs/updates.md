# Updates

Version management and one-click updates

ACS Monitor checks for new versions automatically via ACS Monitor Cloud. When an update is available, super-admins are notified and can apply it with a single click.

### How You're Notified

When a new version is detected, all super-admin users receive an in-app bell notification and an email with the version number and changelog. A blue notification dot also appears on the **Settings &rarr; Updates** tab. Notifications are sent once per version — you won't be spammed.

### Viewing Available Updates

Go to **Settings &rarr; Updates** to see your current version, the latest available version, release date, and a changelog of what's new. If no update information is shown, the system will retrieve it on the next check-in with ACS Monitor Cloud.

### Applying an Update

Click the **Update Now** button (super-admin only). You will be asked to confirm, as the system enters maintenance mode during the update. The process is fully automatic:

- **Maintenance mode enabled** — all users see a branded maintenance page informing them an update is in progress.

- **Full backup created** — database, cache, configuration, and application code are backed up with a self-contained restore script.

- **Update downloaded and verified** — the update package is downloaded from ACS Monitor Cloud and its integrity is verified.

- **Update applied** — code is updated, database migrations are run, caches are cleared, and all services are restarted.

- **Maintenance mode disabled** — the system is back online. The maintenance page auto-refreshes so users return to the application automatically.

### Automatic Rollback

If anything goes wrong during the update, the system automatically rolls back to the pre-update backup. Maintenance mode is disabled and the application is restored to its previous working state. No data is lost.

### Backups

Each update creates a timestamped backup containing a full database dump, cache snapshot, and application configuration. Backups are stored on the server and each includes a `restore.sh` script that can be run manually to restore the system to the exact state before the update.

**Tip:** You can check your current version at any time in Settings &rarr; Updates. The update check happens automatically — there is no need to check manually.
