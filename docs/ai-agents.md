# Ai Agents

## AI Agents (MCP)

Let Claude and other AI agents work with your monitoring

ACS Monitor includes a built-in **Model Context Protocol (MCP)** server. Connect an AI agent such as Claude and it can look up devices, monitors, alerts and metrics, add devices and monitors, create alert rules and notification channels, acknowledge alerts, schedule maintenance windows and run network diagnostics - in plain conversation ("add these five switches", "why is the UPS alerting?", "acknowledge everything from CP1").

### Turning it on

The MCP server ships **switched off**. An administrator enables it under **Settings &rsaquo; AI Agents (MCP)**, adds the agent's address to the IP allowlist and chooses what agents may do. While it is off, the endpoint answers "not found" to everyone.

### Security model

- **IP allowlist** - single addresses or CIDR ranges. An empty list blocks every connection. The list is matched against the TCP peer address: behind a reverse proxy or load balancer that is the proxy's address.

- **API token** - every request carries `Authorization: Bearer `. The agent acts as the token's user, with exactly that user's permissions, narrowed further by the token's abilities. It can never do more than that user could in the web interface. Create a dedicated user per agent with only the permissions it needs.

- **Capability switches** - a server-wide ceiling per area (devices, monitors, alert rules, channels, ...) for viewing, creating/editing and deleting. A tool is offered only when its switch is on *and* the user holds the permission. Deleting is off by default; switching it on asks for confirmation.

- **Audit trail** - every tool call is recorded in the Audit Log under the token's user, with its arguments (secrets masked) and the caller's address.

- **Write-only credentials** - SNMP communities, passwords, tokens, signing secrets, custom header values and Slack webhook URLs are never shown to an agent. Updates keep a stored secret the agent leaves out or sends back redacted.

- **Rate limit** - calls per minute per token (default 60), adjustable in the settings.

### Connecting Claude

**Claude Code** connects to any install:

```
claude mcp add --transport http acs-monitor https://your-acs-monitor/mcp --header "Authorization: Bearer YOUR_TOKEN"
```

**Claude Desktop** connects to HTTPS addresses only (Settings &rsaquo; Connectors &rsaquo; Add custom connector). For an install on plain HTTP, use Claude Code or a local bridge such as `mcp-remote`. The settings page shows your exact endpoint with a ready-to-paste command, and offers **Download agent instructions (.md)**: a file describing the server, its conventions and every tool, to give to your agent. Agents can also fetch it themselves from `/mcp/instructions` with their token.

### What agents can do

|  |  |
| --- | --- |

Agents cannot change settings, the MCP switches or allowlist, users, roles, tokens, licensing, backups or updates.

### Troubleshooting

- **404 Not Found** - the MCP server is switched off.

- **403 Forbidden** - the agent's address is not on the allowlist (behind a proxy, allowlist the proxy), or a browser-based client sent an Origin that is not this install.

- **401 Unauthorized** - the token is missing, wrong or revoked, or its user is deactivated.

- **429 Too Many Requests** - the rate limit was reached; it resets within the minute.

- **A tool is missing** - its capability switch is off, or the token's user (or the token) lacks the permission. The instructions file marks switched-off tools "disabled by your administrator".
