# Dashboards

Custom monitoring dashboards with drag-and-drop widgets

Dashboards provide a customizable view of your infrastructure. Each user can create multiple dashboards, set a default, and share dashboards publicly via a unique link.

### Creating a Dashboard

- Click the dashboard selector in the top bar and choose **"New Dashboard"**

- Enter a name and optionally set it as your default dashboard

- Add widgets using the **"+ Add Widget"** button

- Drag and resize widgets to arrange your layout

- Widget positions auto-save when you stop dragging

### Sharing

Enable sharing from the dashboard edit page. A unique share token is generated — anyone with the link can view the dashboard without logging in. The share URL never expires and the public view auto-recovers from any session timeout, so a wall-mounted NOC TV can keep the URL open indefinitely. The shared view also has its own refresh-interval picker and a fullscreen button so it can be configured for unattended display use.

### Sound on update

Seven widget types (Alert Summary, Alert List, Device Health, Status Card, Status Grid, Monitor List, Uptime Timeline) can play a sound the moment their data changes — useful because dashboards often see live updates faster than the alert pipeline can deliver them. Open the widget in the Add or Edit panel and flip on **Play sound on update**. See [Sounds & audio cues](#sounds) for the full list of triggers and how to map sounds.

### Available Widget Types (25)

#### Time-Series & Trends

- **Line Chart** — Multi-series time-series plots

- **Area Chart** — Filled line chart for visual emphasis

- **Bar Chart** — Grouped or stacked bar intervals

- **Sparkline** — Tiny inline trend line for cards

#### Gauges & Values

- **Radial Gauge** — Circular dial with colored zones (CPU%, etc.)

- **Linear Gauge** — Horizontal progress bar with thresholds

- **Metric Value** — Single large number with trend arrow

- **Dual Metric** — Two metrics side by side (In/Out)

#### Storage & Composition

- **Donut Chart** — Pie split for disk or memory breakdown

- **Storage Bar** — Stacked bar with used/free labels

- **Multi Storage** — List of disks with individual bars

#### Status & Availability

- **Status Card** — Device/monitor badge + uptime + response time

- **Status Grid** — Grid of colored dots for devices or monitors. For devices, status is determined by ping first (falls back to SNMP if no ping monitor exists). Green = up with all monitors healthy, amber = up but one or more monitors have issues, red = unreachable, grey = unknown. Warning and down states pulse. Option to hide unknown status.

- **Device Health** — Live list showing only devices and monitors with problems. Uses the same ping-first logic — devices that respond to ping with all monitors healthy are excluded. Down items (red, pulsing) appear first, followed by warning items (amber). Each row links to the detail page. Shows "All healthy" when there are no issues. Configurable to show devices only, monitors only, or both.

- **Uptime Timeline** — Horizontal up/down history bar

- **Heatmap** — Calendar heatmap of availability

#### Alerts & Events

- **Alert Summary** — Count badges by severity

- **Alert List** — Live scrolling feed of alerts

- **Event Timeline** — Vertical timeline with icons

#### Tables, SSL & Tools

- **Device List / Monitor List** — Tabular status overviews

- **Top N** — Top devices by chosen metric

- **SSL Expiry List / SSL Cert Card** — Certificate tracking

- **Ping Live / Network Tool** — Embedded tool launcher
