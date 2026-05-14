# Licensing

License key, usage caps, and ACS Monitor Cloud

Each ACS Monitor installation is activated with a permanent license key that is embedded during setup. This key uniquely identifies your instance and links it to your account on **ACS Monitor Cloud**.

### How It Works

The application communicates with ACS Monitor Cloud every few minutes to validate the license, report usage statistics, and check for updates. This determines the maximum number of devices and service monitors you can add, and ensures you are always notified when new versions are available.

### License Tiers

| Tier | Device + Monitor Cap | Description |
| --- | --- | --- |
| Free | 100 | No payment required |
| Pro | 500 | Annual subscription |
| Enterprise | 1,000 | Annual subscription |
| Custom | Custom | Contact us for tailored pricing and caps |

### Usage Caps

Your license tier sets a combined cap on the total number of active devices and service monitors. For example, if your tier allows 500, you could have 300 devices and 200 monitors, or any other combination up to 500. When you reach your cap, you will need to upgrade your tier to add more. If you remove devices or monitors, the freed capacity becomes available immediately. Existing monitoring is never interrupted — caps only apply when adding new resources.

### What Gets Reported

The periodic check-in with ACS Monitor Cloud reports: active device and monitor counts, user count, active alert count, application version, operating system, server uptime, CPU/memory/disk usage, database size, and queue health. This data is visible on your ACS Monitor Cloud dashboard so you can monitor your server's health remotely.

### Viewing Your License

Go to **Settings &rarr; License** to view your current license status, including connection status to ACS Monitor Cloud, your tier, current usage against your cap, and license expiry. If ACS Monitor Cloud is temporarily unreachable, the last known cap is used and monitoring continues uninterrupted.

### Upgrading

To upgrade your tier, log in to your account on ACS Monitor Cloud and change the plan for your server. The new cap is picked up automatically within a few minutes — no restart or reconfiguration required.

**Important:** The license key is permanently embedded in your installation and must not be modified. Changing or removing the license key will cause the system to block all device and monitor creation until a valid key is restored.
