# Webhook Ingest

Receive data from external systems via unique webhook URLs

Webhooks allow external systems to push data into ACS Monitor. Each webhook is tied to a specific device and has a unique ingest URL that accepts GET or POST requests without authentication.

### Setting Up a Webhook

- Go to a device's detail page in the Device Hub

- Switch to the **Webhooks** tab

- Click **"+ Create Webhook"**, enter a name and optional description

- Copy the generated ingest URL and configure it in your external system

- Create alert rules on the webhook to trigger notifications based on incoming data

### Ingest URL Format

POST /api/v1/webhook-ingest/{'{token}'}

Any JSON body is accepted and stored. Query parameters are also captured. The webhook records the payload, status, and source IP for each event.

### Webhook Alert Rules

Alert rules can evaluate incoming webhook payloads using JSON path expressions. Supported conditions: status_down, status_up, payload_eq, payload_ne, payload_contains, payload_gt, payload_lt. Each rule can specify a `payload_field` (dot-notation JSON path) and threshold. Notification channels and recovery notifications are fully supported.
