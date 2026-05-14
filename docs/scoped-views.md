# Scoped Views

## Scoped User Views

Per-customer dashboards and device group restrictions

Scoped user views allow administrators to create dedicated, restricted experiences for individual customers or teams. Each user can be locked to specific device groups and a single dashboard, ensuring they only see the infrastructure relevant to them.

### How It Works

When editing a user account under **Administration &rarr; Users**, the **Access Control** section provides three key settings:

| Setting | Description |
| --- | --- |
| Default Dashboard | Assign a specific dashboard as the user's landing page. When they log in or navigate to the dashboard, this is what they see. |
| Restrict to Default Dashboard | When enabled, the user can *only* view their assigned dashboard. They cannot browse, create, or edit other dashboards. The dashboard selector in the top bar is hidden. |
| Allowed Device Groups | Restrict the user to one or more device groups. They will only see devices, alerts, SNMP traps, and search results belonging to those groups. Leave empty for unrestricted access. |

### Setting Up a Customer View

Follow these steps to create a scoped view for a customer or team:

- **Create a device group** — Go to **SNMP Devices** and create a group for the customer's devices (e.g. "Acme Corp"). Assign their devices to this group.

- **Build a dashboard** — Create a new dashboard tailored to the customer. Add widgets that reference their devices or monitors. Name it clearly (e.g. "Acme Corp Dashboard").

- **Create notification channels** — Under **Channels**, create channels for the customer (e.g. an Email channel with their IT team's email address). These will be used to send them alert notifications.

- **Set up alert rules** — Create alert rules for the customer's devices/monitors and attach their notification channels. This ensures they receive alerts only for their own infrastructure.

- **Create the user account** — Under **Administration &rarr; Users**, create a new user with the **Viewer** role (or Operator if they need to acknowledge alerts).

- **Configure access control** — In the user's Access Control section: Set **Default Dashboard** to their dedicated dashboard

- Enable **Restrict to Default Dashboard**

- Select their device group(s) under **Allowed Device Groups**

### What Gets Scoped

**Devices** — only devices in allowed groups are visible

**Alerts** — only alerts from scoped devices appear

**Search results** — global search respects group restrictions

**Dashboard** — locked to assigned dashboard when restricted

**Notifications** — per-customer channels on per-customer alert rules

### Scoped Notifications

To send alert notifications directly to a customer, create dedicated notification channels for them and attach those channels to the relevant alert rules.

- **Create a customer-specific channel** — Go to **Channels** and create a new Email channel with the customer's email address (e.g. "Acme Corp — IT Team"). You can also create SMS or Webhook channels for their own integrations.

- **Create alert rules for their devices** — Set up alert rules targeting the customer's devices or monitors. Under **Notification Channels** on the rule, select only the customer's channel(s).

- **Separate from internal alerts** — Your own admin channels remain on your internal alert rules. Each customer only receives notifications from rules that have their channel attached — they never see alerts for other customers' devices.

**Example setup:** You monitor 3 customers. Each has their own device group, dashboard, and email channel. You create alert rules per customer group — "Acme Corp CPU > 90%" sends to the "Acme Corp — IT Team" email channel, while "Beta Ltd Server Down" sends to "Beta Ltd — Ops". Your own "Admin Alerts" channel is attached to global rules that cover all devices.

**Tip:** Scoped views work with any role. A Viewer with device group restrictions gets a clean, read-only view of just their infrastructure. An Operator can also acknowledge alerts for their scoped devices. Super Admins and Admins always see everything regardless of group restrictions.
