# Backups

Data backup, scheduling, retention, and remote transfer

The backup system creates snapshots of your data that can be used to restore the system in case of failure or data loss. Backups are also created automatically before every system update.

### What's Included

Each backup may contain:

- **Database** — full PostgreSQL dump (compressed)

- **Cache** — Redis data snapshot

- **Time-series metrics** — InfluxDB data export

- **User uploads** — branding assets (logo, favicon) and MIB files

- **Settings** — JSON export of all application settings

- **Restore script** — a `restore.sh` script that can restore the system from the backup

### Creating Backups

Go to **Administration &rarr; Backups** and click **Create Backup**. The backup runs in the background — you can continue using the system while it completes. Backups created before system updates are tagged as "Pre Update".

### Scheduled Backups

Enable scheduled backups in the backup settings panel. Choose the time and frequency (daily, weekly, or monthly). Scheduled backups run automatically and are subject to the same retention rules.

### Retention

Set the maximum number of backups to keep. When the limit is exceeded, the oldest backups are deleted automatically. This applies to all backup types (manual, scheduled, and pre-update).

### Remote Transfer

Configure an SFTP or FTPS destination to automatically transfer completed backups off-site. Set the protocol, host, port, credentials, and remote path in the backup settings. You can also manually transfer individual backups using the upload button in the backup list. Use the **Test Remote Connection** button to verify connectivity before relying on it — it checks both the connection and that the remote path is accessible.

### Restoring a Backup

To restore from a backup, click the restore button (circular arrow icon) on any completed backup in the table. A confirmation dialog will appear explaining exactly what will happen:

- **Data overwrite warning** — the current database, cache, and time-series data will be replaced with the backup contents. This cannot be undone.

- **Maintenance mode** — the system enters maintenance mode and all users see a maintenance page until the restore completes.

- **Restore executes** — the database is restored from the backup dump, cache data is reimported, time-series metrics are restored, and user uploads (branding, MIBs) are replaced.

- **System comes back online** — maintenance mode is disabled, caches are cleared, and the system is fully operational with the restored data.

- **Super-admins notified** — all super-admin users receive an email and in-app notification confirming the restore completed, or detailing any errors if it failed.

The **Restore** column in the backup table tracks the status of each restore attempt. If a restore fails, click the error link in this column to view the full error details in a popup.

### Uploading a Backup

Use the **Upload Backup** button to import a previously downloaded backup archive (.tar.gz). Uploaded backups appear in the list tagged as "Uploaded" and can be restored, downloaded, transferred, or deleted just like any other backup. This is useful for migrating data between servers or restoring from an off-site copy.

### Downloading a Backup

Download any completed backup as a .tar.gz archive using the download button. Keep a copy off-site for disaster recovery.

**Tip:** Enable scheduled backups and configure a remote SFTP/FTPS destination for a fully automated off-site backup strategy.
